---
title: "Redimensionner le sélecteur de schéma et développer ou réduire les arborescences de schéma | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 267ea17d-54fe-4031-a044-719606489f24
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 972be8ca5f412c39e1eb6fa2c81ccd9a21e65a34
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-resize-the-schema-picker-and-expand-and-collapse-the-schema-trees"></a><span data-ttu-id="06225-102">Redimensionner le sélecteur de schéma et développer ou réduire les arborescences de schéma</span><span class="sxs-lookup"><span data-stu-id="06225-102">How to resize the schema picker, and expand and collapse the schema trees</span></span>
<span data-ttu-id="06225-103">Lorsque vous développez des mappages BizTalk, vous avez souvent besoin de développer et de réduire les arborescences des schémas source et de destination pour afficher ou masquer les différents nœuds des schémas.</span><span class="sxs-lookup"><span data-stu-id="06225-103">When developing BizTalk maps, you are likely to need to expand and collapse the source and destination schema trees to expose or to hide the various schema nodes.</span></span> <span data-ttu-id="06225-104">Cette rubrique fournit des instructions détaillées pour redimensionner le sélecteur de schéma et pour développer et réduire l’arborescence du schéma.</span><span class="sxs-lookup"><span data-stu-id="06225-104">This topic provides step-by-step instructions to resize the schema picker, and to expand and collapse the schema tree.</span></span>  

## <a name="resize-the-schema-picker"></a><span data-ttu-id="06225-105">Redimensionner le sélecteur de schéma</span><span class="sxs-lookup"><span data-stu-id="06225-105">Resize the schema picker</span></span>

<span data-ttu-id="06225-106">Lorsque vous créez un mappage, vous ajoutez un schéma source et un schéma de destination.</span><span class="sxs-lookup"><span data-stu-id="06225-106">When you create a map, you add a source schema, and a destination schema.</span></span> <span data-ttu-id="06225-107">Lorsque vous ajoutez ou remplacez un schéma, la fenêtre de sélecteur de Type BizTalk s’ouvre et vous sélectionnez votre schéma.</span><span class="sxs-lookup"><span data-stu-id="06225-107">When you add or replace a schema, the BizTalk Type Picker window opens, and you select your schema.</span></span> 

<span data-ttu-id="06225-108">**En commençant par [!INCLUDE[bts2016_md](../includes/bts2016-md.md)]** , vous pouvez redimensionner la fenêtre Sélecteur de Type.</span><span class="sxs-lookup"><span data-stu-id="06225-108">**Starting with [!INCLUDE[bts2016_md](../includes/bts2016-md.md)]**, you can resize this Type Picker window.</span></span> <span data-ttu-id="06225-109">Cette fonctionnalité vous permet de voir le nom complet de votre schéma.</span><span class="sxs-lookup"><span data-stu-id="06225-109">This feature allows you to see the full name of your schema.</span></span>

1. <span data-ttu-id="06225-110">Dans votre mappage, sélectionnez **ouvrir le schéma de Destination**, ou **ouvrir le schéma Source**.</span><span class="sxs-lookup"><span data-stu-id="06225-110">In your map, select **Open Destination Schema**, or **Open Source Schema**.</span></span>
2. <span data-ttu-id="06225-111">Dans le **sélecteur de Type BizTalk** fenêtre, coin glisser l’angle inférieur droit pour augmenter ou diminuer la taille de fenêtre.</span><span class="sxs-lookup"><span data-stu-id="06225-111">In the **BizTalk Type Picker** window, drag the bottom-right corner to increase or decrease the window size.</span></span>
  
## <a name="expand-all-or-part-of-a-schema-tree"></a><span data-ttu-id="06225-112">Développer tout ou partie d’une arborescence de schéma</span><span class="sxs-lookup"><span data-stu-id="06225-112">Expand all or part of a schema tree</span></span>  
  
1.  <span data-ttu-id="06225-113">Sélectionnez le nœud sous lequel vous souhaitez développer complètement l'arborescence du schéma.</span><span class="sxs-lookup"><span data-stu-id="06225-113">Select the node under which you want to completely expand the schema tree.</span></span>  
  
     <span data-ttu-id="06225-114">Le nœud sélectionné doit être un nœud en regard duquel une icône plus (+) ou moins (-) est affichée.</span><span class="sxs-lookup"><span data-stu-id="06225-114">The selected node must be a node with a plus (+) or minus (-) icon next to it.</span></span>  
  
