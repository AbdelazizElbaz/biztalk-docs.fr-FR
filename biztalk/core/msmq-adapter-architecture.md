---
title: "Architecture de l’adaptateur MSMQ | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- architecture, MSMQ adapters
- MSMQ adapters, architecture
ms.assetid: acecc2a4-0670-487e-be39-28a24c8c3f16
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bd314b6f835568b6336121478268b84381a288ff
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="msmq-adapter-architecture"></a>Architecture de l’adaptateur MSMQ
L'adaptateur MSMQ vous permet de tirer parti des fonctionnalités du service Microsoft Message Queuing (également appelé MSMQ), normalement indisponibles dans BizTalk Server.  
  
## <a name="adapter-structure"></a>Structure de l'adaptateur  
 L'adaptateur MSMQ présente la même structure que d'autres adaptateurs BizTalk et utilise l'Infrastructure d'adaptateurs. Il est constitué d'un composant de conception et d'un composant d'exécution. Le composant d'exécution, à son tour, contient les éléments qui implémentent le transport de messages.  
  
 Le composant de conception permet de configurer les propriétés de l'adaptateur pour l'envoi et la réception.  
  
 Le composant d'exécution peut envoyer des messages à une file d'attente définie au moment de la conception ou recevoir des messages d'une file d'attente désignée. L'exécution de l'adaptateur a lieu dans le même processus que celle de l'application BizTalk Server et n'est pas effectuée sur un hôte isolé.  
  
 Tout le traitement des messages dépend du service Message Queuing local, même pour les files d'attente distantes. Pour les files d'attente distantes, l'adaptateur transmet les messages au service Message Queuing local. À son tour, ce dernier envoie les messages à la file d'attente distante.  
  
 Pour obtenir une liste complète de l’envoi et réception des propriétés de configuration, consultez [comment configurer un Port d’envoi MSMQ](../core/how-to-configure-an-msmq-send-port.md) et [comment configurer un emplacement de réception MSMQ](../core/how-to-configure-an-msmq-receive-location.md).  
  
 Pour plus d'informations sur le service Message Queuing, consultez les rubriques suivantes de la bibliothèque TechNet de Microsoft.  
  
-   **Guide de conception de files d’attente de messages** à [http://go.microsoft.com/fwlink/?LinkId=137080](http://go.microsoft.com/fwlink/?LinkId=137080).  
  
-   **Guide des opérations files d’attente de messages** à [http://go.microsoft.com/fwlink/?LinkId=137079](http://go.microsoft.com/fwlink/?LinkId=137079).  
  
-   **Guide de dépannage de Message Queuing** à [http://go.microsoft.com/fwlink/?LinkId=137081](http://go.microsoft.com/fwlink/?LinkId=137081).  
  
-   **Message Queuing Technical Reference** à [http://go.microsoft.com/fwlink/?LinkId=137082](http://go.microsoft.com/fwlink/?LinkId=137082).  
  
## <a name="see-also"></a>Voir aussi  
 [Nouveautés de l’adaptateur MSMQ ?](../core/what-is-the-msmq-adapter.md)