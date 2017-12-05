---
title: "La sauvegarde de l’analyse BAM et l’analyse de suivi des bases de données de serveur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- backing up, DTS packages
- backing up [BAM], Tracking Analysis Server database
- backing up [BAM], OLAP cubes
- backing up [BAM], DTS packages
- purging, OLAP cubes
- Analysis database [BAM], backing up
- scheduling, BAM backups
- backing up [BAM], Analysis database
- OLAP cubes, purging
- backing up, BAM
- backing up [BAM], database order
- DTS packages, backing up
- backing up [BAM], Star Schema database
- backing up [BAM], scheduling
- Tracking Analysis Server database [BAM], backing up
- Star Schema database [BAM], backing up
ms.assetid: d39e3491-ab54-44f2-990a-7b8ee86f0501
caps.latest.revision: "19"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: effa2f5787f04493713ea6972562fe768081f4bc
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-back-up-the-bam-analysis-and-tracking-analysis-server-databases"></a><span data-ttu-id="a6745-102">Sauvegarde des bases de données Analyse BAM et Analyse des suivis</span><span class="sxs-lookup"><span data-stu-id="a6745-102">How to Back Up the BAM Analysis and Tracking Analysis Server Databases</span></span>
<span data-ttu-id="a6745-103">La base de données d'analyse BAM (Business Activity Monitoring) et la base de données des suivis du serveur d'analyse stockent le contenu dans des cubes SQL Server Analysis Services.</span><span class="sxs-lookup"><span data-stu-id="a6745-103">The Business Activity Monitoring (BAM) Analysis database and the Tracking Analysis Server database store content in SQL Server Analysis Services cubes.</span></span> <span data-ttu-id="a6745-104">Le travail de sauvegarde de BizTalk Server ne sauvegarde pas ces bases de données.</span><span class="sxs-lookup"><span data-stu-id="a6745-104">The Backup BizTalk Server job does not back up these databases.</span></span> <span data-ttu-id="a6745-105">C'est pourquoi, vous devez utiliser le gestionnaire d'analyse SQL Server.</span><span class="sxs-lookup"><span data-stu-id="a6745-105">Instead, to backup these databases, you must use SQL Server Analysis Manager.</span></span>  
  
 <span data-ttu-id="a6745-106">Une fois ces bases de données sauvegardées, vous pouvez purger les cubes OLAP.</span><span class="sxs-lookup"><span data-stu-id="a6745-106">After you back up these databases, you may want to purge the OLAP cubes.</span></span> <span data-ttu-id="a6745-107">Lors de la purge les cubes OLAP, vous devez également effectuer les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="a6745-107">When you purge the OLAP cubes, you must also perform the following steps:</span></span>  
  
1.  <span data-ttu-id="a6745-108">Dans la base de données BAMStarSchema, tronquez la ou les tables de faits du cube OLAP à purger.</span><span class="sxs-lookup"><span data-stu-id="a6745-108">Before you purge the OLAP cubes, in the BAMStarSchema database, truncate the fact table(s) for the cube you want to purge.</span></span> <span data-ttu-id="a6745-109">La convention d’affectation de noms de table est « bam_*\<CubeName\>*_Facts ».</span><span class="sxs-lookup"><span data-stu-id="a6745-109">The table naming convention is "bam_*\<CubeName\>*_Facts".</span></span>  
  
