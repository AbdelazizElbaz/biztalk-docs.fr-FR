---
title: "Comment mettre à jour les références pour le serveur d’analyse BAM et les noms de base de données de schéma en étoile | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- restoring [BAM], Analysis database
- Analysis database [BAM], restoring
- restoring, BAM
- restoring [BAM], updating references
- BAM, restoring
- Analysis database [BAM], updating references
ms.assetid: cbe5e500-0a25-427e-bc76-1eae24b3e5f3
caps.latest.revision: "29"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b4f98129efd2f7c027ecb6c3e69d494ff2e96e8b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-update-references-to-the-bam-analysis-server-and-star-schema-database-names"></a><span data-ttu-id="8c065-102">Mise à jour des références aux noms du serveur Analyse BAM et de la base de données de schémas en étoile BAM</span><span class="sxs-lookup"><span data-stu-id="8c065-102">How to Update References to the BAM Analysis Server and Star Schema Database Names</span></span>
<span data-ttu-id="8c065-103">Si vous avez sauvegardé vos bases de données BAMAnalysis et BAMStarSchema, vous pouvez, dans l'éventualité d'une défaillance de données ou du système, restaurer cette sauvegarde sur un ordinateur distinct et la renommer.</span><span class="sxs-lookup"><span data-stu-id="8c065-103">If you backed up your BAMAnalysis and BAMStarSchema databases, in the event of a system or data failure you can restore that backup to a different computer and you can rename the backup.</span></span>  
  
 <span data-ttu-id="8c065-104">Pour restaurer les bases de données BAMStarSchema et analyse BAM, effectuez les étapes de [comment restaurer vos bases de données](../core/how-to-restore-your-databases.md).</span><span class="sxs-lookup"><span data-stu-id="8c065-104">To restore the BAM Analysis Server or BAMStarSchema databases, perform the steps in [How to Restore Your Databases](../core/how-to-restore-your-databases.md).</span></span> <span data-ttu-id="8c065-105">En outre, vous devez mettre à jour les lots DTS (Data Transformation Services) BAM avec les nouveaux noms du serveur et de la base de données.</span><span class="sxs-lookup"><span data-stu-id="8c065-105">In addition, you must update the BAM Data Transformation Services (DTS) packages with the new server name and database name.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="8c065-106">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="8c065-106">Prerequisites</span></span>  
 <span data-ttu-id="8c065-107">Vous devez être connecté en tant que membre de le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] groupe Administrateurs pour effectuer cette procédure.</span><span class="sxs-lookup"><span data-stu-id="8c065-107">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group to perform this procedure.</span></span>  
  
### <a name="to-update-references-to-the-bam-analysis-server-and-bam-star-schema-database-name-sql-server-2008-r2sp1"></a><span data-ttu-id="8c065-108">Pour mettre à jour les références aux noms du serveur Analyse BAM et de la base de données de schémas en étoile BAM (SQL Server 2008R2/SP1)</span><span class="sxs-lookup"><span data-stu-id="8c065-108">To update references to the BAM Analysis Server and BAM Star Schema database name (SQL Server 2008 R2/SP1)</span></span>  
  
1.  <span data-ttu-id="8c065-109">Arrêtez toute mise à jour du cube d'analyse BAM et tout lot SSIS de maintenance des données, ou empêchez leur exécution jusqu'à ce que vous ayez restauré la base de données BAMAnalysis ou BAMStarSchema.</span><span class="sxs-lookup"><span data-stu-id="8c065-109">Stop any BAM cube update and data maintenance SSIS packages, or prevent them from running until you have restored the BAMAnalysis or BAMStarSchema databases.</span></span>  
  
