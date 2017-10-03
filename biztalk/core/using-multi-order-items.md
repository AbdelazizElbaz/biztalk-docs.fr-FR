---
title: "À l’aide de commandes multiples éléments | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- JD Edwards OneWorld adapters, multiple calls
- JD Edwards OneWorld adapters, multi-order numbers
- multiple edit line calls [JD Edwards OneWorld adapters]
- adapters [JD Edwards OneWorld adapters], multi-order numbers
- multi-order numbers [JD Edwards OneWorld adapters]
- adapters [JD Edwards OneWorld adapters], multiple calls
ms.assetid: 207ea92c-03f7-4117-8414-eb174e659d26
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 389e73ede2d1062c9907bd8640f38ce74ad6f316
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="using-multi-order-items"></a><span data-ttu-id="cc3a8-102">L’utilisation des éléments de commandes multiples</span><span class="sxs-lookup"><span data-stu-id="cc3a8-102">Using Multi-Order Items</span></span>
<span data-ttu-id="cc3a8-103">En raison de la structure de l'API JD Edwards OneWorld, si vous souhaitez utiliser plusieurs numéros de commande avec BizTalk Server, vous devez effectuer plusieurs appels de modification d'article dans votre orchestration pour ajouter ces articles dans une orchestration.</span><span class="sxs-lookup"><span data-stu-id="cc3a8-103">Due to the structure of the JD Edwards OneWorld API, if you want to use multi-order numbers with BizTalk Server, you must make multiple edit line calls in your orchestration to add those line items in an orchestration.</span></span> <span data-ttu-id="cc3a8-104">Par exemple, un article appartenant à plusieurs commandes inclut un en-tête avec un seul numéro de commande, et des détails comprenant plusieurs commandes d'articles (par exemple, Jouet 1pc, Gants 2pcs).</span><span class="sxs-lookup"><span data-stu-id="cc3a8-104">For example, a multi-order item might contain a header with a single order number, and detail that includes several items orders (like Toy 1EA, Gloves 2EA).</span></span>  
  
 <span data-ttu-id="cc3a8-105">Avant de pouvoir utiliser plusieurs appels de modification d'article, le développeur BizTalk Server doit les structurer.</span><span class="sxs-lookup"><span data-stu-id="cc3a8-105">To use multiple edit line calls, it is the responsibility of the BizTalk Server developer to structure them.</span></span> <span data-ttu-id="cc3a8-106">Il doit créer une boucle interne pour que l'orchestration puisse effectuer ces appels.</span><span class="sxs-lookup"><span data-stu-id="cc3a8-106">The developer should create an internal loop in the orchestration to make those calls.</span></span>  
  
 <span data-ttu-id="cc3a8-107">Contrairement au système JD Edwards OneWorld, l'API ne prend pas en charge plusieurs appels de modification d'article.</span><span class="sxs-lookup"><span data-stu-id="cc3a8-107">The JD Edwards OneWorld system supports multiple edit line calls, but the API does not.</span></span> <span data-ttu-id="cc3a8-108">La structure de la méthode de modification d'article est une structure plate, et non une séquence.</span><span class="sxs-lookup"><span data-stu-id="cc3a8-108">If you look at the structure of the Edit Line method, it is a flat structure and not a sequence.</span></span> <span data-ttu-id="cc3a8-109">C'est pourquoi, vous devez appeler la fonction à chaque fois que vous souhaitez insérer un article.</span><span class="sxs-lookup"><span data-stu-id="cc3a8-109">Therefore, you must call the function every time you want to insert a line item.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc3a8-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cc3a8-110">See Also</span></span>  
 [<span data-ttu-id="cc3a8-111">Planification et Architecture</span><span class="sxs-lookup"><span data-stu-id="cc3a8-111">Planning and Architecture</span></span>](../core/planning-and-architecture17.md)