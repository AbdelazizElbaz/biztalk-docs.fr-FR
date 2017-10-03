---
title: "Comment configurer le système de Destination pour l’envoi de journaux | Documents Microsoft"
ms.custom: 
ms.date: 2015-12-03
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- backing up, log shipping
- system failures, preventing
- log shipping
- databases, backing up
- backing up, databases
- system failures, backing up
- backing up, system failures
ms.assetid: 7b4425f5-b105-4fb2-a503-94ca1e75ad55
caps.latest.revision: "54"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ea377f83f6e9c104d1bbd0b2e59923fb11f8fe65
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-the-destination-system-for-log-shipping"></a><span data-ttu-id="179f1-102">Comment configurer le système de Destination pour l’envoi de journaux</span><span class="sxs-lookup"><span data-stu-id="179f1-102">How to Configure the Destination System for Log Shipping</span></span>
<span data-ttu-id="179f1-103">La copie des journaux de transaction offre des fonctionnalités de serveur de secours, ce qui réduit le temps mort en cas de défaillance du système.</span><span class="sxs-lookup"><span data-stu-id="179f1-103">Log shipping provides standby server capabilities to reduce downtime in the event of a system failure.</span></span> <span data-ttu-id="179f1-104">L'envoi de journaux vous permet d'envoyer automatiquement des journaux des transactions à partir du système source vers le système de destination.</span><span class="sxs-lookup"><span data-stu-id="179f1-104">Log shipping allows you to automatically send transaction logs from the source system to the destination system.</span></span> <span data-ttu-id="179f1-105">Au niveau du système de destination, les journaux des transactions sont restaurés dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] des bases de données ; les maintenant étroitement synchronisées avec les bases de données source.</span><span class="sxs-lookup"><span data-stu-id="179f1-105">At the destination system, the transaction logs are restored to the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases; keeping them closely synchronized with the source databases.</span></span>  
  
 <span data-ttu-id="179f1-106">L'envoi de journaux fonctionne dans les environnements monoserveur et de serveur distribué.</span><span class="sxs-lookup"><span data-stu-id="179f1-106">Log shipping works in both single server and distributed server environments.</span></span> <span data-ttu-id="179f1-107">Le serveur ou groupe de serveurs contenant des données actives est appelé « système source (ou principal) ».</span><span class="sxs-lookup"><span data-stu-id="179f1-107">The server or group of servers that contain live data is known as the source (or primary) system.</span></span> <span data-ttu-id="179f1-108">Le serveur ou groupe de serveurs utilisés pour restaurer les sauvegardes de base de données produites par le système source (ou principal) est appelé « système de destination (ou secondaire) ».</span><span class="sxs-lookup"><span data-stu-id="179f1-108">The server or group of servers that are used to restore the database backups produced by the source (or primary) system is known as the destination (or secondary) system.</span></span>  
  
 <span data-ttu-id="179f1-109">[À propos de l’envoi de journaux](https://docs.microsoft.com/sql/database-engine/log-shipping/about-log-shipping-sql-server) dans l’instruction SQL, documentation fournit des détails spécifiques.</span><span class="sxs-lookup"><span data-stu-id="179f1-109">[About Log Shipping](https://docs.microsoft.com/sql/database-engine/log-shipping/about-log-shipping-sql-server) in the SQL documentation provides specific details.</span></span>  
  
 <span data-ttu-id="179f1-110">Vous pouvez utiliser les étapes suivantes pour créer un système de destination constitué d'un seul serveur pour un système source unique.</span><span class="sxs-lookup"><span data-stu-id="179f1-110">You can use the following steps to create a destination system that consists of one server for a single source system.</span></span> <span data-ttu-id="179f1-111">Si le système de destination compte plusieurs serveurs, répétez les étapes sur chaque serveur de destination.</span><span class="sxs-lookup"><span data-stu-id="179f1-111">If the destination system contains multiple servers, repeat the steps on each destination server.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="179f1-112">Conservez toujours une copie de vos fichiers de sauvegarde dans un emplacement sécurisé :</span><span class="sxs-lookup"><span data-stu-id="179f1-112">Always keep a copy of your backup files in a secure location.</span></span> <span data-ttu-id="179f1-113">même si vous disposez de sauvegardes de journal, vous ne pouvez pas restaurer vos bases de données sans les fichiers de sauvegarde.</span><span class="sxs-lookup"><span data-stu-id="179f1-113">Even if you have log backups, you cannot restore your databases without the backup files.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="179f1-114">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="179f1-114">Prerequisites</span></span>  
* <span data-ttu-id="179f1-115">Connectez-vous en tant que membre de le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] groupe Administrateurs.</span><span class="sxs-lookup"><span data-stu-id="179f1-115">Sign in as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group.</span></span>  
  