2.  <span data-ttu-id="06225-115">Sur le **BizTalk** menu, ou dans le menu contextuel du nœud, cliquez sur **développer le nœud d’arborescence**.</span><span class="sxs-lookup"><span data-stu-id="06225-115">On the **BizTalk** menu, or on the shortcut menu for that node, click **Expand Tree Node**.</span></span> <span data-ttu-id="06225-116">Tous les nœuds se trouvant sous le nœud sélectionné sont complètement développés.</span><span class="sxs-lookup"><span data-stu-id="06225-116">All nodes below the selected node are completely expanded.</span></span>  
  
     <span data-ttu-id="06225-117">Si l’arborescence du schéma située sous le nœud sélectionné est déjà entièrement développée, le **développer le nœud d’arborescence** élément de menu est désactivé.</span><span class="sxs-lookup"><span data-stu-id="06225-117">If the schema tree below the selected node is already completely expanded, the **Expand Tree Node** menu item is disabled.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="06225-118">Vous pouvez également appuyer sur CTRL+M, E pour développer les nœuds d'arborescence de schéma.</span><span class="sxs-lookup"><span data-stu-id="06225-118">Alternatively you can press CTRL+M, E to expand the schema tree nodes.</span></span> <span data-ttu-id="06225-119">Pour obtenir la liste des raccourcis clavier, consultez [raccourcis clavier de Mappeur BizTalk](../core/biztalk-mapper-keyboard-shortcuts.md).</span><span class="sxs-lookup"><span data-stu-id="06225-119">For a list of keyboard shortcuts, see [BizTalk Mapper Keyboard Shortcuts](../core/biztalk-mapper-keyboard-shortcuts.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="06225-120">Dans un schéma volumineux et complexe, lorsque vous cliquez sur **développer le nœud d’arborescence** sur un nœud qui contient les types complexes, certains nœuds du schéma peuvent rester dans l’état réduit.</span><span class="sxs-lookup"><span data-stu-id="06225-120">In a large and complex schema, when you click **Expand Tree Node** on a node that contains complex types, some nodes in the schema may remain in the collapsed state.</span></span> <span data-ttu-id="06225-121">Cela est dû au fait que le processus récurrent ne développe que la première occurrence d'un type complexe donné.</span><span class="sxs-lookup"><span data-stu-id="06225-121">This is because the recursive process expands only the first occurrence of a given complex type.</span></span> <span data-ttu-id="06225-122">Vous devrez développer les autres occurrences manuellement.</span><span class="sxs-lookup"><span data-stu-id="06225-122">You must manually expand later occurrences of the same type.</span></span> <span data-ttu-id="06225-123">Ce comportement permet d'optimiser les performances lors du développement de nœuds de grands schémas complexes.</span><span class="sxs-lookup"><span data-stu-id="06225-123">This behavior is designed to optimize performance when expanding nodes in large and complex schemas.</span></span>  
  
## <a name="collapse-all-or-part-of-a-schema-tree"></a><span data-ttu-id="06225-124">Réduire tout ou partie d’une arborescence de schéma</span><span class="sxs-lookup"><span data-stu-id="06225-124">Collapse all or part of a schema tree</span></span>  
  
1.  <span data-ttu-id="06225-125">Sélectionnez le nœud sous lequel vous souhaitez réduire complètement l'arborescence du schéma.</span><span class="sxs-lookup"><span data-stu-id="06225-125">Select the node under which you want to completely collapse the schema tree.</span></span>  
  
     <span data-ttu-id="06225-126">Le nœud sélectionné doit être un nœud en regard duquel une icône plus (+) ou moins (-) est affichée.</span><span class="sxs-lookup"><span data-stu-id="06225-126">The selected node must be a node with a plus (+) or minus (-) icon next to it.</span></span>  
  
