---
title: Orchestration de traitement par lots | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- batching, acknowledgements
- acknowledgements, batching
- batch orchestration
- orchestrations, batch orchestration
- messages, batching
- batching, batch orchestration
- batching, messages
ms.assetid: b449d8d5-72a2-46c8-a2b1-380431175f4d
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9db6ee8b4fd3dec8e2902642634b701889866cf8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="batch-orchestration"></a><span data-ttu-id="028c5-102">Orchestration de traitement par lots</span><span class="sxs-lookup"><span data-stu-id="028c5-102">Batch Orchestration</span></span>
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]<span data-ttu-id="028c5-103">BizTalk Accelerator pour HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) fournit une orchestration (BatchOrchestration.dll) que vous pouvez utiliser pour traiter les lots.</span><span class="sxs-lookup"><span data-stu-id="028c5-103"> BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) provides an orchestration (BatchOrchestration.dll) that you can use to process batches.</span></span> <span data-ttu-id="028c5-104">Cette orchestration peut traiter par lots de messages de HL7 encodé (2.X) et/ou les accusés de réception (ACK).</span><span class="sxs-lookup"><span data-stu-id="028c5-104">This orchestration can process batches of HL7-encoded (2.X) messages and/or acknowledgments (ACKs).</span></span> <span data-ttu-id="028c5-105">L’orchestration est natif [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] orchestration ajoutée par [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] le programme d’installation à votre ensemble d’orchestrations BizTalk (comme indiqué dans les Orchestrations dans l’Explorateur BizTalk).</span><span class="sxs-lookup"><span data-stu-id="028c5-105">The orchestration is a native [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] orchestration added by [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] setup to your set of BizTalk orchestrations (as listed under Orchestrations in BizTalk Explorer).</span></span>  
  
 <span data-ttu-id="028c5-106">L’orchestration fonctionne avec activation du lot, arrêt du lot, et la minuterie du traitement des messages que [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] utilise pour contrôler les lots.</span><span class="sxs-lookup"><span data-stu-id="028c5-106">The orchestration works with batch activation, batch termination, and batch timer messages that [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] uses to control batches.</span></span> <span data-ttu-id="028c5-107">L’orchestration fonctionne également avec le port de contrôle de traitement par lots, qui est une opération de réception du port qui [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] le programme d’installation installe pour traiter les messages de contrôle de traitement par lots.</span><span class="sxs-lookup"><span data-stu-id="028c5-107">The orchestration also works with the batch control port, which is a receive port that [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] setup installs to handle batch control messages.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="028c5-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="028c5-108">See Also</span></span>  
 <span data-ttu-id="028c5-109">[Didacticiel de traitement par lot](../../adapters-and-accelerators/accelerator-hl7/batching-tutorial.md) </span><span class="sxs-lookup"><span data-stu-id="028c5-109">[Batching Tutorial](../../adapters-and-accelerators/accelerator-hl7/batching-tutorial.md) </span></span>  
 [<span data-ttu-id="028c5-110">BizTalk Accelerator pour HL7 composants</span><span class="sxs-lookup"><span data-stu-id="028c5-110">BizTalk Accelerator for HL7 Components</span></span>](../../adapters-and-accelerators/accelerator-hl7/biztalk-accelerator-for-hl7-components.md)