---
title: "Pipelines de réception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- receive pipelines, about receive pipelines
- receive pipelines, message flow
- receive pipelines
- messages, receive pipelines
- messages, message flow
- pipelines, receive pipelines
- receive pipelines, stages
ms.assetid: ee75c1d4-00b7-4177-bca3-1447a39d2238
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a0a248c69cb96603e9c4883e5d21caa39165da13
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="receive-pipelines"></a><span data-ttu-id="8e18f-102">Pipelines de réception</span><span class="sxs-lookup"><span data-stu-id="8e18f-102">Receive Pipelines</span></span>
<span data-ttu-id="8e18f-103">La figure suivante présente le workflow de traitement d'un message en mettant en avant le rôle du pipeline de réception.</span><span class="sxs-lookup"><span data-stu-id="8e18f-103">The following figure shows the message processing workflow, highlighting the receive pipeline.</span></span>  
  
 <span data-ttu-id="8e18f-104">![Diagramme du workflow de traitement de message. ] (../core/media/ebiz-dev-busprcsb.gif "ebiz_dev_busprcsb")</span><span class="sxs-lookup"><span data-stu-id="8e18f-104">![Diagram of the message processing workflow.](../core/media/ebiz-dev-busprcsb.gif "ebiz_dev_busprcsb")</span></span>  
<span data-ttu-id="8e18f-105">Illustration du workflow de traitement d'un message</span><span class="sxs-lookup"><span data-stu-id="8e18f-105">Depicts the message processing workflow.</span></span>  
  
 <span data-ttu-id="8e18f-106">Un pipeline de réception intervient sur un message une fois qu’il est reçu par l’adaptateur de réception.</span><span class="sxs-lookup"><span data-stu-id="8e18f-106">A receive pipeline operates on a message after it is received by the receive adapter.</span></span> <span data-ttu-id="8e18f-107">Le pipeline de réception prend en charge le message initial, effectue quelques transformations et désassemble les données brutes en zéro message, un message ou plusieurs messages.</span><span class="sxs-lookup"><span data-stu-id="8e18f-107">The receive pipeline takes the initial message, performs some transformations, and disassembles the raw data into zero, one, or multiple messages.</span></span> <span data-ttu-id="8e18f-108">Ces messages peuvent ensuite être traités par BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="8e18f-108">These individual messages can then be processed by BizTalk Server.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8e18f-109">Un pipeline de réception peut ne produire aucun message si un composant de consommation lui est ajouté.</span><span class="sxs-lookup"><span data-stu-id="8e18f-109">A receive pipeline can produce zero messages if a consuming component is added to the pipeline.</span></span> <span data-ttu-id="8e18f-110">Dans ce cas, le composant de pipeline consomme le message et ne produit plus de messages de sortie.</span><span class="sxs-lookup"><span data-stu-id="8e18f-110">In this case, the pipeline component consumes the message and does not produce any output messages.</span></span> <span data-ttu-id="8e18f-111">Si un composant de consommation est placé après un composant de désassemblage, le pipeline s’arrête une fois que le premier message est consommé et aucun autre message n’est extrait du composant de désassemblage.</span><span class="sxs-lookup"><span data-stu-id="8e18f-111">If a consuming component is placed after a disassembling component, pipeline execution stops after the first message is consumed and no subsequent messages are retrieved from the disassembling component.</span></span>  
  
 <span data-ttu-id="8e18f-112">Lors de la création d’un processus d’entreprise, vous pouvez créer un pipeline de réception ou utiliser l'un des deux pipelines de réception par défaut fournis avec BizTalk Server, à savoir le pipeline de réception de transfert ou le pipeline de réception XML.</span><span class="sxs-lookup"><span data-stu-id="8e18f-112">When creating a business process, you can create a new receive pipeline or you can use one of the two default receive pipelines included in BizTalk Server—the pass-through receive pipeline or the XML receive pipeline.</span></span> <span data-ttu-id="8e18f-113">Pour plus d’informations sur ces pipelines par défaut, consultez [Pipelines par défaut](../core/default-pipelines.md).</span><span class="sxs-lookup"><span data-stu-id="8e18f-113">For more information about these default pipelines, see [Default Pipelines](../core/default-pipelines.md).</span></span>  
  
 <span data-ttu-id="8e18f-114">Le pipeline de réception se compose de quatre étapes : décoder, désassembler, valider et Résoudretiers.</span><span class="sxs-lookup"><span data-stu-id="8e18f-114">The receive pipeline consists of four stages: Decode, Disassemble, Validate, and ResolveParty.</span></span> <span data-ttu-id="8e18f-115">Cette rubrique regroupe des considérations relatives à la conception pour compléter ces étapes.</span><span class="sxs-lookup"><span data-stu-id="8e18f-115">This topic contains design considerations for populating these stages.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8e18f-116">Dans cette version, la modification de l’ordre de ces étapes dans un pipeline n’est pas prise en charge.</span><span class="sxs-lookup"><span data-stu-id="8e18f-116">In this release, changing the order or presence of these stages in a pipeline is not supported.</span></span>  
  
