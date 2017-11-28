---
title: "Correspondance au niveau de hiérarchie de nœuds | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Field nodes
- BizTalk Mapper, processing
- Record node
- BizTalk Mapper, compiler directives
- destination schemas, matching nodes
- source schemas, matching nodes
- maps, links
- Target Links property
- BizTalk Mapper, links
- compiler directives, matching schema nodes
- compiler directives, flattening source hierarchies
- maps, processing
ms.assetid: 5ba1ac77-0e70-4c58-9b8c-1b379dbbb3bd
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0b2d0c363abfefb9e3d0eb8abfb332c59539bb67
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="node-hierarchy-level-matching"></a><span data-ttu-id="6a596-102">Correspondance au niveau de la hiérarchie de nœuds</span><span class="sxs-lookup"><span data-stu-id="6a596-102">Node-Hierarchy Level Matching</span></span>
<span data-ttu-id="6a596-103">Le Mappeur BizTalk vous permet de configurer une propriété de lien pour contrôler la manière dont le compilateur fait correspondre les hiérarchies de nœuds entre les schémas source et de destination.</span><span class="sxs-lookup"><span data-stu-id="6a596-103">BizTalk Mapper enables you to configure a link property to control how the compiler matches node hierarchies between the source and destination schemas.</span></span> <span data-ttu-id="6a596-104">Lorsque vous créez un lien entre un champ du schéma source et un champ du schéma de destination, le Mappeur BizTalk ajoute automatiquement des liens de compilateur.</span><span class="sxs-lookup"><span data-stu-id="6a596-104">When you create a link from a field in the source schema to a field in the destination schema, BizTalk Mapper automatically adds compiler links.</span></span> <span data-ttu-id="6a596-105">Ces liens de compilateur dépendent de la correspondance que vous sélectionnez.</span><span class="sxs-lookup"><span data-stu-id="6a596-105">These compiler links depend on the matching you select.</span></span>  
  
 <span data-ttu-id="6a596-106">Lorsque vous sélectionnez un lien dans la page de grille affichée, une des propriétés affichées dans le [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] fenêtre Propriétés est le **liaisons cibles** propriété.</span><span class="sxs-lookup"><span data-stu-id="6a596-106">When you select a link in the displayed grid page, one of the properties displayed in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window is the **Target Links** property.</span></span> <span data-ttu-id="6a596-107">Vous avez le choix entre les valeurs suivantes pour chaque lien de votre mappage :</span><span class="sxs-lookup"><span data-stu-id="6a596-107">You can choose among the following possible values for each link in your map:</span></span>  
  
-   <span data-ttu-id="6a596-108">**Liaisons aplaties.**</span><span class="sxs-lookup"><span data-stu-id="6a596-108">**Flatten links.**</span></span> <span data-ttu-id="6a596-109">utilisez cette valeur pour mettre à plat toutes les hiérarchies sources au niveau de l'enregistrement parent dans le nœud du schéma de destination.</span><span class="sxs-lookup"><span data-stu-id="6a596-109">Use this value to flatten all source hierarchies to the parent record in the destination schema node.</span></span>  
  
-   <span data-ttu-id="6a596-110">**Correspondance descendante des liaisons.**</span><span class="sxs-lookup"><span data-stu-id="6a596-110">**Match links top down.**</span></span> <span data-ttu-id="6a596-111">utilisez cette valeur pour faire correspondre les niveaux de nœud du haut vers le bas dans les schémas.</span><span class="sxs-lookup"><span data-stu-id="6a596-111">Use this value to match node levels from the top of the schemas to the bottom of the schemas.</span></span>  
  
-   <span data-ttu-id="6a596-112">**Correspondance ascendante des liaisons.**</span><span class="sxs-lookup"><span data-stu-id="6a596-112">**Match links bottom up.**</span></span> <span data-ttu-id="6a596-113">utilisez cette valeur pour faire correspondre les niveaux de nœud du bas vers le haut dans les schémas.</span><span class="sxs-lookup"><span data-stu-id="6a596-113">Use this value to match node levels from the bottom of the schemas to the top of the schemas.</span></span>  
  
## <a name="flatten-links"></a><span data-ttu-id="6a596-114">Liaisons aplaties</span><span class="sxs-lookup"><span data-stu-id="6a596-114">Flatten Links</span></span>  
 <span data-ttu-id="6a596-115">Dans ce mode, toutes les hiérarchies sources sont mises à plat au niveau de l'enregistrement parent du nœud de destination.</span><span class="sxs-lookup"><span data-stu-id="6a596-115">In this mode, all the source hierarchies are flattened to the parent record of the destination node.</span></span> <span data-ttu-id="6a596-116">Dans le premier cas, le schéma source est plus complexe que le schéma de destination.</span><span class="sxs-lookup"><span data-stu-id="6a596-116">In the first case, the source schema is more complex than the destination schema.</span></span> <span data-ttu-id="6a596-117">Dans le second cas, le schéma de destination est plus complexe.</span><span class="sxs-lookup"><span data-stu-id="6a596-117">In the second case, the destination schema is more complex.</span></span>  
  
 ![](../core/media/bts-tls-flatten.gif "bts_tls_flatten")  
