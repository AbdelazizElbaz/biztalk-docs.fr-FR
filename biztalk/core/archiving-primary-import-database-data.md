---
title: "L’archivage des données de base de données d’importation principale | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Primary Import database [BAM], archiving data
- archived data, BAM
- managing [BAM], archiving data
- data, archiving [BAM]
ms.assetid: 4a014a59-0578-41fa-9441-8b582f54bbe8
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c0fdfd55681fabd1b6cfc72f68b7e33150a121f2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="archiving-primary-import-database-data"></a><span data-ttu-id="ad1bb-102">Archivage des données dans la base de données d'importation principale</span><span class="sxs-lookup"><span data-stu-id="ad1bb-102">Archiving Primary Import Database Data</span></span>
<span data-ttu-id="ad1bb-103">En tant qu'administrateur, vous pouvez indiquer la fenêtre de temps destinée à l'archivage des données d'instance d'activité dans la base de données d'importation principale.</span><span class="sxs-lookup"><span data-stu-id="ad1bb-103">An administrator can specify the time window for archiving activity instance data in the primary import database.</span></span> <span data-ttu-id="ad1bb-104">Pour cela, utilisez les propriétés OnlineWindowTimeUnit et OnlineWindowTimeLength de la table BAM_Metadata_Activities dans la base de données d'importation principale BAM.</span><span class="sxs-lookup"><span data-stu-id="ad1bb-104">You use the OnlineWindowTimeUnit and OnlineWindowTimeLength properties in the BAM_Metadata_Activities table in the BAMPrimaryImport database.</span></span>  
  
 <span data-ttu-id="ad1bb-105">Si les utilisateurs des activités ont déployé plusieurs activités, vous pouvez attribuer une fenêtre de temps différente à chaque activité.</span><span class="sxs-lookup"><span data-stu-id="ad1bb-105">If business users have deployed multiple activities, you can specify a different time window for each activity.</span></span> <span data-ttu-id="ad1bb-106">Pour plus d’informations sur le déploiement des activités, consultez « Définition d’une activité d’entreprise » dans *Guide d’utilisation d’informations travailleurs*.</span><span class="sxs-lookup"><span data-stu-id="ad1bb-106">For information about deploying activities, see "Defining a Business Activity" in *Information Workers Users Guide*.</span></span>  
  
 <span data-ttu-id="ad1bb-107">Le tableau ci-après décrit les valeurs que vous pouvez définir pour les propriétés OnlineWindowTimeUnit et OnlineWindowTimeLength.</span><span class="sxs-lookup"><span data-stu-id="ad1bb-107">The following table describes the values you can use for OnlineWindowTimeUnit and OnlineWindowTimeLength.</span></span>  
  
