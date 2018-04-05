---
title: Appeler des fonctions surchargées et les procédures de base de données Oracle à l’aide de BizTalk Server | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- overloaded functions and procedures, invoking by using BizTalk Server
ms.assetid: a3d76361-6b0c-415a-b4f9-31939abfdc36
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 30d036313a69025e7fcf0e37116fc729623ac782
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="invoke-overloaded-functions-and-procedures-in-oracle-database-using-biztalk-server"></a>Appeler des fonctions surchargées et les procédures de base de données Oracle à l’aide de BizTalk Server
Fonctions et procédures stockées peuvent être surchargées dans une base de données Oracle. Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] prend en charge surchargé des fonctions et procédures en modifiant l’espace de noms cible de l’opération. Par exemple, la structure du message pour les deux procédures surchargées ressemble à :  
  
```  
Stored Procedure Overload 1:  
<[SP_NAME] xmlns="http://Microsoft.LobServices.OracleDB/2007/03/[SCHEMA]/Package/[PACKAGE_NAME]/[SP_NAME]/overload1">    
  <[PRM1_NAME]>value1</[PRM1_NAME]>  
  <[PRM2_NAME]>value1</[PRM2_NAME]>  
  …  
</[SP_NAME]>  
  
Stored Procedure Overload 2:  
<[SP_NAME] xmlns="http://Microsoft.LobServices.OracleDB/2007/03/[SCHEMA]/Package/[PACKAGE_NAME]/[SP_NAME]/overload2">    
  <[PRM1_NAME]>value1</I_[PRM1_NAME]>  
  <[PRM2_NAME]>value1</I_[PRM2_NAME]>  
  …  
</[SP_NAME]>  
```  
  
 La structure du message SOAP et l’action SOAP requis pour appeler une fonction surchargée ou la procédure est similaire à l’appel d’une fonction et la procédure, comme indiqué dans [des schémas de Message pour les fonctions et procédures](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-functions-and-procedures.md).  
  
 L’appel d’une procédure surchargée est similaire à l’appel de toute autre fonction comme décrit dans [appeler les fonctions et les procédures de base de données Oracle à l’aide de BizTalk Server](../../adapters-and-accelerators/adapter-oracle-database/invoke-functions-and-procedures-in-oracle-database-using-biztalk-server.md). Toutefois, pour différencier les fonctions, surchargées le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] ajoute une chaîne unique à l’ID de nœud et l’espace de noms pour l’artefact surchargé il met en évidence. Cette chaîne est « overload1 » pour la première surcharge, « overload2 » pour la surcharge suivante et ainsi de suite.  
  
## <a name="how-to-invoke-overloaded-functions-and-procedures"></a>Explique comment appeler des procédures et fonctions surchargées ?  
 Une opération sur une base de données Oracle à l’aide [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] avec [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] implique les tâches de procédures décrites dans [blocs de construction pour développer des Applications BizTalk avec la base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/building-blocks-to-develop-biztalk-applications-with-oracle-database.md). Pour appeler une fonction dans une base de données Oracle, ces tâches sont :  
  
1.  Créez un projet BizTalk et générer le schéma de la fonction surchargée que vous souhaitez appeler dans une base de données Oracle.  
  
2.  Créer des messages dans le projet BizTalk pour envoyer et recevoir des messages à partir de la base de données Oracle. Vous devez créer des messages pour chaque surcharge.  
  
3.  Créez une orchestration pour appeler la fonction surchargée dans la base de données Oracle.  
  
4.  Générez et déployez le projet BizTalk.  
  
5.  Configurer l’application en créant physique d’envoi et ports de réception BizTalk.  
  
6.  Démarrez l’application BizTalk.  
  
 Cette rubrique fournit des instructions pour effectuer ces tâches.  
  
## <a name="sample-based-on-this-topic"></a>Exemple basé sur cette rubrique  
 Un exemple, InvokeOverloadedProc, en fonction de cette rubrique est également fourni avec le [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]. Pour plus d’informations, consultez [exemples d’adaptateur](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md).  
  
