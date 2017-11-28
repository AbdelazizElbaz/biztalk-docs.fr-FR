---
title: Fonctoid Extracteur de table | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Table Extractor functoids
- Table Extractor functoids, about Table Extractor functoids
ms.assetid: cb5f6f15-f4e1-46d3-846e-6e2664699b62
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 837762dcf1bd0814494f05712eb7d616cdfa7180
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="table-extractor-functoid"></a><span data-ttu-id="bc6c4-102">Fonctoid Extracteur de table</span><span class="sxs-lookup"><span data-stu-id="bc6c4-102">Table Extractor Functoid</span></span>
<span data-ttu-id="bc6c4-103">Le **extracteur de Table** fonctoid détermine les données à extraire de chaque ligne de la grille de bouclage en tant que le **bouclage de Table** fonctoid présente les lignes.</span><span class="sxs-lookup"><span data-stu-id="bc6c4-103">The **Table Extractor** functoid determines which data to extract from each row of the looping grid as the **Table Looping** functoid presents the rows.</span></span> <span data-ttu-id="bc6c4-104">Vous devez installer un **extracteur de Table** pour chaque champ de sortie.</span><span class="sxs-lookup"><span data-stu-id="bc6c4-104">You need one **Table Extractor** functoid for each output field.</span></span> <span data-ttu-id="bc6c4-105">Par exemple, supposez que votre message d'instance d'entrée a une adresse dans un seul format, mais que votre message d'instance de sortie a besoin de l'adresse dans deux formats dont chacun est marqué.</span><span class="sxs-lookup"><span data-stu-id="bc6c4-105">For example, suppose your input instance message had an address in a single format, but your output instance message needed the address in two formats with each format tagged.</span></span> <span data-ttu-id="bc6c4-106">Vous devez un **extracteur de Table** fonctoid de la balise et pour chaque élément de l’adresse.</span><span class="sxs-lookup"><span data-stu-id="bc6c4-106">Then you would need a **Table Extractor** functoid for the tag and for each element of the address.</span></span> <span data-ttu-id="bc6c4-107">Pour plus d’informations sur la configuration de la **extracteur de Table** fonctoid, consultez [Configuration de bouclage Table-Driven](../core/table-driven-looping-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="bc6c4-107">For more information about configuring the **Table Extractor** functoid, see [Table-Driven Looping Configuration](../core/table-driven-looping-configuration.md).</span></span> <span data-ttu-id="bc6c4-108">Consultez également [exemple de bouclage Table-Driven](../core/table-driven-looping-example.md).</span><span class="sxs-lookup"><span data-stu-id="bc6c4-108">Also see [Table-Driven Looping Example](../core/table-driven-looping-example.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc6c4-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bc6c4-109">See Also</span></span>  
 <span data-ttu-id="bc6c4-110">[Fonctoid Bouclage de table](../core/table-looping-functoid.md) </span><span class="sxs-lookup"><span data-stu-id="bc6c4-110">[Table Looping Functoid](../core/table-looping-functoid.md) </span></span>  
 <span data-ttu-id="bc6c4-111">[L’ajout de bouclage de Table et fonctoids Extracteur de Table à une carte](../core/how-to-add-table-looping-and-table-extractor-functoids-to-a-map.md) </span><span class="sxs-lookup"><span data-stu-id="bc6c4-111">[How to Add Table Looping and Table Extractor Functoids to a Map](../core/how-to-add-table-looping-and-table-extractor-functoids-to-a-map.md) </span></span>  
 <span data-ttu-id="bc6c4-112">[Fonctoids avancés](../core/advanced-functoids.md) </span><span class="sxs-lookup"><span data-stu-id="bc6c4-112">[Advanced Functoids](../core/advanced-functoids.md) </span></span>  
 <span data-ttu-id="bc6c4-113">[Fonctoid Index](../core/index-functoid.md) </span><span class="sxs-lookup"><span data-stu-id="bc6c4-113">[Index Functoid](../core/index-functoid.md) </span></span>  
 <span data-ttu-id="bc6c4-114">[Fonctoid Itération](../core/iteration-functoid.md) </span><span class="sxs-lookup"><span data-stu-id="bc6c4-114">[Iteration Functoid](../core/iteration-functoid.md) </span></span>  
 <span data-ttu-id="bc6c4-115">[Fonctoid Bouclage](../core/looping-functoid.md) </span><span class="sxs-lookup"><span data-stu-id="bc6c4-115">[Looping Functoid](../core/looping-functoid.md) </span></span>  
 [<span data-ttu-id="bc6c4-116">Fonctoid Nombre d’enregistrements</span><span class="sxs-lookup"><span data-stu-id="bc6c4-116">Record Count Functoid</span></span>](../core/record-count-functoid.md)