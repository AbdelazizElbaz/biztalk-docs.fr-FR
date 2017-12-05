---
title: Le flux des Messages via BTAHL7 | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- messages, message processing
- messages, message flow
- BTAHL7, message flow
ms.assetid: dd4599af-500d-4e52-85b2-8b6a28fd3f0a
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 33f06c896b58b2ba57c8c1bcee598d23f81b7700
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="how-messages-flow-through-btahl7"></a>Le flux des Messages via BTAHL7
Lorsque vous installez [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator pour HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) sur [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]BizTalk Server, vous ajoutez [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] composants à la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] architecture. La figure suivante illustre le système combiné, qui fournit une présentation de l’architecture de [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)].  
  
 ![](../../adapters-and-accelerators/accelerator-hl7/media/bcd-hl7-sys-archc.gif "bcd_hl7_sys_archc")  
  
## <a name="message-processing-flow"></a>Flux de traitement de message  
 Lorsqu’une application métier-envoie un message à la [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] système, les éléments suivants se produisent :  
  
1.  Si le message est un message HL7, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] reçoit via un adaptateur (généralement un adaptateur MLLP). S’il s’agit d’un message XML, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] reçoit via un adaptateur (généralement un adaptateur HTTP).  
  
    > [!NOTE]
    >  Vous pouvez acheminer des messages XML 2.X et 2. sur n’importe quelle carte ; Toutefois, vous serez généralement transport V2. X via un adaptateur MLLP et que vous feraient généralement transport des messages de 2. des messages XML via un adaptateur HTTP.  
  
2.  Le message est routé via le pipeline de réception pour l’analyse par le désassembleur et la validation.  
  
    1.  Si le message entrant est un message HL7, le désassembleur de fichier plat (DASM) le désassemble en XML. Si le message entrant est un message XML, le XML DASM désassemble il.  
  
    2.  Si le message entrant est un lot de messages, le désassembleur désassemble dans les messages individuels. (Pour plus d’informations, consultez [Message de traitement par lot](../../adapters-and-accelerators/accelerator-hl7/batch-message-processing.md) et [le traitement par lot des messages](../../adapters-and-accelerators/accelerator-hl7/message-batching.md).)  
  
    3.  Le DASM puis valide le message.  
  
    4.  Si vous utilisez un texte bidirectionnel, l’adaptateur de réception MLLP et si le message a été validé par le désassembleur [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] envoie un accusé de réception (ACK) à l’expéditeur d’origine du message via le même adaptateur qui a reçu le message d’origine. Si ce n’est pas le cas, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] envoie un accusé de réception négatif (NAK). (Comment est effectuée cette étape dépend de la configuration de l’accusé de réception. Pour plus d’informations, consultez [Modes d’accusé de réception du Message](../../adapters-and-accelerators/accelerator-hl7/ack-message-modes.md).)  
  
    5.  Si vous n’utilisez pas bidirectionnel MLLP de réception, puis [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] génère un accusé de réception ou les accusés de réception (ou NAK ou NAKs) et le dépose dans la base de données MessageBox. [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]puis l’achemine vers les parties appropriées en fonction de la configuration de port d’envoi, qui utilise une des autres cartes (outre MLLP).  
  
     Pour une liste plus complète des processus effectuée dans le fichier plat et des désassembleurs XML, consultez [BizTalk Accelerator pour HL7 composants](../../adapters-and-accelerators/accelerator-hl7/biztalk-accelerator-for-hl7-components.md).  
  
3.  Une fois que le message passe par l’adaptateur et le pipeline de réception, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] transmet le message dans la base de données MessageBox. [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]Ensuite, détermine où envoyer le message suivant. Si le message fait partie d’une orchestration, il envoie le message au moteur d’Orchestration.  
  
4.  Le moteur d’Orchestration traite le message.  
  
    1.  Si un mappage affecte le message, le mappage transforme le message en fonction de ses règles.  
  
    2.  Si vous avez configuré une règle d’entreprise, [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] appelle le moteur de règles d’entreprise (BRE) en dehors des pipelines, éventuellement dans le moteur d’Orchestration.  
  
    3.  Le moteur d’Orchestration envoie le message à la base de données MessageBox, puis poursuit le traitement de l’orchestration.  
  
5.  En fonction de l’abonnement, [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] achemine le message vers le port d’envoi.  
  
6.  [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]achemine le message via le pipeline d’envoi pour le traitement suivant (le cas échéant) : assembly et la validation.  
  
    1.  Si le message sera un HL7 2.X message, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] assemble le message à partir de XML dans HL7 par l’assembleur de fichier plat (ASM). Si le message entrant est un message XML, le XML DASM assemble.  
  
    2.  Si le message doit faire partie d’un lot de messages, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] assemble chaque message dans le message du lot. (Pour plus d’informations, consultez [Message de traitement par lot](../../adapters-and-accelerators/accelerator-hl7/batch-message-processing.md) et [le traitement par lot des messages](../../adapters-and-accelerators/accelerator-hl7/message-batching.md).)  
  
    3.  Le module ASM valide le message (si activé dans les paramètres de configuration de la partie de l’envoi).  
  
     Pour une liste plus complète des processus effectuée dans le fichier plat et les assembleurs XML, consultez [BizTalk Accelerator pour HL7 composants](../../adapters-and-accelerators/accelerator-hl7/biztalk-accelerator-for-hl7-components.md).  
  
7.  [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]envoie le message via un adaptateur.  
  
    > [!NOTE]
    >  Vous pouvez transporter les messages 2.X et des messages XML 2. sur un nombre de cartes ; Toutefois, la plupart des systèmes de transport 2.X via un adaptateur MLLP 2 XML des messages et via un adaptateur HTTP.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment BTAHL7 route les messages](../../adapters-and-accelerators/accelerator-hl7/how-btahl7-routes-messages.md)