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
# <a name="batch-message-processing"></a>Traitement par lots des messages
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]BizTalk Accelerator pour HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) gère les trois types de HL7 2.X des scénarios de traitement par lots :  
  
-   Scénario de lot entrant fragmentés. [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]analyse de ces lots dans les messages de sortie distincts. [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]envoie les accusés de réception (ACK) pour chaque message dans un lot fragmenté.  
  
-   Traitement par lots dans / lots scénario. Ceux-ci sont liées dans des lots qui [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] ne pas fragmenter, mais transmet et envoie en tant qu’un lot intact. Si [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] envoie un accusé de réception du lot, l’accusé de réception inclut un ID de version.  
  
-   Scénario de créer de lot. Dans ce scénario, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] combine sépare les messages d’entrée dans un lot de sortie.  
  
 Vous pouvez mettre en forme les lots de deux manières :  
  
-   Avec un en-tête de fichier et le code de fin (FHS/FTS) et un en-tête de lot et code de fin (BHS/BTS).  
  
-   Avec aucun fichier ou le lot en-têtes/codes.  
  
## <a name="see-also"></a>Voir aussi  
 [Le traitement par lots du message](../../adapters-and-accelerators/accelerator-hl7/message-batching.md)   
 [Didacticiel de traitement par lot](../../adapters-and-accelerators/accelerator-hl7/batching-tutorial.md)   
 [Partie 1 : Scénario de lot entrant fragmenté](../../adapters-and-accelerators/accelerator-hl7/part-1-fragmented-inbound-batch-scenario.md)   
 [Partie 2 : Traitement par lots de dans / lots scénario](../../adapters-and-accelerators/accelerator-hl7/part-2-batch-in-batch-out-scenario.md)   
 [Partie 3 : Scénario de traitement par lots Créer](../../adapters-and-accelerators/accelerator-hl7/part-3-create-batch-scenario.md)   
 [Traitement des messages](../../adapters-and-accelerators/accelerator-hl7/message-processing.md)