<span data-ttu-id="6a596-118">Liaisons aplaties</span><span class="sxs-lookup"><span data-stu-id="6a596-118">Flatten Links</span></span>  
  
 ![](../core/media/bts-tls-flatten-2.gif "bts_tls_flatten_2")  
<span data-ttu-id="6a596-119">Liaisons aplaties, second cas</span><span class="sxs-lookup"><span data-stu-id="6a596-119">Flatten Links, Second Case</span></span>  
  
## <a name="match-links-top-down"></a><span data-ttu-id="6a596-120">Correspondance descendante des liaisons :</span><span class="sxs-lookup"><span data-stu-id="6a596-120">Match Links Top-Down</span></span>  
 <span data-ttu-id="6a596-121">Ce mode établit des correspondances niveau par niveau de façon descendante.</span><span class="sxs-lookup"><span data-stu-id="6a596-121">This mode matches level to level from the top down.</span></span> <span data-ttu-id="6a596-122">Dans le premier cas, le schéma source est plus complexe que le schéma de destination.</span><span class="sxs-lookup"><span data-stu-id="6a596-122">In the first case, the source schema is more complex than the destination schema.</span></span> <span data-ttu-id="6a596-123">Dans le second cas, le schéma de destination est plus complexe.</span><span class="sxs-lookup"><span data-stu-id="6a596-123">In the second case, the destination schema is more complex.</span></span>  
  
 ![](../core/media/bts-tls-topdown.gif "bts_tls_topdown")  
<span data-ttu-id="6a596-124">Correspondance descendante</span><span class="sxs-lookup"><span data-stu-id="6a596-124">Top-Down Matching</span></span>  
  
 ![](../core/media/bts-tls-topdown-2.gif "bts_tls_topdown_2")  
<span data-ttu-id="6a596-125">Correspondance descendante, second cas</span><span class="sxs-lookup"><span data-stu-id="6a596-125">Top-Down Matching, Second Case</span></span>  
  
## <a name="match-links-bottom-up"></a><span data-ttu-id="6a596-126">Correspondance ascendante des liaisons</span><span class="sxs-lookup"><span data-stu-id="6a596-126">Match Links Bottom-Up</span></span>  
 <span data-ttu-id="6a596-127">Ce mode établit des correspondances niveau par niveau de façon ascendante.</span><span class="sxs-lookup"><span data-stu-id="6a596-127">This mode matches level to level from the bottom up.</span></span> <span data-ttu-id="6a596-128">Dans le premier cas, le schéma source est plus complexe que le schéma de destination.</span><span class="sxs-lookup"><span data-stu-id="6a596-128">In the first case, the source schema is more complex than the destination schema.</span></span> <span data-ttu-id="6a596-129">Dans le second cas, le schéma de destination est plus complexe.</span><span class="sxs-lookup"><span data-stu-id="6a596-129">In the second case, the destination schema is more complex.</span></span>  
  
 ![](../core/media/bts-tls-bottomup.gif "bts_tls_bottomup")  
<span data-ttu-id="6a596-130">Correspondance ascendante</span><span class="sxs-lookup"><span data-stu-id="6a596-130">Bottom-Up Matching</span></span>  
  
 ![](../core/media/bts-tls-bottomup-2.gif "bts_tls_bottomup_2")  
<span data-ttu-id="6a596-131">Correspondance ascendante, second cas</span><span class="sxs-lookup"><span data-stu-id="6a596-131">Bottom-Up Matching, Second Case</span></span>  
  
## <a name="how-biztalk-mapper-processes-link-types"></a><span data-ttu-id="6a596-132">Traitement des types de liens par le Mappeur BizTalk</span><span class="sxs-lookup"><span data-stu-id="6a596-132">How BizTalk Mapper Processes Link Types</span></span>  
 <span data-ttu-id="6a596-133">Étant donné que vous pouvez définir le **liaisons cibles** propriété des valeurs différentes pour différents liens, le Mappeur BizTalk doit pouvoir résoudre les divers paramètres lorsqu’ils peuvent entrer en conflit.</span><span class="sxs-lookup"><span data-stu-id="6a596-133">Because you can set the **Target Links** property to different values for different links, BizTalk Mapper needs a way to resolve the different settings when they may conflict.</span></span>  
  
 <span data-ttu-id="6a596-134">Par exemple, si vous utilisez une directive de compilation aplatie, une directive de compilation de haut en bas et une directive de compilation de bas en haut des liens à partir **champ** nœuds **champ** nœuds dans le schéma de destination et ces nœuds partagent le même parent **enregistrement** nœud, le Mappeur BizTalk ignore les directives de compilateur descendant et ascendant en conflit et traite tous les liens comme s’ils étaient définis sur la directive de compilation aplanie.</span><span class="sxs-lookup"><span data-stu-id="6a596-134">For example, if you use a flatten compiler directive, a top-down compiler directive, and a bottom-up compiler directive for links from **Field** nodes to **Field** nodes in the destination schema, and these nodes share the same parent **Record** node, BizTalk Mapper ignores the conflicting top-down and bottom-up compiler directives and treats all the links as if they were set to the flatten compiler directive.</span></span>  
  
 <span data-ttu-id="6a596-135">Le tableau suivant montre comment le Mappeur BizTalk traite des liens vers des **champ** nœuds dans la même **enregistrement** nœud dans le schéma de destination, basé sur les paramètres pour le **liaisons cibles** propriété pour les liens au sein du même **enregistrement** nœud.</span><span class="sxs-lookup"><span data-stu-id="6a596-135">The following table shows how BizTalk Mapper treats links to **Field** nodes in the same **Record** node in the destination schema, based on the settings for the **Target Links** property for the links within the same **Record** node.</span></span>  
  
