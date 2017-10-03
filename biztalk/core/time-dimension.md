---
title: Dimension de temps | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Time dimension [BAM]
- aggregations [BAM], Time dimension
ms.assetid: 8f83b758-09a1-4efb-ae0e-32753f56c4e4
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 418afdc5b7507aba9a564628341c10495b2a740a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="time-dimension"></a><span data-ttu-id="4a743-102">Dimension de temps</span><span class="sxs-lookup"><span data-stu-id="4a743-102">Time Dimension</span></span>
<span data-ttu-id="4a743-103">La dimension de temps permet de créer des agrégations temporelles.</span><span class="sxs-lookup"><span data-stu-id="4a743-103">The time dimension allows aggregations to be created with respect to time.</span></span> <span data-ttu-id="4a743-104">Par exemple, une dimension de temps peut être utilisée pour créer le tableau suivant :</span><span class="sxs-lookup"><span data-stu-id="4a743-104">For example a time dimension can be used to create the following table:</span></span>  
  
|<span data-ttu-id="4a743-105">Année</span><span class="sxs-lookup"><span data-stu-id="4a743-105">Year</span></span>|<span data-ttu-id="4a743-106">Mois</span><span class="sxs-lookup"><span data-stu-id="4a743-106">Month</span></span>|<span data-ttu-id="4a743-107">Compter</span><span class="sxs-lookup"><span data-stu-id="4a743-107">Count</span></span>|  
|----------|-----------|-----------|  
|<span data-ttu-id="4a743-108">2003</span><span class="sxs-lookup"><span data-stu-id="4a743-108">2003</span></span>|<span data-ttu-id="4a743-109">Janvier</span><span class="sxs-lookup"><span data-stu-id="4a743-109">January</span></span>|<span data-ttu-id="4a743-110">120</span><span class="sxs-lookup"><span data-stu-id="4a743-110">120</span></span>|  
||<span data-ttu-id="4a743-111">February</span><span class="sxs-lookup"><span data-stu-id="4a743-111">February</span></span>|<span data-ttu-id="4a743-112">230</span><span class="sxs-lookup"><span data-stu-id="4a743-112">230</span></span>|  
||<span data-ttu-id="4a743-113">Mars</span><span class="sxs-lookup"><span data-stu-id="4a743-113">March</span></span>|<span data-ttu-id="4a743-114">350</span><span class="sxs-lookup"><span data-stu-id="4a743-114">350</span></span>|  
||<span data-ttu-id="4a743-115">avril</span><span class="sxs-lookup"><span data-stu-id="4a743-115">April</span></span>|<span data-ttu-id="4a743-116">280</span><span class="sxs-lookup"><span data-stu-id="4a743-116">280</span></span>|  
  
 <span data-ttu-id="4a743-117">La dimension de temps peut être combinée avec n’importe quelle autre dimension.</span><span class="sxs-lookup"><span data-stu-id="4a743-117">The time dimension can be combined with any other dimension.</span></span> <span data-ttu-id="4a743-118">Par exemple, vous pouvez utiliser la dimension de temps sur les lignes et la dimension de données sur les colonnes pour créer le tableau suivant :</span><span class="sxs-lookup"><span data-stu-id="4a743-118">For example, you can use the time dimension on rows and the data dimension on columns to create the following table:</span></span>  
  
|||<span data-ttu-id="4a743-119">Raquettes de tennis</span><span class="sxs-lookup"><span data-stu-id="4a743-119">Tennis racquets</span></span>|<span data-ttu-id="4a743-120">Ballons de football</span><span class="sxs-lookup"><span data-stu-id="4a743-120">Soccer balls</span></span>|  
|------|------|---------------------|------------------|  
||<span data-ttu-id="4a743-121">Janvier</span><span class="sxs-lookup"><span data-stu-id="4a743-121">January</span></span>|<span data-ttu-id="4a743-122">50</span><span class="sxs-lookup"><span data-stu-id="4a743-122">50</span></span>|<span data-ttu-id="4a743-123">70</span><span class="sxs-lookup"><span data-stu-id="4a743-123">70</span></span>|  
||<span data-ttu-id="4a743-124">February</span><span class="sxs-lookup"><span data-stu-id="4a743-124">February</span></span>|<span data-ttu-id="4a743-125">120</span><span class="sxs-lookup"><span data-stu-id="4a743-125">120</span></span>|<span data-ttu-id="4a743-126">110</span><span class="sxs-lookup"><span data-stu-id="4a743-126">110</span></span>|  
||<span data-ttu-id="4a743-127">Mars</span><span class="sxs-lookup"><span data-stu-id="4a743-127">March</span></span>|<span data-ttu-id="4a743-128">300</span><span class="sxs-lookup"><span data-stu-id="4a743-128">300</span></span>|<span data-ttu-id="4a743-129">50</span><span class="sxs-lookup"><span data-stu-id="4a743-129">50</span></span>|  
||<span data-ttu-id="4a743-130">avril</span><span class="sxs-lookup"><span data-stu-id="4a743-130">April</span></span>|<span data-ttu-id="4a743-131">220</span><span class="sxs-lookup"><span data-stu-id="4a743-131">220</span></span>|<span data-ttu-id="4a743-132">60</span><span class="sxs-lookup"><span data-stu-id="4a743-132">60</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4a743-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4a743-133">See Also</span></span>  
 <span data-ttu-id="4a743-134">[Dimension de plage numérique](../core/numeric-range-dimension.md) </span><span class="sxs-lookup"><span data-stu-id="4a743-134">[Numeric Range Dimension](../core/numeric-range-dimension.md) </span></span>  
 <span data-ttu-id="4a743-135">[Dimension de progression](../core/progress-dimension.md) </span><span class="sxs-lookup"><span data-stu-id="4a743-135">[Progress Dimension](../core/progress-dimension.md) </span></span>  
 <span data-ttu-id="4a743-136">[Dimension données](../core/data-dimension.md) </span><span class="sxs-lookup"><span data-stu-id="4a743-136">[Data Dimension](../core/data-dimension.md) </span></span>  
 [<span data-ttu-id="4a743-137">Définition des Dimensions</span><span class="sxs-lookup"><span data-stu-id="4a743-137">Defining Dimensions</span></span>](../core/defining-dimensions.md)