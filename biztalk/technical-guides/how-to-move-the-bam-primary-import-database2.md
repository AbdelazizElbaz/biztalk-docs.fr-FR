---
title: Comment déplacer la Database2 d’importation principale BAM | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bc4f2656-2faa-4503-9551-05e1b6eceb1a
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fd6abeeb04521e95b32b4d6007dcc7f1f532bdbb
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/28/2018
---
# <a name="how-to-move-the-bam-primary-import-database"></a><span data-ttu-id="7f9fc-102">Déplacement de la base de données d'importation principale BAM</span><span class="sxs-lookup"><span data-stu-id="7f9fc-102">How to Move the BAM Primary Import Database</span></span>
<span data-ttu-id="7f9fc-103">Cette procédure vous permet de déplacer la base de données d'importation principale BAM vers un autre serveur.</span><span class="sxs-lookup"><span data-stu-id="7f9fc-103">You can use this procedure to move the BAM Primary Import database to another server.</span></span> <span data-ttu-id="7f9fc-104">À partir d’un point de vue du scénario de bout en bout, le déplacement de la base de données d’importation principale BAM implique deux étapes principales :</span><span class="sxs-lookup"><span data-stu-id="7f9fc-104">From an end-to-end scenario perspective, moving the BAM Primary Import database involves two major steps:</span></span>  
  
