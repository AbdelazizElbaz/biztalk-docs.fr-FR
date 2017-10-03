---
title: "Exécuter des opérations sur les tables avec des types de données dans la base de données Oracle | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- operations, performing on tables
- operations, performing on LOB data
ms.assetid: 74276b85-daf1-4d0f-92f9-46d5c27a95a6
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6d01593fb50fd1b6faf851652319628b3d0cae58
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="run-operations-on-tables-with-large-object-data-types-in-oracle-database"></a>Exécuter des opérations sur les tables avec des types de données dans la base de données Oracle
Le [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] prend en charge les types de données Oracle LOB (large object) :  
  
-   Objet binaire volumineux (BLOB)  
  
-   Grand objet CLOB (Character)  
  
-   Objet volumineux de caractères nationaux (NCLOB)  
  
-   Fichier binaire (BFILE). Pour plus d’informations, consultez [effectuant des opérations sur les Tables avec des Types de données BFILE dans la base de données Oracle à l’aide de BizTalk Server](../../adapters-and-accelerators/adapter-oracle-database/run-operations-on-tables-with-bfile-data-types-in-oracle-db-using-biztalk.md).  
  
 Le [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] cela signale les opérations ReadLOB et UpdateLOB pour les tables qui contiennent des colonnes LOB. Pour plus d’informations sur ces opérations, consultez [opérations sur les Tables et vues que contiennent LOB des données dans la base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/operations-on-tables-and-views-that-contain-lob-data-in-oracle-database.md). Pour plus d’informations sur la structure du message SOAP pour l’appel de ces opérations, consultez [des schémas de Message pour des opérations spéciales LOB](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-special-lob-operations2.md).  
  