## <a name="generating-schema"></a>Génération du schéma  
 Dans cette rubrique, pour illustrer comment appeler une fonction surchargée ou une procédure, nous appellerons la procédure GET_ACCOUNT sous le schéma SCOTT\Package\ACCOUNT_PKG. Ce package est créé sous le schéma SCOTT en exécutant les scripts SQL fournis avec les exemples. Il s’agit d’une procédure surchargée où :  
  
-   Une surcharge prend l’ID de compte en tant que paramètre IN et retourne un compte % ROWTYPE comme paramètre de sortie.  
  
-   Deuxième surcharge prend le nom de compte en tant que paramètre IN et retourne un compte % ROWTYPE comme paramètre de sortie.  
  
 Pour en savoir plus sur les exemples et les scripts SQL, consultez [exemples de schéma](../../adapters-and-accelerators/accelerator-rosettanet/schema-samples.md).  
  
 Pour appeler une fonction surchargée, nous génération du schéma pour les deux les procédures surchargées, GET_ACCOUNT.1 et GET_ACCOUNT.2. Consultez [de récupérer les métadonnées pour les opérations de base de données Oracle dans Visual Studio](../../adapters-and-accelerators/adapter-oracle-database/get-metadata-for-oracle-database-operations-in-visual-studio.md) pour plus d’informations sur la génération de schéma.  
  
## <a name="defining-messages-and-message-types"></a>Définition des Messages et les Types de messages  
 Le schéma que vous avez généré précédemment décrit les « types » requis pour les messages dans l’orchestration. Un message est généralement une variable, le type est défini par le schéma correspondant. Vous devez lier le schéma généré à la première étape pour les messages à partir de la fenêtre Vue Orchestration du projet BizTalk.  
  
 Cette rubrique, vous devez créer deux jeux de message de demande-réponse, une requête-réponse définie pour la première surcharge procédure et la deuxième demande-réponse est définie pour la deuxième procédure surchargée.  
  
 Procédez comme suit pour créer des messages et les lier au schéma.  
  
#### <a name="to-create-messages-and-link-to-schema"></a>Pour créer des messages et le lier au schéma  
  
1.  Ouvrez la fenêtre Vue Orchestration du projet BizTalk, s’il n’est pas déjà ouvert. Pour ce faire, cliquez sur **vue**, pointez sur **autres fenêtres**, puis cliquez sur **Vue Orchestration**.  
  
2.  Dans la vue Orchestration, cliquez sur **Messages**, puis cliquez sur **nouveau Message**.  
  
3.  Cliquez sur le message qui vient d’être créé, puis sélectionnez **fenêtre Propriétés**.  
  
4.  Dans le **propriétés** volet pour **Message_1**, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |Identificateur|Type **demande**.|  
    |Type de message|Dans la liste déroulante, développez **schémas**, puis sélectionnez *InvokeOverloadedProc.OracleDBBindingSchema.GET_ACCOUNT*, où *InvokeOverloadedProc* est le nom de votre projet BizTalk. *OracleDBBindingSchema* est le schéma généré pour la procédure GET_ACCOUNT.|  
  
5.  Répétez l’étape précédente pour créer plus de trois messages. Dans le **propriétés** volet pour les nouveaux messages, procédez comme suit :  
  
    |Identificateur de la valeur|Définissez le Type de Message|  
    |-----------------------|-------------------------|  
    |Réponse|*InvokeOverloadedProc.OracleDBBindingSchema.GET_ACCOUNTResponse*|  
    |MAX2|*InvokeOverloadedProc.OracleDBBindingSchema1.GET_ACCOUNT*|  
    |Réponse aux menaces2|*InvokeOverloadedProc.OracleDBBindingSchema1.GET_ACCOUNTResponse*|  
  
## <a name="setting-up-the-orchestration"></a>Configuration de l’Orchestration  
 Vous devez créer une orchestration BizTalk à utiliser [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] pour appeler une procédure surchargée dans une base de données Oracle. Dans cette orchestration, vous supprimez deux messages de demande, un pour chaque procédure surchargée, à la période définie par l’emplacement de réception. Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] consomme les messages et les transmet à la base de données Oracle via ODP. La réponse à partir de la base de données Oracle est enregistrée dans un autre emplacement.  
  
 Étant donné que l’orchestration récupère simultanément les deux requêtes, vous devez inclure une forme Actions parallèles dans l’orchestration. Pour chaque action parallèle, vous devez inclure les envoyer et recevoir des formes pour envoyer des messages à la base de données Oracle et de recevoir des réponses. Toutefois, vous pouvez utiliser les mêmes ports pour envoyer et recevoir des messages pour les deux opérations. Contiendrait une orchestration classique pour appeler les procédures surchargées simultanément :  
  
