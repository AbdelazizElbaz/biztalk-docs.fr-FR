---
title: "Comment faire pour restaurer vos bases de données | Documents Microsoft"
ms.custom: 
ms.date: 2016-05-10
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- backing up, log shipping
- restoring [BAM], Star Schema database, Star Schema database [BAM], restoring
- restoring, 64-bit environments
- Star Schema database [BAM], restoring
- restoring [BAM], Analysis database
- log shipping
- databases, restoring
- Archive database [BAM], restoring
- backing up, restoring
- Analysis database [BAM], restoring
- restoring [BAM], Archive database
- restoring [BAM], Star Schema database
- databases, restoring [64-bit environment]
- Primary Import database [BAM], restoring
- 64-bit environments, restoring databases
- restoring, databases
ms.assetid: 0176932a-6b3d-4502-975b-a76296189092
caps.latest.revision: "52"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6833fff893a692475e97e7722d9d65658eace0d3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-restore-your-databases"></a><span data-ttu-id="159db-102">Restauration de vos bases de données</span><span class="sxs-lookup"><span data-stu-id="159db-102">How to Restore Your Databases</span></span>
<span data-ttu-id="159db-103">Vous devez restaurer toutes les bases de données à la même marque afin de garantir un état transactionnel cohérent entre les bases de données.</span><span class="sxs-lookup"><span data-stu-id="159db-103">You must restore all databases to the same mark to ensure a consistent transactional state among the databases.</span></span> <span data-ttu-id="159db-104">Consultez [Transactions marquées, sauvegardes complètes et sauvegardes de journaux](../core/marked-transactions-full-backups-and-log-backups.md).</span><span class="sxs-lookup"><span data-stu-id="159db-104">See [Marked Transactions, Full Backups, and Log Backups](../core/marked-transactions-full-backups-and-log-backups.md).</span></span>  
  
 <span data-ttu-id="159db-105">S'il n'y a qu'un serveur dans le système de destination, vérifiez que tous les jeux de sauvegarde de journal (à l'exception du jeu le plus récent) ont été restaurés.</span><span class="sxs-lookup"><span data-stu-id="159db-105">If there is only one server in the destination system, make sure that all of the log backup sets (except for the most recent set) have been restored.</span></span> <span data-ttu-id="159db-106">Consultez [affichage de l’historique de restauration des sauvegardes](../core/viewing-the-history-of-restored-backups.md).</span><span class="sxs-lookup"><span data-stu-id="159db-106">See [Viewing the History of Restored Backups](../core/viewing-the-history-of-restored-backups.md).</span></span> <span data-ttu-id="159db-107">Si tous les jeux de sauvegarde de journal n'ont pas été restaurés et que le travail de restauration n'est pas en cours d'exécution, exécutez ce dernier (manuellement le cas échéant).</span><span class="sxs-lookup"><span data-stu-id="159db-107">If all the log backup sets have not been restored, and the restore job is not currently running, run the restore job (manually if necessary).</span></span> <span data-ttu-id="159db-108">S'il reste des jeux de sauvegarde pouvant être restaurés, ils sont traités par le travail jusqu'à ce que qu'ils soient tous restaurés.</span><span class="sxs-lookup"><span data-stu-id="159db-108">If there are outstanding backup sets that can be restored, the job processes them until they are all restored.</span></span>  
  
 <span data-ttu-id="159db-109">S'il y a plusieurs serveurs dans le système de destination, tous les serveurs doivent être restaurés vers le même jeu de sauvegarde.</span><span class="sxs-lookup"><span data-stu-id="159db-109">If there are multiple servers in the destination system, all servers must be restored to the same backup set.</span></span> <span data-ttu-id="159db-110">Consultez l'historique de restauration sur chaque serveur et vérifiez que le jeu de sauvegarde le plus récent restauré est identique sur tous les serveurs.</span><span class="sxs-lookup"><span data-stu-id="159db-110">View the restore history on each server and make sure that the most recent log backup set restored is the same on all servers.</span></span> <span data-ttu-id="159db-111">Si ce n'est pas le cas, vous devez exécuter manuellement le travail de restauration sur chaque serveur pour lequel le jeu de sauvegarde le plus récent doit être restauré.</span><span class="sxs-lookup"><span data-stu-id="159db-111">If it is not, you must manually run the restore job on each server that needs the most recent log backup set restored.</span></span>  
  
 <span data-ttu-id="159db-112">Une fois tous les serveurs restaurés vers le même jeu de sauvegarde, le jeu final peut être restauré manuellement.</span><span class="sxs-lookup"><span data-stu-id="159db-112">After all of the servers are on the same backup set, the final set can be manually restored.</span></span>  
  
 <span data-ttu-id="159db-113">La table adm_BackupHistory est le point d'historique central pour l'envoi des journaux du système source.</span><span class="sxs-lookup"><span data-stu-id="159db-113">The adm_BackupHistory table is the central history point for the log shipping process for the source system.</span></span> <span data-ttu-id="159db-114">Tous les travaux de sauvegarde effectués sont enregistrés dans cette table.</span><span class="sxs-lookup"><span data-stu-id="159db-114">All backup work performed is recorded to this table.</span></span> <span data-ttu-id="159db-115">Tous les serveurs du système de destination lisent cette table pour recevoir les informations nécessaires à l'exécution des travaux de restauration.</span><span class="sxs-lookup"><span data-stu-id="159db-115">All servers in your destination system read from this table to receive the information needed to perform their restore work.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="159db-116">Si vous restaurez la base de données d'importation principale BAM à partir d'une sauvegarde, vous devez également restaurer les bases de données des archives BAM, de schémas en étoile BAM et d'analyse BAM à l'aide d'une sauvegarde antérieure à la sauvegarde principale BAM.</span><span class="sxs-lookup"><span data-stu-id="159db-116">If you restore the BAM Primary Import database from a backup, then you should also restore the BAM Archive, BAM Star Schema, and BAM Analysis databases by using a backup older than the BAM Primary backup.</span></span> <span data-ttu-id="159db-117">Consultez [sauvegarde et restauration BAM](../core/backing-up-and-restoring-bam.md).</span><span class="sxs-lookup"><span data-stu-id="159db-117">See [Backing Up and Restoring BAM](../core/backing-up-and-restoring-bam.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="159db-118">Si vous déplacez les sauvegardes complètes ou de journal d'une base de données source de l'emplacement dans lequel le travail de sauvegarde de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] les a placées, vous devez mettre à jour la ligne associée à cette base de données dans la table bts_LogShippingDatabases sur le système de destination en pointant LogFileLocation ou DBFileLocation sur le nouvel emplacement dans lequel le système de destination doit lire les fichiers de sauvegarde complète/de journal.</span><span class="sxs-lookup"><span data-stu-id="159db-118">If you move the full or log backups for a source database from the location in which the Backup [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] job put them, you should update the associated row for that database in the bts_LogShippingDatabases table on the destination system by setting the LogFileLocation or DBFileLocation to the new location where the destination system should read the full/log backup files.</span></span> <span data-ttu-id="159db-119">Cette table est renseignée lorsque vous exécutez la procédure stockée bts_ConfigureBtsLogShipping.</span><span class="sxs-lookup"><span data-stu-id="159db-119">This table is populated when you run the bts_ConfigureBtsLogShipping stored procedure.</span></span> <span data-ttu-id="159db-120">Par défaut, ces colonnes sont définies sur la valeur Null (qui indique que le système de destination doit lire les fichiers de sauvegarde à partir de l'emplacement stocké dans la table adm_BackupHistory).</span><span class="sxs-lookup"><span data-stu-id="159db-120">By default, these columns are set to null, which indicates that the destination system should read the backup files from the location stored in the adm_BackupHistory table.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="159db-121">Conservez toujours une copie de vos fichiers de sauvegarde dans un emplacement sécurisé :</span><span class="sxs-lookup"><span data-stu-id="159db-121">Always keep a copy of your backup files in a secure location.</span></span> <span data-ttu-id="159db-122">même si vous disposez de sauvegardes de journal, vous ne pouvez pas restaurer vos bases de données sans les fichiers de sauvegarde.</span><span class="sxs-lookup"><span data-stu-id="159db-122">Even if you have log backups, you cannot restore your databases without the backup files.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="159db-123">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="159db-123">Prerequisites</span></span>  
 <span data-ttu-id="159db-124">Connectez-vous à SQL Server en utilisant un compte qui est membre du rôle sysadmin SQL Server.</span><span class="sxs-lookup"><span data-stu-id="159db-124">Log in to SQL Server using an account that is a member of the sysadmin SQL Server role.</span></span>  
  
### <a name="to-restore-your-databases"></a><span data-ttu-id="159db-125">Pour restaurer vos bases de données</span><span class="sxs-lookup"><span data-stu-id="159db-125">To restore your databases</span></span>  
  
1.  <span data-ttu-id="159db-126">Sur le système de destination, ouvrez **SQL Server Management Studio**et vous connecter à votre [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="159db-126">On the destination system, open **SQL Server Management Studio**, and connect to your [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)].</span></span>  
  
2.  <span data-ttu-id="159db-127">Développez **Agent SQL Server**, puis **Travaux**.</span><span class="sxs-lookup"><span data-stu-id="159db-127">Expand **SQL Server Agent**, and expand **Jobs**.</span></span> <span data-ttu-id="159db-128">Procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="159db-128">Do the following:</span></span>  
  
    1.  <span data-ttu-id="159db-129">Cliquez avec le bouton droit sur le travail **Envoi de journaux de BizTalk Server - Obtenir l'historique des sauvegardes** , puis sélectionnez **Désactiver**.</span><span class="sxs-lookup"><span data-stu-id="159db-129">Right-click the **BTS Log Shipping - Get Backup History** job and select **Disable**.</span></span> <span data-ttu-id="159db-130">L'état passe à Réussite.</span><span class="sxs-lookup"><span data-stu-id="159db-130">The status changes to Success.</span></span>  
  
    2.  <span data-ttu-id="159db-131">Cliquez avec le bouton droit sur le travail **Envoi de journaux de BizTalk Server - Restaurer les bases de données** , puis sélectionnez **Désactiver**.</span><span class="sxs-lookup"><span data-stu-id="159db-131">Right-click the **BTS Log Shipping - Restore Databases** job and select **Disable**.</span></span> <span data-ttu-id="159db-132">L'état passe à Réussite.</span><span class="sxs-lookup"><span data-stu-id="159db-132">The status changes to Success.</span></span>  
  
    3.  <span data-ttu-id="159db-133">Cliquez sur le travail **Envoi de journaux de BizTalk Server - Restaurer à la marque** et sélectionnez **Démarrer le travail à l'étape**.</span><span class="sxs-lookup"><span data-stu-id="159db-133">Right-click the **BTS Log Shipping - Restore To Mark** and select **Start Job at Step**.</span></span> <span data-ttu-id="159db-134">Sélectionnez **ID d'étape 1** , puis **Démarrer**.</span><span class="sxs-lookup"><span data-stu-id="159db-134">Select **Step ID 1** and select **Start**.</span></span>  
  
         <span data-ttu-id="159db-135">Lorsque l’état passe à **réussite**, les travaux de l’Agent SQL Server et [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] bases de données sont restaurés dans le système de destination.</span><span class="sxs-lookup"><span data-stu-id="159db-135">When the status changes to **Success**, the SQL Server Agent jobs and [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases are restored to the destination system.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="159db-136">Si l' **État** est Erreur, sélectionnez le lien dans le champ Message pour déterminer la cause.</span><span class="sxs-lookup"><span data-stu-id="159db-136">If the **Status** is Error, select the link in the Message field to determine the cause.</span></span> <span data-ttu-id="159db-137">Ces travaux doivent avoir l'état Réussite avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="159db-137">These jobs should have a Success status before continuing.</span></span>  
  
3.  <span data-ttu-id="159db-138">Sur le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] où vous avez modifié le fichier SampleUpdateInfo.xml, ouvrez une invite de commandes et accédez à :</span><span class="sxs-lookup"><span data-stu-id="159db-138">On the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] where you edited the SampleUpdateInfo.xml file, open a command prompt, and go to:</span></span>  
  
     <span data-ttu-id="159db-139">ordinateur 32 bits :`%SystemDrive%\Program Files\Microsoft BizTalk Server <version>\Schema\Restore`</span><span class="sxs-lookup"><span data-stu-id="159db-139">32-bit computer: `%SystemDrive%\Program Files\Microsoft BizTalk Server <version>\Schema\Restore`</span></span>  
  
     <span data-ttu-id="159db-140">ordinateur 64 bits :`%SystemDrive%\Program Files (x86)\Microsoft BizTalk Server <version>\Bins32\Schema\Restore`</span><span class="sxs-lookup"><span data-stu-id="159db-140">64-bit computer: `%SystemDrive%\Program Files (x86)\Microsoft BizTalk Server <version>\Bins32\Schema\Restore`</span></span>  
  