> [!NOTE]
>  Lorsque vous utilisez la [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] avec [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], l’opération ReadLOB ne prend pas en charge les données de type LOB diffusion en continu à partir d’une base de données Oracle. Pour diffuser des données LOB à partir d’une base de données Oracle à l’aide [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] vous devez utiliser à la place de l’opération Select. Pour plus d’informations sur la diffusion en continu, consultez [prise en charge de diffusion en continu pour les Types de données dans la base de données Oracle LOB](../../adapters-and-accelerators/adapter-oracle-database/streaming-support-for-lob-data-types-in-oracle-database.md). En outre, la réponse à partir de la base de données Oracle pour l’opération ReadLOB validation échoue sur le fichier WSDL. Pour obtenir des instructions sur la procédure pour résoudre l’échec, consultez [résolution des problèmes opérationnels](https://msdn.microsoft.com/library/dd787883.aspx).  
  
## <a name="how-to-perform-operations-on-lob-data"></a>Comment effectuer des opérations sur des données LOB ?  
 Une opération sur une base de données Oracle à l’aide [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] avec [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] implique les tâches de procédures décrites dans [blocs de construction pour développer des Applications BizTalk avec la base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/building-blocks-to-develop-biztalk-applications-with-oracle-database.md). Pour appeler des opérations ReadLOB et UpdateLOB sur une table dans une base de données Oracle, ces tâches sont :  
  
1.  Créez un projet BizTalk et générer le schéma pour les opérations ReadLOB et UpdateLOB.  
  
2.  Créer des messages dans le projet BizTalk pour envoyer et recevoir des messages à partir de la base de données Oracle. Vous devez créer des messages pour l’envoi demande et de recevoir des réponses pour les opérations.  
  
3.  Créez une orchestration pour appeler des opérations ReadLOB et UpdateLOB.  
  
4.  Générez et déployez le projet BizTalk.  
  
5.  Configurer l’application en créant physique d’envoi et ports de réception BizTalk.  
  
6.  Démarrez l’application BizTalk.  
  
 Cette rubrique fournit des instructions pour effectuer ces tâches.  
  
## <a name="sample-based-on-this-topic"></a>Exemple basé sur cette rubrique  
 Un exemple, Operate_LOB, en fonction de cette rubrique est également fourni avec le [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]. Pour plus d’informations, consultez [exemples d’adaptateur](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md).  
  
## <a name="generating-schema"></a>Génération du schéma  
 Dans cette rubrique, pour montrer comment effectuer des opérations ReadLOB et UpdateLOB, nous allons générer des métadonnées pour ces opérations signalées pour la table CUSTOMER sous le schéma SCOTT dans la base de données Oracle. Cette table est créée sous le schéma SCOTT en exécutant les scripts SQL fournis avec les exemples. Pour en savoir plus sur les exemples, consultez [exemples de schéma](../../adapters-and-accelerators/accelerator-rosettanet/schema-samples.md).  
  
## <a name="defining-messages-and-message-types"></a>Définition des Messages et les Types de messages  
 Le schéma que vous avez généré précédemment décrit les « types » requis pour les messages dans l’orchestration. Un message est généralement une variable, le type est défini par le schéma correspondant. Vous devez lier le schéma généré à la première étape pour les messages à partir de la fenêtre Vue Orchestration du projet BizTalk.  
  
 Cette rubrique, vous devez créer deux jeux de message de demande-réponse, une demande-réponse définie pour l’opération ReadLOB et la deuxième requête-réponse défini pour l’opération UpdateLOB.  
  
 Procédez comme suit pour créer des messages et les lier au schéma.  
  
#### <a name="to-create-messages-and-link-to-schema"></a>Pour créer des messages et le lier au schéma  
  
1.  Ouvrez la fenêtre Vue Orchestration du projet BizTalk, s’il n’est pas déjà ouvert. Pour ce faire, cliquez sur **vue**, pointez sur **autres fenêtres**, puis cliquez sur **Vue Orchestration**.  
  
2.  Dans la vue Orchestration, cliquez sur **Messages**, puis cliquez sur **nouveau Message**.  
  
3.  Cliquez sur le message qui vient d’être créé, puis sélectionnez **fenêtre Propriétés**.  
  
4.  Dans le **propriétés** volet pour **Message_1**, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |Identificateur|Type **demande**.|  
    |Type de message|Dans la liste déroulante, développez **schémas**, puis sélectionnez *Operate_LOB. OracleDBBindingSchema.ReadLOB**,* où *Operate_LOB* est le nom de votre projet BizTalk. *OracleDBBindingSchema* est le schéma généré pour les opérations ReadLOB et UpdateLOB sur la table CUSTOMER.|  
  
5.  Répétez l’étape précédente pour créer plus de trois messages. Dans le **propriétés** volet pour les nouveaux messages, procédez comme suit :  
  
    |Identificateur de la valeur|Définissez le Type de Message|  
    |-----------------------|-------------------------|  
    |Réponse|*Operate_LOB. OracleDBBindingSchema.ReadLOBResponse*|  
    |MAX2|*Operate_LOB. OracleDBBindingSchema.UpdateLOB*|  
    |Réponse aux menaces2|*Operate_LOB. OracleDBBindingSchema.UpdateLOBResponse*|  
  
## <a name="setting-up-the-orchestration"></a>Configuration de l’Orchestration  
 Vous devez créer une orchestration BizTalk à utiliser [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] pour appeler des opérations ReadLOB et UpdateLOB sur une table. Cette orchestration, vous permet de supprimer les deux messages de demande, une pour l’opération ReadLOB et l’autre pour l’opération UpdateLOB. Ces messages sont supprimés à un emplacement de réception. Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] consomme les messages et les transmet à la base de données Oracle via ODP. La réponse à partir de la base de données Oracle est enregistrée dans un autre emplacement.  
  
 Étant donné que l’orchestration récupère simultanément les deux requêtes, vous devez inclure une forme Actions parallèles dans l’orchestration. Pour chaque action parallèle, vous devez inclure les envoyer et recevoir des formes pour envoyer des messages à la base de données Oracle et de recevoir des réponses. Toutefois, vous pouvez utiliser les mêmes ports pour envoyer et recevoir des messages pour les deux opérations. Contiendrait une orchestration classique pour effectuer les opérations ReadLOB et UpdateLOB simultanément :  
  
-   Envoyer et recevoir des formes pour envoyer des messages à la base de données Oracle et de recevoir des réponses.  
  
-   Port pour recevoir des messages de demande à envoyer à la base de données Oracle de réception unidirectionnel.  
  
-   Un double port d’envoi pour envoyer des messages de demande à Oracle de base de données et recevoir des réponses.  
  
-   Un port d’envoi unidirectionnel pour envoyer les réponses à partir de la base de données Oracle dans un dossier.  
  
 Un exemple d’orchestration ressemble à ceci :  
  
 ![Orchestration pour la lecture et mise à jour des données LOB](../../adapters-and-accelerators/adapter-oracle-database/media/6523b5e4-3689-433a-8287-eebc36f10442.gif "6523b5e4-3689-433a-8287-eebc36f10442")  
  
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
  
 Étant donné que vous allez traiter deux requêtes et les messages de réponse à l’aide de ces ports, vous devez créer deux opérations pour chaque port, où chaque opération correspond à un type de message. Pour créer une opération, avec le bouton droit de la forme port, puis **nouvelle opération**. Nom de la première opération pour chaque port en tant que **ReadLOB** et la seconde opération pour chaque port en tant que **UpdateLOB**.  
  
