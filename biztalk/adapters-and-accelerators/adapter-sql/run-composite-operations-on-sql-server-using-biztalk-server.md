---
title: "Exécuter des opérations composites sur SQL Server à l’aide de BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 86fd2aa1-20c7-4b58-9f35-83ba0c959cf1
caps.latest.revision: "21"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0f6891f300a89684481184bf255f3cdd54d25845
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="run-composite-operations-on-sql-server-using-biztalk-server"></a>Exécuter des opérations composites sur SQL Server à l’aide de BizTalk Server
Le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] permet aux clients d’adaptateur effectuer des opérations composites sur la base de données SQL Server. Une opération composite peut inclure :  
  
-   INSERT, Update et les opérations de suppression. Une opération Select n’est pas pris en charge dans le cadre d’une opération composite.  
  
-   Procédures stockées sont exécutées en tant qu’opérations.  
  
 Une seule opération composite peut avoir un nombre quelconque de ces opérations, dans n’importe quel ordre. Par exemple, vous pouvez avoir deux opérations d’insertion suivies d’une opération de suppression et enfin une exécution de la procédure stockée. En outre, vous pouvez avoir différentes opérations ciblant des tables de base de données différente ou des vues. Pour plus d’informations sur la façon dont l’adaptateur prend en charge des opérations composites, consultez [exécuter des opérations composites dans SQL Server à l’aide de l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/run-composite-operations-in-sql-server-using-the-sql-adapter.md). Pour plus d’informations sur la structure du message SOAP pour des opérations composites, consultez [des schémas de Message pour des opérations composites](../../adapters-and-accelerators/adapter-sql/message-schemas-for-composite-operations.md).  
  
> [!NOTE]
>  Si vous effectuez une opération sur les tables qui possèdent des colonnes de types définis par l’utilisateur, assurez-vous que vous faites référence à [opérations sur les Tables et les vues avec les Types définis par l’utilisateur à l’aide de l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/operations-on-tables-and-views-with-user-defined-types-using-the-sql-adapter.md) avant de commencer à développer votre application.  
  
## <a name="how-to-perform-composite-operations-on-sql-server"></a>Comment effectuer des opérations composites sur SQL Server  
 Une opération sur l’utilisation de SQL Server le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] avec [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] implique les tâches de procédures décrites dans [blocs de construction pour développer des applications BizTalk à l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/building-blocks-to-develop-biztalk-applications-with-the-sql-adapter.md). Pour effectuer des opérations composites sur la base de données SQL Server, ces tâches sont :  
  
1.  Créez un projet BizTalk et générer le schéma pour toutes les opérations que vous souhaitez appeler.  
  
2.  Créer manuellement un fichier de schéma qui inclut des références à tous les schémas que vous avez créé à l’étape précédente.  
  
3.  Créer des messages dans le projet BizTalk pour envoyer et recevoir des messages à partir de la base de données SQL Server. Ces messages doivent respecter le schéma de demande et de réponse que vous avez créé à l’étape précédente.  
  
4.  Créez une orchestration pour appeler l’opération composite sur la base de données SQL Server.  
  
5.  Générez et déployez le projet BizTalk.  
  
6.  Configurer l’application en créant physique d’envoi et ports de réception BizTalk.  
  
7.  Démarrez l’application BizTalk.  
  
 Cette rubrique fournit des instructions sur la façon d’effectuer ces tâches.  
  
## <a name="sample-based-on-this-topic"></a>Exemple basé sur cette rubrique  
 Un exemple CompositeOperations, en fonction de cette rubrique est fourni avec le [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]. Pour plus d’informations, consultez [exemples de l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/samples-for-the-sql-adapter.md).  
  
## <a name="generating-schema"></a>Génération du schéma  
 Dans cette rubrique, pour montrer comment effectuer des opérations composites, les tâches suivantes seront effectuées dans l’ordre spécifié :  
  
