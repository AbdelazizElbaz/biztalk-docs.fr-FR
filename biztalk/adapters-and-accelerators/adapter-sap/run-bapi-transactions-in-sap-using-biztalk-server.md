---
title: "Exécutez BAPI Transactions dans SAP à l’aide de BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 75ff5cf7-5e98-4d74-a13f-4de65c215d41
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 79cfa3f1b799c4a96cdad7f4c9b89b4b594dc4d8
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="run-bapi-transactions-in-sap-using-biztalk-server"></a>Exécutez BAPI Transactions dans SAP à l’aide de BizTalk Server
Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] permet aux clients d’adaptateur effectuer des transactions sur un système SAP à l’aide de [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]. Avant de créer une orchestration pour une transaction, vous devez d’abord comprendre un scénario de base dans lequel les transactions seront effectuées. Dans un scénario classique de transaction, un message de demande avec plusieurs opérations (par exemple, appeler une commande BAPI) est envoyé au système SAP. Cela est appelé un message « opération ». L’orchestration doit extraire chaque message d’opération à partir du message de demande et envoyer les messages d’opération individuelle au système SAP. L’orchestration envoie les unes après les autres à l’aide de la même connexion. L’orchestration extrait les messages individuels à partir du message « opération » à l’aide d’une transformation XML via un mappage BizTalk.  
  
 Une fois que les opérations sont effectuées, l’orchestration doit valider ou abandonner la transaction en envoyant des messages pour BAPI_TRANSACTION_COMMIT ou BAPI_TRANSACTION_ROLLBACK, respectivement. Il seront appelés « messages de transaction ».  
  
## <a name="how-does-the-adapter-enable-transactions-through-biztalk-server"></a>Comment l’adaptateur n’active pas les Transactions via BizTalk Server ?  
 Pour activer les transactions sur un système SAP à l’aide du [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]:  
  
-   Fournit les propriétés de contexte de message ouvrir, RÉUTILISENT, CLOSE et abandonner.  
  
-   Utilise BAPI_TRANSACTION_COMMIT et BAPI_TRANSACTION_ROLLBACK pour valider ou annuler les opérations. Ceux-ci sont exposés par le système SAP.  
  
 Le tableau suivant répertorie certaines des recommandations sur l’utilisation de propriétés avec BAPI_TRANSACTION_COMMIT ou BAPI_TRANSACTION_ROLLBACK :  
  
|Message|OPEN|RÉUTILISER|CLOSE|ABANDON|  
|-------------|----------|-----------|-----------|-----------|  
|Premier message (message d’opération)|Oui|Non|Non|Non|  
|Messages suivants (messages d’opération)|Non|Oui|Non|Non|  
|BAPI_TRANSACTION_COMMIT (message de transaction)|Non|Non|Oui|Non|  
|BAPI_TRANSACTION_ROLLBACK (message de transaction)|Non|Non|Oui|Oui|  
  
 Dans la table, un « Oui » désigne la propriété de contexte de message à utiliser pour un message. De même, un « non » indique la propriété de contexte de message doit ne pas être utilisée avec un message.  
  
 Résumé de la table :  
  
-   Le premier message doit toujours être un message d’opération et devez utiliser uniquement la propriété ouverte.  
  
-   Les messages d’opération ultérieure doivent utiliser la propriété de réutilisation.  
  
-   Le message de transaction correspondant à BAPI_TRANSACTION_COMMIT pour valider la transaction doit utiliser la propriété ferme.  
  
-   Le message de transaction correspondant à BAPI_TRANSACTION_ROLLBACK pour abandonner la transaction peut utiliser les propriétés de fermer ou abandonner. Si l’abandon, dans l’idéal, le message doit être dans le bloc d’exception d’orchestration.  
  
## <a name="key-considerations-related-to-transactions-using-biztalk-server"></a>Points clés liés aux Transactions à l’aide de BizTalk Server  
  
-   S’il existe plus d’un port d’envoi dans une orchestration, l’adaptateur sépare automatiquement les transactions pour les messages reçus à partir de chaque port. Autrement dit, une transaction ne peut pas couvrir les ports.  
  
-   Nouvelle tentative n’est pas pris en charge pour les messages dans une transaction de SAP. Par conséquent, les utilisateurs doivent définir la message nouvelle tentative à zéro.  
  
-   L’adaptateur peut produire des résultats inattendus pour les combinaisons marqués comme « Non » dans le tableau précédent. Vous devez utiliser les combinaisons de la mention « Oui ».  
  
-   Les messages envoyés à l’adaptateur et qui n’ont pas d’une propriété de contexte de message seront effectués normalement sans être lié au contexte de transaction actuel.  
  
-   BAPI_TRANSACTION_COMMIT ou BAPI_TRANSACTION_ROLLBACK doit être dans l’idéal, le dernier message dans le contexte de transaction actuel dans l’orchestration.  
  
 Les sections suivantes fournissent des instructions sur la façon d’effectuer des transactions dans SAP à l’aide du [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].  
  
## <a name="how-to-perform-a-transaction-on-an-sap-system"></a>Comment effectuer une Transaction sur un système SAP ?  
 Une opération sur un système SAP à l’aide du [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] avec [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] implique les tâches de procédures décrites dans [blocs de construction pour créer des applications SAP](../../adapters-and-accelerators/adapter-sap/building-blocks-to-create-sap-applications.md). Pour effectuer des transactions sur un système SAP, ces tâches sont :  
  
1.  Créez un projet BizTalk et générer le schéma pour le document RFC sur lequel vous souhaitez effectuer la transaction. En outre, vous devez générer le schéma pour BAPI_TRANSACTION_COMMIT et BAPI_TRANSACTION_ROLLBACK RFC.  
  
2.  Créer des messages dans le projet BizTalk pour envoyer et recevoir des messages à partir du système SAP.  
  