## <a name="decode-stage"></a><span data-ttu-id="8e18f-117">Étape Décoder</span><span class="sxs-lookup"><span data-stu-id="8e18f-117">Decode stage</span></span>  
  
-   <span data-ttu-id="8e18f-118">Cette étape est destinée aux composants qui décodent ou déchiffrent le message.</span><span class="sxs-lookup"><span data-stu-id="8e18f-118">This stage is used for components that decode or decrypt the message.</span></span>  
  
    -   <span data-ttu-id="8e18f-119">Il convient que le composant de pipeline Décodeur MIME/SMIME ou un composant de décodage personnalisé soit placé à cette étape si les messages entrants doivent être décodés d’un format en un autre.</span><span class="sxs-lookup"><span data-stu-id="8e18f-119">The MIME/SMIME Decoder pipeline component or a custom decoding component should be placed in this stage if the incoming messages need to be decoded from one format to another.</span></span>  
  
-   <span data-ttu-id="8e18f-120">Cette étape prend en charge un message et produit un message.</span><span class="sxs-lookup"><span data-stu-id="8e18f-120">This stage takes one message and produces one message.</span></span>  
  
-   <span data-ttu-id="8e18f-121">Cette étape peut contenir entre 0 et 255 composants.</span><span class="sxs-lookup"><span data-stu-id="8e18f-121">This stage can contain between zero and 255 components.</span></span>  
  
-   <span data-ttu-id="8e18f-122">Tous les composants de cette étape sont exécutés.</span><span class="sxs-lookup"><span data-stu-id="8e18f-122">All components in this stage are run.</span></span>  
  
## <a name="disassemble-stage"></a><span data-ttu-id="8e18f-123">Étape Désassembler</span><span class="sxs-lookup"><span data-stu-id="8e18f-123">Disassemble stage</span></span>  
  
-   <span data-ttu-id="8e18f-124">Cette étape est destinée aux composants qui analysent ou désassemblent le message.</span><span class="sxs-lookup"><span data-stu-id="8e18f-124">This stage is used for components that parse or disassemble the message.</span></span>  
  
    -   <span data-ttu-id="8e18f-125">Les composants de cette étape testent le message pour déterminer si son format est reconnu.</span><span class="sxs-lookup"><span data-stu-id="8e18f-125">The components within this stage probe the message to see if the format of the message is recognized.</span></span> <span data-ttu-id="8e18f-126">En fonction de la reconnaissance du format, un des composants désassemble le message.</span><span class="sxs-lookup"><span data-stu-id="8e18f-126">Based on the recognition of the format, one of the components disassembles the message.</span></span>  
  
    -   <span data-ttu-id="8e18f-127">Si cette étape comprend plusieurs composants, seul le premier composant qui reconnaît le format du message est exécuté.</span><span class="sxs-lookup"><span data-stu-id="8e18f-127">If this stage contains more than one component, only the first component that recognizes the message format is run.</span></span> <span data-ttu-id="8e18f-128">Si aucun composant de cette étape ne reconnaît le format du message, le traitement du message échoue.</span><span class="sxs-lookup"><span data-stu-id="8e18f-128">If none of the components within the stage recognize the message format, the message processing fails.</span></span>  
  
    -   <span data-ttu-id="8e18f-129">Il convient que cette étape inclue des composants personnalisés implémentant un comportement particulier pour désassembler le contenu des messages.</span><span class="sxs-lookup"><span data-stu-id="8e18f-129">This stage should include any custom components that implement special behavior to disassemble the message contents.</span></span>  
  
    -   <span data-ttu-id="8e18f-130">Cette étape peut contenir entre 0 et 255 composants.</span><span class="sxs-lookup"><span data-stu-id="8e18f-130">This stage can contain between zero and 255 components.</span></span> <span data-ttu-id="8e18f-131">Si cette étape ne comporte aucun composant, le message est transmis.</span><span class="sxs-lookup"><span data-stu-id="8e18f-131">If there are no components in the stage, the message is passed through.</span></span>  
  
## <a name="validate-stage"></a><span data-ttu-id="8e18f-132">Étape Valider</span><span class="sxs-lookup"><span data-stu-id="8e18f-132">Validate stage</span></span>  
  
-   <span data-ttu-id="8e18f-133">Cette étape est destinée aux composants qui valident le format du message.</span><span class="sxs-lookup"><span data-stu-id="8e18f-133">This stage is used for components that validate the message format.</span></span>  
  
    -   <span data-ttu-id="8e18f-134">Un composant de pipeline traite uniquement les messages conformes aux schémas spécifiés dans ce composant.</span><span class="sxs-lookup"><span data-stu-id="8e18f-134">A pipeline component processes only messages that conform to the schemas specified in that component.</span></span> <span data-ttu-id="8e18f-135">Si un pipeline reçoit un message dont le schéma n’est pas associé à un composant du pipeline, ce message n’est pas traité.</span><span class="sxs-lookup"><span data-stu-id="8e18f-135">If a pipeline receives a message whose schema is not associated with any component in the pipeline, that message is not processed.</span></span> <span data-ttu-id="8e18f-136">Selon l'adaptateur qui soumet le message, soit le message est suspendu, soit une erreur s’affiche au niveau de l’expéditeur.</span><span class="sxs-lookup"><span data-stu-id="8e18f-136">Depending on the adapter that submits the message, the message is either suspended or an error is issued to the sender.</span></span>  
  
    -   <span data-ttu-id="8e18f-137">Cette étape est destinée aux composants qui valident les messages XML produits par l’étape Désassembler.</span><span class="sxs-lookup"><span data-stu-id="8e18f-137">Components in this stage are used to validate the XML messages produced by the Disassemble stage.</span></span> <span data-ttu-id="8e18f-138">Ils spécifient les schémas pour procéder à la validation XML.</span><span class="sxs-lookup"><span data-stu-id="8e18f-138">Components in this stage specify schemas to perform the XML validation.</span></span>  
  
