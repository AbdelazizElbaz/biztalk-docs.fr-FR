---
title: "Exécuter des procédures stockées ayant une clause FOR XML dans SQL Server à l’aide de BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1d8fe927-90bf-48fc-a418-63b920b409ed
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2e47c269516ba73ab1e61664d200db207110e98e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="execute-stored-procedures-having-a-for-xml-clause-in-sql-server-using-biztalk-server"></a>Exécuter des procédures stockées ayant une clause FOR XML dans SQL Server à l’aide de BizTalk Server
Une instruction SQL SELECT peut avoir une clause FOR XML qui retourne le résultat de requête au format XML au lieu d’un ensemble de lignes. Vous pouvez également avoir une procédure stockée qui a une instruction SELECT avec une clause FOR XML. [FOR XML (SQL Server)](https://msdn.microsoft.com/library/ms178107.aspx) contient des informations supplémentaires.
  
 Vous pouvez utiliser la station de travail WCF [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] pour exécuter ces procédures stockées.  
  
> [!IMPORTANT]
>  L’adaptateur SQL « natif » disponible avec [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] requiert que les procédures stockées pour que la clause FOR XML dans le cadre de l’instruction SELECT. Vous pouvez utiliser ces procédures stockées avec le WCF [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] sans apporter de modifications à la définition de procédure stockée.  
>   
>  Vous pouvez toujours utiliser les schémas générés à l’aide de l’adaptateur SQL 'native' fourni avec les versions antérieures de [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]. Pour plus d’informations, consultez [requêtes à l’aide de FOR XML avec l’adaptateur WCF-SQL](http://go.microsoft.com/fwlink/?LinkId=223428) (http://go.microsoft.com/fwlink/?LinkId=223428).  
  
## <a name="how-to-invoke-stored-procedures-with-for-xml-clause"></a>L’appel de procédures stockées avec la Clause FOR XML  
 Quand vous appelez une procédure stockée avec la clause FOR XML dans SQL Server Management Studio ou à l’aide de l’adaptateur SQL disponible avec [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], la sortie est sous la forme d’un message xml. Pour utiliser ces procédures avec le WCF [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)], vous devez disposer du schéma du message de sortie. La station de travail WCF [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] requiert ce schéma lors de la réception du message de réponse à partir de SQL Server après l’exécution d’une procédure stockée avec la clause FOR XML. Notez que le message de demande pour appeler cette procédure stockée est généré par l’adaptateur lui-même.  
  
 En plus de comporter le schéma pour le message de réponse, vous devez également effectuer certaines tâches pour appeler une procédure stockée avec la clause FOR XML à l’aide de la station de travail WCF [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].  
  
1.  Générer le schéma pour le message de réponse pour la procédure stockée avec la clause FOR XML. Si vous avez déjà le schéma de réponse généré par l’adaptateur SQL « natif » disponible avec [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], vous pouvez ignorer cette étape.  
  
2.  Créez un projet BizTalk et ajouter le schéma généré pour le projet.  
  
3.  Générer le schéma de la procédure stockée avec la clause FOR XML à l’aide de la station de travail WCF [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]. Cela fournit le schéma du message de demande que l’adaptateur envoie à SQL Server pour appeler la procédure stockée.  
  
4.  Créer des messages dans le projet BizTalk pour envoyer et recevoir des messages à partir de SQL Server. Le message de demande doit être conforme au schéma du message de demande généré par l’adaptateur. Le message de réponse doit être conforme au schéma du message de réponse obtenue soit à l’aide de l’adaptateur SQL « natif » ou en exécutant la procédure stockée avec la clause FOR XML dans SQL Server Management Studio.  
  
5.  Créez une orchestration pour appeler la procédure stockée dans la base de données SQL Server.  
  
6.  Générez et déployez le projet BizTalk.  
  
7.  Configurer l’application en créant physique d’envoi et ports de réception BizTalk.  
  
8.  Démarrez l’application BizTalk.  
  
##  <a name="BKMK_RespSchema"></a>Génération de schéma pour le Message de réponse pour la procédure stockée  
  
> [!NOTE]
>  Vous n’avez pas besoin d’effectuer cette étape si vous avez généré par l’adaptateur SQL disponible avec le schéma de réponse [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].  
  
 Vous pouvez générer le schéma pour le message de réponse pour la procédure stockée, condition de l’instruction SELECT dans la procédure stockée comporte la `xmlschema` clause avec la `for xml` clause. Dans cette rubrique, nous utilisons la procédure stockée de GET_EMP_DETAILS_FOR_XML qui Récupère les détails de l’employé pour un ID d’employé donné. Pour récupérer le schéma en exécutant la procédure stockée, l’instruction SELECT se présente comme suit :  
  
```  
SELECT [Employee_ID] ,[Name] ,[DOJ] ,[Designation] ,[Job_Description] ,[Photo] ,cast([Rating] as varchar(100)) as Rating ,[Salary] ,[Last_Modified] ,[Status] ,[Address]   
FROM [Adapt_Doc].[dbo].[Employee] for xml auto, xmlschema  
```  
  
 Exécutez cette procédure stockée pour obtenir le schéma pour le message de réponse. Notez que la réponse à partir de la procédure stockée contienne le schéma, ainsi que les données à partir de l’exécution de la procédure stockée. Vous devez copier le schéma de la réponse et enregistrez-la dans un bloc de texte. Pour cet exemple, vous pouvez nommer ce schéma en tant que **ResponseSchema.xsd**. Vous devez maintenant créer un projet BizTalk dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] et ajoutez ce schéma au projet.  
  