3.  Créez une orchestration qui extrait individuels « messages d’opération » du message de demande et l’envoie au système SAP. En se basant sur le message de demande, l’orchestration également décide s’il faut valider ou annuler la transaction.  
  
4.  Générez et déployez le projet BizTalk.  
  
5.  Configurer l’application en créant physique d’envoi et ports de réception BizTalk.  
  
6.  Démarrez l’application BizTalk.  
  
 Cette rubrique fournit des instructions pour effectuer ces tâches.  
  
## <a name="sample-based-on-this-topic"></a>Exemple basé sur cette rubrique  
 Un exemple SAPTransaction, en fonction de cette rubrique est fourni avec le [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]. Pour plus d’informations, consultez [exemples pour l’adaptateur SAP](../../adapters-and-accelerators/adapter-sap/samples-for-the-sap-adapter.md).  
  
## <a name="generating-schema"></a>Génération du schéma  
 Pour montrer comment effectuer des transactions sur un système SAP, vous devez les schémas suivants :  
  
-   Pour le message « opération » pour effectuer des opérations sur un système SAP. Le message de demande envoyé à l’adaptateur doit être conforme à ce schéma. Cela peut être n’importe quel schéma spécifiques à l’utilisateur contenant n’importe quel nombre de nœuds de l’opération. Dans cette rubrique, le schéma MultipleOrders.xsd est utilisé. Le schéma est également fourni comme partie de l’exemple de transaction fourni avec le [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] exemples. Pour plus d’informations, consultez [exemples de schéma](../../adapters-and-accelerators/accelerator-rosettanet/schema-samples.md).  
  
-   Pour effectuer les opérations sur un système SAP, comme l’appel d’une demande de changement. Le message de demande d’effectuer une opération doit être conforme à ce schéma. Ce schéma doit être généré à l’aide de la [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]. Dans cette rubrique, le document RFC BAPI_SALESORDER_CREATEFROMDAT2 est appelé. Pour plus d’informations sur la génération de schéma pour RFC, consultez [Parcourir, rechercher et obtenir de métadonnées pour les opérations de RFC dans SAP](../../adapters-and-accelerators/adapter-sap/browse-search-and-get-metadata-for-rfc-operations-in-sap.md).  
  
-   Pour l’abandon ou de valider une transaction. La demande pour valider ou annuler une transaction doit être conforme à ce schéma. Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] utilise le BAPI_TRANSACTION_COMMIT et BAPI_TRANSACTION_ROLLBACK RFC pour commit et rollback les opérations respectivement. Vous devez générer le schéma pour ces RFC à l’aide de la [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)].  
  
> [!NOTE]
>  Vous devez vous assurer que tous les schémas requis sont ajoutés au projet BizTalk.  
  
> [!IMPORTANT]
>  Vous devez ajouter une référence au schéma de propriété BizTalk pour [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] à votre projet BizTalk. Le fichier de schéma, *Microsoft.Adapters.SAP.BiztalkPropertySchema.dll*, est installé par le [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] le programme d’installation, en général au \<lecteur d’installation\>: \Program Files\Microsoft Pack d’adaptateurs BizTalk \Bin.  
  
## <a name="defining-messages-and-message-types"></a>Définition des Messages et les Types de messages  
 Le schéma que vous avez généré précédemment décrit les « types » requis pour les messages dans l’orchestration. Un message est généralement une variable, le type est défini par le schéma correspondant. Vous devez lier le schéma généré à la première étape pour les messages à partir de la fenêtre Vue Orchestration du projet BizTalk.  
  
 Avant de créer des messages, vous devez déterminer le nombre de nœuds de « opération » le message de demande (de type de MultipleOrders.xsd) a. Pour cet exemple, supposons que le message de demande possède deux messages d’opération à appeler la RFC BAPI_SALESORDER_CREATEFROMDAT2. Par conséquent, vous devez créer un ensemble de messages de demande-réponse qui mappe au schéma généré pour ce document RFC.  
  
 Vous devez créer les messages suivants dans le projet BizTalk.  
  
-   Un message, SendtoAdapter, pour le message de demande qui sera envoyé à l’orchestration. Ce message doit être mappé au schéma du message d’entrée, MultipleOrders.xsd.  
  
-   Un message, BAPIMessage, pour la première opération envoyé au système SAP. Vous devez également créer un message de réponse, BAPIResponse, pour la réponse de la première opération. Les messages de demande et de réponse doivent être mappés au schéma généré pour le document RFC BAPI_SALESORDER_CREATEFROMDAT2.  
  
-   Un message, BAPICommitMessage, pour l’opération de validation. Vous devez également créer un message de réponse, BAPICommitResponse, pour le message de réponse correspondant. Les messages de demande et de réponse doivent être mappés au schéma de BAPI_TRANSACTION_COMMIT RFC.  
  
-   Un message, BAPIRollbackMessage, pour l’opération de restauration. Vous devez également créer un message de réponse, BAPIRollbackResponse, pour le message de réponse correspondant. Les messages de demande et de réponse doivent être mappés au schéma de BAPI_TRANSACTION_ROLLBACK RFC.  
  
 Procédez comme suit pour créer des messages et les lier au schéma.  
  
#### <a name="to-create-messages-and-link-to-schema"></a>Pour créer des messages et le lier au schéma  
  
1.  Ouvrez la vue orchestration au projet BizTalk, si elle n’est pas déjà ouvert. Cliquez sur **vue**, pointez sur **autres fenêtres**, puis cliquez sur **Vue Orchestration**.  
  
2.  Dans le **Vue Orchestration**, avec le bouton droit **Messages**, puis cliquez sur **nouveau Message**.  
  
3.  Avec le bouton droit le nouvellement créé le message, puis **fenêtre Propriétés**.  
  
4.  Dans le **propriétés** volet pour **Message_1**, procédez comme suit.  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |Identificateur|Type **SendToAdapter**.|  
    |Type de message|Dans la liste déroulante, développez **schémas**, puis sélectionnez *SAPTransaction.MultipleOrders*, où *SAPTransaction* est le nom de votre projet BizTalk. *MultipleOrders* est le schéma du message de demande.|  
  
