---
title: "Comment déplacer la Database1 d’importation principale BAM | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- migrating, Primary Import database [BAM]
- Primary Import database [BAM], migrating
ms.assetid: fab13fea-5c35-4a9f-977d-cc45545c54b2
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6eca9ed37cf116d57888bae1343e383cc2d2a666
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-move-the-bam-primary-import-database"></a><span data-ttu-id="a6d36-102">Déplacement de la base de données d'importation principale BAM</span><span class="sxs-lookup"><span data-stu-id="a6d36-102">How to Move the BAM Primary Import Database</span></span>
<span data-ttu-id="a6d36-103">Cette procédure vous permet de déplacer la base de données d'importation principale BAM vers un autre serveur.</span><span class="sxs-lookup"><span data-stu-id="a6d36-103">You can use this procedure to move the BAM Primary Import database to another server.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="a6d36-104">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="a6d36-104">Prerequisites</span></span>  
 <span data-ttu-id="a6d36-105">Pour exécuter cette procédure, vous devez être connecté avec un compte membre du rôle de serveur fixe sysadmin SQL Server.</span><span class="sxs-lookup"><span data-stu-id="a6d36-105">You must be logged on with an account that is a member of the SQL Server sysadmin fixed server role to perform this procedure.</span></span>  
  
### <a name="to-move-the-bam-primary-import-database"></a><span data-ttu-id="a6d36-106">Pour déplacer la base de données d'importation principale BAM</span><span class="sxs-lookup"><span data-stu-id="a6d36-106">To move the BAM Primary Import database</span></span>  
  
1.  <span data-ttu-id="a6d36-107">Arrêtez tous les services BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="a6d36-107">Stop all BizTalk Server services.</span></span> <span data-ttu-id="a6d36-108">Pour plus d’informations, consultez [comment démarrer, arrêter, suspendre, reprendre ou redémarrer les Services BizTalk Server](../core/how-to-start-stop-pause-resume-or-restart-biztalk-server-services.md).</span><span class="sxs-lookup"><span data-stu-id="a6d36-108">For more information, see [How to Start, Stop, Pause, Resume, or Restart BizTalk Server Services](../core/how-to-start-stop-pause-resume-or-restart-biztalk-server-services.md).</span></span>  
  
2.  <span data-ttu-id="a6d36-109">Arrêtez le service IIS.</span><span class="sxs-lookup"><span data-stu-id="a6d36-109">Stop the IIS service.</span></span>  
  
3.  <span data-ttu-id="a6d36-110">Arrêtez le service de notification des alertes BAM :</span><span class="sxs-lookup"><span data-stu-id="a6d36-110">Stop the BAM Alerts Notification Service:</span></span>  
  
    1.  <span data-ttu-id="a6d36-111">Cliquez sur **Démarrer**, puis sur **Exécuter**, tapez **cmd**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="a6d36-111">Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
    2.  <span data-ttu-id="a6d36-112">À l'invite de commandes, tapez :</span><span class="sxs-lookup"><span data-stu-id="a6d36-112">At the command prompt, type:</span></span>  
  
        ```  
        Net stop NS$BamAlerts  
        ```  
  
4.  <span data-ttu-id="a6d36-113">Suivez les instructions de la documentation en ligne de SQL Server pour sauvegarder la base de données d'importation principale BAM sur l'ancien serveur.</span><span class="sxs-lookup"><span data-stu-id="a6d36-113">Follow the instructions in SQL Server Books Online to back up the BAM Primary Import database on the old server.</span></span>  
  
5.  <span data-ttu-id="a6d36-114">Copiez la base de données d'importation principale BAM sur le nouveau serveur SQL Server.</span><span class="sxs-lookup"><span data-stu-id="a6d36-114">Copy the BAM Primary Import database to the new SQL Server.</span></span>  
  
6.  <span data-ttu-id="a6d36-115">Suivez les instructions de la documentation en ligne de SQL Server pour restaurer la base de données d'importation principale BAM sur le nouveau serveur.</span><span class="sxs-lookup"><span data-stu-id="a6d36-115">Follow the instructions in SQL Server Books Online to restore the BAM Primary Import database on the new server.</span></span>  
  
