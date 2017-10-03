---
title: "Insérer, mettre à jour, supprimer ou sélectionner des opérations à l’aide de BizTalk Server avec l’adaptateur SQL | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1d411b1a-a36d-4e3e-a56a-91804a5d69b9
caps.latest.revision: "20"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f2216116e00e587d8da0d69cea8cd1c364e5786b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="insert-update-delete-or-select-operations-using-biztalk-server-with-the-sql-adapter"></a>Insérer, mettre à jour, supprimer ou sélectionner des opérations à l’aide de BizTalk Server avec l’adaptateur SQL
Le [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)] expose un ensemble d’opérations standards sur les tables de base de données SQL Server et des vues. Il s’agit des opérations data manipulation language (DML). À l’aide des opérations DML, vous pouvez effectuer de simples Insert, Update, Select et opérations Delete sur les tables et les vues. Pour plus d’informations sur la façon dont l’adaptateur prend en charge ces opérations, consultez [Insert, Update, Delete et sélectionnez les opérations sur les Tables et vues à l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/insert-update-delete-and-select-on-tables-and-views-with-the-sql-adapter.md). Pour plus d’informations sur la structure du message SOAP pour ces opérations, consultez [des schémas de Message pour Insert, Update, Delete et sélectionnez les opérations sur les Tables et vues](../../adapters-and-accelerators/adapter-sql/message-schemas-for-insert-update-delete-and-select-on-tables-and-views.md).  
  
> [!NOTE]
>  Si vous effectuez une opération sur les tables qui possèdent des colonnes de types définis par l’utilisateur, assurez-vous que vous faites référence à [opérations sur les Tables et les vues avec les Types définis par l’utilisateur à l’aide de l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/operations-on-tables-and-views-with-user-defined-types-using-the-sql-adapter.md) avant de commencer à développer votre application.  
  
## <a name="how-to-perform-basic-operations-on-a-sql-server-database"></a>Comment effectuer des opérations de base sur une base de données SQL Server  
 Une opération sur une base de données SQL Server à l’aide de [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] avec [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] implique les tâches de procédures décrites dans [blocs de construction pour développer des applications BizTalk à l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/building-blocks-to-develop-biztalk-applications-with-the-sql-adapter.md). Pour exécuter Insert, Update, Delete ou des opérations Select sur les tables et vues dans SQL Server, ces tâches sont :  
  
1.  Créez un projet BizTalk et générer le schéma pour l’opération que vous souhaitez appeler sur une table de base de données SQL Server ou une vue.  
  
2.  Créer des messages dans le projet BizTalk pour envoyer et recevoir des messages à partir de la base de données SQL Server.  
  
3.  Créez une orchestration pour appeler l’opération sur la table de base de données SQL Server ou la vue.  
  
4.  Générez et déployez le projet BizTalk.  
  
5.  Configurer l’application en créant physique d’envoi et ports de réception BizTalk.  
  
6.  Démarrez l’application BizTalk.  
  
 Cette rubrique fournit des instructions pour effectuer ces tâches.  
  
## <a name="sample-based-on-this-topic"></a>Exemple basé sur cette rubrique  
 Un exemple SelectTable, en fonction de cette rubrique est fourni avec le [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)]. Pour plus d’informations, consultez [exemples de l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/samples-for-the-sql-adapter.md).  
  
## <a name="generating-schema"></a>Génération du schéma  
 Cette rubrique montre comment effectuer des opérations DML base en sélectionnant des enregistrements à partir de la table EMPLOYEE dans la base de données SQL Server. Exécutez les scripts fournis avec les exemples pour créer la table EMPLOYEE. Pour plus d’informations sur les exemples, consultez [exemples de schéma](../../adapters-and-accelerators/accelerator-rosettanet/schema-samples.md).  
  
 Pour illustrer comment sélectionner des enregistrements, le schéma est généré pour l’opération de sélection pour la table EMPLOYEE. Vous devez créer un projet BizTalk et utiliser le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] pour générer le schéma. Consultez [récupérer des métadonnées pour les opérations de SQL Server dans Visual Studio à l’aide de l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/get-metadata-for-sql-server-operations-in-visual-studio-using-the-sql-adapter.md) pour plus d’informations sur la façon de générer des schémas.  
  