### <a name="using-correlation"></a>Utilisation de la corrélation  
 La corrélation est le processus de mise en correspondance d'un message entrant et de l'instance appropriée d'une orchestration. Dans l’orchestration que vous sera envoyé par lots deux messages de demande, un pour chaque surcharge. Utilisation de la corrélation, vous associez un message de demande l’orchestration à droite. Pour plus d’informations sur la corrélation, consultez [à l’aide de corrélations dans les Orchestrations](../../core/using-correlations-in-orchestrations.md).  
  
##### <a name="to-use-correlations"></a>Pour utiliser des corrélations  
  
1.  Promouvoir une propriété à partir du schéma généré pour chaque opération. Par exemple, de promouvoir la propriété LOB_COLUMN à partir du schéma d’opération ReadLOB ; promouvoir la propriété de filtre à partir du schéma d’opération UpdateLOB. Pour promouvoir une propriété, avec le bouton droit de la propriété dans la vue schéma, pointez sur **promouvoir**, puis sélectionnez **Promotion rapide**. Cela ajoute un fichier PropertySchema.xsd à votre projet BizTalk.  
  
     Pour plus d’informations sur la promotion d’une propriété, consultez [promotion des propriétés](../../core/promoting-properties.md).  
  
2.  À partir de la vue Orchestration, cliquez sur **Types de corrélations**, puis sélectionnez **nouveau Type de corrélation**.  
  
3.  Le **propriétés de corrélation** boîte de dialogue répertorie les propriétés que vous avez promu à l’étape 1. Sélectionnez une propriété, puis cliquez sur **ajouter**.  
  
4.  Cliquez sur **OK**.  
  
5.  Pour créer des types de corrélations pour la propriété promue, répétez ces étapes.  
  
6.  Renommez les types de corrélation en fonction de l’opération à que laquelle ils sont associés. Vous pouvez renommer les types de corrélations pour *CorrelationType_ReadLOB* (pour l’opération ReadLOB) et *CorrelationType_UpdateLOB* (pour l’opération UpdateLOB).  
  
7.  À partir de la vue Orchestration, cliquez sur **des ensembles de corrélations**, puis sélectionnez **nouvel ensemble de corrélations**.  
  
8.  Avec le bouton droit de l’ensemble de corrélations nouvellement ajoutée, puis cliquez sur **propriétés**. Dans le **propriétés** volet, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |Type de corrélation|*Operate_LOB. CorrelationType_ReadLOB*|  
    |Identificateur|*Correlation_ReadLOB*|  
  
9. Ajouter un autre ensemble de corrélations et spécifiez les propriétés suivantes à partir du volet Propriétés.  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |Type de corrélation|*Operate_LOB. CorrelationType_UpdateLOB*|  
    |Identificateur|*Correlation_UpdateLOB*|  
  
## <a name="specify-messages-for-action-shapes-and-connect-them-to-ports"></a>Spécifier des Messages pour les formes d’Action et connectez-les aux Ports  
 Le tableau suivant indique les propriétés et leurs valeurs, vous devez définir pour spécifier les messages de formes d’action et les lier aux ports. Les noms répertoriés dans la colonne de forme sont les noms des formes de message tel qu’affiché dans l’orchestration mentionnée précédemment.  
  
|Graphique à base de formes|Propriétés|  
|-----------|----------------|  
|ReceiveMessage|-Définissez **l’initialisation des ensembles de corrélations** à *Correlation_ReadLOB*<br />-Définissez **Message** à *demande*<br />-Définissez **opération** à *FileIn.ReadLOB.Request*|  
|SendMessage|-Définissez **Message** à *demande*<br />-Définissez **opération** à *LOBPort.ReadLOB.Request*|  
|Réception réponse|-Définissez **Message** à *réponse*<br />-Définissez **opération** à *LOBPort.ReadLOB.Response*|  
|SendResponse|-Définissez **Message** à *réponse*<br />-Définissez **opération** à *SaveResponse.ReadLOB.Request*|  
|ReceiveMessage2|-Définissez **l’initialisation des ensembles de corrélations** à *Correlation_UpdateLOB*<br />-Définissez **Message** à *MAX2*<br />-Définissez **opération** à *FileIn.UpdateLOB.Request*|  
|SendMessage2|-Définissez **Message** à *MAX2*<br />-Définissez **opération** à *LOBPort.UpdateLOB.Request*|  
|ReceiveResponse2|-Définissez **Message** à *réponse aux menaces2*<br />-Définissez **opération** à *LOBPort.UpdateLOB.Response*|  
|SendResponse2|-Définissez **Message** à *réponse*<br />-Définissez **opération** à *SaveResponse.UpdateLOB.Request*|  
  
 Une fois que vous avez défini ces propriétés, les formes de message et les ports sont connectés et l’orchestration est terminée.  
  
 Vous devez maintenant générer la solution BizTalk et déployez-le dans un [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]. Pour plus d’informations, consultez [génération et exécution des Orchestrations](../../core/building-and-running-orchestrations.md).  
  
