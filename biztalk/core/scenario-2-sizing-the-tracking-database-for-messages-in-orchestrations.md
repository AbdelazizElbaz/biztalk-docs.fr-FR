---
title: "Scénario 2 : Dimensionnement de la base de données de suivi pour les Messages dans les Orchestrations | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Tracking database, database size
ms.assetid: d1cfb8b9-d4e2-4069-8db3-18f72358652b
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 62ea6e463dfb3a44e2628f57b632634d7a9bd212
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="scenario-2-sizing-the-tracking-database--for-messages-in-orchestrations"></a>Scénario 2 : Dimensionnement de la base de données de suivi pour les Messages dans les Orchestrations
Examinons un exemple comprenant une orchestration. Le schéma suivant représente le processus d'entreprise dans sa totalité. Dans ce scénario, un message entre dans le serveur BizTalk pour passer dans une orchestration avant d'y être modifié, puis il sort par un port d'envoi.  
  
 ![Processus de message BizTalk Server](../core/media/biztalk-server-message-process.gif "BizTalk_Server_Message_Process")  
  
 **Le processus de message BizTalk Server**  
  
 Voici quelques données relatives au présent scénario :  
  
-   taille du message : 5 Ko ;  
  
-   Nous ne sommes pas promouvoir des propriétés.  
  
-   Le nombre de messages que nous avons reçus dans une année : 3,5 millions.  
  
-   suivi activé pour tous les événements, ici au nombre de six :  
  
    -   Réception du message M0  
  
    -   Sortie du message M1 provenant du port de réception  
  
    -   Réception du message M1 par l'orchestration  
  
    -   Sortie du message M2 provenant de l'orchestration  
  
    -   Réception du message M2 par le port d'envoi  
  
    -   Sortie du message M3 par le pipeline d'envoi  
  
-   création de trois messages dans ce scénario : le message M0 étant le message entrant, il n'est pas créé par BizTalk Server. Le message M1 est le message sortant du port de réception, le message M2 est celui généré par l'orchestration et le message M3, celui qui provient du port de transmission.  
  
 L'intégration de ces données à la formule donne le résultat suivant :  
  
```  
[(3*150 bytes) + (6*230 bytes) + (0*0(52 bytes + 0) * 3,500,000]/1024/1024  
[(450 + 1380 + 0) * 3,500,000]/1024/1024 = 6108 MB ~ 5.96 GB per year  
```  
  
## <a name="messages-in-orchestrations-with-a-single-promoted-property"></a>Messages passant par des orchestrations et dont la propriété promue est unique  
 Dans cet exemple, un seul champ est promu, comme dans un exemple précédent. La taille de la propriété promue est d'environ 10 octets. L'équation est alors la suivante :  
  
```  
[((3*150 bytes) + (6*230 bytes) + (1*3*(52 bytes + 10 bytes)) * 3,500,000]/1024/1024  
[(450 + 1380 + 186) * 3,500,000]/1024/1024 = 6729 MB ~ 6.57 GB per year  
```  
  
 Si vous devez promouvoir une autre propriété de 20 octets, la formule se présente comme indiqué ci-dessous :  
  
```  
[(3*150 bytes) + (6*230 bytes) + ((1*3*(52 bytes + 10 bytes) + (1*3*(52 bytes + 20 bytes)) * 3,500,000]/1024/1024  
[(450 + 1380 + 372) * 3,500,000]/1024/1024 = 7350 MB ~ 7.18 GB per year  
```  
  
## <a name="messages-in-orchestrations-with-message-body-tracking-activated"></a>Messages passant par des orchestrations et pour lesquels le suivi du corps des messages est activé  
 Si, dans cet exemple, le suivi de message est pris en compte, le résultat obtenu après avoir calculé l'espace supplémentaire nécessaire est identique à celui obtenu dans le scénario précédent, à savoir 50,1 Go par an.  
  
## <a name="see-also"></a>Voir aussi  
 [À l’aide de Variables de Message à la taille de la base de données de suivi](../core/using-message-variables-to-size-the-tracking-database.md)   
 [Dimensionnement de la base de données de suivi pour suivre les corps de Message](../core/sizing-the-tracking-database-to-track-message-bodies.md)   
 [Scénario 1 : Dimensionnement de la base de données de suivi pour les Messages BizTalk simples](../core/scenario-1-sizing-the-tracking-database-for-simple-biztalk-messages.md)   
 [Scénario 4 : Redimensionnement de la base de données de suivi pour tous les Messages](../core/scenario-4-sizing-the-tracking-database-for-all-messages.md)   
 [Scénario 3 : Dimensionnement de la base de données de suivi des Messages envoyés aux listes de Distribution](../core/scenario-3-size-the-tracking-database-for-messages-sent-to-distribution-lists.md)