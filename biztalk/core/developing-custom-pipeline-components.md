---
title: "Développement de composants de Pipeline personnalisé | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pipeline components [custom]
- pipeline components [custom], about pipeline components
- pipeline components [custom], creating
- customizing, pipeline components
- pipeline interfaces
- IDisassemblerComponent
- pipeline interfaces, about pipeline interfaces
- creating, pipeline components [custom]
- IAssemblerComponent
- IComponent
- pipeline components [custom], customizing
- pipeline interfaces, interface types
- pipeline components [custom], interfaces
- pipeline components [custom], component types
ms.assetid: cce61e0d-f1e3-4ec2-b38c-7c6eaf83ac10
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 723cd04a2a907fdb5d770975c27d47e1752d08ff
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="developing-custom-pipeline-components"></a><span data-ttu-id="f6a4d-102">Développement de composants de Pipeline personnalisé</span><span class="sxs-lookup"><span data-stu-id="f6a4d-102">Developing Custom Pipeline Components</span></span>
<span data-ttu-id="f6a4d-103">Cette section décrit comment développer un composant de pipeline.</span><span class="sxs-lookup"><span data-stu-id="f6a4d-103">This section describes how to develop a pipeline component.</span></span> <span data-ttu-id="f6a4d-104">Vous pouvez créer trois types de composants de pipeline : général, le désassemblage et assemblage.</span><span class="sxs-lookup"><span data-stu-id="f6a4d-104">You can create three types of pipeline components: general, assembling, and disassembling.</span></span> <span data-ttu-id="f6a4d-105">Chacun de ces trois types peut aussi implémenter une fonctionnalité de sonde.</span><span class="sxs-lookup"><span data-stu-id="f6a4d-105">Each of the three types can additionally implement probing functionality.</span></span> <span data-ttu-id="f6a4d-106">Chaque type de composant de pipeline possède une interface associée qui doit être implémentée pour le composant à intégrer le moteur de messagerie BizTalk ; les interfaces de pipeline qui distinguent les types de composants sont **IComponent**, **IAssemblerComponent**, et **IDisassemblerComponent**.</span><span class="sxs-lookup"><span data-stu-id="f6a4d-106">Each type of pipeline component has an associated interface that must be implemented for the component to be plugged into the BizTalk Messaging Engine; the pipeline interfaces that distinguish the types of components are **IComponent**, **IAssemblerComponent**, and **IDisassemblerComponent**.</span></span> <span data-ttu-id="f6a4d-107">Pour les composants de sonde, vous devez implémenter la **IProbeMessage** interface.</span><span class="sxs-lookup"><span data-stu-id="f6a4d-107">For probing components, you must implement the **IProbeMessage** interface.</span></span>  
  
 <span data-ttu-id="f6a4d-108">Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] contient un exemple de composant de pipeline que vous pouvez référencer lors de la création de votre propre composant.</span><span class="sxs-lookup"><span data-stu-id="f6a4d-108">Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] contains a sample pipeline component that you can reference when creating your own component.</span></span> <span data-ttu-id="f6a4d-109">L'exemple de composant illustre comment ajouter des données à la fin et au début d'un message.</span><span class="sxs-lookup"><span data-stu-id="f6a4d-109">The sample component demonstrates how to append data to the end of a message and add data at the beginning of the message.</span></span> <span data-ttu-id="f6a4d-110">Pour plus d’informations sur l’exemple de composant de pipeline, consultez [CustomComponent (exemple BizTalk Server)](../core/customcomponent-biztalk-server-sample.md).</span><span class="sxs-lookup"><span data-stu-id="f6a4d-110">For more information about the sample pipeline component, see [CustomComponent (BizTalk Server Sample)](../core/customcomponent-biztalk-server-sample.md).</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="f6a4d-111">Si vous référencez un composant de pipeline personnalisé à partir d'un pipeline dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], une erreur de compilation peut se produire.</span><span class="sxs-lookup"><span data-stu-id="f6a4d-111">If you reference a custom pipeline component from a pipeline in [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], a compile-time error may occur.</span></span> <span data-ttu-id="f6a4d-112">Pour corriger cette erreur, fermez le Concepteur de pipeline et rouvrez-le avant la compilation.</span><span class="sxs-lookup"><span data-stu-id="f6a4d-112">To correct the error, close Pipeline Designer and reopen it before compiling.</span></span> <span data-ttu-id="f6a4d-113">Vous pouvez également supprimer le composant, puis l'ajouter.</span><span class="sxs-lookup"><span data-stu-id="f6a4d-113">Alternatively, you can remove the component, and then add it.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="f6a4d-114">Lors de la mise à niveau vers [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)], vérifiez que les variables de chaîne des composants de pipeline personnalisés existants ne contiennent pas de caractères de saut de ligne, comme ‘\n’.</span><span class="sxs-lookup"><span data-stu-id="f6a4d-114">When upgrading to [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)], ensure that any string variables in your existing custom pipeline components do not contain any newline characters such as ‘\n’.</span></span> <span data-ttu-id="f6a4d-115">À défaut, une erreur « saut de ligne dans la constante » se produit lors de la compilation du composant dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f6a4d-115">Otherwise, a “newline in constant” error will occur when compiling this component in [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f6a4d-116">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="f6a4d-116">In This Section</span></span>  
  