7.  <span data-ttu-id="a6d36-116">Sur un ordinateur exécutant [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], accédez au dossier suivant :</span><span class="sxs-lookup"><span data-stu-id="a6d36-116">On a computer running [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], browse to the following folder:</span></span>  
  
     [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]<span data-ttu-id="a6d36-117">Schema\Restore.</span><span class="sxs-lookup"><span data-stu-id="a6d36-117">Schema\Restore</span></span>  
  
8.  <span data-ttu-id="a6d36-118">Avec le bouton droit **SampleUpdateInfo.xml**, puis cliquez sur **modifier**.</span><span class="sxs-lookup"><span data-stu-id="a6d36-118">Right-click **SampleUpdateInfo.xml**, and then click **Edit**.</span></span>  
  
9. <span data-ttu-id="a6d36-119">Dans la section base de données primaire importation du fichier, remplacez **« SourceServer »** avec le nom du système source et puis remplacez **« DestinationServer »** avec le nom du système de destination.</span><span class="sxs-lookup"><span data-stu-id="a6d36-119">In the Primary Import Database section of the file, replace **"SourceServer"** with the name of the source system, and then replace **"DestinationServer"** with the name of the destination system.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="a6d36-120">Utilisez des guillemets doubles pour encadrer le nom du système source et du système de destination.</span><span class="sxs-lookup"><span data-stu-id="a6d36-120">Include the quotation marks around the name of the source and destination systems.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a6d36-121">Si vous avez renommé les bases de données BizTalk Server, vous devez également mettre à jour comme il se doit les noms des bases de données.</span><span class="sxs-lookup"><span data-stu-id="a6d36-121">If you renamed any of the BizTalk Server databases, you must also update the database names as appropriate.</span></span>  
  
10. <span data-ttu-id="a6d36-122">Supprimez les marques de commentaire dans les lignes suivantes du fichier XML :</span><span class="sxs-lookup"><span data-stu-id="a6d36-122">Uncomment the following lines in the xml file:</span></span>  
  
    ```  
    - <UpdateConfiguration>  
      <MessageBoxDB oldDBName="BizTalkMsgboxDb" oldDBServer="Server01" newDBName="BizTalkMsgboxDb" newDBServer="Server01" IsMaster="1" />   
      <TrackingDB oldDBName="BizTalkDTADb" oldDBServer="Server01" newDBName="BizTalkDTADb" newDBServer="Server01" />   
      <ManagementDB oldDBName="BizTalkMgmtDb" oldDBServer="Server01" newDBName="BizTalkMgmtDb" newDBServer="Server01" />   
    - <BAM>  
    - <DeploymentUnit Name="OldPrimaryImportDatabase">  
      <Property Name="ServerName">Server01</Property>   
      <Property Name="DatabaseName">BAMPrimaryImport</Property>   
      </DeploymentUnit>  
    - <DeploymentUnit Name="PrimaryImportDatabase">  
      <Property Name="ServerName">Server02</Property>   
      <Property Name="DatabaseName">BAMPrimaryImport</Property>   
      </DeploymentUnit>  
    - <DeploymentUnit Name="ArchivingDatabase">  
      <Property Name="ServerName">Server01</Property>   
      <Property Name="DatabaseName">BAMArchive</Property>   
      </DeploymentUnit>  
    - <DeploymentUnit Name="AnalysisDatabase">  
      <Property Name="ServerName">Server01</Property>   
      <Property Name="DatabaseName">BAMAnalysis</Property>   
      </DeploymentUnit>  
    - <DeploymentUnit Name="StarSchemaDatabase">  
      <Property Name="ServerName">Server01</Property>   
      <Property Name="DatabaseName">BAMStarSchema</Property>   
      </DeploymentUnit>  
    - <DeploymentUnit Name="Alert">  
      <Property Name="DBServer">Server01</Property>   
      <Property Name="InstanceDatabaseName">BAMAlerts</Property>   
      </DeploymentUnit>  
      </BAM>  
    - <OtherDatabases>  
      <Database Name="SSO" oldDBName="SSODB" oldDBServer="Server01" newDBName="SSODB" newDBServer="Server01" />   
      </OtherDatabases>  
      </UpdateConfiguration>  
    ```  
  
