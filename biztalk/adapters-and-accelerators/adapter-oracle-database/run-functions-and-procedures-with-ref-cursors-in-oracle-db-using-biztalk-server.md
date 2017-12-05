---
title: "Appeler des fonctions et procédures avec des REF CURSOR dans la base de données Oracle à l’aide de BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- functions and procedures with REF CURSORS, invoking by using BizTalk Server
- functions and procedures with RECORD types, invoking by using BizTalk Server
- REF CURSORS
- RECORD types
ms.assetid: 5e84b8d3-6352-4911-93f9-5d455ff579d9
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f9072f3df5c85ed09c5efbdc5e690a8eccc97b2f
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="invoke-functions-and-procedures-with-ref-cursors-in-oracle-database-using-biztalk-server"></a>Appeler des fonctions et procédures avec des REF CURSOR dans la base de données Oracle à l’aide de BizTalk Server
Un REF CURSOR est un type de données PL/SQL qui représente un pointeur vers un jeu de résultats côté serveur généré en exécutant une requête. Un type REF CURSOR permet d’entrée et de sortie de diffusion en continu de données et est idéal pour le transfert de grandes quantités de données vers et à partir d’un code de PL/SQL. Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] fortement typée et faiblement typé (SYS_REFCURSOR) REF CURSOR qui peuvent être passés aux procédures PL/SQL et aux fonctions, OUT ou IN des paramètres est prise en charge. Pour plus d’informations sur la façon dont [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] prend en charge REF CURSOR, consultez [opérations sur les fonctions et procédures avec des paramètres REF CURSOR](../../adapters-and-accelerators/adapter-oracle-database/ref-cursor-parameters-in-oracle-database-adapter.md). Pour plus d’informations sur la structure XML pour REF CURSOR, consultez [des schémas de Message pour REF CURSOR](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-ref-cursors.md).  
  
## <a name="how-to-invoke-functions-in-an-oracle-database"></a>Explique comment appeler des fonctions dans une base de données Oracle ?  
 Une opération sur une base de données Oracle à l’aide [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] avec [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] implique les tâches de procédures décrites dans [blocs de construction pour développer des Applications BizTalk avec la base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/building-blocks-to-develop-biztalk-applications-with-oracle-database.md). Pour appeler une fonction dans une base de données Oracle qui prend des REF CURSOR tant que paramètres in et donne des REF CURSOR comme paramètres de sortie, ces tâches sont :  
  
1.  Créez un projet BizTalk et générer le schéma pour la fonction à appeler dans une base de données Oracle.  
  
2.  Créer des messages dans le projet BizTalk pour envoyer et recevoir des messages à partir de la base de données Oracle.  
  
3.  Créez une orchestration pour appeler la fonction dans la base de données Oracle.  
  
4.  Générez et déployez le projet BizTalk.  
  
5.  Configurer l’application en créant physique d’envoi et ports de réception BizTalk.  
  
6.  Démarrez l’application BizTalk.  
  
 Cette rubrique fournit des instructions pour effectuer ces tâches.  
  
## <a name="sample-based-on-this-topic"></a>Exemple basé sur cette rubrique  
 Un exemple, Func_RefCursor, en fonction de cette rubrique est également fourni avec le [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]. Pour plus d’informations, consultez [exemples d’adaptateur](../../adapters-and-accelerators/accelerator-rosettanet/adapter-samples.md).  
  
## <a name="generating-schema"></a>Génération du schéma  
 Dans cette rubrique, pour illustrer comment le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] prend en charge l’appel de fonction qui accepte des paramètres REF CURSOR, nous appellerons la procédure GET_ACTIVITY. Cette procédure accepte un REF CURSOR faiblement typée IN et fortement typées dans des REF CURSOR en tant que paramètres. La fonction retourne l’état, faiblement typée des REF CURSOR et fortement typées dans des REF CURSOR. La procédure GET_ACTIVITY est disponible dans le cadre de la ACCOUNT_PKG créée en exécutant les scripts SQL fournis avec les exemples. Pour en savoir plus sur les exemples et les scripts SQL, consultez [exemples de schéma](../../adapters-and-accelerators/accelerator-rosettanet/schema-samples.md).  
  
 Par conséquent, pour appeler la procédure GET_ACTIVITY, nous génération du schéma de la même procédure sous le schéma SCOTT\Package\ACCOUNT_PKG. Consultez [obtenir les métadonnées pour les opérations de base de données Oracle dans Visual Studio](../../adapters-and-accelerators/adapter-oracle-database/get-metadata-for-oracle-database-operations-in-visual-studio.md) pour plus d’informations sur la génération de schéma.  
  
