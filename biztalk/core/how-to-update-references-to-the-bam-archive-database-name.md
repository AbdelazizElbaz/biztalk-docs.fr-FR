---
title: "Comment mettre à jour les références au nom de base de données BAM Archive | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Archive database [BAM], restoring
- restoring, BAM
- restoring [BAM], Archive database
- restoring [BAM], updating references
- Archive database [BAM], updating references
- BAM, restoring
ms.assetid: a0b8543e-6fc1-412e-b74e-683352d9c49e
caps.latest.revision: "23"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b0df87a548c2a6a5a207673d96a984e16287f04a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-update-references-to-the-bam-archive-database-name"></a><span data-ttu-id="a8da4-102">Mise à jour des références au nom de la base de données des archives BAM</span><span class="sxs-lookup"><span data-stu-id="a8da4-102">How to Update References to the BAM Archive Database Name</span></span>
<span data-ttu-id="a8da4-103">Si vous avez sauvegardé vos bases de données BAMArchive, vous pouvez, dans l'éventualité d'une défaillance de données ou du système, restaurer cette sauvegarde et la renommer.</span><span class="sxs-lookup"><span data-stu-id="a8da4-103">If you backed up your BAMArchive databases, in the event of a system or data failure you can restore that backup and rename it.</span></span>  
  
 <span data-ttu-id="a8da4-104">Pour restaurer les bases de données BAMArchive, effectuez les étapes de [comment restaurer vos bases de données](../core/how-to-restore-your-databases.md).</span><span class="sxs-lookup"><span data-stu-id="a8da4-104">To restore the BAMArchive databases, perform the steps in [How to Restore Your Databases](../core/how-to-restore-your-databases.md).</span></span> <span data-ttu-id="a8da4-105">Vous devez en outre suivre les étapes générales suivantes, qui sont suivies d'une procédure qui les décrit en détails :</span><span class="sxs-lookup"><span data-stu-id="a8da4-105">In addition, you must perform these general steps, which are followed by a procedure that describes the steps in detail:</span></span>  
  
-   <span data-ttu-id="a8da4-106">Mettez à jour les packages DTS de la fonctionnalité BAM avec les nouveaux noms de serveur et de base de données.</span><span class="sxs-lookup"><span data-stu-id="a8da4-106">Update the BAM DTS packages with the new server name and database name.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="a8da4-107">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="a8da4-107">Prerequisites</span></span>  
 <span data-ttu-id="a8da4-108">Vous devez être connecté en tant que membre de le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] groupe Administrateurs pour effectuer cette procédure.</span><span class="sxs-lookup"><span data-stu-id="a8da4-108">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group to perform this procedure.</span></span>  
  
### <a name="to-update-references-to-the-bam-archive-database-name-sql-server-2008-r2sp1"></a><span data-ttu-id="a8da4-109">Pour mettre à jour les références au nom de la base de données BAMArchive (SQL Server 2008 R2/SP1)</span><span class="sxs-lookup"><span data-stu-id="a8da4-109">To update references to the BAM Archive database name (SQL Server 2008 R2/SP1)</span></span>  
  
1.  <span data-ttu-id="a8da4-110">Arrêtez toute mise à jour du cube d'analyse BAM et tout lot DTS de maintenance des données, ou empêchez leur exécution jusqu'à ce que vous ayez restauré la base de données BAMArchive.</span><span class="sxs-lookup"><span data-stu-id="a8da4-110">Stop any BAM cube update and data maintenance DTS packages, or prevent them from running until you have restored the BAMArchive database.</span></span>  
  
2.  <span data-ttu-id="a8da4-111">Arrêtez le service de l'application BizTalk (y compris le service Bus d'événements BAM) de sorte qu'il ne tente pas d'importer davantage de données dans la base de données.</span><span class="sxs-lookup"><span data-stu-id="a8da4-111">Stop the BizTalk Application service (which includes the BAM Event Bus service) so it does not try to import more data into the database.</span></span>  
  
    1.  <span data-ttu-id="a8da4-112">Cliquez sur **Démarrer**, cliquez sur **exécuter**, puis tapez **services.msc**.</span><span class="sxs-lookup"><span data-stu-id="a8da4-112">Click **Start**, click **Run**, and then type **services.msc**.</span></span>  
  
    2.  <span data-ttu-id="a8da4-113">Cliquez sur le **groupe BizTalk des services BizTalk : BizTalkServerApplication** de service, puis cliquez sur **arrêter**.</span><span class="sxs-lookup"><span data-stu-id="a8da4-113">Right-click the **BizTalk Service BizTalk Group: BizTalkServerApplication** service and then click **Stop**.</span></span>  
  