> [!IMPORTANT]
>  Veillez à supprimer la `xmlschema` clause après avoir exécuté la procédure stockée pour générer le schéma. Si vous ne le faites pas, lorsque vous exécutez pour finir la procédure stockée via BizTalk, vous générerez à nouveau le schéma du message de réponse. Par conséquent, pour obtenir le message de réponse en tant que xml, vous devez supprimer la `xmlschema` clause.  
  
#### <a name="to-add-the-schema-to-a-biztalk-project"></a>Pour ajouter le schéma à un projet BizTalk  
  
1.  Créez un projet BizTalk dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)].  
  
2.  Ajoutez le schéma de réponse que vous avez généré pour la procédure stockée au projet BizTalk. Cliquez sur le projet BizTalk dans l’Explorateur de solutions, pointez sur **ajouter**, puis cliquez sur **élément existant**. Dans la boîte de dialogue Ajouter un élément existant, accédez à l’emplacement où vous avez enregistré le schéma et cliquez sur **ajouter**.  
  
3.  Ouvrez le schéma dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] et apportez les modifications suivantes.  
  
    1.  Ajouter un nœud au schéma et déplacer le nœud racine existant sous ce nœud qui vient d’être ajouté. Donnez un nom pour le nœud racine. Pour cette rubrique, renommez le nœud racine de **racine**.  
  
    2.  Le schéma de réponse généré pour la procédure stockée fait référence à un sqltypes.xsd. Vous pouvez obtenir le schéma sqltypes.xsd [http://go.microsoft.com/fwlink/?LinkId=131087](http://go.microsoft.com/fwlink/?LinkId=131087). Ajoutez le schéma sqltypes.xsd au projet BizTalk.  
  
    3.  Dans le schéma généré pour la procédure stockée, modifiez la valeur de `import schemaLocation` à ce qui suit.  
  
        ```  
        import schemaLocation=”sqltypes.xsd”  
        ```  
  
         Pour cela, car vous avez déjà ajouté le schéma sqltypes.xsd à votre projet BizTalk.  
  
    4.  Fournir un espace de noms cible du schéma. Cliquez sur le  **\<schéma >** nœud et dans le volet Propriétés, spécifiez un espace de noms dans le **cible Namespace** propriété. Pour cette rubrique, donnez à l’espace de noms `http://ForXmlStoredProcs/namespace`.  
  
## <a name="generating-schema-for-the-request-message-to-invoke-the-stored-procedure"></a>Génération du schéma du Message de demande appeler la procédure stockée  
 Pour générer le schéma du message de requête que vous pouvez utiliser la [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] à partir d’un projet BizTalk dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]. Pour cette rubrique, générez le schéma pour la procédure stockée de GET_EMP_DETAILS_FOR_XML. Pour plus d’informations sur la façon de générer le schéma à l’aide de [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], consultez [récupérer des métadonnées pour les opérations de SQL Server dans Visual Studio à l’aide de l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/get-metadata-for-sql-server-operations-in-visual-studio-using-the-sql-adapter.md).  
  
> [!IMPORTANT]
>  Vous devez générer le schéma en sélectionnant la procédure uniquement à partir de la **procédures** nœud [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)].  
  
