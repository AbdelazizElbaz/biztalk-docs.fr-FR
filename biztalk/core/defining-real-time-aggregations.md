---
title: "Définition des agrégations en temps réel | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- real-time data, aggregating
- aggregations [BAM], real-time data
ms.assetid: cb3d7124-1663-4af2-9540-4171cc51568a
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b2b2df32149f67a002a5a6281b6f1abd848523a6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="defining-real-time-aggregations"></a><span data-ttu-id="505d3-102">Définition des agrégations en temps réel</span><span class="sxs-lookup"><span data-stu-id="505d3-102">Defining Real-Time Aggregations</span></span>
<span data-ttu-id="505d3-103">Dans certains cas, le temps constituant un paramètre primordial pour des tranches déterminées d'agrégations multidimensionnelles, il est nécessaire de rendre ces agrégations disponibles en temps réel.</span><span class="sxs-lookup"><span data-stu-id="505d3-103">In some cases, specific slices of the multi-dimensional aggregations are so time- sensitive that you want them to be available in real time.</span></span> <span data-ttu-id="505d3-104">Supposons que votre entreprise vende des denrées périssables et que vous souhaitiez que l'agrégation des quantités de produits aux différentes étapes de la livraison soit disponible en temps réel.</span><span class="sxs-lookup"><span data-stu-id="505d3-104">For example, your business is selling perishable products and you want the aggregation of product quantity in different stages of delivery to be available in real time.</span></span> <span data-ttu-id="505d3-105">D'autre part, vous voulez disposer d'autres agrégations, comme celle de l'âge du consommateur moyen, mais uniquement à la fin du mois en vue d'une analyse Business Intelligence.</span><span class="sxs-lookup"><span data-stu-id="505d3-105">At the same time, you want other aggregations such as the age of your typical customers, but only at the end of the month for business intelligence analysis.</span></span>  
  
-   <span data-ttu-id="505d3-106">À l’aide de la **tableau croisé dynamique** barre d’outils, marquez le tableau croisé dynamique sélectionné comme une agrégation en temps réel (RTA), le cas échéant.</span><span class="sxs-lookup"><span data-stu-id="505d3-106">Using the **PivotTable** toolbar, mark the selected PivotTable as a real-time aggregation (RTA), if applicable.</span></span> <span data-ttu-id="505d3-107">Le type de données contenu dans le tableau croisé dynamique doit déterminer s'il doit être affiché en temps réel.</span><span class="sxs-lookup"><span data-stu-id="505d3-107">The type of data contained in the PivotTable should determine whether it needs to be viewed in real time.</span></span> <span data-ttu-id="505d3-108">Par exemple, un rapport effectuant le suivi heure par heure des commandes sur le Web doit être affiché en temps réel, tandis qu'un rapport qui effectue le suivi journalier des totaux des ventes ne nécessite pas un affichage en temps réel.</span><span class="sxs-lookup"><span data-stu-id="505d3-108">For example, a report that tracks hourly Web orders might need to viewed in real time, whereas a report that tracks daily sales totals would not be viewed in real time.</span></span>  
  
     ![](../core/media/ebiz-sdk-sample-bam12.gif "ebiz_sdk_sample_bam12")  
<span data-ttu-id="505d3-109">Bouton RTA</span><span class="sxs-lookup"><span data-stu-id="505d3-109">RTA button</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="505d3-110">Ne définissez pas plusieurs RTA utilisant une même activité BAM.</span><span class="sxs-lookup"><span data-stu-id="505d3-110">Do not define multiple RTAs that use the same BAM activity.</span></span> <span data-ttu-id="505d3-111">Si vous le faites, les données RTA seront incorrectes lors de l'archivage des données BAM.</span><span class="sxs-lookup"><span data-stu-id="505d3-111">If you do so, the RTA data will be incorrect when you archive the BAM data.</span></span>  
  
 <span data-ttu-id="505d3-112">Pour plus d'informations sur les tableaux croisés dynamiques, consultez l'aide en ligne d'Excel.</span><span class="sxs-lookup"><span data-stu-id="505d3-112">For more information about Pivot tables, see Excel online help.</span></span> <span data-ttu-id="505d3-113">Après avoir créé votre tableau croisé dynamique, vous pouvez afficher vos données BAM actives.</span><span class="sxs-lookup"><span data-stu-id="505d3-113">After you create your Pivot table, you can view your live BAM data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="505d3-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="505d3-114">See Also</span></span>  
 <span data-ttu-id="505d3-115">[Affichage des données BAM actives](../core/viewing-live-bam-data.md) </span><span class="sxs-lookup"><span data-stu-id="505d3-115">[Viewing Live BAM Data](../core/viewing-live-bam-data.md) </span></span>  
 <span data-ttu-id="505d3-116">[Dimension de progression](../core/progress-dimension.md) </span><span class="sxs-lookup"><span data-stu-id="505d3-116">[Progress Dimension](../core/progress-dimension.md) </span></span>  
 <span data-ttu-id="505d3-117">[Dimension données](../core/data-dimension.md) </span><span class="sxs-lookup"><span data-stu-id="505d3-117">[Data Dimension](../core/data-dimension.md) </span></span>  
 <span data-ttu-id="505d3-118">[Dimension de temps](../core/time-dimension.md) </span><span class="sxs-lookup"><span data-stu-id="505d3-118">[Time Dimension](../core/time-dimension.md) </span></span>  
 <span data-ttu-id="505d3-119">[Dimension de plage numérique](../core/numeric-range-dimension.md) </span><span class="sxs-lookup"><span data-stu-id="505d3-119">[Numeric Range Dimension](../core/numeric-range-dimension.md) </span></span>  
 [<span data-ttu-id="505d3-120">Définition des Dimensions</span><span class="sxs-lookup"><span data-stu-id="505d3-120">Defining Dimensions</span></span>](../core/defining-dimensions.md)