## <a name="configuring-the-biztalk-application"></a>Configuration de l’Application BizTalk  
 Après avoir déployé le projet BizTalk, l’orchestration que vous avez créé précédemment est répertoriée sous le **Orchestrations** volet de la console Administration de BizTalk Server. Vous devez utiliser la console Administration de BizTalk Server pour configurer l’application. Pour une procédure pas à pas, consultez [procédure pas à pas : déploiement d’une Application BizTalk base](Walkthrough:%20Deploying%20a%20Basic%20BizTalk%20Application.md).
  
 Configuration d’une application implique :  
  
-   Sélection d’un hôte de l’application.  
  
-   Mappage de ports que vous avez créé dans l’orchestration aux ports physiques dans la console Administration de BizTalk Server. Pour cette orchestration, vous devez :  
  
    -   Définir un emplacement sur le disque dur et un port de fichier correspondant où vous allez déposer les messages de demande, une pour les opérations ReadLOB et UpdateLOB. L’orchestration BizTalk consommer les messages de demande et l’envoyer à la base de données Oracle.  
  
    -   Définir un emplacement sur le disque dur et un port de fichier correspondant dans lequel l’orchestration BizTalk supprime les messages de réponse, une pour chaque opération, contenant la réponse à la base de données Oracle.  
  
    -   Définir un port d’envoi WCF-Custom ou WCF-OracleDB physique pour envoyer des messages à la base de données Oracle. Vous devez également spécifier l’action dans le port d’envoi. Pour plus d’informations sur la création des ports WCF-Custom ou WCF-OracleDB, consultez [configurer manuellement une liaison de port physique à l’adaptateur de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/manually-configure-a-physical-port-binding-to-the-oracle-database-adapter.md). Car le WCF-Custom ou WCF-OracleDB port d’envoi envoie et recevoir des messages conformes à plusieurs schémas et effectue deux opérations, vous devez définir une action dynamique pour les opérations. Pour plus d’informations sur les actions, consultez [configurer l’action SOAP pour la base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/configure-the-soap-action-for-oracle-database.md). Pour cette orchestration, l’action doit être définie comme suit :  
  
        ```  
        \<BtsActionMapping xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema">  
          <Operation Name="ReadLOB" Action="http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/CUSTOMER/ReadLOB" />  
          <Operation Name="UpdateLOB" Action="http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/CUSTOMER/UpdateLOB" />  
        </BtsActionMapping>  
        ```  
  
        > [!NOTE]
        >  Génération de schéma à l’aide du [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] crée également un fichier de liaison contenant des informations sur les ports et les actions à définir pour ces ports. Vous pouvez importer ce fichier de liaison à partir de la console Administration de BizTalk Server pour créer des ports d’envoi (pour les appels sortants) ou de ports de réception (d’appels entrants). Pour plus d’informations, consultez [configurer une liaison de port physique à l’aide d’un fichier de liaison de port pour la base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/configure-a-physical-port-binding-using-a-port-binding-file-to-oracle-database.md).  
  
## <a name="starting-the-application"></a>Démarrage de l’Application  
 Vous devez démarrer l’application BizTalk pour effectuer une opération sur la base de données Oracle. Pour obtenir des instructions sur le démarrage d’une application BizTalk, consultez [comment démarrer une Orchestration](../../core/how-to-start-an-orchestration.md).  
  
 À ce stade, vérifiez que :  
  
-   Le fichier de port de réception pour recevoir des messages de demande pour l’orchestration est en cours d’exécution.  
  
-   Le port d’envoi FILE pour recevoir les messages de réponse à partir de l’orchestration est en cours d’exécution.  
  
-   Port ou WCF-OracleDB pour envoyer des messages à la base de données est en cours d’exécution de Oracle d’envoi WCF-Custom.  
  
-   L’orchestration BizTalk pour l’opération est en cours d’exécution.  
  