## <a name="defining-messages-and-message-types"></a>Définition des Messages et les Types de messages  
 Le schéma que vous avez généré précédemment décrit les « types » requis pour les messages dans l’orchestration. Un message est généralement une variable, le type est défini par le schéma correspondant. Vous devez maintenant créer des messages pour l’orchestration et les lier aux schémas que vous avez créé à l’étape précédente.  
  
#### <a name="to-create-messages-and-link-to-schema"></a>Pour créer des messages et le lier au schéma  
  
1.  Ajouter une orchestration au projet BizTalk. À partir de l’Explorateur de solutions, cliquez sur le nom du projet BizTalk, pointez sur **ajouter**, puis cliquez sur **un nouvel élément**. Tapez un nom pour l’orchestration BizTalk, puis cliquez sur **ajouter**.  
  
2.  Ouvrez la fenêtre Vue Orchestration du projet BizTalk, s’il n’est pas déjà ouvert. Pour ce faire, cliquez sur **vue**, pointez sur **autres fenêtres**, puis cliquez sur **Vue Orchestration**.  
  
3.  Dans la vue Orchestration, cliquez sur **Messages**, puis cliquez sur **nouveau Message**.  
  
4.  Cliquez sur le message qui vient d’être créé, puis sélectionnez **fenêtre Propriétés**.  
  
5.  Dans le **propriétés** volet pour le **Message_1**, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |Identificateur|Type`Request`|  
    |Type de message|Dans la liste déroulante, développez **schémas**, puis sélectionnez *ForXMLProcedure.Procedure_dbo. GET_EMP_DETAILS_FOR_XML*, où ForXMLProcedure est le nom de votre projet BizTalk. Procedure_dbo est le schéma généré pour appeler la procédure GET_EMP_DETAILS_FOR_XML.|  
  
6.  Répétez l’étape 2 pour créer un nouveau message. Dans le **propriétés** volet pour le nouveau message, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |Identificateur|Type`Response`|  
    |Type de message|Dans la liste déroulante, développez **schémas**, puis sélectionnez *ForXMLProcedure.ResponseSchema*, où ResponseSchema est le nom du schéma de réponse généré par l’exécution de la procédure stockée en tant que décrit sous [génération de schéma pour le Message de réponse pour la procédure stockée](#BKMK_RespSchema).|  
  
## <a name="setting-up-the-orchestration"></a>Configuration de l’Orchestration  
 Vous devez créer une orchestration BizTalk à utiliser [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] pour exécuter une procédure stockée dans SQL Server. Dans cette orchestration, vous déposez un message de demande à une emplacement de réception. Le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] consomme ce message et le transmet à SQL Server. La réponse à partir de SQL Server est enregistrée dans un autre emplacement. Vous devez inclure l’envoi et reçoivent des formes pour envoyer des messages à SQL Server et de recevoir des réponses, respectivement. Un exemple d’orchestration permettant d’appeler une procédure semblable au suivant :  
  
 ![Orchestration permettant d’appeler des procédures stockées](../../adapters-and-accelerators/adapter-sql/media/eac6e8b6-f0f4-44af-8218-03ca3864b267.gif "eac6e8b6-f0f4-44af-8218-03ca3864b267")  
  
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
|MessageIn|-Définissez **identificateur** à *(messagein)*<br />-Définissez **Type** à *MessageInType*<br />-Définissez **modèle de Communication** à *à sens unique*<br />-Définissez **Direction de Communication** à *de réception*|  
|LOBPort|-Définissez **identificateur** à *LOBPort*<br />-Définissez **Type** à *LOBPortType*<br />-Définissez **modèle de Communication** à *demande-réponse*<br />-Définissez **Direction de Communication** à *envoi / réception*|  
|ResponseOut|-Définissez **identificateur** à *ResponseOut*<br />-Définissez **Type** à *ResponseOutType*<br />-Définissez **modèle de Communication** à *à sens unique*<br />-Définissez **Direction de Communication** à *envoyer*|  
  
### <a name="specify-messages-for-action-shapes-and-connect-them-to-ports"></a>Spécifier des Messages pour les formes d’Action et connectez-les aux Ports  
 Le tableau suivant indique les propriétés et leurs valeurs, vous devez définir pour spécifier les messages de formes d’action et lier les messages aux ports. Les noms répertoriés dans la colonne de forme sont les noms des formes de message tel qu’affiché dans l’orchestration mentionnée précédemment.  
  