2.  <span data-ttu-id="8c065-110">Arrêtez le service de l'application BizTalk (y compris le service de bus d'événements BAM) de sorte qu'il ne tente pas d'importer davantage de données dans les bases de données.</span><span class="sxs-lookup"><span data-stu-id="8c065-110">Stop the BizTalk Application service (which includes the BAM Event Bus service) so it does not try to import more data into the databases.</span></span>  
  
    1.  <span data-ttu-id="8c065-111">Cliquez sur **Démarrer**, cliquez sur **exécuter**, puis tapez **services.msc**.</span><span class="sxs-lookup"><span data-stu-id="8c065-111">Click **Start**, click **Run**, and then type **services.msc**.</span></span>  
  
    2.  <span data-ttu-id="8c065-112">Cliquez sur le **groupe BizTalk des services BizTalk : BizTalkServerApplication** de service, puis cliquez sur **arrêter**.</span><span class="sxs-lookup"><span data-stu-id="8c065-112">Right-click the **BizTalk Service BizTalk Group: BizTalkServerApplication** service and then click **Stop**.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="8c065-113">Une autre façon d’arrêter un service consiste à utiliser le **Net Stop** commande.</span><span class="sxs-lookup"><span data-stu-id="8c065-113">Another way to stop a service is to use the **Net Stop** command.</span></span> <span data-ttu-id="8c065-114">Pour arrêter le service BizTalk à l’aide de Net Stop, ouvrez un **invite de commandes** (si vous utilisez Windows Server 2008 ou Windows Vista, démarrez l’invite de commandes à l’aide de **exécuter en tant qu’administrateur**) et tapez la commande suivante : `Net Stop BTSSvc$BizTalkServerApplication` Appuyez sur **entrée**.</span><span class="sxs-lookup"><span data-stu-id="8c065-114">To stop the BizTalk service using Net Stop, open a **Command Prompt** (If using Windows Server 2008 or Windows Vista, start the Command Prompt using **Run As Administrator**) and type the following: `Net Stop BTSSvc$BizTalkServerApplication` then press **Enter**.</span></span>  
  
3.  <span data-ttu-id="8c065-115">Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur **Microsoft SQL Server 2008 R2**, puis cliquez sur **SQL Server Business Intelligence Development Studio**.</span><span class="sxs-lookup"><span data-stu-id="8c065-115">Click **Start**, click **All Programs**, click **Microsoft SQL Server 2008 R2**, and then click **SQL Server Business Intelligence Development Studio**.</span></span>  
  
4.  <span data-ttu-id="8c065-116">Créez un projet dans SQL Server Business Intelligence Development Studio.</span><span class="sxs-lookup"><span data-stu-id="8c065-116">In SQL Server Business Intelligence Development Studio, create a new project.</span></span> <span data-ttu-id="8c065-117">Cliquez sur **fichier**, cliquez sur **nouveau**, puis cliquez sur **projet**.</span><span class="sxs-lookup"><span data-stu-id="8c065-117">Click **File**, click **New**, and then click **Project**.</span></span>  
  
5.  <span data-ttu-id="8c065-118">Dans le **nouveau projet** boîte de dialogue **modèles**, cliquez sur **projet Integration Services**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="8c065-118">In the **New Project** dialog box, in **Templates**, click **Integration Services Project**, and then click **OK**.</span></span>  
  
6.  <span data-ttu-id="8c065-119">Dans le **projet Integration Services** boîte de dialogue **l’Explorateur de solutions**, avec le bouton droit **Packages SSIS**, puis cliquez sur **ajouter un Package existant**.</span><span class="sxs-lookup"><span data-stu-id="8c065-119">In the **Integration Services Project** dialog box, in **Solution Explorer**, right-click **SSIS Packages**, and then click **Add Existing Package**.</span></span>  
  
7.  <span data-ttu-id="8c065-120">Dans le **ajouter la copie des packages existants** boîte de dialogue le **Server** liste déroulante, sélectionnez le serveur qui contient le package BAM_AN.</span><span class="sxs-lookup"><span data-stu-id="8c065-120">In the **Add Copy of Existing Package** dialog box, in the **Server** drop-down list box, select the server that contains the BAM_AN package.</span></span>  
  
8.  <span data-ttu-id="8c065-121">Dans **chemin d’accès du Package**, cliquez sur le bouton de sélection.</span><span class="sxs-lookup"><span data-stu-id="8c065-121">In **Package Path**, click the ellipses button.</span></span>  
  
9. <span data-ttu-id="8c065-122">Dans le **Package SSIS** boîte de dialogue, sélectionnez le package BAM_AN, cliquez sur **OK**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="8c065-122">In the **SSIS Package** dialog box, select the BAM_AN package, click **OK**, and then click **OK**.</span></span>  
  
     <span data-ttu-id="8c065-123">À présent, le package s'affiche dans l'Explorateur de solutions.</span><span class="sxs-lookup"><span data-stu-id="8c065-123">The package is now listed in Solution Explorer.</span></span>  
  
10. <span data-ttu-id="8c065-124">Dans **l’Explorateur de solutions**, double-cliquez sur le package BAM_AN.</span><span class="sxs-lookup"><span data-stu-id="8c065-124">In **Solution Explorer**, double-click the BAM_AN package.</span></span> <span data-ttu-id="8c065-125">Dans **gestionnaires de connexions**, double-cliquez sur le numéro de base de données 3 (base de données MSDB).</span><span class="sxs-lookup"><span data-stu-id="8c065-125">In **Connection Managers**, double-click database number 3 (MSDB database).</span></span>  
  