4.  <span data-ttu-id="159db-141">À l'invite de commandes, tapez :</span><span class="sxs-lookup"><span data-stu-id="159db-141">At the command prompt, type:</span></span>  
  
     `cscript UpdateDatabase.vbs SampleUpdateInfo.xml`  
  
     <span data-ttu-id="159db-142">Ce script met à jour toutes les tables qui stockent des informations sur l'emplacement des autres bases de données.</span><span class="sxs-lookup"><span data-stu-id="159db-142">This script updates all tables that store information about the location of other databases.</span></span>  
  
    > [!IMPORTANT]
    >  -   <span data-ttu-id="159db-143">Exécutez UpdateDatabase.vbs sur **un** serveur dans le groupe BizTalk.</span><span class="sxs-lookup"><span data-stu-id="159db-143">Run UpdateDatabase.vbs on **one** server in the BizTalk group.</span></span>  
    > -   <span data-ttu-id="159db-144">Sur les ordinateurs 64 bits, vous devez exécuter UpdateDatabase.vbs à partir d'une invite de commandes 64 bits.</span><span class="sxs-lookup"><span data-stu-id="159db-144">On 64-bit computers, you must run UpdateDatabase.vbs from a 64-bit command prompt.</span></span> <span data-ttu-id="159db-145">Notez que l'invite de commandes par défaut sur les ordinateurs 64 bits est une invite de commandes 64 bits et se trouve dans %SystemDrive%\windows\System32\cmd.exe.</span><span class="sxs-lookup"><span data-stu-id="159db-145">Note that the default command prompt on 64-bit computers is a 64-bit command prompt and is located at %SystemDrive%\windows\System32\cmd.exe.</span></span>  
    > -   <span data-ttu-id="159db-146">Le moteur EDI BizTalk ne nécessite aucune de ses propres modifications à SampleUpdateInfo.xml lors de la restauration des bases de données.</span><span class="sxs-lookup"><span data-stu-id="159db-146">The BizTalk EDI engine does not require any of its own modifications to SampleUpdateInfo.xml when restoring databases.</span></span>  <span data-ttu-id="159db-147">Il s’appuie sur la connectivité à la base de données BizTalkDTADb pour accéder aux tables EDI.</span><span class="sxs-lookup"><span data-stu-id="159db-147">It relies on connectivity to the BizTalkDTADb database to access the EDI tables.</span></span>  
  
