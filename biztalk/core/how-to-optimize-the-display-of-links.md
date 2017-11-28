---
title: "Comment faire pour optimiser l’affichage de liens | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2a9e16ff-01d3-4b7d-91c4-59d17266ee6d
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 689ab4c67bfe8cabc8109c373e899d391fdd56a5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-optimize-the-display-of-links"></a><span data-ttu-id="459bd-102">Optimisation de l'affichage des liens</span><span class="sxs-lookup"><span data-stu-id="459bd-102">How to Optimize the Display of Links</span></span>
<span data-ttu-id="459bd-103">Lorsque la taille des schémas est importante, vos mappages peuvent inclure un grand nombre de liens entre le schéma source et le schéma de destination.</span><span class="sxs-lookup"><span data-stu-id="459bd-103">When the schemas are big, your maps might include a large number of links between the source and the destination schemas.</span></span> <span data-ttu-id="459bd-104">La présence d'un aussi grand nombre de liens sur la surface de mappage complique le suivi d'un lien ou d'un objet sur lequel vous devez travailler.</span><span class="sxs-lookup"><span data-stu-id="459bd-104">With many links across the map surface, you may find it difficult to track a link or an object you need to work on.</span></span> <span data-ttu-id="459bd-105">De même, cette visibilité rend difficile le suivi d'une relation de bout en bout entre un schéma source, les liens, les fonctoids et le schéma de destination.</span><span class="sxs-lookup"><span data-stu-id="459bd-105">Also, it can be difficult for you to track an end-to-end relationship between a source schema, the links, the functoids, and the destination schema.</span></span> <span data-ttu-id="459bd-106">Le Mappeur BizTalk permet de mieux gérer les schémas complexes et volumineux et d'optimiser l'affichage des liens du mappage.</span><span class="sxs-lookup"><span data-stu-id="459bd-106">In the BizTalk Mapper, you can better manage complex and large schemas, and bring out an optimized display of links in the map.</span></span> <span data-ttu-id="459bd-107">Cette rubrique fournit des détails sur l'affichage des liens.</span><span class="sxs-lookup"><span data-stu-id="459bd-107">This topic provides details about how to view links.</span></span>  
  
 <span data-ttu-id="459bd-108">Vous pouvez classer les liens selon la typologie suivante :</span><span class="sxs-lookup"><span data-stu-id="459bd-108">You can categorize the links as follows:</span></span>  
  
-   <span data-ttu-id="459bd-109">Partiellement dans l'étendue</span><span class="sxs-lookup"><span data-stu-id="459bd-109">Partially in scope</span></span>  
  
-   <span data-ttu-id="459bd-110">Entièrement dans l'étendue</span><span class="sxs-lookup"><span data-stu-id="459bd-110">Completely in scope</span></span>  
  
-   <span data-ttu-id="459bd-111">Entièrement hors de l'étendue</span><span class="sxs-lookup"><span data-stu-id="459bd-111">Completely out of scope</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="459bd-112">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="459bd-112">Prerequisites</span></span>  
 <span data-ttu-id="459bd-113">Les instructions suivantes requièrent que le Mappeur BizTalk est en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="459bd-113">These instructions require that BizTalk Mapper is running.</span></span>  
  
## <a name="to-view-the-links-partially-in-scope"></a><span data-ttu-id="459bd-114">Affichage des liens partiellement dans l'étendue</span><span class="sxs-lookup"><span data-stu-id="459bd-114">To view the links partially in scope</span></span>  
 <span data-ttu-id="459bd-115">Les liens possédant au moins une extrémité visible sur la surface de la grille sont considérés comme « partiellement dans l'étendue ».</span><span class="sxs-lookup"><span data-stu-id="459bd-115">Links that have at least one end visible on the grid surface are called “partially in scope.”</span></span>  
  
 <span data-ttu-id="459bd-116">La figure ci-dessous illustre un lien « partiellement dans l'étendue ».</span><span class="sxs-lookup"><span data-stu-id="459bd-116">The figure below shows a link that is “partially in scope.”</span></span> <span data-ttu-id="459bd-117">Ces liens sont affichés en tant que lignes en pointillé dans la page de la grille.</span><span class="sxs-lookup"><span data-stu-id="459bd-117">These links are shown as dashed lines on the grid page.</span></span>  
  
 <span data-ttu-id="459bd-118">Cliquez sur le lien partiellement visible sur la surface de la grille : la page se déplace automatiquement vers le haut ou vers le bas de manière à placer la relation dans la vue active.</span><span class="sxs-lookup"><span data-stu-id="459bd-118">Click the link that is partially visible on the grid surface, and the grid page automatically moves up/down to bring the relationship into the current view.</span></span>  
  
 <span data-ttu-id="459bd-119">![Liaisons du Mappeur partiellement dans l’étendue](../core/media/mapper-partiallyinscope.gif "Mapper_PartiallyInScope")</span><span class="sxs-lookup"><span data-stu-id="459bd-119">![Mapper links partially in scope](../core/media/mapper-partiallyinscope.gif "Mapper_PartiallyInScope")</span></span>  
  
