---
title: "Dimension de plage numérique | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- aggregations [BAM], Numeric Range dimension
- Numeric Range dimension [BAM]
ms.assetid: a874ce44-b034-498f-ba58-114028dbef2c
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2fb6d4c21e0a207cfeec3e592569ca0f48f3badf
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="numeric-range-dimension"></a><span data-ttu-id="72df8-102">Dimension de la plage numérique</span><span class="sxs-lookup"><span data-stu-id="72df8-102">Numeric Range Dimension</span></span>
<span data-ttu-id="72df8-103">La dimension de plage numérique permet de classer les agrégations par catégories en fonction de noms conviviaux de plages données.</span><span class="sxs-lookup"><span data-stu-id="72df8-103">The numeric range dimension allows aggregations to be categorized based on friendly names of given ranges.</span></span> <span data-ttu-id="72df8-104">Par exemple, un analyste d'entreprise peut définir une dimension de plage numérique intitulée Taille du bon de commande, dotée des plages suivantes : Peu élevé pour les bons de commande d'un montant compris entre 0 et 100 €, Moyen pour ceux dont le montant est compris entre 100 et 1 000 € et Important pour ceux d'un montant supérieur à 1 000 €.</span><span class="sxs-lookup"><span data-stu-id="72df8-104">For example, a business analyst can define a numeric range dimension named PO Size with the ranges Small for purchase orders between 0-$100, Medium for purchase orders between $100 to $1,000, and Large for purchase orders exceeding $1,000.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="72df8-105">Si un montant de bon de commande n’est pas dans les plages définies, par exemple, un montant de bon de commande est inférieur à 0, et ensuite une ligne « hors limites » sera automatiquement créée par l’analyse BAM pour contenir les données d’out-of-range.</span><span class="sxs-lookup"><span data-stu-id="72df8-105">If a purchase order amount is not in the defined ranges, for example, a purchase order amount is less than 0, and then an "Out of range" row will be automatically created by BAM to accommodate the out-of-range data.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="72df8-106">Vous ne pouvez pas créer deux dimensions de plage numérique faisant référence au même alias de données.</span><span class="sxs-lookup"><span data-stu-id="72df8-106">You cannot create two numeric range dimensions that reference the same data alias.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72df8-107">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="72df8-107">See Also</span></span>  
 <span data-ttu-id="72df8-108">[Comment utiliser le tableau croisé dynamique](../core/how-to-use-the-pivottable.md) </span><span class="sxs-lookup"><span data-stu-id="72df8-108">[How to Use the PivotTable](../core/how-to-use-the-pivottable.md) </span></span>  
 <span data-ttu-id="72df8-109">[Dimension de progression](../core/progress-dimension.md) </span><span class="sxs-lookup"><span data-stu-id="72df8-109">[Progress Dimension](../core/progress-dimension.md) </span></span>  
 <span data-ttu-id="72df8-110">[Dimension données](../core/data-dimension.md) </span><span class="sxs-lookup"><span data-stu-id="72df8-110">[Data Dimension](../core/data-dimension.md) </span></span>  
 <span data-ttu-id="72df8-111">[Dimension de temps](../core/time-dimension.md) </span><span class="sxs-lookup"><span data-stu-id="72df8-111">[Time Dimension](../core/time-dimension.md) </span></span>  
 [<span data-ttu-id="72df8-112">Définition des Dimensions</span><span class="sxs-lookup"><span data-stu-id="72df8-112">Defining Dimensions</span></span>](../core/defining-dimensions.md)