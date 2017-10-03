---
title: "Message de flux dans l’initiateur BTARN | Documents Microsoft"
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
- initiator BTARN
ms.assetid: 315f3d4c-5e40-4b8e-b135-9da98dc2db1e
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 85fed6404627fd8abfa9d50e7d56d98ff7306f09
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="message-flow-in-the-initiator-btarn"></a>Flux de messages de l’initiateur BTARN
Flux de messages sur un ordinateur de l’initiateur démarre avec la réception d’un message de l’application métier-terminale, dans son format propriétaire. Elle implique la conversion de ce message pour un Framework RNIF (RosettaNet Implementation)-message compatible, puis envoyer le message via Internet à l’ordinateur de répondeur.  
  
 Si le processus PIP (Partner Interface) est l’action unique, la réponse uniquement est un message de signal d’accusé de réception. Pour plus d’informations sur les flux de messages d’action unique, consultez « Flux d’un initiée par Message » plus loin dans cette rubrique. Si l’adresse PIP est de double action, l’initiateur recevra un message de réponse et répondre avec un accusé de réception, en plus du flux de messages d’action unique.  
  
 Si l’adresse PIP est asynchrone, chaque transmission de messages sur Internet se produit sur une autre connexion HTTP. Si l’adresse PIP est synchrone, chaque transmission de message se produit sur la même connexion, qui contient de l’adaptateur HTTP jusqu'à ce que le processus est terminé. Dans un scénario synchrone double action, l’ordinateur récepteur n’envoie pas d’accusé de réception à l’ordinateur initiateur en réponse au message de demande initiale. Le message de réponse sert d'accusé de réception.  
  
## <a name="btarn-components-on-the-initiator-computer"></a>Composants BTARN sur l’ordinateur de l’initiateur  
 Comme un message transite par [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] sur l’ordinateur de l’initiateur, les composants suivants traitent le message :  
  
-   Adaptateur SQL  
  
-   Pipeline de réception XML  
  
-   Processus privés initiateur  
  
-   Processus public d’initiateur  
  
-   Pipeline d’envoi XML  
  
-   adaptateur HTTP  
  
-   Page du fichier RNIFSend.aspx  
  
 Pour plus d’informations sur ces composants, et comment ils traitent un message, consultez [de traitement du Message dans BTARN](../../adapters-and-accelerators/accelerator-rosettanet/message-processing-in-btarn.md).  
  
## <a name="flow-of-an-initiated-message"></a>Flux d’un Message de déclenchement  
 Les étapes suivantes décrivent le flux de messages d’un message initié par l’initiateur [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] ordinateur. Ce processus est représenté dans la figure suivante.  
  
 ![](../../adapters-and-accelerators/accelerator-rosettanet/media/rn3-initiator-send-message-flow.gif "RN3_Initiator_Send_Message_Flow")  
  
1.  L’application métier-envoie le message à [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)].  
  
2.  [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]envoie le message à partir de la [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] base de données à l’adaptateur SQL.  
  
3.  Le code XML de réception pipeline a simple XML validation du message.  
  
4.  [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]achemine le message vers la base de données MessageBox.  
  
5.  Le processus privé traite le contenu du message du service.  
  
6.  Le processus public traite les en-têtes RNIF du message.  
  
7.  [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]achemine le message à la base de données MessageBox.  
  
8.  Le pipeline d’envoi exécute l’assembly et signature, chiffrement/encodage du message.  
  
9. [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]achemine le message vers l’adaptateur HTTP.  
  
10. [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]achemine le message vers la page du fichier RNIFSend.aspx, qui l’envoie vers sa destination sur Internet.  
  
## <a name="see-also"></a>Voir aussi  
 [Flux de messages de BTARN](../../adapters-and-accelerators/accelerator-rosettanet/message-flow-in-btarn.md)   
 [Flux de messages de répondeur BTARN](../../adapters-and-accelerators/accelerator-rosettanet/message-flow-in-the-responder-btarn.md)   
 [Traitement des messages dans BTARN](../../adapters-and-accelerators/accelerator-rosettanet/message-processing-in-btarn.md)