## <a name="executing-the-operation"></a>L’exécution de l’opération  
 Après avoir exécuté l’application, vous devez supprimer l’emplacement de réception de messages dans le fichier de demande. Le schéma pour les messages de demande doit être conforme au schéma pour les opérations que vous avez généré précédemment. Consultez [des schémas de Message pour des opérations spéciales LOB](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-special-lob-operations2.md) pour plus d’informations sur le schéma de message de demande pour l’appel d’opérations sur les types de données LOB à l’aide de la [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].  
  
 L’orchestration consomme les messages de requête et les envoie à la base de données Oracle. La réponse à partir de la base de données Oracle est enregistrée à un autre emplacement de fichier définie dans le cadre de l’orchestration.  
  
 Pour cette orchestration, nous avons d’abord supprimer un message de demande pour l’opération UpdateLOB mettre à jour la colonne PHOTO (de type de données objet BLOB) de la table CUSTOMER. Le message de demande pour appeler la mise à jour la colonne PHOTO pour un client spécifique est :  
  
```  
<UpdateLOB xmlns="http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/CUSTOMER">  
  <LOB_COLUMN>PHOTO</LOB_COLUMN>  
  <FILTER>Name='Mindy Martin'</FILTER>  
  <Stream>YWJjZA==</Stream>  
</UpdateLOB>  
```  
  
> [!NOTE]
>  La chaîne de filtre doit toujours extraire une ligne correspondante dans le cas contraire le lève de carte de base de données Oracle une XmlReaderParsingException. Plus la valeur pour le \<flux > élément doit être de type de base64Binary.  
  
 La réponse pour l’opération UpdateLOB est :  
  
```  
\<?xml version="1.0" encoding="utf-8"?>  
<UpdateLOBResponse xmlns="http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/CUSTOMER"></UpdateLOBResponse>  
```  
  
 Nous avons maintenant déposez un message de demande pour l’opération ReadLOB lire les données qui a été mis à jour par l’opération UpdateLOB. Le message de demande d’appeler l’opération ReadLOB sur la colonne PHOTO pour un client spécifique est :  
  
```  
<ReadLOB xmlns="http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/CUSTOMER">  
  <LOB_COLUMN>PHOTO</LOB_COLUMN>  
  <FILTER>NAME='Mindy Martin'</FILTER>  
</ReadLOB>  
```  
  
> [!NOTE]
>  La chaîne de filtre doit toujours d’extraire une ligne correspondante. S’il existe plus d’une ligne correspondante, le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] retourne uniquement la colonne LOB de la première ligne (correspondance).  
  
 La réponse pour l’opération ReadLOB est :  
  
```  
\<?xml version="1.0" encoding="utf-8"?>  
<ReadLOBResponse mlns="http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/CUSTOMER">  
  <ReadLOBResult>YWJjZA==</ReadLOBResult>  
</ReadLOBResponse>  
```  
  
> [!NOTE]
>  La réponse pour l’opération ReadLOB risque d’échouer à valider le WSDL. Vous devez effectuer certaines tâches pour valider le ReadLOB contre le WSDL. Pour plus d’informations, consultez [résolution des problèmes opérationnels](https://msdn.microsoft.com/library/dd787883.aspx).  
  
## <a name="possible-exceptions"></a>Exceptions possibles  
 Pour plus d’informations sur les exceptions, vous pouvez rencontrer lors de l’exécution d’opérations sur la table qui contient à l’aide des données LOB [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], consultez [Exceptions et gestion des erreurs](../../adapters-and-accelerators/adapter-oracle-database/exceptions-and-error-handling-with-the-oracle-database-adapter.md).  
  
## <a name="best-practices"></a>Bonnes pratiques  
 Après avoir déployé et configuré le projet BizTalk, vous pouvez exporter les paramètres de configuration dans un fichier XML appelé le fichier de liaisons. Une fois que vous générez un fichier de liaison, vous pouvez importer les paramètres de configuration à partir du fichier afin que vous n’avez pas besoin de créer les ports d’envoi, ports, etc. pour la même orchestration de réception. Pour plus d’informations sur les fichiers de liaison, consultez [liaisons de l’adaptateur de base de données Oracle de réutiliser](../../adapters-and-accelerators/adapter-oracle-database/reuse-oracle-database-adapter-bindings.md).  
  
## <a name="see-also"></a>Voir aussi  
[Blocs de construction pour les applications BizTalk de développer avec la base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/building-blocks-to-develop-biztalk-applications-with-oracle-database.md)