-   Insérer l’enregistrement dans la table EMPLOYEE.  
  
-   Récupérer toutes les colonnes pour le dernier enregistrement inséré en appelant la procédure stockée de GET_LAST_EMP_DATA.  
  
-   Supprimer l’enregistrement de la table EMPLOYEE.  
  
 Exécutez les scripts fournis avec les exemples pour créer la table EMPLOYEE. Pour plus d’informations sur les exemples, consultez [exemples de schéma](../../adapters-and-accelerators/accelerator-rosettanet/schema-samples.md).  
  
 Vous devez créer un projet BizTalk et utiliser le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] pour générer le schéma pour ces opérations. Consultez [récupérer des métadonnées pour les opérations de SQL Server dans Visual Studio à l’aide de l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/get-metadata-for-sql-server-operations-in-visual-studio-using-the-sql-adapter.md) pour plus d’informations sur la façon de générer des schémas.  
  
## <a name="creating-a-composite-schema-definition"></a>Création d’une définition de schéma Composite  
 Vous devez maintenant créer un schéma composite qui fait référence à des schémas créés pour les opérations individuelles. Procédez comme suit pour créer une définition de schéma composite.  
  
#### <a name="to-add-a-composite-schema-definition"></a>Pour ajouter une définition de schéma composite  
  
1.  Ajouter un fichier de schéma au projet BizTalk. Cliquez sur le nom du projet, pointez sur **ajouter**, puis cliquez sur **un nouvel élément**. Dans le **ajouter un nouvel élément** boîte de dialogue, à partir de la **catégories** , cliquez sur **les fichiers de schéma**. À partir de la **modèles** , cliquez sur **schéma**. Spécifiez un nom pour le fichier de schéma, puis cliquez sur **OK**.  
  
     Pour cet exemple, spécifiez le nom de fichier de schéma en tant que `CompositeSchema.xsd`.  
  
2.  Ajouter des références au schéma généré pour les différentes opérations que vous souhaitez effectuer. Dans cet exemple, les différents schémas générés pour les opérations sont :  
  
    -   TableOperation.dbo.Employee.xsd, pour les opérations Insert et Delete.  
  
    -   PROCEDURE.dbo.xsd, pour le GET_LAST_EMP_DATA procédure stockée.  
  
     Pour ajouter des références :  
  
    1.  Avec le bouton droit de la racine  **\<schéma\>**  nœud dans le CompositeSchema.xsd, puis cliquez sur **propriétés**.  
  
    2.  Dans le **propriété** , cliquez sur le bouton de sélection **(...)**  contre le **importations** propriété.  
  
         ![Importer les définitions de schéma](../../adapters-and-accelerators/adapter-oracle-database/media/d084d0f0-60b5-4ae8-9e80-7ed2c9e3ecca.gif "d084d0f0-60b5-4ae8-9e80-7ed2c9e3ecca")  
  
    3.  Dans le **importations** boîte de dialogue, à partir de la **importer le nouveau schéma en tant que** liste, sélectionnez **XSD : importer**, puis cliquez sur **ajouter**.  
  
    4.  Dans le **sélecteur de Type BizTalk** boîte de dialogue, développez le nœud de nom de projet BizTalk, développez **schémas**, puis sélectionnez le schéma que vous souhaitez importer. Dans cet exemple, sélectionnez < BizTalk_project_name >. TableOperation_dbo_Employee. Cliquez sur **OK**.  
  
         Répétez cette étape pour importer < BizTalk_project_name >. Procedure_dbo trop.  
  
    5.  Dans le **importations** boîte de dialogue, cliquez sur **OK**.  
  
