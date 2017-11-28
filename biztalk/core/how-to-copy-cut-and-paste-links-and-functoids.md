---
title: Comment copier, couper et coller des liens et fonctoids | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 80b4792a-5ff6-4603-96cd-b3d3d530c12f
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5eec0ddc164af936e1c3739e4da167753a6e58c8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-copy-cut-and-paste-links-and-functoids"></a><span data-ttu-id="75dbf-102">Coupage, copie et collage de liens et fonctoid</span><span class="sxs-lookup"><span data-stu-id="75dbf-102">How to Copy, Cut, and Paste Links and Functoids</span></span>
<span data-ttu-id="75dbf-103">La fonction copier/couper/coller dans le Mappeur BizTalk permet de réutiliser une relation.</span><span class="sxs-lookup"><span data-stu-id="75dbf-103">The copy/cut/paste feature in the BizTalk Mapper enables the reusability of a relationship.</span></span> <span data-ttu-id="75dbf-104">Cette rubrique fournit des instructions pas à pas pour copier, couper et coller des fonctoids et/or des liens dans un mappage.</span><span class="sxs-lookup"><span data-stu-id="75dbf-104">This topic provides step-by-step instructions to copy, cut, and paste functoids and/or links in a map.</span></span>  
  
 <span data-ttu-id="75dbf-105">Vous pouvez utiliser la fonction copier/coller pour réutiliser un ensemble de fonctoids et/ou de liens.</span><span class="sxs-lookup"><span data-stu-id="75dbf-105">You can use the copy/paste feature when you want to reuse a set of functoids and/or links.</span></span> <span data-ttu-id="75dbf-106">Lorsque vous voulez supprimer la sélection de l'emplacement existant et la déplacer vers un nouvel emplacement, vous pouvez utiliser la fonction couper/coller.</span><span class="sxs-lookup"><span data-stu-id="75dbf-106">And, when you want to remove the selection from the existing location and move it to a new location, you can use the cut/paste feature.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="75dbf-107">Vous trouvez que la fonction couper/coller et la fonction de déplacement sont similaires ?</span><span class="sxs-lookup"><span data-stu-id="75dbf-107">Do you feel cut/paste feature and the move feature are similar?</span></span> <span data-ttu-id="75dbf-108">Il existe une différence.</span><span class="sxs-lookup"><span data-stu-id="75dbf-108">There is a difference.</span></span> <span data-ttu-id="75dbf-109">Lorsque vous sélectionnez couper, seuls les fonctoids et/ou les liens de votre sélection sont supprimés de la page de grille source.</span><span class="sxs-lookup"><span data-stu-id="75dbf-109">When you select cut, only the functoids and/or links in your selection are removed from the source grid page.</span></span> <span data-ttu-id="75dbf-110">Mais, lorsque vous sélectionnez déplacer, tous les fonctoids et liens de la relation (indépendamment de la sélection) sont supprimés de manière récursive de la page de grille source.</span><span class="sxs-lookup"><span data-stu-id="75dbf-110">But, when you select move, all the functoids and links in the relationship (irrespective of the selection), recursively, are removed from the source grid page.</span></span> <span data-ttu-id="75dbf-111">Pour plus d’informations sur le déplacement d’une relation, consultez [comment déplacer une relation entre les Pages de grille](../core/how-to-move-a-relationship-between-grid-pages.md).</span><span class="sxs-lookup"><span data-stu-id="75dbf-111">For more information about moving a relationship, see [How to Move a Relationship Between Grid Pages](../core/how-to-move-a-relationship-between-grid-pages.md).</span></span>  
  
 <span data-ttu-id="75dbf-112">Lorsque vous copiez/coupez un ensemble de fonctoids et/ou liens, fonctoids, étiquettes, commentaires et valeurs constantes (ainsi que les espaces réservés appropriés) associés qu’ensemble sont conservés.</span><span class="sxs-lookup"><span data-stu-id="75dbf-112">When you copy/cut a set of functoids and/or links, the functoids, labels, comments, and the constant values (along with the correct place holders) associated with that set are retained.</span></span>  
  
 <span data-ttu-id="75dbf-113">Vous pouvez copier/couper uniquement ces éléments de mappage :</span><span class="sxs-lookup"><span data-stu-id="75dbf-113">You can copy/cut only these map items:</span></span>  
  
-   <span data-ttu-id="75dbf-114">Lien du schéma source au schéma de destination.</span><span class="sxs-lookup"><span data-stu-id="75dbf-114">Link from source to target schema.</span></span>  
  