-   Envoyer et recevoir des formes pour envoyer des messages à la base de données Oracle et de recevoir des réponses.  
  
-   Port pour recevoir des messages de demande à envoyer à la base de données Oracle de réception unidirectionnel.  
  
-   Un double port d’envoi pour envoyer des messages de demande à Oracle de base de données et recevoir des réponses.  
  
-   Un port d’envoi unidirectionnel pour envoyer les réponses à partir de la base de données Oracle dans un dossier.  
  
 Un exemple d’orchestration à appeler la surcharge premier et deuxième procédure GET_ACCOUNT ressemble à ceci :  
  
 ![Orchestration permettant d’appeler des lots surchargés](../../adapters-and-accelerators/adapter-oracle-database/media/f8e4ad6f-9140-43b1-b931-28c9ba11cc8e.gif "f8e4ad6f-9140-43b1-b931-28c9ba11cc8e")  
  
### <a name="adding-message-shapes"></a>Ajouter des formes de Message  
 Assurez-vous que vous spécifiez les propriétés suivantes pour chacune des formes de message. Les noms répertoriés dans la colonne de forme sont les noms des formes de message tel qu’affiché dans l’orchestration juste-mentionné. Le tableau suivant répertorie les formes, que vous devez inclure pour l’une des actions parallèles.  
  
|Graphique à base de formes|Type de forme|Propriétés|  
|-----------|----------------|----------------|  
|ReceiveMessage|Recevoir|-Définissez **nom** à *ReceiveMessage*<br />-Définissez **activer** à *True*|  
|SendMessage|Send|-Définissez **nom** à *SendMessage*|  
|Réception réponse|Recevoir|-Définissez **nom** à *ReceiveResponse*<br />-Définissez **activer** à *False*|  
|SendResponse|Send|-Définissez **nom** à *SendResponse*|  
  
 Le tableau suivant répertorie les formes que vous devez inclure pour l’autre action parallèle.  
  
|Graphique à base de formes|Type de forme|Propriétés|  
|-----------|----------------|----------------|  
|ReceiveMessage2|Recevoir|-Définissez **nom** à *ReceiveMessage2*<br />-Définissez **activer** à *True*|  
|SendMessage2|Send|-Définissez **nom** à *SendMessage2*|  
|ReceiveResponse2|Recevoir|-Définissez **nom** à *ReceiveResponse2*<br />-Définissez **activer** à *False*|  
|SendResponse2|Send|-Définissez **nom** à *SendResponse2*|  
  
### <a name="adding-ports"></a>Ajout de Ports  
 Assurez-vous que vous spécifiez les propriétés suivantes pour chacun des ports logiques. Les noms répertoriés dans la colonne de Port sont les noms des ports tel qu’affiché dans l’orchestration.  
  
|Port|Propriétés|  
|----------|----------------|  
|Fichier|-Définissez **identificateur** à *FileIn*<br />-Définissez **Type** à *FileInType*<br />-Définissez **modèle de Communication** à *à sens unique*<br />-Définissez **Direction de Communication** à *de réception*|  
|LOBPort|-Définissez **identificateur** à *LOBPort*<br />-Définissez **Type** à *LOBPortType*<br />-Définissez **modèle de Communication** à *demande-réponse*<br />-Définissez **Direction de Communication** à *envoi / réception*|  
|SaveResponse|-Définissez **identificateur** à *SaveResponse*<br />-Définissez **Type** à *SaveResponseType*<br />-Définissez **modèle de Communication** à *à sens unique*<br />-Définissez **Direction de Communication** à *envoyer*|  
  
 Étant donné que vous allez traiter deux requêtes et les messages de réponse à l’aide de ces ports, vous devez créer deux opérations pour chaque port, où chaque opération correspond à un type de message. Pour créer une opération, avec le bouton droit de la forme port, puis **nouvelle opération**. Nom de la première opération pour chaque port en tant que **Overload1** et la seconde opération pour chaque port en tant que **Overload2**.  
  
