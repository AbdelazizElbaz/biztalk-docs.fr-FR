---
title: Planification de SQL Server Integration Services Packages | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 037ae2cf-c352-4823-95df-9a723f2b5a81
caps.latest.revision: "22"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a531a5d0a2233dba5826f4bff680a3c55403671d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="scheduling-sql-server-integration-services-packages"></a><span data-ttu-id="48d10-102">Planification des packages SQL Server Integration Services</span><span class="sxs-lookup"><span data-stu-id="48d10-102">Scheduling SQL Server Integration Services Packages</span></span>
<span data-ttu-id="48d10-103">Les utilisateurs créent les vues BAM en fonction des données stockées dans un cube OLAP (Online Analytical Processing).</span><span class="sxs-lookup"><span data-stu-id="48d10-103">Users create BAM views based on data stored in an online analytical processing (OLAP) cube.</span></span> <span data-ttu-id="48d10-104">Le package Integration Services de mise à jour du cube actualise les données du cube afin que les données affichées dans les vues OLAP soient correctes.</span><span class="sxs-lookup"><span data-stu-id="48d10-104">The Cube Update Integration Services package refreshes the data in the cube so that OLAP views reflect the correct data.</span></span>  
  
 <span data-ttu-id="48d10-105">Vous devez exécuter ce package au moins une fois pour que les vues OLAP fonctionnent.</span><span class="sxs-lookup"><span data-stu-id="48d10-105">You must run this package at least once for the OLAP views to work.</span></span> <span data-ttu-id="48d10-106">Pour une maintenance continue, vous devez planifier une exécution régulière de ce package.</span><span class="sxs-lookup"><span data-stu-id="48d10-106">For ongoing maintenance, you should schedule the package to run on a regular basis.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="48d10-107">Si vous avez restauré la base de données de schémas en étoile BAM ou arrêté [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] avant d'exécuter le package Integration Services de mise à jour du cube, vous devez actualiser les sources de données dans [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Analysis Manager ou redémarrer le service OLAP afin que le package puisse être exécuté correctement.</span><span class="sxs-lookup"><span data-stu-id="48d10-107">If you restored the BAM Star Schema database or stopped [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] before running the Cube Update Integration Services package, you must refresh the data sources in [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Analysis Manager or restart the OLAP service before you can run the package successfully.</span></span>  
  
 <span data-ttu-id="48d10-108">Vous pouvez planifier l'exécution d'un package enregistré à un moment précis, ponctuellement ou à intervalles réguliers.</span><span class="sxs-lookup"><span data-stu-id="48d10-108">You can schedule a saved package to execute at specific times, either once or at recurring intervals.</span></span> <span data-ttu-id="48d10-109">Exemple :</span><span class="sxs-lookup"><span data-stu-id="48d10-109">For example:</span></span>  
  
-   <span data-ttu-id="48d10-110">Tous les jours à minuit.</span><span class="sxs-lookup"><span data-stu-id="48d10-110">Daily at midnight.</span></span>  
  
-   <span data-ttu-id="48d10-111">chaque semaine, le dimanche, à 6h00 ;</span><span class="sxs-lookup"><span data-stu-id="48d10-111">Weekly on Sunday at 06:00.</span></span>  
  