11. <span data-ttu-id="a6d36-123">Lorsque vous avez terminé la modification du fichier, enregistrez-le et fermez-le.</span><span class="sxs-lookup"><span data-stu-id="a6d36-123">When you are finished editing the file, save it and exit.</span></span>  
  
12. <span data-ttu-id="a6d36-124">Cliquez sur **Démarrer**, puis sur **Exécuter**, tapez **cmd**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="a6d36-124">Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
13. <span data-ttu-id="a6d36-125">À l'invite de commandes, accédez au répertoire suivant :</span><span class="sxs-lookup"><span data-stu-id="a6d36-125">At the command prompt, navigate to the following directory:</span></span>  
  
     [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]<span data-ttu-id="a6d36-126">Schema\Restore.</span><span class="sxs-lookup"><span data-stu-id="a6d36-126">Schema\Restore</span></span>  
  
14. <span data-ttu-id="a6d36-127">À l'invite de commandes, tapez :</span><span class="sxs-lookup"><span data-stu-id="a6d36-127">At the command prompt, type:</span></span>  
  
     <span data-ttu-id="a6d36-128">**cscript UpdateDatabase.vbs SampleUpdateInfo.xml**</span><span class="sxs-lookup"><span data-stu-id="a6d36-128">**cscript UpdateDatabase.vbs SampleUpdateInfo.xml**</span></span>  
  
15. <span data-ttu-id="a6d36-129">Mettez à jour la référence à la base de données d'importation principale BAM dans tous les fichiers Microsoft Excel de données actives BAM.</span><span class="sxs-lookup"><span data-stu-id="a6d36-129">Update the reference to BAM Primary Import Database in all BAM Livedata Microsoft Excel files.</span></span> <span data-ttu-id="a6d36-130">Pour chaque fichier :</span><span class="sxs-lookup"><span data-stu-id="a6d36-130">For each file:</span></span>  
  
    1.  <span data-ttu-id="a6d36-131">Ouvrez le fichier Excel de données actives.</span><span class="sxs-lookup"><span data-stu-id="a6d36-131">Open the Excel live data file.</span></span> <span data-ttu-id="a6d36-132">Le nom de fichier se termine par _LiveData.xls.</span><span class="sxs-lookup"><span data-stu-id="a6d36-132">The file name ends with _LiveData.xls.</span></span>  
  
    2.  <span data-ttu-id="a6d36-133">Sur le **BAM** menu, cliquez sur **connexion DB BAM**.</span><span class="sxs-lookup"><span data-stu-id="a6d36-133">On the **BAM** menu, click **BAM DB Connection**.</span></span>  
  
    3.  <span data-ttu-id="a6d36-134">Dans le **sélectionner la base de données BAM** boîte de dialogue, entrez la base de données SQL Server et BAMPrimaryImport, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="a6d36-134">In the **Select BAM Database** dialog box, enter the SQL Server and BAMPrimaryImport database, and then click **OK**.</span></span>  
  
    4.  <span data-ttu-id="a6d36-135">Sur le **fichier** menu, cliquez sur **fermer et retourner à Microsoft Excel**.</span><span class="sxs-lookup"><span data-stu-id="a6d36-135">On the **File** menu, click **Close and Return to Microsoft Excel**.</span></span>  
  
    5.  <span data-ttu-id="a6d36-136">Dans le menu **Fichier** , cliquez sur **Enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="a6d36-136">On the **File** menu, click **Save**.</span></span>  
  