3.  Ajoutez deux nœuds enfants au nœud de schéma racine. Un nœud enfant correspond au schéma de requête de l’opération composite. L’autre nœud enfant correspond au schéma de réponse. Le nœud qui correspond au schéma de requête peut avoir n’importe quel nom. Le nœud qui correspond au schéma de réponse doit être appelé < request_schema_node > réponse. Pour cet exemple, nous appelons le nœud de schéma de demande en tant que **demande**. Par conséquent, le nœud de schéma de réponse est appelé **requête-réponse**.  
  
    > [!NOTE]
    >  Par défaut, un **racine** nœud est également ajouté à un fichier de schéma. Vous pouvez renommer la **racine** nœud **demande**. Pour renommer un nœud, cliquez sur le nom de nœud et cliquez sur **renommer**.  
  
     Pour ajouter un nœud sous la  **\<schéma\>**  nœud :  
  
    1.  Avec le bouton droit le  **\<schéma\>**  nœud **insérer un nœud de schéma**, puis cliquez sur **enregistrement enfant**.  
  
    2.  Renommez le nouveau nœud **requête-réponse**.  
  
4.  Ajouter des nœuds enfants sous le **demande** nœud qui correspondent au schéma de requête pour chaque opération que vous effectuerez dans le cadre de l’opération composite. Pour cet exemple, vous devez ajouter des nœuds enfants correspondant à ce qui suit :  
  
    -   Insérer et supprimer des opérations sur la table EMPLOYEE.  
  
    -   GET_LAST_EMP_DATA de procédure stockée.  
  
    > [!IMPORTANT]
    >  Vous devez ajouter les nœuds dans le même ordre que celui dans lequel vous souhaitez effectuer les opérations. Par exemple, si vous souhaitez insérer un enregistrement, puis exécuter une procédure stockée et supprimez un enregistrement, vous devez d’abord ajouter un nœud pour l’opération d’insertion, suivi par un nœud de la procédure stockée et enfin sur un nœud pour l’opération de suppression.  
  
     Pour ajouter des nœuds enfants à la **demande** nœud :  
  
    1.  Avec le bouton droit le **demande** nœud **insérer un nœud de schéma**, puis cliquez sur **enregistrement enfant**.  
  
         ![Insérer des nœuds enfants pour un schéma](../../adapters-and-accelerators/adapter-oracle-database/media/58992131-13a6-45c3-9513-5c0995091fae.gif "58992131-13a6-45c3-9513-5c0995091fae")  
  
    2.  Renommer l’enregistrement pour correspondre à un schéma de demande pour une opération que vous effectuez dans le cadre de l’opération composite. Par exemple, renommer le nœud « INSERT ».  
  
    3.  Mappage de la **insérer** nœud pour le schéma de demande pour l’opération d’insertion sur la table EMPLOYEE. Pour ce faire, cliquez sur le **insérer** nœud, puis cliquez sur **propriétés**. Dans le **propriétés** zone, à partir de la **Data Structure Type** liste, sélectionnez **Insert (référence)**.  
  
         ![Mapper des nœuds enfants au schéma request](../../adapters-and-accelerators/adapter-sql/media/5ace18be-0fe8-44c6-bd2f-cb19035494b5.gif "5ace18be-0fe8-44c6-bd2f-cb19035494b5")  
  
    4.  Répétez ces étapes pour ajouter des nœuds pour les schémas de requête pour la procédure GET_LAST_EMP_DATA stockées et de l’opération de suppression. Spécifiez les noms des nœuds et les mapper vers le schéma correspondant, comme indiqué dans le tableau suivant.  
  
        |Nom de nœud|Mappé au schéma|  
        |---------------|----------------------|  
        |GET_LAST_EMP_DATA|GET_LAST_EMP_DATA (référence)|  
        |DELETE|Delete (référence)|  
  