|Graphique à base de formes|Propriétés|  
|-----------|----------------|  
|ReceiveMessage|-Définissez **Message** à *demande*<br />-Définissez **opération** à *MessageIn.FOR_XML. Demande*|  
|SendMessage|-Définissez **Message** à *demande*<br />-Définissez **opération** à *LOBPort.FOR_XML. Demande*|  
|Réception réponse|-Définissez **Message** à *réponse*<br />-Définissez **opération** à *LOBPort.FOR_XML. Réponse*|  
|SendResponse|-Définissez **Message** à *réponse*<br />-Définissez **opération** à *ResponseOut.FOR_XML. Demande*|  
  
 Une fois que vous avez défini ces propriétés, les formes de message et les ports sont connectés et l’orchestration est terminée.  
  
 Vous devez maintenant générer la solution BizTalk et déployez-le dans un [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]. Pour plus d’informations, consultez [génération et exécution des Orchestrations](../../core/building-and-running-orchestrations.md).
  
## <a name="configuring-the-biztalk-application"></a>Configuration de l’Application BizTalk  
 Après avoir déployé le projet BizTalk, l’orchestration que vous avez créé précédemment est répertoriée sous le volet Orchestrations dans la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration. Vous devez utiliser le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration pour configurer l’application. Pour une procédure pas à pas, consultez [procédure pas à pas : déploiement d’une Application BizTalk base](Walkthrough:%20Deploying%20a%20Basic%20BizTalk%20Application.md).
  
 Configuration d’une application implique :  
  
-   Sélection d’un hôte de l’application.  
  