5.  Répétez l’étape précédente pour créer les six plus de messages. Dans le **propriétés** volet pour les nouveaux messages, procédez comme suit.  
  
    |Identificateur de la valeur|Définissez le Type de Message|  
    |-----------------------|-------------------------|  
    |BAPIMessage|*SAPTransaction.SAPBindingSchema.BAPI_SALESORDER_CREATEFROMDAT2*|  
    |BAPIResponse|*SAPTransaction.SAPBindingSchema.BAPI_SALESORDER_CREATEFROMDAT2Response*|  
    |BAPICommitMessage|*SAPTransaction.SAPBindingSchema.BAPI_TRANSACTION_COMMIT*|  
    |BAPICommitResponse|*SAPTransaction.SAPBindingSchema.BAPI_TRANSACTION_COMMITResponse*|  
    |BAPIRollbackMessage|*SAPTransaction.SAPBindingSchema.BAPI_TRANSACTION_ROLLBACK*|  
    |BAPIRollbackResponse|*SAPTransaction.SAPBindingSchema.BAPI_TRANSACTION_ROLLBACKResponse*|  
  
## <a name="setting-up-the-orchestration"></a>Configuration de l’Orchestration  
 Vous devez créer une orchestration BizTalk à utiliser [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] pour effectuer des transactions dans un système SAP. Dans cette orchestration, vous déposez un message de demande à une emplacement de réception. Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] consomme le message et le transmet au système SAP. La réponse du système SAP est enregistrée dans un autre emplacement.  
  
 Une autre considération à prendre lors de la création d’une orchestration consiste à :  
  
-   Mapper le schéma du message de demande à celle de la RFC BAPI_SALESORDER_CREATEFROMDAT2.  
  
-   Mapper le schéma du message de demande à celle du BAPI_TRANSACTION_COMMIT et BAPI_TRANSACTION_ROLLBACK RFC.  
  
 Vous pouvez mapper les schémas à l’aide d’une transformation XML via un mappage BizTalk. Pour ce faire, inclure des formes transformer dans l’orchestration.  
  
 Enfin, selon si le message de demande possède des informations pour valider ou abandonner la transaction, l’orchestration doit décider sur le message approprié pour être envoyé au système SAP. Pour ce faire, inclure une forme décider de l’orchestration.  
  
 Pour plus d’informations sur les différentes formes incluses dans l’orchestration, consultez le **l’interface utilisateur du Concepteur d’Orchestration** [!INCLUDE[ui-guidance-developers-reference](../../includes/ui-guidance-developers-reference.md)].
  
 Un exemple d’orchestration pour une transaction SAP ressemble à ceci.  
  
 ![Orchestration permettant d’effectuer des transactions dans SAP](../../adapters-and-accelerators/adapter-sap/media/727f82e9-51a9-4a94-9d0a-d05c17904bde.gif "727f82e9-51a9-4a94-9d0a-d05c17904bde")  
  
### <a name="adding-message-shapes"></a>Ajouter des formes de Message  
 Assurez-vous que vous spécifiez les propriétés suivantes pour chacune des formes de message. Les noms répertoriés dans la colonne de forme sont les noms des formes de message tel qu’affiché dans l’orchestration précédente.  
  
|Graphique à base de formes|Type de forme|Propriétés|  
|-----------|----------------|----------------|  
|ReceiveInputXML|Recevoir|-Définissez **nom** à *ReceiveInputXML*<br /><br /> -Définissez **activer** à *True*|  
|SendToLOB|Send|-Définissez **nom** à *SendToLOB*|  
|Réception réponse|Recevoir|-Définissez **nom** à *ReceiveResponse*<br /><br /> -Définissez **activer** à *False*|  
|SendResponse|Send|-Définissez **nom** à *SendResponse*|  
  
 Étant donné que le message de demande possède deux messages insert, vous devez créer un autre ensemble d’envoi et reçoivent des formes pour envoyer des messages à SAP et de recevoir une réponse. Toutefois, les messages insert peuvent être validées ou restaurées, le deuxième ensemble de formes doit être créé dans un bloc de décision. Vous devez créer un ensemble de formes de validation et un autre ensemble de formes à la restauration.  
  
> [!NOTE]
>  Vous pouvez ajouter un bloc de décision en faisant glisser la forme décider à partir de la boîte à outils Orchestrations BizTalk.  
  
#### <a name="message-shapes-for-commit"></a>Les formes de message pour valider  
 Le tableau suivant répertorie les formes pour le chemin « validation » de l’orchestration. Ici, vous n’avez pas besoin de créer un message de réception pour un message de demande. Le message de demande est passé à partir de la forme d’un message précédent.  
  
|Graphique à base de formes|Type de forme|Propriétés|  
|-----------|----------------|----------------|  
|SendBAPICommit|Send|-Définissez **nom** à *SendBAPICommit*|  
|ReceiveCommitResponse|Recevoir|-Définissez **nom** à *ReceiveCommitResponse*<br /><br /> -Définissez **activer** à *False*|  
|SendResponse2|Send|-Définissez **nom** à *SendResponse2*|  
  
#### <a name="message-shapes-for-abort"></a>Les formes de message pour abandonner  
 Le tableau suivant répertorie les formes pour le chemin « restauration » de l’orchestration.  
  
|Graphique à base de formes|Type de forme|Propriétés|  
|-----------|----------------|----------------|  
|SendBAPIRollback|Send|-Définissez **nom** à *SendBAPIRollback*|  
|ReceiveRollbackResponse|Recevoir|-Définissez **nom** à *ReceiveRollbackResponse*<br /><br /> -Définissez **activer** à *False*|  
|SendResponse3|Send|-Définissez **nom** à *SendResponse3*|  
  