5.  <span data-ttu-id="159db-148">Copiez le fichier SampleUpdateInfo.xml modifié dans le dossier suivant sur **chaque** ordinateur exécutant [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] dans ce groupe BizTalk :</span><span class="sxs-lookup"><span data-stu-id="159db-148">Copy the edited SampleUpdateInfo.xml file to the following folder on **every** computer running [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] in this BizTalk group:</span></span>  
  
     <span data-ttu-id="159db-149">ordinateur 32 bits : copier vers`%SystemDrive%\Program Files\Microsoft BizTalk Server <version>\Schema\Restore`</span><span class="sxs-lookup"><span data-stu-id="159db-149">32-bit computer: Copy to `%SystemDrive%\Program Files\Microsoft BizTalk Server <version>\Schema\Restore`</span></span>  
  
     <span data-ttu-id="159db-150">ordinateur 64 bits : copier vers`%SystemDrive%\Program Files (x86)\Microsoft BizTalk Server <version>\Bins32\Schema\Restore`</span><span class="sxs-lookup"><span data-stu-id="159db-150">64-bit computer: Copy to `%SystemDrive%\Program Files (x86)\Microsoft BizTalk Server <version>\Bins32\Schema\Restore`</span></span>  
  
6.  <span data-ttu-id="159db-151">Sur **chaque** ordinateur dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] de groupe, ouvrez une invite de commandes et accédez à :</span><span class="sxs-lookup"><span data-stu-id="159db-151">On **each** computer in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] group, open a command prompt, and go to:</span></span>  
  
     <span data-ttu-id="159db-152">ordinateur 32 bits :`%SystemDrive%\Program Files\Microsoft BizTalk Server <version>\Schema\Restore`</span><span class="sxs-lookup"><span data-stu-id="159db-152">32-bit computer: `%SystemDrive%\Program Files\Microsoft BizTalk Server <version>\Schema\Restore`</span></span>  
  
     <span data-ttu-id="159db-153">ordinateur 64 bits :`%SystemDrive%Program Files (x86)Microsoft BizTalk Server <version>Bins32SchemaRestore`</span><span class="sxs-lookup"><span data-stu-id="159db-153">64-bit computer: `%SystemDrive%Program Files (x86)Microsoft BizTalk Server <version>Bins32SchemaRestore`</span></span>  
  
