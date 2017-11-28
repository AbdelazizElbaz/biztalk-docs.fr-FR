---
title: "Dimension données | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Data dimension [BAM]
- aggregations [BAM], data dimensions
ms.assetid: 07b5e56a-4fd5-4c88-a98a-758e514d0621
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b7138cf31a9cb86a9ba949142129ac5c906754b1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="data-dimension"></a><span data-ttu-id="6e4e7-102">Dimension Données</span><span class="sxs-lookup"><span data-stu-id="6e4e7-102">Data Dimension</span></span>
<span data-ttu-id="6e4e7-103">Définir une dimension de données permet d'utiliser la valeur de certains éléments de texte de l'activité BAM dans des lignes ou des colonnes.</span><span class="sxs-lookup"><span data-stu-id="6e4e7-103">Defining a data dimension allows the value of some text items in the BAM activity to be used on rows or columns.</span></span> <span data-ttu-id="6e4e7-104">Par exemple, une dimension de données nommée Produit peut être utilisée pour créer le tableau suivant :</span><span class="sxs-lookup"><span data-stu-id="6e4e7-104">For example a data dimension named Product can be used to create the following table:</span></span>  
  
|<span data-ttu-id="6e4e7-105">Product</span><span class="sxs-lookup"><span data-stu-id="6e4e7-105">Product</span></span>|<span data-ttu-id="6e4e7-106">Compter</span><span class="sxs-lookup"><span data-stu-id="6e4e7-106">Count</span></span>|  
|-------------|-----------|  
|<span data-ttu-id="6e4e7-107">Raquettes de tennis</span><span class="sxs-lookup"><span data-stu-id="6e4e7-107">Tennis racquets</span></span>|<span data-ttu-id="6e4e7-108">100</span><span class="sxs-lookup"><span data-stu-id="6e4e7-108">100</span></span>|  
|<span data-ttu-id="6e4e7-109">Ballons de football</span><span class="sxs-lookup"><span data-stu-id="6e4e7-109">Soccer balls</span></span>|<span data-ttu-id="6e4e7-110">200</span><span class="sxs-lookup"><span data-stu-id="6e4e7-110">200</span></span>|  
  
 <span data-ttu-id="6e4e7-111">De même, plusieurs dimensions de données peuvent être définies dans l'Assistant Vue BAM.</span><span class="sxs-lookup"><span data-stu-id="6e4e7-111">Also, more than one data dimension can be defined in the BAM view wizard.</span></span> <span data-ttu-id="6e4e7-112">Par exemple, définissez une dimension de données nommée **emplacement** avec les niveaux **état** et **Ville** peut être utilisé pour créer le tableau suivant :</span><span class="sxs-lookup"><span data-stu-id="6e4e7-112">For example, defining a data dimension named **Location** with levels for **State** and **City** can be used to create the following table:</span></span>  
  
|||||  
|-|-|-|-|  
||<span data-ttu-id="6e4e7-113">California</span><span class="sxs-lookup"><span data-stu-id="6e4e7-113">California</span></span>||<span data-ttu-id="6e4e7-114">Washington</span><span class="sxs-lookup"><span data-stu-id="6e4e7-114">Washington</span></span>|  
||<span data-ttu-id="6e4e7-115">Los Angeles</span><span class="sxs-lookup"><span data-stu-id="6e4e7-115">Los Angeles</span></span>|<span data-ttu-id="6e4e7-116">San Francisco</span><span class="sxs-lookup"><span data-stu-id="6e4e7-116">San Francisco</span></span>|<span data-ttu-id="6e4e7-117">Seattle</span><span class="sxs-lookup"><span data-stu-id="6e4e7-117">Seattle</span></span>|  
|<span data-ttu-id="6e4e7-118">Raquettes de tennis</span><span class="sxs-lookup"><span data-stu-id="6e4e7-118">Tennis racquets</span></span>|<span data-ttu-id="6e4e7-119">50</span><span class="sxs-lookup"><span data-stu-id="6e4e7-119">50</span></span>|<span data-ttu-id="6e4e7-120">20</span><span class="sxs-lookup"><span data-stu-id="6e4e7-120">20</span></span>|<span data-ttu-id="6e4e7-121">30</span><span class="sxs-lookup"><span data-stu-id="6e4e7-121">30</span></span>|  
|<span data-ttu-id="6e4e7-122">Ballons de football</span><span class="sxs-lookup"><span data-stu-id="6e4e7-122">Soccer balls</span></span>|<span data-ttu-id="6e4e7-123">130</span><span class="sxs-lookup"><span data-stu-id="6e4e7-123">130</span></span>|<span data-ttu-id="6e4e7-124">50</span><span class="sxs-lookup"><span data-stu-id="6e4e7-124">50</span></span>|<span data-ttu-id="6e4e7-125">20</span><span class="sxs-lookup"><span data-stu-id="6e4e7-125">20</span></span>|  
  
 <span data-ttu-id="6e4e7-126">Dans ce tableau, la dimension Produit a été utilisée sur les lignes et la dimension Lieu sur les colonnes.</span><span class="sxs-lookup"><span data-stu-id="6e4e7-126">In this table, the Product dimension was used as the rows, and the Location dimension was used as the columns.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e4e7-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6e4e7-127">See Also</span></span>  
 <span data-ttu-id="6e4e7-128">[Dimension de temps](../core/time-dimension.md) </span><span class="sxs-lookup"><span data-stu-id="6e4e7-128">[Time Dimension](../core/time-dimension.md) </span></span>  
 <span data-ttu-id="6e4e7-129">[Dimension de progression](../core/progress-dimension.md) </span><span class="sxs-lookup"><span data-stu-id="6e4e7-129">[Progress Dimension](../core/progress-dimension.md) </span></span>  
 <span data-ttu-id="6e4e7-130">[Dimension de plage numérique](../core/numeric-range-dimension.md) </span><span class="sxs-lookup"><span data-stu-id="6e4e7-130">[Numeric Range Dimension](../core/numeric-range-dimension.md) </span></span>  
 [<span data-ttu-id="6e4e7-131">Définition des Dimensions</span><span class="sxs-lookup"><span data-stu-id="6e4e7-131">Defining Dimensions</span></span>](../core/defining-dimensions.md)