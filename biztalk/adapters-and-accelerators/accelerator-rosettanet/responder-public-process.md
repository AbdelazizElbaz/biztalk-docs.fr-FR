---
title: "Processus Public de répondeur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- messages, message flow
- messages, public processes
- public processes, message flow
- public processes, responder
ms.assetid: 78d83954-2998-44ac-a527-5e5858c61009
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c89c246bca80fdb648df909cd4f01fca4e2691dc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="responder-public-process"></a>Processus Public de répondeur
Ce processus public sur le répondeur reçoit le message de Framework RNIF (RosettaNet Implementation) de l’initiateur et réagit en conséquence.  
  
## <a name="message-flow-in-the-responder-public-process"></a>Flux de messages dans le processus Public répondeur  
 Le flux de messages via le processus public du répondeur est comme suit :  
  
1.  Le processus public répondeur reçoit le message RNIF à partir de la base de données MessageBox de répondeur.  
  
2.  Le processus public extrait le contenu du service et les en-têtes du message d’action et les envoie au processus privé.  
  
    > [!NOTE]
    >  Le processus public répondeur effectue une validation standard sur le message entrant (et toute validation supplémentaire inclus dans une carte de la validation, le cas échéant). Si la validation est réussie, le processus public initie l’adaptateur d’application pour effectuer la notification conformément à l’implémentation spécifique. Le processus public répondeur enregistre le message dans la base de données MessageBox et informe le processus privé répondeur qu’il a enregistré le message dans la MessageBox (à l’aide de la `BeginNotify` méthode dans la `ApplicationAdapter` classe). Pour plus d’informations sur l’adaptateur de validation et d’un adaptateur d’application, consultez [ValidationAdapter &#91; RN3 &#93; ](../../adapters-and-accelerators/accelerator-rosettanet/validationadapter.md) et [ApplicationAdapter &#91; RN3 &#93; ](../../adapters-and-accelerators/accelerator-rosettanet/applicationadapter.md).  
  
3.  Si l’activité est asynchrone et action unique, le processus public construit un message de signal RNIF (acceptation de l’accusé de réception) en encapsulant la partie du message de contenu de service avec le préambule, l’en-tête de service et (pour RNIF 2.01) l’en-tête de remise. Le processus public construit le préambule, l’en-tête de service et l’en-tête de remise à l’aide des informations stockées dans l’accord de partenariat commercial entre les parties : les paramètres de configuration de processus, les informations de configuration sur la source et tiers de destination et les variables de processus PIP (Partner Interface). Le processus envoie ensuite le message de signal à l’initiateur.  
  
    > [!NOTE]
    >  Si le message est un message d’action unique, le flux de messages est terminé.  
  
4.  Le processus public entre un état d’attente (en attente d’action par le processus privé répondeur).  
  
5.  Les actions suivantes peuvent se terminer à l’état d’attente (en attente d’action par le processus privé répondeur) :  
  
    1.  Le processus privé répondeur renvoie un message de contenu du service de réponse et les en-têtes, en réponse au message d’action d’origine (qui était un message à double action).  
  
         Si le processus public reçoit le contenu de la réponse du processus privé, le processus public construit un message RNIF qui contient le contenu de service. Il le fait en encapsulant la partie du message de contenu de service avec les en-têtes qui contiennent les informations de configuration sur les parties de la source et de destination et les variables PIP stockées dans l’accord entre les parties.  
  
         Le processus public envoie le message RNIF à l’initiateur utilise le port de lien de rôle de l’Action/Signal.  
  
         Si le processus public reçoit une notification qui [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] n’a pas été envoyer le message, le processus public envoie cet état au processus privé, puis se termine.  
  
         Si le processus public reçoit une notification qui [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] a bien envoyé le message, le processus passe à un état d’attente (en attente d’action par l’initiateur). Cet état d’attente est similaire à l’état d’attente que l’initiateur entre lorsqu’il est en attente pour l’action par le répondeur.  
  
    2.  Le processus public reçoit un message de Notification d’échec (n) à partir de l’initiateur.  
  
    > [!NOTE]
    >  Le processus privé répondeur informera le processus public répondeur après avoir correctement traité le message entrant. Uniquement après le répondeur public processus a reçu cette notification (à partir de la `EndNotify` méthode dans la `ApplicationAdapter` classe) est le processus public répondeur être terminé.  
  
6.  Le processus public répondeur passe à un état d’attente (en attente pour recevoir un signal de l’initiateur en réponse au message de réponse envoyé par le processus public répondeur).  
  
## <a name="see-also"></a>Voir aussi  
 [Processus publics](../../adapters-and-accelerators/accelerator-rosettanet/public-processes.md)   
 [Processus Public d’initiateur](../../adapters-and-accelerators/accelerator-rosettanet/initiator-public-process.md)   
 [ApplicationAdapter](../../adapters-and-accelerators/accelerator-rosettanet/applicationadapter.md)   
 [ValidationAdapter](../../adapters-and-accelerators/accelerator-rosettanet/validationadapter.md)