|<span data-ttu-id="6a596-136">Mise à plat</span><span class="sxs-lookup"><span data-stu-id="6a596-136">Flatten</span></span>|<span data-ttu-id="6a596-137">Descendant</span><span class="sxs-lookup"><span data-stu-id="6a596-137">Top-down</span></span>|<span data-ttu-id="6a596-138">Ascendant</span><span class="sxs-lookup"><span data-stu-id="6a596-138">Bottom-up</span></span>|<span data-ttu-id="6a596-139">Résultat</span><span class="sxs-lookup"><span data-stu-id="6a596-139">Result</span></span>|  
|-------------|---------------|----------------|------------|  
|<span data-ttu-id="6a596-140">0 ou plus</span><span class="sxs-lookup"><span data-stu-id="6a596-140">0 or more</span></span>|<span data-ttu-id="6a596-141">1 ou plus</span><span class="sxs-lookup"><span data-stu-id="6a596-141">1 or more</span></span>|<span data-ttu-id="6a596-142">1 ou plus</span><span class="sxs-lookup"><span data-stu-id="6a596-142">1 or more</span></span>|<span data-ttu-id="6a596-143">Le Mappeur BizTalk traite tous les liens comme s'ils étaient définis sur la directive de compilateur de mise à plat.</span><span class="sxs-lookup"><span data-stu-id="6a596-143">BizTalk Mapper treats all the links as if they were set to the flatten compiler directive.</span></span>|  
|<span data-ttu-id="6a596-144">1 ou plus</span><span class="sxs-lookup"><span data-stu-id="6a596-144">1 or more</span></span>|<span data-ttu-id="6a596-145">1 ou plus</span><span class="sxs-lookup"><span data-stu-id="6a596-145">1 or more</span></span>|<span data-ttu-id="6a596-146">0</span><span class="sxs-lookup"><span data-stu-id="6a596-146">0</span></span>|<span data-ttu-id="6a596-147">Le Mappeur BizTalk traite tous les liens comme s'ils étaient définis sur la directive de compilateur descendant.</span><span class="sxs-lookup"><span data-stu-id="6a596-147">BizTalk Mapper treats all the links as if they were set to the top-down compiler directive.</span></span>|  
|<span data-ttu-id="6a596-148">1 ou plus</span><span class="sxs-lookup"><span data-stu-id="6a596-148">1 or more</span></span>|<span data-ttu-id="6a596-149">0</span><span class="sxs-lookup"><span data-stu-id="6a596-149">0</span></span>|<span data-ttu-id="6a596-150">1 ou plus</span><span class="sxs-lookup"><span data-stu-id="6a596-150">1 or more</span></span>|<span data-ttu-id="6a596-151">Le Mappeur BizTalk traite tous les liens comme s'ils étaient définis sur la directive de compilateur ascendant.</span><span class="sxs-lookup"><span data-stu-id="6a596-151">BizTalk Mapper treats all the links as if they were set to the bottom-up compiler directive.</span></span>|  
  
 <span data-ttu-id="6a596-152">Les directives de compilateur descendant et ascendant ont priorité sur la directive de compilateur de mise à plat, mais s'annulent l'une l'autre lorsqu'elles coexistent.</span><span class="sxs-lookup"><span data-stu-id="6a596-152">The top-down and bottom-up compiler directives take precedence over the flatten compiler directive, but cancel each other out when both are present.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a596-153">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6a596-153">See Also</span></span>  
 <span data-ttu-id="6a596-154">[Fonctoid copie de masse](../core/mass-copy-functoid.md) </span><span class="sxs-lookup"><span data-stu-id="6a596-154">[Mass Copy Functoid](../core/mass-copy-functoid.md) </span></span>  
 <span data-ttu-id="6a596-155">[Comment définir la valeur du compilateur Source de liens](../core/how-to-set-the-source-links-compiler-value.md) </span><span class="sxs-lookup"><span data-stu-id="6a596-155">[How to Set the Source Links Compiler Value](../core/how-to-set-the-source-links-compiler-value.md) </span></span>  
 [<span data-ttu-id="6a596-156">Compilation des mappages</span><span class="sxs-lookup"><span data-stu-id="6a596-156">Compiling Maps</span></span>](../core/compiling-maps.md)