> [!IMPORTANT]
>  Si vous générez des métadonnées pour les opérations sur une table qui comporte des colonnes de types définis par l’utilisateur (UDT), assurez-vous que les assemblys respectifs de l’UDT sont disponibles au même emplacement que le [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] exécutable, devenv.exe. Le fichier exécutable est généralement disponible dans `<installation drive>:\Program Files\Microsoft Visual Studio <version>\Common7\IDE`. Dans cet exemple, la table EMPLOYEE possède une colonne UDT (Point). Veillez à copier l’assembly correspondant au même emplacement que le [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] exécutable.  
>   
>  Pour plus d’informations sur la création d’un UDT, consultez [créer un Type défini par l’utilisateur](https://msdn.microsoft.com/library/ms131106.aspx). Pour plus d’informations sur la façon d’inscrire un UDT dans SQL Server, consultez [Types Registering User-Defined dans SQL Server](https://msdn.microsoft.com/library/eybzcxe6(v=vs.85).aspx).  
  
## <a name="defining-messages-and-message-types"></a>Définition des Messages et les Types de messages  
 Le schéma que vous avez généré précédemment décrit les « types » requis pour les messages dans l’orchestration. Un message est généralement une variable, du type défini par le schéma correspondant. Vous devez maintenant créer des messages pour l’orchestration et les lier aux schémas que vous avez créé à l’étape précédente.  
  
1.  Ajouter une orchestration au projet BizTalk. À partir de l’Explorateur de solutions, cliquez sur le nom du projet BizTalk, pointez sur **ajouter**, puis cliquez sur **un nouvel élément**. Tapez un nom pour l’orchestration BizTalk, puis cliquez sur **ajouter**.  
  
2.  Ouvrez la fenêtre Vue Orchestration du projet BizTalk, s’il n’est pas déjà ouvert. Pour ce faire, cliquez sur **vue**, pointez sur **autres fenêtres**, puis cliquez sur **Vue Orchestration**.  
  
3.  Dans la vue Orchestration, cliquez sur **Messages**, puis cliquez sur **nouveau Message**.  
  
4.  Cliquez sur le message qui vient d’être créé, puis sélectionnez **fenêtre Propriétés**.  
  
5.  Dans le **propriétés** volet pour le **Message_1**, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |Identificateur|Type`Request`|  
    |Type de message|Dans la liste déroulante, développez **schémas**, puis sélectionnez *SelectTable.TableOperation_dbo_Employee.Select*, où SelectTable est le nom de votre projet BizTalk. TableOperation_dbo_Employee est le schéma généré pour l’opération Select sur la table EMPLOYEE.|  
  
6.  Répétez l’étape 2 pour créer un nouveau message. Dans le **propriétés** volet pour le nouveau message, procédez comme suit :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |Identificateur|Type`Response`|  
    |Type de message|Dans la liste déroulante, développez **schémas**, puis sélectionnez *SelectTable.TableOperation_dbo_Employee.SelectResponse*.|  
  
## <a name="setting-up-the-orchestration"></a>Configuration de l’Orchestration  
 Vous devez créer une orchestration BizTalk à utiliser [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] pour effectuer une opération sur SQL Server. Dans cette orchestration, vous déposez un message de demande à une emplacement de réception. Le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] consomme ce message et le transmet à SQL Server. La réponse à partir de SQL Server est enregistrée dans un autre emplacement. Vous devez inclure l’envoi et reçoivent des formes pour envoyer des messages à SQL Server et de recevoir des réponses, respectivement. Un exemple d’orchestration pour l’opération Select ressemble à ceci :  
  
 ![Orchestration permettant l’opération Select sur SQL Server](../../adapters-and-accelerators/adapter-sql/media/e74e342f-ba66-41fe-bd34-d45cd8767ef8.gif "e74e342f-ba66-41fe-bd34-d45cd8767ef8")  
  
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
|ReceiveMessage|-Définissez **Message** à *demande*<br />-Définissez **opération** à *MessageIn.Select.Request*|  
|SendMessage|-Définissez **Message** à *demande*<br />-Définissez **opération** à *LOBPort.Select.Request*|  
|Réception réponse|-Définissez **Message** à *réponse*<br />-Définissez **opération** à *LOBPort.Select.Response*|  
|SendResponse|-Définissez **Message** à *réponse*<br />-Définissez **opération** à *ResponseOut.Select.Request*|  
  
 Une fois que vous avez défini ces propriétés, les formes de message et les ports sont connectés, et l’orchestration est terminée.  
  
 Vous devez maintenant générer la solution BizTalk et déployez-le sur BizTalk Server. Pour plus d’informations, consultez [génération et exécution des Orchestrations](../../core/building-and-running-orchestrations.md).  
  