### <a name="setting-the-rule-expression"></a>Définition de l’Expression de la règle  
 Inclus les formes de message pour la validation et de l’abandon d’opérations au sein d’un bloc de décision en ajoutant une forme décider. Pour spécifier la condition sur laquelle l’orchestration est une décision, vous devez spécifier une expression de la forme de la règle en fonction sur laquelle la transaction est soit être validée ou restaurée. Par exemple, vous devez spécifier l’expression suivante pour la forme de règle :  
  
```  
SendToAdapter.isCommit == true  
```  
  
 WHERE, SendToAdapter est le message que vous avez créé pour le schéma du message de demande. Ainsi, dans le message de demande, si le `isCommit` a la valeur de balise **True**, l’orchestration prend l’itinéraire « commit ». Sinon, l’orchestration met l’itinéraire « restauration ».  
  
 Pour être en mesure de spécifier cette condition dans l’éditeur d’expression, vous devez avoir promu le `isCommit` propriété dans le schéma de message du message de demande envoyé à l’adaptateur. Pour cette rubrique, le schéma d’entrée à utiliser est MultipleOrders.xsd. Vous devez promouvoir le `isCommit` propriété dans ce schéma. Pour plus d’informations sur la promotion d’une propriété, consultez [promotion des propriétés](../../core/promoting-properties.md).
  
### <a name="adding-construct-message-shapes"></a>Ajouter des formes de Message de construction  
 Comme indiqué précédemment, le message de demande envoyé à l’adaptateur contient insérer deux messages, puis un message de validation ou d’abandon. Vous devez ajouter une forme construire un Message, et dans laquelle une transformation de forme pour extraire des messages d’opération individuelle à envoyer au système SAP. Vous devez également ajouter une forme assignation du Message pour définir des propriétés de contexte pour l’activation des transactions le message.  
  
#### <a name="the-first-construct-message-shape"></a>La première forme construire un Message  
 Supposons que la première forme construire un Message est appelée « ReceiveXML. » Pour cette forme, spécifiez la propriété Messages construits en tant que « BAPIMessage ». Double-cliquez sur la forme Transformer pour ouvrir la **transformer la Configuration** boîte de dialogue. Dans la boîte de dialogue :  
  
-   Choisissez cette option pour créer un nouveau mappage.  
  
-   Dans le volet gauche, sélectionnez **Source** et à partir de la **nom de la Variable** liste déroulante Sélectionnez *SendToAdapter*.  
  
-   Dans le volet gauche, sélectionnez **Destination** et à partir de la **nom de la Variable** liste déroulante Sélectionnez *BAPIMessage*.  
  
-   Cliquez sur **OK** pour démarrer le mappeur. Mapper le schéma du message de demande pour le schéma de la BAPI_SALESORDER_CREATEFROMDAT2. Vous pouvez utiliser la **Index** fonctoid pour créer un mappage entre la schémas source et les destination. Un **Index** fonctoid vous permet de sélectionner des informations pour un enregistrement spécifique dans une série d’enregistrements.  
  
     La figure suivante illustre les schémas mappés en utilisant un **Index** fonctoid.  
  
     ![Schémas mappés à l’aide d’un fonctoid Index](../../adapters-and-accelerators/adapter-sap/media/d0ade577-ea74-4be3-a724-4ba19397d8d3.gif "d0ade577-ea74-4be3-a724-4ba19397d8d3")  
  
     Pour plus d’informations sur l’utilisation de la **transformer la Configuration** boîte de dialogue, consultez la **boîte de dialogue de Configuration transformer** [!INCLUDE[ui-guidance-developers-reference](../../includes/ui-guidance-developers-reference.md)].
  
     Pour plus d’informations sur l’utilisation du fonctoid Index, consultez [fonctoid Index](../../core/index-functoid.md).
       
     Après avoir mappé les schémas, vous pouvez tester le mappage à l’aide de la page de propriétés du fichier de mappage. Pour plus d’informations, consultez la  **<Map File> boîte de dialogue Page de propriétés, de tester le mappage** onglet [!INCLUDE[ui-guidance-developers-reference](../../includes/ui-guidance-developers-reference.md)].
  
 Dans la forme assignation du Message, spécifiez la propriété de contexte de message pour démarrer la transaction. Par exemple, la propriété de contexte de message pour le premier message peut être :  
  
```  
BAPIMessage(Microsoft.Adapters.SAP.BiztalkPropertySchema.ConnectionState) = "OPEN";  
```  
  
#### <a name="the-commit-construct-message-shape"></a>La forme construire un Message de la validation  
 Supposons que la forme construire un Message pour l’opération de validation est appelée « CommitMessage ». Pour cette forme, spécifiez la propriété Messages construits en tant que « BAPICommitMessage ». Double-cliquez sur la forme Transformer pour ouvrir la **transformer la Configuration** boîte de dialogue. Dans la boîte de dialogue :  
  
-   Choisissez cette option pour créer un nouveau mappage.  
  
-   Dans le volet gauche, sélectionnez **Source** et à partir de la **nom de la Variable** liste déroulante Sélectionnez *SendToAdapter*.  
  
-   Dans le volet gauche, sélectionnez **Destination** et à partir de la **nom de la Variable** liste déroulante Sélectionnez *BAPICommitMessage*.  
  
-   Cliquez sur OK pour lancer le mappeur. Mapper le schéma du message de demande pour le schéma de BAPI_TRANSACTION_COMMIT. Vous ne devez pas inclure un fonctoid Index pour ce mappage, car le nœud BAPI_TRANSACTION_COMMIT ne contient pas d’une hiérarchie de l’enregistrement.  
  
 Dans la forme assignation du Message, spécifiez la propriété de contexte de message pour valider la transaction. Par exemple, la propriété de contexte de message pour le premier message peut être :  
  
```  
BAPICommitMessage(Microsoft.Adapters.SAP.BiztalkPropertySchema.ConnectionState) = "CLOSE";  
```  
  
