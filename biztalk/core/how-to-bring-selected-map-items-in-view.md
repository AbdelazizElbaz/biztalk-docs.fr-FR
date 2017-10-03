---
title: "Comment afficher le mappage sélectionné dans la vue des éléments | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3e287b22-5738-428a-aa35-cced877e51ea
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3e10a4b54688c59991f25bb69a3251bee2f4607b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-bring-selected-map-items-in-view"></a><span data-ttu-id="e9910-102">Placement des éléments de mappage sélectionnés dans la vue</span><span class="sxs-lookup"><span data-stu-id="e9910-102">How to Bring Selected Map Items in View</span></span>
<span data-ttu-id="e9910-103">Dans les versions précédentes du Mappeur BizTalk, si un mappage incluait de grands schémas, vous deviez faire défiler manuellement le volet du schéma source, la page de grille et le volet du schéma cible pour afficher tous les éléments de mappage appropriés dans une vue unique.</span><span class="sxs-lookup"><span data-stu-id="e9910-103">With earlier versions of BizTalk Mapper, if a map comprised big schemas, you had to manually scroll the source schema pane, the grid page, and the target schema pane to bring all the relevant map items into a single view.</span></span> <span data-ttu-id="e9910-104">Le Mappeur BizTalk dans [!INCLUDE[prague](../includes/prague-md.md)] permet d'afficher tous les éléments de mappage appropriés du lien/fonctoid sélectionné dans une vue unique en faisant défiler automatiquement la page de grille.</span><span class="sxs-lookup"><span data-stu-id="e9910-104">The BizTalk Mapper with [!INCLUDE[prague](../includes/prague-md.md)] allows you to bring all the relevant map items of the selected functoid/link into a single view by automatically scrolling the grid page.</span></span> <span data-ttu-id="e9910-105">Cette rubrique fournit des informations sur l'exécution de cette opération.</span><span class="sxs-lookup"><span data-stu-id="e9910-105">This topic provides information about how to perform the operation.</span></span>  
  
 <span data-ttu-id="e9910-106">En fonction de votre sélection (un nœud de schéma source, un élément dans la vue de relation ou un nœud de schéma cible), le Mappeur BizTalk fait défiler automatiquement les vues de schéma et de relation de manière synchronisée, tout en affichant la vue de l'ensemble des relations de l'élément sélectionné.</span><span class="sxs-lookup"><span data-stu-id="e9910-106">Depending on your selection (a source schema node, an element in the relationship view, or a target schema node), the BizTalk Mapper auto-scrolls the schema views and relationship view in a synchronized fashion, and displays the overall relationship view of the selected item.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e9910-107">La fonctionnalité de défilement automatique est activée après que le Mappeur BizTalk ait mis en surbrillance tous les éléments de mappage appropriés.</span><span class="sxs-lookup"><span data-stu-id="e9910-107">The auto-scroll feature comes into effect after the BizTalk Mapper has emphasized all the relevant map items.</span></span> <span data-ttu-id="e9910-108">En d'autres termes, les éléments associés à la sélection sont d'abord mis en surbrillance, puis le Mappeur BizTalk utilise le défilement automatique pour placer les éléments associés dans la vue.</span><span class="sxs-lookup"><span data-stu-id="e9910-108">In other words, first the elements related to the selection are highlighted, and then the BizTalk Mapper auto-scrolls to bring the related elements into view.</span></span>  
  
 <span data-ttu-id="e9910-109">Le Mappeur BizTalk ne déplace pas réellement les objets de la grille.</span><span class="sxs-lookup"><span data-stu-id="e9910-109">The BizTalk Mapper does not actually move the grid objects.</span></span> <span data-ttu-id="e9910-110">Ceux-ci retrouvent leurs emplacements respectifs lorsque vous supprimez ou modifiez la sélection.</span><span class="sxs-lookup"><span data-stu-id="e9910-110">The grid objects return to their respective locations when you remove or modify the selection.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="e9910-111">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="e9910-111">Prerequisites</span></span>  
 <span data-ttu-id="e9910-112">Cette opération nécessite l'exécution du Mappeur BizTalk.</span><span class="sxs-lookup"><span data-stu-id="e9910-112">This operation requires that BizTalk Mapper is running.</span></span>  
  
### <a name="to-bring-the-selected-map-items-in-view"></a><span data-ttu-id="e9910-113">Pour placer les éléments de mappage sélectionnés dans la vue</span><span class="sxs-lookup"><span data-stu-id="e9910-113">To bring the selected map items in view</span></span>  
  
