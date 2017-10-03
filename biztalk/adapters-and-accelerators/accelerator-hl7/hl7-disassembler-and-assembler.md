---
title: "HL7 Désassembleur et assembleur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- assembler, HL7
- disassembler, HL7
ms.assetid: 54e83a04-86c8-482f-bea3-dbbdeb4584d6
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e81d621656fc678196f7f6fb709b29de87a3aaf9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="hl7-disassembler-and-assembler"></a>HL7 Désassembleur et assembleur
Le HL7 désassembleur et assembleur prennent en charge les messages à encodage HL7. Étant donné que [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] traite les messages en mode natif au format XML, [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator pour HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) utilise le HL7 désassembleur et assembleur pour faire [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] un moteur d’intégration HL7.  
  
## <a name="hl7-disassembler"></a>Désassembleur de HL7  
 Le désassembleur de HL7 analyse les messages entrants HL7 encodé en segments XML pour le traitement. Il effectue la validation de l’en-tête de message et du corps de la validation de base. Il détermine le schéma qu’il utilise pour analyser le message HL7 (consultez [détermination du schéma dans le HL7 2.X désassembleur](../../adapters-and-accelerators/accelerator-hl7/schema-determination-in-the-hl7-2-x-disassembler.md)), détermine la partie de la source du message et effectue une validation supplémentaire du corps (s’il est activé pour le tiers).  
  
## <a name="hl7-assembler"></a>HL7 assembleur  
 L’assembleur HL7 sérialise les segments XML dans un message HL7 sortant. Il détermine le schéma qu’il utilise pour sérialiser le message HL7 (consultez [détermination du schéma dans le HL7 2.X assembleur](../../adapters-and-accelerators/accelerator-hl7/schema-determination-in-the-hl7-2-x-assembler.md)), détermine le tiers de destination pour le message et effectue la validation du corps (si activé pour le tiers).  
  
 L’assembleur peut sérialiser les messages d’accusé de réception (ACK) suivants :  
  
-   Statique  
  
-   Mode d’origine  
  
-   Mode étendu  
  
 L’assembleur HL7 a également la possibilité de router les messages d’accusé de réception différés.  
  
## <a name="see-also"></a>Voir aussi  
 [Traitement des fichiers plats BTAHL72X](../../adapters-and-accelerators/accelerator-hl7/btahl72x-flat-file-processing.md)   
 [BizTalk Accelerator pour HL7 composants](../../adapters-and-accelerators/accelerator-hl7/biztalk-accelerator-for-hl7-components.md)