* <span data-ttu-id="179f1-116">Utilisez la même version de SQL Server sur les systèmes source et de destination.</span><span class="sxs-lookup"><span data-stu-id="179f1-116">Use the same version of SQL Server on the source and destination systems.</span></span> <span data-ttu-id="179f1-117">SQL Server doit être installé dans le même emplacement relatif sur les systèmes source et de destination.</span><span class="sxs-lookup"><span data-stu-id="179f1-117">SQL Server must be installed in the same relative location on the source and destination systems.</span></span>  
  
* <span data-ttu-id="179f1-118">Le répertoire du journal des transactions SQL (fichiers .LDF) présent sur le système source doit également exister sur le système de destination.</span><span class="sxs-lookup"><span data-stu-id="179f1-118">The directory for SQL transaction log (.LDF files) on the source system must also exist on the destination system.</span></span> <span data-ttu-id="179f1-119">Si tel n'est pas le cas, créez le répertoire en lui donnant les mêmes nom et autorisations que sur le système source.</span><span class="sxs-lookup"><span data-stu-id="179f1-119">If this directory is not on the destination system, create the directory with the same name and permissions as on the source system.</span></span>  
  
### <a name="configure-the-destination-system-for-log-shipping"></a><span data-ttu-id="179f1-120">Configurer le système de destination pour l’envoi de journaux</span><span class="sxs-lookup"><span data-stu-id="179f1-120">Configure the destination system for log shipping</span></span>  
  
1.  <span data-ttu-id="179f1-121">Sur le système de destination, ouvrez **SQL Server Management Studio**et vous connecter à votre serveur SQL Server.</span><span class="sxs-lookup"><span data-stu-id="179f1-121">On the destination system, open **SQL Server Management Studio**, and connect to your SQL Server.</span></span> <span data-ttu-id="179f1-122">Sélectionnez **master** à partir de bases de données disponibles.</span><span class="sxs-lookup"><span data-stu-id="179f1-122">Select **master** from Available Databases.</span></span>  
  
2.  <span data-ttu-id="179f1-123">Sur le **fichier** menu, **ouvrir** le script SQL suivant :</span><span class="sxs-lookup"><span data-stu-id="179f1-123">On the **File** menu, **Open** the following SQL script:</span></span>  
  
    ```    
    %SystemDrive%\Program Files\Microsoft BizTalk Server <version>\Schema\LogShipping_Destination_Schema.sql  
    ```  
  
3.  <span data-ttu-id="179f1-124">Sur le **requête** menu, sélectionnez **Execute**.</span><span class="sxs-lookup"><span data-stu-id="179f1-124">On the **Query** menu, select **Execute**.</span></span>  
  
     <span data-ttu-id="179f1-125">Le *LogShipping_Destination_Schema* supprime et recrée les tables utilisées pour la restauration des bases de données source sur le système de destination.</span><span class="sxs-lookup"><span data-stu-id="179f1-125">The *LogShipping_Destination_Schema* drops and recreates the tables used for restoring the source databases on the destination system.</span></span> <span data-ttu-id="179f1-126">Cela inclut les tables permettant de stocker la liste des bases de données en cours de récupération, les copies de l'historique des sauvegardes importées à partir de la base de données BizTalkMgmtDb du système source, ainsi que les informations sur les travaux de l'Agent SQL Server configurés pour être exécutés sur les bases de données sources.</span><span class="sxs-lookup"><span data-stu-id="179f1-126">This includes tables to store the list of databases being recovered, copies of the backup history imported from the source system's BizTalkMgmtDb database, and information about SQL Server Agent jobs configured to run against the source databases.</span></span>  
  