5.  Ajouter des nœuds enfants sous le **requête-réponse** nœud qui correspondent au schéma de réponse pour chaque opération que vous effectuerez dans le cadre de l’opération composite. Pour cet exemple, vous devez ajouter des nœuds enfants correspondant à ce qui suit :  
  
    -   Insérer et supprimer des opérations sur la table EMPLOYEE.  
  
    -   GET_LAST_EMP_DATA de procédure stockée.  
  
    > [!IMPORTANT]
    >  Vous devez ajouter les nœuds enfants dans le même ordre que les nœuds enfants sous le **demande** nœud.  
  
     Pour ajouter des nœuds enfants à la **requête-réponse** nœud :  
  
    1.  Avec le bouton droit le **requête-réponse** nœud **insérer un nœud de schéma**, puis cliquez sur **enregistrement enfant**.  
  
    2.  Renommer l’enregistrement pour correspondre à un schéma de réponse pour une opération que vous effectuez dans le cadre de l’opération composite. Par exemple, renommer le nœud à « InsertResponse ».  
  
    3.  Mappage de la **InsertResponse** nœud pour le schéma de réponse pour l’opération d’insertion sur la table EMPLOYEE. Pour ce faire, cliquez sur le **InsertResponse** nœud, puis cliquez sur **propriétés**. Dans le **propriétés** zone, à partir de la **Data Structure Type** liste, sélectionnez **InsertResponse (référence)**.  
  
    4.  Répétez ces étapes pour ajouter des nœuds pour les schémas de réponse pour la procédure stockée de GET_LAST_EMP_DATA et l’opération de suppression. Spécifiez les noms des nœuds et les mapper vers le schéma correspondant, comme indiqué dans le tableau suivant.  
  
        |Nom de nœud|Mappé au schéma|  
        |---------------|----------------------|  
        |GET_LAST_EMP_DATAResponse|GET_LAST_EMP_DATAResponse (référence)|  
        |DeleteResponse|DeleteResponse (référence)|  
  
6.  Enregistrer le **CompositeSchema.xsd** fichier.  
  
## <a name="defining-messages-and-message-types"></a>Définition des Messages et les Types de messages  
 Le schéma composite que vous avez créé dans la dernière étape décrit les « types » requis pour les messages dans une orchestration. Un message est généralement une variable, le type est défini par le schéma correspondant. Vous devez maintenant créer des messages pour l’orchestration et les lier au schéma que vous avez créé à l’étape précédente.  
  
#### <a name="to-create-messages-and-link-to-schema"></a>Pour créer des messages et le lier au schéma  
  
1.  Ajouter une orchestration au projet BizTalk. À partir de l’Explorateur de solutions, cliquez sur le nom du projet BizTalk, pointez sur **ajouter**, puis cliquez sur **un nouvel élément**. Tapez un nom pour l’orchestration BizTalk, puis cliquez sur **ajouter**.  
  
2.  Ouvrez la fenêtre Vue Orchestration du projet BizTalk, s’il n’est pas déjà ouvert. Pour ce faire, cliquez sur **vue**, pointez sur **autres fenêtres**, puis cliquez sur **Vue Orchestration**.  
  
3.  Dans la vue Orchestration, cliquez sur **Messages**, puis cliquez sur **nouveau Message**.  
  
4.  Cliquez sur le message qui vient d’être créé, puis sélectionnez **fenêtre Propriétés**.  
  
5.  Dans le **propriétés** volet pour le **Message_1**, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |Identificateur|Type`Request`|  
    |Type de message|Dans la liste déroulante, développez **schémas**, puis sélectionnez *CompositeOp.CompositeSchema.Request*, où CompositeOp est le nom de votre projet BizTalk. CompositeSchema est le schéma que vous avez créé manuellement pour les opérations composites.|  
  
6.  Répétez l’étape 2 pour créer un nouveau message. Dans le **propriétés** volet pour le nouveau message, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |Identificateur|Type`Response`|  
    |Type de message|Dans la liste déroulante, développez **schémas**, puis sélectionnez *CompositeOp.CompositeSchema.RequestResponse*.|  
  
