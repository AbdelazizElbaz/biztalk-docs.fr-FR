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
# <a name="batch-orchestration"></a>Orchestration de traitement par lots
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]BizTalk Accelerator pour HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) fournit une orchestration (BatchOrchestration.dll) que vous pouvez utiliser pour traiter les lots. Cette orchestration peut traiter par lots de messages de HL7 encodé (2.X) et/ou les accusés de réception (ACK). L’orchestration est natif [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] orchestration ajoutée par [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] le programme d’installation à votre ensemble d’orchestrations BizTalk (comme indiqué dans les Orchestrations dans l’Explorateur BizTalk).  
  
 L’orchestration fonctionne avec activation du lot, arrêt du lot, et la minuterie du traitement des messages que [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] utilise pour contrôler les lots. L’orchestration fonctionne également avec le port de contrôle de traitement par lots, qui est une opération de réception du port qui [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] le programme d’installation installe pour traiter les messages de contrôle de traitement par lots.  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiel de traitement par lot](../../adapters-and-accelerators/accelerator-hl7/batching-tutorial.md)   
 [BizTalk Accelerator pour HL7 composants](../../adapters-and-accelerators/accelerator-hl7/biztalk-accelerator-for-hl7-components.md)