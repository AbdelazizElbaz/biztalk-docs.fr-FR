---
title: Bouclage conditionnel | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Looping functoids, conditional
- Equal functoids
- maps, conditional looping
ms.assetid: eb16efb8-b12c-47d6-afc9-579fc85ea59c
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c5452f6b8768442b95ac6bddde0e84ba07f68c85
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="conditional-looping"></a><span data-ttu-id="7f569-102">Bouclage conditionnel</span><span class="sxs-lookup"><span data-stu-id="7f569-102">Conditional Looping</span></span>
<span data-ttu-id="7f569-103">Vous pouvez ajouter des conditions à un **bouclage** fonctoid en liant la sortie d’un **bouclage** fonctoid et un **logiques** fonctoid au même enregistrement de destination.</span><span class="sxs-lookup"><span data-stu-id="7f569-103">You can add conditions to a **Looping** functoid by linking the output of a **Looping** functoid and a **Logical** functoid to the same destination record.</span></span> <span data-ttu-id="7f569-104">Les enregistrements de destination sont créés uniquement lorsque la condition logique est remplie.</span><span class="sxs-lookup"><span data-stu-id="7f569-104">The destination records are created only when the logical condition is met.</span></span>  
  
## <a name="conditional-looping-map"></a><span data-ttu-id="7f569-105">Mappage de bouclage conditionnel</span><span class="sxs-lookup"><span data-stu-id="7f569-105">Conditional Looping Map</span></span>  
 <span data-ttu-id="7f569-106">![Mappage qui illustre un fonctoid Bouclage conditionnel. ] (../core/media/loopingconditionalfunctoid.gif "loopingconditionalfunctoid")</span><span class="sxs-lookup"><span data-stu-id="7f569-106">![Map illustrating conditional looping functoid.](../core/media/loopingconditionalfunctoid.gif "loopingconditionalfunctoid")</span></span>  
  
 <span data-ttu-id="7f569-107">Dans la figure précédente, la première **égal** fonctoid compare le **nom** champ sous **FoodSurvey** à « Wendy Wheeler ».</span><span class="sxs-lookup"><span data-stu-id="7f569-107">In the preceding figure, the first **Equal** functoid compares the **Name** field under **FoodSurvey** to "Wendy Wheeler".</span></span> <span data-ttu-id="7f569-108">La seconde **égal** fonctoid compare le **nom** champ sous **FlowerSurvey** à « Kelly Focht ».</span><span class="sxs-lookup"><span data-stu-id="7f569-108">The second **Equal** functoid compares the **Name** field under **FlowerSurvey** to "Kelly Focht".</span></span> <span data-ttu-id="7f569-109">Par conséquent, le mappage crée la destination **adresse** enregistrements uniquement pour les deux noms.</span><span class="sxs-lookup"><span data-stu-id="7f569-109">Thus, the map creates the destination **Address** records only for the two names.</span></span> <span data-ttu-id="7f569-110">À l’aide de l’exemple de données à partir de la **bouclage** exemple de fonctoid, le message d’instance de sortie s’affiche comme suit.</span><span class="sxs-lookup"><span data-stu-id="7f569-110">Using the sample data from the **Looping** functoid example, the output instance message would appear as follows.</span></span>  
  
```  
<ns0:MasterAddresses xmlns:ns0="http://ConditionalLoop.MasterAddresses">  
    <Address Name="Wendy Wheeler" Street="7890 Broadway" City="Columbus" State="OH" PostalCode="46290">  
    <Address Name="Kelly Focht" Street="456 1st Ave" City="Miami" State="FL" PostalCode="81406">  
</ns0:MasterAddresses>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7f569-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7f569-111">See Also</span></span>  
 <span data-ttu-id="7f569-112">[Comment ajouter des fonctoids à une carte de bouclage](../core/how-to-add-looping-functoids-to-a-map.md) </span><span class="sxs-lookup"><span data-stu-id="7f569-112">[How to Add Looping Functoids to a Map](../core/how-to-add-looping-functoids-to-a-map.md) </span></span>  
 <span data-ttu-id="7f569-113">[Fonctoids avancés](../core/advanced-functoids.md) </span><span class="sxs-lookup"><span data-stu-id="7f569-113">[Advanced Functoids](../core/advanced-functoids.md) </span></span>  
 <span data-ttu-id="7f569-114">[Fonctoid Index](../core/index-functoid.md) </span><span class="sxs-lookup"><span data-stu-id="7f569-114">[Index Functoid](../core/index-functoid.md) </span></span>  
 <span data-ttu-id="7f569-115">[Fonctoid Itération](../core/iteration-functoid.md) </span><span class="sxs-lookup"><span data-stu-id="7f569-115">[Iteration Functoid](../core/iteration-functoid.md) </span></span>  
 <span data-ttu-id="7f569-116">[Fonctoid Bouclage](../core/looping-functoid.md) </span><span class="sxs-lookup"><span data-stu-id="7f569-116">[Looping Functoid](../core/looping-functoid.md) </span></span>  
 [<span data-ttu-id="7f569-117">Fonctoid Nombre d’enregistrements</span><span class="sxs-lookup"><span data-stu-id="7f569-117">Record Count Functoid</span></span>](../core/record-count-functoid.md)