#### <a name="the-rollback-construct-message-shape"></a>La forme construire un Message Rollback  
 Supposons que la forme construire un Message pour l’opération de restauration est appelée « RollbackMessage ». Pour cette forme, spécifiez la propriété Messages construits en tant que « BAPIRollbackMessage ». Double-cliquez sur la forme Transformer pour ouvrir la **transformer la Configuration** boîte de dialogue. Dans la boîte de dialogue :  
  
-   Choisissez cette option pour créer un nouveau mappage.  
  
-   Dans le volet gauche, sélectionnez **Source** et à partir de la **nom de la Variable** liste déroulante Sélectionnez *SendToAdapter*.  
  
-   Dans le volet gauche, sélectionnez **Destination** et à partir de la **nom de la Variable** liste déroulante Sélectionnez *BAPIRollbackMessage*.  
  
-   Cliquez sur OK pour lancer le mappeur. Mapper le schéma du message de demande pour le schéma de BAPI_TRANSACTION_ROLLBACK. Vous ne devez pas inclure un fonctoid Index pour ce mappage, car le nœud BAPI_TRANSACTION_ROLLBACK ne contient pas d’une hiérarchie de l’enregistrement.  
  
 Dans la forme assignation du Message, spécifiez la propriété de contexte de message pour annuler la transaction. Par exemple, la propriété de contexte de message pour le premier message peut être :  
  
```  
BAPIRollbackMessage(Microsoft.Adapters.SAP.BiztalkPropertySchema.ConnectionState) = "ABORT";  
```  
  
> [!IMPORTANT]
>  Dans les scénarios classiques, le message correspondant à BAPI_TRANSACTION_ROLLBACK avec la propriété de contexte d’annulation doit être utilisé dans un bloc d’exception.  
  
### <a name="adding-ports"></a>Ajout de Ports  
 Assurez-vous que vous spécifiez les propriétés suivantes pour chacun des ports logiques. Les noms répertoriés dans le *Port* colonne sont les noms des ports que ceux affichés dans l’orchestration.  
  
 Pour cette orchestration, trois ports sont créés. Le premier port récupère le message de demande à partir d’un dossier spécifié. Le deuxième port envoie les messages au système SAP et reçoit une réponse. Le troisième port enregistre la réponse à un autre dossier. Par conséquent :  
  
-   Le premier port reçoit uniquement des messages pour un schéma unique, c'est-à-dire MultipleOrders.xsd.  
  
-   Le deuxième port envoie et reçoit des messages pour le schéma de BAPI_SALESORDER_CREATEFROMDAT2 RFC. En outre, le même port servira à valider ou restaurer la transaction. Par conséquent, ce port reçoit également des messages de schémas pour BAPI_TRANSACTION_COMMIT et BAPI_TRANSACTION_ROLLBACK RFC. Pour ce faire, trois opérations différents sont créées sur ce port, chacun correspondant à un schéma de message spécifique.  
  
-   Comme pour le deuxième port, ce port sera également recevoir les messages avec trois schémas différents. Par conséquent, il est nécessaire de créer les trois différentes opérations sur ce port.  
  
|Port|Propriétés|  
|----------|----------------|  
|Fichier|-Définissez **identificateur** à *FileIn*<br /><br /> -Définissez **Type** à *FileInType*<br /><br /> -Définissez **modèle de Communication** à *à sens unique*<br /><br /> -Définissez **Direction de Communication** à *de réception*|  
|LOBPort|-Définissez **identificateur** à *LOBPort*<br /><br /> -Définissez **Type** à *LOBPortType*<br /><br /> -Définissez **modèle de Communication** à *demande-réponse*<br /><br /> -Définissez **Direction de Communication** à *envoi / réception*<br /><br /> -Créer une opération *BAPIMessage*.<br /><br /> -Créer une opération *CommitMessage*. Cette opération sera utilisée pour envoyer le message de validation.<br /><br /> -Créer une opération *RollbackMessage*. Cette opération sera utilisée pour envoyer le message de la restauration.|  
|SaveResponse|-Définissez **identificateur** à *SaveResponse*<br /><br /> -Définissez **Type** à *SaveResponseType*<br /><br /> -Définissez **modèle de Communication** à *à sens unique*<br /><br /> -Définissez **Direction de Communication** à *envoyer*.<br /><br /> -Créer une opération *BAPIMessage*.<br /><br /> -Créer une opération *CommitMessage*. Cette opération permet de sauvegarder les réponses pour le message de validation.<br /><br /> -Créer une opération *RollbackMessage*. Cette opération permet de sauvegarder les réponses pour le message de la restauration.|  
  
## <a name="specify-messages-for-action-shapes-and-connect-to-ports"></a>Spécifier des Messages pour les formes d’Action et de se connecter à des Ports  
 Le tableau suivant indique les propriétés et leurs valeurs à définir pour spécifier les messages de formes d’action et les lier aux ports. Les noms répertoriés dans le *forme* colonne sont les noms des formes de message, tel qu’affiché dans l’orchestration précédente.  
  
|Graphique à base de formes|Propriétés|  
|-----------|----------------|  
|ReceiveInputXML|-Définissez **Message** à *SendToAdapter*<br /><br /> -Définissez **opération** à *FileIn.Transaction.Request*|  
|SendToLOB|-Définissez **Message** à *BAPIMessage*<br /><br /> -Définissez **opération** à *LOBPort.BAPIMessage.Request*|  
|Réception réponse|-Définissez **Message** à *BAPIResponse*<br /><br /> -Définissez **opération** à *LOBPort.BAPIMessage.Response*|  
|SendResponse|-Définissez **Message** à *BAPIResponse*<br /><br /> -Définissez **opération** à *SaveResponse.BAPIMessage.Request*|  
|SendBAPICommit|-Définissez **Message** à *BAPICommitMessage*<br /><br /> -Définissez **opération** à *LOBPort.CommitMessage.Request*|  
|ReceiveCommitResponse|-Définissez **Message** à *BAPICommitResponse*<br /><br /> -Définissez **opération** à *LOBPort.CommitMessage.Response*|  
|SendResponse2|-Définissez **Message** à *BAPICommitResponse*<br /><br /> -Définissez **opération** à *SaveResponse.CommitMessage.Request*|  
|SendBAPIRollback|-Définissez **Message** à *BAPIRollbackMessage*<br /><br /> -Définissez **opération** à *LOBPort.RollbackMessage.Request*|  
|ReceiveRollbackResponse|-Définissez **Message** à *BAPIRollbackResponse*<br /><br /> -Définissez **opération** à *LOBPort.RollbackMessage.Response*|  
|SendResponse3|-Définissez **Message** à *BAPIRollbackResponse*<br /><br /> -Définissez **opération** à *SaveResponse.RollbackMessage.Request*|  
  
 Une fois que vous avez défini ces propriétés, les formes de message et les ports sont connectés et l’orchestration est terminée.  
  
