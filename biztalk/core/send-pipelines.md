---
title: "Pipelines d’envoi | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- send pipelines, message flow
- send pipelines, about send pipelines
- messages, message flow
- send pipelines, stages
- pipelines, send pipelines
- messages, send pipelines
ms.assetid: c963b2d8-3b2b-4575-8105-c750deae8189
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ef08909dbc47e11f5c9fecae6f65e01dbe79441b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="send-pipelines"></a><span data-ttu-id="fbf6b-102">Pipelines d’envoi</span><span class="sxs-lookup"><span data-stu-id="fbf6b-102">Send Pipelines</span></span>
<span data-ttu-id="fbf6b-103">La figure présente le workflow de traitement d'un message en mettant en avant le rôle du pipeline d'envoi.</span><span class="sxs-lookup"><span data-stu-id="fbf6b-103">The following figure shows the message processing workflow, highlighting the send pipeline.</span></span>  
  
 <span data-ttu-id="fbf6b-104">![Diagramme de flux de travail pour le traitement d’un message. ] (../core/media/ebiz-dev-busprcsadptc.gif "ebiz_dev_busprcsadptc")</span><span class="sxs-lookup"><span data-stu-id="fbf6b-104">![Diagram of workflow for processing a message.](../core/media/ebiz-dev-busprcsadptc.gif "ebiz_dev_busprcsadptc")</span></span>  
<span data-ttu-id="fbf6b-105">Illustration du workflow de traitement d'un message</span><span class="sxs-lookup"><span data-stu-id="fbf6b-105">Depicts the message processing workflow.</span></span>  
  
 <span data-ttu-id="fbf6b-106">Un pipeline d'envoi est chargé de traiter les documents avant leur envoi vers leur destination finale.</span><span class="sxs-lookup"><span data-stu-id="fbf6b-106">A send pipeline is responsible for processing documents before sending them to their final destinations.</span></span> <span data-ttu-id="fbf6b-107">Il prend en charge un message et produit un message à envoyer.</span><span class="sxs-lookup"><span data-stu-id="fbf6b-107">The send pipeline takes one message and produces one message to send.</span></span>  
  
 <span data-ttu-id="fbf6b-108">Vous pouvez créer un pipeline d'envoi ou utiliser l'un des deux pipelines d'envoi par défaut fournis avec BizTalk Server, le pipeline d'envoi de transfert et le pipeline d'envoi XML.</span><span class="sxs-lookup"><span data-stu-id="fbf6b-108">You can create a new send pipeline or you can use one of the two default send pipelines included in BizTalk Server—the pass-through send pipeline and the XML send pipeline.</span></span>  
  
 <span data-ttu-id="fbf6b-109">Par défaut, le pipeline d’envoi se compose de trois étapes vides : préassembler, assembler et coder.</span><span class="sxs-lookup"><span data-stu-id="fbf6b-109">By default, the send pipeline consists of three empty stages: Pre-assemble, Assemble and Encode.</span></span> <span data-ttu-id="fbf6b-110">Cette rubrique regroupe des considérations relatives à la conception pour compléter ces étapes.</span><span class="sxs-lookup"><span data-stu-id="fbf6b-110">This topic contains design considerations for populating these stages.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fbf6b-111">Un pipeline d'envoi peut ne produire aucun message quand un composant de consommation lui est ajouté.</span><span class="sxs-lookup"><span data-stu-id="fbf6b-111">A send pipeline can produce zero messages when a consuming component is added to the pipeline.</span></span>  
  
## <a name="pre-assemble-stage"></a><span data-ttu-id="fbf6b-112">Étape Préassembler</span><span class="sxs-lookup"><span data-stu-id="fbf6b-112">Pre-assemble stage</span></span>  
  
-   <span data-ttu-id="fbf6b-113">Cette étape est un espace réservé aux composants personnalisés qui doivent exécuter une action sur le message avant que ce dernier soit sérialisé.</span><span class="sxs-lookup"><span data-stu-id="fbf6b-113">This stage is a placeholder for custom components that should perform some action on the message before the message is serialized.</span></span>  
  
-   <span data-ttu-id="fbf6b-114">Cette étape est exécutée une seule fois par message.</span><span class="sxs-lookup"><span data-stu-id="fbf6b-114">This stage is run once per message.</span></span>  
  
-   <span data-ttu-id="fbf6b-115">Cette étape peut contenir entre 0 et 255 composants.</span><span class="sxs-lookup"><span data-stu-id="fbf6b-115">This stage can contain between zero and 255 components.</span></span>  
  
