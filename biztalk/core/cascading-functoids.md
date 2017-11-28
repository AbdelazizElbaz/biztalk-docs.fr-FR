---
title: Fonctoids en cascade | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- functoid types, Cascading
- Cascading functoids
ms.assetid: 03c46e7b-be1c-475e-b68b-f9d1d7732fce
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0d5e9cfcad2432eb83c8a251147bac76b20db0bc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="cascading-functoids"></a><span data-ttu-id="c4de2-102">Fonctoids en cascade</span><span class="sxs-lookup"><span data-stu-id="c4de2-102">Cascading Functoids</span></span>
<span data-ttu-id="c4de2-103">On dit que les fonctoids sont en cascade lorsqu'un fonctoid est lié à un autre fonctoid avant d’être lié à un enregistrement ou à un champ dans le schéma de destination.</span><span class="sxs-lookup"><span data-stu-id="c4de2-103">Functoids are said to be cascaded when one functoid is linked to another functoid before it is linked to a record or field in the destination schema.</span></span> <span data-ttu-id="c4de2-104">Par exemple, vous pouvez créer des fonctoids en cascade dans lesquels deux chaînes concaténées produisent une troisième chaîne alimentée dans un champ du schéma de destination.</span><span class="sxs-lookup"><span data-stu-id="c4de2-104">For example, you can create cascading functoids in which two concatenated strings produce a third string fed into a field in the destination schema.</span></span>  
  
 <span data-ttu-id="c4de2-105">Lorsque vous placez des fonctoids en cascade, vous pouvez créer des transformations consécutives et multiples dans la page de grille.</span><span class="sxs-lookup"><span data-stu-id="c4de2-105">When you cascade functoids, you can create multiple, consecutive transformations in the grid page.</span></span> <span data-ttu-id="c4de2-106">Il n'existe pas de limite au nombre de fonctoids que vous pouvez mettre en cascade dans une page, veillez toutefois à utiliser la mise en cascade judicieusement.</span><span class="sxs-lookup"><span data-stu-id="c4de2-106">While there is no limit to the number of functoids that you can cascade in a page, use cascading wisely.</span></span> <span data-ttu-id="c4de2-107">La mise en cascade complexe allonge le temps de transformation d'un message d'instance d'entrée en message d'instance de sortie, ce qui réduit considérablement les performances d'exécution.</span><span class="sxs-lookup"><span data-stu-id="c4de2-107">Complex cascading can increase the time to transform an input instance message into an output instance message, significantly reducing run time performance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4de2-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c4de2-108">See Also</span></span>  
 <span data-ttu-id="c4de2-109">[Fonctoids dans les mappages](../core/functoids-in-maps.md) </span><span class="sxs-lookup"><span data-stu-id="c4de2-109">[Functoids in Maps](../core/functoids-in-maps.md) </span></span>  
 [<span data-ttu-id="c4de2-110">À l’aide des fonctoids pour créer des mappages plus complexes</span><span class="sxs-lookup"><span data-stu-id="c4de2-110">Using Functoids to Create More Complex Mappings</span></span>](../core/using-functoids-to-create-more-complex-mappings.md)