-   <span data-ttu-id="75dbf-115">Lien du fonctoid au nœud de schéma, si et seulement si le fonctoid est également sélectionné avec le lien.</span><span class="sxs-lookup"><span data-stu-id="75dbf-115">Link from functoid to schema node, if and only if the “functoid” is also selected along with the link.</span></span>  
  
-   <span data-ttu-id="75dbf-116">Lien du fonctoid au fonctoid, si et seulement si les fonctoids sont sélectionnés avec le lien.</span><span class="sxs-lookup"><span data-stu-id="75dbf-116">Link from functoid to functoid, if and only if both the functoids are selected along with the link.</span></span>  
  
 <span data-ttu-id="75dbf-117">Vous pouvez copier/couper des fonctoids et/ou des liens à partir de :</span><span class="sxs-lookup"><span data-stu-id="75dbf-117">You can copy/cut functoids and/or links from:</span></span>  
  
-   <span data-ttu-id="75dbf-118">Au sein de la même page de grille d'un mappage</span><span class="sxs-lookup"><span data-stu-id="75dbf-118">Within the same grid page of a map</span></span>  
  
-   <span data-ttu-id="75dbf-119">D'une page de grille à l'autre dans le même mappage</span><span class="sxs-lookup"><span data-stu-id="75dbf-119">One grid page to the other in the same map</span></span>  
  
-   <span data-ttu-id="75dbf-120">D'un mappage à l'autre dans la même instance de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="75dbf-120">One map to the other in the same instance of Visual Studio</span></span>  
  
-   <span data-ttu-id="75dbf-121">Entre différentes instances de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="75dbf-121">Across different instances of Visual Studio</span></span>  
  
 <span data-ttu-id="75dbf-122">Vous pouvez annuler ou rétablir les opérations Couper et Coller.</span><span class="sxs-lookup"><span data-stu-id="75dbf-122">You can undo or redo the cut and paste operations.</span></span> <span data-ttu-id="75dbf-123">Pour plus d’informations, consultez [comment annuler ou rétablir les opérations de l’utilisateur](../core/how-to-undo-or-redo-user-operations.md).</span><span class="sxs-lookup"><span data-stu-id="75dbf-123">For more information, see [How to Undo or Redo User Operations](../core/how-to-undo-or-redo-user-operations.md).</span></span>  
  
 <span data-ttu-id="75dbf-124">En outre, vous devez prendre en compte les points suivants lors du collage de liens :</span><span class="sxs-lookup"><span data-stu-id="75dbf-124">In addition to this, you must consider the following points while pasting links:</span></span>  
  
-   <span data-ttu-id="75dbf-125">Un lien entre les schémas source et cible peut être collé si et seulement si le mappage actuel, où le lien est collé, contient un nœud source ainsi qu'un nœud cible dont le XPath est identique au XPath des nœuds source et cible pour le lien collé.</span><span class="sxs-lookup"><span data-stu-id="75dbf-125">A link between the source and target schema can be pasted if and only if the current map, where the link is being pasted, contains a source node as well as a target node whose XPath is identical to the XPath of the source and target nodes for the link being pasted.</span></span>  
  
-   <span data-ttu-id="75dbf-126">Un lien entre les schémas source et cible peut être collé si et seulement s'il n'existe aucun lien entre les nœuds source et cible susmentionnés.</span><span class="sxs-lookup"><span data-stu-id="75dbf-126">A link between the source and target schema can be pasted if and only if there is no existing link between the aforesaid source and target nodes.</span></span>  
  
-   <span data-ttu-id="75dbf-127">Un lien entre un fonctoid et le schéma de destination peut être collé si et seulement s'il existe un nœud cible dont le XPath est identique au XPath du nœud cible du lien collé.</span><span class="sxs-lookup"><span data-stu-id="75dbf-127">A link from a functoid to target schema can be pasted if and only if there exists a target node whose XPath is same as the XPath of the target node of the link being pasted.</span></span>  
  