11. <span data-ttu-id="8c065-126">Dans le **Gestionnaire de connexions** boîte de dialogue le **nom du serveur** zone, entrez le nom du serveur MSDB, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="8c065-126">In the **Connection Manager** dialog box, in the **Server name** box, enter the name of the MSDB server, and then click **OK**.</span></span>  
  
12. <span data-ttu-id="8c065-127">Cliquez sur le **Explorateur de Package** onglet, double-cliquez sur le **Variables** dossier, puis mettez à jour les valeurs pour le nom de serveur d’importation principale et principal d’importation de nom de base de données.</span><span class="sxs-lookup"><span data-stu-id="8c065-127">Click the **Package Explorer** tab, double-click the **Variables** folder, and then update the values for the primary import server name and primary import database name.</span></span>  
  
13. <span data-ttu-id="8c065-128">Cliquez sur **fichier**, puis cliquez sur **Enregistrer tout**.</span><span class="sxs-lookup"><span data-stu-id="8c065-128">Click **File**, and then click **Save All**.</span></span>  
  
14. <span data-ttu-id="8c065-129">Dans **Microsoft SQL Server Management Studio**, cliquez sur **connexion**.</span><span class="sxs-lookup"><span data-stu-id="8c065-129">In **Microsoft SQL Server Management Studio**, click **Connect**.</span></span>  
  
15. <span data-ttu-id="8c065-130">Cliquez sur **Integration Services**, double-cliquez sur **Packages stockés**, cliquez sur **MSDB**, cliquez sur le package BAM_AN, puis cliquez sur **importer un Package**.</span><span class="sxs-lookup"><span data-stu-id="8c065-130">Click **Integration Services**, double-click **Stored Packages**, click **MSDB**, right-click the BAM_AN package, and then click **Import Package**.</span></span>  
  
16. <span data-ttu-id="8c065-131">Dans le **importer un Package** boîte de dialogue **emplacement du Package**, sélectionnez **système de fichiers**.</span><span class="sxs-lookup"><span data-stu-id="8c065-131">In the **Import Package** dialog box, in **Package location**, select **File System**.</span></span>  
  
17. <span data-ttu-id="8c065-132">Dans **chemin d’accès du Package**, accédez à votre projet enregistré, sélectionnez le BAM_AN\*fichier .dtsx, puis cliquez sur **ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="8c065-132">In **Package Path**, navigate to your saved project, select the BAM_AN\*.dtsx file, and then click **Open**.</span></span>  
  
18. <span data-ttu-id="8c065-133">Cliquez à l’intérieur du **nom du Package** case pour remplir automatiquement la zone.</span><span class="sxs-lookup"><span data-stu-id="8c065-133">Click inside the **Package Name** box to automatically populate the box.</span></span>  
  
19. <span data-ttu-id="8c065-134">Cliquez sur **OK**, puis cliquez sur **Oui** à remplacer.</span><span class="sxs-lookup"><span data-stu-id="8c065-134">Click **OK**, and then click **Yes** to overwrite.</span></span>  
  
20. <span data-ttu-id="8c065-135">Redémarrez le service de l'application BizTalk.</span><span class="sxs-lookup"><span data-stu-id="8c065-135">Restart the BizTalk Application service.</span></span>  
  
    1.  <span data-ttu-id="8c065-136">Cliquez sur **Démarrer**, cliquez sur **exécuter**, puis tapez **services.msc**.</span><span class="sxs-lookup"><span data-stu-id="8c065-136">Click **Start**, click **Run**, and then type **services.msc**.</span></span>  
  
    2.  <span data-ttu-id="8c065-137">Cliquez sur le **groupe BizTalk des services BizTalk : BizTalkServerApplication** de service, puis cliquez sur **Démarrer**.</span><span class="sxs-lookup"><span data-stu-id="8c065-137">Right-click the **BizTalk Service BizTalk Group: BizTalkServerApplication** service and then click **Start**.</span></span>  
  
21. <span data-ttu-id="8c065-138">Activez les mises à jour du cube d'analyse BAM et les lots SSIS de gestion des données.</span><span class="sxs-lookup"><span data-stu-id="8c065-138">Enable any BAM cube update and data maintenance SSIS packages.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c065-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8c065-139">See Also</span></span>  
 [<span data-ttu-id="8c065-140">Sauvegarde et restauration BAM</span><span class="sxs-lookup"><span data-stu-id="8c065-140">Backing Up and Restoring BAM</span></span>](../core/backing-up-and-restoring-bam.md)