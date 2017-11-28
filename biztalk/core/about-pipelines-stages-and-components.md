---
title: "À propos des Pipelines, des étapes et composants | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Microsoft.BizTalk.Component.Interop namespace
- pipelines, about pipelines
ms.assetid: a98e1c93-f264-4577-bd12-4430a5859e3c
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 070c785924021f8e398a547c01afe969fa6430cc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="about-pipelines-stages-and-components"></a><span data-ttu-id="ed4cc-102">À propos des pipelines, des étapes et des composants</span><span class="sxs-lookup"><span data-stu-id="ed4cc-102">About Pipelines, Stages, and Components</span></span>
<span data-ttu-id="ed4cc-103">Un pipeline est une portion de l'infrastructure logicielle qui contient un ensemble de composants .NET ou COM qui traitent les messages dans un ordre prédéfini.</span><span class="sxs-lookup"><span data-stu-id="ed4cc-103">A pipeline is a piece of software infrastructure that contains a set of .NET or COM components that process messages in a predefined sequence.</span></span> <span data-ttu-id="ed4cc-104">Il divise le traitement en catégories de travail appelées étapes et détermine l'ordre d'exécution de ces étapes.</span><span class="sxs-lookup"><span data-stu-id="ed4cc-104">A pipeline divides processing into categories of work called stages, and determines the sequence in which the stages are performed.</span></span> <span data-ttu-id="ed4cc-105">Chaque étape définit des groupes de travail logiques, identifie les composants qui la constituent et détermine le mode d'exécution des composants de pipeline de cette étape.</span><span class="sxs-lookup"><span data-stu-id="ed4cc-105">Each stage defines logical work groups, determines which components can go in that stage, and specifies how the pipeline components in the stage are run.</span></span>  
  
 <span data-ttu-id="ed4cc-106">À chaque étape, les composants de pipeline effectuent des tâches spécifiques.</span><span class="sxs-lookup"><span data-stu-id="ed4cc-106">Within each stage, pipeline components perform specific tasks.</span></span> <span data-ttu-id="ed4cc-107">Par exemple, les composants des étapes d'un pipeline de réception pourront décoder, désassembler puis convertir des documents au format XML à partir d'autres formats.</span><span class="sxs-lookup"><span data-stu-id="ed4cc-107">For example, components within stages of a receive pipeline may decode, disassemble, and then convert documents from other formats to XML.</span></span> <span data-ttu-id="ed4cc-108">Pipelines d’envoi est essentiellement inverse : conversion de documents XML vers d’autres formats, assembler et chiffrer avec chaque composant de pipeline exécutant une portion de l’ensemble du processus.</span><span class="sxs-lookup"><span data-stu-id="ed4cc-108">Send pipelines do essentially the opposite: convert documents from XML to other formats, assemble, and encrypt, with each pipeline component performing a portion of the entire process.</span></span> <span data-ttu-id="ed4cc-109">Bien qu'une étape soit un conteneur de composants, chaque étape est elle-même un composant avec des métadonnées.</span><span class="sxs-lookup"><span data-stu-id="ed4cc-109">Although a stage is a container of components, each stage is itself a component with metadata.</span></span> <span data-ttu-id="ed4cc-110">Les étapes n'ont pas de code d'exécution, contrairement aux composants de pipeline.</span><span class="sxs-lookup"><span data-stu-id="ed4cc-110">Stages have no execution code, as opposed to pipeline components, which do have execution code.</span></span>  
  
 <span data-ttu-id="ed4cc-111">La figure suivante montre comment la surface de conception de pipeline illustre les pipelines.</span><span class="sxs-lookup"><span data-stu-id="ed4cc-111">The following figure shows how the pipeline design surface illustrates pipelines.</span></span> <span data-ttu-id="ed4cc-112">Ce pipeline comporte deux étapes : l'étape d'assemblage et l'étape de codage.</span><span class="sxs-lookup"><span data-stu-id="ed4cc-112">This pipeline has two stages, the Assemble stage and the Encode stage.</span></span> <span data-ttu-id="ed4cc-113">Le composant de pipeline Assembleur XML a été ajouté à l’étape d’assemblage, mais la phase de codage est encore vide, car elle affiche toujours **Déposer ici !**</span><span class="sxs-lookup"><span data-stu-id="ed4cc-113">The XML Assembler pipeline component was added to the Assemble stage, but the Encode stage is still empty, because it still shows **Drop Here!**</span></span> <span data-ttu-id="ed4cc-114">pour indiquer qu’un composant de pipeline peut être ajouté à l’étape.</span><span class="sxs-lookup"><span data-stu-id="ed4cc-114">to indicate that a pipeline component can be added to the stage.</span></span>  
  
 <span data-ttu-id="ed4cc-115">![Étapes et les composants d’un pipeline BizTalk](../core/media/ebiz-pipe-stages02.gif "ebiz_pipe_stages02")</span><span class="sxs-lookup"><span data-stu-id="ed4cc-115">![Stages and components in a BizTalk pipeline](../core/media/ebiz-pipe-stages02.gif "ebiz_pipe_stages02")</span></span>  