## <a name="handling-exceptions"></a>La gestion des Exceptions  
 Dans les orchestrations complexes semblable à celui pour effectuer des transactions de BAPI, il est important d’effectuer le suivi de l’état de l’orchestration, signaler des erreurs lorsqu’ils se produisent, afin que vous pouvez résoudre les problèmes qu’ils se produisent. L’orchestration BizTalk fournit des outils pour gérer les erreurs, pour maintenir l’état d’une orchestration et pour résoudre les problèmes qu’ils ont lieu via les transactions, la compensation et la gestion des exceptions.  
  
 En tant qu’infrastructure pour les transactions et la gestion des exceptions, le Concepteur d’Orchestration fournit le **étendue** forme. Une étendue peut avoir un type de transaction, une compensation et n'importe quel nombre de gestionnaires d'exception. Une étendue contient un ou plusieurs blocs. Il a un corps et peut éventuellement avoir n’importe quel nombre de blocs de gestion des exceptions est ajoutée. Dans le cas des transactions BAPI, l’intégralité de l’orchestration (voir la figure précédente) peut être inclus dans une étendue.  
  
 Pour intercepter l’exception, vous devez ajouter un **intercepter l’Exception** bloc à l’orchestration. **Intercepter Exception** blocs sont attachés à la fin d’un **étendue** forme dans le Concepteur d’Orchestration. Dans le cas des transactions BAPI, vous devez ajouter la routine « Annulation » pour le **intercepter l’Exception** bloquer, autrement dit, vous devez ajouter les éléments suivants à la routine « Annulation » :  
  
-   Forme construire un Message comprenant une transformation (pour extraire le message de demande à partir du message d’entrée) et une forme assignation du Message (pour définir la propriété de contexte)  
  
-   Envoyer et recevoir des formes.  
  
 L’exemple de transaction de SAP pour [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] (SAPTransaction) livré avec [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] illustre la gestion des exceptions, trop. Pour plus d’informations sur l’exemple, consultez [exemples pour l’adaptateur SAP](../../adapters-and-accelerators/adapter-sap/samples-for-the-sap-adapter.md).  
  
 Pour plus d’informations sur la gestion des exceptions, en général, à l’aide de [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], consultez [à l’aide de Transactions et gestion des Exceptions](../../core/using-transactions-and-handling-exceptions.md).
  
## <a name="add-the-biztalk-property-schema-to-biztalk"></a>Ajoutez le schéma de propriété BizTalk à BizTalk  
 Dans votre projet BizTalk, vous avez ajouté une référence d’assembly au schéma de propriété BizTalk pour [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]. Vous devez ajouter le même assembly en tant que ressource dans l’application BizTalk, autrement dit, l’application où sera déployé le projet BizTalk. Le fichier de schéma, *Microsoft.Adapters.SAP.BiztalkPropertySchema.dll*, est installé par le [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] le programme d’installation en général sous \<lecteur d’installation\>: \Program Files\Microsoft l’adaptateur BizTalk Pack\bin. Sans cette ressource, vous ne serez pas en mesure de déployer votre projet.  
  
#### <a name="to-add-an-assembly-as-a-resource-in-biztalk"></a>Pour ajouter un assembly en tant que ressource dans BizTalk Server  
  
1.  Démarrer le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.  
  
2.  Dans l’arborescence de la console, développez **groupe BizTalk**, développez **Applications**et puis l’application à laquelle vous souhaitez ajouter un assembly BizTalk.  
  
3.  Avec le bouton droit **ressources**, pointez sur **ajouter** puis cliquez sur **assemblys BizTalk**.  
  
4.  Dans le **ajouter une ressource** boîte de dialogue, cliquez sur **ajouter**, accédez au dossier contenant le fichier d’assembly BizTalk, sélectionnez le fichier d’assembly BizTalk, puis cliquez sur **ouvrir**.  
  
5.  Dans **Options**, spécifiez les options d’installation de l’assembly BizTalk dans le GAC, puis cliquez sur **OK**.  
  
 Vous devez maintenant créer la solution BizTalk et déployez-le sur un serveur BizTalk. Pour plus d’informations, consultez [génération et exécution des Orchestrations](../../core/building-and-running-orchestrations.md).
  
## <a name="configuring-the-biztalk-application"></a>Configuration de l’Application BizTalk  
 Après avoir déployé le projet BizTalk, l’orchestration que vous avez créé précédemment est répertoriée sous le **Orchestrations** volet de la console Administration de BizTalk Server. Vous devez utiliser la console Administration de BizTalk Server pour configurer l’application. Pour plus d’informations sur la configuration d’une application, consultez [comment configurer une Application](../../core/how-to-configure-an-application.md).
  
 Configuration d’une application implique :  
  
-   Sélection d’un hôte de l’application.  
  