2.  <span data-ttu-id="06225-127">Sur le **BizTalk** menu, ou dans le menu contextuel du nœud, cliquez sur **réduire le nœud d’arborescence**.</span><span class="sxs-lookup"><span data-stu-id="06225-127">On the **BizTalk** menu, or on the shortcut menu for that node, click **Collapse Tree Node**.</span></span>  
  
     <span data-ttu-id="06225-128">Tous les nœuds se trouvant sous le nœud sélectionné sont réduits.</span><span class="sxs-lookup"><span data-stu-id="06225-128">All nodes below the selected node are completely collapsed.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="06225-129">Vous pouvez également appuyer sur CTRL+M, C pour réduire les nœuds d'arborescence de schéma.</span><span class="sxs-lookup"><span data-stu-id="06225-129">Alternatively you can press CTRL+M, C to collapse the schema tree nodes.</span></span> <span data-ttu-id="06225-130">Pour obtenir la liste des raccourcis clavier, consultez [raccourcis clavier de Mappeur BizTalk](../core/biztalk-mapper-keyboard-shortcuts.md).</span><span class="sxs-lookup"><span data-stu-id="06225-130">For a list of keyboard shortcuts, see [BizTalk Mapper Keyboard Shortcuts](../core/biztalk-mapper-keyboard-shortcuts.md).</span></span>  
  
     <span data-ttu-id="06225-131">Si l’arborescence du schéma située sous le nœud sélectionné est déjà complètement réduite, le **réduire le nœud d’arborescence** élément de menu est désactivé.</span><span class="sxs-lookup"><span data-stu-id="06225-131">If the schema tree below the selected node is already collapsed, the **Collapse Tree Node** menu item is disabled.</span></span>  
  
 <span data-ttu-id="06225-132">Cette opération ne conserve pas les paramètres individuels de développement et de réduction des nœuds situés sous le nœud sélectionné.</span><span class="sxs-lookup"><span data-stu-id="06225-132">This operation will not remember the individual expand and collapse settings of the nodes below the selected node.</span></span> <span data-ttu-id="06225-133">Lorsque vous développez à nouveau le nœud réduit, les paramètres précédents sont perdus, et vous devez développer l’arborescence de schéma se trouvant en dessous de ce point nœud par nœud, ou la développer entièrement.</span><span class="sxs-lookup"><span data-stu-id="06225-133">When you re-expand the collapsed node, previous settings are lost, and you must expand the schema tree below that point node-by-node, or expand it entirely.</span></span>  
  
### <a name="expand-a-node"></a><span data-ttu-id="06225-134">Développez un nœud</span><span class="sxs-lookup"><span data-stu-id="06225-134">Expand a node</span></span>
  
-   <span data-ttu-id="06225-135">Cliquez sur l’icône plus (+) située à côté du nœud que vous voulez développer.</span><span class="sxs-lookup"><span data-stu-id="06225-135">Click the plus (+) icon next to the node you want to expand.</span></span>  
  
 <span data-ttu-id="06225-136">Le nœud sélectionné est développé.</span><span class="sxs-lookup"><span data-stu-id="06225-136">The selected node is expanded.</span></span> <span data-ttu-id="06225-137">Le fait que ses nœuds descendants soient développés ou réduits dépend de la façon dont le nœud sélectionné a été réduit et des paramètres de développement et de réduction précédents.</span><span class="sxs-lookup"><span data-stu-id="06225-137">Whether or not its descendent nodes are expanded or collapsed depends on how the selected node was collapsed and their previous expand and collapse settings.</span></span>  
  
### <a name="collapse-a-node"></a><span data-ttu-id="06225-138">Réduire un nœud</span><span class="sxs-lookup"><span data-stu-id="06225-138">Collapse a node</span></span>
  
-   <span data-ttu-id="06225-139">Cliquez sur l’icône moins (-) située à côté du nœud que vous voulez réduire.</span><span class="sxs-lookup"><span data-stu-id="06225-139">Click the minus (-) icon next to the node you want to collapse.</span></span>  
  
 <span data-ttu-id="06225-140">Le nœud sélectionné est réduit.</span><span class="sxs-lookup"><span data-stu-id="06225-140">The selected node is collapsed.</span></span>  
  
 <span data-ttu-id="06225-141">Cette opération conserve les paramètres individuels de développement et de réduction des nœuds situés sous le nœud sélectionné.</span><span class="sxs-lookup"><span data-stu-id="06225-141">This operation will remember the individual expand and collapse settings of the nodes below the selected node.</span></span> <span data-ttu-id="06225-142">Lorsque vous développez à nouveau le nœud réduit à l’aide de l’icône plus (+), les paramètres individuels précédents ne sont pas perdus, et l’arborescence de schéma se trouvant sous ce point est rétablie dans son état précédent.</span><span class="sxs-lookup"><span data-stu-id="06225-142">When you re-expand the collapsed node by using the plus (+) icon, the previous individual settings are not lost, and the schema tree below that point returns to its previous state.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06225-143">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="06225-143">See Also</span></span>  
 [<span data-ttu-id="06225-144">À l’aide du Mappeur BizTalk</span><span class="sxs-lookup"><span data-stu-id="06225-144">Using BizTalk Mapper</span></span>](../core/using-biztalk-mapper.md)