4.  <span data-ttu-id="179f1-127">Sur le **fichier** menu, **ouvrir** le script SQL suivant :</span><span class="sxs-lookup"><span data-stu-id="179f1-127">On the **File** menu, **Open** the following SQL script:</span></span>  
  
    ```    
    %SystemDrive%\Program Files\Microsoft BizTalk Server <version>\Schema\LogShipping_Destination_Logic.sql  
    ```  
  
5.  <span data-ttu-id="179f1-128">Sur le **requête** menu, sélectionnez **Execute**.</span><span class="sxs-lookup"><span data-stu-id="179f1-128">On the **Query** menu, select **Execute**.</span></span>  
  
6.  <span data-ttu-id="179f1-129">Sur l’ou les ordinateurs que vous avez identifié en tant que le système de destination, ouvrez **SQL Server Management Studio** et se connecter à SQL Server.</span><span class="sxs-lookup"><span data-stu-id="179f1-129">On the computer or computers you have identified as the destination system, open **SQL Server Management Studio** and connect to the SQL Server.</span></span>  
  
7.  <span data-ttu-id="179f1-130">Sélectionnez **nouvelle requête**.</span><span class="sxs-lookup"><span data-stu-id="179f1-130">Select **New Query**.</span></span> <span data-ttu-id="179f1-131">Dans la fenêtre de requête, collez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="179f1-131">In the query window, paste the following command:</span></span>  
  
    ```  
    exec bts_ConfigureBizTalkLogShipping @nvcDescription = '<MyLogShippingSolution>',  
    @nvcMgmtDatabaseName = '<BizTalkServerManagementDatabaseName>',  
    @nvcMgmtServerName = '<BizTalkServerManagementDatabaseServer>',  
    @SourceServerName = null, -- null indicates that this destination server restores all databases  
    @fLinkServers = 1 -- 1 automatically links the server to the management database  
    ```  
  
     <span data-ttu-id="179f1-132">Puis :</span><span class="sxs-lookup"><span data-stu-id="179f1-132">Then:</span></span>  
  
    1.  <span data-ttu-id="179f1-133">Sur le système de destination, activez  **[Ad Hoc Distributed Queries](https://docs.microsoft.com/sql/database-engine/configure-windows/server-configuration-options-sql-server)**.</span><span class="sxs-lookup"><span data-stu-id="179f1-133">On the destination system, enable **[Ad Hoc Distributed Queries](https://docs.microsoft.com/sql/database-engine/configure-windows/server-configuration-options-sql-server)**.</span></span>  
  
    2.  <span data-ttu-id="179f1-134">Dans la fenêtre de requête, remplacez  *\<MyLogShippingSolution >* avec une description significative, entourée par des guillemets simples.</span><span class="sxs-lookup"><span data-stu-id="179f1-134">In the query window, replace *\<MyLogShippingSolution>* with a meaningful description, surrounded by single quotes.</span></span>  
  
    3.  <span data-ttu-id="179f1-135">Dans la fenêtre de requête, remplacez  *\<BizTalkServerManagementDatabaseName >* et  *\<BizTalkServerManagementDatabaseServer >* avec le nom et l’emplacement de votre données de gestion BizTalk source, entourée de guillemets simples.</span><span class="sxs-lookup"><span data-stu-id="179f1-135">In the query window, replace *\<BizTalkServerManagementDatabaseName>* and *\<BizTalkServerManagementDatabaseServer>* with the name and location of your source BizTalk Management database, surrounded by single quotes.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="179f1-136">Si vous disposez de plusieurs serveurs sources, vous pouvez restaurer chaque serveur source sur son propre serveur de destination.</span><span class="sxs-lookup"><span data-stu-id="179f1-136">If you have more than one source server, you can restore each source server to its own destination server.</span></span> <span data-ttu-id="179f1-137">Sur chaque serveur de destination, dans le  **@SourceServerName = null** paramètre, remplacez *null* par le nom du serveur source approprié, entouré de guillemets simples (par exemple,  **@SourceServerName = 'MySourceServer'**).</span><span class="sxs-lookup"><span data-stu-id="179f1-137">On each destination server, in the **@SourceServerName = null** parameter, replace *null* with the name of the appropriate source server, surrounded by single quotes (for example, **@SourceServerName = 'MySourceServer',**).</span></span>  
  
8.  <span data-ttu-id="179f1-138">Sur le **requête** menu, sélectionnez **Execute**.</span><span class="sxs-lookup"><span data-stu-id="179f1-138">On the **Query** menu, select **Execute**.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="179f1-139">En cas d'échec de la requête, vous devez résoudre le problème lié à la requête, puis recommencer cette procédure, à partir de l'étape 1, pour reconfigurer le système de destination.</span><span class="sxs-lookup"><span data-stu-id="179f1-139">If the query fails, after you fix the problem with the query, you must start over from step 1 of this procedure to reconfigure the destination system.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="179f1-140">Les travaux de restauration sur le système de destination tentent de recréer les journaux et les fichiers de données pour chaque base de données restaurée dans le même emplacement où ils se trouvaient sur le serveur de bases de données source.</span><span class="sxs-lookup"><span data-stu-id="179f1-140">The restore jobs on the destination system attempt to recreate the log and data files for each restored database in the same location as they existed on the source database server.</span></span>  
  
9. <span data-ttu-id="179f1-141">Sur le système de destination dans **SQL Server Management Studio**, développez **l’Agent SQL Server**, développez **travaux**.</span><span class="sxs-lookup"><span data-stu-id="179f1-141">On the destination system in **SQL Server Management Studio**, expand **SQL Server Agent**, and expand **Jobs**.</span></span>  
  
     <span data-ttu-id="179f1-142">Dans le volet de détails, il existe trois nouveaux travaux :</span><span class="sxs-lookup"><span data-stu-id="179f1-142">In the details pane, there are three new jobs:</span></span>  
  
    -   <span data-ttu-id="179f1-143">**Obtenir l’historique de sauvegarde des journaux de BizTalk Server**</span><span class="sxs-lookup"><span data-stu-id="179f1-143">**BTS Log Shipping Get Backup History**</span></span>  
  
         <span data-ttu-id="179f1-144">Ce travail BizTalk déplace des enregistrements d'historique de sauvegarde de la source vers la destination.</span><span class="sxs-lookup"><span data-stu-id="179f1-144">This BizTalk job moves backup history records from the source to the destination.</span></span> <span data-ttu-id="179f1-145">Par défaut, ce travail est planifié pour être exécuté toutes les minutes.</span><span class="sxs-lookup"><span data-stu-id="179f1-145">It is scheduled by default to run every minute.</span></span> <span data-ttu-id="179f1-146">Il est exécuté aussi souvent que possible afin de déplacer des enregistrements de l'historique depuis la source vers la destination</span><span class="sxs-lookup"><span data-stu-id="179f1-146">This job runs as frequently as possible in order to move history records from the source to the destination.</span></span> <span data-ttu-id="179f1-147">En cas de défaillance du système source, le serveur identifié comme système de destination continue de traiter les enregistrements de l'historique déjà importés.</span><span class="sxs-lookup"><span data-stu-id="179f1-147">In the event of a system failure to the source system, the server that you identified as the destination system continues to process the history records that have already been imported.</span></span>  
  
    -   <span data-ttu-id="179f1-148">**Restauration de bases de données de copie des journaux de serveur BizTalk Server**</span><span class="sxs-lookup"><span data-stu-id="179f1-148">**BTS Server Log Shipping Restore Databases**</span></span>  
  
         <span data-ttu-id="179f1-149">Ce travail BizTalk restaure les fichiers de sauvegarde des bases de données indiquées pour la source vers le serveur de destination.</span><span class="sxs-lookup"><span data-stu-id="179f1-149">This BizTalk job restores backup files for the given databases for the source to the destination server.</span></span> <span data-ttu-id="179f1-150">Par défaut, ce travail est planifié pour être exécuté toutes les minutes.</span><span class="sxs-lookup"><span data-stu-id="179f1-150">It is scheduled by default to run every minute.</span></span> <span data-ttu-id="179f1-151">Ce travail est exécuté en permanence, tant que des fichiers de sauvegarde sont à restaurer.</span><span class="sxs-lookup"><span data-stu-id="179f1-151">This job runs continuously without completing as long as there are backup files to restore.</span></span> <span data-ttu-id="179f1-152">Pour plus de précautions, vous pouvez exécuter ce travail une fois de plus pour vous assurer qu'il est bien fait.</span><span class="sxs-lookup"><span data-stu-id="179f1-152">As an extra precaution, you can run this job an additional time to ensure that it is complete.</span></span>  
  
    -   <span data-ttu-id="179f1-153">**ENVOI des journaux de restauration jusqu'à une marque**</span><span class="sxs-lookup"><span data-stu-id="179f1-153">**BTS Log Shipping Restore To Mark**</span></span>  
  
         <span data-ttu-id="179f1-154">Ce travail BizTalk restaure toutes les bases de données jusqu'à une marque dans la dernière sauvegarde du journal.</span><span class="sxs-lookup"><span data-stu-id="179f1-154">This BizTalk job restores all of the databases to a mark in the last log backup.</span></span> <span data-ttu-id="179f1-155">Cela garantit la cohérence transactionnelle de toutes les bases de données.</span><span class="sxs-lookup"><span data-stu-id="179f1-155">This ensures that all of the databases are in a transactionally consistent state.</span></span> <span data-ttu-id="179f1-156">En outre, ce travail recrée, sur le système de destination, tous les travaux de l'Agent SQL Server qui étaient sur le système source.</span><span class="sxs-lookup"><span data-stu-id="179f1-156">In addition, this job re-creates all of the SQL Server Agent jobs on the destination system that had been on the source system.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="179f1-157">Vous devez surveiller ces travaux pour vous assurer qu'ils n'échouent pas.</span><span class="sxs-lookup"><span data-stu-id="179f1-157">You should monitor these jobs to ensure that they do not fail.</span></span>  
  
10. <span data-ttu-id="179f1-158">Dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], accédez au dossier suivant :</span><span class="sxs-lookup"><span data-stu-id="179f1-158">On the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], go to the following folder:</span></span>  
  
     <span data-ttu-id="179f1-159">ordinateur 32 bits : %SystemDrive%\Program Files\Microsoft BizTalk Server \<version > \Schema\Restore</span><span class="sxs-lookup"><span data-stu-id="179f1-159">32-bit computer: %SystemDrive%\Program Files\Microsoft BizTalk Server \<version>\Schema\Restore</span></span>  
  
     <span data-ttu-id="179f1-160">ordinateur 64 bits : %SystemDrive%\Program Files (x86) \Microsoft BizTalk Server \<version > \Bins32\Schema\Restore</span><span class="sxs-lookup"><span data-stu-id="179f1-160">64-bit computer: %SystemDrive%\Program Files (x86)\Microsoft BizTalk Server \<version>\Bins32\Schema\Restore</span></span>  
  