7.  <span data-ttu-id="159db-154">À l'invite de commandes, tapez :</span><span class="sxs-lookup"><span data-stu-id="159db-154">At the command prompt, type:</span></span>  
  
     `cscript UpdateRegistry.vbs SampleUpdateInfo.xml`  
  
     <span data-ttu-id="159db-155">Ce script met à jour toutes les entrées de Registre qui stockent des informations sur l'emplacement des autres bases de données.</span><span class="sxs-lookup"><span data-stu-id="159db-155">This script updates all registry entries that store information about the location of other databases.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="159db-156">Exécutez UpdateRegistry.vbs sur **chaque** serveur dans le groupe BizTalk.</span><span class="sxs-lookup"><span data-stu-id="159db-156">Run UpdateRegistry.vbs on **every** server in the BizTalk group.</span></span>  
    >   
    >  <span data-ttu-id="159db-157">Sur les ordinateurs 64 bits, vous devez exécuter UpdateRegistry.vbs à partir d'une invite de commandes 64 bits.</span><span class="sxs-lookup"><span data-stu-id="159db-157">On 64-bit computers, you must run UpdateRegistry.vbs from a 64-bit command prompt.</span></span>  <span data-ttu-id="159db-158">Notez que l'invite de commandes par défaut sur les ordinateurs 64 bits est une invite de commandes 64 bits et se trouve dans %SystemDrive%\windows\System32\cmd.exe.</span><span class="sxs-lookup"><span data-stu-id="159db-158">Note that the default command prompt on 64-bit computers is a 64-bit command prompt and is located at %SystemDrive%\windows\System32\cmd.exe.</span></span>  
  
