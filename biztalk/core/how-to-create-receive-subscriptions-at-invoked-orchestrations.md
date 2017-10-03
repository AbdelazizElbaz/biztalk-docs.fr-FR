---
title: "Comment créer des Orchestrations appelées abonnements de réception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3423309a-cb5a-40a5-9582-6ee3ac82b538
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c419101aa16c23f5fd8a644c0fe33f269d06d6ba
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-create-receive-subscriptions-at-invoked-orchestrations"></a>Création d'abonnements de réception pour les orchestrations appelées
Bien que vous pouvez transmettre des messages en tant que paramètres via la **démarrer Orchestration** forme lorsque vous démarrez une orchestration, dans certains scénarios que vous pouvez envoyer des messages à partir de l’orchestration de l’appelant à l’orchestration appelée après le appel. C'est par exemple le cas si vous ne savez pas, au moment de l'appel, quels messages transmettre, ou si d'autres orchestrations ont besoin d'envoyer des messages de manière dynamique à l'orchestration appelée.  
  
 Pour envoyer un message à une orchestration appelée, il faut transmettre une corrélation qui permettra à l'orchestration appelée de créer l'abonnement par le biais duquel recevoir le message. Toutefois, se contenter de transmettre la corrélation ne suffit pas. Si vous procédez de cette manière, les messages que vous avez envoyés de l'orchestration de l'appelant à l'orchestration appelée généreront l'erreur « Impossible d'acheminer le message publié, car aucun abonné n'a été trouvé ». Il s’agit en raison de la manière suivante :  
  
-   L'orchestration appelée présente une condition d'engorgement.  
  
-   Il n'existe aucun point de validation qui puisse permettre à l'orchestration appelée d'envoyer l'abonnement à la base de données MessageBox pour le routage et recevoir les messages.  
  
 Vous pouvez résoudre ce problème de la manière suivante :  
  
1.  Dans l'orchestration de l'appelant, vous disposez d'une réception avec activation pour recevoir le message. Une fois que vous recevez le message dans l’orchestration de l’appelant, initialisez l’ensemble de corrélations, puis passez l’ensemble de corrélations et une réception auto-corrélation à liaison directe via la **démarrer Orchestration** forme. Le port ainsi transmis devient un port d'envoi dans l'orchestration appelée, grâce auquel le message pourra être renvoyé pour permettre la synchronisation avec l'orchestration de l'appelant.  
  
2.  Dans l'orchestration appelée, renvoyez un message à l'orchestration de l'appelant par le biais du port d'auto-corrélation. Cette opération effectue une synchronisation avec l'orchestration de l'appelant, laquelle permet d'éviter les risques d'engorgement et permet de fournir un point de validation lors de la création de l'abonnement de réception dans la base de données MessageBox pour le routage dans l'orchestration appelée.  
  
3.  L'orchestration de l'appelant reçoit le message via le port d'auto-corrélation et se synchronise avec l'orchestration appelée. Notez que les réceptions du port d'auto-corrélation ne requièrent pas de suivis. Vous pouvez désormais envoyer en toute sécurité des messages entre l'orchestration de l'appelant et l'orchestration appelée, et cette dernière recevra les messages basés sur la corrélation.  
  
 Bien que la méthode précitée soit efficace, il existe une meilleure méthode. Elle consiste à transmettre le message qui initialise la corrélation sur laquelle se baser. Lors de la synchronisation des orchestrations de l'appelant et appelée via un port d'auto-corrélation, il est recommandé de toujours transmettre le message permettant d'initialiser les corrélations. La procédure suivante constitue la méthode la plus fiable et la plus performante :  
  
1.  Dans l'orchestration de l'appelant, vous disposez d'une réception avec activation pour recevoir le message. Après avoir reçu le message, transmettez un message et une réception auto-corrélation à liaison directe via la **démarrer Orchestration** forme. Le message transmis servira à initialiser la corrélation dans l'orchestration appelée. Le port ainsi transmis devient un port d'envoi dans l'orchestration appelée, grâce auquel le message pourra être renvoyé pour permettre la synchronisation avec l'orchestration de l'appelant.  
  
2.  Dans l'orchestration appelée, initialisez la corrélation et renvoyez un message à l'orchestration de l'appelant. Cette opération effectue une synchronisation avec l'orchestration de l'appelant, laquelle permet d'éviter les risques d'engorgement et permet de fournir un point de validation lors de la création de l'abonnement de réception dans la base de données MessageBox pour le routage dans l'orchestration appelée.  
  
3.  L'orchestration de l'appelant reçoit le message via le port d'auto-corrélation et se synchronise avec l'orchestration appelée. Notez que le port d’autocorrélation reçoit n’avez pas besoin de suivis. Vous pouvez désormais envoyer en toute sécurité des messages entre l'orchestration de l'appelant et l'orchestration appelée, et cette dernière recevra les messages basés sur la corrélation.  
  
## <a name="see-also"></a>Voir aussi  
 [À l’aide de corrélations dans les Orchestrations](../core/using-correlations-in-orchestrations.md)   
 [Ports de liaison de l’utilisation directe d’autocorrélation](../core/how-to-use-self-correlating-direct-bound-ports.md)