### <a name="using-correlation"></a>Utilisation de la corrélation  
 La corrélation est le processus de mise en correspondance d'un message entrant et de l'instance appropriée d'une orchestration. Dans l’orchestration que vous sera envoyé par lots deux messages de demande, un pour chaque surcharge. Utilisation de la corrélation, vous associez un message de demande l’orchestration à droite. Pour plus d’informations sur la corrélation, consultez [à l’aide de corrélations dans les Orchestrations](../../core/using-correlations-in-orchestrations.md).  
  
##### <a name="to-use-correlations"></a>Pour utiliser des corrélations  
  
1.  Promouvoir une propriété à partir du schéma généré pour chaque fonction surchargée. Par exemple, de promouvoir la propriété de l’aide à partir du schéma pour la première surcharge ; promouvoir la propriété ANAME à partir du schéma de la deuxième surcharge. Pour promouvoir une propriété, avec le bouton droit de la propriété dans la vue schéma, pointez sur **promouvoir**, puis sélectionnez **Promotion rapide**. Cela ajoute un fichier PropertySchema.xsd à votre projet BizTalk.  
  
     Pour plus d’informations sur la promotion d’une propriété, consultez [promotion des propriétés](../../core/promoting-properties.md).  
  
2.  À partir de la vue Orchestration, cliquez sur **Types de corrélations**, puis sélectionnez **nouveau Type de corrélation**.  
  
3.  Le **propriétés de corrélation** boîte de dialogue répertorie les propriétés que vous avez promu à l’étape 1. Sélectionnez une propriété, puis cliquez sur **ajouter**.  
  
4.  Cliquez sur **OK**.  
  
5.  Pour créer des types de corrélations pour la propriété promue, répétez ces étapes.  
  
6.  Renommez les types de corrélation basées sur la propriété à laquelle elles sont associées. Vous pouvez renommer les types de corrélations pour *CorrelationType_AID* (pour la propriété aide) et *CorrelationType_ANAME* (pour la propriété ANAME).  
  
7.  À partir de la vue Orchestration, cliquez sur **des ensembles de corrélations**, puis sélectionnez **nouvel ensemble de corrélations**.  
  
8.  Avec le bouton droit de l’ensemble de corrélations nouvellement ajoutée, puis cliquez sur **propriétés**. Dans le volet Propriétés, effectuez les opérations suivantes :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |Type de corrélation|*InvokeOverloadedProc.CorrelationType_AID*|  
    |Identificateur|*Correlation_AID*|  
  
9. Ajouter un autre ensemble de corrélations et spécifiez les propriétés suivantes à partir du volet Propriétés.  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |Type de corrélation|*InvokeOverloadedProc.CorrelationType_ANAME*|  
    |Identificateur|*Correlation_ANAME*|  
  
## <a name="specify-messages-for-action-shapes-and-connect-them-to-ports"></a>Spécifier des Messages pour les formes d’Action et connectez-les aux Ports  
 Le tableau suivant indique les propriétés et leurs valeurs, vous devez définir pour spécifier les messages de formes d’action et lier les messages aux ports. Les noms répertoriés dans la colonne de forme sont les noms des formes de message tel qu’affiché dans l’orchestration mentionnée précédemment.  
  