## <a name="configuring-the-biztalk-application"></a>Configuration de l’Application BizTalk  
 Après avoir déployé le projet BizTalk, l’orchestration que vous avez créé précédemment est répertoriée sous le volet Orchestrations dans la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration. Vous devez utiliser le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration pour configurer l’application. Pour une procédure pas à pas, consultez [procédure pas à pas : déploiement d’une Application BizTalk base](Walkthrough:%20Deploying%20a%20Basic%20BizTalk%20Application.md).
  
 Configuration d’une application implique :  
  
-   Sélection d’un hôte de l’application.  
  
-   Mappage de ports que vous avez créé dans l’orchestration aux ports physiques dans le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration. Pour cette orchestration, vous devez :  
  
    -   Définir un emplacement sur le disque dur et un port de fichier correspondant où vous allez déposer un message de demande. L’orchestration BizTalk consommer le message de demande et l’envoyer à la base de données SQL Server.  
  
    -   Définir un emplacement sur le disque dur et un port de fichier correspondant dans lequel l’orchestration BizTalk supprimera le message de réponse contenant la réponse à la base de données SQL Server.  
  
    -   Définir un port d’envoi WCF-Custom ou WCF-SQL physique pour envoyer des messages à la base de données SQL Server. Vous devez également spécifier l’action dans le port d’envoi. Pour plus d’informations sur la création de ports, consultez [configurer manuellement une liaison de port physique à l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/manually-configure-a-physical-port-binding-to-the-sql-adapter.md).
  
        > [!NOTE]
        >  Génération de schéma à l’aide du [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] crée également un fichier de liaison qui contient des informations sur les ports et les actions à définir pour ces ports. Vous pouvez importer ce fichier de liaison à partir de la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration pour créer des ports d’envoi (pour les appels sortants) ou de ports de réception (d’appels entrants). Pour plus d’informations, consultez [configurer une liaison de port physique à l’aide d’un fichier de liaison de port à utiliser l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/configure-a-physical-port-binding-using-a-port-binding-file-to-sql-adapter.md).
  
## <a name="starting-the-application"></a>Démarrage de l’Application  
 Vous devez démarrer l’application BizTalk pour sélectionner des enregistrements à partir d’une table de base de données SQL Server. Pour savoir comment démarrer une application BizTalk, consultez [comment démarrer une Orchestration](../../core/how-to-start-an-orchestration.md).
  
 À ce stade, vérifiez que :  
  
-   Le fichier de port de réception pour recevoir des messages de demande pour l’orchestration est en cours d’exécution.  
  
-   Le port d’envoi FILE pour recevoir les messages de réponse à partir de l’orchestration est en cours d’exécution.  
  
-   Le port d’envoi WCF-Custom ou WCF-SQL pour envoyer des messages à la base de données SQL Server est en cours d’exécution.  
  
-   L’orchestration BizTalk pour l’opération est en cours d’exécution.  
  
