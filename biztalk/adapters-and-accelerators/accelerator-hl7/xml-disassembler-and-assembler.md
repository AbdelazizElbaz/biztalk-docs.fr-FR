---
title: "Désassembleur XML et assembleur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- disassembler, XML
- assembler, XML
ms.assetid: 242a7a96-2342-4ab5-9d3f-1acbcc7ffd14
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a4978484f888290377986ee4ae8bf049c14a1b31
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="xml-disassembler-and-assembler"></a>Assembleur et désassembleur XML
Le désassembleur XML et l’assembleur de s’assurer que [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator pour HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) prend en charge non seulement les messages encodés HL7, mais prend également en charge les messages XML entrants et/ou sortants.  
  
## <a name="xml-disassembler"></a>Désassembleur XML  
 Le désassembleur XML traite les messages XML entrants en segments XML pour le traitement. Comme il traite les messages, le désassembleur effectue les tâches suivantes :  
  
-   Gère les séquences d’échappement  
  
-   Gère les vérifications des propriétés obligatoire ou facultatif  
  
-   Handles déclarés de segments de Z  
  
 Comme il traite les messages, le désassembleur effectue les opérations suivantes :  
  
-   Validation syntaxique  
  
-   Validation de schéma (si activé)  
  
## <a name="xml-assembler"></a>Assembleur XML  
 L’assembleur XML sérialise les segments XML dans un message XML sortant. L’assembleur XML prend en charge et crée des messages (ACK) de l’accusé de réception suivant :  
  
-   Statique  
  
-   Mode d’origine  
  
-   Mode étendu  
  
 L’assembleur XML a également la possibilité de router les messages d’accusé de réception différés.  
  
## <a name="see-also"></a>Voir aussi  
 [Traitement de BTAHL72XML](../../adapters-and-accelerators/accelerator-hl7/btahl72xml-processing.md)   
 [BizTalk Accelerator pour HL7 composants](../../adapters-and-accelerators/accelerator-hl7/biztalk-accelerator-for-hl7-components.md)