-   <span data-ttu-id="fbf6b-116">Tous les composants de cette étape sont exécutés.</span><span class="sxs-lookup"><span data-stu-id="fbf6b-116">All components in this stage are run.</span></span>  
  
## <a name="assemble-stage"></a><span data-ttu-id="fbf6b-117">Étape Assembler</span><span class="sxs-lookup"><span data-stu-id="fbf6b-117">Assemble stage</span></span>  
  
-   <span data-ttu-id="fbf6b-118">Les composants de cette étape sont chargés d'assembler ou de sérialiser le message et de le convertir au format XML ou à partir de ce format.</span><span class="sxs-lookup"><span data-stu-id="fbf6b-118">Components in this stage are responsible for assembling or serializing the message and converting it to or from XML.</span></span>  
  
-   <span data-ttu-id="fbf6b-119">Cette étape accepte zéro ou un composant.</span><span class="sxs-lookup"><span data-stu-id="fbf6b-119">This stage accepts zero components or one component.</span></span>  
  
-   <span data-ttu-id="fbf6b-120">Tous les composants de cette étape sont exécutés.</span><span class="sxs-lookup"><span data-stu-id="fbf6b-120">All components in this stage are run.</span></span>  
  
## <a name="encode-stage"></a><span data-ttu-id="fbf6b-121">Étape Coder</span><span class="sxs-lookup"><span data-stu-id="fbf6b-121">Encode stage</span></span>  
  
-   <span data-ttu-id="fbf6b-122">Cette étape est destinée aux composants qui codent ou chiffrent le message.</span><span class="sxs-lookup"><span data-stu-id="fbf6b-122">This stage is used for components that encode or encrypt the message.</span></span>  
  
    -   <span data-ttu-id="fbf6b-123">Vous devez placer le composant Encodeur MIME/SMIME ou un composant de codage personnalisé à cette étape si la signature du message est requise.</span><span class="sxs-lookup"><span data-stu-id="fbf6b-123">Place the MIME/SMIME Encoder component or a custom encoding component in this stage if message signing is required.</span></span>  
  
-   <span data-ttu-id="fbf6b-124">Cette étape est exécutée une seule fois par message.</span><span class="sxs-lookup"><span data-stu-id="fbf6b-124">This stage is run once per message.</span></span>  
  
-   <span data-ttu-id="fbf6b-125">Cette étape peut contenir entre 0 et 255 composants.</span><span class="sxs-lookup"><span data-stu-id="fbf6b-125">This stage can contain between zero and 255 components.</span></span>  
  
-   <span data-ttu-id="fbf6b-126">Tous les composants de cette étape sont exécutés.</span><span class="sxs-lookup"><span data-stu-id="fbf6b-126">All components in this stage are executed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fbf6b-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fbf6b-127">See Also</span></span>  
 <span data-ttu-id="fbf6b-128">[Pipelines de réception](../core/receive-pipelines.md) </span><span class="sxs-lookup"><span data-stu-id="fbf6b-128">[Receive Pipelines](../core/receive-pipelines.md) </span></span>  
 <span data-ttu-id="fbf6b-129">[À propos des Pipelines, des étapes et des composants](../core/about-pipelines-stages-and-components.md) </span><span class="sxs-lookup"><span data-stu-id="fbf6b-129">[About Pipelines, Stages, and Components](../core/about-pipelines-stages-and-components.md) </span></span>  
 <span data-ttu-id="fbf6b-130">[Types de Pipelines](../core/types-of-pipelines.md) </span><span class="sxs-lookup"><span data-stu-id="fbf6b-130">[Types of Pipelines](../core/types-of-pipelines.md) </span></span>  
 <span data-ttu-id="fbf6b-131">[Pipelines par défaut](../core/default-pipelines.md) </span><span class="sxs-lookup"><span data-stu-id="fbf6b-131">[Default Pipelines](../core/default-pipelines.md) </span></span>  
 <span data-ttu-id="fbf6b-132">[Modèles de pipeline](../core/pipeline-templates.md) </span><span class="sxs-lookup"><span data-stu-id="fbf6b-132">[Pipeline Templates](../core/pipeline-templates.md) </span></span>  
 <span data-ttu-id="fbf6b-133">[Composants de pipeline](../core/pipeline-components.md) </span><span class="sxs-lookup"><span data-stu-id="fbf6b-133">[Pipeline Components](../core/pipeline-components.md) </span></span>  
 [<span data-ttu-id="fbf6b-134">Types de composants de Pipeline</span><span class="sxs-lookup"><span data-stu-id="fbf6b-134">Types of Pipeline Components</span></span>](../core/types-of-pipeline-components.md)