---
title: "Scénario 3 : Dimensionnement de la base de données de suivi pour les Messages envoyés hors aux listes de Distribution | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Tracking database, database size
ms.assetid: bc6e0da0-46d1-42d6-8ec9-29a28719fbb3
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dca1722e24e0c76c85699ea00fcf6ffc120b2e14
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="scenario-3-sizing-the-tracking-database--for-messages-sent-out-to-distribution-lists"></a>Scénario 3 : Dimensionnement de la base de données de suivi des Messages envoyés aux listes de Distribution
Dans le schéma suivant, un message passe par un processus d'orchestration pour être modifié au sein de l'orchestration avant d'être envoyé vers différents ports d'envoi par le biais d'une liste de distribution.  
  
 ![Message à travers une orchestration à plusieurs ports](../core/media/biztalk-server-message-orch-multiple-ports.gif "BizTalk_Server_message_orch_multiple_ports")  
  
 **Message de BizTalk Server qui se déroule à travers une orchestration est envoyé vers différents ports**  
  
 Voici quelques données relatives au présent scénario :  
  
-   Taille du message de 10 Ko.  
  
-   aucune propriété à promouvoir ;  
  
-   nombre de messages reçus dans une année : 3,5 millions ;  
  
-   suivi activé pour tous les événements, ici au nombre de cinq :  
  
    -   Réception du message M0  
  
    -   Sortie du message M1 provenant du port de réception  
  
    -   Sortie du message M3 par le port d'envoi  
  
    -   Sortie du message M4 par le port d'envoi  
  
    -   Sortie du message M5 par le port d'envoi  
  
 Application de ces informations à l’équation donne les éléments suivants :  
  
```  
[(5*252 bytes) + (10*182 bytes) + (0*5(40 bytes + 0) * 3,500,000]/1024/1024  
[(1620 + 1820 + 0) * 3,500,000]/1024/1024 = 10280.61 MB ~ 10.04 GB per year  
```  
  
## <a name="messages-in-an-orchestration-that-are-sent-out-to-a-distribution-list-with-a-single-promoted-property"></a>Messages passant par un processus d'orchestration et envoyés vers une liste de distribution dont une seule propriété est promue  
 Dans cet exemple, une seule propriété d'environ 10 octets est promue, comme dans un précédent exemple. L'équation est alors la suivante :  
  
```  
[((5*150 bytes) + (10*230 bytes) + (1*5(52 bytes + 10 bytes)) * 3,500,000]/1024/1024  
[(750 + 2300 + 260) * 3,500,000]/1024/1024 = 11048 MB ~ 10.79 GB per year  
```  
  
 Si vous souhaitez promouvoir une autre propriété de 20 octets, l'équation prend la forme suivante :  
  
```  
[((5*150 bytes) + (10*230 bytes) + ((1*5(52 bytes + 10 bytes) + (1*5(52 bytes + 20 bytes)) * 3,500,000]/1024/1024  
[(750 + 2300 + 670) * 3,500,000]/1024/1024 = 12417 MB ~ 12.13 GB per year  
```  
  
## <a name="messages-in-an-orchestration-that-are-sent-out-to-a-distribution-list-with-message-body-tracking-activated"></a>Messages passant par un processus d'orchestration, envoyés vers une liste de distribution et pour lesquels le suivi du corps des messages est activé  
 Si, dans cet exemple, le suivi de message est pris en compte, l'équation se présente comme suit :  
  
```  
[3,500,000 * 6 * 5KB]/1024 = 102539.06 MB ~ 100.14 GB per year  
  
```  
  
## <a name="see-also"></a>Voir aussi  
 [À l’aide de Variables de Message à la taille de la base de données de suivi](../core/using-message-variables-to-size-the-tracking-database.md)   
 [Dimensionnement de la base de données de suivi pour suivre les corps de Message](../core/sizing-the-tracking-database-to-track-message-bodies.md)   
 [Scénario 1 : Dimensionnement de la base de données de suivi pour les Messages BizTalk simples](../core/scenario-1-sizing-the-tracking-database-for-simple-biztalk-messages.md)   
 [Scénario 2 : Dimensionnement de la base de données de suivi pour les Messages dans les Orchestrations](../core/scenario-2-sizing-the-tracking-database-for-messages-in-orchestrations.md)   
 [Scénario 4 : Redimensionnement de la base de données de suivi pour tous les Messages](../core/scenario-4-sizing-the-tracking-database-for-all-messages.md)