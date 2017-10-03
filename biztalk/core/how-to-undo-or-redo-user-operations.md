---
title: "Comment annuler ou rétablir les opérations de l’utilisateur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1cb3708e-a9c2-4795-aba0-9c6d9635e08c
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f6f47071ee003a896b66120c0fd81a121ab73230
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-undo-or-redo-user-operations"></a><span data-ttu-id="f2a3f-102">Annulation ou rétablissement des opérations de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="f2a3f-102">How to Undo or Redo User Operations</span></span>
<span data-ttu-id="f2a3f-103">La prise en charge des options Annuler/Rétablir constitue une aide précieuse fournie par le Mappeur BizTalk.</span><span class="sxs-lookup"><span data-stu-id="f2a3f-103">The support for undo/redo is yet another usability aid provided by the BizTalk Mapper.</span></span> <span data-ttu-id="f2a3f-104">Si vous n'êtes pas satisfait des modifications effectuées, ou si vous avez apporté une modification par erreur, vous pouvez utiliser l'option Annuler pour revenir à un état antérieur à partir duquel vous reprendrez l'opération.</span><span class="sxs-lookup"><span data-stu-id="f2a3f-104">If you are not satisfied with modifications you have made, or if you have made a change by mistake, you can use undo to gradually come back to an earlier "untouched" state, and resume from there.</span></span> <span data-ttu-id="f2a3f-105">L'option Rétablir permet de réappliquer les actions de modification que vous avez annulées.</span><span class="sxs-lookup"><span data-stu-id="f2a3f-105">Redo allows you to reapply the editing actions that have been undone.</span></span> <span data-ttu-id="f2a3f-106">Cette rubrique fournit des informations sur les opérations que vous pouvez annuler/rétablir.</span><span class="sxs-lookup"><span data-stu-id="f2a3f-106">This topic provides information about the operations that you can undo/redo.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="f2a3f-107">Vous pouvez annuler une opération lorsque vous avez apporté au moins une modification au mappage.</span><span class="sxs-lookup"><span data-stu-id="f2a3f-107">You can undo an operation only when you have performed at least one edit operation on the map.</span></span> <span data-ttu-id="f2a3f-108">L'option Rétablir n'est disponible que si vous avez utilisé la commande Annuler.</span><span class="sxs-lookup"><span data-stu-id="f2a3f-108">Redo is unavailable unless you have used the undo command.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="f2a3f-109">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="f2a3f-109">Prerequisites</span></span>  
 <span data-ttu-id="f2a3f-110">Les instructions suivantes requièrent que le Mappeur BizTalk est en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="f2a3f-110">These instructions require that BizTalk Mapper is running.</span></span>  
  
## <a name="what-can-you-undoredo"></a><span data-ttu-id="f2a3f-111">Opérations qu'il est possible d'annuler/rétablir</span><span class="sxs-lookup"><span data-stu-id="f2a3f-111">What can you undo/redo?</span></span>  
 <span data-ttu-id="f2a3f-112">Vous pouvez annuler/rétablir toutes les opérations de modification,</span><span class="sxs-lookup"><span data-stu-id="f2a3f-112">You can undo/redo all editing operations.</span></span> <span data-ttu-id="f2a3f-113">à savoir :</span><span class="sxs-lookup"><span data-stu-id="f2a3f-113">The operations that can be undone/redone are as follows:</span></span>  
  
-   <span data-ttu-id="f2a3f-114">Couper/copier/coller des fonctoids et/ou des liens</span><span class="sxs-lookup"><span data-stu-id="f2a3f-114">Cutting/copying/pasting functoids and/or link</span></span>  
  
     <span data-ttu-id="f2a3f-115">Il ne suffit pas de sélectionner et de copier des éléments (liens/fonctoids) pour les annuler et les rétablir.</span><span class="sxs-lookup"><span data-stu-id="f2a3f-115">You cannot undo or redo any number of items (links/functoids) by simply selecting and copying them.</span></span> <span data-ttu-id="f2a3f-116">La fonction de copie ne change rien au mappage.</span><span class="sxs-lookup"><span data-stu-id="f2a3f-116">Copy function does not change anything on the map.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f2a3f-117">Pour plus d’informations sur la façon de couper/copier/coller un fonctoid, consultez [comment copier, couper et coller un fonctoid](../core/how-to-copy-cut-and-paste-a-functoid.md).</span><span class="sxs-lookup"><span data-stu-id="f2a3f-117">For information about how to cut/copy/paste a functoid, see [How to Copy, Cut, and Paste a Functoid](../core/how-to-copy-cut-and-paste-a-functoid.md).</span></span> <span data-ttu-id="f2a3f-118">Pour plus d’informations sur la façon de couper/copier/coller fonctoid et un lien, consultez [comment copier, couper et collez les liens et fonctoids](../core/how-to-copy-cut-and-paste-links-and-functoids.md).</span><span class="sxs-lookup"><span data-stu-id="f2a3f-118">For more information about how to cut/copy/paste functoid and link, see [How to Copy, Cut, and Paste Links and Functoids](../core/how-to-copy-cut-and-paste-links-and-functoids.md).</span></span>  
  
