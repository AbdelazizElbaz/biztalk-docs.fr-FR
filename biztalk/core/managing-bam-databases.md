---
title: "Gestion des bases de données BAM | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing [BAM], databases
- databases [BAM], managing
- databases, BAM
ms.assetid: ce3c472e-2da1-4d67-816a-befe4ded20d9
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1dbe8cdb2c7806ab62b67db80c4741d64560fba9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="managing-bam-databases"></a><span data-ttu-id="263b9-102">Gestion des bases de données BAM</span><span class="sxs-lookup"><span data-stu-id="263b9-102">Managing BAM Databases</span></span>
<span data-ttu-id="263b9-103">Les administrateurs utilisent l'utilitaire de gestion de l'analyse BAM (bm.exe) pour configurer, gérer et mettre à jour les bases de données BAM.</span><span class="sxs-lookup"><span data-stu-id="263b9-103">Administrators use the BAM Management utility (bm.exe) to set up, manage, and update the BAM databases.</span></span> <span data-ttu-id="263b9-104">Cette section vous indique comment vous servir de l'utilitaire de gestion de l'analyse BAM pour accomplir ces tâches d'administration courantes (voir tableau suivant) pour les bases de données BAM.</span><span class="sxs-lookup"><span data-stu-id="263b9-104">This section shows you how to use the BAM Management utility to perform these common administrator tasks for the BAM databases, which are described in the following table.</span></span>  
  
 <span data-ttu-id="263b9-105">Pour plus d’informations sur la sauvegarde et restauration des bases de données BAM, consultez [sauvegarde et restauration de BAM](../core/backing-up-and-restoring-bam.md).</span><span class="sxs-lookup"><span data-stu-id="263b9-105">For information about backing up and restoring the BAM databases, see [Backing Up and Restoring BAM](../core/backing-up-and-restoring-bam.md).</span></span>  
  
|<span data-ttu-id="263b9-106">Base de données</span><span class="sxs-lookup"><span data-stu-id="263b9-106">Database</span></span>|<span data-ttu-id="263b9-107">Nom par défaut de la base de données</span><span class="sxs-lookup"><span data-stu-id="263b9-107">Default database name</span></span>|<span data-ttu-id="263b9-108"> Description</span><span class="sxs-lookup"><span data-stu-id="263b9-108">Description</span></span>|  
|--------------|---------------------------|-----------------|  
|<span data-ttu-id="263b9-109">Base de données d'importation principale BAM</span><span class="sxs-lookup"><span data-stu-id="263b9-109">BAM Primary Import database</span></span>|<span data-ttu-id="263b9-110">BAMPrimaryImport</span><span class="sxs-lookup"><span data-stu-id="263b9-110">BAMPrimaryImport</span></span>|<span data-ttu-id="263b9-111">Base de données ou l'analyse BAM collecte les données de suivi brutes.</span><span class="sxs-lookup"><span data-stu-id="263b9-111">Where BAM collects raw tracking data.</span></span>|  
|<span data-ttu-id="263b9-112">Base de données de l'application des services de notification BAM</span><span class="sxs-lookup"><span data-stu-id="263b9-112">BAM Notification Services Application database</span></span>|<span data-ttu-id="263b9-113">BAMAlertsApplication</span><span class="sxs-lookup"><span data-stu-id="263b9-113">BAMAlertsApplication</span></span>|<span data-ttu-id="263b9-114">Contient des informations d'alerte relatives aux notifications BAM.</span><span class="sxs-lookup"><span data-stu-id="263b9-114">Contains alert information for BAM notifications.</span></span> <span data-ttu-id="263b9-115">Par exemple, lorsque vous créez une alerte à partir du portail BAM, des entrées spécifiant les conditions et les événements auxquels l'alerte se rapporte ainsi que des éléments de données relatifs à l'alerte sont insérés dans la base de données.</span><span class="sxs-lookup"><span data-stu-id="263b9-115">For example, when you create an alert using the BAM portal, entries are inserted in the database specifying the conditions and events to which the alert pertains, as well as other supporting data items for the alert.</span></span>|  
|<span data-ttu-id="263b9-116">Base de données de l'instance des services de notification BAM</span><span class="sxs-lookup"><span data-stu-id="263b9-116">BAM Notification Services Instance database</span></span>|<span data-ttu-id="263b9-117">BAMAlertsNSMain</span><span class="sxs-lookup"><span data-stu-id="263b9-117">BAMAlertsNSMain</span></span>|<span data-ttu-id="263b9-118">Contient des informations d'instance précisant la manière dont les services de notification se connectent au système contrôlé par l'analyse BAM.</span><span class="sxs-lookup"><span data-stu-id="263b9-118">Contains instance information specifying how the notification services connect to the system that BAM is monitoring.</span></span>|  
|<span data-ttu-id="263b9-119">Base de données de schémas en étoile BAM</span><span class="sxs-lookup"><span data-stu-id="263b9-119">BAM Star Schema database</span></span>|<span data-ttu-id="263b9-120">BAMStarSchema</span><span class="sxs-lookup"><span data-stu-id="263b9-120">BAMStarSchema</span></span>|<span data-ttu-id="263b9-121">Contient le tableau intermédiaire et les tables de mesures et de dimensions.</span><span class="sxs-lookup"><span data-stu-id="263b9-121">Contains the staging table, and the measure and dimension tables.</span></span>|  
|<span data-ttu-id="263b9-122">Base de données d'analyse BAM</span><span class="sxs-lookup"><span data-stu-id="263b9-122">BAM Analysis database</span></span>|<span data-ttu-id="263b9-123">BAMAnalysis</span><span class="sxs-lookup"><span data-stu-id="263b9-123">BAMAnalysis</span></span>|<span data-ttu-id="263b9-124">Contient les cubes OLAP d'analyse BAM pour les analyses en ligne et hors ligne.</span><span class="sxs-lookup"><span data-stu-id="263b9-124">Contains BAM OLAP cubes for both online and offline analysis.</span></span>|  
|<span data-ttu-id="263b9-125">Base de données des archives de l'analyse BAM</span><span class="sxs-lookup"><span data-stu-id="263b9-125">BAM Archive database</span></span>|<span data-ttu-id="263b9-126">BAMArchive</span><span class="sxs-lookup"><span data-stu-id="263b9-126">BAMArchive</span></span>|<span data-ttu-id="263b9-127">Archive d'anciennes données d'activité d'entreprise.</span><span class="sxs-lookup"><span data-stu-id="263b9-127">Archives old business activity data.</span></span> <span data-ttu-id="263b9-128">Vous pouvez créer une base de données des archives de l'analyse BAM pour réduire la quantité de données d'activité d'entreprise accumulées dans la base de données d'importation principale BAM.</span><span class="sxs-lookup"><span data-stu-id="263b9-128">You can create a BAM Archive database to minimize the accumulation of business activity data in the BAM Primary Import database.</span></span>|  
  
