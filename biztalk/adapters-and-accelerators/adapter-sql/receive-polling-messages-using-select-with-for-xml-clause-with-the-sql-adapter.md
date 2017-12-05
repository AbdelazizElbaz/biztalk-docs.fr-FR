---
title: "Recevoir des messages d’interrogation à l’aide des instructions SELECT avec la Clause FOR XML à partir de SQL à l’aide de BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 65c629c1-9ef7-4aa1-8ec1-f94a3cb41cb0
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 51cd634d7933f7e25de2e742711b1593bf6b6dc1
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="receive-polling-messages-using-select-statements-with-for-xml-clause-from-sql-using-biztalk-server"></a>Recevoir des messages d’interrogation à l’aide des instructions SELECT avec la Clause FOR XML à partir de SQL à l’aide de BizTalk Server
Vous pouvez configurer le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] pour recevoir des messages de modification de données périodiques de tables SQL Server ou des vues à l’aide des instructions SELECT ou des procédures stockées qui incluent une clause FOR XML. Vous pouvez spécifier ces instructions en tant qu’instruction d’interrogation de l’adaptateur s’exécute pour interroger la base de données. L’instruction d’interrogation peut être une instruction SELECT ou une procédure stockée qui retourne un jeu de résultats.  
  
 Pour plus d’informations sur la façon dont l’adaptateur prend en charge d’interrogation, consultez [prise en charge pour l’interrogation](https://msdn.microsoft.com/library/dd788416.aspx). Pour plus d’informations sur la structure du message SOAP pour les opérations d’interrogation, consultez [des schémas de Message pour l’interrogation et les opérations de TypedPolling](../../adapters-and-accelerators/adapter-sql/message-schemas-for-the-polling-and-typedpolling-operations.md). L’instruction SQL [clause FOR XML](https://docs.microsoft.com/sql/relational-databases/xml/for-xml-sql-server) fournit plus de détails.
  
> [!NOTE]
>  Cette rubrique montre comment utiliser le **XmlPolling** opération pour recevoir des messages de l’interrogation entrante. Le **XmlPolling** opération est utilisée pour interroger une base de données SQL Server à l’aide des instructions SELECT ou des procédures stockées qui incluent une clause FOR XML. Le message pour le **XmlPolling** opération inclut le message xml reçu en exécutant l’instruction SELECT ou la procédure stockée dans SQL Server Management Studio.  
>   
>  Vous pouvez également utiliser l’adaptateur pour recevoir les différents types de messages de l’interrogation.  
>   
>  -   Si vous souhaitez obtenir un message d’interrogation faiblement typée, vous devez utiliser l’opération d’interrogation. Pour plus d’informations, consultez [Messages basés sur la réception d’interrogation de données modifiées à partir de SQL Server à l’aide de BizTalk Server](../../adapters-and-accelerators/adapter-sql/receive-polling-based-data-changed-messages-from-sql-server-using-biztalk.md).  
> -   Si vous souhaitez obtenir le message d’interrogation fortement typée, vous devez utiliser le **TypedPolling** opération. Vous devez également utiliser le **TypedPolling** opération plusieurs opérations d’interrogation dans une même application BizTalk. Pour obtenir des instructions sur la façon d’effectuer **TypedPolling** opération, consultez [réception fortement typé reposant sur l’interrogation Messages de modification de données à partir de SQL Server à l’aide de BizTalk Server](../../adapters-and-accelerators/adapter-sql/receive-strongly-typed-polling-based-data-changed-messages-from-sql-in-biztalk.md).  
  
> [!IMPORTANT]
>  Si vous souhaitez disposer d’interrogation plus d’une opération dans une même application BizTalk, vous devez spécifier un **InboundID** propriété de connexion dans le cadre de la connexion URI pour le rendre unique. Avec un URI de connexion unique, vous pouvez créer plusieurs ports de réception qui interrogent la même base de données, ou même de la même table dans une base de données. Pour plus d’informations, consultez [de réception d’interrogation Messages entre plusieurs Ports réception à partir de SQL à l’aide de BizTalk Server](../../adapters-and-accelerators/adapter-sql/receive-polling-messages-across-multiple-receive-ports-from-sql-using-biztalk.md).  
  
## <a name="how-this-topic-demonstrates-polling"></a>Comment cette rubrique illustre l’interrogation  
 Dans cette rubrique, pour illustrer comment le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] prend en charge la réception de données des messages de modification, nous utilisons une instruction SELECT avec la clause FOR XML pour interroger la base de données SQL Server. Lorsque vous appelez une telle instruction dans SQL Server Management Studio, la sortie est sous la forme d’un message xml. Pour utiliser ces instructions pour interroger une base de données SQL Server, vous devez disposer du schéma du message xml de réponse. Le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] requiert ce schéma pour recevoir un message d’interrogation après l’exécution d’une instruction SELECT avec la clause FOR XML. Par conséquent, pour utiliser une instruction SELECT avec la clause FOR XML pour interroger la base de données SQL Server, vous devez effectuer l’ensemble suivant de tâches.  
  