## <a name="setting-up-the-orchestration"></a>Configuration de l’Orchestration  
 Vous devez créer une orchestration BizTalk à utiliser [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] pour effectuer des opérations composites sur SQL Server. Dans cette orchestration, vous déposez un message de demande à une emplacement de réception. Le message de demande doit être conforme au schéma composite que vous avez créé précédemment. Le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] consomme ce message et le transmet à SQL Server. La réponse à partir de SQL Server est enregistrée dans un autre emplacement. Vous devez inclure l’envoi et reçoivent des formes pour envoyer des messages à SQL Server et de recevoir des réponses, respectivement. Une orchestration de base pour effectuer des opérations composites ressemble à ceci :  
  
 ![Orchestration permettant d’effectuer des opérations composites](../../adapters-and-accelerators/adapter-oracle-database/media/4a1ecae7-8bf2-4c8a-a413-34d6a402cbfb.gif "4a1ecae7-8bf2-4c8a-a413-34d6a402cbfb")  
  
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
|ReceiveMessage|-Définissez **Message** à *demande*<br />-Définissez **opération** à *MessageIn.CompositeOp.Request*|  
|SendMessage|-Définissez **Message** à *demande*<br />-Définissez **opération** à *LOBPort.CompositeOp.Request*|  
|Réception réponse|-Définissez **Message** à *réponse*<br />-Définissez **opération** à *LOBPort.CompositeOp.Response*|  
|SendResponse|-Définissez **Message** à *réponse*<br />-Définissez **opération** à *ResponseOut.CompositeOp.Request*|  
  
 Une fois que vous avez défini ces propriétés, les formes de message et les ports sont connectés et l’orchestration est terminée.  
  
 Vous devez maintenant générer la solution BizTalk et déployez-le dans un [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]. Pour plus d’informations, consultez [génération et exécution des Orchestrations](../../core/building-and-running-orchestrations.md).
  
## <a name="configuring-the-biztalk-application"></a>Configuration de l’Application BizTalk  
 Après avoir déployé le projet BizTalk, l’orchestration que vous avez créé précédemment est répertoriée sous le volet Orchestrations dans la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration. Vous devez utiliser le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration pour configurer l’application. Pour une procédure pas à pas, consultez [procédure pas à pas : déploiement d’une Application BizTalk base](Walkthrough:%20Deploying%20a%20Basic%20BizTalk%20Application.md).
  
 Configuration d’une application implique :  
  
-   Sélection d’un hôte de l’application.  
  
-   Mappage de ports que vous avez créé dans l’orchestration aux ports physiques dans le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration. Pour cette orchestration, vous devez :  
  
    -   Définir un emplacement sur le disque dur et un port de fichier correspondant où vous allez déposer un message de demande. L’orchestration BizTalk consommer le message de demande et l’envoyer à la base de données SQL Server.  
  
    -   Définir un emplacement sur le disque dur et un port de fichier correspondant dans lequel l’orchestration BizTalk supprimera le message de réponse contenant la réponse à la base de données SQL Server.  
  
    -   Définir un port d’envoi WCF-Custom ou WCF-SQL physique pour envoyer des messages à la base de données SQL Server. Étant donné que les opérations étant comme partie de l’opération composite sont exécutées dans une transaction unique, assurez-vous que le **UseAmbientTransaction** liaison de la propriété est définie sur **True**.  
  
         Vous devez également spécifier l’action dans le port d’envoi. L’action pour une opération composite est «**CompositeOperation**». Pour plus d’informations sur la création de ports, consultez [configurer manuellement une liaison de port physique à l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/manually-configure-a-physical-port-binding-to-the-sql-adapter.md). Pour plus d’informations sur la façon de spécifier des actions pour les ports, consultez [configurer l’action SOAP pour l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/configure-the-soap-action-for-the-sql-adapter.md).
  
        > [!NOTE]
        >  Génération de schéma à l’aide du [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] crée également un fichier de liaison qui contient des informations sur les ports et les actions à définir pour ces ports. Vous pouvez importer ce fichier de liaison à partir de la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration pour créer des ports d’envoi (pour les appels sortants) ou de ports de réception (d’appels entrants). Pour plus d’informations, consultez [configurer une liaison de port physique à l’aide d’un fichier de liaison de port à utiliser l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/configure-a-physical-port-binding-using-a-port-binding-file-to-sql-adapter.md). Si vous importez ce fichier de liaison, l’action sur le port d’envoi WCF-Custom ou WCF-SQL est définie à une action dynamique impliquant toutes les opérations que vous avez sélectionné dans le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] lors de la génération du schéma. Pour une opération composite, vous devez remplacer l’action dynamique avec « CompositeOperation ».  
  