-   <span data-ttu-id="75dbf-128">Un lien entre un schéma source et un fonctoid peut être collé si et seulement s'il existe un nœud source dont le XPath est identique au XPath du nœud source du lien collé.</span><span class="sxs-lookup"><span data-stu-id="75dbf-128">A link from a source schema to a functoid can be pasted if and only if there exists a source node whose XPath is same as the XPath of the source node of the link being pasted.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="75dbf-129">Si vous sélectionnez plusieurs éléments (liens et/ou fonctoids) dont certaines ne peuvent pas être coupés/copiés, puis que vous exécutez une commande de coupe/copie, le message d'avertissement « Impossible de couper/copier certains des éléments sélectionnés » s'affiche dans la barre d'état de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="75dbf-129">When you select multiple items (links and/or functoids) such that some of them cannot be cut/copied, then on executing the cut/copy command, the status bar in Visual Studio displays a warning message “Some of the selected items could not be cut/copied.”</span></span> <span data-ttu-id="75dbf-130">Le message fournit également tous les détails utiles.</span><span class="sxs-lookup"><span data-stu-id="75dbf-130">The message also displays relevant details.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="75dbf-131">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="75dbf-131">Prerequisites</span></span>  
 <span data-ttu-id="75dbf-132">Les instructions suivantes requièrent que le Mappeur BizTalk est en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="75dbf-132">These instructions require that BizTalk Mapper is running.</span></span>  
  
### <a name="to-copy-and-paste-a-relationship"></a><span data-ttu-id="75dbf-133">Pour copier et coller une relation</span><span class="sxs-lookup"><span data-stu-id="75dbf-133">To copy and paste a relationship</span></span>  
  
1.  <span data-ttu-id="75dbf-134">Dans l'Explorateur de solutions, ouvrez le projet BizTalk, puis double-cliquez sur le mappage pour ouvrir ce dernier dans le Mappeur BizTalk.</span><span class="sxs-lookup"><span data-stu-id="75dbf-134">In Solution Explorer, open the BizTalk project, and then double-click the map to open it in BizTalk Mapper.</span></span>  
  
2.  <span data-ttu-id="75dbf-135">Sélectionnez les fonctoids et/ou les liens à copier.</span><span class="sxs-lookup"><span data-stu-id="75dbf-135">Select the functoids and/or links you want to copy.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="75dbf-136">Vous pouvez les sélectionner en maintenant appuyée la touche CTRL et en sélectionnant les fonctoids et/ou liens souhaités ou en faisant un glisser-déplacer entre les liens pour former un rectangle de sélection.</span><span class="sxs-lookup"><span data-stu-id="75dbf-136">You can select either by holding down the CTRL key, and then selecting the desired functoids and/or links or by dragging and dropping the mouse across the links to form a rectangular selection.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="75dbf-137">Vous pouvez utiliser la fonction de « sélection dans le Ruban » pour sélectionner plusieurs liens et/ou fonctoids.</span><span class="sxs-lookup"><span data-stu-id="75dbf-137">You can use the “ribbon select” operation to select multiple link(s) and/or functoid(s).</span></span> <span data-ttu-id="75dbf-138">Pour plus d’informations, consultez [comment sélectionner plusieurs liens et fonctoids](../core/how-to-select-multiple-links-and-functoids.md).</span><span class="sxs-lookup"><span data-stu-id="75dbf-138">For more information, see [How to Select Multiple Links and Functoids](../core/how-to-select-multiple-links-and-functoids.md).</span></span>  
  
3.  <span data-ttu-id="75dbf-139">Cliquez sur la sélection.</span><span class="sxs-lookup"><span data-stu-id="75dbf-139">Right-click the selection.</span></span> <span data-ttu-id="75dbf-140">puis cliquez sur **copie**.</span><span class="sxs-lookup"><span data-stu-id="75dbf-140">and then click **Copy**.</span></span> <span data-ttu-id="75dbf-141">Vous pouvez également appuyer sur CTRL+C sur le clavier.</span><span class="sxs-lookup"><span data-stu-id="75dbf-141">Alternatively, you can press CTRL+C on the keyboard.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="75dbf-142">Pour obtenir la liste des raccourcis clavier, consultez [raccourcis clavier de Mappeur BizTalk](../core/biztalk-mapper-keyboard-shortcuts.md).</span><span class="sxs-lookup"><span data-stu-id="75dbf-142">For a list of keyboard shortcuts, see [BizTalk Mapper Keyboard Shortcuts](../core/biztalk-mapper-keyboard-shortcuts.md).</span></span>  
  
4.  <span data-ttu-id="75dbf-143">Placez le curseur là où vous voulez coller la sélection.</span><span class="sxs-lookup"><span data-stu-id="75dbf-143">Place the cursor where you wish to paste the selection.</span></span>  
  