-   Mappage de ports que vous avez créé dans l’orchestration aux ports physiques dans la console Administration de BizTalk Server. Pour cette orchestration, vous devez :  
  
    -   Définir un emplacement sur le disque dur et un port de fichier correspondant où vous allez déposer un message de demande. L’orchestration BizTalk consommer le message de demande et l’envoyer au système SAP.  
  
    -   Définir un emplacement sur le disque dur et un port de fichier correspondant dans lequel l’orchestration BizTalk supprimera le message de réponse contenant la réponse du système SAP.  
  
    -   Définir un port d’envoi WCF-Custom ou WCF-SAP physique pour envoyer des messages au système SAP. Pour plus d’informations sur la création de ports, consultez [configurer manuellement une liaison de port physique à l’adaptateur SAP](../../adapters-and-accelerators/adapter-sap/manually-configure-a-physical-port-binding-to-the-sap-adapter.md). Étant donné que l’envoi envoie le port et recevoir des messages conformes à plusieurs schémas et effectue deux opérations, vous devez définir une action dynamique pour les opérations. Pour plus d’informations sur les actions, consultez [configurer l’action SOAP pour le système SAP](../../adapters-and-accelerators/adapter-sap/configure-the-soap-action-for-the-sap-system.md). Assurez-vous que vous respectiez les points clés suivants lors de la création d’un WCF-Custom ou WCF-SAP port d’envoi pour effectuer des transactions.  
  
        |Définissez les paramètres suivants|Cette valeur|  
        |-----------------------|-------------------|  
        |Action|Le port d’envoi envoie et reçoit des messages pour plusieurs opérations. Par conséquent, l’action sur le port d’envoi doit être définie pour chaque opération.<br /><br /> `<BtsActionMapping>   <Operation Name="BAPIMessage" Action="http://Microsoft.LobServices.Sap/2007/03/Rfc/BAPI_SALESORDER_CREATEFROMDAT2" />   <Operation Name="CommitMessage" Action="http://Microsoft.LobServices.Sap/2007/03/Rfc/BAPI_TRANSACTION_COMMIT" />   <Operation Name="RollbackMessage" Action="http://Microsoft.LobServices.Sap/2007/03/Rfc/BAPI_TRANSACTION_ROLLBACK" /> </BtsActionMapping>`|  
        |EnableBizTalkCompatibilityMode|Affectez à cette propriété de liaison **True**.|  
        |EnableConnectionPooling|Affectez à cette propriété de liaison **False** avant d’effectuer des transactions. Dans les scénarios où le canal entre l’adaptateur et BizTalk est inattendue, la connexion correspondante est ajoutée au pool de connexions. Lorsqu’un autre canal est ouvert, et le nouveau canal choisit le même objet de connexion, les transactions non validées sur l’ancien objet de connexion sera également validées lorsque les transactions sont validées sur le nouveau canal. Pour éviter cela, le regroupement de connexions doit être désactivé lors de l’exécution de transactions.|  
  
        > [!NOTE]
        >  Génération de schéma à l’aide du [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] crée également un fichier de liaison contenant des informations sur les ports et les actions à définir pour ces ports. Vous pouvez importer ce fichier de liaison à partir de la console Administration de BizTalk Server pour créer des ports d’envoi (pour les appels sortants) ou de ports de réception (d’appels entrants). Pour plus d’informations, consultez [configurer une liaison de port physique à l’aide d’un fichier de liaison de port à SAP](../../adapters-and-accelerators/adapter-sap/configure-a-physical-port-binding-using-a-port-binding-file-to-sap.md).
  
        > [!IMPORTANT]
        >  Vous pouvez configurer un transport secondaire sur un WCF-Custom ou WCF-SAP port d’envoi qui vous permet d’envoyer des messages à un autre système SAP si le transport principal ne fonctionne pas. Toutefois, pour effectuer des transactions sur un système SAP, basée sur le WCF [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] ne prend pas en charge la spécification d’un transport secondaire qui pointe vers un autre serveur SAP.  
  
## <a name="starting-the-application"></a>Démarrage de l’Application  
 Vous devez démarrer l’exécution de transactions BizTalk application d’un système SAP. Pour obtenir des instructions sur le démarrage d’une application BizTalk, consultez [comment démarrer une Orchestration](../../core/how-to-start-an-orchestration.md), [comment démarrer une application](../../core/how-to-start-and-stop-a-biztalk-application.md).
  
 À ce stade, vérifiez que :  
  
-   Le fichier de port de réception pour recevoir des messages de demande pour l’orchestration est en cours d’exécution.  
  
-   Le port d’envoi FILE pour recevoir les messages de réponse à partir de l’orchestration est en cours d’exécution.  
  
-   Le port d’envoi WCF-Custom ou WCF-SAP pour envoyer des messages au système SAP est en cours d’exécution.  
  
-   L’orchestration BizTalk pour l’opération est en cours d’exécution.  
  
## <a name="executing-the-operation"></a>L’exécution de l’opération  
 Après avoir exécuté l’application, vous devez supprimer un message de demande pour l’orchestration à un emplacement prédéfini. Le message de demande doit être conforme à un schéma spécifique, par exemple, MultipleOrders.xsd schéma. Par exemple, un message de demande pour créer des commandes client dans un système SAP, puis pour valider l’opération est :  
  