## <a name="to-view-the-links-completely-in-scope"></a><span data-ttu-id="459bd-120">Affichage des liens entièrement dans l'étendue</span><span class="sxs-lookup"><span data-stu-id="459bd-120">To view the links completely in scope</span></span>  
 <span data-ttu-id="459bd-121">Un lien dont les deux extrémités (nœud à nœud, nœud à fonctoid, fonctoid à fonctoid ou fonctoid à nœud) sont visibles sur la surface de la grille est considéré comme « entièrement dans l'étendue ».</span><span class="sxs-lookup"><span data-stu-id="459bd-121">A link that has both ends (node to node, node to functoid, functoid-to-functoid, or functoid to node) visible on the grid surface is called “completely in scope.”</span></span>  
  
 <span data-ttu-id="459bd-122">La figure ci-dessous illustre un lien reliant « DataCollection1 » et « ST01 » entièrement dans l'étendue.</span><span class="sxs-lookup"><span data-stu-id="459bd-122">The figure below shows a link between “DataCollection1” and “ST01” that is completely in scope.</span></span>  
  
 <span data-ttu-id="459bd-123">Cliquez sur le lien : la relation entre le nœud source et le nœud cible est sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="459bd-123">Click the link, and the relationship from source node to target node is selected.</span></span>  
  
 <span data-ttu-id="459bd-124">![Liaisons du Mappeur entièrement dans l’étendue](../core/media/mapper-completelyinscope.gif "Mapper_CompletelyInScope")</span><span class="sxs-lookup"><span data-stu-id="459bd-124">![Mapper links completely in scope](../core/media/mapper-completelyinscope.gif "Mapper_CompletelyInScope")</span></span>  
  
## <a name="to-view-the-links-completely-out-of-scope"></a><span data-ttu-id="459bd-125">Affichage des liens entièrement hors de l'étendue</span><span class="sxs-lookup"><span data-stu-id="459bd-125">To view the links completely out of scope</span></span>  
 <span data-ttu-id="459bd-126">Un lien dont aucune de ses extrémités n'est visible dans la vue active du mappage est considéré comme « entièrement hors de l'étendue ».</span><span class="sxs-lookup"><span data-stu-id="459bd-126">A link that has neither of its end points visible in the current map view is called “completely out of scope.”</span></span>  
  
 <span data-ttu-id="459bd-127">La figure ci-dessous illustre un lien « entièrement hors de l'étendue ».</span><span class="sxs-lookup"><span data-stu-id="459bd-127">The figure below shows a link that is completely out of scope.</span></span>  
  
 <span data-ttu-id="459bd-128">Si vous ne souhaitez pas afficher ces liens sur la carte de surface (car aucun des liens sont visibles), vous pouvez choisir de les mettre hors tension en cliquant sur ![afficher tous les liens](../core/media/mapper-showhideoutscopelinks.gif "Mapper_ShowHideOutScopeLinks") sur le Mappeur ruban de l’utilitaire.</span><span class="sxs-lookup"><span data-stu-id="459bd-128">If you do not want to display these links on the map surface (because none of the links are visible), you may choose to turn them off by clicking ![Show all links](../core/media/mapper-showhideoutscopelinks.gif "Mapper_ShowHideOutScopeLinks") on the Mapper utility ribbon.</span></span> <span data-ttu-id="459bd-129">Cela permet de réduire le nombre de liens affichés sur la vue Grille.</span><span class="sxs-lookup"><span data-stu-id="459bd-129">This reduces the amount of links that are visible on the grid view.</span></span>  
  
 <span data-ttu-id="459bd-130">![Liaisons du Mappeur entièrement hors de portée](../core/media/mapper-completelyoutscope.gif "Mapper_CompletelyOutScope")</span><span class="sxs-lookup"><span data-stu-id="459bd-130">![Mapper links completely out of scope](../core/media/mapper-completelyoutscope.gif "Mapper_CompletelyOutScope")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="459bd-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="459bd-131">See Also</span></span>  
 [<span data-ttu-id="459bd-132">À l’aide des fonctionnalités améliorées dans le Mappeur BizTalk</span><span class="sxs-lookup"><span data-stu-id="459bd-132">Using Enhanced Features in BizTalk Mapper</span></span>](../core/using-enhanced-features-in-biztalk-mapper.md)