5.  <span data-ttu-id="75dbf-144">Avec le bouton droit sur la page de grille, puis cliquez sur **coller**.</span><span class="sxs-lookup"><span data-stu-id="75dbf-144">Right-click on the grid page, and then click **Paste**.</span></span> <span data-ttu-id="75dbf-145">Vous pouvez également appuyer sur CTRL+V sur le clavier.</span><span class="sxs-lookup"><span data-stu-id="75dbf-145">Alternatively, you can select and press CTRL+V on the keyboard.</span></span> <span data-ttu-id="75dbf-146">Une copie de la sélection apparaît au nouvel emplacement.</span><span class="sxs-lookup"><span data-stu-id="75dbf-146">A copy of the selection appears at the new location.</span></span>  
  
### <a name="to-cut-and-paste-a-relationship"></a><span data-ttu-id="75dbf-147">Pour couper et coller une relation</span><span class="sxs-lookup"><span data-stu-id="75dbf-147">To cut and paste a relationship</span></span>  
  
1.  <span data-ttu-id="75dbf-148">Dans l'Explorateur de solutions, ouvrez le projet BizTalk, puis double-cliquez sur le mappage pour ouvrir ce dernier dans le Mappeur BizTalk.</span><span class="sxs-lookup"><span data-stu-id="75dbf-148">In Solution Explorer, open the BizTalk project, and then double-click the map to open it in BizTalk Mapper.</span></span>  
  
2.  <span data-ttu-id="75dbf-149">Sélectionnez les fonctoids et/ou les liens à couper.</span><span class="sxs-lookup"><span data-stu-id="75dbf-149">Select the functoids and/or links you want to cut.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="75dbf-150">Vous pouvez les sélectionner en maintenant appuyée la touche CTRL et en sélectionnant les fonctoids et/ou liens souhaités ou en faisant un glisser-déplacer entre les liens pour former un rectangle de sélection.</span><span class="sxs-lookup"><span data-stu-id="75dbf-150">You can select either by holding down the CTRL key, and then selecting the desired functoids and/or links or by dragging and dropping the mouse across the links to form a rectangular selection.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="75dbf-151">Vous pouvez utiliser la fonction de « sélection dans le Ruban » pour sélectionner plusieurs liens et/ou fonctoids.</span><span class="sxs-lookup"><span data-stu-id="75dbf-151">You can use the “ribbon select” operation to select multiple link(s) and/or functoid(s).</span></span> <span data-ttu-id="75dbf-152">Pour plus d’informations, consultez [comment sélectionner plusieurs liens et fonctoids](../core/how-to-select-multiple-links-and-functoids.md).</span><span class="sxs-lookup"><span data-stu-id="75dbf-152">For more information, see [How to Select Multiple Links and Functoids](../core/how-to-select-multiple-links-and-functoids.md).</span></span>  
  
3.  <span data-ttu-id="75dbf-153">Avec le bouton droit de la sélection, puis cliquez sur **couper**.</span><span class="sxs-lookup"><span data-stu-id="75dbf-153">Right-click the selection, and then click **Cut**.</span></span> <span data-ttu-id="75dbf-154">Vous pouvez également appuyer sur CTRL+X sur le clavier.</span><span class="sxs-lookup"><span data-stu-id="75dbf-154">Alternatively, you can press CTRL+X on the keyboard.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="75dbf-155">Pour obtenir la liste des raccourcis clavier, consultez [raccourcis clavier de Mappeur BizTalk](../core/biztalk-mapper-keyboard-shortcuts.md).</span><span class="sxs-lookup"><span data-stu-id="75dbf-155">For a list of keyboard shortcuts, see [BizTalk Mapper Keyboard Shortcuts](../core/biztalk-mapper-keyboard-shortcuts.md).</span></span>  
  
4.  <span data-ttu-id="75dbf-156">Placez le curseur là où vous voulez coller la sélection.</span><span class="sxs-lookup"><span data-stu-id="75dbf-156">Place the cursor where you wish to paste the selection.</span></span>  
  
5.  <span data-ttu-id="75dbf-157">Avec le bouton droit sur la page de grille, puis cliquez sur **coller**.</span><span class="sxs-lookup"><span data-stu-id="75dbf-157">Right-click on the grid page, and then click **Paste**.</span></span> <span data-ttu-id="75dbf-158">Vous pouvez également appuyer sur CTRL+V sur le clavier.</span><span class="sxs-lookup"><span data-stu-id="75dbf-158">Alternatively, you can select and press CTRL+V on the keyboard.</span></span> <span data-ttu-id="75dbf-159">La sélection est supprimée de l'emplacement existant et apparaît au nouvel emplacement.</span><span class="sxs-lookup"><span data-stu-id="75dbf-159">The selection is deleted from the existing location and appears at the new location.</span></span>