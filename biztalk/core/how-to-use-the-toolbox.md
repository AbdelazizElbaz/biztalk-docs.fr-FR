---
title: "L’utilisation de la boîte à outils | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- creating, pipelines
- pipeline components, deleting from toolbox
- pipeline components, Pipeline Designer
- pipeline components, adding to toolbox
- Pipeline Designer, toolbox
- pipelines, creating
ms.assetid: 7a60c590-1a38-46fe-addf-0aa2c8b63cf9
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3965a063aebcc932f07937fd19c3998412591ea1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-use-the-toolbox"></a><span data-ttu-id="31af6-102">Utilisation de la boîte à outils</span><span class="sxs-lookup"><span data-stu-id="31af6-102">How to Use the Toolbox</span></span>
<span data-ttu-id="31af6-103">Pour créer un pipeline, il faut glisser des composants (formes) de la boîte à outils jusqu'à la surface de conception.</span><span class="sxs-lookup"><span data-stu-id="31af6-103">You create a pipeline by dragging components (shapes) from the Toolbox to the design surface.</span></span> <span data-ttu-id="31af6-104">Le Concepteur de pipeline vous aide à assembler des pipelines valides en soumettant le processus de création à certaines restrictions.</span><span class="sxs-lookup"><span data-stu-id="31af6-104">Pipeline Designer helps you assemble valid pipelines by placing certain restrictions on the creation process.</span></span> <span data-ttu-id="31af6-105">Vous ne pouvez sélectionner que des composants de boîte à outils qui s'appliquent au type de pipeline que vous êtes en train de créer.</span><span class="sxs-lookup"><span data-stu-id="31af6-105">You can only select Toolbox components that apply to the pipeline type you are creating.</span></span> <span data-ttu-id="31af6-106">Ainsi, un pipeline de réception affichera les décodeurs, désassembleurs et valideurs comme des composants de boîte à outils valides, tandis que les encodeurs et les assembleurs seront désactivés (apparaissant de façon grisée).</span><span class="sxs-lookup"><span data-stu-id="31af6-106">For example, a receive pipeline will show decoders, disassemblers, and validators as valid Toolbox components, while encoders and assemblers will be disabled (dimmed).</span></span>  
  
 <span data-ttu-id="31af6-107">De plus, les phases ne peuvent accepter que des composants valides.</span><span class="sxs-lookup"><span data-stu-id="31af6-107">In addition, stages can accept only valid components.</span></span> <span data-ttu-id="31af6-108">Il est par exemple impossible de glisser un composant d'encodeur sur une phase d'assemblage.</span><span class="sxs-lookup"><span data-stu-id="31af6-108">For example, you cannot drag an encoder component to an Assemble stage.</span></span> <span data-ttu-id="31af6-109">Lorsque vous faites glisser un composant près d'un emplacement de dépôt valide, une flèche apparaît, indiquant l'endroit où le composant peut être inséré.</span><span class="sxs-lookup"><span data-stu-id="31af6-109">When you drag a component near a valid drop location, an arrow appears, indicating the point where the component can be inserted.</span></span>  
  
 <span data-ttu-id="31af6-110">Si vous faites glisser un composant valide sur une phase réduite, laissez-y la souris quelques secondes pour la développer, puis déposez-y le composant.</span><span class="sxs-lookup"><span data-stu-id="31af6-110">If you drag a valid component onto a stage that is collapsed, pause the mouse over the stage for a few seconds to expand it, and then drop the component into the stage.</span></span>  
  
 <span data-ttu-id="31af6-111">L'ajout d'un composant personnalisé à la boîte à outils dans le Concepteur de pipeline est similaire à la procédure standard Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="31af6-111">Adding a custom component to the Toolbox in Pipeline Designer is similar to the standard Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] procedure.</span></span>  
  
 <span data-ttu-id="31af6-112">**Formes début et fin**</span><span class="sxs-lookup"><span data-stu-id="31af6-112">**Start and End Shapes**</span></span>  
  
 <span data-ttu-id="31af6-113">**Démarrer** et **fin** formes apparaissent sous forme de puces dans tous les pipelines.</span><span class="sxs-lookup"><span data-stu-id="31af6-113">**Start** and **End** shapes appear as bullets on all pipelines.</span></span> <span data-ttu-id="31af6-114">Elles sont représentées sur la surface de conception à des fins d'organisation visuelle uniquement.</span><span class="sxs-lookup"><span data-stu-id="31af6-114">They are provided on the design surface for visual organization only.</span></span> <span data-ttu-id="31af6-115">Il n'y a qu'un exemplaire de chacune et elles ne peuvent être ni ajoutées ni supprimées.</span><span class="sxs-lookup"><span data-stu-id="31af6-115">There is only one of each, and they can neither be added nor deleted.</span></span> <span data-ttu-id="31af6-116">Le **Démarrer** et **fin** formes n’apparaissent pas dans la boîte à outils.</span><span class="sxs-lookup"><span data-stu-id="31af6-116">The **Start** and **End** shapes do not appear in the Toolbox.</span></span>  
  