8.  <span data-ttu-id="159db-159">Redémarrez tous les services [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="159db-159">Restart all the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] services.</span></span> <span data-ttu-id="159db-160">Consultez [comment faire pour démarrer, arrêter, suspendre, reprendre ou redémarrer le serveur BizTalk Services](../core/how-to-start-stop-pause-resume-or-restart-biztalk-server-services.md).</span><span class="sxs-lookup"><span data-stu-id="159db-160">See [How to Start, Stop, Pause, Resume, or Restart BizTalk Server Services](../core/how-to-start-stop-pause-resume-or-restart-biztalk-server-services.md).</span></span>  
  
9. <span data-ttu-id="159db-161">Une fois vos bases de données restaurées, redémarrez le service WMI (Windows Management Instrumentation) :</span><span class="sxs-lookup"><span data-stu-id="159db-161">After restoring your databases, restart the Windows Management Instrumentation service:</span></span>  
  
    1.  <span data-ttu-id="159db-162">Ouvrez **services.msc**.</span><span class="sxs-lookup"><span data-stu-id="159db-162">Open **services.msc**.</span></span>  
  
    2.  <span data-ttu-id="159db-163">Cliquez avec le bouton droit sur **Windows Management Instrumentation**, puis sélectionnez **Redémarrer**.</span><span class="sxs-lookup"><span data-stu-id="159db-163">Right-click **Windows Management Instrumentation**, and then select **Restart**.</span></span>  
  