```  
<ns0:Orders xmlns:ns0="http://BAPISend.MultipleOrders">  
  <Order>  
      <ORDER_HEADER_IN>  
        <DOC_TYPE>TA</DOC_TYPE>  
        <SALES_ORG>1000</SALES_ORG>  
        <DISTR_CHAN>10</DISTR_CHAN>  
        <DIVISION>00</DIVISION>  
        <SALES_OFF>1000</SALES_OFF>  
        <REQ_DATE_H>20060901</REQ_DATE_H>  
        <PURCH_DATE>20060901</PURCH_DATE>  
        <PURCH_NO_C>Cust A</PURCH_NO_C>  
        <CURRENCY>EUR</CURRENCY>  
      </ORDER_HEADER_IN>  
      <ORDER_ITEMS_IN>  
          <MATERIAL>P-109</MATERIAL>  
          <PLANT>1000</PLANT>  
          <TARGET_QU>ST</TARGET_QU>  
      </ORDER_ITEMS_IN>  
      <ORDER_PARTNERS>  
          <PARTN_ROLE>AG</PARTN_ROLE>  
          <PARTN_NUMB>0000000257</PARTN_NUMB>  
      </ORDER_PARTNERS>  
    <RETURN></RETURN>  
  </Order>  
  <isCommit>true</isCommit>  
  <BAPI_TRANSACTION_COMMIT>  
  </BAPI_TRANSACTION_COMMIT>  
</ns0:Orders>  
```  
  
 L’orchestration consomme le message et l’envoie au système SAP. La réponse du système SAP est enregistrée à un autre emplacement de fichier définie dans le cadre de l’orchestration. Pour le message de demande ci-dessus, vous obtenez deux messages de réponse, une pour l’appel de la RFC BAPI_SALESORDER_CREATEFROMDAT2 et l’autre pour l’opération de validation à l’aide de BAPI_TRANSACTION_COMMIT.  
  
 La réponse pour BAPI_SALESORDER_CREATEFROMDAT2 est :  
  
```  
<?xml version="1.0" encoding="utf-8" ?>   
<BAPI_SALESORDER_CREATEFROMDAT2Response xmlns="http://Microsoft.LobServices.Sap/2007/03/Rfc/">  
  <SALESDOCUMENT />   
  <ORDER_ITEMS_IN>  
    <BAPISDITM xmlns="http://Microsoft.LobServices.Sap/2007/03/Types/Rfc/">  
      <ITM_NUMBER>0</ITM_NUMBER>   
      <HG_LV_ITEM>0</HG_LV_ITEM>   
      <PO_ITM_NO />   
      ......  
    </BAPISDITM>  
  </ORDER_ITEMS_IN>  
  <ORDER_PARTNERS>  
    <BAPIPARNR xmlns="http://Microsoft.LobServices.Sap/2007/03/Types/Rfc/">  
      <PARTN_ROLE>AG</PARTN_ROLE>   
      <PARTN_NUMB>0000000257</PARTN_NUMB>   
      <ITM_NUMBER>0</ITM_NUMBER>   
      ......   
    </BAPIPARNR>  
  </ORDER_PARTNERS>  
</BAPI_SALESORDER_CREATEFROMDAT2Response>  
```  
  
 La réponse pour BAPI_TRANSACTION_COMMIT est :  
  
```  
<?xml version="1.0" encoding="utf-8" ?>   
<BAPI_TRANSACTION_COMMITResponse xmlns="http://Microsoft.LobServices.Sap/2007/03/Rfc/">  
  <RETURN>  
    <TYPE xmlns="http://Microsoft.LobServices.Sap/2007/03/Types/Rfc/" />   
    <ID xmlns="http://Microsoft.LobServices.Sap/2007/03/Types/Rfc/" />   
    <NUMBER xmlns="http://Microsoft.LobServices.Sap/2007/03/Types/Rfc/">0</NUMBER>   
    <MESSAGE xmlns="http://Microsoft.LobServices.Sap/2007/03/Types/Rfc/" />   
    <LOG_NO xmlns="http://Microsoft.LobServices.Sap/2007/03/Types/Rfc/" />   
    <LOG_MSG_NO xmlns="http://Microsoft.LobServices.Sap/2007/03/Types/Rfc/">0</LOG_MSG_NO>   
    <MESSAGE_V1 xmlns="http://Microsoft.LobServices.Sap/2007/03/Types/Rfc/" />   
    <MESSAGE_V2 xmlns="http://Microsoft.LobServices.Sap/2007/03/Types/Rfc/" />   
    <MESSAGE_V3 xmlns="http://Microsoft.LobServices.Sap/2007/03/Types/Rfc/" />   
    <MESSAGE_V4 xmlns="http://Microsoft.LobServices.Sap/2007/03/Types/Rfc/" />   
    <PARAMETER xmlns="http://Microsoft.LobServices.Sap/2007/03/Types/Rfc/" />   
    <ROW xmlns="http://Microsoft.LobServices.Sap/2007/03/Types/Rfc/">0</ROW>   
    <FIELD xmlns="http://Microsoft.LobServices.Sap/2007/03/Types/Rfc/" />   
    <SYSTEM xmlns="http://Microsoft.LobServices.Sap/2007/03/Types/Rfc/" />   
  </RETURN>  
</BAPI_TRANSACTION_COMMITResponse>  
```  
  
> [!NOTE]
>  Si le message de requête appelé le RFC BAPI_TRANSACTION_ROLLBACK, la seconde réponse sera pour BAPI_TRANSACTION_ROLLBACK.  
  
## <a name="possible-exceptions"></a>Exceptions possibles  
 Pour plus d’informations sur les exceptions que vous pouvez rencontrer lors de l’exécution des transactions sur un système SAP à l’aide de BizTalk Server, consultez [Exceptions et gestion des erreurs avec l’adaptateur SAP](../../adapters-and-accelerators/adapter-sap/exceptions-and-error-handling-with-the-sap-adapter.md).  
  
## <a name="best-practices"></a>Bonnes pratiques  
 Après avoir déployé et configuré le projet BizTalk, vous pouvez exporter les paramètres de configuration dans un fichier XML appelé le fichier de liaisons. Une fois que vous générez un fichier de liaison, vous pouvez importer les paramètres de configuration à partir du fichier afin que vous n’avez pas besoin de créer les ports d’envoi et de réception, de l’orchestration même. Pour plus d’informations sur les fichiers de liaison, consultez [liaisons de l’adaptateur SAP de réutiliser](../../adapters-and-accelerators/adapter-sap/reuse-sap-adapter-bindings.md).  
  
## <a name="see-also"></a>Voir aussi  
[Développer des applications BizTalk](../../adapters-and-accelerators/adapter-sap/develop-biztalk-applications-using-the-sap-adapter.md)