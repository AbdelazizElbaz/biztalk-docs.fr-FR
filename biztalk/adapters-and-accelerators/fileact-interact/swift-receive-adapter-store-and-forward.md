---
title: "Magasin de l’adaptateur et le transfert de réception SWIFT | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 11eeb335-366b-4b29-9078-de9396b258ca
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 315b9bbe6985bbce5ccb44d8d4846b18730f292b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="swift-receive-adapter-store-and-forward"></a>Magasin de l’adaptateur et le transfert de réception SWIFT
L’adaptateur de réception reçoit des messages à partir du magasin SWIFT et la file d’attente de transfert (msng). Pour recevoir des messages à partir de la file d’attente, l’adaptateur doit ouvrir une session avec la file d’attente MSNG. Pour ouvrir la file d’attente, il doit avoir un processus client dédié qui établit la session avec la file d’attente. Dans la conception, ce processus est implémenté comme un COM + d’un composant d’out-of-Process.  
  
## <a name="push-session-store-and-forward-sequence"></a>Push de magasin de session et la séquence de transfert  
 La liste suivante décrit le magasin et la séquence de transfert.  
  
1.  Démarrer l’application serveur qui traite les messages.  
  
2.  Le processus serveur ouvre les contextes de sécurité requis lors de la première SwCallback avec la Sw:HandleInitRequest comme une primitive d’entrée.  
  
3.  Le serveur répond à la Sw:HandleInitRequest avec un ou les deux Sw:CryptoMode et Sw:FACryptoMode définie sur Avancé.  
  
     Le serveur est maintenant prêt à commencer le traitement des demandes entrantes.  
  
4.  Pour démarrer la remise de messages à partir d’une file d’attente, un processus client démarre une session de push. Selon la configuration de l’adaptateur (mode par envoi), l’adaptateur de réception génère un processus client appelé SnFQueueManager.exe pour acquérir la file d’attente en mode push.  
  
5.  Un SwCall() s’exécute avec Sw:AcquireSnFRequest (dans le Sw:ExchangeSnFRequest) comme une primitive d’entrée. Cette demande démarre une session avec la file d’attente indiqué (si le SwSec:AuthorisationContext a le rôle RBAC requis).  
  
6.  Immédiatement après la réponse avec « Accepté » dans le Sw:AcquireStatus, SWIFTNet SnF commence à envoyer des messages sur le serveur comme indiqué dans l’acquisition. Si l’adaptateur de réception n’a pas encore démarré, messages Obtient des exceptions. (C’est pourquoi il est important que les adaptateurs de réception déjà démarrés).  
  
7.  SWIFTNet SnF démarre en exécutant un push d’un nombre de messages (jusqu'à la taille de fenêtre).  
  
8.  Pour chaque message d’accusé de réception, un nouveau message (le cas échéant) est envoyé.  
  
9. Le processus du client (SnFQueueManager.exe) a fait son travail et peut se terminer maintenant. Le processus émet SwSec:DestroyContextRequest, qui nettoie les contextes de sécurité. Après le Sw:TermRequest, le processus s’arrête.  
  
### <a name="message-correlation"></a>Corrélation de messages  
 Le champ RequestRef est conservé et remplacé dans les messages de réponse par l’adaptateur de réception. Cela garantit la corrélation de bout en bout entre le message entrant et le message de réponse  
  
### <a name="duplicate-processing"></a>Traitement dupliqué  
 Si la réception d’une demande de FileAct et de l’instance de l’adaptateur reçoit un message avec un nœud de l’indicateur Possible de dupliquer, il doit vérifier si le transfert référencé est déjà terminée correctement ou si elle a échoué et prenez les mesures appropriées. Si le transfert de fichiers a déjà eu lieu, puis l’adaptateur met à jour le statut du transfert en tant que « Duplicate » dans le cas contraire elle met à jour en tant que « Accepté ».  
  
### <a name="acknowledgments"></a>Accusés de réception  
 Si l’expéditeur demande un accusé de réception d’une demande de FileAct, l’adaptateur vérifie pour l’événement de fin de transfert de fichier et génère l’accusé de réception après avoir vérifié la valeur digest du fichier. L’adaptateur envoie le message d’accusé de réception à BizTalk pour l’adaptateur d’envoi pour le choisir et l’envoyer à l’expéditeur.  
  
## <a name="see-also"></a>Voir aussi  
 [Architecture de l’adaptateur de réception SWIFT](../../adapters-and-accelerators/fileact-interact/swift-receive-adapter-architecture.md)   
 [URI d’adaptateur de réception SWIFT](../../adapters-and-accelerators/fileact-interact/swift-receive-adapter-uri.md)   
 [Initialisation de l’adaptateur de réception SWIFT](../../adapters-and-accelerators/fileact-interact/swift-receive-adapter-initialization.md)   
 [Contexte de sécurité de l’adaptateur de réception SWIFT](../../adapters-and-accelerators/fileact-interact/swift-receive-adapter-security-context.md)   
 [Les Modes synchrone et différé de l’adaptateur de réception SWIFT](../../adapters-and-accelerators/fileact-interact/swift-receive-adapter-synchronous-and-deferred-modes.md)