11. <span data-ttu-id="179f1-161">Avec le bouton droit **SampleUpdateInfo.xml**, puis sélectionnez **modifier**.</span><span class="sxs-lookup"><span data-stu-id="179f1-161">Right-click **SampleUpdateInfo.xml**, and select **Edit**.</span></span> <span data-ttu-id="179f1-162">Procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="179f1-162">Do the following:</span></span>  
  
    -   <span data-ttu-id="179f1-163">Remplacez toutes les instances de **« SourceServer »** avec le nom du système source.</span><span class="sxs-lookup"><span data-stu-id="179f1-163">Replace all instances of **"SourceServer"** with the name of the source system.</span></span>  
  
    -   <span data-ttu-id="179f1-164">Remplacez toutes les instances de **« DestinationServer »** avec le nom du système de destination.</span><span class="sxs-lookup"><span data-stu-id="179f1-164">Replace all instances of **"DestinationServer"** with the name of the destination system.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="179f1-165">Utilisez des guillemets doubles pour encadrer le nom du système source et du système de destination.</span><span class="sxs-lookup"><span data-stu-id="179f1-165">Include the quotation marks around the name of the source and destination systems.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="179f1-166">Si vous avez renommé une des bases de données [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], vous devez également mettre à jour les noms de base de données dans le fichier XML.</span><span class="sxs-lookup"><span data-stu-id="179f1-166">If you renamed any of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases, you must also update the database names within the XML file.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="179f1-167">Si vous avez configuré l’analyse BAM, vous devez ajouter les lignes suivantes dans le **OtherDatabases** section de la **SampleUpdateInfo.xml** fichier pour les bases de données BAMAlertsApplication et BAMAlertsNSMain :</span><span class="sxs-lookup"><span data-stu-id="179f1-167">If you have configured BAM, you must add the following lines in the **OtherDatabases** section of the **SampleUpdateInfo.xml** file for the BAMAlertsApplication and BAMAlertsNSMain databases:</span></span>   
    > `<Database Name="BAM Alerts Application DB" oldDBName="BAMAlertsApplication" oldDBServer="SourceServer" newDBName=" BAMAlertsApplication" newDBServer="DestinationServer"/>`  
    > `<Database Name="BAM Alerts Instance DB" oldDBName="BAMAlertsNSMain" oldDBServer="SourceServer" newDBName="BAMAlertsNSMain" newDBServer="DestinationServer"/>`  
    >   
    >  <span data-ttu-id="179f1-168">Si vous avez modifié le nom par défaut de ces deux bases de données, utilisez les noms de bases de données réels.</span><span class="sxs-lookup"><span data-stu-id="179f1-168">If you changed the default name for these two databases, please use the actual database names.</span></span>  
  