<span data-ttu-id="ed4cc-116">Illustration des étapes et des composants d'un pipeline BizTalk</span><span class="sxs-lookup"><span data-stu-id="ed4cc-116">Illustrates stages and components in a BizTalk pipeline.</span></span>  
  
 <span data-ttu-id="ed4cc-117">Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] contient un ensemble de modèles de pipeline, de composants de pipeline et de pipelines par défaut.</span><span class="sxs-lookup"><span data-stu-id="ed4cc-117">Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] contains a set of pipeline templates, pipeline components, and default pipelines.</span></span> <span data-ttu-id="ed4cc-118">Vous pouvez créer et configurer des pipelines à l’aide de l’interface utilisateur du Concepteur de Pipeline ; vous implémentez les pipelines à l’aide de l’API dans le **Microsoft.BizTalk.Component.Interop** espace de noms.</span><span class="sxs-lookup"><span data-stu-id="ed4cc-118">You can create and configure pipelines by using the Pipeline Designer user interface; you implement pipelines by using the API in the **Microsoft.BizTalk.Component.Interop** namespace.</span></span> <span data-ttu-id="ed4cc-119">Il n'est pas possible de modifier les modèles de pipeline.</span><span class="sxs-lookup"><span data-stu-id="ed4cc-119">You cannot modify the pipeline templates.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ed4cc-120">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="ed4cc-120">In This Section</span></span>  
  
-   [<span data-ttu-id="ed4cc-121">Types de Pipelines</span><span class="sxs-lookup"><span data-stu-id="ed4cc-121">Types of Pipelines</span></span>](../core/types-of-pipelines.md)  
  
-   [<span data-ttu-id="ed4cc-122">Types de composants de Pipeline</span><span class="sxs-lookup"><span data-stu-id="ed4cc-122">Types of Pipeline Components</span></span>](../core/types-of-pipeline-components.md)  
  
-   [<span data-ttu-id="ed4cc-123">Étapes de canalisation</span><span class="sxs-lookup"><span data-stu-id="ed4cc-123">Pipeline Stages</span></span>](../core/pipeline-stages.md)  
  
-   [<span data-ttu-id="ed4cc-124">Pipelines par défaut</span><span class="sxs-lookup"><span data-stu-id="ed4cc-124">Default Pipelines</span></span>](../core/default-pipelines.md)  
  
-   [<span data-ttu-id="ed4cc-125">Modèles de pipeline</span><span class="sxs-lookup"><span data-stu-id="ed4cc-125">Pipeline Templates</span></span>](../core/pipeline-templates.md)  
  
-   [<span data-ttu-id="ed4cc-126">Composants de pipeline</span><span class="sxs-lookup"><span data-stu-id="ed4cc-126">Pipeline Components</span></span>](../core/pipeline-components.md)  
  
-   [<span data-ttu-id="ed4cc-127">Résolution de schéma dans les composants de Pipeline</span><span class="sxs-lookup"><span data-stu-id="ed4cc-127">Schema Resolution in Pipeline Components</span></span>](../core/schema-resolution-in-pipeline-components.md)  
  
-   [<span data-ttu-id="ed4cc-128">Utilisation d’enveloppes dans l’assembleur XML et les composants de Pipeline désassembleur</span><span class="sxs-lookup"><span data-stu-id="ed4cc-128">Envelope Use in the XML Assembler and Disassembler Pipeline Components</span></span>](../core/envelope-use-in-the-xml-assembler-and-disassembler-pipeline-components.md)  
  
-   [<span data-ttu-id="ed4cc-129">Rétrogradation de propriétés dans les composants de Pipeline assembleur</span><span class="sxs-lookup"><span data-stu-id="ed4cc-129">Property Demotion in Assembler Pipeline Components</span></span>](../core/property-demotion-in-assembler-pipeline-components.md)  
  
-   [<span data-ttu-id="ed4cc-130">Promotion des propriétés dans les composants de Pipeline désassembleur</span><span class="sxs-lookup"><span data-stu-id="ed4cc-130">Property Promotion in Disassembler Pipeline Components</span></span>](../core/property-promotion-in-disassembler-pipeline-components.md)  
  
-   [<span data-ttu-id="ed4cc-131">Composants de Pipeline désassembleur les champs distinctifs</span><span class="sxs-lookup"><span data-stu-id="ed4cc-131">Distinguished Fields in Disassembler Pipeline Components</span></span>](../core/distinguished-fields-in-disassembler-pipeline-components.md)