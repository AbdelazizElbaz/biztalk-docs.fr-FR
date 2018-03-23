---
title: Mise en évidence des éléments de la carte | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a2732b36-ca57-4566-ba26-da27a3082f32
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d6bb03969a044c6a474f5d2d1c1e5e1a5067cf81
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/23/2018
---
# <a name="how-to-emphasize-map-items"></a><span data-ttu-id="8984c-102">Mise en évidence des éléments de mappage</span><span class="sxs-lookup"><span data-stu-id="8984c-102">How to Emphasize Map Items</span></span>
<span data-ttu-id="8984c-103">Dans le Mappeur BizTalk, lorsque vous sélectionnez un élément de mappage, tous les liens et fonctoids associés sont mis en évidence.</span><span class="sxs-lookup"><span data-stu-id="8984c-103">In the BizTalk Mapper, when you select a map item, all the associated links and functoids are emphasized.</span></span> <span data-ttu-id="8984c-104">Cela est utile dans les mappages comprenant de nombreux liens, où il est difficile d'identifier une relation et les éléments de schéma associés.</span><span class="sxs-lookup"><span data-stu-id="8984c-104">This is useful in maps with many links, where it is difficult to identify a relationship and the related schema items.</span></span>  
  
 <span data-ttu-id="8984c-105">Lorsque vous sélectionnez un lien, un fonctoid ou un élément de schéma, le Mappeur BizTalk met en évidence la relation et les éléments de schéma.</span><span class="sxs-lookup"><span data-stu-id="8984c-105">When you select a link, a functoid, or a schema element, the BizTalk Mapper emphasizes the related relationship and schema elements.</span></span> <span data-ttu-id="8984c-106">Pour l'élément de mappage sélectionné, l'ensemble des liens entrants et sortants sont mis en gras (de manière récursive) et tous les autres éléments de mappage sont grisés. La capture d'écran suivante montre l'élément de mappage sélectionné en gras et en couleur, et les autres éléments de façon moins distincte.</span><span class="sxs-lookup"><span data-stu-id="8984c-106">For the selected map item, all the incoming links and the outgoing links (recursively) are highlighted in bold, and all the other map items are greyed out. The following screenshot shows the selected map item in bold and color and the other map items appear lighter.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8984c-107">Dans ce contexte, une relation associée signifie que l'ensemble des liens, fonctoids ou éléments de schéma sont directement ou indirectement liés à l'élément de mappage sélectionné.</span><span class="sxs-lookup"><span data-stu-id="8984c-107">In this context, a related relationship means all the links, functoids, or schema elements directly or indirectly linked to the selected map item.</span></span>  
  
 <span data-ttu-id="8984c-108">![Mettre en évidence un élément cartographique](../core/media/mapper-intelliselect.gif "Mapper_IntelliSelect")</span><span class="sxs-lookup"><span data-stu-id="8984c-108">![Emphasizing a map item](../core/media/mapper-intelliselect.gif "Mapper_IntelliSelect")</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="8984c-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="8984c-109">Prerequisites</span></span>  
 <span data-ttu-id="8984c-110">Cette opération nécessite l'exécution du Mappeur BizTalk.</span><span class="sxs-lookup"><span data-stu-id="8984c-110">This operation requires that BizTalk Mapper is running.</span></span>  
  
## <a name="to-emphasize-a-map-item"></a><span data-ttu-id="8984c-111">Pour mettre en évidence un élément de mappage</span><span class="sxs-lookup"><span data-stu-id="8984c-111">To emphasize a map item</span></span>  
  
-   <span data-ttu-id="8984c-112">Cliquez sur un élément de mappage (lien, fonctoid ou élément de schéma).</span><span class="sxs-lookup"><span data-stu-id="8984c-112">Click a map item (a link, a functoid, or a schema element).</span></span> <span data-ttu-id="8984c-113">Vous pouvez voir que tous les autres liens et fonctoids (y compris les nœuds de schéma) associés à l'élément de mappage sélectionné dans la page de grille active sont en évidence.</span><span class="sxs-lookup"><span data-stu-id="8984c-113">You can see that all the other links and functoids (including the schema nodes) associated with the selected map item in the current grid page are highlighted.</span></span>  
  
     <span data-ttu-id="8984c-114">Parfois, pour le nœud sélectionné, il peut y avoir des relations existantes dans d'autres pages de grille.</span><span class="sxs-lookup"><span data-stu-id="8984c-114">Sometimes, for the selected node, there might be relationships existing in other grid pages.</span></span> <span data-ttu-id="8984c-115">Dans ce cas, le Mappeur BizTalk met en évidence l'instance dans la page de grille active, ainsi que l'onglet de la page où existe l'autre relation associée au nœud sélectionné.</span><span class="sxs-lookup"><span data-stu-id="8984c-115">In such a case, the BizTalk Mapper emphasizes the instance in current grid page and also highlights the page tab where the other related relationship to the selected node exists.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8984c-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8984c-116">See Also</span></span>  
 [<span data-ttu-id="8984c-117">À l’aide des fonctionnalités améliorées dans le Mappeur BizTalk</span><span class="sxs-lookup"><span data-stu-id="8984c-117">Using Enhanced Features in BizTalk Mapper</span></span>](../core/using-enhanced-features-in-biztalk-mapper.md)