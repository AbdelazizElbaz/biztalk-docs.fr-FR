---
title: Les processus Public initiateur | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- public processes, initiator
- CIDX, 0A1 messages
- messages, 0A1 messages
- messages, message flow
- messages, public processes
- 0A1 messages
- public processes, message flow
ms.assetid: 371d0792-d346-405b-a8f4-2dfa64dd1566
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: df1565915d36f3036543ff69c5da680d5949dc74
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="initiator-public-process"></a>Processus Public d’initiateur
Ce processus lance Framework RNIF (RosettaNet Implementation) sur le système de l’initiateur de messagerie en créant et en envoyant le message d’entreprise RNIF initial.  
  
## <a name="message-flow-in-the-initiator-public-process"></a>Flux de messages dans le processus Public initiateur  
 Le flux de messages via le processus public initiateur est comme suit :  
  
1.  Le processus public initiateur reçoit le contenu du service et les pièces jointes à partir du processus privé via le port de service-content.  
  
2.  Le processus public envoie la réponse au processus privé et n’est aucun traitement supplémentaire.  
  
3.  Si le processus public reçoit une notification qui [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] n’a pas été envoyer le message, le processus public envoie cet état au processus privé de l’initiateur, puis se termine.  
  
4.  Si le processus public reçoit une notification qui [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] a bien envoyé le message, le processus passe à un état d’attente (en attente pour l’action par le répondeur).  
  
5.  Les actions suivantes peuvent se terminer à l’état d’attente :  
  
    1.  Le processus public reçoit un signal d’accusé de réception de répondeur.  
  
         Si la non-répudiation pour le signal est requis (tel que défini dans les paramètres de configuration de processus), le processus lit le digest, met en corrélation le condensat du signal avec le résumé dans le message d’action d’origine, puis le signal.  
  
         Le processus public envoie les en-têtes et le contenu du service du signal au processus privé.  
  
    2.  Le processus public reçoit un message de réponse de l’action de double de répondeur.  
  
         Le processus extrait le contenu de service et les en-têtes de message de réponse et les envoie au processus privé.  
  
         Si l’activité est synchrone, le processus construit un message de signal RNIF en encapsulant la partie du message de contenu de service avec le préambule, en-tête de service et en-tête de remise (pour RNIF 2.01). Le processus crée le préambule et les en-têtes à l’aide des informations de configuration sur les parties de la source et de destination et les variables PIP stockées dans l’accord de partenariat commercial entre les parties. Le processus envoie ensuite le message de signal au répondeur.  
  
         Si l’activité est asynchrone, le processus se termine.  
  
    3.  Le processus public reçoit un message de Notification d’échec (n) de répondeur. Le processus public envoie un message d’état correspondant au processus privé initiateur. Ensuite, le processus privé gère l’erreur et met fin à la fois aux processus.  
  
    4.  Le processus public ne reçoit pas une alerte signalant un accusé de réception du récepteur dans le temps à la période d’accusé de réception (tel que défini dans les paramètres de configuration de processus). Dans ce cas, une des opérations suivantes se produit :  
  
         Si le nombre de tentatives (tel que défini dans les paramètres de configuration de processus) n’a pas atteint zéro, et que l’activité est asynchrone, le processus public envoie à nouveau le message.  
  
         Si le nombre de tentatives (tel que défini dans les paramètres de configuration de processus) n’a pas atteint zéro, et que l’activité est synchrone, le processus public envoie un message de 0 a 1.  
  
        > [!NOTE]
        >  CIDX ne prend pas en charge les messages de 0 a 1.  
  
         Si le nombre de tentatives atteint zéro sans un envoi réussi, le processus public publie un message d’erreur, et si ce n’est pas CIDX, le processus public envoie un message de 0 a 1.  
  
         Si l’activité est synchrone, et ce n’est pas CIDX, le processus public envoie un message de 0 a 1.  
  
    5.  Si aucune action se produit dans le temps à la période d’exécution, et ce n’est pas CIDX, le processus public envoie un message de 0 a 1.  
  
## <a name="see-also"></a>Voir aussi  
 [Processus publics](../../adapters-and-accelerators/accelerator-rosettanet/public-processes.md)   
 [Processus Public de répondeur](../../adapters-and-accelerators/accelerator-rosettanet/responder-public-process.md)