1.  Générer le schéma pour le message de réponse XML pour l’instruction SELECT avec la clause FOR XML.  
  
2.  Créez un projet BizTalk et ajouter le schéma généré pour le projet.  
  
3.  Créez un message dans le projet BizTalk pour la réception des messages de réponse XML à partir de la base de données SQL Server.  
  
4.  Créez une orchestration pour recevoir des messages à partir de la base de données SQL Server et les enregistrer dans un dossier.  
  
5.  Générez et déployez le projet BizTalk.  
  
6.  Configurer l’application en créant physique d’envoi et ports de réception BizTalk.  
  
    > [!IMPORTANT]
    >  Pour les scénarios de trafic entrant d’interrogation, vous devez toujours configurer un WCF-Custom unidirectionnel ou port de réception WCF-SQL. Ports de réception bidirectionnel WCF-Custom ou WCF-SQL ne sont pas pris en charge pour les opérations entrantes.  
  
7.  Démarrez l’application BizTalk.  
  
##  <a name="BKMK_RespSchema"></a>Génération de schéma pour le Message de réponse pour l’instruction SELECT  
 Vous pouvez générer le schéma de message de réponse pour l’instruction SELECT en incluant le `xmlschema` clause avec la `for xml` clause. Dans cette rubrique, nous utilisons une instruction SELECT pour extraire des informations pour un ID d’employé donné. Pour récupérer le schéma en exécutant une instruction SELECT, l’instruction SELECT doit être écrite de la manière suivante :  
  
```  
SELECT Employee_ID ,Name ,Designation FROM Employee for xml auto, xmlschema  
```  
  
 Exécutez cette instruction SELECT pour obtenir le schéma pour le message de réponse. Enregistrez le schéma. Vous devez maintenant créer un projet BizTalk dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] et ajoutez ce schéma au projet. Pour cet exemple, vous pouvez nommer ce schéma en tant que **PollingResponse.xsd**.  
  
> [!IMPORTANT]
>  Veillez à supprimer la `xmlschema` clause après avoir exécuté l’instruction SELECT pour générer le schéma. Si vous ne le faites pas, lorsque vous exécutez enfin l’instruction SELECT via BizTalk en tant que partie de l’opération XmlPolling, vous générerez à nouveau le schéma du message de réponse. Par conséquent, pour obtenir le message de réponse en tant que xml, vous devez supprimer la `xmlschema` clause.  
  
#### <a name="to-add-the-schema-to-a-biztalk-project"></a>Pour ajouter le schéma à un projet BizTalk  
  
1.  Créez un projet BizTalk dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)].  
  
2.  Ajoutez le schéma de réponse que vous avez généré pour la procédure stockée au projet BizTalk. Cliquez sur le projet BizTalk dans l’Explorateur de solutions, pointez sur **ajouter**, puis cliquez sur **élément existant**. Dans la boîte de dialogue Ajouter un élément existant, accédez à l’emplacement où vous avez enregistré le schéma et cliquez sur **ajouter**.  
  