1.  <span data-ttu-id="e9910-114">Sur le ruban de l’utilitaire mappeur, cliquez sur l’icône de défilement automatique ![automatique &#45; icône de défilement](../core/media/mapper-intelliscroll.gif "Mapper_IntelliScroll") à désactiver.</span><span class="sxs-lookup"><span data-stu-id="e9910-114">On the Mapper utility ribbon, click the auto-scroll icon ![Auto&#45;scroll icon](../core/media/mapper-intelliscroll.gif "Mapper_IntelliScroll") to switch it OFF.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e9910-115">Le ![automatique &#45; icône de défilement](../core/media/mapper-intelliscroll.gif "Mapper_IntelliScroll") icône est activée (OFF) par défaut.</span><span class="sxs-lookup"><span data-stu-id="e9910-115">The ![Auto&#45;scroll icon](../core/media/mapper-intelliscroll.gif "Mapper_IntelliScroll") icon is switched OFF by default.</span></span>  
  
2.  <span data-ttu-id="e9910-116">Cliquez sur un fonctoid ou un lien. Les éléments de mappage appropriés sont mis en surbrillance.</span><span class="sxs-lookup"><span data-stu-id="e9910-116">Click a functoid or a link; the relevant map items in the relationship are emphasized.</span></span>  
  
     <span data-ttu-id="e9910-117">La figure suivante affiche le lien sélectionné en bleu.</span><span class="sxs-lookup"><span data-stu-id="e9910-117">The following figure displays the selected link in blue color.</span></span> <span data-ttu-id="e9910-118">À son tour, le Mappeur BizTalk met en surbrillance les autres éléments de mappage appropriés de la sélection, en vert.</span><span class="sxs-lookup"><span data-stu-id="e9910-118">In turn, BizTalk Mapper emphasizes the other map items relevant to the selection, in green color.</span></span> <span data-ttu-id="e9910-119">Dans la figure, vous pouvez voir que tous les éléments de la relation sélectionnée, bien que mis en surbrillance, ne figurent pas entièrement dans la vue active.</span><span class="sxs-lookup"><span data-stu-id="e9910-119">From the figure, you can see that all the elements of the selected relationship, though emphasized, are completely not in the current view.</span></span>  
  
     <span data-ttu-id="e9910-120">![Liens lorsque automatique &#45; le défilement est mis hors tension](../core/media/autoscroll-switchoff.gif "AutoScroll_SwitchOff")</span><span class="sxs-lookup"><span data-stu-id="e9910-120">![Links when auto&#45;scrolling is switched off](../core/media/autoscroll-switchoff.gif "AutoScroll_SwitchOff")</span></span>  
  
3.  <span data-ttu-id="e9910-121">Cliquez sur l’icône de défilement automatique ![automatique &#45; icône de défilement](../core/media/mapper-intelliscroll.gif "Mapper_IntelliScroll") à sa mise sous tension.</span><span class="sxs-lookup"><span data-stu-id="e9910-121">Click the auto-scroll icon ![Auto&#45;scroll icon](../core/media/mapper-intelliscroll.gif "Mapper_IntelliScroll") to switch it ON.</span></span>  
  
     <span data-ttu-id="e9910-122">Le Mappeur BizTalk utilise le défilement automatique pour placer tous les éléments appropriés dans la vue de mappage active.</span><span class="sxs-lookup"><span data-stu-id="e9910-122">The BizTalk Mapper automatically scrolls to bring all the relevant items in the selection into the current map view.</span></span>  
  
     <span data-ttu-id="e9910-123">![Afficher lorsque le défilement automatique est allumé](../core/media/autoscroll-switchon.gif "AutoScroll_SwitchOn")</span><span class="sxs-lookup"><span data-stu-id="e9910-123">![View when autoscrolling is switched on](../core/media/autoscroll-switchon.gif "AutoScroll_SwitchOn")</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e9910-124">Vous pouvez également utiliser les combinaisons de touches CTRL+M, CTRL+U.</span><span class="sxs-lookup"><span data-stu-id="e9910-124">Alternatively, you can press CTRL+M, CTRL+U from the keyboard.</span></span> <span data-ttu-id="e9910-125">Pour obtenir la liste des raccourcis du mappeur, consultez [raccourcis clavier de Mappeur BizTalk](../core/biztalk-mapper-keyboard-shortcuts.md).</span><span class="sxs-lookup"><span data-stu-id="e9910-125">For a list of Mapper keyboard shortcuts, see [BizTalk Mapper Keyboard Shortcuts](../core/biztalk-mapper-keyboard-shortcuts.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9910-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e9910-126">See Also</span></span>  
 [<span data-ttu-id="e9910-127">À l’aide des fonctionnalités améliorées dans le Mappeur BizTalk</span><span class="sxs-lookup"><span data-stu-id="e9910-127">Using Enhanced Features in BizTalk Mapper</span></span>](../core/using-enhanced-features-in-biztalk-mapper.md)