## <a name="in-this-section"></a><span data-ttu-id="263b9-129">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="263b9-129">In This Section</span></span>  
  
-   [<span data-ttu-id="263b9-130">L’archivage des données de base de données d’importation principale</span><span class="sxs-lookup"><span data-stu-id="263b9-130">Archiving Primary Import Database Data</span></span>](../core/archiving-primary-import-database-data.md)  
  
-   [<span data-ttu-id="263b9-131">Création d’une vue partitionnée dans la base de données d’archivage</span><span class="sxs-lookup"><span data-stu-id="263b9-131">Creating a Partitioned View in the Archiving Database</span></span>](../core/creating-a-partitioned-view-in-the-archiving-database.md)  
  
-   [<span data-ttu-id="263b9-132">Planification de SQL Server Integration Services Packages</span><span class="sxs-lookup"><span data-stu-id="263b9-132">Scheduling SQL Server Integration Services Packages</span></span>](../core/scheduling-sql-server-integration-services-packages.md)  
  
-   [<span data-ttu-id="263b9-133">Procédure : configurer des bases de données BAM à l’aide de l’utilitaire de gestion BAM</span><span class="sxs-lookup"><span data-stu-id="263b9-133">How to Set Up the BAM Databases Using the BAM Management Utility</span></span>](../core/how-to-set-up-the-bam-databases-using-the-bam-management-utility.md)  
  
-   [<span data-ttu-id="263b9-134">Comment récupérer le fichier de Configuration BAM à l’aide de l’utilitaire de gestion BAM</span><span class="sxs-lookup"><span data-stu-id="263b9-134">How to Retrieve the BAM Configuration File Using the BAM Management Utility</span></span>](../core/how-to-retrieve-the-bam-configuration-file-using-the-bam-management-utility.md)  
  
-   [<span data-ttu-id="263b9-135">Comment mettre à jour la Configuration BAM à l’aide de l’utilitaire de gestion BAM</span><span class="sxs-lookup"><span data-stu-id="263b9-135">How to Update the BAM Configuration Using the BAM Management Utility</span></span>](../core/how-to-update-the-bam-configuration-using-the-bam-management-utility.md)  
  
-   [<span data-ttu-id="263b9-136">Comment référencer des bases de données importation principale BAM supplémentaires</span><span class="sxs-lookup"><span data-stu-id="263b9-136">How to Reference Additional BAM Primary Import Databases</span></span>](../core/how-to-reference-additional-bam-primary-import-databases.md)  
  
-   [<span data-ttu-id="263b9-137">Comment désactiver une référence de base de données d’importation principale BAM</span><span class="sxs-lookup"><span data-stu-id="263b9-137">How to Disable a BAM Primary Import Database Reference</span></span>](../core/how-to-disable-a-bam-primary-import-database-reference.md)  
  
-   [<span data-ttu-id="263b9-138">Comment répertorier toutes les bases de données référencées</span><span class="sxs-lookup"><span data-stu-id="263b9-138">How to List All Referenced Databases</span></span>](../core/how-to-list-all-referenced-databases.md)  
  
-   [<span data-ttu-id="263b9-139">Comment supprimer des Instances d’activité incomplètes</span><span class="sxs-lookup"><span data-stu-id="263b9-139">How to Remove Incomplete Activity Instances</span></span>](../core/how-to-remove-incomplete-activity-instances.md)  
  
-   [<span data-ttu-id="263b9-140">Comment mettre à jour la Configuration après une sauvegarde et restauration de l’utilitaire BAM Management</span><span class="sxs-lookup"><span data-stu-id="263b9-140">How to Update the BAM Management Utility Configuration After a Backup and Restore</span></span>](../core/update-the-bam-management-utility-configuration-after-a-backup-and-restore.md)  
  
-   [<span data-ttu-id="263b9-141">L’intégration BAM avec SQL Server Reporting Services</span><span class="sxs-lookup"><span data-stu-id="263b9-141">How to Integrate BAM with SQL Server Reporting Services</span></span>](../core/how-to-integrate-bam-with-sql-server-reporting-services.md)  
  
## <a name="see-also"></a><span data-ttu-id="263b9-142">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="263b9-142">See Also</span></span>  
 [<span data-ttu-id="263b9-143">La gestion BAM</span><span class="sxs-lookup"><span data-stu-id="263b9-143">Managing BAM</span></span>](../core/managing-bam.md)