-   <span data-ttu-id="8e18f-139">Cette étape peut contenir entre 0 et 255 composants.</span><span class="sxs-lookup"><span data-stu-id="8e18f-139">This stage can contain between zero and 255 components.</span></span>  
  
-   <span data-ttu-id="8e18f-140">Tous les composants de cette étape sont exécutés.</span><span class="sxs-lookup"><span data-stu-id="8e18f-140">All components in this stage are run.</span></span>  
  
    -   <span data-ttu-id="8e18f-141">Cette étape peut être exécutée plusieurs fois.</span><span class="sxs-lookup"><span data-stu-id="8e18f-141">This stage may be run more than once.</span></span> <span data-ttu-id="8e18f-142">Elle est exécutée une fois par message créé par l’étape Désassembler.</span><span class="sxs-lookup"><span data-stu-id="8e18f-142">It runs once per message created by the Disassemble stage.</span></span>  
  
## <a name="resolveparty-stage"></a><span data-ttu-id="8e18f-143">Étape RésoudreTiers</span><span class="sxs-lookup"><span data-stu-id="8e18f-143">ResolveParty stage</span></span>  
  
-   <span data-ttu-id="8e18f-144">Cette étape est un espace réservé pour le [composant de Pipeline résolution tiers](../core/party-resolution-pipeline-component.md).</span><span class="sxs-lookup"><span data-stu-id="8e18f-144">This stage is a placeholder for the [Party Resolution Pipeline Component](../core/party-resolution-pipeline-component.md).</span></span>  
  
-   <span data-ttu-id="8e18f-145">Cette étape peut être exécutée plusieurs fois.</span><span class="sxs-lookup"><span data-stu-id="8e18f-145">This stage may be run more than once.</span></span> <span data-ttu-id="8e18f-146">Elle est exécutée une fois par message créé par l’étape Désassembler.</span><span class="sxs-lookup"><span data-stu-id="8e18f-146">It runs once per message created by the Disassemble stage.</span></span>  
  
-   <span data-ttu-id="8e18f-147">Cette étape peut contenir entre 0 et 255 composants.</span><span class="sxs-lookup"><span data-stu-id="8e18f-147">This stage can contain between zero and 255 components.</span></span>  
  
-   <span data-ttu-id="8e18f-148">Tous les composants de cette étape sont exécutés.</span><span class="sxs-lookup"><span data-stu-id="8e18f-148">All components in this stage are run.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e18f-149">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8e18f-149">See Also</span></span>  
 <span data-ttu-id="8e18f-150">[Pipelines d’envoi](../core/send-pipelines.md) </span><span class="sxs-lookup"><span data-stu-id="8e18f-150">[Send Pipelines](../core/send-pipelines.md) </span></span>  
 <span data-ttu-id="8e18f-151">[À propos des Pipelines, des étapes et des composants](../core/about-pipelines-stages-and-components.md) </span><span class="sxs-lookup"><span data-stu-id="8e18f-151">[About Pipelines, Stages, and Components](../core/about-pipelines-stages-and-components.md) </span></span>  
 <span data-ttu-id="8e18f-152">[Types de composants de Pipeline](../core/types-of-pipeline-components.md) </span><span class="sxs-lookup"><span data-stu-id="8e18f-152">[Types of Pipeline Components](../core/types-of-pipeline-components.md) </span></span>  
 <span data-ttu-id="8e18f-153">[Pipelines par défaut](../core/default-pipelines.md) </span><span class="sxs-lookup"><span data-stu-id="8e18f-153">[Default Pipelines](../core/default-pipelines.md) </span></span>  
 <span data-ttu-id="8e18f-154">[Modèles de pipeline](../core/pipeline-templates.md) </span><span class="sxs-lookup"><span data-stu-id="8e18f-154">[Pipeline Templates](../core/pipeline-templates.md) </span></span>  
 <span data-ttu-id="8e18f-155">[Composants de pipeline](../core/pipeline-components.md) </span><span class="sxs-lookup"><span data-stu-id="8e18f-155">[Pipeline Components](../core/pipeline-components.md) </span></span>  
 [<span data-ttu-id="8e18f-156">Types de Pipelines</span><span class="sxs-lookup"><span data-stu-id="8e18f-156">Types of Pipelines</span></span>](../core/types-of-pipelines.md)