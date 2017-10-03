---
title: "Fonctoid déclarer | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e91dac06-f909-4fb2-8c87-828a3dfe2c27
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 03237c27e0e35642be197b549c8b0102d9350702
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="assert-functoid"></a><span data-ttu-id="44865-102">Fonctoid déclarer</span><span class="sxs-lookup"><span data-stu-id="44865-102">Assert Functoid</span></span>

## <a name="overview"></a><span data-ttu-id="44865-103">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="44865-103">Overview</span></span>
<span data-ttu-id="44865-104">Le **Assert** fonctoid génère une valeur de chaîne ou lève une exception basée sur une valeur booléenne.</span><span class="sxs-lookup"><span data-stu-id="44865-104">The **Assert** functoid either outputs a string value or throws an exception based on a Boolean value.</span></span> <span data-ttu-id="44865-105">Si vous combinez ce fonctoid avec un ou plusieurs de la **logiques** fonctoids, vous pouvez tester efficacement des hypothèses sur les conditions dans votre carte.</span><span class="sxs-lookup"><span data-stu-id="44865-105">If you combine this functoid with one or more of the **Logical** functoids, you can effectively test assumptions about conditions in your map.</span></span> <span data-ttu-id="44865-106">Par exemple, si vous disposez d’une carte qui attend des montants de commande fournisseur jamais à dépasser un seuil donné, vous pouvez tester la valeur de bon de commande à l’aide de la **supérieur à** fonctoid et connectez-la à la **Assert**fonctoid.</span><span class="sxs-lookup"><span data-stu-id="44865-106">For example, if you have a map that expects purchase order amounts never to exceed a certain threshold, you can test the purchase order value by using the **Greater Than** functoid and then connect it to the **Assert** functoid.</span></span> <span data-ttu-id="44865-107">Si le fonctoid logique retourne **True**, le **Assert** fonctoid lève une exception à l’aide d’une chaîne que vous fournissez.</span><span class="sxs-lookup"><span data-stu-id="44865-107">If the logical functoid returns **True**, the **Assert** functoid will throw an exception using a string you provide.</span></span>  
  
 <span data-ttu-id="44865-108">![Fonctoid déclarer](../core/media/assertfunctoid.gif "AssertFunctoid")</span><span class="sxs-lookup"><span data-stu-id="44865-108">![Assert Functoid](../core/media/assertfunctoid.gif "AssertFunctoid")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44865-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="44865-109">See Also</span></span>  
 <span data-ttu-id="44865-110">**Référence du fonctoid déclarer** et **référence des fonctoids logiques**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span><span class="sxs-lookup"><span data-stu-id="44865-110">**Assert Functoid Reference** and **Logical Functoids Reference** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span></span>