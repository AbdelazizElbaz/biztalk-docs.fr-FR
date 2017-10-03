---
title: "Message de flux dans le répondeur BTARN | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BizTalk Accelerator for RosettaNet, message flow
- BTARN, components
- messages, message flow
- responder BTARN
ms.assetid: 66de8694-a248-47e8-9483-9eedf2324b33
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f3ad33db4f67336f41ac868a7a14e1266a85dd45
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="message-flow-in-the-responder-btarn"></a>Flux de messages de répondeur BTARN
Flux de messages sur un ordinateur de répondeur démarre avec la réception d’un message via Internet à partir de l’ordinateur de l’initiateur. Elle implique la conversion de ce message à partir d’un Framework RNIF (RosettaNet Implementation)-message conforme à un message dans le format propriétaire de l’application principale et puis d’acheminer le message à l’application line-of-business.  
  
 Si le processus PIP (Partner Interface) est l’action unique, la réponse uniquement est un message de signal d’accusé de réception. Si l’adresse PIP est de double action, le répondeur doit traiter et envoyer un message de réponse et par la suite de recevoir un accusé de réception pour cette réponse.  
  
 Si l’adresse PIP est asynchrone, chaque transmission de messages sur Internet se produit sur une autre connexion HTTP. Si l’adresse PIP est synchrone, chaque transmission de message se produit sur la même connexion, qui contient de l’adaptateur HTTP jusqu'à ce que le processus est terminé. Dans un scénario synchrone double action, l’ordinateur récepteur n’envoie pas d’accusé de réception à l’ordinateur initiateur en réponse au message de demande initiale. Le message de réponse sert d'accusé de réception.  
  
## <a name="btarn-components-on-the-responder-computer"></a>Composants BTARN sur l’ordinateur de répondeur  
 Comme un message transite par [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] sur l’ordinateur de répondeur, les composants suivants traitent le message :  
  
-   Page de RNIFReceive.aspx  
  
-   adaptateur HTTP  
  
-   Pipeline de réception  
  
-   Processus public de répondeur  
  
-   Processus privés répondeur  
  
-   Adaptateur SQL  
  
-   Pipeline d’envoi  
  
 Pour plus d’informations sur ces composants, et comment ils traitent un message, consultez [de traitement du Message dans BTARN](../../adapters-and-accelerators/accelerator-rosettanet/message-processing-in-btarn.md).  
  
## <a name="message-flow-on-the-responder-computer"></a>Flux de messages sur l’ordinateur de répondeur  
 Le flux de messages d’un message reçu via le répondeur [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] ordinateur est comme suit :  
  
 ![](../../adapters-and-accelerators/accelerator-rosettanet/media/rn3-responder-receive-message-flow.gif "RN3_Responder_Receive_Message_Flow")  
  
1.  La page aspx RNIFReceive reçoit le message entrant à partir de l’initiateur.  
  
2.  [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]envoie le message à l’adaptateur HTTP qui soumet au pipeline de réception.  
  
3.  Le pipeline de réception décode, désassemble, effectue la résolution du tiers dans le message et convertit ensuite le message au format propriétaire de l’application de line-of-business back-end.  
  
4.  [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]achemine le message vers la base de données MessageBox.  
  
5.  Le processus public traite les en-têtes RNIF du message.  
  
6.  Le processus privé traite le contenu du message du service. Il génère un accusé de réception qui est retourné pour le processus public, à la base de données MessageBox, au pipeline d’envoi, puis à l’adaptateur HTTP pour un retour sur Internet à l’initiateur.  
  
7.  [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]achemine le message vers la base de données MessageBox.  
  
8.  Le pipeline d’envoi assemble et puis signes/chiffre/encode le message.  
  
9. [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]achemine le message vers l’adaptateur SQL.  
  
10. [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]envoie le message à [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)]et à l’application métier-sur le serveur principal.  
  
## <a name="see-also"></a>Voir aussi  
 [Flux de messages de BTARN](../../adapters-and-accelerators/accelerator-rosettanet/message-flow-in-btarn.md)   
 [Flux de messages de l’initiateur BTARN](../../adapters-and-accelerators/accelerator-rosettanet/message-flow-in-the-initiator-btarn.md)