|Graphique à base de formes|Propriétés|  
|-----------|----------------|  
|ReceiveMessage|-Définissez **l’initialisation des ensembles de corrélations** à *Correlation_AID*<br />-Définissez **Message** à *demande*<br />-Définissez **opération** à *FileIn.Overload1.Request*|  
|SendMessage|-Définissez **Message** à *demande*<br />-Définissez **opération** à *LOBPort.Overload1.Request*|  
|Réception réponse|-Définissez **Message** à *réponse*<br />-Définissez **opération** à *LOBPort.Overload1.Response*|  
|SendResponse|-Définissez **Message** à *réponse*<br />-Définissez **opération** à *SaveResponse.Overload1.Request*|  
|ReceiveMessage2|-Définissez **l’initialisation des ensembles de corrélations** à *Correlation_ANAME*<br />-Définissez **Message** à *MAX2*<br />-Définissez **opération** à *FileIn.Overload2.Request*|  
|SendMessage2|-Définissez **Message** à *MAX2*<br />-Définissez **opération** à *LOBPort.Overload2.Request*|  
|ReceiveResponse2|-Définissez **Message** à *réponse aux menaces2*<br />-Définissez **opération** à *LOBPort.Overload2.Response*|  
|SendResponse2|-Définissez **Message** à *réponse aux menaces2*<br />-Définissez **opération** à *SaveResponse.Overload2.Request*|  
  
 Une fois que vous avez défini ces propriétés, les formes de message et les ports sont connectés et l’orchestration est terminée.  
  
 Vous devez maintenant générer la solution BizTalk et déployez-le dans un [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]. Pour plus d’informations, consultez [génération et exécution des Orchestrations](../../core/building-and-running-orchestrations.md).  
  
## <a name="configuring-the-biztalk-application"></a>Configuration de l’Application BizTalk  
 Après avoir déployé le projet BizTalk, l’orchestration que vous avez créé précédemment est répertoriée sous le **Orchestrations** volet de la console Administration de BizTalk Server. Vous devez utiliser la console Administration de BizTalk Server pour configurer l’application. Pour une procédure pas à pas, consultez [procédure pas à pas : déploiement d’une Application BizTalk base](Walkthrough:%20Deploying%20a%20Basic%20BizTalk%20Application.md).
  
 Configuration d’une application implique :  
  
-   Sélection d’un hôte de l’application.  
  
-   Mappage de ports que vous avez créé dans l’orchestration aux ports physiques dans la console Administration de BizTalk Server. Pour cette orchestration, vous devez :  
  
    -   Définir un emplacement sur le disque dur et un port de fichier correspondant où vous allez déposer les messages de demande, une pour chaque procédure surchargée. L’orchestration BizTalk consommer les messages de demande et l’envoyer à la base de données Oracle.  
  
    -   Définir un emplacement sur le disque dur et un port de fichier correspondant dans lequel l’orchestration BizTalk supprime les messages de réponse, une pour chaque procédure surchargée, qui contient la réponse à partir de la base de données Oracle.  
  
    -   Définir un port d’envoi WCF-Custom ou WCF-OracleDB physique pour envoyer des messages à la base de données Oracle. Vous devez également spécifier l’action dans le port d’envoi. Pour plus d’informations sur la création des ports WCF-Custom ou WCF-OracleDB, consultez [configurer manuellement une liaison de port physique à l’adaptateur de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/manually-configure-a-physical-port-binding-to-the-oracle-database-adapter.md). Car le WCF-Custom ou WCF-OracleDB port d’envoi envoie et recevoir des messages conformes à plusieurs schémas et effectue deux opérations, vous devez définir une action dynamique pour les opérations. Pour plus d’informations sur les actions, consultez [configurer l’action SOAP pour la base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/configure-the-soap-action-for-oracle-database.md). Pour cette orchestration, l’action doit être définie comme suit :  
  
        ```  
        <BtsActionMapping>  
          <Operation Name="Overload1" Action="http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Package/ACCOUNT_PKG/GET_ACCOUNT/overload1" />  
          <Operation Name="Overload2" Action="http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Package/ACCOUNT_PKG/GET_ACCOUNT/overload2" />  
        </BtsActionMapping>  
        ```  
  
        > [!NOTE]
        >  Génération de schéma à l’aide du [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] crée également un fichier de liaison contenant des informations sur les ports et les actions à définir pour ces ports. Vous pouvez importer ce fichier de liaison à partir de la console Administration de BizTalk Server pour créer des ports d’envoi (pour les appels sortants) ou de ports de réception (d’appels entrants). Pour plus d’informations, consultez [configurer une liaison de port physique à l’aide d’un fichier de liaison de port pour la base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/configure-a-physical-port-binding-using-a-port-binding-file-to-oracle-database.md).  
  