> [!IMPORTANT]
>  Si vous effectuez des opérations sur une table qui comporte des colonnes de types définis par l’utilisateur (UDT), assurez-vous que les assemblys respectifs de l’UDT sont disponibles au même emplacement que le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] exécutable, btsntsvc.exe. Le fichier exécutable est généralement disponible dans `<installation drive>:\Program Files\Microsoft BizTalk Server <version>`. Dans cet exemple, la table EMPLOYEE possède une colonne UDT (Point). Veillez à copier l’assembly correspondant au même emplacement que le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] exécutable.  
>   
>  Pour plus d’informations sur la création d’un UDT, consultez [créer un Type défini par l’utilisateur](https://msdn.microsoft.com/library/ms131106.aspx). Pour plus d’informations sur la façon d’inscrire un UDT dans SQL Server, consultez [Types Register User-Defined dans SQL Server](https://msdn.microsoft.com/library/ms131079.aspx).  
  
## <a name="executing-the-operation"></a>L’exécution de l’opération  
 Après avoir exécuté l’application, vous devez supprimer un message de demande pour le fichier de l’emplacement de réception. Le schéma du message de demande doit être conforme au schéma pour l’opération de sélection que vous avez créé précédemment. Par exemple, le message de demande pour sélectionner tous les enregistrements de la table EMPLOYEE est la suivante :  
  
```  
<Select xmlns="http://schemas.microsoft.com/Sql/2008/05/TableOp/dbo/Employee">  
  <Columns>*</Columns>  
  <Query>where Employee_ID=10001</Query>  
</Select>  
```  
  
 Ce message de demande pour récupérer les enregistrements de la table Employee qui satisfont la condition spécifiée dans le `<Query>` élément. Si vous souhaitez extraire des colonnes spécifiques de la table, vous devez les spécifier dans le < colonnes\> élément, séparé par des virgules, dans l’ordre où ils apparaissent dans la définition de table. Si vous ne souhaitez pas spécifier une condition pour récupérer des données, laissez le `<Query>` élément vide. Consultez [des schémas de Message pour Insert, Update, Delete et sélectionnez les opérations sur les Tables et vues](../../adapters-and-accelerators/adapter-sql/message-schemas-for-insert-update-delete-and-select-on-tables-and-views.md) pour plus d’informations sur le schéma de message de demande pour effectuer des opérations DML base sur SQL Server, base de données des tables et vues à l’aide de la [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].  
  
 L’orchestration consomme le message et l’envoie à la base de données SQL Server. La réponse à partir de la base de données SQL Server est enregistrée dans l’autre emplacement de fichier définie dans le cadre de l’orchestration. Par exemple, la réponse à partir de la base de données SQL Server pour le précédent message de demande est la suivante :  
  
```  
\<?xml version="1.0" encoding="utf-8" ?>   
<SelectResponse xmlns="mssql://Microsoft.LobServices.Sql/2008/01/TVOp/dbo/Employee">  
  <SelectResult>  
    <Employee xmlns="mssql://Microsoft.LobServices.Sql/2008/01/Types/Tables/dbo">  
      <Employee_ID>10001</Employee_ID>  
      <Name>John</Name>  
      <DOJ>1983-12-31T00:00:00Z</DOJ>  
      <Designation>Manager</Designation>  
      <Job_Description>Management</Job_Description>  
      <Photo>EjRVYzRFVQ==</Photo>  
      <Rating>1,2</Rating>  
      <Salary>100000.00</Salary>  
      <Last_Modified>AAAAAAAAD6I=</Last_Modified>  
    </Employee>  
  </SelectResult>  
</SelectResponse>  
```  
  
## <a name="best-practices"></a>Bonnes pratiques  
  
-   Après avoir déployé et configuré le projet BizTalk, vous pouvez exporter les paramètres de configuration dans un fichier XML appelé le fichier de liaison. Une fois que vous générez un fichier de liaison, vous pouvez importer les paramètres de configuration à partir du fichier, afin que vous n’avez pas besoin de créer des éléments tels que les ports d’envoi et ports de réception d’une même orchestration. Pour plus d’informations sur les fichiers de liaison, consultez [liaisons de l’adaptateur SQL de réutiliser](../../adapters-and-accelerators/adapter-sql/reuse-sql-adapter-bindings.md).
  
-   Si vous insérez, mettez à jour, ou suppression de grands volumes de données que vous définissez les valeurs de délai d’attente de droite pour l’adaptateur WCF et pour la transaction MS DTC. Pour plus d’informations, consultez le problème de « l’adaptateur ne peut pas insérer, mettre à jour ou supprimer des volumes importants de données en une seule opération à l’aide de BizTalk Server » dans [dépanner les problèmes opérationnels avec l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/troubleshoot-operational-issues-with-the-sql-adapter.md).  
  
## <a name="see-also"></a>Voir aussi  
[Développer des applications BizTalk à l’aide de l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/develop-biztalk-applications-using-the-sql-adapter.md)