## <a name="defining-messages-and-message-types"></a>Définition des Messages et les Types de messages  
 Le schéma que vous avez généré précédemment décrit les « types » requis pour les messages dans l’orchestration. Un message est généralement une variable, le type est défini par le schéma correspondant. Vous devez lier le schéma généré à la première étape pour les messages à partir de la fenêtre Vue Orchestration du projet BizTalk.  
  
 Cette rubrique, vous devez créer deux messages : un pour envoyer une demande à la base de données Oracle et l’autre pour recevoir une réponse.  
  
 Procédez comme suit pour créer des messages et les lier au schéma :  
  
#### <a name="to-create-messages-and-link-to-schema"></a>Pour créer des messages et le lier au schéma  
  
1.  Ouvrez la fenêtre Vue Orchestration du projet BizTalk, s’il n’est pas déjà ouvert. Pour ce faire, cliquez sur **vue**, pointez sur **autres fenêtres**, puis cliquez sur **Vue Orchestration**.  
  
2.  Dans la vue Orchestration, cliquez sur **Messages**, puis cliquez sur **nouveau Message**.  
  
3.  Cliquez sur le message qui vient d’être créé, puis sélectionnez **fenêtre Propriétés**.  
  
4.  Dans le **propriétés** volet pour **Message_1**, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |Identificateur|Type **demande**.|  
    |Type de message|Dans la liste déroulante, développez **schémas**, puis sélectionnez *Func_RefCursor.OracleDBBindingSchema.GET_ACTIVITY*, où *Func_RefCursor* est le nom de votre BizTalk projet. *OracleDBBindingSchema* est le schéma généré pour la procédure GET_ACTIVITY.|  
  
5.  Répétez l’étape précédente pour créer un nouveau message. Dans le **propriétés** volet pour le nouveau message, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |Identificateur|Type **réponse**.|  
    |Type de message|*Func_RefCursor.OracleDBBindingSchema.GET_ACTIVITYResponse*|  
  
## <a name="setting-up-the-orchestration"></a>Configuration de l’Orchestration  
 Vous devez créer une orchestration BizTalk à utiliser [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] pour appeler une procédure avec des paramètres REF CURSOR. Dans cette orchestration, vous déposez un message de demande à une emplacement de réception. Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] consomme ce message et le transmet à la base de données Oracle via ODP. La réponse à partir de la base de données Oracle est enregistrée dans un autre emplacement. Contiendrait une orchestration classique pour appeler des fonctions et procédures avec des REF CURSOR :  
  
-   Envoyer et recevoir des formes pour envoyer des messages à la base de données Oracle et de recevoir des réponses.  
  
-   Port pour recevoir des messages de demande à envoyer à la base de données Oracle de réception unidirectionnel.  
  
-   Un double port d’envoi pour envoyer des messages de demande à Oracle de base de données et recevoir des réponses.  
  
-   Un port d’envoi unidirectionnel pour envoyer les réponses à partir de la base de données Oracle dans un dossier.  
  
 Un exemple d’orchestration ressemble à ceci :  
  
 ![Orchestrations permettant l’utilisation des Ref CURSOR dans Oracle](../../adapters-and-accelerators/adapter-oracle-database/media/41ed9647-a49d-4122-b9fc-c5ce4dca3533.gif "41ed9647-a49d-4122-b9fc-c5ce4dca3533")  
  
### <a name="adding-message-shapes"></a>Ajouter des formes de Message  
 Assurez-vous que vous spécifiez les propriétés suivantes pour chacune des formes de message. Les noms répertoriés dans la colonne de forme sont les noms des formes de message tel qu’affiché dans l’orchestration juste-mentionné.  
  
|Graphique à base de formes|Type de forme|Propriétés|  
|-----------|----------------|----------------|  
|ReceiveMessage|Recevoir|-Définissez **nom** à *ReceiveMessage*<br />-Définissez **activer** à *True*|  
|SendMessage|Send|-Définissez **nom** à *SendMessage*|  
|Réception réponse|Recevoir|-Définissez **nom** à *ReceiveResponse*<br />-Définissez **activer** à *False*|  
|SendResponse|Send|-Définissez **nom** à *SendResponse*|  
  
### <a name="adding-ports"></a>Ajout de Ports  
 Assurez-vous que vous spécifiez les propriétés suivantes pour chacun des ports logiques. Les noms répertoriés dans la colonne de Port sont les noms des ports tel qu’affiché dans l’orchestration.  
  