### <a name="to-add-a-pipeline-component-to-the-toolbox"></a><span data-ttu-id="31af6-117">Pour ajouter un composant de pipeline à la boîte à outils</span><span class="sxs-lookup"><span data-stu-id="31af6-117">To add a pipeline component to the Toolbox</span></span>  
  
1.  <span data-ttu-id="31af6-118">Dans le menu **Outils** , cliquez sur **Choisir des éléments de boîte à outils**.</span><span class="sxs-lookup"><span data-stu-id="31af6-118">On the **Tools** menu, click **Choose Toolbox Items**.</span></span>  
  
     <span data-ttu-id="31af6-119">— Ou :</span><span class="sxs-lookup"><span data-stu-id="31af6-119">—Or—</span></span>  
  
     <span data-ttu-id="31af6-120">Avec le bouton droit de la boîte à outils, puis cliquez sur **choisir des éléments de**.</span><span class="sxs-lookup"><span data-stu-id="31af6-120">Right-click the Toolbox and then click **Choose Items**.</span></span>  
  
2.  <span data-ttu-id="31af6-121">Dans le **personnaliser la boîte à outils** boîte de dialogue, cliquez sur le **composants de Pipeline BizTalk** onglet.</span><span class="sxs-lookup"><span data-stu-id="31af6-121">In the **Customize Toolbox** dialog box, click the **BizTalk Pipeline Components** tab.</span></span>  
  
     <span data-ttu-id="31af6-122">Une boîte de dialogue affiche les composants de pipeline compatibles.</span><span class="sxs-lookup"><span data-stu-id="31af6-122">A dialog box displays the compatible pipeline components.</span></span> <span data-ttu-id="31af6-123">Vous pouvez naviguer dans les différentes catégories en cliquant sur les onglets de la partie supérieure de cette boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="31af6-123">You can navigate through the categories by clicking the tabs at the top of the dialog box.</span></span>  
  
3.  <span data-ttu-id="31af6-124">Sélectionnez le composant que vous souhaitez ajouter à la boîte à outils.</span><span class="sxs-lookup"><span data-stu-id="31af6-124">Select the component you want to add to the Toolbox.</span></span>  
  
4.  <span data-ttu-id="31af6-125">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="31af6-125">Click **OK**.</span></span> <span data-ttu-id="31af6-126">Le composant s’affiche dans le **composants de Pipeline BizTalk** onglet de la boîte à outils.</span><span class="sxs-lookup"><span data-stu-id="31af6-126">The component will appear on the **BizTalk Pipeline Components** tab of the Toolbox.</span></span>  
  
### <a name="to-remove-a-pipeline-component-from-the-toolbox"></a><span data-ttu-id="31af6-127">Pour supprimer un composant de pipeline de la boîte à outils</span><span class="sxs-lookup"><span data-stu-id="31af6-127">To remove a pipeline component from the Toolbox</span></span>  
  
-   <span data-ttu-id="31af6-128">Ouvrez le **personnaliser la boîte à outils** boîte de dialogue (comme dans la procédure précédente) et désactivez le composant à supprimer.</span><span class="sxs-lookup"><span data-stu-id="31af6-128">Open the **Customize Toolbox** dialog box (as in the preceding procedure) and clear the component to be removed.</span></span>  
  
     <span data-ttu-id="31af6-129">Les composants restent inscrits même après leur suppression de la boîte à outils.</span><span class="sxs-lookup"><span data-stu-id="31af6-129">A component remains registered even after it has been removed from the Toolbox.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31af6-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="31af6-130">See Also</span></span>  
 <span data-ttu-id="31af6-131">[Comment créer un Pipeline](../core/how-to-create-a-new-pipeline.md) </span><span class="sxs-lookup"><span data-stu-id="31af6-131">[How to Create a New Pipeline](../core/how-to-create-a-new-pipeline.md) </span></span>  
 <span data-ttu-id="31af6-132">[Comment ouvrir un Pipeline](../core/how-to-open-a-pipeline.md) </span><span class="sxs-lookup"><span data-stu-id="31af6-132">[How to Open a Pipeline](../core/how-to-open-a-pipeline.md) </span></span>  
 <span data-ttu-id="31af6-133">[Comment accéder à l’aide du clavier](../core/how-to-navigate-with-the-keyboard.md) </span><span class="sxs-lookup"><span data-stu-id="31af6-133">[How to Navigate with the Keyboard](../core/how-to-navigate-with-the-keyboard.md) </span></span>  
 [<span data-ttu-id="31af6-134">Création de Pipelines avec le Concepteur de Pipeline</span><span class="sxs-lookup"><span data-stu-id="31af6-134">Creating Pipelines with Pipeline Designer</span></span>](../core/creating-pipelines-with-pipeline-designer.md)