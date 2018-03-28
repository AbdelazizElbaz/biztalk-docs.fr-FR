---
title: Comment déplacer la Database2 de schéma en étoile BAM | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a6832ac2-c8c5-4515-883e-26d125d6ace0
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d74e49cc1504547bff80bd2688383f1f6bea053c
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/28/2018
---
# <a name="how-to-move-the-bam-star-schema-database"></a><span data-ttu-id="ee984-102">Déplacement de la base de données de schémas en étoile BAM</span><span class="sxs-lookup"><span data-stu-id="ee984-102">How to Move the BAM Star Schema Database</span></span>
<span data-ttu-id="ee984-103">Cette procédure vous permet de déplacer la base de données de schémas en étoile BAM vers un autre serveur.</span><span class="sxs-lookup"><span data-stu-id="ee984-103">You can use this procedure to move the BAM Star Schema database to another server.</span></span>  <span data-ttu-id="ee984-104">À partir d’un point de vue du scénario de bout en bout, le déplacement de la base de données de schémas en étoile BAM implique deux étapes principales :</span><span class="sxs-lookup"><span data-stu-id="ee984-104">From an end-to-end scenario perspective, moving the BAM Star Schema database involves two major steps:</span></span>  
  
-   [<span data-ttu-id="ee984-105">Déplacement de la base de données de schéma en étoile BAM</span><span class="sxs-lookup"><span data-stu-id="ee984-105">Moving the BAM Star Schema Database</span></span>](../technical-guides/how-to-move-the-bam-star-schema-database2.md#BKMK_StarMoveDB)  
  
-   [<span data-ttu-id="ee984-106">Mise à jour des références à la nouvelle base de données de schéma en étoile BAM</span><span class="sxs-lookup"><span data-stu-id="ee984-106">Updating References to the New BAM Star Schema Database</span></span>](../technical-guides/how-to-move-the-bam-star-schema-database2.md#BKMK_StarUpdate)  
  
## <a name="prerequisites"></a><span data-ttu-id="ee984-107">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="ee984-107">Prerequisites</span></span>  
 <span data-ttu-id="ee984-108">Pour exécuter cette procédure, vous devez ouvrir une session à l'aide d'un compte membre du rôle serveur fixe sysadmin [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ee984-108">You must be logged on with an account that is a member of the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] sysadmin fixed server role to perform this procedure.</span></span>  
  
##  <a name="BKMK_StarMoveDB"></a> <span data-ttu-id="ee984-109">Déplacement de la base de données de schéma en étoile BAM</span><span class="sxs-lookup"><span data-stu-id="ee984-109">Moving the BAM Star Schema Database</span></span>  
 <span data-ttu-id="ee984-110">Les étapes de la procédure suivante pour déplacer la base de données de schémas en étoile BAM.</span><span class="sxs-lookup"><span data-stu-id="ee984-110">Perform the steps in the following procedure to move the BAM Star Schema database.</span></span>  
  
#### <a name="to-move-the-bam-star-schema-database"></a><span data-ttu-id="ee984-111">Pour déplacer la base de données de schémas en étoile BAM</span><span class="sxs-lookup"><span data-stu-id="ee984-111">To move the BAM Star Schema database</span></span>  
  
1.  <span data-ttu-id="ee984-112">Arrêtez toute analyse BAM cube mise à jour et les données maintenance SSIS, ou empêchez leur exécution jusqu'à ce que vous avez restauré la base de données de schémas en étoile BAM.</span><span class="sxs-lookup"><span data-stu-id="ee984-112">Stop any BAM cube update and data maintenance SSIS packages, or prevent them from running until you have restored the BAM Star Schema database.</span></span>  
  
2.  <span data-ttu-id="ee984-113">Arrêtez tous les services [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ee984-113">Stop all [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] services.</span></span> <span data-ttu-id="ee984-114">Pour plus d’informations, consultez la rubrique [comment démarrer, arrêter, suspendre, reprendre ou redémarrer les Services BizTalk Server](http://go.microsoft.com/fwlink/?LinkId=154394) (http://go.microsoft.com/fwlink/?LinkId=154394) dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] aide.</span><span class="sxs-lookup"><span data-stu-id="ee984-114">For more information, see the topic [How To Start, Stop, Pause, Resume, or Restart BizTalk Server Services](http://go.microsoft.com/fwlink/?LinkId=154394) (http://go.microsoft.com/fwlink/?LinkId=154394) in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help.</span></span>  
  
3.  <span data-ttu-id="ee984-115">Arrêtez le service IIS.</span><span class="sxs-lookup"><span data-stu-id="ee984-115">Stop the IIS service.</span></span>  
  
4.  <span data-ttu-id="ee984-116">Arrêtez le service de Notification des alertes BAM :</span><span class="sxs-lookup"><span data-stu-id="ee984-116">Stop the BAM Alerts Notification service:</span></span>  
  
    1.  <span data-ttu-id="ee984-117">Cliquez sur **Démarrer**, puis sur **Exécuter**, tapez **cmd**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="ee984-117">Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
    2.  <span data-ttu-id="ee984-118">À l'invite de commandes, tapez :</span><span class="sxs-lookup"><span data-stu-id="ee984-118">At the command prompt, type:</span></span>  
  
         <span data-ttu-id="ee984-119">**Net stop NS$ BamAlerts**</span><span class="sxs-lookup"><span data-stu-id="ee984-119">**Net stop NS$BamAlerts**</span></span>  
  
5.  <span data-ttu-id="ee984-120">Sauvegardez la base de données de schémas en étoile BAM sur l’ancien serveur.</span><span class="sxs-lookup"><span data-stu-id="ee984-120">Back up the BAM Star Schema database on the old server.</span></span> <span data-ttu-id="ee984-121">Pour obtenir des instructions sur la sauvegarde d’une base de données, suivez les instructions à [procédure : sauvegarder une base de données (SQL Server Management Studio)](http://go.microsoft.com/fwlink/?LinkId=156510) (http://go.microsoft.com/fwlink/?LinkId=156510) dans [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] la documentation en ligne sur la sauvegarde d’une base de données.</span><span class="sxs-lookup"><span data-stu-id="ee984-121">For instructions on backing up a database, follow the instructions at [How to: Back Up a Database (SQL Server Management Studio)](http://go.microsoft.com/fwlink/?LinkId=156510) (http://go.microsoft.com/fwlink/?LinkId=156510) in [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Books Online on how to back up a database.</span></span>  
  
6.  <span data-ttu-id="ee984-122">Copier la base de données de schémas en étoile BAM vers la nouvelle [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] ordinateur.</span><span class="sxs-lookup"><span data-stu-id="ee984-122">Copy the BAM Star Schema database to the new [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] computer.</span></span>  
  
7.  <span data-ttu-id="ee984-123">Restaurez la base de données de schémas en étoile BAM sur le nouveau serveur.</span><span class="sxs-lookup"><span data-stu-id="ee984-123">Restore the BAM Star Schema database on the new server.</span></span> <span data-ttu-id="ee984-124">Pour obtenir des instructions sur la restauration de la base de données, suivez les instructions à [Comment : restaurer une sauvegarde de base de données (SQL Server Management Studio)](http://go.microsoft.com/fwlink/?LinkId=156511) (http://go.microsoft.com/fwlink/?LinkId=156511) dans [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] la documentation en ligne sur la façon de restaurer une base de données.</span><span class="sxs-lookup"><span data-stu-id="ee984-124">For instructions on restoring the database, follow the instructions at [How to: Restore a Database Backup (SQL Server Management Studio)](http://go.microsoft.com/fwlink/?LinkId=156511) (http://go.microsoft.com/fwlink/?LinkId=156511) in [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Books Online on how to restore a database.</span></span>  
  
##  <a name="BKMK_StarUpdate"></a> <span data-ttu-id="ee984-125">Mise à jour des références à la nouvelle base de données de schéma en étoile BAM</span><span class="sxs-lookup"><span data-stu-id="ee984-125">Updating References to the New BAM Star Schema Database</span></span>  
 <span data-ttu-id="ee984-126">Une fois que vous avez déplacé la base de données, vous devez mettre à jour toutes les références à la nouvelle base de schéma en étoile BAM.</span><span class="sxs-lookup"><span data-stu-id="ee984-126">After you have moved the database, you must update all the references to the new BAM Star Schema Database.</span></span> <span data-ttu-id="ee984-127">Les références suivantes doivent être mises à jour :</span><span class="sxs-lookup"><span data-stu-id="ee984-127">The following references must be updated:</span></span>  
  
-   <span data-ttu-id="ee984-128">Mettre à jour la configuration BAM avec les nouveaux noms de base de données et le serveur.</span><span class="sxs-lookup"><span data-stu-id="ee984-128">Update the BAM configuration with the new database and server names.</span></span> <span data-ttu-id="ee984-129">Consultez [pour mettre à jour la configuration BAM](../technical-guides/how-to-move-the-bam-star-schema-database2.md#BKMK_StarUpdateBAMConfig).</span><span class="sxs-lookup"><span data-stu-id="ee984-129">See [To update the BAM configuration](../technical-guides/how-to-move-the-bam-star-schema-database2.md#BKMK_StarUpdateBAMConfig).</span></span>  
  
-   <span data-ttu-id="ee984-130">Mettre à jour les nouveaux noms de serveur et de base de données dans tous les packages SSIS d’analyse BAM.</span><span class="sxs-lookup"><span data-stu-id="ee984-130">Update the new server and database names in all BAM analysis SSIS packages.</span></span> <span data-ttu-id="ee984-131">Consultez [pour mettre à jour les noms de serveur et base de données dans tous les packages BAM SSIS](../technical-guides/how-to-move-the-bam-star-schema-database2.md#BKMK_StarUpdateRef).</span><span class="sxs-lookup"><span data-stu-id="ee984-131">See [To update server and database names in all BAM SSIS packages](../technical-guides/how-to-move-the-bam-star-schema-database2.md#BKMK_StarUpdateRef).</span></span>  
  
-   <span data-ttu-id="ee984-132">Mettre à jour les nouveaux noms de serveur et de base de données dans des sources de données pour tous les cubes OLAP non.</span><span class="sxs-lookup"><span data-stu-id="ee984-132">Update the new server and database names in data sources for all non-OLAP cubes.</span></span> <span data-ttu-id="ee984-133">Consultez [pour mettre à jour les noms de serveur et base de données dans des sources de données pour tous les cubes OLAP non](../technical-guides/how-to-move-the-bam-star-schema-database2.md#BKMK_UpdateDS_non_OLAP).</span><span class="sxs-lookup"><span data-stu-id="ee984-133">See [To update server and database names in data sources for all non-OLAP cubes](../technical-guides/how-to-move-the-bam-star-schema-database2.md#BKMK_UpdateDS_non_OLAP).</span></span>  
  
###  <a name="BKMK_StarUpdateBAMConfig"></a> <span data-ttu-id="ee984-134">Pour mettre à jour la configuration BAM</span><span class="sxs-lookup"><span data-stu-id="ee984-134">To update the BAM configuration</span></span>  
  
1.  <span data-ttu-id="ee984-135">Obtenez une copie du fichier .xml utilisé pour restaurer BAM :</span><span class="sxs-lookup"><span data-stu-id="ee984-135">Get a copy of the .xml file used for restoring BAM:</span></span>  
  
    1.  <span data-ttu-id="ee984-136">Cliquez sur **Démarrer**, puis sur **Exécuter**, tapez **cmd**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="ee984-136">Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
    2.  <span data-ttu-id="ee984-137">Sur un ordinateur exécutant BizTalk Server, accédez au dossier suivant :</span><span class="sxs-lookup"><span data-stu-id="ee984-137">On a computer running BizTalk Server, browse to the following folder:</span></span>  
  
        -   <span data-ttu-id="ee984-138">Si [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] est installé sur une version 64 bits de Windows Server :</span><span class="sxs-lookup"><span data-stu-id="ee984-138">If [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is installed on a 64-bit version of Windows Server:</span></span>  
  
             <span data-ttu-id="ee984-139">**% ProgramFiles% (x86) %\Microsoft BizTalk Server 2010\Tracking**</span><span class="sxs-lookup"><span data-stu-id="ee984-139">**%ProgramFiles(x86)%\Microsoft BizTalk Server 2010\Tracking**</span></span>  
  
        -   <span data-ttu-id="ee984-140">Si [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] est installé sur une version 32 bits de Windows Server :</span><span class="sxs-lookup"><span data-stu-id="ee984-140">If [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is installed on a 32-bit version of Windows Server:</span></span>  
  
             <span data-ttu-id="ee984-141">**%ProgramFiles%\Microsoft BizTalk Server 2010\Tracking**</span><span class="sxs-lookup"><span data-stu-id="ee984-141">**%ProgramFiles%\Microsoft BizTalk Server 2010\Tracking**</span></span>  
  
    3.  <span data-ttu-id="ee984-142">À l'invite de commandes, tapez :</span><span class="sxs-lookup"><span data-stu-id="ee984-142">At the command prompt, type:</span></span>  
  
         <span data-ttu-id="ee984-143">**BM.exe get-config –filename:BAMConfiguration.xml-server :\<nom_serveur\> -base de données :\<base de données\>**</span><span class="sxs-lookup"><span data-stu-id="ee984-143">**Bm.exe get-config –filename:BAMConfiguration.xml -server:\<servername\> -database:\<database\>**</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="ee984-144">Lorsque vous exécutez cette commande, remplacez le nom actuel du serveur à partir duquel obtenir les informations de configuration pour \<nom_serveur\> et remplacez-le par le nom réel de la base de données à partir duquel obtenir les informations de configuration \<base de données\>.</span><span class="sxs-lookup"><span data-stu-id="ee984-144">When running this command, substitute the actual name of the server from which to get the configuration information for \<servername\> and substitute the actual name of the database from which to get the configuration information for \<database\>.</span></span> <span data-ttu-id="ee984-145">Pour plus d’informations sur l’utilisation de l’utilitaire de gestion BAM (BM), consultez [Infrastructure de gestion des commandes](http://go.microsoft.com/fwlink/?LinkId=156516) (http://go.microsoft.com/fwlink/?LinkId=156516) dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] aide.</span><span class="sxs-lookup"><span data-stu-id="ee984-145">For more information about using the BAM Management (BM) utility, see [Infrastructure Management Commands](http://go.microsoft.com/fwlink/?LinkId=156516) (http://go.microsoft.com/fwlink/?LinkId=156516) in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help.</span></span>  
  
2.  <span data-ttu-id="ee984-146">Modifiez le fichier BAMConfiguration.xml et définissez la **nom_serveur** dans la `<DeploymentUnit Name="StarSchemaDatabase">` section pour le nouveau nom du serveur.</span><span class="sxs-lookup"><span data-stu-id="ee984-146">Edit the BAMConfiguration.xml file and change the **ServerName** in the `<DeploymentUnit Name="StarSchemaDatabase">` section to the new server name.</span></span>  
  
3.  <span data-ttu-id="ee984-147">Enregistrez le fichier BAMConfiguration.xml, puis fermez-le.</span><span class="sxs-lookup"><span data-stu-id="ee984-147">Save and close the BAMConfiguration.xml file.</span></span>  
  
4.  <span data-ttu-id="ee984-148">Cliquez sur **Démarrer**, puis sur **Exécuter**, tapez **cmd**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="ee984-148">Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="ee984-149">Sur un ordinateur exécutant BizTalk Server, accédez au dossier suivant :</span><span class="sxs-lookup"><span data-stu-id="ee984-149">On a computer running BizTalk Server, browse to the following folder:</span></span>  
  
    -   <span data-ttu-id="ee984-150">Si [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] est installé sur une version 64 bits de Windows Server :</span><span class="sxs-lookup"><span data-stu-id="ee984-150">If [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is installed on a 64-bit version of Windows Server:</span></span>  
  
         <span data-ttu-id="ee984-151">**% ProgramFiles% (x86) %\Microsoft BizTalk Server 2010\Tracking**</span><span class="sxs-lookup"><span data-stu-id="ee984-151">**%ProgramFiles(x86)%\Microsoft BizTalk Server 2010\Tracking**</span></span>  
  
    -   <span data-ttu-id="ee984-152">Si [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] est installé sur une version 32 bits de Windows Server :</span><span class="sxs-lookup"><span data-stu-id="ee984-152">If [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is installed on a 32-bit version of Windows Server:</span></span>  
  
         <span data-ttu-id="ee984-153">**%ProgramFiles%\Microsoft BizTalk Server 2010\Tracking**</span><span class="sxs-lookup"><span data-stu-id="ee984-153">**%ProgramFiles%\Microsoft BizTalk Server 2010\Tracking**</span></span>  
  
6.  <span data-ttu-id="ee984-154">À l'invite de commandes, tapez :</span><span class="sxs-lookup"><span data-stu-id="ee984-154">At the command prompt, type:</span></span>  
  
     <span data-ttu-id="ee984-155">**BM.exe update-config-FileName:BAMConfiguration.xml**</span><span class="sxs-lookup"><span data-stu-id="ee984-155">**bm.exe update-config -FileName:BAMConfiguration.xml**</span></span>  
  
###  <a name="BKMK_StarUpdateRef"></a> <span data-ttu-id="ee984-156">Pour mettre à jour les noms de serveur et base de données dans tous les packages BAM SSIS</span><span class="sxs-lookup"><span data-stu-id="ee984-156">To update server and database names in all BAM SSIS packages</span></span>  
  
1.  <span data-ttu-id="ee984-157">Mettre à jour les noms de serveur et de base de données dans tous les lots analyse BAM SSIS qui portent le préfixe « BAM_AN_ ».</span><span class="sxs-lookup"><span data-stu-id="ee984-157">Update the server and database names in all BAM analysis SSIS packages, which are prefixed with "BAM_AN_".</span></span> <span data-ttu-id="ee984-158">Pour ce faire, cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur **Microsoft SQL Server 2008 R2** ou **Microsoft SQL Server 2008 SP1**, puis cliquez sur **SQL Server Business Intelligence Development Studio**.</span><span class="sxs-lookup"><span data-stu-id="ee984-158">To do so, click **Start**, click **All Programs**, click **Microsoft SQL Server 2008 R2** or **Microsoft SQL Server 2008 SP1**, and then click **SQL Server Business Intelligence Development Studio**.</span></span>  
  
2.  <span data-ttu-id="ee984-159">Créez un projet dans SQL Server Business Intelligence Development Studio.</span><span class="sxs-lookup"><span data-stu-id="ee984-159">In SQL Server Business Intelligence Development Studio, create a new project.</span></span> <span data-ttu-id="ee984-160">Cliquez sur **fichier**, cliquez sur **nouveau**, puis cliquez sur **projet**.</span><span class="sxs-lookup"><span data-stu-id="ee984-160">Click **File**, click **New**, and then click **Project**.</span></span>  
  
3.  <span data-ttu-id="ee984-161">Dans le **nouveau projet** boîte de dialogue le **Types de projets** , cliquez sur **projets Business Intelligence**.</span><span class="sxs-lookup"><span data-stu-id="ee984-161">In the **New Project** dialog box, in the **Project Types** box, click **Business Intelligence Projects**.</span></span> <span data-ttu-id="ee984-162">Dans le volet droit, dans le **modèles** , cliquez sur **projet Integration Services**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="ee984-162">On the right pane, in the **Templates** box, click **Integration Services Project**, and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="ee984-163">Dans le **projet Integration Services** avec le bouton droit de la boîte de dialogue Explorateur de solutions, **Packages SSIS**, puis cliquez sur **ajouter un Package existant**.</span><span class="sxs-lookup"><span data-stu-id="ee984-163">In the **Integration Services Project** dialog box, in Solution Explorer, right-click **SSIS Packages**, and then click **Add Existing Package**.</span></span>  
  
5.  <span data-ttu-id="ee984-164">Dans le **ajouter la copie des packages existants** boîte de dialogue le **Server** liste déroulante, sélectionnez le serveur qui contient les packages BAM_AN_ \*.</span><span class="sxs-lookup"><span data-stu-id="ee984-164">In the **Add Copy of Existing Package** dialog box, in the **Server** drop-down list box, select the server that contains the BAM_AN_\* packages.</span></span>  
  
6.  <span data-ttu-id="ee984-165">Dans **chemin d’accès du Package**, cliquez sur le bouton de sélection.</span><span class="sxs-lookup"><span data-stu-id="ee984-165">In **Package Path**, click the ellipses button.</span></span>  
  
7.  <span data-ttu-id="ee984-166">Dans le **Package SSIS** boîte de dialogue, sélectionnez le package que vous souhaitez mettre à jour, cliquez sur **OK**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="ee984-166">In the **SSIS Package** dialog box, select the package you want to update, click **OK**, and then click **OK**.</span></span>  
  
     <span data-ttu-id="ee984-167">À présent, le package s'affiche dans l'Explorateur de solutions.</span><span class="sxs-lookup"><span data-stu-id="ee984-167">The package is now listed in Solution Explorer.</span></span>  
  
8.  <span data-ttu-id="ee984-168">Dans l’Explorateur de solutions, double-cliquez sur le package que vous avez ajouté à l’étape précédente.</span><span class="sxs-lookup"><span data-stu-id="ee984-168">In Solution Explorer, double-click the package you added in the previous step.</span></span> <span data-ttu-id="ee984-169">Dans **gestionnaires de connexions** onglet (disponible dans la moitié inférieure de l’écran), double-cliquez sur le nombre de sources de données 2 (base de données BAMStarSchema).</span><span class="sxs-lookup"><span data-stu-id="ee984-169">In **Connection Managers** tab (available towards the lower half of the screen), double-click data source number 2 (BAMStarSchema database).</span></span>  
  
9. <span data-ttu-id="ee984-170">Dans le **Gestionnaire de connexions** boîte de dialogue le **nom du serveur** zone, entrez le nom du serveur, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="ee984-170">In the **Connection Manager** dialog box, in the **Server name** box, enter the name of the server, and then click **OK**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ee984-171">Répétez cette opération pour le numéro de source de données 3 (base de données MSDB).</span><span class="sxs-lookup"><span data-stu-id="ee984-171">Repeat this for data source number 3 (MSDB database).</span></span>  
  
10. <span data-ttu-id="ee984-172">Dans le **gestionnaires de connexions** onglet, double-cliquez sur le nombre de sources de données 4 (base de données BAMAnalysis).</span><span class="sxs-lookup"><span data-stu-id="ee984-172">In the **Connection Managers** tab, double-click data source number 4 (BAMAnalysis database).</span></span> <span data-ttu-id="ee984-173">Dans le **ajouter le Gestionnaire de connexions Analysis Services** boîte de dialogue, cliquez sur **modifier**.</span><span class="sxs-lookup"><span data-stu-id="ee984-173">In the **Add Analysis Services Connection Manager** dialog box, click **Edit**.</span></span>  
  
11. <span data-ttu-id="ee984-174">Dans le **Gestionnaire de connexions** boîte de dialogue le **nom du serveur** , entrez le nom du serveur, cliquez sur **OK**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="ee984-174">In the **Connection Manager** dialog box, in the **Server name** box, enter the name of the server, click **OK**, and then click **OK**.</span></span>  
  
12. <span data-ttu-id="ee984-175">Cliquez sur le **Explorateur de Package** onglet, double-cliquez sur le **Variables** dossier, puis mettez à jour les valeurs de la **AnalysisDatabase**, **AnalysisServer** , **PrimaryImportDatabase**, **PrimaryImportServer**, **StarSchemaDatabase**, et **StarSchemaServer** variables.</span><span class="sxs-lookup"><span data-stu-id="ee984-175">Click the **Package Explorer** tab, double-click the **Variables** folder, and then update the values for the **AnalysisDatabase**, **AnalysisServer**, **PrimaryImportDatabase**, **PrimaryImportServer**, **StarSchemaDatabase**, and **StarSchemaServer** variables.</span></span> <span data-ttu-id="ee984-176">Vous devez mettre à jour les valeurs pour pointer vers le nouveau serveur et base de données.</span><span class="sxs-lookup"><span data-stu-id="ee984-176">You must update the values to point to the new server and database.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ee984-177">Répétez l’étape 4 et 12 pour tous les packages que vous souhaitez mettre à jour.</span><span class="sxs-lookup"><span data-stu-id="ee984-177">Repeat step 4 through 12 for all the packages that you want to update.</span></span>  
  
13. <span data-ttu-id="ee984-178">Cliquez sur puis **fichier** menu, puis sur **Enregistrer tout**.</span><span class="sxs-lookup"><span data-stu-id="ee984-178">Click then **File** menu, and then click **Save All**.</span></span>  
  
14. <span data-ttu-id="ee984-179">Démarrez SQL Server Management Studio.</span><span class="sxs-lookup"><span data-stu-id="ee984-179">Start the SQL Server Management Studio.</span></span> <span data-ttu-id="ee984-180">Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur **Microsoft SQL Server 2008 R2** ou **Microsoft SQL Server 2008 SP1**, puis cliquez sur  **SQL Server Management Studio**.</span><span class="sxs-lookup"><span data-stu-id="ee984-180">Click **Start**, click **All Programs**, click **Microsoft SQL Server 2008 R2** or **Microsoft SQL Server 2008 SP1**, and then click **SQL Server Management Studio**.</span></span>  
  
15. <span data-ttu-id="ee984-181">Dans le **se connecter au serveur** boîte de dialogue, à partir de la **Server** liste de type liste déroulante, sélectionnez **Integration Services**.</span><span class="sxs-lookup"><span data-stu-id="ee984-181">In the **Connect to Server** dialog box, from the **Server** type drop-down list, select **Integration Services**.</span></span>  
  
16. <span data-ttu-id="ee984-182">Spécifiez le nom du serveur et les informations d’identification pour se connecter au serveur et cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="ee984-182">Specify the server name and credentials to connect to the server and click **OK**.</span></span>  
  
17. <span data-ttu-id="ee984-183">Dans le **l’Explorateur d’objets**, développez **Integration Services**, développez **Packages stockés**, puis cliquez sur **MSDB**.</span><span class="sxs-lookup"><span data-stu-id="ee984-183">In the **Object Explorer**, expand **Integration Services**, expand **Stored Packages**, and then click **MSDB**.</span></span>  
  
18. <span data-ttu-id="ee984-184">Dans le **détails de l’Explorateur d’objets** onglet, cliquez sur le package de mise à jour précédemment, puis sur **importer un Package**.</span><span class="sxs-lookup"><span data-stu-id="ee984-184">In the **Object Explorer Details** tab, right-click the package that you updated earlier and then click **Import Package**.</span></span>  
  
19. <span data-ttu-id="ee984-185">Dans le **importer un Package** boîte de dialogue, à partir de la **emplacement du Package** la liste déroulante, sélectionnez **système de fichiers**.</span><span class="sxs-lookup"><span data-stu-id="ee984-185">In the **Import Package** dialog box, from the **Package location** drop-down list, select **File System**.</span></span>  
  
20. <span data-ttu-id="ee984-186">Dans **chemin d’accès du Package**, accédez à votre projet enregistré, sélectionnez le fichier .dtsx pour le package que vous souhaitez importer, puis cliquez sur **ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="ee984-186">In **Package Path**, navigate to your saved project, select the .dtsx file for the package you want to import, and then click **Open**.</span></span>  
  
21. <span data-ttu-id="ee984-187">Cliquez dans la zone Nom du Package pour remplir automatiquement la zone.</span><span class="sxs-lookup"><span data-stu-id="ee984-187">Click inside the Package Name box to automatically populate the box.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ee984-188">Répétez l’étape 18 à 21 pour tous les packages que vous souhaitez mettre à jour.</span><span class="sxs-lookup"><span data-stu-id="ee984-188">Repeat step 18 through 21 for all the packages that you want to update.</span></span>  
  
22. <span data-ttu-id="ee984-189">Cliquez sur **OK**, puis cliquez sur **Oui** à remplacer.</span><span class="sxs-lookup"><span data-stu-id="ee984-189">Click **OK**, and then click **Yes** to overwrite.</span></span>  
  
23. <span data-ttu-id="ee984-190">Activez les mises à jour du cube d'analyse BAM et les lots SSIS de gestion des données.</span><span class="sxs-lookup"><span data-stu-id="ee984-190">Enable any BAM cube update and data maintenance SSIS packages.</span></span>  
  
###  <a name="BKMK_UpdateDS_non_OLAP"></a> <span data-ttu-id="ee984-191">Pour mettre à jour les noms de serveur et base de données dans des sources de données pour tous les cubes OLAP non</span><span class="sxs-lookup"><span data-stu-id="ee984-191">To update server and database names in data sources for all non-OLAP cubes</span></span>  
  
1.  <span data-ttu-id="ee984-192">Mettre à jour les noms de serveur et de base de données dans des sources de données pour tous les cubes non OLAP.</span><span class="sxs-lookup"><span data-stu-id="ee984-192">Update the server and database names in data sources for all non-OLAP cubes.</span></span> <span data-ttu-id="ee984-193">Pour ce faire, cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur **Microsoft SQL Server 2008 R2** ou **Microsoft SQL Server 2008 SP1**, puis cliquez sur **SQL Server Management Studio**.</span><span class="sxs-lookup"><span data-stu-id="ee984-193">To do so, click **Start**, click **All Programs**, click **Microsoft SQL Server 2008 R2** or **Microsoft SQL Server 2008 SP1**, and then click **SQL Server Management Studio**.</span></span>  
  
2.  <span data-ttu-id="ee984-194">Dans le **se connecter au serveur** boîte de dialogue, pour le **type de serveur** liste déroulante, sélectionnez **Analysis Services**, fournissez le nom du serveur, sélectionnez une méthode d’authentification (et fournir des informations d’identification si nécessaire), puis cliquez sur **connexion**.</span><span class="sxs-lookup"><span data-stu-id="ee984-194">In the **Connect to Server** dialog box, for the **Server type** drop-down list select **Analysis Services**, provide the server name, select an authentication method (and provide credentials if required), and then click **Connect**.</span></span>  
  
3.  <span data-ttu-id="ee984-195">Dans l’Explorateur d’objets, développez **bases de données**, développez **BAMAnalysis**, développez **des Sources de données**, puis double-cliquez sur une source de données.</span><span class="sxs-lookup"><span data-stu-id="ee984-195">In the Object Explorer, expand **Databases**, expand **BAMAnalysis**, expand **Data Sources**, and then double-click a data source.</span></span>  
  
4.  <span data-ttu-id="ee984-196">Dans le **propriétés Source de données** boîte de dialogue, cliquez sur le bouton de sélection **(...)**  contre le **chaîne de connexion** propriété.</span><span class="sxs-lookup"><span data-stu-id="ee984-196">In the **Data Source Properties** dialog box, click the ellipsis button **(…)** against the **Connection String** property.</span></span>  
  
5.  <span data-ttu-id="ee984-197">Dans le **Gestionnaire de connexions** boîte de dialogue le **nom du serveur** , entrez le nom du serveur hébergeant la base de données BAMStarSchema, cliquez sur **OK**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="ee984-197">In the **Connection Manager** dialog box, in the **Server name** box, enter the name of the server hosting the BAMStarSchema database, click **OK**, and then click **OK**.</span></span>  
  
6.  <span data-ttu-id="ee984-198">Démarrer toutes les [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] services.</span><span class="sxs-lookup"><span data-stu-id="ee984-198">Start all [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] services.</span></span> <span data-ttu-id="ee984-199">Pour plus d’informations, consultez la rubrique [comment démarrer, arrêter, suspendre, reprendre ou redémarrer les Services BizTalk Server](http://go.microsoft.com/fwlink/?LinkId=154394) (http://go.microsoft.com/fwlink/?LinkId=154394) dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] aide.</span><span class="sxs-lookup"><span data-stu-id="ee984-199">For more information, see the topic [How To Start, Stop, Pause, Resume, or Restart BizTalk Server Services](http://go.microsoft.com/fwlink/?LinkId=154394) (http://go.microsoft.com/fwlink/?LinkId=154394) in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help.</span></span>  
  
7.  <span data-ttu-id="ee984-200">Démarrez le service IIS.</span><span class="sxs-lookup"><span data-stu-id="ee984-200">Start the IIS service.</span></span>  
  
8.  <span data-ttu-id="ee984-201">Démarrez le service de Notification des alertes BAM :</span><span class="sxs-lookup"><span data-stu-id="ee984-201">Start the BAM Alerts Notification service:</span></span>  
  
    1.  <span data-ttu-id="ee984-202">Cliquez sur **Démarrer**, puis sur **Exécuter**, tapez **cmd**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="ee984-202">Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
    2.  <span data-ttu-id="ee984-203">À l'invite de commandes, tapez :</span><span class="sxs-lookup"><span data-stu-id="ee984-203">At the command prompt, type:</span></span>  
  
         <span data-ttu-id="ee984-204">**Net start NS$ BamAlerts**</span><span class="sxs-lookup"><span data-stu-id="ee984-204">**Net start NS$BamAlerts**</span></span>  
  
9. <span data-ttu-id="ee984-205">Résoudre toutes les instances de suivi incomplètes.</span><span class="sxs-lookup"><span data-stu-id="ee984-205">Resolve any incomplete trace instances.</span></span>  <span data-ttu-id="ee984-206">Pour plus d’informations sur la résolution des instances d’activité BAM incomplètes, consultez [comment résoudre les Instances d’activité incomplètes](http://go.microsoft.com/fwlink/?LinkId=151475) (http://go.microsoft.com/fwlink/?LinkId=151475).</span><span class="sxs-lookup"><span data-stu-id="ee984-206">For information about resolving incomplete BAM activity instances, see [How to Resolve Incomplete Activity Instances](http://go.microsoft.com/fwlink/?LinkId=151475) (http://go.microsoft.com/fwlink/?LinkId=151475).</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="ee984-207">Comme une bonne pratique, vous devez également déplacer les packages SSIS BAM_AN_ \* pour le serveur qui héberge la base de données BAMStarSchema.</span><span class="sxs-lookup"><span data-stu-id="ee984-207">As a good practice, you should also move the BAM_AN_\* SSIS packages to the server hosting the BAMStarSchema database.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee984-208">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ee984-208">See Also</span></span>  
 [<span data-ttu-id="ee984-209">Déplacement de bases de données</span><span class="sxs-lookup"><span data-stu-id="ee984-209">Moving Databases</span></span>](../technical-guides/moving-databases.md)