|Port|Propriétés|  
|----------|----------------|  
|Fichier|-Définissez **identificateur** à *FileIn*<br />-Définissez **Type** à *FileInType*<br />-Définissez **modèle de Communication** à *à sens unique*<br />-Définissez **Direction de Communication** à *de réception*|  
|LOBPort|-Définissez **identificateur** à *LOBPort*<br />-Définissez **Type** à *LOBPortType*<br />-Définissez **modèle de Communication** à *demande-réponse*<br />-Définissez **Direction de Communication** à *envoi / réception*|  
|SaveResponse|-Définissez **identificateur** à *SaveResponse*<br />-Définissez **Type** à *SaveResponseType*<br />-Définissez **modèle de Communication** à *à sens unique*<br />-Définissez **Direction de Communication** à *envoyer*|  
  
## <a name="specify-messages-for-action-shapes-and-connect-them-to-ports"></a>Spécifier des Messages pour les formes d’Action et connectez-les aux Ports  
 Le tableau suivant indique les propriétés et leurs valeurs, vous devez définir pour spécifier les messages de formes d’action et les lier aux ports. Les noms répertoriés dans la colonne de forme sont les noms des formes de message tel qu’affiché dans l’orchestration mentionnée précédemment.  
  
|Graphique à base de formes|Propriétés|  
|-----------|----------------|  
|ReceiveMessage|-Définissez **Message** à *demande*<br />-Définissez **opération** à *FileIn.REFCURSOR.Request*|  
|SendMessage|-Définissez **Message** à *demande*<br />-Définissez **opération** à *LOBPort.REFCURSOR.Request*|  
|Réception réponse|-Définissez **Message** à *réponse*<br />-Définissez **opération** à *LOBPort.REFCURSOR.Response*|  
|SendResponse|-Définissez **Message** à *réponse*<br />-Définissez **opération** à *SaveResponse.REFCURSOR.Request*|  
  
 Une fois que vous avez défini ces propriétés, les formes de message et les ports sont connectés et l’orchestration est terminée.  
  
 Vous devez maintenant générer la solution BizTalk et déployez-le dans un [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]. Pour plus d’informations, consultez [génération et exécution des Orchestrations](../../core/building-and-running-orchestrations.md).  
  
## <a name="configuring-the-biztalk-application"></a>Configuration de l’Application BizTalk  
 Après avoir déployé le projet BizTalk, l’orchestration que vous avez créé précédemment est répertoriée sous le **Orchestrations** volet de la console Administration de BizTalk Server. Vous devez utiliser la console Administration de BizTalk Server pour configurer l’application. Pour une procédure pas à pas, consultez [procédure pas à pas : déploiement d’une Application BizTalk base](Walkthrough:%20Deploying%20a%20Basic%20BizTalk%20Application.md).
  
 Configuration d’une application implique :  
  
-   Sélection d’un hôte de l’application.  
  
-   Mappage de ports que vous avez créé dans l’orchestration aux ports physiques dans la console Administration de BizTalk Server. Pour cette orchestration, vous devez :  
  
    -   Définir un emplacement sur le disque dur et un port de fichier correspondant où vous allez déposer un message de demande. L’orchestration BizTalk consommer le message de demande et l’envoyer à la base de données Oracle.  
  
    -   Définir un emplacement sur le disque dur et un port de fichier correspondant dans lequel l’orchestration BizTalk supprimera le message de réponse contenant la réponse à la base de données Oracle.  
  
    -   Définir un port d’envoi WCF-Custom ou WCF-OracleDB physique pour envoyer des messages à la base de données Oracle. Vous devez également spécifier l’action dans le port d’envoi. Pour plus d’informations sur la création des ports WCF-Custom ou WCF-OracleDB, consultez [configurer manuellement la liaison du port physique à l’adaptateur de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/manually-configure-a-physical-port-binding-to-the-oracle-database-adapter.md).  
  
        > [!NOTE]
        >  Génération de schéma à l’aide du [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] crée également un fichier de liaison contenant des informations sur les ports et les actions à définir pour ces ports. Vous pouvez importer ce fichier de liaison à partir de la console Administration de BizTalk Server pour créer des ports d’envoi (pour les appels sortants) ou de ports de réception (d’appels entrants). Pour plus d’informations, consultez [liaison de port physique configurer à l’aide du fichier de liaison de port à la base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/configure-a-physical-port-binding-using-a-port-binding-file-to-oracle-database.md).  
  
## <a name="starting-the-application"></a>Démarrage de l’Application  
 Vous devez démarrer l’application BizTalk pour appeler une procédure dans une table de base de données Oracle. Pour obtenir des instructions sur le démarrage d’une application BizTalk, consultez [comment démarrer une Orchestration](../../core/how-to-start-an-orchestration.md).  
  
 À ce stade, vérifiez que :  
  
-   Le fichier de port de réception pour recevoir des messages de demande pour l’orchestration est en cours d’exécution.  
  
-   Le port d’envoi FILE pour recevoir les messages de réponse à partir de l’orchestration est en cours d’exécution.  
  