-   <span data-ttu-id="f2a3f-119">Lier un nœud source à un nœud cible, un nœud source à un fonctoid, un fonctoid à un autre ou un fonctoid à un nœud cible</span><span class="sxs-lookup"><span data-stu-id="f2a3f-119">Linking a source node to a target node, or a source node to a functoid, a functoid to another functoid, or a functoid to a target node</span></span>  
  
-   <span data-ttu-id="f2a3f-120">Supprimer des fonctoids et/ou des liens</span><span class="sxs-lookup"><span data-stu-id="f2a3f-120">Deleting functoids and/or links</span></span>  
  
-   <span data-ttu-id="f2a3f-121">Déplacer les liens et les fonctoids sélectionnés vers une autre page de la grille</span><span class="sxs-lookup"><span data-stu-id="f2a3f-121">Moving selected links and functoids to another grid page</span></span>  
  
-   <span data-ttu-id="f2a3f-122">Ajouter, déplacer, réorganiser ou supprimer des pages de la grille</span><span class="sxs-lookup"><span data-stu-id="f2a3f-122">Adding, moving, reordering, or deleting grid pages</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f2a3f-123">Pour plus d’informations sur l’ajout, déplacement, la réorganisation ou la suppression de pages de grille, consultez [comment réorganiser les Pages de grille](../core/how-to-reorder-grid-pages.md).</span><span class="sxs-lookup"><span data-stu-id="f2a3f-123">For information on adding, moving, reordering, or deleting grid pages, see [How to Reorder Grid Pages](../core/how-to-reorder-grid-pages.md).</span></span>  
  
-   <span data-ttu-id="f2a3f-124">Sélectionner les schémas source et de destination lors de la création d'un mappage.</span><span class="sxs-lookup"><span data-stu-id="f2a3f-124">Selecting source and destination schemas while creating a map</span></span>  
  
-   <span data-ttu-id="f2a3f-125">Remplacer les schémas source et de destination</span><span class="sxs-lookup"><span data-stu-id="f2a3f-125">Replacing source/destination schema</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f2a3f-126">Pour plus d’informations sur la façon de remplacer les schémas source et de destination, consultez [comment remplacer les schémas](../core/how-to-replace-schemas.md).</span><span class="sxs-lookup"><span data-stu-id="f2a3f-126">For information on how to replace source/destination schema, see [How to Replace Schemas](../core/how-to-replace-schemas.md).</span></span>  
  
-   <span data-ttu-id="f2a3f-127">Configurer les paramètres d'entrée des fonctoids</span><span class="sxs-lookup"><span data-stu-id="f2a3f-127">Configuring input parameters for functoids</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f2a3f-128">Pour plus d’informations, consultez [comment configurer les paramètres d’entrée du fonctoid](../core/how-to-configure-functoid-input-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="f2a3f-128">For more information, see [How to Configure Functoid Input Parameters](../core/how-to-configure-functoid-input-parameters.md).</span></span>  
  
-   <span data-ttu-id="f2a3f-129">Configurer et modifier les étiquettes des liens</span><span class="sxs-lookup"><span data-stu-id="f2a3f-129">Setting/editing labels for links</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f2a3f-130">Pour plus d’informations, consultez [étiquette un lien à](../core/how-to-label-a-link.md).</span><span class="sxs-lookup"><span data-stu-id="f2a3f-130">For more information, see [How to Label a Link](../core/how-to-label-a-link.md).</span></span>  
  
