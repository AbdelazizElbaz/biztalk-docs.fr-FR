---
title: Le traitement des messages du lot | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- examples, batching
- batching, examples
- batching, batch types
ms.assetid: 264f91b5-3e33-4b87-9da3-866eaa464b0f
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: aad80bb8fe9a59163ee17e7862bece728fdc52b3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="batch-message-processing"></a><span data-ttu-id="2125a-102">Traitement par lots des messages</span><span class="sxs-lookup"><span data-stu-id="2125a-102">Batch Message Processing</span></span>
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]<span data-ttu-id="2125a-103">BizTalk Accelerator pour HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) gère les trois types de HL7 2.X des scénarios de traitement par lots :</span><span class="sxs-lookup"><span data-stu-id="2125a-103"> BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) handles three types of HL7 2.X batch scenarios:</span></span>  
  
-   <span data-ttu-id="2125a-104">Scénario de lot entrant fragmentés.</span><span class="sxs-lookup"><span data-stu-id="2125a-104">Fragmented inbound batch scenario.</span></span> [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="2125a-105">analyse de ces lots dans les messages de sortie distincts.</span><span class="sxs-lookup"><span data-stu-id="2125a-105"> parses these batches into separate output messages.</span></span> [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="2125a-106">envoie les accusés de réception (ACK) pour chaque message dans un lot fragmenté.</span><span class="sxs-lookup"><span data-stu-id="2125a-106"> sends acknowledgments (ACKs) for each message in a fragmented batch.</span></span>  
  
-   <span data-ttu-id="2125a-107">Traitement par lots dans / lots scénario.</span><span class="sxs-lookup"><span data-stu-id="2125a-107">Batch in/batch out scenario.</span></span> <span data-ttu-id="2125a-108">Ceux-ci sont liées dans des lots qui [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] ne pas fragmenter, mais transmet et envoie en tant qu’un lot intact.</span><span class="sxs-lookup"><span data-stu-id="2125a-108">These are in-bound batches that [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] does not fragment, but passes through and sends as an intact batch.</span></span> <span data-ttu-id="2125a-109">Si [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] envoie un accusé de réception du lot, l’accusé de réception inclut un ID de version.</span><span class="sxs-lookup"><span data-stu-id="2125a-109">If [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] sends an ACK for the batch, the ACK includes a version ID.</span></span>  
  
-   <span data-ttu-id="2125a-110">Scénario de créer de lot.</span><span class="sxs-lookup"><span data-stu-id="2125a-110">Create-batch scenario.</span></span> <span data-ttu-id="2125a-111">Dans ce scénario, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] combine sépare les messages d’entrée dans un lot de sortie.</span><span class="sxs-lookup"><span data-stu-id="2125a-111">In this scenario, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] combines separate input messages into an output batch.</span></span>  
  
 <span data-ttu-id="2125a-112">Vous pouvez mettre en forme les lots de deux manières :</span><span class="sxs-lookup"><span data-stu-id="2125a-112">You can format batches in either of two ways:</span></span>  
  
-   <span data-ttu-id="2125a-113">Avec un en-tête de fichier et le code de fin (FHS/FTS) et un en-tête de lot et code de fin (BHS/BTS).</span><span class="sxs-lookup"><span data-stu-id="2125a-113">With a file header and trailer (FHS/FTS) and a batch header and trailer (BHS/BTS).</span></span>  
  
-   <span data-ttu-id="2125a-114">Avec aucun fichier ou le lot en-têtes/codes.</span><span class="sxs-lookup"><span data-stu-id="2125a-114">With no file or batch headers/trailers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2125a-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2125a-115">See Also</span></span>  
 <span data-ttu-id="2125a-116">[Le traitement par lots du message](../../adapters-and-accelerators/accelerator-hl7/message-batching.md) </span><span class="sxs-lookup"><span data-stu-id="2125a-116">[Message Batching](../../adapters-and-accelerators/accelerator-hl7/message-batching.md) </span></span>  
 <span data-ttu-id="2125a-117">[Didacticiel de traitement par lot](../../adapters-and-accelerators/accelerator-hl7/batching-tutorial.md) </span><span class="sxs-lookup"><span data-stu-id="2125a-117">[Batching Tutorial](../../adapters-and-accelerators/accelerator-hl7/batching-tutorial.md) </span></span>  
 <span data-ttu-id="2125a-118">[Partie 1 : Scénario de lot entrant fragmenté](../../adapters-and-accelerators/accelerator-hl7/part-1-fragmented-inbound-batch-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="2125a-118">[Part 1: Fragmented Inbound Batch Scenario](../../adapters-and-accelerators/accelerator-hl7/part-1-fragmented-inbound-batch-scenario.md) </span></span>  
 <span data-ttu-id="2125a-119">[Partie 2 : Traitement par lots de dans / lots scénario](../../adapters-and-accelerators/accelerator-hl7/part-2-batch-in-batch-out-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="2125a-119">[Part 2: Batch In/Batch Out Scenario](../../adapters-and-accelerators/accelerator-hl7/part-2-batch-in-batch-out-scenario.md) </span></span>  
 <span data-ttu-id="2125a-120">[Partie 3 : Scénario de traitement par lots Créer](../../adapters-and-accelerators/accelerator-hl7/part-3-create-batch-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="2125a-120">[Part 3: Create-Batch Scenario](../../adapters-and-accelerators/accelerator-hl7/part-3-create-batch-scenario.md) </span></span>  
 [<span data-ttu-id="2125a-121">Traitement des messages</span><span class="sxs-lookup"><span data-stu-id="2125a-121">Message Processing</span></span>](../../adapters-and-accelerators/accelerator-hl7/message-processing.md)