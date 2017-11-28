---
title: "Comment déplacer et copier des nœuds | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e4f1ec14-c607-4da3-9139-73a61963b819
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a55901e9ba6b27d05dccce0e547df618123ab466
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-move-and-copy-nodes"></a><span data-ttu-id="d79c3-102">Comment déplacer et copier des nœuds</span><span class="sxs-lookup"><span data-stu-id="d79c3-102">How to Move and Copy Nodes</span></span>
<span data-ttu-id="d79c3-103">Il vous arrivera probablement de vouloir déplacer un nœud existant vers un autre emplacement dans l'arborescence de schéma.</span><span class="sxs-lookup"><span data-stu-id="d79c3-103">You will probably encounter situations where you want to move an existing node to a different location in the schema tree.</span></span> <span data-ttu-id="d79c3-104">Vous pourrez gagner du temps si vous effectuez une copie du nœud existant et que vous le collez à un autre endroit de l'arborescence de schéma.</span><span class="sxs-lookup"><span data-stu-id="d79c3-104">You might also be able to save time by making a copy of an existing node and then pasting it into a different location in the schema tree.</span></span> <span data-ttu-id="d79c3-105">Cette rubrique contient des instructions détaillées pour exécuter ces tâches.</span><span class="sxs-lookup"><span data-stu-id="d79c3-105">This topic provides step-by-step instructions for performing these tasks.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d79c3-106">L'Éditeur BizTalk ne prend en charge la copie et le collage de nœuds qu'à l'intérieur des schémas et non pas d'un schéma à l'autre.</span><span class="sxs-lookup"><span data-stu-id="d79c3-106">BizTalk Editor supports copying and pasting nodes only within schemas, not between schemas.</span></span>  
  
### <a name="to-move-a-node-within-a-schema"></a><span data-ttu-id="d79c3-107">Pour déplacer un nœud dans un schéma</span><span class="sxs-lookup"><span data-stu-id="d79c3-107">To move a node within a schema</span></span>  
  
1.  <span data-ttu-id="d79c3-108">Si nécessaire, développez l'arborescence de schéma afin d'afficher le nœud que vous comptez déplacer et l'emplacement dans lequel vous souhaitez le placer.</span><span class="sxs-lookup"><span data-stu-id="d79c3-108">If necessary, expand the schema tree to show both the node you are moving and the location to which you want to move it.</span></span> <span data-ttu-id="d79c3-109">Pour plus d’informations sur le développement et réduction de l’arborescence du schéma, consultez [la gestion de l’arborescence du schéma](../core/how-to-manage-the-schema-tree-view.md).</span><span class="sxs-lookup"><span data-stu-id="d79c3-109">For more information about expanding and collapsing the schema tree view, see [Managing the Schema Tree View](../core/how-to-manage-the-schema-tree-view.md).</span></span>  
  
2.  <span data-ttu-id="d79c3-110">Cliquez sur le nœud que vous voulez déplacer et maintenez le bouton de la souris enfoncé pour faire glisser le nœud vers un autre emplacement de l'arborescence.</span><span class="sxs-lookup"><span data-stu-id="d79c3-110">Click and hold the node that you want to move and drag it to another location in the tree.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d79c3-111">Quand vous commencez à déplacer le nœud vers le haut ou le bas de l'arborescence de schéma, le pointeur de la souris se transforme en une flèche vers le haut ou vers le bas, ou en une flèche enfant.</span><span class="sxs-lookup"><span data-stu-id="d79c3-111">When you begin to drag the node up and down the schema tree, the mouse pointer changes to an Up, Down, or child arrow.</span></span> <span data-ttu-id="d79c3-112">Cette flèche indique où le nœud sera placé lorsque vous relâcherez le bouton de la souris : avant le nœud, après le nœud ou en tant qu'enfant du nœud.</span><span class="sxs-lookup"><span data-stu-id="d79c3-112">This arrow indicates where the node will be placed when you release the mouse button, either before the node, after the node, or as a child of the node.</span></span>  
  
#### <a name="to-copy-a-node-within-a-schema"></a><span data-ttu-id="d79c3-113">Pour copier un nœud dans un schéma</span><span class="sxs-lookup"><span data-stu-id="d79c3-113">To copy a node within a schema</span></span>  
  
1.  <span data-ttu-id="d79c3-114">Cliquez sur le nœud que vous souhaitez copier, puis cliquez sur **copie**.</span><span class="sxs-lookup"><span data-stu-id="d79c3-114">Right-click the node that you want to copy, and then click **Copy**.</span></span>  
  
2.  <span data-ttu-id="d79c3-115">Cliquez sur le **enregistrement** nœud ou nœud de groupe dans lequel vous souhaitez insérer le nœud copié, puis cliquez sur **coller**.</span><span class="sxs-lookup"><span data-stu-id="d79c3-115">Right-click the **Record** node or group node into which you want to insert the copied node, and then click **Paste**.</span></span>  
  
     <span data-ttu-id="d79c3-116">La copie du nœud copié est placée à la fin des nœuds enfants de la **enregistrement** nœud ou nœud de groupe que vous avez sélectionné à l’étape 2.</span><span class="sxs-lookup"><span data-stu-id="d79c3-116">The copy of the copied node is placed at the end of the child nodes of the **Record** node or group node you selected in step 2.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d79c3-117">Vous ne pouvez utiliser la fonctionnalité couper/copier/coller que dans un seul schéma.</span><span class="sxs-lookup"><span data-stu-id="d79c3-117">You may only use cut/copy/paste functionality within a single schema.</span></span> <span data-ttu-id="d79c3-118">En d'autres termes, il est impossible de copier des nœuds d'un schéma à l'autre.</span><span class="sxs-lookup"><span data-stu-id="d79c3-118">In other words, you cannot copy nodes from one schema into another schema.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d79c3-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d79c3-119">See Also</span></span>  
 [<span data-ttu-id="d79c3-120">Utilisation des nœuds existants</span><span class="sxs-lookup"><span data-stu-id="d79c3-120">Working with Existing Nodes</span></span>](../core/working-with-existing-nodes.md)