-   <span data-ttu-id="48d10-112">le premier jour du mois, ou le dernier.</span><span class="sxs-lookup"><span data-stu-id="48d10-112">The first or last day of the month.</span></span>  
  
 <span data-ttu-id="48d10-113">Un package planifié est exécuté par [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] de la même façon qu'un travail.</span><span class="sxs-lookup"><span data-stu-id="48d10-113">A scheduled package is executed by [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] as a job.</span></span>  
  
 <span data-ttu-id="48d10-114">Pour plus d’informations sur l’exécution [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] packages, consultez [http://go.microsoft.com/fwlink/?LinkId=125738](http://go.microsoft.com/fwlink/?LinkId=125738).</span><span class="sxs-lookup"><span data-stu-id="48d10-114">For information about running [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] packages, see [http://go.microsoft.com/fwlink/?LinkId=125738](http://go.microsoft.com/fwlink/?LinkId=125738).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="48d10-115">Par défaut, la journalisation pour l’archivage et la mise à jour de cube des packages BAM SSIS est activée et stockée dans la base de données msdb.</span><span class="sxs-lookup"><span data-stu-id="48d10-115">By default, logging for archiving and cubing BAM SSIS packages is turned on and is stored in the msdb database.</span></span> <span data-ttu-id="48d10-116">Au fil du temps, cette fonctionnalité peut créer un volume considérable de données de journal des événements SSIS en raison d’un grand nombre d’activités BAM ou d’une exécution fréquente de packages SSIS appartenant à l’analyse BAM.</span><span class="sxs-lookup"><span data-stu-id="48d10-116">Overtime, this may result in a significant volume of SSIS event log data caused by large number of BAM activities or frequent execution of BAM owned SSIS packages.</span></span> <span data-ttu-id="48d10-117">Pour résoudre ce problème, vous pouvez supprimer les anciennes entrées de journal, car celles-ci sont principalement utilisées à des fins de débogage.</span><span class="sxs-lookup"><span data-stu-id="48d10-117">To resolve this, you can delete the old log entries because these entries are used primarily for debugging.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="48d10-118">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="48d10-118">Prerequisites</span></span>  
 <span data-ttu-id="48d10-119">Pour exécuter ces procédures, vous devez ouvrir une session en tant que membre du groupe Administrateurs BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="48d10-119">You must be logged on as a member of the BizTalk Server Administrators group to perform these procedures.</span></span>  
  
### <a name="to-run-the-cube-update-integration-services-package"></a><span data-ttu-id="48d10-120">Pour exécuter le package Integration Services de mise à jour du cube</span><span class="sxs-lookup"><span data-stu-id="48d10-120">To run the Cube Update Integration Services package</span></span>  
  
1.  <span data-ttu-id="48d10-121">Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur **Microsoft SQL Server 2008 SP1** ou **Microsoft SQL Server 2008 R2**, puis cliquez sur  **SQL Server Management Studio**.</span><span class="sxs-lookup"><span data-stu-id="48d10-121">Click **Start**, click **All Programs**, click **Microsoft SQL Server 2008 SP1** or **Microsoft SQL Server 2008 R2**, and then click **SQL Server Management Studio**.</span></span>  
  
2.  <span data-ttu-id="48d10-122">Dans le **se connecter au serveur** boîte de dialogue le **type de serveur** la liste déroulante, sélectionnez **Integration Services**.</span><span class="sxs-lookup"><span data-stu-id="48d10-122">In the **Connect to server** dialog box, in the **Server type** drop-down list, select **Integration Services**.</span></span>  
  
3.  <span data-ttu-id="48d10-123">Dans le **nom du serveur** liste déroulante, sélectionnez le nom du serveur sur lequel vous exécutez le package.</span><span class="sxs-lookup"><span data-stu-id="48d10-123">In the **Server name** drop-down list, select the name of the server on which you are running the package.</span></span>  
  
4.  <span data-ttu-id="48d10-124">Dans le **authentification** liste déroulante, sélectionnez le type d’authentification que vous utilisez pour vous connecter au serveur.</span><span class="sxs-lookup"><span data-stu-id="48d10-124">In the **Authentication** drop-down list, select the type of authentication that you are using to connect to the server.</span></span>  
  
5.  <span data-ttu-id="48d10-125">Si nécessaire, tapez votre nom d’utilisateur et un mot de passe.</span><span class="sxs-lookup"><span data-stu-id="48d10-125">If necessary, type your user name and password.</span></span>  
  
6.  <span data-ttu-id="48d10-126">Cliquez sur **Se connecter**.</span><span class="sxs-lookup"><span data-stu-id="48d10-126">Click **Connect**.</span></span>  
  
7.  <span data-ttu-id="48d10-127">Dans l’arborescence de la console, développez **Integration Services**, développez **Packages stockés**, puis cliquez sur **MSDB**.</span><span class="sxs-lookup"><span data-stu-id="48d10-127">In the console tree, expand **Integration Services**, expand **Stored Packages**, and then click **MSDB**.</span></span>  
  
8.  <span data-ttu-id="48d10-128">Cliquez sur le **BAM_AN_\<nom de la vue >** du package, puis cliquez sur **exécuter le Package**.</span><span class="sxs-lookup"><span data-stu-id="48d10-128">Right-click the **BAM_AN_\<View name>** package, and then click **Run Package**.</span></span>  
  
### <a name="to-run-the-maintaining-bam-data-integration-services-package"></a><span data-ttu-id="48d10-129">Pour exécuter le package Integration Services de maintenance des données BAM</span><span class="sxs-lookup"><span data-stu-id="48d10-129">To run the Maintaining BAM Data Integration Services package</span></span>  
  
1.  <span data-ttu-id="48d10-130">Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur **Microsoft SQL Server 2008 SP1** ou **Microsoft SQL Server 2008 R2**, puis cliquez sur  **SQL Server Management Studio**.</span><span class="sxs-lookup"><span data-stu-id="48d10-130">Click **Start**, click **All Programs**, click **Microsoft SQL Server 2008 SP1** or **Microsoft SQL Server 2008 R2**, and then click **SQL Server Management Studio**.</span></span>  
  
2.  <span data-ttu-id="48d10-131">Dans le **se connecter au serveur** boîte de dialogue le **type de serveur** la liste déroulante, sélectionnez **Integration Services**.</span><span class="sxs-lookup"><span data-stu-id="48d10-131">In the **Connect to server** dialog box, in the **Server type** drop-down list, select **Integration Services**.</span></span>  
  
3.  <span data-ttu-id="48d10-132">Dans le **nom du serveur** liste déroulante, sélectionnez le nom du serveur sur lequel vous exécutez le package.</span><span class="sxs-lookup"><span data-stu-id="48d10-132">In the **Server name** drop-down list, select the name of the server on which you are running the package.</span></span>  
  
4.  <span data-ttu-id="48d10-133">Dans le **authentification** liste déroulante, sélectionnez le type d’authentification que vous utilisez pour vous connecter au serveur.</span><span class="sxs-lookup"><span data-stu-id="48d10-133">In the **Authentication** drop-down list, select the type of authentication that you are using to connect to the server.</span></span>  
  
5.  <span data-ttu-id="48d10-134">Si nécessaire, tapez votre nom d’utilisateur et un mot de passe.</span><span class="sxs-lookup"><span data-stu-id="48d10-134">If necessary, type your user name and password.</span></span>  
  
6.  <span data-ttu-id="48d10-135">Cliquez sur **Se connecter**.</span><span class="sxs-lookup"><span data-stu-id="48d10-135">Click **Connect**.</span></span>  
  
7.  <span data-ttu-id="48d10-136">Dans l’arborescence de la console, développez **Integration Services**, développez **Packages stockés**, puis cliquez sur **MSDB**.</span><span class="sxs-lookup"><span data-stu-id="48d10-136">In the console tree, expand **Integration Services**, expand **Stored Packages**, and then click **MSDB**.</span></span>  
  
8.  <span data-ttu-id="48d10-137">Cliquez sur le **BAM_DM_\<nom de l’activité >** du package, puis cliquez sur **exécuter le Package**.</span><span class="sxs-lookup"><span data-stu-id="48d10-137">Right-click the **BAM_DM_\<Activity name>** package, and then click **Run Package**.</span></span>  
  
### <a name="to-schedule-the-packages-to-run-regularly"></a><span data-ttu-id="48d10-138">Pour planifier l'exécution régulière des packages</span><span class="sxs-lookup"><span data-stu-id="48d10-138">To schedule the packages to run regularly</span></span>  
  
1.  <span data-ttu-id="48d10-139">Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur **Microsoft SQL Server 2008 SP1** ou **Microsoft SQL Server 2008 R2**, puis cliquez sur  **SQL Server Management Studio**.</span><span class="sxs-lookup"><span data-stu-id="48d10-139">Click **Start**, click **All Programs**, click **Microsoft SQL Server 2008 SP1** or **Microsoft SQL Server 2008 R2**, and then click **SQL Server Management Studio**.</span></span>  
  
2.  <span data-ttu-id="48d10-140">Dans le **se connecter au serveur** boîte de dialogue le **type de serveur** la liste déroulante, sélectionnez **moteur de base de données**.</span><span class="sxs-lookup"><span data-stu-id="48d10-140">In the **Connect to server** dialog box, in the **Server type** drop-down list, select **Database Engine**.</span></span>  
  
3.  <span data-ttu-id="48d10-141">Dans le **nom du serveur** liste déroulante, sélectionnez le nom du serveur sur lequel vous exécutez le package.</span><span class="sxs-lookup"><span data-stu-id="48d10-141">In the **Server name** drop-down list, select the name of the server on which you are running the package.</span></span>  
  
4.  <span data-ttu-id="48d10-142">Dans le **authentification** liste déroulante, sélectionnez le type d’authentification que vous utilisez pour vous connecter au serveur.</span><span class="sxs-lookup"><span data-stu-id="48d10-142">In the **Authentication** drop-down list, select the type of authentication that you are using to connect to the server.</span></span>  
  
5.  <span data-ttu-id="48d10-143">Si nécessaire, tapez votre nom d’utilisateur et un mot de passe.</span><span class="sxs-lookup"><span data-stu-id="48d10-143">If necessary, type your user name and password.</span></span>  
  
6.  <span data-ttu-id="48d10-144">Cliquez sur **Se connecter**.</span><span class="sxs-lookup"><span data-stu-id="48d10-144">Click **Connect**.</span></span>  
  
7.  <span data-ttu-id="48d10-145">Dans l’arborescence de la console, développez votre serveur, puis sélectionnez **l’Agent SQL Server**.</span><span class="sxs-lookup"><span data-stu-id="48d10-145">In the console tree, expand your server, and select **SQL Server Agent**.</span></span>  
  
8.  <span data-ttu-id="48d10-146">Si **l’Agent SQL Server** est désactivé, cliquez sur **l’Agent SQL Server**, puis sélectionnez **Démarrer**.</span><span class="sxs-lookup"><span data-stu-id="48d10-146">If **SQL Server Agent** is disabled, right-click **SQL Server Agent**, and then select **Start**.</span></span>  
  
9. <span data-ttu-id="48d10-147">Avec le bouton droit **l’Agent SQL Server**, puis sélectionnez **nouveau travail**.</span><span class="sxs-lookup"><span data-stu-id="48d10-147">Right-click **SQL Server Agent**, and select  **New Job**.</span></span>  
  
10. <span data-ttu-id="48d10-148">Dans le **nouveau travail** boîte de dialogue, tapez un nom pour la tâche dans le **nom** zone de texte.</span><span class="sxs-lookup"><span data-stu-id="48d10-148">In the **New Job** dialog box, type a name for the job in the **Name** text box.</span></span>  
  
11. <span data-ttu-id="48d10-149">Dans le **sélectionner une page** fenêtre, cliquez sur **étapes**, puis cliquez sur **nouveau**.</span><span class="sxs-lookup"><span data-stu-id="48d10-149">In the **Select a page** window, click **Steps**, and then click **New**.</span></span> <span data-ttu-id="48d10-150">Cette opération ouvre le **nouvelle étape du travail** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="48d10-150">This opens the **New Job Step** dialog box.</span></span>  
  
12. <span data-ttu-id="48d10-151">Dans le **nom de l’étape** texte, tapez le nom d’identification de l’étape.</span><span class="sxs-lookup"><span data-stu-id="48d10-151">In the **Step name** text box, type an identifying name for the step.</span></span>  
  
13. <span data-ttu-id="48d10-152">Dans le **Type** la liste déroulante, sélectionnez **Package SQL Server Integration Services** et dans le **source du Package** la liste déroulante, sélectionnez **magasin de packages SSIS** .</span><span class="sxs-lookup"><span data-stu-id="48d10-152">In the **Type** drop-down list, select **SQL Server Integration Services Package** and in the **Package source** drop-down list, select **SSIS Package Store**.</span></span>  
  
14. <span data-ttu-id="48d10-153">Dans le **Server** liste déroulante, sélectionnez le serveur sur lequel vous exécutez la tâche.</span><span class="sxs-lookup"><span data-stu-id="48d10-153">In the **Server** drop-down list, select the server on which you are running the job.</span></span>  
  
15. <span data-ttu-id="48d10-154">Cliquez sur le bouton de sélection de fichier pour le **Package** texte, sélectionnez le package que vous planifiez (soit la **BAM_DM_\<nom de l’activité >** ou **BAM_AN_\< Nom de la vue >** package), puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="48d10-154">Click the file selector button for the **Package** text box, select the package you are scheduling (either the **BAM_DM_\<Activity name>** or **BAM_AN_\<View name>** package), and then click **OK**.</span></span>  
  
16. <span data-ttu-id="48d10-155">Dans le **sélectionner une page** fenêtre, cliquez sur **planifications**, puis cliquez sur **nouveau**.</span><span class="sxs-lookup"><span data-stu-id="48d10-155">In the **Select a page** window, click **Schedules**, and then click **New**.</span></span> <span data-ttu-id="48d10-156">Cette opération ouvre le **nouvelle planification du travail** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="48d10-156">This opens the **New Job Schedule** dialog box.</span></span>  
  
17. <span data-ttu-id="48d10-157">Dans le **nom** zone de texte, tapez un nom pour la planification.</span><span class="sxs-lookup"><span data-stu-id="48d10-157">In the **Name** text box, type a name for the schedule.</span></span>  
  
18. <span data-ttu-id="48d10-158">Créez votre planification en vous servant des champs de fréquence.</span><span class="sxs-lookup"><span data-stu-id="48d10-158">Create your schedule using the frequency fields.</span></span>  
  
19. <span data-ttu-id="48d10-159">Cliquez sur **OK** pour enregistrer le travail.</span><span class="sxs-lookup"><span data-stu-id="48d10-159">Click **OK** to save the job.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="48d10-160">Si BAM est configuré avec une instance de SQL Server autre que l'instance par défaut, le BAM_AN_POCube DTSPackage n'est pas planifié/exécuté correctement.</span><span class="sxs-lookup"><span data-stu-id="48d10-160">If BAM is configured with a non-default instance of SQL Server, then the BAM_AN_POCube DTSPackage does not get scheduled/executed accurately.</span></span> <span data-ttu-id="48d10-161">Vous devez modifier le fichier de configuration pour autoriser la poursuite de l'exécution des packages.</span><span class="sxs-lookup"><span data-stu-id="48d10-161">You need to modify the configuration file to allow packages to continue running.</span></span> <span data-ttu-id="48d10-162">Pour plus d’informations, reportez-vous à la section « Modification du contenu du fichier Configuration » à [http://go.microsoft.com/fwlink/?LinkId=196768](http://go.microsoft.com/fwlink/?LinkId=196768).</span><span class="sxs-lookup"><span data-stu-id="48d10-162">For more information, refer to the "Modifying the Contents of the Configuration File" section at [http://go.microsoft.com/fwlink/?LinkId=196768](http://go.microsoft.com/fwlink/?LinkId=196768).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48d10-163">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="48d10-163">See Also</span></span>  
 [<span data-ttu-id="48d10-164">Gestion des bases de données BAM</span><span class="sxs-lookup"><span data-stu-id="48d10-164">Managing BAM Databases</span></span>](../core/managing-bam-databases.md)