-   [<span data-ttu-id="7f9fc-105">Déplacement de la base de données importation principale BAM</span><span class="sxs-lookup"><span data-stu-id="7f9fc-105">Moving the BAM Primary Import Database</span></span>](../technical-guides/how-to-move-the-bam-primary-import-database2.md#BKMK_MovingBAMPI)  
  
-   [<span data-ttu-id="7f9fc-106">Mise à jour des références à la nouvelle base de données importation principale BAM</span><span class="sxs-lookup"><span data-stu-id="7f9fc-106">Updating References to the New BAM Primary Import Database</span></span>](../technical-guides/how-to-move-the-bam-primary-import-database2.md#BKMK_BAMPIRef)  
  
## <a name="prerequisites"></a><span data-ttu-id="7f9fc-107">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="7f9fc-107">Prerequisites</span></span>  
 <span data-ttu-id="7f9fc-108">Pour exécuter cette procédure, vous devez ouvrir une session à l'aide d'un compte membre du rôle serveur fixe sysadmin [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7f9fc-108">You must be logged on with an account that is a member of the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] sysadmin fixed server role to perform this procedure.</span></span>  
  
##  <a name="BKMK_MovingBAMPI"></a> <span data-ttu-id="7f9fc-109">Déplacement de la base de données importation principale BAM</span><span class="sxs-lookup"><span data-stu-id="7f9fc-109">Moving the BAM Primary Import Database</span></span>  
 <span data-ttu-id="7f9fc-110">Les étapes de la procédure suivante pour déplacer la base de données d’importation principale BAM.</span><span class="sxs-lookup"><span data-stu-id="7f9fc-110">Perform the steps in the following procedure to move the BAM Primary Import database.</span></span>  
  
#### <a name="to-move-the-bam-primary-import-database"></a><span data-ttu-id="7f9fc-111">Pour déplacer la base de données d'importation principale BAM</span><span class="sxs-lookup"><span data-stu-id="7f9fc-111">To move the BAM Primary Import database</span></span>  
  
1.  <span data-ttu-id="7f9fc-112">Arrêtez toute analyse BAM cube mise à jour et les données maintenance SSIS, ou empêchez leur exécution jusqu'à ce que vous avez restauré la base de données d’importation principale BAM.</span><span class="sxs-lookup"><span data-stu-id="7f9fc-112">Stop any BAM cube update and data maintenance SSIS packages, or prevent them from running until you have restored the BAM Primary Import database.</span></span>  
  
2.  <span data-ttu-id="7f9fc-113">Arrêtez tous les services [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7f9fc-113">Stop all [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] services.</span></span> <span data-ttu-id="7f9fc-114">Pour plus d’informations, consultez la rubrique [comment démarrer, arrêter, suspendre, reprendre ou redémarrer les Services BizTalk Server](http://go.microsoft.com/fwlink/?LinkId=154394) (http://go.microsoft.com/fwlink/?LinkId=154394) dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] aide.</span><span class="sxs-lookup"><span data-stu-id="7f9fc-114">For more information, see the topic [How To Start, Stop, Pause, Resume, or Restart BizTalk Server Services](http://go.microsoft.com/fwlink/?LinkId=154394) (http://go.microsoft.com/fwlink/?LinkId=154394) in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help.</span></span>  
  
3.  <span data-ttu-id="7f9fc-115">Arrêtez le service IIS.</span><span class="sxs-lookup"><span data-stu-id="7f9fc-115">Stop the IIS service.</span></span>  
  
4.  <span data-ttu-id="7f9fc-116">Arrêtez le service de Notification des alertes BAM :</span><span class="sxs-lookup"><span data-stu-id="7f9fc-116">Stop the BAM Alerts Notification service:</span></span>  
  
    1.  <span data-ttu-id="7f9fc-117">Cliquez sur **Démarrer**, puis sur **Exécuter**, tapez **cmd**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="7f9fc-117">Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
    2.  <span data-ttu-id="7f9fc-118">À l'invite de commandes, tapez :</span><span class="sxs-lookup"><span data-stu-id="7f9fc-118">At the command prompt, type:</span></span>  
  
         <span data-ttu-id="7f9fc-119">**Net stop NS$ BamAlerts**</span><span class="sxs-lookup"><span data-stu-id="7f9fc-119">**Net stop NS$BamAlerts**</span></span>  
  
5.  <span data-ttu-id="7f9fc-120">Sauvegardez la principale BAM importer la base de données sur l’ancien serveur.</span><span class="sxs-lookup"><span data-stu-id="7f9fc-120">Back up the BAM Primary import database on the old server.</span></span> <span data-ttu-id="7f9fc-121">Pour obtenir des instructions sur la sauvegarde d’une base de données, suivez les instructions sur la sauvegarde d’une base de données à [procédure : sauvegarder une base de données (SQL Server Management Studio)](http://go.microsoft.com/fwlink/?LinkId=156510) (http://go.microsoft.com/fwlink/?LinkId=156510) dans [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] la documentation en ligne.</span><span class="sxs-lookup"><span data-stu-id="7f9fc-121">For instructions on backing up a database, follow the instructions on how to back up a database at [How to: Back Up a Database (SQL Server Management Studio)](http://go.microsoft.com/fwlink/?LinkId=156510) (http://go.microsoft.com/fwlink/?LinkId=156510) in [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Books Online.</span></span>  
  
6.  <span data-ttu-id="7f9fc-122">Copier la base de données d’importation principale BAM vers la nouvelle [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] ordinateur.</span><span class="sxs-lookup"><span data-stu-id="7f9fc-122">Copy the BAM Primary Import database to the new [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] computer.</span></span>  
  
7.  <span data-ttu-id="7f9fc-123">Restaurez la base de données importation principale BAM sur le nouveau serveur.</span><span class="sxs-lookup"><span data-stu-id="7f9fc-123">Restore the BAM Primary import database on the new server.</span></span> <span data-ttu-id="7f9fc-124">Pour obtenir des instructions sur la restauration de la base de données, suivez les instructions relatives à la restauration d’une base de données à [Comment : restaurer une sauvegarde de base de données (SQL Server Management Studio)](http://go.microsoft.com/fwlink/?LinkId=156511) (http://go.microsoft.com/fwlink/?LinkId=156511) dans [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] la documentation en ligne.</span><span class="sxs-lookup"><span data-stu-id="7f9fc-124">For instructions on restoring the database, follow the instructions on how to restore a database at [How to: Restore a Database Backup (SQL Server Management Studio)](http://go.microsoft.com/fwlink/?LinkId=156511) (http://go.microsoft.com/fwlink/?LinkId=156511) in [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Books Online.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="7f9fc-125">Si vous restaurez la base de données d'importation principale BAM à partir d'une sauvegarde, vous devez également restaurer les bases de données des archives BAM, de schémas en étoile BAM et d'analyse BAM à l'aide d'une sauvegarde antérieure à la sauvegarde principale BAM.</span><span class="sxs-lookup"><span data-stu-id="7f9fc-125">If you restore the BAM Primary Import database from a backup, then you should also restore the BAM Archive, BAM Star Schema, and BAM Analysis databases by using a backup older than the BAM Primary backup.</span></span>  
  
##  <a name="BKMK_BAMPIRef"></a> <span data-ttu-id="7f9fc-126">Mise à jour des références à la nouvelle base de données importation principale BAM</span><span class="sxs-lookup"><span data-stu-id="7f9fc-126">Updating References to the New BAM Primary Import Database</span></span>  
 <span data-ttu-id="7f9fc-127">Une fois que vous avez déplacé la base de données, vous devez mettre à jour toutes les références à la nouvelle base importation principale BAM.</span><span class="sxs-lookup"><span data-stu-id="7f9fc-127">After you have moved the database, you must update all the references to the new BAM Primary Import Database.</span></span> <span data-ttu-id="7f9fc-128">Les références suivantes doivent être mises à jour :</span><span class="sxs-lookup"><span data-stu-id="7f9fc-128">The following references must be updated:</span></span>  
  
-   <span data-ttu-id="7f9fc-129">Mettre à jour toutes les bases de données BizTalk avec le nouveau nom de serveur.</span><span class="sxs-lookup"><span data-stu-id="7f9fc-129">Update all the BizTalk databases with the new server name.</span></span> <span data-ttu-id="7f9fc-130">Vous pouvez le faire en utilisant le script UpdateDatabase.vbs.</span><span class="sxs-lookup"><span data-stu-id="7f9fc-130">You can do so by using the UpdateDatabase.vbs script.</span></span> <span data-ttu-id="7f9fc-131">Consultez [pour mettre à jour des bases de données BizTalk avec le nouveau nom de serveur](../technical-guides/how-to-move-the-bam-primary-import-database2.md#BKMK_UpdateDB).</span><span class="sxs-lookup"><span data-stu-id="7f9fc-131">See [To update BizTalk Databases with the new server name](../technical-guides/how-to-move-the-bam-primary-import-database2.md#BKMK_UpdateDB).</span></span>  
  
-   <span data-ttu-id="7f9fc-132">Mettre à jour le fichier Web.config pour le portail BAM.</span><span class="sxs-lookup"><span data-stu-id="7f9fc-132">Update the Web.config file for the BAM portal.</span></span> <span data-ttu-id="7f9fc-133">Consultez [pour mettre à jour le fichier Web.config pour le portail BAM](../technical-guides/how-to-move-the-bam-primary-import-database2.md#BKMK_Config).</span><span class="sxs-lookup"><span data-stu-id="7f9fc-133">See [To update the Web.config file for the BAM portal](../technical-guides/how-to-move-the-bam-primary-import-database2.md#BKMK_Config).</span></span>  
  
-   <span data-ttu-id="7f9fc-134">Mettre à jour la référence à la base d’importation principale BAM dans tous les fichiers de données actives d’analyse BAM, Microsoft Excel.</span><span class="sxs-lookup"><span data-stu-id="7f9fc-134">Update the reference to the BAM Primary Import Database in all BAM Livedata Microsoft Excel files.</span></span> <span data-ttu-id="7f9fc-135">Consultez [pour mettre à jour la référence dans les fichiers de données actives d’analyse BAM, Microsoft Excel](../technical-guides/how-to-move-the-bam-primary-import-database2.md#BKMK_UpdateExcel).</span><span class="sxs-lookup"><span data-stu-id="7f9fc-135">See [To update reference in BAM Livedata Microsoft Excel files](../technical-guides/how-to-move-the-bam-primary-import-database2.md#BKMK_UpdateExcel).</span></span>  
  
-   <span data-ttu-id="7f9fc-136">Mettre à jour les nouveaux noms de serveur et de base de données dans tous les packages SSIS d’analyse BAM.</span><span class="sxs-lookup"><span data-stu-id="7f9fc-136">Update the new server and database names in all BAM analysis SSIS packages.</span></span> <span data-ttu-id="7f9fc-137">Consultez [pour mettre à jour les noms de serveur et base de données dans tous les packages BAM SSIS](../technical-guides/how-to-move-the-bam-primary-import-database2.md#BKMK_UpdatePckg).</span><span class="sxs-lookup"><span data-stu-id="7f9fc-137">See [To update server and database names in all BAM SSIS packages](../technical-guides/how-to-move-the-bam-primary-import-database2.md#BKMK_UpdatePckg).</span></span>  
  
-   <span data-ttu-id="7f9fc-138">Mettre à jour les nouveaux noms de serveur et de base de données dans des sources de données pour tous les cubes OLAP.</span><span class="sxs-lookup"><span data-stu-id="7f9fc-138">Update the new server and database names in data sources for all OLAP cubes.</span></span> <span data-ttu-id="7f9fc-139">Consultez [pour mettre à jour les noms de serveur et base de données dans des sources de données pour tous les cubes OLAP](../technical-guides/how-to-move-the-bam-primary-import-database2.md#BKMK_UpdateDSOLAP).</span><span class="sxs-lookup"><span data-stu-id="7f9fc-139">See [To update server and database names in data sources for all OLAP cubes](../technical-guides/how-to-move-the-bam-primary-import-database2.md#BKMK_UpdateDSOLAP).</span></span>  
  
###  <a name="BKMK_UpdateDB"></a> <span data-ttu-id="7f9fc-140">Pour mettre à jour des bases de données BizTalk avec le nouveau nom de serveur</span><span class="sxs-lookup"><span data-stu-id="7f9fc-140">To update BizTalk Databases with the new server name</span></span>  
  
1.  <span data-ttu-id="7f9fc-141">Sur un ordinateur exécutant BizTalk Server, accédez au dossier suivant :</span><span class="sxs-lookup"><span data-stu-id="7f9fc-141">On a computer running BizTalk Server, browse to the following folder:</span></span>  
  
    -   <span data-ttu-id="7f9fc-142">Si [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] est installé sur une version 64 bits de Windows Server :</span><span class="sxs-lookup"><span data-stu-id="7f9fc-142">If [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is installed on a 64-bit version of Windows Server:</span></span>  
  
         <span data-ttu-id="7f9fc-143">**%ProgramFiles(x86)%\Microsoft BizTalk Server 2010\bins32\Schema\Restore**</span><span class="sxs-lookup"><span data-stu-id="7f9fc-143">**%ProgramFiles(x86)%\Microsoft BizTalk Server 2010\bins32\Schema\Restore**</span></span>  
  
    -   <span data-ttu-id="7f9fc-144">Si [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] est installé sur une version 32 bits de Windows Server :</span><span class="sxs-lookup"><span data-stu-id="7f9fc-144">If [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is installed on a 32-bit version of Windows Server:</span></span>  
  
         <span data-ttu-id="7f9fc-145">**%ProgramFiles%\Microsoft BizTalk Server 2010\Schema\Restore**</span><span class="sxs-lookup"><span data-stu-id="7f9fc-145">**%ProgramFiles%\Microsoft BizTalk Server 2010\Schema\Restore**</span></span>  
  
2.  <span data-ttu-id="7f9fc-146">Avec le bouton droit **SampleUpdateInfo.xml**, puis cliquez sur **modifier**.</span><span class="sxs-lookup"><span data-stu-id="7f9fc-146">Right-click **SampleUpdateInfo.xml**, and then click **Edit**.</span></span>  
  
3.  <span data-ttu-id="7f9fc-147">Ajoutez des marques de commentaire à toutes les sections de la base de données, à l'exception de BizTalkMgmtDb, OldPrimaryImportDatabase, PrimaryImportDatabase, ArchivingDatabase, AnalysisDatabase, StarSchemaDatabase et Alert.</span><span class="sxs-lookup"><span data-stu-id="7f9fc-147">Comment out all of the database sections except for the BizTalkMgmtDb, OldPrimaryImportDatabase, PrimaryImportDatabase, ArchivingDatabase, AnalysisDatabase, StarSchemaDatabase, and Alert.</span></span>  
  
4.  <span data-ttu-id="7f9fc-148">Dans le `OldPrimaryImportDatabase` section du fichier, pour le `ServerName` propriété, remplacez **SourceServer** avec le nom du serveur existant dans lequel se trouve la base de données.</span><span class="sxs-lookup"><span data-stu-id="7f9fc-148">In the `OldPrimaryImportDatabase` section of the file, for the `ServerName` property, replace **SourceServer** with the name of existing server where the database resides.</span></span>  
  
5.  <span data-ttu-id="7f9fc-149">Dans le `PrimaryImportDatabase` section du fichier, pour le `ServerName` propriété, remplacez **DestinationServer** avec le nom du serveur où vous avez déplacé la base de données d’importation principale BAM</span><span class="sxs-lookup"><span data-stu-id="7f9fc-149">In the `PrimaryImportDatabase` section of the file, for the `ServerName` property, replace **DestinationServer** with the name of the server where you have moved the BAM Primary Import database</span></span>  
  
6.  <span data-ttu-id="7f9fc-150">BizTalkMgmtDb, ArchivingDatabase, AnalysisDatabase, StarSchemaDatabase et Alert sections, définir la « SourceServer » et « Serveur de Destination » pour le nom du serveur où se trouvent les bases de données.</span><span class="sxs-lookup"><span data-stu-id="7f9fc-150">For the BizTalkMgmtDb, ArchivingDatabase, AnalysisDatabase, StarSchemaDatabase, and Alert sections, set the "SourceServer" and "Destination Server" to the name of the existing server where those databases reside.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="7f9fc-151">Utilisez des guillemets doubles pour encadrer le nom du système source et du système de destination.</span><span class="sxs-lookup"><span data-stu-id="7f9fc-151">Include the quotation marks around the name of the source and destination systems.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="7f9fc-152">Si vous avez renommé l'une des bases de données [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], vous devez également mettre à jour les noms des bases de données.</span><span class="sxs-lookup"><span data-stu-id="7f9fc-152">If you renamed any of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases, you must also update the database names as appropriate.</span></span>  
  
7.  <span data-ttu-id="7f9fc-153">Lorsque vous avez terminé la modification du fichier, enregistrez-le et fermez-le.</span><span class="sxs-lookup"><span data-stu-id="7f9fc-153">When you are finished editing the file, save it and exit.</span></span>  
  
8.  <span data-ttu-id="7f9fc-154">Cliquez sur **Démarrer**, puis sur **Exécuter**, tapez **cmd**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="7f9fc-154">Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
9. <span data-ttu-id="7f9fc-155">À l'invite de commandes, accédez au répertoire suivant :</span><span class="sxs-lookup"><span data-stu-id="7f9fc-155">At the command prompt, navigate to the following directory:</span></span>  
  
    -   <span data-ttu-id="7f9fc-156">Si [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] est installé sur une version 64 bits de Windows Server :</span><span class="sxs-lookup"><span data-stu-id="7f9fc-156">If [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is installed on a 64-bit version of Windows Server:</span></span>  
  
         <span data-ttu-id="7f9fc-157">**%ProgramFiles(x86)%\Microsoft BizTalk Server 2010\Schema\Restore**</span><span class="sxs-lookup"><span data-stu-id="7f9fc-157">**%ProgramFiles(x86)%\Microsoft BizTalk Server 2010\Schema\Restore**</span></span>  
  
    -   <span data-ttu-id="7f9fc-158">Si [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] est installé sur une version 32 bits de Windows Server :</span><span class="sxs-lookup"><span data-stu-id="7f9fc-158">If [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is installed on a 32-bit version of Windows Server:</span></span>  
  
         <span data-ttu-id="7f9fc-159">**%ProgramFiles%\Microsoft BizTalk Server 2010\Schema\Restore**</span><span class="sxs-lookup"><span data-stu-id="7f9fc-159">**%ProgramFiles%\Microsoft BizTalk Server 2010\Schema\Restore**</span></span>  
  
10. <span data-ttu-id="7f9fc-160">À l'invite de commandes, tapez :</span><span class="sxs-lookup"><span data-stu-id="7f9fc-160">At the command prompt, type:</span></span>  
  
     <span data-ttu-id="7f9fc-161">**cscript UpdateDatabase.vbs SampleUpdateInfo.xml**</span><span class="sxs-lookup"><span data-stu-id="7f9fc-161">**cscript UpdateDatabase.vbs SampleUpdateInfo.xml**</span></span>  
  
###  <a name="BKMK_Config"></a> <span data-ttu-id="7f9fc-162">Pour mettre à jour le fichier Web.config pour le portail BAM</span><span class="sxs-lookup"><span data-stu-id="7f9fc-162">To update the Web.config file for the BAM portal</span></span>  
  
1.  <span data-ttu-id="7f9fc-163">Sur un ordinateur exécutant BizTalk Server, la mise à jour les fichiers Web.config sous  **\<lecteur\>: \Program Files\Microsoft BizTalk Server 2010\BAMPortal\BAMManagementService\Web.Config**. Mettre à jour les noms de serveur et de base de données dans la section suivante dans le fichier Web.config :</span><span class="sxs-lookup"><span data-stu-id="7f9fc-163">On a computer running BizTalk Server, update the Web.config files under **\<drive\>:\Program Files\Microsoft BizTalk Server 2010\BAMPortal\BAMManagementService\Web.Config**. Update the server and database names in the following section in the Web.config:</span></span>  
  
    ```  
    <appSettings>  
      <add key="BamServer" value="<ServerName>" />  
      <add key="BamDatabase" value="<DatabaseName>" />  
    </appSettings>  
    ```  
  
2.  <span data-ttu-id="7f9fc-164">Sur un ordinateur exécutant BizTalk Server, la mise à jour les fichiers Web.config sous  **\<lecteur\>: \Program Files\Microsoft BizTalk Server 2010\BAMPortal\BAMQueryService\Web.Config**. Mettre à jour les noms de serveur et de base de données dans la section suivante dans le fichier Web.config :</span><span class="sxs-lookup"><span data-stu-id="7f9fc-164">On a computer running BizTalk Server, update the Web.config files under **\<drive\>:\Program Files\Microsoft BizTalk Server 2010\BAMPortal\BAMQueryService\Web.Config**. Update the server and database names in the following section in the Web.config:</span></span>  
  
    ```  
    <appSettings>  
      <add key="BamServer" value="<ServerName>" />  
      <add key="BamDatabase" value="<DatabaseName>" />  
      <add key="MaxResultRows" value="2000" />  
    </appSettings>  
    ```  
  
3.  <span data-ttu-id="7f9fc-165">Enregistrez et fermez les fichiers.</span><span class="sxs-lookup"><span data-stu-id="7f9fc-165">Save and close the files.</span></span>  
  
###  <a name="BKMK_UpdateExcel"></a> <span data-ttu-id="7f9fc-166">Pour mettre à jour la référence dans les fichiers de données actives d’analyse BAM, Microsoft Excel</span><span class="sxs-lookup"><span data-stu-id="7f9fc-166">To update reference in BAM Livedata Microsoft Excel files</span></span>  
  
1.  <span data-ttu-id="7f9fc-167">Ouvrez le fichier Excel de données actives.</span><span class="sxs-lookup"><span data-stu-id="7f9fc-167">Open the Excel live data file.</span></span> <span data-ttu-id="7f9fc-168">Le nom de fichier se termine par _LiveData.xls.</span><span class="sxs-lookup"><span data-stu-id="7f9fc-168">The file name ends with _LiveData.xls.</span></span>  
  
2.  <span data-ttu-id="7f9fc-169">Sur le **BAM** menu, cliquez sur **connexion DB BAM**.</span><span class="sxs-lookup"><span data-stu-id="7f9fc-169">On the **BAM** menu, click **BAM DB Connection**.</span></span>  
  
3.  <span data-ttu-id="7f9fc-170">Dans le **sélectionner la base de données BAM** boîte de dialogue, entrez le [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] ordinateur et le BAMPrimaryImport de base de données, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="7f9fc-170">In the **Select BAM Database** dialog box, enter the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] computer and the BAMPrimaryImport database, and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="7f9fc-171">Sur le **fichier** menu, cliquez sur **fermer et retourner à Microsoft Excel**.</span><span class="sxs-lookup"><span data-stu-id="7f9fc-171">On the **File** menu, click **Close and Return to Microsoft Excel**.</span></span>  
  
5.  <span data-ttu-id="7f9fc-172">Dans le menu **Fichier** , cliquez sur **Enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="7f9fc-172">On the **File** menu, click **Save**.</span></span>  
  
###  <a name="BKMK_UpdatePckg"></a> <span data-ttu-id="7f9fc-173">Pour mettre à jour les noms de serveur et base de données dans tous les packages BAM SSIS</span><span class="sxs-lookup"><span data-stu-id="7f9fc-173">To update server and database names in all BAM SSIS packages</span></span>  
  
1.  <span data-ttu-id="7f9fc-174">Mettre à jour les noms de serveur et de base de données dans tous les lots analyse BAM SSIS qui sont précédés de « BAM_AN_ » ou « BAM_DM_ ».</span><span class="sxs-lookup"><span data-stu-id="7f9fc-174">Update the server and database names in all BAM analysis SSIS packages, which are prefixed with "BAM_AN_" or "BAM_DM_".</span></span> <span data-ttu-id="7f9fc-175">Pour ce faire, cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur **Microsoft SQL Server 2008 R2** ou **Microsoft SQL Server 2008 SP1**, puis cliquez sur **SQL Server Business Intelligence Development Studio**.</span><span class="sxs-lookup"><span data-stu-id="7f9fc-175">To do so, click **Start**, click **All Programs**, click **Microsoft SQL Server 2008 R2** or **Microsoft SQL Server 2008 SP1**, and then click **SQL Server Business Intelligence Development Studio**.</span></span>  
  
2.  <span data-ttu-id="7f9fc-176">Créez un projet dans SQL Server Business Intelligence Development Studio.</span><span class="sxs-lookup"><span data-stu-id="7f9fc-176">In SQL Server Business Intelligence Development Studio, create a new project.</span></span> <span data-ttu-id="7f9fc-177">Cliquez sur **fichier**, cliquez sur **nouveau**, puis cliquez sur **projet**.</span><span class="sxs-lookup"><span data-stu-id="7f9fc-177">Click **File**, click **New**, and then click **Project**.</span></span>  
  
3.  <span data-ttu-id="7f9fc-178">Dans le **nouveau projet** boîte de dialogue le **Types de projets** , cliquez sur **projets Business Intelligence**.</span><span class="sxs-lookup"><span data-stu-id="7f9fc-178">In the **New Project** dialog box, in the **Project Types** box, click **Business Intelligence Projects**.</span></span> <span data-ttu-id="7f9fc-179">Dans le volet droit, dans le **modèles** , cliquez sur **projet Integration Services**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="7f9fc-179">In the right pane, in the **Templates** box, click **Integration Services Project**, and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="7f9fc-180">Dans le **projet Integration Services** avec le bouton droit de la boîte de dialogue Explorateur de solutions, **Packages SSIS**, puis cliquez sur **ajouter un Package existant**.</span><span class="sxs-lookup"><span data-stu-id="7f9fc-180">In the **Integration Services Project** dialog box, in Solution Explorer, right-click **SSIS Packages**, and then click **Add Existing Package**.</span></span>  
  
5.  <span data-ttu-id="7f9fc-181">Dans le **ajouter la copie des packages existants** boîte de dialogue le **Server** liste déroulante, sélectionnez le serveur qui contient les packages BAM_AN_ * et BAM_DM_ *.</span><span class="sxs-lookup"><span data-stu-id="7f9fc-181">In the **Add Copy of Existing Package** dialog box, in the **Server** drop-down list box, select the server that contains the BAM_AN_* and BAM_DM_* packages.</span></span>  
  
6.  <span data-ttu-id="7f9fc-182">Dans **chemin d’accès du Package**, cliquez sur le bouton de sélection.</span><span class="sxs-lookup"><span data-stu-id="7f9fc-182">In **Package Path**, click the ellipses button.</span></span>  
  
7.  <span data-ttu-id="7f9fc-183">Dans le **Package SSIS** boîte de dialogue, sélectionnez le package que vous souhaitez mettre à jour, cliquez sur **OK**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="7f9fc-183">In the **SSIS Package** dialog box, select the package you want to update, click **OK**, and then click **OK**.</span></span>  
  
     <span data-ttu-id="7f9fc-184">À présent, le package s'affiche dans l'Explorateur de solutions.</span><span class="sxs-lookup"><span data-stu-id="7f9fc-184">The package is now listed in Solution Explorer.</span></span>  
  
8.  <span data-ttu-id="7f9fc-185">Dans l’Explorateur de solutions, double-cliquez sur le package que vous avez ajouté à l’étape précédente.</span><span class="sxs-lookup"><span data-stu-id="7f9fc-185">In Solution Explorer, double-click the package you added in the previous step.</span></span> <span data-ttu-id="7f9fc-186">Dans **gestionnaires de connexions** onglet (disponible dans la moitié inférieure de l’écran), double-cliquez sur le nombre de sources de données 1 (base de données BAMPrimaryImport).</span><span class="sxs-lookup"><span data-stu-id="7f9fc-186">In **Connection Managers** tab (available towards the lower half of the screen), double-click data source number 1 (BAMPrimaryImport database).</span></span>  
  
9. <span data-ttu-id="7f9fc-187">Dans le **Gestionnaire de connexions** boîte de dialogue le **nom du serveur** zone, entrez le nom du serveur, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="7f9fc-187">In the **Connection Manager** dialog box, in the **Server name** box, enter the name of the server, and then click **OK**.</span></span>  
  
10. <span data-ttu-id="7f9fc-188">Cliquez sur le **Explorateur de Package** onglet, double-cliquez sur le **Variables** dossier, puis mettez à jour les valeurs de la **PrimaryImportDatabase** et  **PrimaryImportServer** variables.</span><span class="sxs-lookup"><span data-stu-id="7f9fc-188">Click the **Package Explorer** tab, double-click the **Variables** folder, and then update the values for the **PrimaryImportDatabase** and **PrimaryImportServer** variables.</span></span> <span data-ttu-id="7f9fc-189">Vous devez mettre à jour les valeurs pour pointer vers le nouveau serveur et base de données.</span><span class="sxs-lookup"><span data-stu-id="7f9fc-189">You must update the values to point to the new server and database.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="7f9fc-190">Répétez l’étape 4 et 10 pour tous les packages que vous souhaitez mettre à jour.</span><span class="sxs-lookup"><span data-stu-id="7f9fc-190">Repeat step 4 through 10 for all the packages that you want to update.</span></span>  
  
11. <span data-ttu-id="7f9fc-191">Cliquez sur puis **fichier** menu, puis sur **Enregistrer tout**.</span><span class="sxs-lookup"><span data-stu-id="7f9fc-191">Click then **File** menu, and then click **Save All**.</span></span>  
  
12. <span data-ttu-id="7f9fc-192">Démarrez SQL Server Management Studio.</span><span class="sxs-lookup"><span data-stu-id="7f9fc-192">Start the SQL Server Management Studio.</span></span> <span data-ttu-id="7f9fc-193">Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur **Microsoft SQL Server 2008 R2** ou **Microsoft SQL Server 2008 SP1**, puis cliquez sur  **SQL Server Management Studio**.</span><span class="sxs-lookup"><span data-stu-id="7f9fc-193">Click **Start**, click **All Programs**, click **Microsoft SQL Server 2008 R2** or **Microsoft SQL Server 2008 SP1**, and then click **SQL Server Management Studio**.</span></span>  
  
13. <span data-ttu-id="7f9fc-194">Dans le **se connecter au serveur** boîte de dialogue, à partir de la **Server** liste de type liste déroulante, sélectionnez **Integration Services**.</span><span class="sxs-lookup"><span data-stu-id="7f9fc-194">In the **Connect to Server** dialog box, from the **Server** type drop-down list, select **Integration Services**.</span></span>  
  
14. <span data-ttu-id="7f9fc-195">Spécifiez le nom du serveur et les informations d’identification pour se connecter au serveur et cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="7f9fc-195">Specify the server name and credentials to connect to the server and click **OK**.</span></span>  
  
15. <span data-ttu-id="7f9fc-196">Dans le **l’Explorateur d’objets**, développez **Integration Services**, développez **Packages stockés**, puis cliquez sur **MSDB**.</span><span class="sxs-lookup"><span data-stu-id="7f9fc-196">In the **Object Explorer**, expand **Integration Services**, expand **Stored Packages**, and then click **MSDB**.</span></span>  
  
16. <span data-ttu-id="7f9fc-197">Dans le **détails de l’Explorateur d’objets** onglet, cliquez sur le package de mise à jour précédemment, puis sur **importer un Package**.</span><span class="sxs-lookup"><span data-stu-id="7f9fc-197">In the **Object Explorer Details** tab, right-click the package that you updated earlier and then click **Import Package**.</span></span>  
  
17. <span data-ttu-id="7f9fc-198">Dans le **importer un Package** boîte de dialogue, à partir de la **emplacement du Package** la liste déroulante, sélectionnez **système de fichiers**.</span><span class="sxs-lookup"><span data-stu-id="7f9fc-198">In the **Import Package** dialog box, from the **Package location** drop-down list, select **File System**.</span></span>  
  
18. <span data-ttu-id="7f9fc-199">Dans **chemin d’accès du Package**, accédez à votre projet enregistré, sélectionnez le fichier .dtsx pour le package que vous souhaitez importer, puis cliquez sur **ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="7f9fc-199">In **Package Path**, navigate to your saved project, select the .dtsx file for the package you want to import, and then click **Open**.</span></span>  
  
19. <span data-ttu-id="7f9fc-200">Cliquez dans la zone Nom du Package pour remplir automatiquement la zone.</span><span class="sxs-lookup"><span data-stu-id="7f9fc-200">Click inside the Package Name box to automatically populate the box.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="7f9fc-201">Répétez l’étape 16 à 19 pour tous les packages que vous souhaitez mettre à jour.</span><span class="sxs-lookup"><span data-stu-id="7f9fc-201">Repeat step 16 through 19 for all the packages that you want to update.</span></span>  
  
20. <span data-ttu-id="7f9fc-202">Cliquez sur **OK**, puis cliquez sur **Oui** à remplacer.</span><span class="sxs-lookup"><span data-stu-id="7f9fc-202">Click **OK**, and then click **Yes** to overwrite.</span></span>  
  
21. <span data-ttu-id="7f9fc-203">Activez les mises à jour du cube d'analyse BAM et les lots SSIS de gestion des données.</span><span class="sxs-lookup"><span data-stu-id="7f9fc-203">Enable any BAM cube update and data maintenance SSIS packages.</span></span>  
  
###  <a name="BKMK_UpdateDSOLAP"></a> <span data-ttu-id="7f9fc-204">Pour mettre à jour les noms de serveur et base de données dans des sources de données pour tous les cubes OLAP</span><span class="sxs-lookup"><span data-stu-id="7f9fc-204">To update server and database names in data sources for all OLAP cubes</span></span>  
  
1.  <span data-ttu-id="7f9fc-205">Mettre à jour les noms de serveur et de base de données dans des sources de données pour tous les cubes OLAP.</span><span class="sxs-lookup"><span data-stu-id="7f9fc-205">Update the server and database names in data sources for all OLAP cubes.</span></span> <span data-ttu-id="7f9fc-206">Pour ce faire, cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur **Microsoft SQL Server 2008 R2** ou **Microsoft SQL Server 2008 SP1**, puis cliquez sur **SQL Server Management Studio**.</span><span class="sxs-lookup"><span data-stu-id="7f9fc-206">To do so, click **Start**, click **All Programs**, click **Microsoft SQL Server 2008 R2** or **Microsoft SQL Server 2008 SP1**, and then click **SQL Server Management Studio**.</span></span>  
  
2.  <span data-ttu-id="7f9fc-207">Dans le **se connecter au serveur** boîte de dialogue, pour le **type de serveur** liste déroulante, sélectionnez **Analysis Services**, fournissez le nom du serveur, sélectionnez une méthode d’authentification (et fournir des informations d’identification si nécessaire), puis cliquez sur **connexion**.</span><span class="sxs-lookup"><span data-stu-id="7f9fc-207">In the **Connect to Server** dialog box, for the **Server type** drop-down list select **Analysis Services**, provide the server name, select an authentication method (and provide credentials if required), and then click **Connect**.</span></span>  
  
3.  <span data-ttu-id="7f9fc-208">Dans l’Explorateur d’objets, développez **bases de données**, développez **BAMAnalysis**, développez **des Sources de données**, puis double-cliquez sur une source de données.</span><span class="sxs-lookup"><span data-stu-id="7f9fc-208">In the Object Explorer, expand **Databases**, expand **BAMAnalysis**, expand **Data Sources**, and then double-click a data source.</span></span>  
  
4.  <span data-ttu-id="7f9fc-209">Dans le **propriétés Source de données** boîte de dialogue, cliquez sur le bouton de sélection **(...)**  contre le **chaîne de connexion** propriété.</span><span class="sxs-lookup"><span data-stu-id="7f9fc-209">In the **Data Source Properties** dialog box, click the ellipsis button **(…)** against the **Connection String** property.</span></span>  
  
5.  <span data-ttu-id="7f9fc-210">Dans le **Gestionnaire de connexions** boîte de dialogue le **nom du serveur** , entrez le nom du serveur hébergeant la base de données, cliquez sur **OK**, puis cliquez sur  **OK**.</span><span class="sxs-lookup"><span data-stu-id="7f9fc-210">In the **Connection Manager** dialog box, in the **Server name** box, enter the name of the server hosting the BAMPrimaryImport database, click **OK**, and then click **OK**.</span></span>  
  
6.  <span data-ttu-id="7f9fc-211">Démarrer toutes les [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] services.</span><span class="sxs-lookup"><span data-stu-id="7f9fc-211">Start all [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] services.</span></span> <span data-ttu-id="7f9fc-212">Pour plus d’informations, consultez la rubrique [comment démarrer, arrêter, suspendre, reprendre ou redémarrer les Services BizTalk Server](http://go.microsoft.com/fwlink/?LinkId=154394) (http://go.microsoft.com/fwlink/?LinkId=154394) dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] aide.</span><span class="sxs-lookup"><span data-stu-id="7f9fc-212">For more information, see the topic [How To Start, Stop, Pause, Resume, or Restart BizTalk Server Services](http://go.microsoft.com/fwlink/?LinkId=154394) (http://go.microsoft.com/fwlink/?LinkId=154394) in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help.</span></span>  
  
7.  <span data-ttu-id="7f9fc-213">Démarrez le service IIS.</span><span class="sxs-lookup"><span data-stu-id="7f9fc-213">Start the IIS service.</span></span>  
  
8.  <span data-ttu-id="7f9fc-214">Démarrez le service de Notification des alertes BAM :</span><span class="sxs-lookup"><span data-stu-id="7f9fc-214">Start the BAM Alerts Notification service:</span></span>  
  
    1.  <span data-ttu-id="7f9fc-215">Cliquez sur **Démarrer**, puis sur **Exécuter**, tapez **cmd**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="7f9fc-215">Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
    2.  <span data-ttu-id="7f9fc-216">À l'invite de commandes, tapez :</span><span class="sxs-lookup"><span data-stu-id="7f9fc-216">At the command prompt, type:</span></span>  
  
         <span data-ttu-id="7f9fc-217">**Net start NS$ BamAlerts**</span><span class="sxs-lookup"><span data-stu-id="7f9fc-217">**Net start NS$BamAlerts**</span></span>  
  
9. <span data-ttu-id="7f9fc-218">Résoudre toutes les instances de suivi incomplètes.</span><span class="sxs-lookup"><span data-stu-id="7f9fc-218">Resolve any incomplete trace instances.</span></span>  <span data-ttu-id="7f9fc-219">Pour plus d’informations sur la résolution des instances d’activité BAM incomplètes, consultez [comment résoudre les Instances d’activité incomplètes](http://go.microsoft.com/fwlink/?LinkId=151475) (http://go.microsoft.com/fwlink/?LinkId=151475).</span><span class="sxs-lookup"><span data-stu-id="7f9fc-219">For information about resolving incomplete BAM activity instances, see [How to Resolve Incomplete Activity Instances](http://go.microsoft.com/fwlink/?LinkId=151475) (http://go.microsoft.com/fwlink/?LinkId=151475).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f9fc-220">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7f9fc-220">See Also</span></span>  
 [<span data-ttu-id="7f9fc-221">Déplacement de bases de données</span><span class="sxs-lookup"><span data-stu-id="7f9fc-221">Moving Databases</span></span>](../technical-guides/moving-databases.md)