## <a name="starting-the-application"></a>Démarrage de l’Application  
 Vous devez démarrer l’application BizTalk pour effectuer des opérations composites sur la base de données SQL Server. Pour obtenir des instructions sur le démarrage d’une application BizTalk, consultez [comment démarrer une Orchestration](../../core/how-to-start-an-orchestration.md).
  
 À ce stade, vérifiez que :  
  
-   Le fichier de port de réception pour recevoir des messages de demande pour l’orchestration est en cours d’exécution.  
  
-   Le port d’envoi FILE pour recevoir les messages de réponse à partir de l’orchestration est en cours d’exécution.  
  
-   Le port d’envoi WCF-Custom ou WCF-SQL pour envoyer des messages à la base de données SQL Server est en cours d’exécution.  
  
-   L’orchestration BizTalk pour l’opération est en cours d’exécution.  
  
## <a name="executing-the-operation"></a>L’exécution de l’opération  
 Après avoir exécuté l’application, vous devez supprimer un message de demande pour le fichier de l’emplacement de réception. Le schéma du message de demande doit être conforme au schéma pour les opérations composites que vous avez créé précédemment. Par exemple, un message de demande qui insère un enregistrement dans la table EMPLOYEE, appelle la procédure stockée de GET_LAST_EMP_DATA et supprime un enregistrement de la table EMPLOYEE est la suivante :  
  
```  
<Request xmlns="http://CompositeTest.CompositeSchema">  
  <Insert xmlns="http://schemas.microsoft.com/Sql/2008/05/TableOp/dbo/Employee">  
    <Rows>  
      <Employee xmlns="http://schemas.microsoft.com/Sql/2008/05/Types/Tables/dbo">  
        <Name>John</Name>  
        <Designation>Manager</Designation>  
        <Salary>100000</Salary>  
      </Employee>  
    </Rows>  
  </Insert>  
  <GET_LAST_EMP_DATA xmlns="http://schemas.microsoft.com/Sql/2008/05/Procedures/dbo" />  
  <Delete xmlns="http://schemas.microsoft.com/Sql/2008/05/TableOp/dbo/Employee">  
    <Rows>  
      <Employee xmlns="http://schemas.microsoft.com/Sql/2008/05/Types/Tables/dbo">  
        <Name>John</Name>  
      </Employee>  
    </Rows>  
  </Delete>  
</Request>  
```  
  
 Consultez [des schémas de Message pour des opérations composites](../../adapters-and-accelerators/adapter-sql/message-schemas-for-composite-operations.md) pour plus d’informations sur le schéma de message de demande pour effectuer des opérations composites sur le serveur SQL de base de données à l’aide de la [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].  
  
 L’orchestration consomme le message et l’envoie à la base de données SQL Server. La réponse à partir de la base de données SQL Server est enregistrée dans l’autre emplacement de fichier définie dans le cadre de l’orchestration. Par exemple, la réponse à partir de la base de données SQL Server pour le précédent message de demande est la suivante :  
  
