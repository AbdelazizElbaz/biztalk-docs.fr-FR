---
title: Traitement de BTAHL72XML | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- 2.XML messages, processing
- acknowledgements, 2.XML messages
- 2.XML messages, message modes
- message modes, 2.XML message
- 2.XML messages
- validating, 2.XML messages
- 2.XML messages, acknowledgements
- 2.XML messages, validating
ms.assetid: 2f12cb44-816c-4773-9db0-9cbc3d1b1aee
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e86697884c28d71fa9fb91c8b276293f7d36a588
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="btahl72xml-processing"></a>Traitement de BTAHL72XML
Les composants suivants dans [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator pour HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) traiter les messages HL7 2 XML (codé en XML) :  
  
-   Pipelines et les bibliothèques principales : [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]. PipelineCommon.dll et [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]. PipelineMessageCore.dll  
  
-   Bibliothèques d’assembleur et désassembleur : [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]. HL72XmlAsm.dll et [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]. HL72XmlDAsm.dll  
  
-   Adaptateur d’envoi de la bibliothèque de validation d’accusé de réception (ACK) utilisée pour le MLLP bidirectionnelle : [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]. HL7ACKHelper.dll  
  
## <a name="xml-message-modes"></a>Modes de Message XML  
 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]prend en charge les modes de message suivants pour les messages XML de 2 :  
  
-   Mode éditeur-abonné (pub-sub)  
  
     Le serveur de publication diffuse à un tiers d’abonnés, comme déclaratives ou une non sollicité mise à jour. [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]et [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] fournissent une grande souplesse pour ce mode, étant donné que vous pouvez gérer les abonnements et les parties après le moment du design.  
  
-   Mode de requête-réponse  
  
     Un échange de messages interrogative ou d’une requête dans lequel une demande spécifique à partir d’une entité spécifique génère un message de répond.  
  
## <a name="xml-validation"></a>Validation XML  
 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]Fournit la validation suivante de 2. des messages XML :  
  
-   Lecteur XML  
  
-   Schéma  
  
     Pour activer ou désactiver la validation de schéma par le tiers. [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]utilise les schémas XML de 2 HL7 directement lors du traitement, de déterminée par le champ d’en-tête MSH9.3 structure de message et le champ d’ID de Version MSH12 (2.3.1, 2.4 ou 2.5). [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]utilise les fonctions de traitement XML standards dans [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].  
  
-   Segment de Z  
  
     [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]valide qu’aucun segment déclarée n’est inclus dans un segment Z non déclaré.  
  
## <a name="ack-generation"></a>Génération de l’accusé de réception  
 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]prend en charge les types d’accusés de réception (ACK) suivants pour les messages XML de 2. Les deux le type d’erreur HL7 et [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] type d’erreur (secondaire) sont utilisées :  
  
-   Accusés de réception d’origine HL7  
  
-   HL7 améliorée des accusés de réception  
  
     Validation acceptent et Application  
  
## <a name="see-also"></a>Voir aussi  
 [Traitement des messages](../../adapters-and-accelerators/accelerator-hl7/message-processing.md)   
 [Utilisation de schémas XML de 2 HL7](../../adapters-and-accelerators/accelerator-hl7/using-hl7-2-xml-schemas.md)