-   Le port d’envoi WCF-Custom ou WCF-OracleDB à envoyer des messages à la base de données Oracle est en cours d’exécution.  
  
-   L’orchestration BizTalk pour l’opération est en cours d’exécution.  
  
## <a name="executing-the-operation"></a>L’exécution de l’opération  
 Après avoir exécuté l’application, vous devez supprimer un message de demande pour le fichier de l’emplacement de réception. Le schéma du message de demande doit être conforme au schéma pour la procédure que vous avez généré précédemment. Consultez [des schémas de Message pour les fonctions et procédures](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-functions-and-procedures.md) pour plus d’informations sur le schéma de message de demande pour l’appel de fonctions à l’aide de la [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].  
  
 Pour appeler la procédure GET_ACTIVITY, vous devez spécifier faiblement typée de REF CURSOR et fortement typées dans des REF CURSOR en tant que paramètres. Par conséquent, le message de demande pour appeler cette procédure est :  
  
```  
<GET_ACTIVITY xmlns="http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Package/ACCOUNT_PKG">  
  <INRECS>BEGIN OPEN ? FOR SELECT * FROM ACCOUNTACTIVITY WHERE ACCOUNT=100001; END;</INRECS>  
  <INOUTRECS_IN>BEGIN ACCOUNT_PKG.GET_ALL_ACTIVITY(?); END;</INOUTRECS_IN>  
</GET_ACTIVITY>  
```  
  
 L’orchestration consomme le message de demande et l’envoie à la base de données Oracle. La réponse à partir de la base de données Oracle est enregistrée dans l’autre emplacement de fichier définie dans le cadre de l’orchestration.  
  
 La réponse pour le message de demande ci-dessus est la suivante :  
  
```  
<?xml version="1.0" encoding="utf-8" ?>   
<GET_ACTIVITYResponse xmlns="http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Package/ACCOUNT_PKG">  
  <STATUS>5</STATUS>   
  <INOUTRECS>  
    <INOUTRECSRECORD xmlns="http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Package/ACCOUNT_PKG/GET_ACTIVITY">  
      <TID>1</TID>   
      <ACCOUNT>100001</ACCOUNT>   
      <AMOUNT>500</AMOUNT>   
      <DESCRIPTION />   
      <TRANSDATE>2007-10-16T16:58:44</TRANSDATE>   
      <PROCESSED>n</PROCESSED>   
    </INOUTRECSRECORD>  
    <INOUTRECSRECORD xmlns="http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Package/ACCOUNT_PKG/GET_ACTIVITY">  
      .....   
      .....   
    </INOUTRECSRECORD>  
    ....  
    ....  
  </INOUTRECS>  
  <OUTRECS>  
    <GenRecordRow xmlns="http://Microsoft.LobServices.OracleDB/2007/03">  
      <GenRecordColumn>  
        <GenRecordColumn>  
          <ColumnName>TID</ColumnName>   
          <ColumnValue>1</ColumnValue>   
          <ColumnType>System.Decimal</ColumnType>   
        </GenRecordColumn>  
        <GenRecordColumn>  
          ....   
        </GenRecordColumn>  
        .....  
        .....  
      </GenRecordColumn>  
    </GenRecordRow>  
    <GenRecordRow xmlns="http://Microsoft.LobServices.OracleDB/2007/03">  
      .....  
      .....  
    </GenRecordRow>  
    .....  
    .....  
  </OUTRECS>  
</GET_ACTIVITYResponse>  
```  
  
 Notez que la réponse contienne un état, faiblement typée des REF CURSOR et un IN fortement typée OUT REF CUROSR.  
  
## <a name="possible-exceptions"></a>Exceptions possibles  
 Pour plus d’informations sur les exceptions, vous pouvez rencontrer lors de l’appel à l’aide des procédures et des fonctions [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], consultez [Exceptions et gestion des erreurs](../../adapters-and-accelerators/adapter-oracle-database/exceptions-and-error-handling-with-the-oracle-database-adapter.md).  
  
## <a name="best-practices"></a>Bonnes pratiques  
 Après avoir déployé et configuré le projet BizTalk, vous pouvez exporter les paramètres de configuration dans un fichier XML appelé le fichier de liaisons. Une fois que vous générez un fichier de liaison, vous pouvez importer les paramètres de configuration à partir du fichier afin que vous n’avez pas besoin de créer les ports d’envoi, ports, etc. pour la même orchestration de réception. Pour plus d’informations sur les fichiers de liaison, consultez [liaisons de l’adaptateur de base de données Oracle de réutiliser](../../adapters-and-accelerators/adapter-oracle-database/reuse-oracle-database-adapter-bindings.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Développer des applications BizTalk](../../core/develop-your-biztalk-applications.md)