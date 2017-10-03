---
title: Comment ajouter un composant de pipeline | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: pipelines, components
ms.assetid: 6b1dbeab-6acc-46d7-8ddd-79b79da3591c
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9a9f11f03e818ae1067bc22027822bfeef202260
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-add-a-component-to-a-pipeline"></a><span data-ttu-id="506d3-102">Comment ajouter un composant de pipeline</span><span class="sxs-lookup"><span data-stu-id="506d3-102">How to Add a Component to a Pipeline</span></span>
<span data-ttu-id="506d3-103">Pour ajouter des composants à des pipelines, faites-les glisser depuis la boîte à outils vers la surface de conception.</span><span class="sxs-lookup"><span data-stu-id="506d3-103">You add components to pipelines by dragging from the Toolbox to the design surface.</span></span>  
  
### <a name="to-add-a-component-to-a-pipeline"></a><span data-ttu-id="506d3-104">Pour ajouter un composant à un pipeline</span><span class="sxs-lookup"><span data-stu-id="506d3-104">To add a component to a pipeline</span></span>  
  
-   <span data-ttu-id="506d3-105">Dans la boîte à outils, faites glisser le composant de pipeline sur un **Déposer ici !**</span><span class="sxs-lookup"><span data-stu-id="506d3-105">In the Toolbox, drag the pipeline component onto a **Drop Here!**</span></span> <span data-ttu-id="506d3-106">zone sur l’aire de conception.</span><span class="sxs-lookup"><span data-stu-id="506d3-106">box on the design surface.</span></span>  
  
 <span data-ttu-id="506d3-107">L'illustration ci-dessous montre comment la surface de conception de pipeline représente les pipelines.</span><span class="sxs-lookup"><span data-stu-id="506d3-107">The following illustration shows how the pipeline design surface illustrates pipelines.</span></span> <span data-ttu-id="506d3-108">Ce pipeline comporte deux étapes : l'étape d'assemblage et l'étape de codage.</span><span class="sxs-lookup"><span data-stu-id="506d3-108">This pipeline has two stages, the Assemble stage and the Encode stage.</span></span> <span data-ttu-id="506d3-109">Le composant de pipeline Assembleur XML a été ajouté à l’étape d’assemblage, mais la phase de codage est encore vide, car elle affiche toujours **Déposer ici !**</span><span class="sxs-lookup"><span data-stu-id="506d3-109">The XML Assembler pipeline component was added to the Assemble stage, but the Encode stage is still empty, because it still shows **Drop Here!**</span></span> <span data-ttu-id="506d3-110">pour indiquer qu’un composant de pipeline peut être ajouté à l’étape.</span><span class="sxs-lookup"><span data-stu-id="506d3-110">to indicate that a pipeline component can be added to the stage.</span></span>  
  
 <span data-ttu-id="506d3-111">![Étapes et les composants d’un pipeline BizTalk](../core/media/ebiz-pipe-stages02.gif "ebiz_pipe_stages02")</span><span class="sxs-lookup"><span data-stu-id="506d3-111">![Stages and components in a BizTalk pipeline](../core/media/ebiz-pipe-stages02.gif "ebiz_pipe_stages02")</span></span>  
<span data-ttu-id="506d3-112">Illustration des étapes et des composants d'un pipeline BizTalk</span><span class="sxs-lookup"><span data-stu-id="506d3-112">Illustrates stages and components in a BizTalk pipeline.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="506d3-113">Un composant de pipeline peut uniquement être supprimé à des emplacements précis sur l’aire de conception.</span><span class="sxs-lookup"><span data-stu-id="506d3-113">A pipeline component can only be dropped at specific places on the design surface.</span></span> <span data-ttu-id="506d3-114">Il ne peut ainsi être déposé que dans une étape avec laquelle il a des affinités.</span><span class="sxs-lookup"><span data-stu-id="506d3-114">The pipeline component can only be dropped in a stage in which it has stage affinity.</span></span> <span data-ttu-id="506d3-115">Un cercle barré d'un trait apparaît à côté du pointeur aux endroits où le composant de pipeline ne peut pas être déposé.</span><span class="sxs-lookup"><span data-stu-id="506d3-115">A circle with a line through it appears next to the pointer where the pipeline component cannot be dropped.</span></span> <span data-ttu-id="506d3-116">Là où le composant de pipeline peut être placé, une flèche apparaît et une portion de la surface de conception est mise en surbrillance.</span><span class="sxs-lookup"><span data-stu-id="506d3-116">An arrow appears, and a portion of the design surface is highlighted where a pipeline component can be placed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="506d3-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="506d3-117">See Also</span></span>  
 <span data-ttu-id="506d3-118">[Comment créer un Pipeline](../core/how-to-create-a-new-pipeline.md) </span><span class="sxs-lookup"><span data-stu-id="506d3-118">[How to Create a New Pipeline](../core/how-to-create-a-new-pipeline.md) </span></span>  
 <span data-ttu-id="506d3-119">[Comment ouvrir un Pipeline](../core/how-to-open-a-pipeline.md) </span><span class="sxs-lookup"><span data-stu-id="506d3-119">[How to Open a Pipeline](../core/how-to-open-a-pipeline.md) </span></span>  
 <span data-ttu-id="506d3-120">[L’utilisation de la boîte à outils](../core/how-to-use-the-toolbox.md) </span><span class="sxs-lookup"><span data-stu-id="506d3-120">[How to Use the Toolbox](../core/how-to-use-the-toolbox.md) </span></span>  
 <span data-ttu-id="506d3-121">[Comment accéder à l’aide du clavier](../core/how-to-navigate-with-the-keyboard.md) </span><span class="sxs-lookup"><span data-stu-id="506d3-121">[How to Navigate with the Keyboard](../core/how-to-navigate-with-the-keyboard.md) </span></span>  
 [<span data-ttu-id="506d3-122">Création de Pipelines avec le Concepteur de Pipeline</span><span class="sxs-lookup"><span data-stu-id="506d3-122">Creating Pipelines with Pipeline Designer</span></span>](../core/creating-pipelines-with-pipeline-designer.md)