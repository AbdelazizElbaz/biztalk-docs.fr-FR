---
title: "Fonctoid Itération | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Iteration functoids
- Greater Than or Equal To functoids
- And functoids
- Less Than or Equal To functoids
ms.assetid: 24d8911d-2282-4b07-910c-eb2e846dc1f9
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a491b8829f23296e77ba5a89d12985e8ccd32783
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="iteration-functoid"></a><span data-ttu-id="127a5-102">Fonctoid Itération</span><span class="sxs-lookup"><span data-stu-id="127a5-102">Iteration Functoid</span></span>
<span data-ttu-id="127a5-103">Le **itération** fonctoid sorties commençant à 1 pour le premier enregistrement, 2 pour le deuxième enregistrement de la structure de l’index de l’enregistrement actif dans une boucle et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="127a5-103">The **Iteration** functoid outputs the index of the current record in a looping structure, beginning at 1 for the first record, 2 for the second record, and so on.</span></span>  
  
 <span data-ttu-id="127a5-104">L’illustration suivante montre un **itération** fonctoid combiné avec un **supérieur ou égal à** fonctoid, un **inférieure ou égale à** fonctoid et un **et**  fonctoid pour créer l’équivalent d’un **pour** boucle.</span><span class="sxs-lookup"><span data-stu-id="127a5-104">The following figure shows an **Iteration** functoid combined with a **Greater Than or Equal To** functoid, a **Less Than or Equal To** functoid, and an **And** functoid to create the equivalent of a **For** loop.</span></span>  
  
 <span data-ttu-id="127a5-105">![Mappage illustrant l’utilisation du fonctoid itération](../core/media/iterationfunctoid.gif "iterationfunctoid")</span><span class="sxs-lookup"><span data-stu-id="127a5-105">![Map illustrating the use of the iteration functoid](../core/media/iterationfunctoid.gif "iterationfunctoid")</span></span>  
<span data-ttu-id="127a5-106">Mappage du fonctoid Itération</span><span class="sxs-lookup"><span data-stu-id="127a5-106">Iteration Functoid Map</span></span>  
  
 <span data-ttu-id="127a5-107">Supposent que le **supérieur ou égal à** teste fonctoid supérieur ou égal à 2 et le **inférieure ou égale à** des tests pour le fonctoid inférieur ou égal à 4 valeurs.</span><span class="sxs-lookup"><span data-stu-id="127a5-107">Assume that the **Greater Than or Equal To** functoid tests for values greater than or equal to 2, and the **Less Than or Equal To** functoid tests for values less than or equal to 4.</span></span> <span data-ttu-id="127a5-108">Dans ce cas, le **et** fonctoid retournera **true** uniquement pour les enregistrements de 2, 3 et 4.</span><span class="sxs-lookup"><span data-stu-id="127a5-108">In that case, the **And** functoid will return **true** only for records 2, 3, and 4.</span></span> <span data-ttu-id="127a5-109">Par conséquent, l’instance de sortie contiendra enregistre les deux, trois et quatre du message d’instance d’entrée.</span><span class="sxs-lookup"><span data-stu-id="127a5-109">Thus, the output instance will contain records two, three, and four of the input instance message.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="127a5-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="127a5-110">See Also</span></span>  
 <span data-ttu-id="127a5-111">[Ajout de fonctoids itération à un mappage](../core/how-to-add-iteration-functoids-to-a-map.md) </span><span class="sxs-lookup"><span data-stu-id="127a5-111">[How to Add Iteration Functoids to a Map](../core/how-to-add-iteration-functoids-to-a-map.md) </span></span>  
 <span data-ttu-id="127a5-112">[Fonctoids avancés](../core/advanced-functoids.md) </span><span class="sxs-lookup"><span data-stu-id="127a5-112">[Advanced Functoids](../core/advanced-functoids.md) </span></span>  
 <span data-ttu-id="127a5-113">[Fonctoid Index](../core/index-functoid.md) </span><span class="sxs-lookup"><span data-stu-id="127a5-113">[Index Functoid](../core/index-functoid.md) </span></span>  
 <span data-ttu-id="127a5-114">[Fonctoid Bouclage](../core/looping-functoid.md) </span><span class="sxs-lookup"><span data-stu-id="127a5-114">[Looping Functoid](../core/looping-functoid.md) </span></span>  
 [<span data-ttu-id="127a5-115">Fonctoid Nombre d’enregistrements</span><span class="sxs-lookup"><span data-stu-id="127a5-115">Record Count Functoid</span></span>](../core/record-count-functoid.md)