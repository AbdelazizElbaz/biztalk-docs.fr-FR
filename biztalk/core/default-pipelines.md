---
title: "Pipelines par défaut | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pipelines, PassThruTransmit
- pipelines, PassThruReceive
- pipelines, XMLTransmit
- pipelines, StsReceive
- pipelines, StsSend
- pipelines, StsFileReceive
- Microsoft.BizTalk.KwTpm.StsDefaultPipelines.EnvSchema XML envelope
- pipelines, XMLReceive
- pipelines, backward compatibility
- Microsoft.BizTalk.DefaultPipelines assembly
- pipelines, default
ms.assetid: 7d82bb2c-c7f1-44a1-9e1b-89b0bb806845
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8ceb3f06f2e2b57ec37bc4a95a385574de594940
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="default-pipelines"></a><span data-ttu-id="fb1eb-102">Pipelines par défaut</span><span class="sxs-lookup"><span data-stu-id="fb1eb-102">Default Pipelines</span></span>
<span data-ttu-id="fb1eb-103">Lorsque vous créez une application, les pipelines par défaut sont créés et déployés par défaut et apparaissent dans l'assembly Microsoft.BizTalk.DefaultPipelines, dans le dossier \References de chaque projet BizTalk.</span><span class="sxs-lookup"><span data-stu-id="fb1eb-103">When you create a new application, the default pipelines are created and deployed by default and appear in the Microsoft.BizTalk.DefaultPipelines assembly in the \References folder for every BizTalk project.</span></span> <span data-ttu-id="fb1eb-104">Ces pipelines ne peuvent pas être modifiés dans le Concepteur de pipeline.</span><span class="sxs-lookup"><span data-stu-id="fb1eb-104">The default pipelines cannot be modified in Pipeline Designer.</span></span> <span data-ttu-id="fb1eb-105">Ils peuvent être sélectionnés au moment de la configuration d'un port d'envoi ou d'un emplacement de réception dans l'Explorateur BizTalk.</span><span class="sxs-lookup"><span data-stu-id="fb1eb-105">These pipelines can be selected when configuring a send port or receive location in BizTalk Explorer.</span></span> <span data-ttu-id="fb1eb-106">Cette rubrique décrit ce que sont les pipelines par défaut et explique quand les utiliser.</span><span class="sxs-lookup"><span data-stu-id="fb1eb-106">This topic describes the default pipelines and when to use them.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fb1eb-107">Les pipelines d'envoi et de réception XML ne prennent pas en charge les documents XML de taille supérieure à 4 gigaoctets.</span><span class="sxs-lookup"><span data-stu-id="fb1eb-107">The XML receive and XML send pipelines do not support XML documents larger than 4 gigabytes.</span></span>  
  
## <a name="passthrureceive-pipeline"></a><span data-ttu-id="fb1eb-108">Pipeline PassThruReceive</span><span class="sxs-lookup"><span data-stu-id="fb1eb-108">PassThruReceive pipeline</span></span>  
 <span data-ttu-id="fb1eb-109">Le pipeline de réception de transfert n'a pas de composants.</span><span class="sxs-lookup"><span data-stu-id="fb1eb-109">The pass-through receive pipeline has no components.</span></span> <span data-ttu-id="fb1eb-110">Il est utilisé dans le cadre des scénarios de transfert simples, quand aucun traitement de charge de message n'est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="fb1eb-110">It is used for simple pass-through scenarios when no message payload processing is necessary.</span></span> <span data-ttu-id="fb1eb-111">On s'en sert généralement lorsque la source et la destination du message sont connues et que le message ne requiert ni validation, ni codage, ni désassemblage.</span><span class="sxs-lookup"><span data-stu-id="fb1eb-111">This pipeline is generally used when the source and the destination of the message are known, and the message requires no validation, encoding, or disassembling.</span></span> <span data-ttu-id="fb1eb-112">Il est fréquemment utilisé avec le pipeline d'envoi de transfert.</span><span class="sxs-lookup"><span data-stu-id="fb1eb-112">This pipeline is commonly used in conjunction with the pass-through send pipeline.</span></span>  
  
 <span data-ttu-id="fb1eb-113">Ne comportant pas de désassembleur, le pipeline de réception de transfert ne peut pas servir pour acheminer des messages vers des orchestrations.</span><span class="sxs-lookup"><span data-stu-id="fb1eb-113">Because it does not contain a disassembler, the pass-through receive pipeline cannot be used to route messages to orchestrations.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fb1eb-114">Le pipeline de réception de transfert ne prend pas en charge la promotion des propriétés.</span><span class="sxs-lookup"><span data-stu-id="fb1eb-114">The pass-through receive pipeline does not support property promotion.</span></span>  
  
## <a name="passthrutransmit-pipeline"></a><span data-ttu-id="fb1eb-115">Pipeline PassThruTransmit</span><span class="sxs-lookup"><span data-stu-id="fb1eb-115">PassThruTransmit pipeline</span></span>  
 <span data-ttu-id="fb1eb-116">Le pipeline d'envoi de transfert n'a pas de composants.</span><span class="sxs-lookup"><span data-stu-id="fb1eb-116">The pass-through-send pipeline has no components.</span></span> <span data-ttu-id="fb1eb-117">On s'en sert généralement lorsque aucun traitement de document n'est nécessaire avant l'envoi du message vers une destination.</span><span class="sxs-lookup"><span data-stu-id="fb1eb-117">This pipeline is generally used when no document processing is necessary before sending the message to a destination.</span></span>  
  
