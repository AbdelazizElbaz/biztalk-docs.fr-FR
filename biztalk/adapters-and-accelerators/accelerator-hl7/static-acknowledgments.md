---
title: "Accusés de réception statiques | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- static acknowledgements
- acknowledgements, static acknowledgements
ms.assetid: 1cdd01fc-1dae-4851-917f-4f13a0f9595a
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8081dc0f3c37c40cb1103567ae06f80037a12730
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="static-acknowledgments"></a>Accusés de réception statiques
BizTalk Accelerator pour HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) prend en charge les modes d’origine, améliorée, différée et statiques d’accusé de réception (ACK). Si vous sélectionnez mode statique de l’accusé de réception pour un tiers dans [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Configuration Explorateur, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] génère des accusés de réception statiques qui contiennent uniquement une indication de réussite ou l’échec. L’accusé de réception statique indique si le système de réception reçu et traité le message, dans le cas de réussite et Échec valeurs configurées dans [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] l’Explorateur de Configuration.  
  
 D’origine, amélioré et des modes, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] génère des accusés de réception dynamiques. Ils sont codés HL7 et contiennent des champs tels que le champ Code d’accusé de réception MSA.1 et le segment ERR. Le champ MSA.1 d’un accusé de réception dynamique indique si une condition d’échec est le rejet ou une erreur, ce qui entraîne un traitement différent (consultez [Segment d’accusé de réception de Message](../../adapters-and-accelerators/accelerator-hl7/message-acknowledgment-segment.md)). Le segment ERR fournit des informations détaillées sur l’erreur. Accusés de réception statiques ne fournissent aucune information.  
  
 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]traite un accusé de réception statique différemment d’un accusé de réception dynamique. Si un port d’envoi bidirectionnel (qui n’envoie le message suivant après avoir reçu l’accusé de réception) reçoit l’accusé de réception statique et l’accusé de réception indique un échec (ou n’est pas un accusé de réception valide), [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] sera déplacer vers le transport secondaire ou suspendre le message. Il ne sera pas relancé le message, comme si elle a reçu un accusé de réception dynamique, en fonction de la condition d’échec.  
  
 Lorsque le [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] analyseur traite un accusé de réception statique, il écrit la **IsStaticAck** propriété booléenne dans le contexte du message. Le sérialiseur utilise cette valeur pour déterminer si elle doit traiter le message comme un accusé de réception statique.  
  
## <a name="see-also"></a>Voir aussi  
 [Création et le traitement des accusés de réception](../../adapters-and-accelerators/accelerator-hl7/creating-and-processing-acknowledgments.md)   
 [Segment de message d’accusé de réception](../../adapters-and-accelerators/accelerator-hl7/message-acknowledgment-segment.md)