## <a name="starting-the-application"></a>Démarrage de l’Application  
 Vous devez démarrer l’application BizTalk permettant d’appeler une fonction dans une table de base de données Oracle. Pour obtenir des instructions sur le démarrage d’une application BizTalk, consultez [comment démarrer une Orchestration](../../core/how-to-start-an-orchestration.md).  
  
 À ce stade, vérifiez que :  
  
-   Le fichier de port de réception pour recevoir des messages de demande pour l’orchestration est en cours d’exécution.  
  
-   Le port d’envoi FILE pour recevoir les messages de réponse à partir de l’orchestration est en cours d’exécution.  
  
-   Le port d’envoi WCF-Custom ou WCF-OracleDB à envoyer des messages à la base de données Oracle est en cours d’exécution.  
  
-   L’orchestration BizTalk pour l’opération est en cours d’exécution.  
  
## <a name="executing-the-operation"></a>L’exécution de l’opération  
 Après avoir exécuté l’application, vous devez supprimer deux demande d’emplacement de réception de messages (une pour chaque procédure surchargée) dans le fichier. Le schéma pour les messages de demande doit être conforme au schéma pour la procédure que vous avez généré précédemment. Consultez [des schémas de Message pour les fonctions et procédures](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-functions-and-procedures.md) pour plus d’informations sur le schéma de message de demande pour l’appel de fonctions à l’aide de la [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].  
  
 Par exemple, le message de demande pour appeler la première surcharge de la procédure GET_ACCOUNT est la suivante :  
  
```  
<GET_ACCOUNT xmlns="http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Package/ACCOUNT_PKG/GET_ACCOUNT/overload1">  
  <AID>100001</AID>  
</GET_ACCOUNT>  
```  
  
 De même, le message de demande pour appeler la deuxième surcharge de la procédure GET_ACCOUNT est :  
  
```  
<GET_ACCOUNT xmlns="http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Package/ACCOUNT_PKG/GET_ACCOUNT/overload2">  
  <ANAME>Mindy Martin</ANAME>  
</GET_ACCOUNT>  
```  
  
 Le premier message de demande appelle la procédure GET_ACCOUNT pour récupérer l’enregistrement avec l’ID de compte égal à 100020. Le deuxième message de demande appelle la procédure GET_ACCOUNT pour récupérer les enregistrements ayant le nom du compte en tant que « John Smith ».  
  
 L’orchestration consomme les messages de requête et les envoie à la base de données Oracle. La réponse à partir de la base de données Oracle est enregistrée à un autre emplacement de fichier définie dans le cadre de l’orchestration. Par exemple, la réponse pour l’appel de la première procédure surchargée est :  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<GET_ACCOUNTResponse mlns="http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Package/ACCOUNT_PKG/GET_ACCOUNT/overload1">  
 <ACCT>  
  <ACCTID>100001</ACCTID>  
  <NAME>Ty Carlson</NAME>  
  <BALANCE>9000</BALANCE>  
 </ACCT>  
</GET_ACCOUNTResponse>  
```  
  
## <a name="possible-exceptions"></a>Exceptions possibles  
 Pour plus d’informations sur les exceptions, vous pouvez rencontrer lors de l’appel des packages surchargés à l’aide de [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], consultez [Exceptions et gestion des erreurs](../../adapters-and-accelerators/adapter-oracle-database/exceptions-and-error-handling-with-the-oracle-database-adapter.md).  
  
## <a name="best-practices"></a>Bonnes pratiques  
 Après avoir déployé et configuré le projet BizTalk, vous pouvez exporter les paramètres de configuration dans un fichier XML appelé le fichier de liaisons. Une fois que vous générez un fichier de liaison, vous pouvez importer les paramètres de configuration à partir du fichier afin que vous n’avez pas besoin de créer les ports d’envoi, ports, etc. pour la même orchestration de réception. Pour plus d’informations sur les fichiers de liaison, consultez [liaisons de l’adaptateur de base de données Oracle de réutiliser](../../adapters-and-accelerators/adapter-oracle-database/reuse-oracle-database-adapter-bindings.md).  
  
## <a name="see-also"></a>Voir aussi  
[Blocs de construction pour les applications BizTalk de développer la base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/building-blocks-to-develop-biztalk-applications-with-oracle-database.md)