## <a name="xmlreceive-pipeline"></a><span data-ttu-id="fb1eb-118">Pipeline XMLReceive</span><span class="sxs-lookup"><span data-stu-id="fb1eb-118">XMLReceive pipeline</span></span>  
 <span data-ttu-id="fb1eb-119">Le pipeline de réception XML est composé des phases suivantes :</span><span class="sxs-lookup"><span data-stu-id="fb1eb-119">The XML receive pipeline consists of the following stages:</span></span>  
  
-   <span data-ttu-id="fb1eb-120">**Décoder.**</span><span class="sxs-lookup"><span data-stu-id="fb1eb-120">**Decode.**</span></span> <span data-ttu-id="fb1eb-121">Vide</span><span class="sxs-lookup"><span data-stu-id="fb1eb-121">Empty</span></span>  
  
-   <span data-ttu-id="fb1eb-122">**Désassembler.**</span><span class="sxs-lookup"><span data-stu-id="fb1eb-122">**Disassemble.**</span></span> <span data-ttu-id="fb1eb-123">contient le composant Désassembleur XML.</span><span class="sxs-lookup"><span data-stu-id="fb1eb-123">Contains the XML Disassembler component</span></span>  
  
-   <span data-ttu-id="fb1eb-124">**Valider.**</span><span class="sxs-lookup"><span data-stu-id="fb1eb-124">**Validate.**</span></span> <span data-ttu-id="fb1eb-125">Vide</span><span class="sxs-lookup"><span data-stu-id="fb1eb-125">Empty</span></span>  
  
-   <span data-ttu-id="fb1eb-126">**Résoudretiers.**</span><span class="sxs-lookup"><span data-stu-id="fb1eb-126">**ResolveParty.**</span></span> <span data-ttu-id="fb1eb-127">exécute le composant Résolution du tiers, qui résout l'objet du certificat ou l'ID de sécurité source vers l'ID de tiers.</span><span class="sxs-lookup"><span data-stu-id="fb1eb-127">Runs the Party Resolution component, which resolves the certificate subject or the source security ID to the party ID.</span></span>  
  
## <a name="xmltransmit-pipeline"></a><span data-ttu-id="fb1eb-128">Pipeline XMLTransmit</span><span class="sxs-lookup"><span data-stu-id="fb1eb-128">XMLTransmit pipeline</span></span>  
 <span data-ttu-id="fb1eb-129">Le pipeline d'envoi XML est composé des phases suivantes :</span><span class="sxs-lookup"><span data-stu-id="fb1eb-129">The XML send pipeline consists of the following stages:</span></span>  
  
-   <span data-ttu-id="fb1eb-130">**Préassembler.**</span><span class="sxs-lookup"><span data-stu-id="fb1eb-130">**Pre-assemble.**</span></span> <span data-ttu-id="fb1eb-131">Vide</span><span class="sxs-lookup"><span data-stu-id="fb1eb-131">Empty</span></span>  
  
-   <span data-ttu-id="fb1eb-132">**Assembler.**</span><span class="sxs-lookup"><span data-stu-id="fb1eb-132">**Assemble.**</span></span> <span data-ttu-id="fb1eb-133">contient le composant Assembleur XML.</span><span class="sxs-lookup"><span data-stu-id="fb1eb-133">Contains the XML Assembler component</span></span>  
  
-   <span data-ttu-id="fb1eb-134">**Encoder.**</span><span class="sxs-lookup"><span data-stu-id="fb1eb-134">**Encode.**</span></span> <span data-ttu-id="fb1eb-135">Vide</span><span class="sxs-lookup"><span data-stu-id="fb1eb-135">Empty</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb1eb-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fb1eb-136">See Also</span></span>  
 <span data-ttu-id="fb1eb-137">[Types de Pipelines](../core/types-of-pipelines.md) </span><span class="sxs-lookup"><span data-stu-id="fb1eb-137">[Types of Pipelines](../core/types-of-pipelines.md) </span></span>  
 <span data-ttu-id="fb1eb-138">[Types de composants de Pipeline](../core/types-of-pipeline-components.md) </span><span class="sxs-lookup"><span data-stu-id="fb1eb-138">[Types of Pipeline Components](../core/types-of-pipeline-components.md) </span></span>  
 <span data-ttu-id="fb1eb-139">[Modèles de pipeline](../core/pipeline-templates.md) </span><span class="sxs-lookup"><span data-stu-id="fb1eb-139">[Pipeline Templates](../core/pipeline-templates.md) </span></span>  
 <span data-ttu-id="fb1eb-140">[Composants de pipeline](../core/pipeline-components.md) </span><span class="sxs-lookup"><span data-stu-id="fb1eb-140">[Pipeline Components](../core/pipeline-components.md) </span></span>  
 [<span data-ttu-id="fb1eb-141">À propos des Pipelines, des étapes et des composants</span><span class="sxs-lookup"><span data-stu-id="fb1eb-141">About Pipelines, Stages, and Components</span></span>](../core/about-pipelines-stages-and-components.md)