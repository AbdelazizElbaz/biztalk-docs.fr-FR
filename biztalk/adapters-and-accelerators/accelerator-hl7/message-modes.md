---
title: Modes de message | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- message modes, about message modes
- messages, message modes
- message modes, HL7 messages
ms.assetid: 2d832b67-6f0e-45e1-95ac-cb80b74a7831
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b09a610d000ae6beaef75b1ed0144d1597d517b8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="message-modes"></a>Modes de messages
Il existe deux concepts de base qui sous-tendent tous les messages HL7. Ces concepts d’adresses différentes façons dans lequel des systèmes indépendants qui échangent des données peuvent interagir et fournissent une structure qui prend en charge les exigences d’interopérabilité dans le temps au sein d’un système de soins de santé distribué. Les concepts ci-dessous définissent les thèmes sous-jacent derrière la conception HL7 :  
  
-   **Mode de messagerie**. La reconnaissance des trois objectifs fondamentaux pour l’échange d’informations : diffusion des informations (déclaratives), pour demander des informations (interrogative) et vous demande que le système entreprendre une action (impératif). Chacun de ces objectifs a ses besoins et le modèle de flux de messages.  
  
-   **Mode d’accusé de réception**. La nécessité de prendre en charge étroitement et faiblement couplées styles de messagerie. Les modes d’accusé de réception pour HL7 permettent à une application émettrice pour demander une réponse du récepteur, ou pour activer le réseau sous-jacent garantir la remise des messages.  
  
-   **Localisation**. La nécessité de prendre en charge des exigences spécifiques en permettant aux entités introduire des documents spécifiques au site dans les spécifications de message.  
  
-   **Évolution**. La nécessité de prendre en charge des sites avec nombreuses interfaces et de nombreuses applications en activant l’interopérabilité entre les versions standards. Ainsi, les entités à l’étape interface les mises à niveau, sans nécessiter des mises à niveau simultanées de toutes les interfaces.  
  
 Les fonctions suivantes de [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator pour HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) prend en charge les spécifications ci-dessus :  
  
-   Modes d’accusé de réception HL7. [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]prend en charge le mode d’accusé de réception d’origine en passant des accusés de réception application à l’expéditeur du message d’origine.  
  
-   Différents modes de messagerie. Cela permet la diffusion vers plusieurs destinations et relie les requêtes à la réponse de la requête associée.  
  
-   Prise en charge de plusieurs versions, y compris XML et encodages de délimitée par des canaux.  
  
-   Le mappage entre les mises à niveau et les versions HL7 activer divers environnements.  
  
-   Localisation (personnalisation) au sein de l’orchestration.  
  
-   Outils pour prendre en charge le débogage et l’évaluation des nouvelles interfaces.  
  
## <a name="see-also"></a>Voir aussi  
 [Le traitement des Messages HL7](../../adapters-and-accelerators/accelerator-hl7/processing-hl7-messages.md)   
 [L’utilisation des schémas 2.X HL7](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-x-schemas.md)   
 [Utilisation de schémas XML de 2 HL7](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-xml-schemas.md)   
 [Les événements et les Types de messages](../../adapters-and-accelerators/accelerator-hl7/message-types-and-events.md)   
 [La messagerie HL7](../../adapters-and-accelerators/accelerator-hl7/hl7-messaging.md)