-   Mappage de ports que vous avez créé dans l’orchestration aux ports physiques dans le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration. Pour cette orchestration, vous devez :  
  
    -   Définir un emplacement sur le disque dur et un port de fichier correspondant où vous allez déposer un message de demande. L’orchestration BizTalk consommer le message de demande et l’envoyer à la base de données SQL Server.  
  
    -   Définir un emplacement sur le disque dur et un port de fichier correspondant dans lequel l’orchestration BizTalk supprimera le message de réponse contenant la réponse à partir de la base de données SQL Server.  
  
    -   Définir un port d’envoi WCF-Custom ou WCF-SQL physique pour envoyer des messages à la base de données SQL Server. Pour obtenir des instructions sur la création d’un port d’envoi, consultez [configurer manuellement une liaison de port physique à l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/manually-configure-a-physical-port-binding-to-the-sql-adapter.md).
  
         Vous devez également spécifier l’action dans le port d’envoi. Pour les procédures qui contiennent la clause FOR XML, vous devez définir l’action dans le format suivant.  
  
        ```  
        XmlProcedure/<schema_name>/<procedure_name>  
        ```  
  
         Par conséquent, pour cette rubrique où nous examinons l’exécution de la procédure GET_EMP_DETAILS_FOR_XML, l’action sera :  
  
        ```  
        XmlProcedure/dbo/GET_EMP_DETAILS_FOR_XML  
        ```  
  
         Pour plus d’informations sur l’action de paramètre, consultez [configurer l’action SOAP pour l’adaptateur SQL ](../../adapters-and-accelerators/adapter-sql/configure-the-soap-action-for-the-sql-adapter.md).
  
         Vous devez également définir les propriétés de liaison suivantes lors de l’exécution d’une procédure stockée avec la clause FOR XML.  
  
        |Nom de propriété de liaison|Affectez la valeur|  
        |---------------------------|-----------------|  
        |XmlStoredProcedureRootNodeName|Spécifiez le nom du nœud racine que vous avez ajouté pour le schéma de réponse que vous avez généré pour la procédure stockée, comme indiqué dans [génération de schéma pour le Message de réponse pour la procédure stockée](#BKMK_RespSchema). Pour cette rubrique, affectez la valeur **racine**.|  
        |XmlStoredProcedureRootNodeNamespace|Spécifier l’espace de noms cible pour le schéma de réponse que vous avez généré pour la procédure stockée, comme décrit sous [génération de schéma pour le Message de réponse pour la procédure stockée](#BKMK_RespSchema). Pour cette rubrique, affectez la valeur `http://ForXmlStoredProcs/namespace`.|  
  
         Pour plus d’informations sur la spécification des valeurs de propriétés de liaison, consultez [configurer les propriétés de liaison de l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/configure-the-binding-properties-for-the-sql-adapter.md).  
  
        > [!NOTE]
        >  Génération de schéma à l’aide du [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] crée également un fichier de liaison qui contient des informations sur les ports et les actions à définir pour ces ports. Vous pouvez importer ce fichier de liaison à partir de la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration pour créer des ports d’envoi (pour les appels sortants) ou de ports de réception (d’appels entrants). Pour plus d’informations, consultez [configurer une liaison de port physique à l’aide d’un fichier de liaison de port à utiliser l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/configure-a-physical-port-binding-using-a-port-binding-file-to-sql-adapter.md).
  
## <a name="starting-the-application"></a>Démarrage de l’Application  
 Vous devez démarrer l’application BizTalk pour appeler les procédures dans la base de données SQL Server. Pour obtenir des instructions sur le démarrage d’une application BizTalk, consultez [comment démarrer une Orchestration](../../core/how-to-start-an-orchestration.md).
  
 À ce stade, vérifiez que :  
  
-   Le fichier de port de réception pour recevoir des messages de demande pour l’orchestration est en cours d’exécution.  
  
-   Le port d’envoi FILE pour recevoir les messages de réponse à partir de l’orchestration est en cours d’exécution.  
  
-   Le port d’envoi WCF-Custom ou WCF-SQL pour envoyer des messages à la base de données SQL Server est en cours d’exécution.  
  
-   L’orchestration BizTalk pour l’opération est en cours d’exécution.  
  
## <a name="executing-the-operation"></a>L’exécution de l’opération  
 Après avoir exécuté l’application, vous devez supprimer un message de demande pour le fichier de l’emplacement de réception. Le schéma du message de demande doit être conforme au schéma de requête pour la procédure que vous avez généré à l’aide de la [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]. Par exemple, le message de demande pour appeler le code XML GET_EMP_DETAILS_FOR est la suivante :  
  
```  
<GET_EMP_DETAILS_FOR_XML xmlns="http://schemas.microsoft.com/Sql/2008/05/Procedures/dbo">  
  <emp_id>10765</emp_id>  
</GET_EMP_DETAILS_FOR_XML>  
```  
  
 Consultez [des schémas de Message pour les procédures et fonctions](../../adapters-and-accelerators/adapter-sql/message-schemas-for-procedures-and-functions.md) pour plus d’informations sur le schéma de message de demande pour l’appel des procédures dans SQL Server de base de données à l’aide de la [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].  
  
 L’orchestration consomme le message et l’envoie à la base de données SQL Server. La réponse à partir de la base de données SQL Server est enregistrée dans l’autre emplacement de fichier définie dans le cadre de l’orchestration. Par exemple, la réponse à partir de la base de données SQL Server pour le précédent message de demande est la suivante :  
  
```  
\<?xml version="1.0" encoding="utf-8"?>  
<Root xmlns="http://ForXmlStoredProcs/namespace">  
  \<Adapt_Doc.dbo.Employee Employee_ID="10765" Name="John" Designation="asdfaf" Salary="3434.00" Last_Modified="AAAAAAAANso=" Status="0" xmlns="" />  
</Root>  
```  
  
 Notez que la réponse est reçue dans le même schéma, tel que généré par l’exécution de la procédure stockée. Notez également que le nœud racine et l’espace de noms est celui que vous avez spécifié en tant que valeurs pour **XmlStoredProcedureRootNodeName** et **XmlStoredProcedureRootNodeNamespace** respectivement les propriétés de liaison.  
  
## <a name="best-practices"></a>Bonnes pratiques  
 Après avoir déployé et configuré le projet BizTalk, vous pouvez exporter les paramètres de configuration dans un fichier XML appelé le fichier de liaison. Une fois que vous générez un fichier de liaison, vous pouvez importer les paramètres de configuration à partir du fichier, afin que vous n’avez pas besoin de créer des éléments tels que les ports d’envoi et ports de réception d’une même orchestration. Pour plus d’informations sur les fichiers de liaison, consultez [réutiliser les liaisons de l’adaptateur](../../adapters-and-accelerators/adapter-sql/reuse-sql-adapter-bindings.md).  
  
## <a name="see-also"></a>Voir aussi  
[Développer des applications BizTalk à l’aide de l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/develop-biztalk-applications-using-the-sql-adapter.md)