3.  <span data-ttu-id="a8da4-114">Cliquez sur **Démarrer**, cliquez sur **programmes**, cliquez sur **Microsoft SQL Server 2008 R2**, puis cliquez sur **SQL Server Business Intelligence Development Studio**.</span><span class="sxs-lookup"><span data-stu-id="a8da4-114">Click **Start**, click **Programs**, click **Microsoft SQL Server 2008 R2**, and then click **SQL Server Business Intelligence Development Studio**.</span></span>  
  
4.  <span data-ttu-id="a8da4-115">Créez un projet dans SQL Server Business Intelligence Development Studio.</span><span class="sxs-lookup"><span data-stu-id="a8da4-115">In SQL Server Business Intelligence Development Studio, create a new project.</span></span> <span data-ttu-id="a8da4-116">Cliquez sur **fichier**, cliquez sur **nouveau**, puis cliquez sur **projet**.</span><span class="sxs-lookup"><span data-stu-id="a8da4-116">Click **File**, click **New**, and then click **Project**.</span></span>  
  
5.  <span data-ttu-id="a8da4-117">Dans le **nouveau projet** boîte de dialogue **modèles**, cliquez sur **projet Integration Services**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="a8da4-117">In the **New Project** dialog box, in **Templates**, click **Integration Services Project**, and then click **OK**.</span></span>  
  
6.  <span data-ttu-id="a8da4-118">Dans le **projet Integration Services** boîte de dialogue **l’Explorateur de solutions**, avec le bouton droit **Packages SSIS**, puis cliquez sur **ajouter un Package existant**.</span><span class="sxs-lookup"><span data-stu-id="a8da4-118">In the **Integration Services Project** dialog box, in **Solution Explorer**, right-click **SSIS Packages**, and then click **Add Existing Package**.</span></span>  
  
7.  <span data-ttu-id="a8da4-119">Dans le **ajouter la copie des packages existants** boîte de dialogue le **Server** liste déroulante, sélectionnez le serveur qui contient le package BAM_DM.</span><span class="sxs-lookup"><span data-stu-id="a8da4-119">In the **Add Copy of Existing Package** dialog box, in the **Server** drop-down list box, select the server that contains the BAM_DM package.</span></span>  
  
8.  <span data-ttu-id="a8da4-120">Dans **chemin d’accès du Package**, cliquez sur le bouton de sélection.</span><span class="sxs-lookup"><span data-stu-id="a8da4-120">In **Package Path**, click the ellipses button.</span></span>  
  
9. <span data-ttu-id="a8da4-121">Dans le **Package SSIS** boîte de dialogue, sélectionnez le package BAM_DM, cliquez sur **OK**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="a8da4-121">In the **SSIS Package** dialog box, select the BAM_DM package, click **OK**, and then click **OK**.</span></span>  
  
     <span data-ttu-id="a8da4-122">À présent, le package s'affiche dans l'Explorateur de solutions.</span><span class="sxs-lookup"><span data-stu-id="a8da4-122">The package is now listed in Solution Explorer.</span></span>  
  
10. <span data-ttu-id="a8da4-123">Dans **l’Explorateur de solutions**, double-cliquez sur le package BAM_DM.</span><span class="sxs-lookup"><span data-stu-id="a8da4-123">In **Solution Explorer**, double-click the BAM_DM package.</span></span> <span data-ttu-id="a8da4-124">Dans **gestionnaires de connexions**, double-cliquez sur le numéro de base de données 3 (base de données MSDB).</span><span class="sxs-lookup"><span data-stu-id="a8da4-124">In **Connection Managers**, double-click database number 3 (MSDB database).</span></span>  
  
11. <span data-ttu-id="a8da4-125">Dans le **Gestionnaire de connexions** boîte de dialogue le **nom du serveur** zone, entrez le nom du serveur MSDB, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="a8da4-125">In the **Connection Manager** dialog box, in the **Server name** box, enter the name of the MSDB server, and then click **OK**.</span></span>  
  