16. <span data-ttu-id="a6d36-137">Mettez à jour le nom du serveur et celui de la base de données dans tous les lots DTS de l'analyse BAM dotés du préfixe « BAM_AN_ » ou « BAM_DM_ » en suivant la procédure ci-dessous :</span><span class="sxs-lookup"><span data-stu-id="a6d36-137">Update the server and database names in all BAM analysis DTS packages, which are prefixed with "BAM_AN_" or "BAM_DM_" by following these steps:</span></span>  
  
    1.  <span data-ttu-id="a6d36-138">Sur le serveur hébergeant l'analyse BAM, ouvrez SQL Server Enterprise Manager.</span><span class="sxs-lookup"><span data-stu-id="a6d36-138">On the server hosting BAM, open SQL Server Enterprise Manager.</span></span>  
  
    2.  <span data-ttu-id="a6d36-139">Ouvrez le **Data Transformation Services** dossier.</span><span class="sxs-lookup"><span data-stu-id="a6d36-139">Open the **Data Transformation Services** folder.</span></span>  
  
    3.  <span data-ttu-id="a6d36-140">Ouvrez le **lots locaux** dossier, puis ouvrez les packages DTS.</span><span class="sxs-lookup"><span data-stu-id="a6d36-140">Open the **Local Packages** folder, and then open the DTS packages.</span></span>  
  
    4.  <span data-ttu-id="a6d36-141">Sur le **Package** menu, cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="a6d36-141">On the **Package** menu, click **Properties**.</span></span>  
  
    5.  <span data-ttu-id="a6d36-142">Sur le **les Variables globales** , onglet de la mettre à jour les valeurs pour le serveur d’importation principale et la base de données.</span><span class="sxs-lookup"><span data-stu-id="a6d36-142">On the **Global Variables** tab, update the values for the primary import server and database.</span></span>  
  
    6.  <span data-ttu-id="a6d36-143">Modifiez les lignes suivantes de sorte qu'elles correspondent au nouveau serveur et à la nouvelle base de données :</span><span class="sxs-lookup"><span data-stu-id="a6d36-143">Change the following lines to match your new server and database:</span></span>  
  
         <span data-ttu-id="a6d36-144">PrimaryImportServer = «*\<nom_serveur >*»</span><span class="sxs-lookup"><span data-stu-id="a6d36-144">PrimaryImportServer= "*\<ServerName>*"</span></span>  
  
         <span data-ttu-id="a6d36-145">PrimaryImportDatabase = «*\<DatabaseName >*»</span><span class="sxs-lookup"><span data-stu-id="a6d36-145">PrimaryImportDatabase = "*\<DatabaseName>*"</span></span>  
  
17. <span data-ttu-id="a6d36-146">Démarrez tous les services BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="a6d36-146">Start all BizTalk Server services.</span></span> <span data-ttu-id="a6d36-147">Pour plus d’informations, consultez [comment démarrer, arrêter, suspendre, reprendre ou redémarrer les Services BizTalk Server](../core/how-to-start-stop-pause-resume-or-restart-biztalk-server-services.md).</span><span class="sxs-lookup"><span data-stu-id="a6d36-147">For more information, see [How to Start, Stop, Pause, Resume, or Restart BizTalk Server Services](../core/how-to-start-stop-pause-resume-or-restart-biztalk-server-services.md).</span></span>  
  
18. <span data-ttu-id="a6d36-148">Démarrez le service IIS.</span><span class="sxs-lookup"><span data-stu-id="a6d36-148">Start the IIS service.</span></span>  
  
19. <span data-ttu-id="a6d36-149">Démarrez le service de notification des alertes BAM :</span><span class="sxs-lookup"><span data-stu-id="a6d36-149">Start the BAM Alerts Notification Service:</span></span>  
  
    1.  <span data-ttu-id="a6d36-150">Cliquez sur **Démarrer**, puis sur **Exécuter**, tapez **cmd**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="a6d36-150">Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
    2.  <span data-ttu-id="a6d36-151">À l'invite de commandes, tapez :</span><span class="sxs-lookup"><span data-stu-id="a6d36-151">At the command prompt, type:</span></span>  
  
        ```  
        Net start NS$BamAlerts  
        ```  
  
## <a name="see-also"></a><span data-ttu-id="a6d36-152">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a6d36-152">See Also</span></span>  
 [<span data-ttu-id="a6d36-153">Déplacement de bases de données BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="a6d36-153">Moving BizTalk Server Databases</span></span>](../core/moving-biztalk-server-databases.md)