12. <span data-ttu-id="179f1-169">Si vous avez plusieurs bases de données MessageBox dans votre [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] système, ajouter une ligne messageboxdb supplémentaire à la liste, puis définissez **IsMaster = « 0 »** pour les bases de données non-master.</span><span class="sxs-lookup"><span data-stu-id="179f1-169">If you have more than one MessageBox database in your [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] system, add another MessageBoxDB line to the list, and then set **IsMaster="0"** for the non-master databases.</span></span>  
  
13. <span data-ttu-id="179f1-170">Si vous utilisez l'analyse BAM ou le moteur de règles, supprimez les commentaires dans ces lignes, si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="179f1-170">If you are using BAM or the Rules Engine, uncomment these lines as appropriate.</span></span>  
  
14. <span data-ttu-id="179f1-171">Si vous avez des bases de données personnalisées, ajoutez-les sous la  **\<OtherDatabases >** section.</span><span class="sxs-lookup"><span data-stu-id="179f1-171">If you have any custom databases, add them under the **\<OtherDatabases>** section.</span></span> <span data-ttu-id="179f1-172">Consultez [comment sauvegarder des bases de données personnalisées](../core/how-to-back-up-custom-databases.md).</span><span class="sxs-lookup"><span data-stu-id="179f1-172">See [How to Back Up Custom Databases](../core/how-to-back-up-custom-databases.md).</span></span>  
  
