---
title: Comment copier, couper et coller un fonctoid | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 825847e4-87db-4b40-8e5d-5b5b1c79c6de
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9af3662fb866eb09c1dcb2516279ca097cc998f6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-copy-cut-and-paste-a-functoid"></a><span data-ttu-id="9b550-102">Coupage, copie et collage d'un fonctoid</span><span class="sxs-lookup"><span data-stu-id="9b550-102">How to Copy, Cut, and Paste a Functoid</span></span>
<span data-ttu-id="9b550-103">La fonctionnalité copier/couper/coller du Mappeur BizTalk permet la réutilisation des fonctoids.</span><span class="sxs-lookup"><span data-stu-id="9b550-103">The copy/cut/paste feature in the BizTalk Mapper enables the reusability of functoids.</span></span> <span data-ttu-id="9b550-104">Dans un mappage, vous pouvez copier, couper et coller un ou plusieurs fonctoids à partir d'une page de grille sur une autre.</span><span class="sxs-lookup"><span data-stu-id="9b550-104">In a map, you can copy, cut, and paste one or more functoids from one grid page to another.</span></span> <span data-ttu-id="9b550-105">Cette rubrique contient des instructions détaillées pour effectuer ces opérations.</span><span class="sxs-lookup"><span data-stu-id="9b550-105">This topic provides step-by-step instructions to perform these operations.</span></span>  
  
 <span data-ttu-id="9b550-106">Vous pouvez faire appel à la fonctionnalité copier/coller lorsque vous souhaitez réutiliser des fonctoids.</span><span class="sxs-lookup"><span data-stu-id="9b550-106">You can use the copy/paste feature when you want to reuse functoids.</span></span> <span data-ttu-id="9b550-107">Lorsque vous souhaitez supprimer un fonctoid de son emplacement actuel pour le déplacer vers un nouvel emplacement, vous pouvez utiliser la fonctionnalité couper/coller.</span><span class="sxs-lookup"><span data-stu-id="9b550-107">And, when you want to remove a functoid from the existing location and move it to a new location, you can use the cut/paste feature.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="9b550-108">Lorsque vous choisissez de copier un fonctoid, le fonctoid en lui-même, son étiquette, ses commentaires, ses entrées constantes ainsi que les index d'espaces réservés sont copiés.</span><span class="sxs-lookup"><span data-stu-id="9b550-108">When you choose to copy a functoid, the functoid, its label, comments, and the constant-inputs, along with the placeholder indices, are copied.</span></span> <span data-ttu-id="9b550-109">De même, lorsque vous choisissez de couper un fonctoid, le fonctoid en lui-même, son étiquette, ses commentaires, ses entrées constantes ainsi que les index d'espaces réservés sont coupés.</span><span class="sxs-lookup"><span data-stu-id="9b550-109">Similarly, when you choose to cut a functoid, the functoid, its label, comments, constant-inputs, along with the placeholder indices, are cut.</span></span> <span data-ttu-id="9b550-110">Toutefois, lorsque vous collez votre sélection (après l'avoir coupée), les liens orphelins sont supprimés et seul le fonctoid est conservé ;</span><span class="sxs-lookup"><span data-stu-id="9b550-110">But, when you paste (after choosing to cut) the selection, only the functoid is retained and the orphaned links are deleted.</span></span> <span data-ttu-id="9b550-111">l'étiquette, les commentaires, les entrées constantes et les index d'espaces réservés ne sont pas conservés.</span><span class="sxs-lookup"><span data-stu-id="9b550-111">The label, comments, constant inputs, and placeholder indices are not retained.</span></span>  
  
 <span data-ttu-id="9b550-112">Si vous sélectionnez simplement un fonctoid, qu'il soit lié à un autre fonctoid ou à un nœud de schéma, lui seul est coupé ou copié, sans les liens.</span><span class="sxs-lookup"><span data-stu-id="9b550-112">If you select only a functoid, which is either linked to another functoid or a schema node, only the functoid will be cut or copied, without the links.</span></span> <span data-ttu-id="9b550-113">Si vous coupez un fonctoid qui est lié soit à d'autres fonctoids du mappage soit aux nœuds de schéma, les liens pointant vers ce fonctoid sont supprimés.</span><span class="sxs-lookup"><span data-stu-id="9b550-113">If you cut a functoid that is linked to other functoids in the map or to the schema nodes, the links to the functoid that is cut are deleted.</span></span>  
  
 <span data-ttu-id="9b550-114">Vous pouvez copier/couper des fonctoids :</span><span class="sxs-lookup"><span data-stu-id="9b550-114">You can copy/cut functoids from:</span></span>  
  
-   <span data-ttu-id="9b550-115">Au sein de la même page de grille d'un mappage</span><span class="sxs-lookup"><span data-stu-id="9b550-115">Within the same grid page of a map</span></span>  
  
-   <span data-ttu-id="9b550-116">D'une page de grille à l'autre dans le même mappage</span><span class="sxs-lookup"><span data-stu-id="9b550-116">One grid page to the other in the same map</span></span>  
  
-   <span data-ttu-id="9b550-117">entre instances de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="9b550-117">One instance of Visual Studio to another</span></span>  
  
 <span data-ttu-id="9b550-118">Vous pouvez annuler ou rétablir les opérations Couper et Coller.</span><span class="sxs-lookup"><span data-stu-id="9b550-118">You can undo or redo the cut and paste operations.</span></span> <span data-ttu-id="9b550-119">Pour plus d’informations, consultez [comment annuler ou rétablir les opérations de l’utilisateur](../core/how-to-undo-or-redo-user-operations.md).</span><span class="sxs-lookup"><span data-stu-id="9b550-119">For more information, see [How to Undo or Redo User Operations](../core/how-to-undo-or-redo-user-operations.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="9b550-120">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="9b550-120">Prerequisites</span></span>  
 <span data-ttu-id="9b550-121">Les instructions suivantes requièrent que le Mappeur BizTalk est en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="9b550-121">These instructions require that BizTalk Mapper is running.</span></span>  
  
### <a name="to-copy-and-paste-a-functoid"></a><span data-ttu-id="9b550-122">Pour copier et coller un fonctoid</span><span class="sxs-lookup"><span data-stu-id="9b550-122">To copy and paste a functoid</span></span>  
  
1.  <span data-ttu-id="9b550-123">Dans l'Explorateur de solutions, ouvrez le projet BizTalk, puis double-cliquez sur le mappage pour ouvrir ce dernier dans le Mappeur BizTalk.</span><span class="sxs-lookup"><span data-stu-id="9b550-123">In Solution Explorer, open the BizTalk project, and then double-click the map to open it in BizTalk Mapper.</span></span>  
  
2.  <span data-ttu-id="9b550-124">Sélectionnez le fonctoid à copier.</span><span class="sxs-lookup"><span data-stu-id="9b550-124">Select the functoid you want to copy.</span></span> <span data-ttu-id="9b550-125">Pour sélectionnez plusieurs fonctoids, cliquez sur un fonctoid, maintenez la touche CTRL enfoncée, puis cliquez sur les autres fonctoids.</span><span class="sxs-lookup"><span data-stu-id="9b550-125">To select multiple functoids, click one functoid, hold down the CTRL key, and then click the other functoids.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="9b550-126">Vous pouvez utiliser la fonction de « sélection dans le Ruban » pour sélectionner plusieurs liens et/ou fonctoids.</span><span class="sxs-lookup"><span data-stu-id="9b550-126">You can use the “ribbon select” operation to select multiple link(s) and/or functoid(s).</span></span> <span data-ttu-id="9b550-127">Pour plus d’informations, consultez [comment sélectionner plusieurs liens et fonctoids](../core/how-to-select-multiple-links-and-functoids.md).</span><span class="sxs-lookup"><span data-stu-id="9b550-127">For more information, see [How to Select Multiple Links and Functoids](../core/how-to-select-multiple-links-and-functoids.md).</span></span>  
  
3.  <span data-ttu-id="9b550-128">Avec le bouton droit de la sélection, puis cliquez sur **copie**.</span><span class="sxs-lookup"><span data-stu-id="9b550-128">Right-click the selection, and then click **Copy**.</span></span> <span data-ttu-id="9b550-129">Vous pouvez également cliquer sur **copie** à partir de Visual Studio **modifier** menu ou appuyez sur CTRL + C du clavier.</span><span class="sxs-lookup"><span data-stu-id="9b550-129">Alternatively, you can either click **Copy** from the Visual Studio’s **Edit** menu or press CTRL+C on the keyboard.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="9b550-130">Pour obtenir la liste des raccourcis clavier, consultez [raccourcis clavier de Mappeur BizTalk](../core/biztalk-mapper-keyboard-shortcuts.md).</span><span class="sxs-lookup"><span data-stu-id="9b550-130">For a list of keyboard shortcuts, see [BizTalk Mapper Keyboard Shortcuts](../core/biztalk-mapper-keyboard-shortcuts.md).</span></span>  
  
4.  <span data-ttu-id="9b550-131">Positionnez le pointeur à l'emplacement où vous voulez coller le fonctoid.</span><span class="sxs-lookup"><span data-stu-id="9b550-131">Place the cursor where you wish to paste the functoid.</span></span>  
  
5.  <span data-ttu-id="9b550-132">Avec le bouton droit sur la page de grille, puis cliquez sur **coller**.</span><span class="sxs-lookup"><span data-stu-id="9b550-132">Right-click on the grid page, and then click **Paste**.</span></span> <span data-ttu-id="9b550-133">Vous pouvez également cliquer sur **coller** à partir de Visual Studio **modifier** menu ou appuyez sur CTRL + V du clavier.</span><span class="sxs-lookup"><span data-stu-id="9b550-133">Alternatively, you can either click **Paste** from the Visual Studio’s **Edit** menu or press CTRL+V on the keyboard.</span></span> <span data-ttu-id="9b550-134">Une copie du fonctoid ou du groupe de fonctoids sélectionné s'affiche dans le nouvel emplacement.</span><span class="sxs-lookup"><span data-stu-id="9b550-134">A copy of the selected functoid or group of functoids appears at the new location.</span></span>  
  
### <a name="to-cut-and-paste-a-functoid"></a><span data-ttu-id="9b550-135">Pour couper et coller un fonctoid</span><span class="sxs-lookup"><span data-stu-id="9b550-135">To cut and paste a functoid</span></span>  
  
1.  <span data-ttu-id="9b550-136">Dans l'Explorateur de solutions, ouvrez le projet BizTalk, puis double-cliquez sur le mappage pour ouvrir ce dernier dans le Mappeur BizTalk.</span><span class="sxs-lookup"><span data-stu-id="9b550-136">In Solution Explorer, open the BizTalk project, and then double-click the map to open it in BizTalk Mapper.</span></span>  
  
2.  <span data-ttu-id="9b550-137">Sélectionnez le fonctoid à couper.</span><span class="sxs-lookup"><span data-stu-id="9b550-137">Select the functoid you want to cut.</span></span> <span data-ttu-id="9b550-138">Pour sélectionnez plusieurs fonctoids, cliquez sur un fonctoid, maintenez la touche CTRL enfoncée, puis cliquez sur les autres fonctoids.</span><span class="sxs-lookup"><span data-stu-id="9b550-138">To select multiple functoids, click one functoid, hold down the CTRL key, and then click the other functoids.</span></span>  
  
3.  <span data-ttu-id="9b550-139">Avec le bouton droit de la sélection, puis cliquez sur **couper**.</span><span class="sxs-lookup"><span data-stu-id="9b550-139">Right-click the selection, and then click **Cut**.</span></span> <span data-ttu-id="9b550-140">Vous pouvez également cliquer sur **couper** à partir de Visual Studio **modifier** menu ou appuyez sur CTRL + X sur le clavier.</span><span class="sxs-lookup"><span data-stu-id="9b550-140">Alternatively, you can either click **Cut** from the Visual Studio’s **Edit** menu or press CTRL+X on the keyboard.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="9b550-141">Pour obtenir la liste des raccourcis clavier, consultez [raccourcis clavier de Mappeur BizTalk](../core/biztalk-mapper-keyboard-shortcuts.md).</span><span class="sxs-lookup"><span data-stu-id="9b550-141">For a list of keyboard shortcuts, see [BizTalk Mapper Keyboard Shortcuts](../core/biztalk-mapper-keyboard-shortcuts.md).</span></span>  
  
4.  <span data-ttu-id="9b550-142">Positionnez le pointeur à l'emplacement où vous voulez coller le fonctoid.</span><span class="sxs-lookup"><span data-stu-id="9b550-142">Place the cursor where you wish to paste the functoid.</span></span>  
  
5.  <span data-ttu-id="9b550-143">Avec le bouton droit sur la page de grille, puis cliquez sur **coller**.</span><span class="sxs-lookup"><span data-stu-id="9b550-143">Right-click on the grid page, and then click **Paste**.</span></span> <span data-ttu-id="9b550-144">Vous pouvez également cliquer sur **coller** à partir de Visual Studio **modifier** menu ou appuyez sur CTRL + V du clavier.</span><span class="sxs-lookup"><span data-stu-id="9b550-144">Alternatively, you can either click **Paste** from the Visual Studio’s **Edit** menu or press CTRL+V on the keyboard.</span></span> <span data-ttu-id="9b550-145">Le fonctoid ou groupe de fonctoids sélectionné est supprimé de son emplacement actuel et s'affiche dans son nouvel emplacement.</span><span class="sxs-lookup"><span data-stu-id="9b550-145">The selected functoid or group of functoids are deleted from the existing location and appear at the new location.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b550-146">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9b550-146">See Also</span></span>  
 [<span data-ttu-id="9b550-147">À l’aide des fonctoids pour créer des mappages plus complexes</span><span class="sxs-lookup"><span data-stu-id="9b550-147">Using Functoids to Create More Complex Mappings</span></span>](../core/using-functoids-to-create-more-complex-mappings.md)