3.  Ouvrez le schéma dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] et apportez les modifications suivantes.  
  
    1.  Ajouter un nœud au schéma et déplacer le nœud racine existant sous ce nœud qui vient d’être ajouté. Donnez un nom pour le nœud racine. Pour cette rubrique, renommez le nœud racine de **racine**.  
  
    2.  Le schéma de réponse généré par l’instruction SELECT fait référence à un sqltypes.xsd. Vous pouvez obtenir le schéma sqltypes.xsd [http://go.microsoft.com/fwlink/p/?LinkId=131087](http://go.microsoft.com/fwlink/p/?LinkId=131087). Ajoutez le schéma sqltypes.xsd au projet BizTalk.  
  
    3.  Dans le schéma généré pour l’instruction SELECT, modifiez la valeur de `import schemaLocation` à ce qui suit.  
  
        ```  
        import schemaLocation=”sqltypes.xsd”  
        ```  
  
         Pour cela, car vous avez déjà ajouté le schéma sqltypes.xsd à votre projet BizTalk.  
  
    4.  Fournir un espace de noms cible du schéma. Cliquez sur le  **\<schéma\>**  nœud et dans le volet Propriétés, spécifiez un espace de noms dans le **cible Namespace** propriété. Pour cette rubrique, donnez à l’espace de noms `http://ForXmlPolling/namespace`.  
  
## <a name="defining-messages-and-message-types"></a>Définition des Messages et les Types de messages  
 Le schéma que vous avez généré précédemment décrit les « types » requis pour les messages dans l’orchestration. Un message est généralement une variable, le type est défini par le schéma correspondant. Une fois que le schéma est généré, vous devez le lier aux messages à partir de la vue de l’Orchestration du projet BizTalk.  
  
 Pour cette rubrique, vous devez créer un message à recevoir des messages à partir de la base de données SQL Server.  
  
 Procédez comme suit pour créer des messages et les lier au schéma.  
  
#### <a name="to-create-messages-and-link-to-schema"></a>Pour créer des messages et le lier au schéma  
  
1.  Ajouter une orchestration au projet BizTalk. À partir de l’Explorateur de solutions, cliquez sur le nom du projet BizTalk, pointez sur **ajouter**, puis cliquez sur **un nouvel élément**. Tapez un nom pour l’orchestration BizTalk, puis **ajouter**.  
  
2.  Ouvrez la fenêtre Vue orchestration du projet BizTalk, s’il n’est pas déjà ouvert. Cliquez sur **vue**, pointez sur **autres fenêtres**, puis cliquez sur **Vue Orchestration**.  
  
3.  Dans le **Vue Orchestration**, avec le bouton droit **Messages**, puis cliquez sur **nouveau Message**.  
  
4.  Cliquez sur le message qui vient d’être créé, puis sélectionnez **fenêtre Propriétés**.  
  
5.  Dans le **propriétés** volet pour **Message_1**, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |Identificateur|Type **PollingMessage**.|  
    |Type de message|Dans la liste déroulante, développez **schémas**, puis sélectionnez *ForXMLPolling.PollingResponse*, où *ForXMLPolling* est le nom de votre projet BizTalk. *PollingResponse* est le nom du schéma de réponse généré par l’exécution de l’instruction SELECT comme décrit sous [recevoir des messages d’interrogation à l’aide des instructions SELECT avec la Clause FOR XML à partir de SQL à l’aide de BizTalk Server](../../adapters-and-accelerators/adapter-sql/receive-polling-messages-using-select-with-for-xml-clause-with-the-sql-adapter.md).|  
  
## <a name="setting-up-the-orchestration"></a>Configuration de l’Orchestration  
 Vous devez créer une orchestration BizTalk à utiliser [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] pour recevoir les messages de modification de données reposant sur l’interrogation de la base de données SQL Server. Dans cette orchestration, l’adaptateur reçoit la réponse de l’instruction select spécifiée pour le **PollingStatement** propriété de liaison. La réponse pour l’instruction SELECT est enregistrée dans un emplacement de fichier. Contiendrait une orchestration classique permettant l’interrogation d’une base de données SQL Server :  
  
-   Recevoir et envoyer des formes pour recevoir des messages à partir de SQL Server et les envoyer vers un port FILE, respectivement.  
  
-   Unidirectionnel port de réception pour recevoir des messages à partir de SQL Server.  
  
    > [!IMPORTANT]
    >  Pour les scénarios d’interrogation entrant que vous devez toujours configurer un port de réception unidirectionnel. Bidirectionnel recevoir des ports ne sont pas pris en charge pour les opérations entrantes.  
  
-   Un port d’envoi unidirectionnel pour envoyer des réponses d’interrogation à partir d’une base de données SQL Server dans un dossier.  
  
 Un exemple d’orchestration semblable au suivant.  
  
 ![Orchestration permettant l’interrogation d’une base de données SQL Server](../../adapters-and-accelerators/adapter-sql/media/5cf65d53-d70d-444d-82f7-2561efcd9ee4.gif "5cf65d53-d70d-444d-82f7-2561efcd9ee4")  
  
### <a name="adding-message-shapes"></a>Ajouter des formes de Message  
 Assurez-vous que vous spécifiez les propriétés suivantes pour chacune des formes de message. Les noms répertoriés dans la colonne de forme sont les noms des formes de message tel qu’affiché dans l’orchestration juste-mentionné.  
  
|Graphique à base de formes|Type de forme|Propriétés|  
|-----------|----------------|----------------|  
|ReceiveMessage|Recevoir|-Définissez **nom** à *ReceiveMessage*<br /><br /> -Définissez **activer** à *True*|  
|SaveMessage|Send|-Définissez **nom** à *SaveMessage*|  
  
### <a name="adding-ports"></a>Ajout de Ports  
 Assurez-vous que vous spécifiez les propriétés suivantes pour chacun des ports logiques. Les noms répertoriés dans la colonne de Port sont les noms des ports tel qu’affiché dans l’orchestration.  
  
|Port|Propriétés|  
|----------|----------------|  
|SQLReceivePort|-Définissez **identificateur** à *SQLReceivePort*<br /><br /> -Définissez **Type** à *SQLReceivePortType*<br /><br /> -Définissez **modèle de Communication** à *à sens unique*<br /><br /> -Définissez **Direction de Communication** à *de réception*|  
|SaveMessagePort|-Définissez **identificateur** à *SaveMessagePort*<br /><br /> -Définissez **Type** à *SaveMessagePortType*<br /><br /> -Définissez **modèle de Communication** à *à sens unique*<br /><br /> -Définissez **Direction de Communication** à *envoyer*|  
  
### <a name="specify-messages-for-action-shapes-and-connect-to-ports"></a>Spécifier des Messages pour les formes d’Action et de se connecter à des Ports  
 Le tableau suivant indique les propriétés et leurs valeurs, vous devez définir pour spécifier les messages de formes d’action et lier les messages aux ports. Les noms répertoriés dans la colonne de forme sont les noms des formes de message tel qu’affiché dans l’orchestration mentionnée précédemment.  
  
|Graphique à base de formes|Propriétés|  
|-----------|----------------|  
|ReceiveMessage|-Définissez **Message** à *de réception*<br /><br /> -Définissez **opération** à *SQLReceivePort.XmlPolling.Request*|  
|SaveMessage|-Définissez **Message** à *de réception*<br /><br /> -Définissez **opération** à *SaveMessagePort.XmlPolling.Request*|  
  
 Une fois que vous avez défini ces propriétés, les formes de message et les ports sont connectés et l’orchestration est terminée.  
  
 Vous devez maintenant générer la solution BizTalk et déployez-le dans un [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]. Pour plus d’informations, consultez [génération et exécution des Orchestrations](../../core/building-and-running-orchestrations.md).
  
## <a name="configuring-the-biztalk-application"></a>Configuration de l’Application BizTalk  
 Après avoir déployé le projet BizTalk, l’orchestration que vous avez créé précédemment est répertoriée sous le **Orchestrations** volet de la console Administration de BizTalk Server. Vous devez utiliser le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration pour configurer l’application. Pour une procédure pas à pas, consultez [procédure pas à pas : déploiement d’une Application BizTalk base](Walkthrough:%20Deploying%20a%20Basic%20BizTalk%20Application.md).
  
 Configuration d’une application implique :  
  
-   Sélection d’un hôte de l’application.  
  
-   Mappage de ports que vous avez créé dans l’orchestration aux ports physiques dans la console Administration de BizTalk Server. Pour cette orchestration, vous devez :  
  
    -   Définir un emplacement sur le disque dur et un port de fichier correspondant dans lequel l’orchestration BizTalk supprimera les messages à partir de la base de données SQL Server. Ces messages seront en réponse à l’instruction d’interrogation que vous spécifiez pour le port de réception.  
  
    -   Définir un WCF-Custom physique ou le port de réception unidirectionnel WCF-SQL. Ce port interroge la base de données SQL Server avec l’instruction d’interrogation que vous spécifiez pour le port. Pour plus d’informations sur la création de ports, consultez [configurer manuellement une liaison de port physique à l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/manually-configure-a-physical-port-binding-to-the-sql-adapter.md). Assurez-vous que vous spécifiez les propriétés suivantes de la liaison pour le port de réception.  
  
        > [!IMPORTANT]
        >  Vous n’avez pas besoin d’effectuer cette étape si vous avez spécifié les propriétés de liaison au moment du design. Dans ce cas, vous pouvez créer un WCF-custom ou WCF-SQL port de réception, avec le jeu de propriétés de liaison requis, en important le fichier de liaison créé par le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]. Pour plus d’informations, consultez [configurer une liaison de port physique à l’aide d’un fichier de liaison de port à utiliser l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/configure-a-physical-port-binding-using-a-port-binding-file-to-sql-adapter.md).  
  
        |Propriété de liaison|Valeur|  
        |----------------------|-----------|  
        |**InboundOperationType**|Assurez-vous que vous affectez la valeur **XmlPolling**.|  
        |**PolledDataAvailableStatement**|Assurez-vous que vous spécifiez une instruction SQL. Pour cette rubrique, spécifiez :<br /><br /> `SELECT COUNT(*) FROM Employee`|  
        |**PollingStatement**|Vérifiez que vous fournissez la même instruction, sans le `xmlschema` clause, que vous avez spécifié lors de la génération du schéma, comme décrit dans [recevoir des messages d’interrogation à l’aide des instructions SELECT avec la Clause FOR XML à partir de SQL à l’aide de BizTalk Server](../../adapters-and-accelerators/adapter-sql/receive-polling-messages-using-select-with-for-xml-clause-with-the-sql-adapter.md).<br /><br /> `SELECT Employee_ID ,Name ,Designation FROM Employee for xml auto`<br /><br /> **Remarque :** Notez que l’instruction SELECT ne contient-elle pas le `xmlschema` clause.|  
        |**XmlStoredProcedureRootNodeName**|Spécifiez le nom du nœud racine que vous avez ajouté au schéma de réponse que vous avez généré pour l’instruction SELECT, comme indiqué dans [génération de schéma pour le Message de réponse pour l’instruction SELECT](#BKMK_RespSchema). Pour cette rubrique, affectez la valeur **racine**.|  
        |**XmlStoredProcedureRootNodeNamespace**|Spécifier l’espace de noms cible pour le schéma de réponse que vous avez généré pour l’instruction SELECT, comme décrit sous [génération de schéma pour le Message de réponse pour l’instruction SELECT](#BKMK_RespSchema). Pour cette rubrique, affectez la valeur `http://ForXmlPolling/namespace`.|  
  
         Pour plus d’informations sur les propriétés de liaison différente, consultez [en savoir plus sur l’adaptateur BizTalk pour les propriétés de liaison de l’adaptateur SQL Server](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md).  
  
        > [!NOTE]
        >  Nous vous recommandons de configurer le niveau d’isolation de transaction et le délai d’attente de transaction lors de l’exécution d’opérations entrantes à l’aide de la [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]. Vous pouvez effectuer afin d’en ajoutant le service de port de réception comportement lors de la configuration WCF-Custom ou WCF-SQL. Pour obtenir des instructions sur la façon d’ajouter le comportement de service, consultez [configurer Transaction Isolation Level et délai de Transaction SQL](../../adapters-and-accelerators/adapter-sql/configure-transaction-isolation-level-and-transaction-timeout-with-sql.md).  
  
## <a name="starting-the-application"></a>Démarrage de l’Application  
 Vous devez démarrer l’application BizTalk pour recevoir des messages à partir de la base de données SQL Server. Pour obtenir des instructions sur le démarrage d’une application BizTalk, consultez [comment démarrer une Orchestration](../../core/how-to-start-an-orchestration.md).
  
 À ce stade, vérifiez que :  
  
-   Le WCF-Custom ou WCF-SQL unidirectionnel port de réception, qui interroge la base de données SQL Server à l’aide d’instructions spécifiées pour le **PollingStatement** propriété, de liaison est en cours d’exécution.  
  
-   Le port d’envoi de fichier qui reçoit des messages à partir de SQL Server, est en cours d’exécution.  
  
-   L’orchestration BizTalk pour l’opération est en cours d’exécution.  
  
## <a name="executing-the-operation"></a>L’exécution de l’opération  
 Après avoir exécuté l’application, l’ensemble d’actions suivantes ont lieu, dans l’ordre :  
  
-   L’adaptateur exécute le **PolledDataAvailableStatement** sur l’employé de table et détermine que la table comporte des enregistrements pour l’interrogation.  
  
-   L’adaptateur exécute l’instruction d’interrogation et reçoit un message de l’interrogation de la base de données SQL Server. Étant donné que l’instruction d’interrogation se compose d’une instruction SELECT avec une clause FOR XML, le message d’interrogation reçu par l’adaptateur ressemble à ceci :  
  
    ```  
    <?xml version="1.0" encoding="utf-8" ?>   
    <Root xmlns="http://ForXmlPolling/namespace">  
      <Employee Employee_ID="10765" Name="John" Designation="Tester" xmlns="" />   
      <Employee Employee_ID="10766" Name="Sam" Designation="Manager" xmlns="" />   
      .....  
      .....  
    </Root>  
    ```  
  
     Notez que le message d’interrogation est reçu dans le même schéma généré par l’exécution de l’instruction SELECT avec la **xmlschema** clause. Notez également que le nœud racine et l’espace de noms est celui que vous avez spécifié en tant que valeurs pour **XmlStoredProcedureRootNodeName** et **XmlStoredProcedureRootNodeNamespace** respectivement les propriétés de liaison.  
  
> [!NOTE]
>  Le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] continue à interroger jusqu'à ce que vous désactiviez explicitement le port de réception à partir de la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.  
  
## <a name="best-practices"></a>Bonnes pratiques  
 Après avoir déployé et configuré le projet BizTalk, vous pouvez exporter les paramètres de configuration dans un fichier XML appelé le fichier de liaison. Une fois que vous générez un fichier de liaison, vous pouvez importer les paramètres de configuration à partir du fichier, afin que vous n’avez pas besoin de créer les ports d’envoi et de réception pour l’orchestration même. Pour plus d’informations sur les fichiers de liaison, consultez [réutiliser les liaisons de l’adaptateur](../../adapters-and-accelerators/adapter-sql/reuse-sql-adapter-bindings.md).
  
## <a name="see-also"></a>Voir aussi  
 [Interrogation SQL Server à l’aide de l’adaptateur SQL avec BizTalk Server](../../adapters-and-accelerators/adapter-sql/poll-sql-server-using-the-sql-adapter-with-biztalk-server.md)