12. <span data-ttu-id="a8da4-126">Cliquez sur le **Explorateur de Package** onglet, double-cliquez sur le **Variables** dossier, puis mettez à jour les valeurs pour le nom de serveur d’importation principale et principal d’importation de nom de base de données.</span><span class="sxs-lookup"><span data-stu-id="a8da4-126">Click the **Package Explorer** tab, double-click the **Variables** folder, and then update the values for the primary import server name and primary import database name.</span></span>  
  
13. <span data-ttu-id="a8da4-127">Cliquez sur **fichier**, puis cliquez sur **Enregistrer tout**.</span><span class="sxs-lookup"><span data-stu-id="a8da4-127">Click **File**, and then click **Save All**.</span></span>  
  
14. <span data-ttu-id="a8da4-128">Dans **Microsoft SQL Server Management Studio**, cliquez sur **connexion**.</span><span class="sxs-lookup"><span data-stu-id="a8da4-128">In **Microsoft SQL Server Management Studio**, click **Connect**.</span></span>  
  
15. <span data-ttu-id="a8da4-129">Cliquez sur **Integration Services**, double-cliquez sur **Packages stockés**, cliquez sur **MSDB**, cliquez sur le package BAM_DM, puis cliquez sur **importer un Package**.</span><span class="sxs-lookup"><span data-stu-id="a8da4-129">Click **Integration Services**, double-click **Stored Packages**, click **MSDB**, right-click the BAM_DM package, and then click **Import Package**.</span></span>  
  
16. <span data-ttu-id="a8da4-130">Dans le **importer un Package** boîte de dialogue **emplacement du Package**, sélectionnez **système de fichiers**.</span><span class="sxs-lookup"><span data-stu-id="a8da4-130">In the **Import Package** dialog box, in **Package location**, select **File System**.</span></span>  
  
17. <span data-ttu-id="a8da4-131">Dans **chemin d’accès du Package**, accédez à votre projet enregistré, sélectionnez le BAM_DM\*fichier .dtsx, puis cliquez sur **ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="a8da4-131">In **Package Path**, navigate to your saved project, select the BAM_DM\*.dtsx file, and then click **Open**.</span></span>  
  
18. <span data-ttu-id="a8da4-132">Cliquez à l’intérieur du **nom du Package** case pour remplir automatiquement la zone.</span><span class="sxs-lookup"><span data-stu-id="a8da4-132">Click inside the **Package Name** box to automatically populate the box.</span></span>  
  
19. <span data-ttu-id="a8da4-133">Cliquez sur **OK**, puis cliquez sur **Oui** à remplacer.</span><span class="sxs-lookup"><span data-stu-id="a8da4-133">Click **OK**, and then click **Yes** to overwrite.</span></span>  
  
20. <span data-ttu-id="a8da4-134">Redémarrez le service de l'application BizTalk.</span><span class="sxs-lookup"><span data-stu-id="a8da4-134">Restart the BizTalk Application service.</span></span>  
  
    1.  <span data-ttu-id="a8da4-135">Cliquez sur **Démarrer**, cliquez sur **exécuter**, puis tapez **services.msc**.</span><span class="sxs-lookup"><span data-stu-id="a8da4-135">Click **Start**, click **Run**, and then type **services.msc**.</span></span>  
  
    2.  <span data-ttu-id="a8da4-136">Cliquez sur le **groupe BizTalk des services BizTalk : BizTalkServerApplication** de service, puis cliquez sur **Démarrer**.</span><span class="sxs-lookup"><span data-stu-id="a8da4-136">Right-click the **BizTalk Service BizTalk Group: BizTalkServerApplication** service and then click **Start**.</span></span>  
  
21. <span data-ttu-id="a8da4-137">Activez les mises à jour du cube d'analyse BAM et les lots SSIS de gestion des données.</span><span class="sxs-lookup"><span data-stu-id="a8da4-137">Enable any BAM cube update and data maintenance SSIS packages.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8da4-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a8da4-138">See Also</span></span>  
 [<span data-ttu-id="a8da4-139">Sauvegarde et restauration BAM</span><span class="sxs-lookup"><span data-stu-id="a8da4-139">Backing Up and Restoring BAM</span></span>](../core/backing-up-and-restoring-bam.md)