15. <span data-ttu-id="179f1-173">Lorsque vous avez fini de modifier le fichier, enregistrez-le et fermez-le.</span><span class="sxs-lookup"><span data-stu-id="179f1-173">When you are finished editing the file, save it, and exit.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="179f1-174">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="179f1-174">Next Steps</span></span>  
 [<span data-ttu-id="179f1-175">Comment faire pour restaurer vos bases de données</span><span class="sxs-lookup"><span data-stu-id="179f1-175">How to Restore Your Databases</span></span>](../core/how-to-restore-your-databases.md)  
  
## <a name="see-also"></a><span data-ttu-id="179f1-176">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="179f1-176">See Also</span></span>  
 <span data-ttu-id="179f1-177">[Comment configurer le travail de sauvegarde de BizTalk Server](../core/how-to-configure-the-backup-biztalk-server-job.md) </span><span class="sxs-lookup"><span data-stu-id="179f1-177">[How to Configure the Backup BizTalk Server Job](../core/how-to-configure-the-backup-biztalk-server-job.md) </span></span>  
 <span data-ttu-id="179f1-178">[Comment planifier le travail de sauvegarde de BizTalk Server](../core/how-to-schedule-the-backup-biztalk-server-job.md) </span><span class="sxs-lookup"><span data-stu-id="179f1-178">[How to Schedule the Backup BizTalk Server Job](../core/how-to-schedule-the-backup-biztalk-server-job.md) </span></span>  
 [<span data-ttu-id="179f1-179">Comment sauvegarder des bases de données personnalisées</span><span class="sxs-lookup"><span data-stu-id="179f1-179">How to Back Up Custom Databases</span></span>](../core/how-to-back-up-custom-databases.md)