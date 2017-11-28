---
title: "Agrégations planifiées | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BAM, aggregations
- scheduling, aggregations [BAM]
- aggregations [BAM], scheduling
ms.assetid: 4e2da2eb-b1fc-4b27-98d6-564e6df719e1
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0cf2558b046d53deb6036553c5206beebd4d80ab
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="scheduled-aggregations"></a><span data-ttu-id="4bcef-102">Agrégations planifiées</span><span class="sxs-lookup"><span data-stu-id="4bcef-102">Scheduled Aggregations</span></span>
<span data-ttu-id="4bcef-103">Dans le composant BAM, les agrégations planifiées reposent sur des cubes OLAP générés de façon dynamique et sur des lots DTS (Data Transformation Services).</span><span class="sxs-lookup"><span data-stu-id="4bcef-103">BAM bases scheduled aggregations on dynamically generated OLAP cubes and Data Transformation Services (DTS) packages.</span></span> <span data-ttu-id="4bcef-104">Les données des agrégations planifiées constituent une capture instantanée de vos activités d'entreprise lorsque vous démarrez le lot DTS.</span><span class="sxs-lookup"><span data-stu-id="4bcef-104">The data in scheduled aggregations represents a snapshot of your business activities when you start your DTS package.</span></span> <span data-ttu-id="4bcef-105">Pour ce faire, la première étape du lot DTS pour l’analyse est un appel à la procédure stockée **bam_Metadata_BeginAnalysis** capable d’extraire un instantané consistant en :</span><span class="sxs-lookup"><span data-stu-id="4bcef-105">To achieve this, the first step of the DTS package for analysis is a call to the stored procedure **bam_Metadata_BeginAnalysis** that will retrieve a snapshot consisting of:</span></span>  
  
-   <span data-ttu-id="4bcef-106">une capture instantanée de toutes les instances d'activité en cours ;</span><span class="sxs-lookup"><span data-stu-id="4bcef-106">A snapshot copy of all activity instances in progress</span></span>  
  
-   <span data-ttu-id="4bcef-107">une fenêtre incrémentielle des instances d'activité terminées entre le moment où vous avez lancé l'exécution du lot DTS pour la dernière fois et le moment de la capture instantanée.</span><span class="sxs-lookup"><span data-stu-id="4bcef-107">A view that represents an incremental window on the completed activity instances from the moment that you ran the DTS package for the last time to the moment of the snapshot</span></span>  
  
 <span data-ttu-id="4bcef-108">Pour obtenir ce résultat, le composant BAM applique un verrou exclusif sur le stockage d'activité pendant un cours instant afin d'empêcher l'écriture des données dans ce même temps.</span><span class="sxs-lookup"><span data-stu-id="4bcef-108">BAM achieves this by taking an exclusive lock on the Activity Storage for a very short time, thus preventing any data writing at the same time.</span></span> <span data-ttu-id="4bcef-109">Une fois la capture instantanée extraite par le composant BAM, le lot DTS peut mettre du temps à s'exécuter mais durant ce processus, le composant BAM ignore toute nouvelle donnée.</span><span class="sxs-lookup"><span data-stu-id="4bcef-109">Once BAM takes the snapshot, the DTS package might take a long time to run, but BAM will ignore any new data that arrives during the processing.</span></span> <span data-ttu-id="4bcef-110">Le schéma ci-dessous illustre cette activité :</span><span class="sxs-lookup"><span data-stu-id="4bcef-110">The following figure illustrates this activity:</span></span>  
  
 ![](../core/media/ebiz-prog-bam-data-maint-fig9.gif "ebiz_prog_bam_data_maint_fig9")  
<span data-ttu-id="4bcef-111">Agrégations planifiées BAM</span><span class="sxs-lookup"><span data-stu-id="4bcef-111">BAM Scheduled Aggregations</span></span>  
  
 <span data-ttu-id="4bcef-112">Dans ce schéma, le composant BAM déplace des données entre les instances d'activité terminées et le cube OLAP des instances terminées</span><span class="sxs-lookup"><span data-stu-id="4bcef-112">In the figure, BAM moves data about the completed activity instances to the Completed Instances OLAP cube.</span></span> <span data-ttu-id="4bcef-113">et traite le cube de façon incrémentielle.</span><span class="sxs-lookup"><span data-stu-id="4bcef-113">BAM incrementally processes this cube.</span></span>  
  
 <span data-ttu-id="4bcef-114">Dans le même temps, il déplace les données entre les activités en cours et le cube des instances actives, traité dans son intégralité par le lot DTS.</span><span class="sxs-lookup"><span data-stu-id="4bcef-114">At the same time, BAM moves the data about the activities still in progress to the Active Instances cube, which the DTS package fully processes.</span></span> <span data-ttu-id="4bcef-115">Cela est possible dans la mesure ou le composant BAM considère que pour un instant donné, seul un nombre réduit d'activités est en cours de processus.</span><span class="sxs-lookup"><span data-stu-id="4bcef-115">This is acceptable, because BAM assumes that only a relatively small number of activities are in progress at any given moment.</span></span>  
  
 <span data-ttu-id="4bcef-116">Les données destinées aux agrégations planifiées sont disponibles dans un cube virtuel permettant d'effacer la différence entre les activités terminées et les activités en cours.</span><span class="sxs-lookup"><span data-stu-id="4bcef-116">Data for the scheduled aggregations is available from a virtual cube that hides the difference between the completed and current activities.</span></span> <span data-ttu-id="4bcef-117">Pour plus d’informations, consultez [interrogation des données agrégées planifiées](../core/querying-scheduled-aggregated-data.md).</span><span class="sxs-lookup"><span data-stu-id="4bcef-117">For more information, see [Querying Scheduled Aggregated Data](../core/querying-scheduled-aggregated-data.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4bcef-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4bcef-118">See Also</span></span>  
 [<span data-ttu-id="4bcef-119">Qu’est une agrégation ?</span><span class="sxs-lookup"><span data-stu-id="4bcef-119">What Is an Aggregation?</span></span>](../core/what-is-an-aggregation.md)