|<span data-ttu-id="ad1bb-108">Propriété</span><span class="sxs-lookup"><span data-stu-id="ad1bb-108">Property</span></span>|<span data-ttu-id="ad1bb-109">Valeur</span><span class="sxs-lookup"><span data-stu-id="ad1bb-109">Value</span></span>|  
|--------------|-----------|  
|<span data-ttu-id="ad1bb-110">OnlineWindowTimeUnit</span><span class="sxs-lookup"><span data-stu-id="ad1bb-110">OnlineWindowTimeUnit</span></span>|<span data-ttu-id="ad1bb-111">Cette propriété peut être : mois, jour, heure ou minute.</span><span class="sxs-lookup"><span data-stu-id="ad1bb-111">This property can be: month, day, hour, or minute.</span></span> <span data-ttu-id="ad1bb-112">La valeur par défaut de cette propriété est « mois ».</span><span class="sxs-lookup"><span data-stu-id="ad1bb-112">The default value of this property is month.</span></span>|  
|<span data-ttu-id="ad1bb-113">OnlineWindowTimeLength</span><span class="sxs-lookup"><span data-stu-id="ad1bb-113">OnlineWindowTimeLength</span></span>|<span data-ttu-id="ad1bb-114">Cette propriété doit être définie par un entier.</span><span class="sxs-lookup"><span data-stu-id="ad1bb-114">This property must be an integer.</span></span> <span data-ttu-id="ad1bb-115">La valeur par défaut de cette propriété est 6.</span><span class="sxs-lookup"><span data-stu-id="ad1bb-115">The default value of this property is 6.</span></span>|  
  
 <span data-ttu-id="ad1bb-116">Le composant BAM retire des données de la base de données d'importation principale BAM par partition. Cette opération se produit lorsqu'une partition se trouve en dehors de la fenêtre en ligne spécifiée (heure actuelle - OnlineWindowTimeLength de OnlineWindowTimeUnit).</span><span class="sxs-lookup"><span data-stu-id="ad1bb-116">BAM moves data out of the BAM primary import database by partition, when the partition is older than the online window (current time - OnlineWindowTimeLength of OnlineWindowTimeUnit).</span></span> <span data-ttu-id="ad1bb-117">Par exemple, si OnlineWindowTimeLength = 5 et OnlineWindowTimeUnit = jour, les partitions datant de plus de 5 jours sont supprimées.</span><span class="sxs-lookup"><span data-stu-id="ad1bb-117">For example, for OnlineWindowTimeLength = 5 and OnlineWindowTimeUnit = day, partitions older than 5 days are removed.</span></span>  
  
 <span data-ttu-id="ad1bb-118">Le composant BAM place alors les données d'instance d'activité dans la base de données des archives BAM.</span><span class="sxs-lookup"><span data-stu-id="ad1bb-118">BAM moves archived activity instance data into the BAM archiving database.</span></span> <span data-ttu-id="ad1bb-119">Indiquez cette base de données pendant la configuration de l'analyse BAM de BizTalk.</span><span class="sxs-lookup"><span data-stu-id="ad1bb-119">You specify the BAM archiving database during BizTalk BAM Configuration.</span></span> <span data-ttu-id="ad1bb-120">Pour plus d’informations sur la configuration BAM de BizTalk, consultez [schéma de Configuration BAM](../core/bam-configuration-schema.md).</span><span class="sxs-lookup"><span data-stu-id="ad1bb-120">For information about BizTalk BAM configuration, see [BAM Configuration Schema](../core/bam-configuration-schema.md).</span></span>  
  
 <span data-ttu-id="ad1bb-121">Le composant BAM n'archive pas les données d'instance d'activité si vous n'avez pas exécuté le lot DTS (Data Transformation Services) de mise à jour du cube BAM. Ce dernier traite les données d'instance dans le cube de l'activité.</span><span class="sxs-lookup"><span data-stu-id="ad1bb-121">BAM will not archive activity instance data if you have not run the BAM cube update Data Transformation Services (DTS) package, which processes the instance data into the activity cube.</span></span>  
  
 <span data-ttu-id="ad1bb-122">Pour plus d’informations sur l’exécution du lot DTS de maintenance de données BAM, consultez [lots DTS BAM](../core/bam-dts-packages.md).</span><span class="sxs-lookup"><span data-stu-id="ad1bb-122">For information about running the BAM data maintenance DTS package, see [BAM DTS Packages](../core/bam-dts-packages.md).</span></span>  
  
 <span data-ttu-id="ad1bb-123">Avec le temps, la taille de la base de données BAMArchive augmente à mesure que des données d'instance d'activité y sont ajoutées.</span><span class="sxs-lookup"><span data-stu-id="ad1bb-123">Over time the BAMArchive database will grow in size as activity instance data is added.</span></span> <span data-ttu-id="ad1bb-124">Bien qu'il n'existe aucune méthode simple pour tronquer une base de données entière, vous pouvez régulièrement tronquer le journal des transactions de la base de données afin de réduire les besoins de stockage, et procéder à la sauvegarde et à l'archivage de la base de données BAMArchive entière.</span><span class="sxs-lookup"><span data-stu-id="ad1bb-124">Although there is no straightforward way to truncate an entire database, you can periodically truncate the database transaction log to reduce the storage requirements, and you can periodically back up and archive the entire BAMArchive database.</span></span> <span data-ttu-id="ad1bb-125">Pour plus d'informations, consultez la rubrique « Troncation du journal des transactions » dans la documentation en ligne de SQL Server.</span><span class="sxs-lookup"><span data-stu-id="ad1bb-125">See “Truncating the transaction log” in SQL Server Books Online for more information.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad1bb-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ad1bb-126">See Also</span></span>  
 <span data-ttu-id="ad1bb-127">[Définition de la fenêtre de temps et les propriétés de tranche de temps](../core/defining-the-time-window-and-time-slice-properties.md) </span><span class="sxs-lookup"><span data-stu-id="ad1bb-127">[Defining the Time Window and Time Slice Properties](../core/defining-the-time-window-and-time-slice-properties.md) </span></span>  
 [<span data-ttu-id="ad1bb-128">Gestion de l’Infrastructure dynamique BAM</span><span class="sxs-lookup"><span data-stu-id="ad1bb-128">Managing the BAM Dynamic Infrastructure</span></span>](../core/managing-the-bam-dynamic-infrastructure.md)