2.  <span data-ttu-id="a6745-110">Une fois les cubes OLAP purgés, vous devez traiter entièrement les cubes actifs, terminés et virtuels.</span><span class="sxs-lookup"><span data-stu-id="a6745-110">After you purge the OLAP cubes, you must fully process active, completed, and virtual cubes.</span></span>  
  
 <span data-ttu-id="a6745-111">Pour obtenir des instructions sur la sauvegarde des bases de données d'analyse, consultez la rubrique « Archivage d'une base de données Analysis Services » dans la documentation en ligne de SQL Server.</span><span class="sxs-lookup"><span data-stu-id="a6745-111">For instructions about backing up the analysis databases, see "Archiving an Analysis Services Database" in SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="a6745-112">**Planification des sauvegardes pour les bases de données BAM**</span><span class="sxs-lookup"><span data-stu-id="a6745-112">**Scheduling backups for the BAM databases**</span></span>  
  
 <span data-ttu-id="a6745-113">Si vous utilisez l'analyse BAM, vérifiez que ni le traitement des cubes BAM ni les lots DTS (Data Transformation Services) de maintenance des données ne sont exécutés lorsque le lot de sauvegarde est programmé pour s'exécuter.</span><span class="sxs-lookup"><span data-stu-id="a6745-113">If you are using BAM, verify that neither the BAM cube process nor data maintenance Data Transformation Services (DTS) packages are running when the backup package is scheduled to run.</span></span>  
  
 <span data-ttu-id="a6745-114">Pour assurer la cohérence des schémas dans les bases de données BAM, sauvegardez celles-ci, ainsi que les lots DTS, à chaque déploiement ou annulation de déploiement d'une activité BAM.</span><span class="sxs-lookup"><span data-stu-id="a6745-114">To ensure consistent schema across all BAM databases, back up the BAM databases and DTS packages each time you deploy or undeploy a BAM activity.</span></span>  
  
 <span data-ttu-id="a6745-115">Sauvegardez les bases de données d'analyse BAM et BAMStarSchema à chaque déploiement ou annulation de déploiement d'une vue BAM.</span><span class="sxs-lookup"><span data-stu-id="a6745-115">Back up the BAM Analysis database and BAMStarSchema database each time you deploy or undeploy a BAM view.</span></span>  
  
 <span data-ttu-id="a6745-116">Sauvegardez les bases de données BAM dans l'ordre suivant :</span><span class="sxs-lookup"><span data-stu-id="a6745-116">Back up the BAM databases in the following order:</span></span>  
  
1.  <span data-ttu-id="a6745-117">Configurez le travail de sauvegarde de BizTalk Server pour sauvegarder la base de données BAMPrimaryImport et les autres bases de données BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="a6745-117">Run the Backup BizTalk Server job to back up the BAMPrimaryImport database and your other BizTalk Server databases.</span></span>  
  
2.  <span data-ttu-id="a6745-118">Exécutez le lot DTS de maintenance des données BAM pour toutes les activités.</span><span class="sxs-lookup"><span data-stu-id="a6745-118">Run the BAM data maintenance DTS package for all activities.</span></span>  
  
     <span data-ttu-id="a6745-119">Intégrez ces étapes à un lot DTS et planifiez une exécution régulière du lot.</span><span class="sxs-lookup"><span data-stu-id="a6745-119">Incorporate these steps into a DTS package, and schedule the package to run on a regular basis.</span></span> <span data-ttu-id="a6745-120">Pour assurer l'intégrité des données, vérifiez qu'aucun autre lot DTS de création de cubes ou de maintenance de données n'est exécuté lorsque ce lot de sauvegarde doit être exécuté.</span><span class="sxs-lookup"><span data-stu-id="a6745-120">To ensure data integrity, make sure no other BAM cubing or data maintenance DTS packages run when this backup package is scheduled to run.</span></span>  
  
     <span data-ttu-id="a6745-121">Pour vous assurer de récupérer un ensemble complet de données archivées si la base de données BAMArchive échoue, sauvegardez cette dernière après y avoir copié la partition, mais avant de supprimer celle-ci de la base de données BAMPrimaryImport.</span><span class="sxs-lookup"><span data-stu-id="a6745-121">To ensure that you can recover a complete set of archived data if the BAMArchive database fails, back up the BAMArchive database after you copy the partition into the BAMArchive database, but before you delete the partition from the BAMPrimaryImport database.</span></span> <span data-ttu-id="a6745-122">Pour ce faire, modifiez le lot DTS de maintenance des données pour chaque activité pour insérer une étape pour sauvegarder la base de données BAMArchive avant la dernière étape du lot DTS, « Finalisation de l'archivage ».</span><span class="sxs-lookup"><span data-stu-id="a6745-122">To do this, modify the data maintenance DTS package for each activity to insert a step to back up the BAMArchive database before the last step in the DTS package, "End Archiving."</span></span>  
  
3.  <span data-ttu-id="a6745-123">Sauvegardez la base de données BAMAnalysis, puis la base de données BAMStarSchema.</span><span class="sxs-lookup"><span data-stu-id="a6745-123">Back up the BAMAnalysis database, and then the BAMStarSchema database.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6745-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a6745-124">See Also</span></span>  
 [<span data-ttu-id="a6745-125">Sauvegarde et restauration des bases de données BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="a6745-125">Backing Up and Restoring the BizTalk Server Databases</span></span>](../core/backing-up-and-restoring-the-biztalk-server-databases.md)