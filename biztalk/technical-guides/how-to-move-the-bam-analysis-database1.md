---
title: "Comment déplacer la Database1 d’analyse BAM | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d8094153-072b-427a-b3a0-7310a37cf584
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 971a9c69e98bf894d41d5e23d0e852162c2ab139
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-move-the-bam-analysis-database"></a><span data-ttu-id="07347-102">Déplacement de la base de données d'analyse BAM</span><span class="sxs-lookup"><span data-stu-id="07347-102">How to Move the BAM Analysis Database</span></span>
<span data-ttu-id="07347-103">Cette procédure vous permet de déplacer la base de données d'analyse BAM vers un autre serveur.</span><span class="sxs-lookup"><span data-stu-id="07347-103">You can use this procedure to move the BAM Analysis database to another server.</span></span>  <span data-ttu-id="07347-104">À partir d’un point de vue du scénario de bout en bout, le déplacement de la base de données analyse BAM comprend deux étapes principales :</span><span class="sxs-lookup"><span data-stu-id="07347-104">From an end-to-end scenario perspective, moving the BAM Analysis database involves two major steps:</span></span>  
  
-   [<span data-ttu-id="07347-105">Déplacement de la base de données analyse BAM</span><span class="sxs-lookup"><span data-stu-id="07347-105">Moving the BAM Analysis Database</span></span>](../technical-guides/how-to-move-the-bam-analysis-database1.md#BKMK_AnalyMoveDB)  
  
-   [<span data-ttu-id="07347-106">Mise à jour des références à la nouvelle base de données analyse BAM</span><span class="sxs-lookup"><span data-stu-id="07347-106">Updating References to the New BAM Analysis Database</span></span>](../technical-guides/how-to-move-the-bam-analysis-database1.md#BKMK_AnalyUpdate)  
  
## <a name="prerequisites"></a><span data-ttu-id="07347-107">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="07347-107">Prerequisites</span></span>  
 <span data-ttu-id="07347-108">Pour exécuter cette procédure, vous devez ouvrir une session à l'aide d'un compte membre du rôle serveur fixe sysadmin [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="07347-108">You must be logged on with an account that is a member of the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] sysadmin fixed server role to perform this procedure.</span></span>  
  
##  <span data-ttu-id="07347-109"><a name="BKMK_AnalyMoveDB"></a>Déplacement de la base de données analyse BAM</span><span class="sxs-lookup"><span data-stu-id="07347-109"><a name="BKMK_AnalyMoveDB"></a> Moving the BAM Analysis Database</span></span>  
 <span data-ttu-id="07347-110">Effectuez les opérations dans la procédure suivante pour déplacer la base de données analyse BAM.</span><span class="sxs-lookup"><span data-stu-id="07347-110">Perform the steps in the following procedure to move the BAM Analysis database.</span></span>  
  
#### <a name="to-move-the-bam-analysis-database"></a><span data-ttu-id="07347-111">Pour déplacer la base de données d'analyse BAM</span><span class="sxs-lookup"><span data-stu-id="07347-111">To move the BAM Analysis database</span></span>  
  
1.  <span data-ttu-id="07347-112">Arrêtez toute analyse BAM cube mise à jour et les données de gestion SSIS, ou empêchez leur exécution jusqu'à ce que vous avez restauré la base de données analyse BAM.</span><span class="sxs-lookup"><span data-stu-id="07347-112">Stop any BAM cube update and data maintenance SSIS packages, or prevent them from running until you have restored the BAM Analysis database.</span></span>  
  
2.  <span data-ttu-id="07347-113">Arrêtez tous les services [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="07347-113">Stop all [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] services.</span></span> <span data-ttu-id="07347-114">Pour plus d’informations, consultez la rubrique [comment démarrer, arrêter, suspendre, reprendre ou redémarrer les Services BizTalk Server](http://go.microsoft.com/fwlink/?LinkId=154394) (http://go.microsoft.com/fwlink/?LinkId=154394) dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] aide.</span><span class="sxs-lookup"><span data-stu-id="07347-114">For more information, see the topic [How To Start, Stop, Pause, Resume, or Restart BizTalk Server Services](http://go.microsoft.com/fwlink/?LinkId=154394) (http://go.microsoft.com/fwlink/?LinkId=154394) in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help.</span></span>  
  
3.  <span data-ttu-id="07347-115">Arrêtez le service IIS.</span><span class="sxs-lookup"><span data-stu-id="07347-115">Stop the IIS service.</span></span>  
  
4.  <span data-ttu-id="07347-116">Arrêtez le service de Notification des alertes BAM :</span><span class="sxs-lookup"><span data-stu-id="07347-116">Stop the BAM Alerts Notification service:</span></span>  
  
    1.  <span data-ttu-id="07347-117">Cliquez sur **Démarrer**, puis sur **Exécuter**, tapez **cmd**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="07347-117">Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
    2.  <span data-ttu-id="07347-118">À l'invite de commandes, tapez :</span><span class="sxs-lookup"><span data-stu-id="07347-118">At the command prompt, type:</span></span>  
  
         <span data-ttu-id="07347-119">**Net stop NS$ BamAlerts**</span><span class="sxs-lookup"><span data-stu-id="07347-119">**Net stop NS$BamAlerts**</span></span>  
  
5.  <span data-ttu-id="07347-120">Sauvegardez la base de données analyse BAM sur l’ancien serveur.</span><span class="sxs-lookup"><span data-stu-id="07347-120">Back up the BAM Analysis database on the old server.</span></span> <span data-ttu-id="07347-121">Pour obtenir des instructions sur la sauvegarde d’une base de données, suivez les instructions à [procédure : sauvegarder une base de données (SQL Server Management Studio)](http://go.microsoft.com/fwlink/?LinkId=156510) (http://go.microsoft.com/fwlink/?LinkId=156510) dans [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] la documentation en ligne sur la sauvegarde d’une base de données.</span><span class="sxs-lookup"><span data-stu-id="07347-121">For instructions on backing up a database, follow the instructions at [How to: Back Up a Database (SQL Server Management Studio)](http://go.microsoft.com/fwlink/?LinkId=156510) (http://go.microsoft.com/fwlink/?LinkId=156510) in [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Books Online on how to back up a database.</span></span>  
  
6.  <span data-ttu-id="07347-122">Copier la base de données analyse BAM vers la nouvelle [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] ordinateur.</span><span class="sxs-lookup"><span data-stu-id="07347-122">Copy the BAM Analysis database to the new [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] computer.</span></span>  
  
7.  <span data-ttu-id="07347-123">Restaurez la base de données analyse BAM sur le nouveau serveur.</span><span class="sxs-lookup"><span data-stu-id="07347-123">Restore the BAM Analysis database on the new server.</span></span> <span data-ttu-id="07347-124">Pour obtenir des instructions sur la restauration de la base de données, suivez les instructions à [Comment : restaurer une sauvegarde de base de données (SQL Server Management Studio)](http://go.microsoft.com/fwlink/?LinkId=156511) (http://go.microsoft.com/fwlink/?LinkId=156511) dans [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] la documentation en ligne sur la façon de restaurer une base de données.</span><span class="sxs-lookup"><span data-stu-id="07347-124">For instructions on restoring the database, follow the instructions at [How to: Restore a Database Backup (SQL Server Management Studio)](http://go.microsoft.com/fwlink/?LinkId=156511) (http://go.microsoft.com/fwlink/?LinkId=156511) in [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Books Online on how to restore a database.</span></span>  
  
##  <span data-ttu-id="07347-125"><a name="BKMK_AnalyUpdate"></a>Mise à jour des références à la nouvelle base de données analyse BAM</span><span class="sxs-lookup"><span data-stu-id="07347-125"><a name="BKMK_AnalyUpdate"></a> Updating References to the New BAM Analysis Database</span></span>  
 <span data-ttu-id="07347-126">Une fois que vous avez déplacé la base de données, vous devez mettre à jour toutes les références à la nouvelle base de données analyse BAM.</span><span class="sxs-lookup"><span data-stu-id="07347-126">After you have moved the database, you must update all the references to the new BAM Analysis Database.</span></span> <span data-ttu-id="07347-127">Les références suivantes doivent être mises à jour :</span><span class="sxs-lookup"><span data-stu-id="07347-127">The following references must be updated:</span></span>  
  
-   <span data-ttu-id="07347-128">Mettre à jour la configuration BAM avec les nouveaux noms de base de données et le serveur.</span><span class="sxs-lookup"><span data-stu-id="07347-128">Update the BAM configuration with the new database and server names.</span></span> <span data-ttu-id="07347-129">Consultez [pour mettre à jour la configuration BAM](../technical-guides/how-to-move-the-bam-analysis-database1.md#BKMK_AnalyUpdateBAMConfig).</span><span class="sxs-lookup"><span data-stu-id="07347-129">See [To update the BAM configuration](../technical-guides/how-to-move-the-bam-analysis-database1.md#BKMK_AnalyUpdateBAMConfig).</span></span>  
  
-   <span data-ttu-id="07347-130">Mettre à jour les nouveaux noms de serveur et de base de données dans tous les packages SSIS d’analyse BAM.</span><span class="sxs-lookup"><span data-stu-id="07347-130">Update the new server and database names in all BAM analysis SSIS packages.</span></span> <span data-ttu-id="07347-131">Consultez [pour mettre à jour les noms de serveur et base de données dans tous les packages BAM SSIS](../technical-guides/how-to-move-the-bam-analysis-database1.md#BKMK_AnalyUpdateSSIS).</span><span class="sxs-lookup"><span data-stu-id="07347-131">See [To update server and database names in all BAM SSIS packages](../technical-guides/how-to-move-the-bam-analysis-database1.md#BKMK_AnalyUpdateSSIS).</span></span>  
  
###  <span data-ttu-id="07347-132"><a name="BKMK_AnalyUpdateBAMConfig"></a>Pour mettre à jour la configuration BAM</span><span class="sxs-lookup"><span data-stu-id="07347-132"><a name="BKMK_AnalyUpdateBAMConfig"></a> To update the BAM configuration</span></span>  
  
1.  <span data-ttu-id="07347-133">Obtenez une copie du fichier .xml utilisé pour restaurer BAM :</span><span class="sxs-lookup"><span data-stu-id="07347-133">Get a copy of the .xml file used for restoring BAM:</span></span>  
  
    1.  <span data-ttu-id="07347-134">Cliquez sur **Démarrer**, puis sur **Exécuter**, tapez **cmd**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="07347-134">Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
    2.  <span data-ttu-id="07347-135">Sur un ordinateur exécutant [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)], accédez au dossier suivant :</span><span class="sxs-lookup"><span data-stu-id="07347-135">On a computer running [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)], browse to the following folder:</span></span>  
  
        -   <span data-ttu-id="07347-136">Si [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] est installé sur une version 64 bits de Windows Server :</span><span class="sxs-lookup"><span data-stu-id="07347-136">If [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is installed on a 64-bit version of Windows Server:</span></span>  
  
             <span data-ttu-id="07347-137">**% ProgramFiles% (x86) %\Microsoft BizTalk Server 2010\Tracking**</span><span class="sxs-lookup"><span data-stu-id="07347-137">**%ProgramFiles(x86)%\Microsoft BizTalk Server 2010\Tracking**</span></span>  
  
        -   <span data-ttu-id="07347-138">Si [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] est installé sur une version 32 bits de Windows Server :</span><span class="sxs-lookup"><span data-stu-id="07347-138">If [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is installed on a 32-bit version of Windows Server:</span></span>  
  
             <span data-ttu-id="07347-139">**%ProgramFiles%\Microsoft BizTalk Server 2010\Tracking**</span><span class="sxs-lookup"><span data-stu-id="07347-139">**%ProgramFiles%\Microsoft BizTalk Server 2010\Tracking**</span></span>  
  
    3.  <span data-ttu-id="07347-140">À l'invite de commandes, tapez :</span><span class="sxs-lookup"><span data-stu-id="07347-140">At the command prompt, type:</span></span>  
  
         <span data-ttu-id="07347-141">**BM.exe get-config –filename:BAMConfiguration.xml-server :\<nom_serveur >-base de données :\<base de données >**</span><span class="sxs-lookup"><span data-stu-id="07347-141">**Bm.exe get-config –filename:BAMConfiguration.xml -server:\<servername> -database:\<database>**</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="07347-142">Lorsque vous exécutez cette commande, remplacez le nom actuel du serveur à partir duquel obtenir les informations de configuration pour \<nom_serveur > et remplacez le nom actuel de la base de données à partir duquel obtenir les informations de configuration pour \<base de données >.</span><span class="sxs-lookup"><span data-stu-id="07347-142">When running this command, substitute the actual name of the server from which to get the configuration information for \<servername> and substitute the actual name of the database from which to get the configuration information for \<database>.</span></span> <span data-ttu-id="07347-143">Pour plus d’informations sur l’utilisation de l’utilitaire de gestion BAM (BM), consultez [Infrastructure de gestion des commandes](http://go.microsoft.com/fwlink/?LinkId=156516) (http://go.microsoft.com/fwlink/?LinkId=156516) dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] aide.</span><span class="sxs-lookup"><span data-stu-id="07347-143">For more information about using the BAM Management (BM) utility, see [Infrastructure Management Commands](http://go.microsoft.com/fwlink/?LinkId=156516) (http://go.microsoft.com/fwlink/?LinkId=156516) in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help.</span></span>  
  
2.  <span data-ttu-id="07347-144">Modifiez le fichier BAMConfiguration.xml et définissez la **nom_serveur** dans la `<DeploymentUnit Name="AnalysisDatabase">` section pour le nouveau nom du serveur.</span><span class="sxs-lookup"><span data-stu-id="07347-144">Edit the BAMConfiguration.xml file and change the **ServerName** in the `<DeploymentUnit Name="AnalysisDatabase">` section to the new server name.</span></span>  
  
3.  <span data-ttu-id="07347-145">Enregistrez le fichier BAMConfiguration.xml, puis fermez-le.</span><span class="sxs-lookup"><span data-stu-id="07347-145">Save and close the BAMConfiguration.xml file.</span></span>  
  
4.  <span data-ttu-id="07347-146">Cliquez sur **Démarrer**, puis sur **Exécuter**, tapez **cmd**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="07347-146">Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="07347-147">Sur un ordinateur exécutant [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)], accédez au dossier suivant :</span><span class="sxs-lookup"><span data-stu-id="07347-147">On a computer running [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)], browse to the following folder:</span></span>  
  
    -   <span data-ttu-id="07347-148">Si [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] est installé sur une version 64 bits de Windows Server :</span><span class="sxs-lookup"><span data-stu-id="07347-148">If [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is installed on a 64-bit version of Windows Server:</span></span>  
  
         <span data-ttu-id="07347-149">**% ProgramFiles% (x86) %\Microsoft BizTalk Server 2010\Tracking**</span><span class="sxs-lookup"><span data-stu-id="07347-149">**%ProgramFiles(x86)%\Microsoft BizTalk Server 2010\Tracking**</span></span>  
  
    -   <span data-ttu-id="07347-150">Si [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] est installé sur une version 32 bits de Windows Server :</span><span class="sxs-lookup"><span data-stu-id="07347-150">If [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is installed on a 32-bit version of Windows Server:</span></span>  
  
         <span data-ttu-id="07347-151">**%ProgramFiles%\Microsoft BizTalk Server 2010\Tracking**</span><span class="sxs-lookup"><span data-stu-id="07347-151">**%ProgramFiles%\Microsoft BizTalk Server 2010\Tracking**</span></span>  
  
6.  <span data-ttu-id="07347-152">À l'invite de commandes, tapez :</span><span class="sxs-lookup"><span data-stu-id="07347-152">At the command prompt, type:</span></span>  
  
     <span data-ttu-id="07347-153">**BM.exe update-config-FileName:BAMConfiguration.xml**</span><span class="sxs-lookup"><span data-stu-id="07347-153">**bm.exe update-config -FileName:BAMConfiguration.xml**</span></span>  
  
###  <span data-ttu-id="07347-154"><a name="BKMK_AnalyUpdateSSIS"></a>Pour mettre à jour les noms de serveur et base de données dans tous les packages BAM SSIS</span><span class="sxs-lookup"><span data-stu-id="07347-154"><a name="BKMK_AnalyUpdateSSIS"></a> To update server and database names in all BAM SSIS packages</span></span>  
  
1.  <span data-ttu-id="07347-155">Mettre à jour les noms de serveur et de base de données dans tous les lots analyse BAM SSIS qui portent le préfixe « BAM_AN_ ».</span><span class="sxs-lookup"><span data-stu-id="07347-155">Update the server and database names in all BAM analysis SSIS packages, which are prefixed with "BAM_AN_".</span></span> <span data-ttu-id="07347-156">Pour ce faire, cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur **Microsoft SQL Server 2008 R2** ou **Microsoft SQL Server 2008 SP1**, puis cliquez sur **SQL Server Business Intelligence Development Studio**.</span><span class="sxs-lookup"><span data-stu-id="07347-156">To do so, click **Start**, click **All Programs**, click **Microsoft SQL Server 2008 R2** or **Microsoft SQL Server 2008 SP1**, and then click **SQL Server Business Intelligence Development Studio**.</span></span>  
  
2.  <span data-ttu-id="07347-157">Créez un projet dans SQL Server Business Intelligence Development Studio.</span><span class="sxs-lookup"><span data-stu-id="07347-157">In SQL Server Business Intelligence Development Studio, create a new project.</span></span> <span data-ttu-id="07347-158">Cliquez sur **fichier**, cliquez sur **nouveau**, puis cliquez sur **projet**.</span><span class="sxs-lookup"><span data-stu-id="07347-158">Click **File**, click **New**, and then click **Project**.</span></span>  
  
3.  <span data-ttu-id="07347-159">Dans le **nouveau projet** boîte de dialogue le **Types de projets** , cliquez sur **projets Business Intelligence**.</span><span class="sxs-lookup"><span data-stu-id="07347-159">In the **New Project** dialog box, in the **Project Types** box, click **Business Intelligence Projects**.</span></span> <span data-ttu-id="07347-160">Dans le volet droit, dans le **modèles** , cliquez sur **projet Integration Services**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="07347-160">On the right pane, in the **Templates** box, click **Integration Services Project**, and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="07347-161">Dans le **projet Integration Services** avec le bouton droit de la boîte de dialogue Explorateur de solutions, **Packages SSIS**, puis cliquez sur **ajouter un Package existant**.</span><span class="sxs-lookup"><span data-stu-id="07347-161">In the **Integration Services Project** dialog box, in Solution Explorer, right-click **SSIS Packages**, and then click **Add Existing Package**.</span></span>  
  
5.  <span data-ttu-id="07347-162">Dans le **ajouter la copie des packages existants** boîte de dialogue le **Server** liste déroulante, sélectionnez le serveur qui contient les packages BAM_AN_ *.</span><span class="sxs-lookup"><span data-stu-id="07347-162">In the **Add Copy of Existing Package** dialog box, in the **Server** drop-down list box, select the server that contains the BAM_AN_* packages.</span></span>  
  
6.  <span data-ttu-id="07347-163">Dans **chemin d’accès du Package**, cliquez sur le bouton de sélection.</span><span class="sxs-lookup"><span data-stu-id="07347-163">In **Package Path**, click the ellipses button.</span></span>  
  
7.  <span data-ttu-id="07347-164">Dans le **Package SSIS** boîte de dialogue, sélectionnez le package que vous souhaitez mettre à jour, cliquez sur **OK**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="07347-164">In the **SSIS Package** dialog box, select the package you want to update, click **OK**, and then click **OK**.</span></span>  
  
     <span data-ttu-id="07347-165">À présent, le package s'affiche dans l'Explorateur de solutions.</span><span class="sxs-lookup"><span data-stu-id="07347-165">The package is now listed in Solution Explorer.</span></span>  
  
8.  <span data-ttu-id="07347-166">Dans l’Explorateur de solutions, double-cliquez sur le package que vous avez ajouté à l’étape précédente.</span><span class="sxs-lookup"><span data-stu-id="07347-166">In Solution Explorer, double-click the package you added in the previous step.</span></span> <span data-ttu-id="07347-167">Dans **gestionnaires de connexions** onglet (disponible dans la moitié inférieure de l’écran), double-cliquez sur le nombre de sources de données 2 (base de données BAMArchive).</span><span class="sxs-lookup"><span data-stu-id="07347-167">In **Connection Managers** tab (available towards the lower half of the screen), double-click data source number 2 (BAMArchive database).</span></span>  
  
9. <span data-ttu-id="07347-168">Dans le **Gestionnaire de connexions** boîte de dialogue le **nom du serveur** zone, entrez le nom du serveur, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="07347-168">In the **Connection Manager** dialog box, in the **Server name** box, enter the name of the server, and then click **OK**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="07347-169">Répétez cette opération pour le numéro de source de données 3 (base de données MSDB).</span><span class="sxs-lookup"><span data-stu-id="07347-169">Repeat this for data source number 3 (MSDB database).</span></span>  
  
10. <span data-ttu-id="07347-170">Dans le **gestionnaires de connexions** onglet, double-cliquez sur le nombre de sources de données 4 (base de données BAMAnalysis).</span><span class="sxs-lookup"><span data-stu-id="07347-170">In the **Connection Managers** tab, double-click data source number 4 (BAMAnalysis database).</span></span> <span data-ttu-id="07347-171">Dans le **ajouter le Gestionnaire de connexions Analysis Services** boîte de dialogue, cliquez sur **modifier**.</span><span class="sxs-lookup"><span data-stu-id="07347-171">In the **Add Analysis Services Connection Manager** dialog box, click **Edit**.</span></span>  
  
11. <span data-ttu-id="07347-172">Dans le **Gestionnaire de connexions** boîte de dialogue le **nom du serveur** , entrez le nom du serveur, cliquez sur **OK**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="07347-172">In the **Connection Manager** dialog box, in the **Server name** box, enter the name of the server, click **OK**, and then click **OK**.</span></span>  
  
12. <span data-ttu-id="07347-173">Cliquez sur le **Explorateur de Package** onglet, double-cliquez sur le **Variables** dossier, puis mettez à jour les valeurs de la **AnalysisDatabase**, **AnalysisServer** , **PrimaryImportDatabase**, **PrimaryImportServer**, **StarSchemaDatabase**, et **StarSchemaServer** variables.</span><span class="sxs-lookup"><span data-stu-id="07347-173">Click the **Package Explorer** tab, double-click the **Variables** folder, and then update the values for the **AnalysisDatabase**, **AnalysisServer**, **PrimaryImportDatabase**, **PrimaryImportServer**, **StarSchemaDatabase**, and **StarSchemaServer** variables.</span></span> <span data-ttu-id="07347-174">Vous devez mettre à jour les valeurs pour pointer vers le nouveau serveur et base de données.</span><span class="sxs-lookup"><span data-stu-id="07347-174">You must update the values to point to the new server and database.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="07347-175">Répétez l’étape 4 et 12 pour tous les packages que vous souhaitez mettre à jour.</span><span class="sxs-lookup"><span data-stu-id="07347-175">Repeat step 4 through 12 for all the packages that you want to update.</span></span>  
  
13. <span data-ttu-id="07347-176">Cliquez sur puis **fichier** menu, puis sur **Enregistrer tout**.</span><span class="sxs-lookup"><span data-stu-id="07347-176">Click then **File** menu, and then click **Save All**.</span></span>  
  
14. <span data-ttu-id="07347-177">Démarrez SQL Server Management Studio.</span><span class="sxs-lookup"><span data-stu-id="07347-177">Start the SQL Server Management Studio.</span></span> <span data-ttu-id="07347-178">Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur **Microsoft SQL Server 2008 R2** ou **Microsoft SQL Server 2008 SP1**, puis cliquez sur  **SQL Server Management Studio**.</span><span class="sxs-lookup"><span data-stu-id="07347-178">Click **Start**, click **All Programs**, click **Microsoft SQL Server 2008 R2** or **Microsoft SQL Server 2008 SP1**, and then click **SQL Server Management Studio**.</span></span>  
  
15. <span data-ttu-id="07347-179">Dans le **se connecter au serveur** boîte de dialogue, à partir de la **Server** liste de type liste déroulante, sélectionnez **Integration Services**.</span><span class="sxs-lookup"><span data-stu-id="07347-179">In the **Connect to Server** dialog box, from the **Server** type drop-down list, select **Integration Services**.</span></span>  
  
16. <span data-ttu-id="07347-180">Spécifiez le nom du serveur et les informations d’identification pour se connecter au serveur et cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="07347-180">Specify the server name and credentials to connect to the server and click **OK**.</span></span>  
  
17. <span data-ttu-id="07347-181">Dans le **l’Explorateur d’objets**, développez **Integration Services**, développez **Packages stockés**, puis cliquez sur **MSDB**.</span><span class="sxs-lookup"><span data-stu-id="07347-181">In the **Object Explorer**, expand **Integration Services**, expand **Stored Packages**, and then click **MSDB**.</span></span>  
  
18. <span data-ttu-id="07347-182">Dans le **détails de l’Explorateur d’objets** onglet, cliquez sur le package de mise à jour précédemment, puis sur **importer un Package**.</span><span class="sxs-lookup"><span data-stu-id="07347-182">In the **Object Explorer Details** tab, right-click the package that you updated earlier and then click **Import Package**.</span></span>  
  
19. <span data-ttu-id="07347-183">Dans le **importer un Package** boîte de dialogue, à partir de la **emplacement du Package** la liste déroulante, sélectionnez **système de fichiers**.</span><span class="sxs-lookup"><span data-stu-id="07347-183">In the **Import Package** dialog box, from the **Package location** drop-down list, select **File System**.</span></span>  
  
20. <span data-ttu-id="07347-184">Dans **chemin d’accès du Package**, accédez à votre projet enregistré, sélectionnez le fichier .dtsx pour le package que vous souhaitez importer, puis cliquez sur **ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="07347-184">In **Package Path**, navigate to your saved project, select the .dtsx file for the package you want to import, and then click **Open**.</span></span>  
  
21. <span data-ttu-id="07347-185">Cliquez dans la zone Nom du Package pour remplir automatiquement la zone.</span><span class="sxs-lookup"><span data-stu-id="07347-185">Click inside the Package Name box to automatically populate the box.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="07347-186">Répétez l’étape 18 à 21 pour tous les packages que vous souhaitez mettre à jour.</span><span class="sxs-lookup"><span data-stu-id="07347-186">Repeat step 18 through 21 for all the packages that you want to update.</span></span>  
  
22. <span data-ttu-id="07347-187">Cliquez sur **OK**, puis cliquez sur **Oui** à remplacer.</span><span class="sxs-lookup"><span data-stu-id="07347-187">Click **OK**, and then click **Yes** to overwrite.</span></span>  
  
23. <span data-ttu-id="07347-188">Démarrer toutes les [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] services.</span><span class="sxs-lookup"><span data-stu-id="07347-188">Start all [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] services.</span></span> <span data-ttu-id="07347-189">Pour plus d’informations, consultez la rubrique [comment démarrer, arrêter, suspendre, reprendre ou redémarrer les Services BizTalk Server](http://go.microsoft.com/fwlink/?LinkId=154394) (http://go.microsoft.com/fwlink/?LinkId=154394) dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] aide.</span><span class="sxs-lookup"><span data-stu-id="07347-189">For more information, see the topic [How To Start, Stop, Pause, Resume, or Restart BizTalk Server Services](http://go.microsoft.com/fwlink/?LinkId=154394) (http://go.microsoft.com/fwlink/?LinkId=154394) in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help.</span></span>  
  
24. <span data-ttu-id="07347-190">Démarrez le service IIS.</span><span class="sxs-lookup"><span data-stu-id="07347-190">Start the IIS service.</span></span>  
  
25. <span data-ttu-id="07347-191">Démarrez le service de Notification des alertes BAM :</span><span class="sxs-lookup"><span data-stu-id="07347-191">Start the BAM Alerts Notification service:</span></span>  
  
    1.  <span data-ttu-id="07347-192">Cliquez sur **Démarrer**, puis sur **Exécuter**, tapez **cmd**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="07347-192">Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
    2.  <span data-ttu-id="07347-193">À l'invite de commandes, tapez :</span><span class="sxs-lookup"><span data-stu-id="07347-193">At the command prompt, type:</span></span>  
  
         <span data-ttu-id="07347-194">**Net start NS$ BamAlerts**</span><span class="sxs-lookup"><span data-stu-id="07347-194">**Net start NS$BamAlerts**</span></span>  
  
26. <span data-ttu-id="07347-195">Activez les mises à jour du cube d'analyse BAM et les lots SSIS de gestion des données.</span><span class="sxs-lookup"><span data-stu-id="07347-195">Enable any BAM cube update and data maintenance SSIS packages.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07347-196">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="07347-196">See Also</span></span>  
 [<span data-ttu-id="07347-197">Déplacement de bases de données</span><span class="sxs-lookup"><span data-stu-id="07347-197">Moving Databases</span></span>](../technical-guides/moving-databases.md)