10. <span data-ttu-id="159db-164">Ouvrez **Administration de BizTalk Server.**</span><span class="sxs-lookup"><span data-stu-id="159db-164">Open **BizTalk Server Administration**.</span></span> <span data-ttu-id="159db-165">Procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="159db-165">Do the following:</span></span>  
  
    1.  <span data-ttu-id="159db-166">Cliquez avec le bouton droit sur le projet **BizTalk Group** , puis sélectionnez **Supprimer**.</span><span class="sxs-lookup"><span data-stu-id="159db-166">Right-click the **BizTalk Group** and select **Remove**.</span></span>  
  
    2.  <span data-ttu-id="159db-167">Cliquez avec le bouton droit sur le nœud **Administration de BizTalk Server** et sélectionnez **Se connecter au groupe existant**.</span><span class="sxs-lookup"><span data-stu-id="159db-167">Right-click **BizTalk Server Administration** and select **Connect to Existing Group**.</span></span>  
  
    3.  <span data-ttu-id="159db-168">Dans **Nom du serveur SQL**, sélectionnez le nom de l'instance SQL Server qui héberge la base de données de gestion BizTalk.</span><span class="sxs-lookup"><span data-stu-id="159db-168">In **SQL Server name**, select the name of the SQL Server instance that hosts the BizTalk Management database.</span></span> <span data-ttu-id="159db-169">Lorsque vous sélectionnez l'instance SQL Server, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] détecte automatiquement les bases de données [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sur l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="159db-169">When you select the SQL Server instance, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] automatically detects the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases on that computer.</span></span>  
  
    4.  <span data-ttu-id="159db-170">Dans **Nom de la base de données**, sélectionnez votre base de données de gestion BizTalk (**BizTalkMgmtDb** par défaut), puis sélectionnez **OK**.</span><span class="sxs-lookup"><span data-stu-id="159db-170">In **Database name**, select your BizTalk Management database (**BizTalkMgmtDb** by default), and then select **OK**.</span></span>  
  
     <span data-ttu-id="159db-171">La console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ajoute le groupe BizTalk à la console Administration.</span><span class="sxs-lookup"><span data-stu-id="159db-171">The [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console adds the BizTalk group to the Administration console.</span></span>  
  
     <span data-ttu-id="159db-172">[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] est désormais restauré et doit être en cours d'exécution.</span><span class="sxs-lookup"><span data-stu-id="159db-172">Your [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is now restored and should be running.</span></span> <span data-ttu-id="159db-173">Configurez ensuite le travail de sauvegarde de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour commencer l'écriture des sauvegardes vers un nouveau serveur de destination.</span><span class="sxs-lookup"><span data-stu-id="159db-173">Next, configure the Backup [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] job to start writing backups to a new destination server.</span></span> <span data-ttu-id="159db-174">Vous devez également reconfigurer un nouveau système de destination.</span><span class="sxs-lookup"><span data-stu-id="159db-174">You should also reconfigure a new destination system.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="159db-175">Si vous utilisez le moteur des règles, vous devez redémarrer le service de mise à jour du moteur des règles sur chaque serveur du groupe [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] après la restauration des bases de données.</span><span class="sxs-lookup"><span data-stu-id="159db-175">If you are using the Rules Engine, after restoring the databases, you must restart the Rule Engine Update Service on every server in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] group.</span></span> <span data-ttu-id="159db-176">Consultez [comment faire pour démarrer, arrêter, suspendre, reprendre ou redémarrer le serveur BizTalk Services](../core/how-to-start-stop-pause-resume-or-restart-biztalk-server-services.md).</span><span class="sxs-lookup"><span data-stu-id="159db-176">See [How to Start, Stop, Pause, Resume, or Restart BizTalk Server Services](../core/how-to-start-stop-pause-resume-or-restart-biztalk-server-services.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="159db-177">Si vous utilisez l'analyse BAM, vous devez à présent restaurer les bases de données BAM.</span><span class="sxs-lookup"><span data-stu-id="159db-177">If you are using BAM, this is the time to restore the BAM databases.</span></span> <span data-ttu-id="159db-178">Consultez [sauvegarde et restauration BAM](../core/backing-up-and-restoring-bam.md).</span><span class="sxs-lookup"><span data-stu-id="159db-178">See [Backing Up and Restoring BAM](../core/backing-up-and-restoring-bam.md).</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="159db-179">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="159db-179">Next Steps</span></span>  
 [<span data-ttu-id="159db-180">Sauvegarde et restauration BAM</span><span class="sxs-lookup"><span data-stu-id="159db-180">Backing Up and Restoring BAM</span></span>](../core/backing-up-and-restoring-bam.md)  
  
## <a name="see-also"></a><span data-ttu-id="159db-181">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="159db-181">See Also</span></span>  
 <span data-ttu-id="159db-182">[Comment configurer le travail de sauvegarde de BizTalk Server](../core/how-to-configure-the-backup-biztalk-server-job.md) </span><span class="sxs-lookup"><span data-stu-id="159db-182">[How to Configure the Backup BizTalk Server Job](../core/how-to-configure-the-backup-biztalk-server-job.md) </span></span>  
 [<span data-ttu-id="159db-183">Comment configurer le système de Destination pour l’envoi de journaux</span><span class="sxs-lookup"><span data-stu-id="159db-183">How to Configure the Destination System for Log Shipping</span></span>](../core/how-to-configure-the-destination-system-for-log-shipping.md)