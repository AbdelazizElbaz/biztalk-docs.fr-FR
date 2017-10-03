---
title: Bouclage de table et de fonctoids Extracteur de Table | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2907aada-f11a-485c-85c8-03092803ccf7
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 02d4433255ac00d51c88b45bd1a2b5205bd1c735
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="table-looping-and-table-extractor-functoids"></a><span data-ttu-id="26a4c-102">Bouclage de table et de fonctoids Extracteur de Table</span><span class="sxs-lookup"><span data-stu-id="26a4c-102">Table Looping and Table Extractor Functoids</span></span>

## <a name="overview"></a><span data-ttu-id="26a4c-103">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="26a4c-103">Overview</span></span>
<span data-ttu-id="26a4c-104">Dans un mappage, vous avez généralement une structure dans le message d'instance de sortie pour chaque structure du message d’instance d'entrée.</span><span class="sxs-lookup"><span data-stu-id="26a4c-104">In a map, you commonly have one structure in the output instance message for each structure in the input instance message.</span></span> <span data-ttu-id="26a4c-105">Toutefois, dans certains cas, vous avez besoin qu’une structure d’instance d’entrée produise plusieurs structures d’instance de sortie.</span><span class="sxs-lookup"><span data-stu-id="26a4c-105">However, there are cases when you need an input instance structure to produce multiple output instance structures.</span></span> <span data-ttu-id="26a4c-106">Le bouclage piloté par la table vous permet de créer des mappages générant de telles structures multiples.</span><span class="sxs-lookup"><span data-stu-id="26a4c-106">Table-driven looping enables you to create maps generating such multiple structures.</span></span>  
  
 <span data-ttu-id="26a4c-107">Utilisations de bouclage piloté par les table le **bouclage de Table** fonctoid et **extracteur de Table** fonctoid.</span><span class="sxs-lookup"><span data-stu-id="26a4c-107">Table-driven looping uses the **Table Looping** functoid and the **Table Extractor** functoid.</span></span> <span data-ttu-id="26a4c-108">Le **bouclage de Table** le fonctoid ne comporte une table interne que vous configurez.</span><span class="sxs-lookup"><span data-stu-id="26a4c-108">The **Table Looping** functoid has an internal table you configure.</span></span> <span data-ttu-id="26a4c-109">Pour chaque d’entrée d’enregistrement ou un champ, la **bouclage de Table** fonctoid génère les lignes de la table, une à la fois.</span><span class="sxs-lookup"><span data-stu-id="26a4c-109">For each input record or field, the **Table Looping** functoid outputs the rows of the table, one at a time.</span></span> <span data-ttu-id="26a4c-110">Par exemple, s’il existe dix enregistrements dans le message d’instance d’entrée et deux lignes dans la table interne de la **bouclage de Table**, le fonctoid génère un total de vingt lignes, deux pour chacun des dix enregistrements.</span><span class="sxs-lookup"><span data-stu-id="26a4c-110">For example, if there are ten records in the input instance message and two rows in the internal table of the **Table Looping**, the functoid outputs a total of twenty rows, two for each of the ten records.</span></span> <span data-ttu-id="26a4c-111">Le **extracteur de Table** fonctoid extrait l’élément désiré à partir d’une ligne et le transmet le message d’instance de sortie.</span><span class="sxs-lookup"><span data-stu-id="26a4c-111">The **Table Extractor** functoid extracts the desired item from a row and passes it on to the output instance message.</span></span>  
  
 <span data-ttu-id="26a4c-112">Pour plus d’informations, consultez la **référence du fonctoid Bouclage de Table** et **référence du fonctoid Extracteur de Table** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span><span class="sxs-lookup"><span data-stu-id="26a4c-112">For more details, see the **Table Looping Functoid Reference** and **Table Extractor Functoid Reference** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span>
  
## <a name="next-steps"></a><span data-ttu-id="26a4c-113">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="26a4c-113">Next steps</span></span>
  
-   [<span data-ttu-id="26a4c-114">Fonctoid Bouclage de table</span><span class="sxs-lookup"><span data-stu-id="26a4c-114">Table Looping Functoid</span></span>](../core/table-looping-functoid.md)  
  
-   [<span data-ttu-id="26a4c-115">Fonctoid Extracteur de table</span><span class="sxs-lookup"><span data-stu-id="26a4c-115">Table Extractor Functoid</span></span>](../core/table-extractor-functoid.md)  
  
-   [<span data-ttu-id="26a4c-116">Configuration de bouclage piloté par table</span><span class="sxs-lookup"><span data-stu-id="26a4c-116">Table-Driven Looping Configuration</span></span>](../core/table-driven-looping-configuration.md)  
  
-   [<span data-ttu-id="26a4c-117">Exemple de bouclage piloté par table</span><span class="sxs-lookup"><span data-stu-id="26a4c-117">Table-Driven Looping Example</span></span>](../core/table-driven-looping-example.md)