-   [<span data-ttu-id="f6a4d-117">À l’aide des Interfaces de Pipeline</span><span class="sxs-lookup"><span data-stu-id="f6a4d-117">Using Pipeline Interfaces</span></span>](../core/using-pipeline-interfaces.md)  
  
-   [<span data-ttu-id="f6a4d-118">Développement d’un composant de Pipeline général</span><span class="sxs-lookup"><span data-stu-id="f6a4d-118">Developing a General Pipeline Component</span></span>](../core/developing-a-general-pipeline-component.md)  
  
-   [<span data-ttu-id="f6a4d-119">Développement d’un composant de Pipeline d’assemblage</span><span class="sxs-lookup"><span data-stu-id="f6a4d-119">Developing an Assembling Pipeline Component</span></span>](../core/developing-an-assembling-pipeline-component.md)  
  
-   [<span data-ttu-id="f6a4d-120">Développement d’un composant de Pipeline de désassemblage</span><span class="sxs-lookup"><span data-stu-id="f6a4d-120">Developing a Disassembling Pipeline Component</span></span>](../core/developing-a-disassembling-pipeline-component.md)  
  
-   [<span data-ttu-id="f6a4d-121">Développement d’un composant de Pipeline de sonde</span><span class="sxs-lookup"><span data-stu-id="f6a4d-121">Developing a Probing Pipeline Component</span></span>](../core/developing-a-probing-pipeline-component.md)  
  
-   [<span data-ttu-id="f6a4d-122">Implémentation d’une méthode Seek dans un composant de Pipeline managé de diffusion en continu</span><span class="sxs-lookup"><span data-stu-id="f6a4d-122">Implementing a Seek Method in a Managed Streaming Pipeline Component</span></span>](../core/implementing-a-seek-method-in-a-managed-streaming-pipeline-component.md)  
  
-   [<span data-ttu-id="f6a4d-123">À l’aide de moteurs d’analyse et de sérialisation</span><span class="sxs-lookup"><span data-stu-id="f6a4d-123">Using the Parsing and Serializing Engines</span></span>](../core/using-the-parsing-and-serializing-engines.md)  
  
-   [<span data-ttu-id="f6a4d-124">Rapports d’erreurs à partir des composants de Pipeline</span><span class="sxs-lookup"><span data-stu-id="f6a4d-124">Reporting Errors from Pipeline Components</span></span>](../core/reporting-errors-from-pipeline-components.md)  
  
-   [<span data-ttu-id="f6a4d-125">Déploiement des composants de Pipeline</span><span class="sxs-lookup"><span data-stu-id="f6a4d-125">Deploying Pipeline Components</span></span>](../core/deploying-pipeline-components.md)  
  
-   [<span data-ttu-id="f6a4d-126">Débogage des Pipelines personnalisés</span><span class="sxs-lookup"><span data-stu-id="f6a4d-126">Debugging Custom Pipelines</span></span>](../core/debugging-custom-pipelines.md)