```  
<?xml version="1.0" encoding="utf-8" ?>   
<RequestResponse xmlns="http://CompositeTest.CompositeSchema">  
  <InsertResponse xmlns="http://schemas.microsoft.com/Sql/2008/05/TableOp/dbo/Employee">  
    <InsertResult>  
      <long xmlns="http://schemas.microsoft.com/2003/10/Serialization/Arrays">10080</long>   
    </InsertResult>  
  </InsertResponse>  
  <GET_LAST_EMP_DATAResponse xmlns="http://schemas.microsoft.com/Sql/2008/05/Procedures/dbo">  
    <GET_LAST_EMP_DATAResult>  
      <DataSet xmlns="http://schemas.datacontract.org/2004/07/System.Data">  
        <xs:schema id="NewDataSet" xmlns:xs="http://www.w3.org/2001/XMLSchema" xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
          <xs:element msdata:IsDataSet="true" name="NewDataSet">  
            <xs:complexType>  
              <xs:sequence>  
                <xs:element minOccurs="0" maxOccurs="unbounded" name="NewTable">  
                  <xs:complexType>  
                    <xs:sequence>  
                      <xs:element minOccurs="0" name="Employee_ID" type="xs:int" />   
                      <xs:element minOccurs="0" name="Name" type="xs:string" />   
                      <xs:element minOccurs="0" name="DOJ" type="xs:dateTime" />   
                      <xs:element minOccurs="0" name="Designation" type="xs:string" />   
                      <xs:element minOccurs="0" name="Job_Description" type="xs:string" />   
                      <xs:element minOccurs="0" name="Photo" type="xs:base64Binary" />   
                      <xs:element minOccurs="0" name="Rating" type="xs:string" />   
                      <xs:element minOccurs="0" name="Salary" type="xs:decimal" />   
                      <xs:element minOccurs="0" name="Last_Modified" type="xs:base64Binary" />   
                    </xs:sequence>  
                  </xs:complexType>  
                </xs:element>  
              </xs:sequence>  
            </xs:complexType>  
          </xs:element>  
        </xs:schema>  
        <diffgr:diffgram xmlns:diffgr="urn:schemas-microsoft-com:xml-diffgram-v1">  
          <NewDataSet xmlns="">  
            <NewTable>  
              <Employee_ID>10080</Employee_ID>   
              <Name>John</Name>   
              <Designation>Manager</Designation>   
              <Salary>100000.00</Salary>   
              <Last_Modified>AAAAAAAAF40=</Last_Modified>   
            </NewTable>  
          </NewDataSet>  
        </diffgr:diffgram>  
      </DataSet>  
    </GET_LAST_EMP_DATAResult>  
    <ReturnValue>0</ReturnValue>   
  </GET_LAST_EMP_DATAResponse>  
  <DeleteResponse xmlns="http://schemas.microsoft.com/Sql/2008/05/TableOp/dbo/Employee">  
    <DeleteResult>1</DeleteResult>   
  </DeleteResponse>  
</RequestResponse>  
```  
  
 La réponse précédente contient plusieurs jeux de résultats correspondant différentes opérations effectuées dans le cadre de l’opération composite. Par exemple, le `InsertResult` élément contient 10080, qui est l’identificateur unique de l’enregistrement qui vient d’être ajouté.  
  
## <a name="best-practices"></a>Bonnes pratiques  
 Après avoir déployé et configuré le projet BizTalk, vous pouvez exporter les paramètres de configuration dans un fichier XML appelé le fichier de liaison. Une fois que vous générez un fichier de liaison, vous pouvez importer les paramètres de configuration à partir du fichier, afin que vous n’avez pas besoin de créer des éléments tels que les ports d’envoi et ports de réception d’une même orchestration. Pour plus d’informations sur les fichiers de liaison, consultez [réutiliser les liaisons de l’adaptateur](../../adapters-and-accelerators/adapter-sql/reuse-sql-adapter-bindings.md).
  
## <a name="see-also"></a>Voir aussi  
[Développer des applications BizTalk avec l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/develop-biztalk-applications-using-the-sql-adapter.md)