-   <span data-ttu-id="f2a3f-131">Définir/éditer des étiquettes et/ou des commentaires pour les fonctoids</span><span class="sxs-lookup"><span data-stu-id="f2a3f-131">Setting/editing labels and/or comments for functoids</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f2a3f-132">Pour plus d’informations, consultez [étiquette et commentaires à un fonctoid](../core/how-to-label-and-comment-a-functoid.md).</span><span class="sxs-lookup"><span data-stu-id="f2a3f-132">For more information, see [How to Label and Comment a Functoid](../core/how-to-label-and-comment-a-functoid.md).</span></span>  
  
-   <span data-ttu-id="f2a3f-133">Ignorer les propriétés Espaces de noms des liaisons et Priorité des types de scripts pour la grille du Mappeur.</span><span class="sxs-lookup"><span data-stu-id="f2a3f-133">Ignore Namespaces for Links and Script Type Precedence properties for Mapper grid.</span></span>  
  
-   <span data-ttu-id="f2a3f-134">Remplacer une liaison en déplaçant l'un de ses points de terminaison d'un nœud ou fonctoid vers un autre nœud ou fonctoid.</span><span class="sxs-lookup"><span data-stu-id="f2a3f-134">Replacing a link by dragging one end point of a link from a node or functoid to anther node or functoid.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f2a3f-135">Pour plus d’informations, consultez [comment créer des liens](../core/how-to-create-links.md).</span><span class="sxs-lookup"><span data-stu-id="f2a3f-135">For more information, see [How to Create Links](../core/how-to-create-links.md).</span></span>  
  
-   <span data-ttu-id="f2a3f-136">Exécution de plusieurs modifications dans le **configurer \<fonctoid > fonctoid** boîte de dialogue, qui est traitée comme une seule opération.</span><span class="sxs-lookup"><span data-stu-id="f2a3f-136">Performing multiple modifications in the **Configure \<Functoid> Functoid** dialog box, which is treated as a single operation.</span></span>  
  
-   <span data-ttu-id="f2a3f-137">Faire glisser des liens et/ou des fonctoids sur la grille du Mappeur.</span><span class="sxs-lookup"><span data-stu-id="f2a3f-137">Dragging functoid(s) and/or link(s) within the Mapper grid.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f2a3f-138">Pour plus d’informations, consultez [comment déplacer une relation entre les Pages de grille](../core/how-to-move-a-relationship-between-grid-pages.md).</span><span class="sxs-lookup"><span data-stu-id="f2a3f-138">For more information, see [How to Move a Relationship Between Grid Pages](../core/how-to-move-a-relationship-between-grid-pages.md).</span></span>  
  
## <a name="how-can-you-undoredo-any-operation"></a><span data-ttu-id="f2a3f-139">Annulation et rétablissement d'une opération</span><span class="sxs-lookup"><span data-stu-id="f2a3f-139">How can you undo/redo any operation?</span></span>  
 <span data-ttu-id="f2a3f-140">Vous pouvez annuler/rétablir une opération à l'aide de l'une des méthodes suivantes :</span><span class="sxs-lookup"><span data-stu-id="f2a3f-140">You can undo/redo an operation in one of the following ways:</span></span>  
  
-   <span data-ttu-id="f2a3f-141">À partir de Visual Studio **modifier** menu.</span><span class="sxs-lookup"><span data-stu-id="f2a3f-141">From the Visual Studio’s **Edit** menu.</span></span>  
  
-   <span data-ttu-id="f2a3f-142">En cliquant sur les icônes Annuler et Rétablir de la barre d'outils.</span><span class="sxs-lookup"><span data-stu-id="f2a3f-142">Clicking the undo and redo icons on the toolbar.</span></span>  
  
-   <span data-ttu-id="f2a3f-143">En appuyant sur CTRL+Z pour annuler et CTRL+Y pour rétablir.</span><span class="sxs-lookup"><span data-stu-id="f2a3f-143">Pressing CTRL+Z for undo and CTRL+Y for redo.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2a3f-144">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f2a3f-144">See Also</span></span>  
 [<span data-ttu-id="f2a3f-145">Utilisation des Pages de grille</span><span class="sxs-lookup"><span data-stu-id="f2a3f-145">Working with Grid Pages</span></span>](../core/working-with-grid-pages.md)