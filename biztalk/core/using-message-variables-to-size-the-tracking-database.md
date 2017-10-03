---
title: "À l’aide de Variables de Message à la taille de la base de données de suivi | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- message variables [Tracking database], CMsgs
- message variables [Tracking database], Events
- message variables [Tracking database], Properties
- Tracking database, database size
- message variables [Tracking database], Nserv
- message variables [Tracking database], Msgs
- message variables [Tracking database], PropSize
- message variables [Tracking database]
- message variables [Tracking database], MsgSize
- message variables [Tracking database], MsgNum
- Tracking database, messages
ms.assetid: 2d31ae25-3d16-4002-b5a5-dca25e764ecd
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5418cdf79499302e6127db7fb66f108825a0d8c0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="using-message-variables-to-size-the-tracking-database"></a>Utilisation de variables de message pour déterminer la taille de la base de données des suivis
Dans Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], un certain nombre de variables permettent de déterminer la taille que la base de données des suivis BizTalk (BizTalkDTADb) est susceptible d'atteindre au bout d'une période donnée. Ces variables sont les suivantes :  
  
-   nombre de pipelines utilisés ;  
  
-   nombre d'orchestrations concernées ;  
  
-   nombre d'événements générés ;  
  
-   Nombre de propriétés de message soumises à un suivi  
  
-   nombre de messages créés ;  
  
-   estimation du nombre de messages reçus dans le laps de temps spécifié.  
  
 Bien que l'équation à utiliser afin d'obtenir une estimation de la taille de la base de données des suivis soit simple, vous devez l'appliquer à chaque processus de messagerie entrant et sortant qui utilise l'implémentation BizTalk Server. En d'autres termes, vous devez appliquer cette équation à chacun des différents scénarios de message et ajouter les résultats obtenus pour arriver à une estimation de la taille finale de la base de données. Dans le cas présent, nous examinerons deux scénarios. Il s'agit des scénarios suivants :  
  
1.  Réception et transformation d'un message, puis envoi du message ainsi obtenu  
  
2.  Réception d'un message, application d'un processus d'entreprise, puis envoi du message ainsi obtenu  
  
 Ces deux types de scénarios peuvent se présenter dans un environnement BizTalk Server et chacun d'entre eux génère une quantité différente de données de suivi. La quantité totale de données de suivi générée par l'installation de BizTalk Server est égale à la somme de tous les scénarios.  
  
 Voici quelques-unes des variables utilisées pour l'équation :  
  
|Variable| Description|  
|--------------|-----------------|  
|**Nserv**|Nombre de services (nombre de pipelines + nombre d'orchestrations)|  
|**Événements**|Nombre d'événements de message générés|  
|**Propriétés**|Nombre de propriétés de message soumises à un suivi|  
|**PropSize**|Taille en octets de la propriété promue (champ)|  
|**CMsgs**|Nombre de messages créés par message entrant|  
|**Empilés**|Estimation du nombre de messages entrants dans un laps de temps donné|  
|**MsgSize**|Taille du message|  
|**MsgNum**|Nombre de messages suivis pour chaque message entrant|  
  
 L'équation est la suivante :  
  
```  
[((Nserv * 150 bytes) + (Events * 230 bytes) + (Properties * CMsgs*(52 bytes + PropSize))) * Msgs]/1024/1024 = Data size in MB  
```  
  
 Cette équation permet de calculer uniquement les données de suivi générées par les messages mais ne prend pas en compte les données de suivi générées pour le débogueur d'orchestration. Vous devez appliquer cette formule à chaque processus de message afin d'estimer la taille de la base de données des suivis.  
  
## <a name="see-also"></a>Voir aussi  
 [Dimensionnement de la base de données de suivi pour suivre les corps de Message](../core/sizing-the-tracking-database-to-track-message-bodies.md)   
 [Scénario 1 : Dimensionnement de la base de données de suivi pour les Messages BizTalk simples](../core/scenario-1-sizing-the-tracking-database-for-simple-biztalk-messages.md)   
 [Scénario 2 : Dimensionnement de la base de données de suivi pour les Messages dans les Orchestrations](../core/scenario-2-sizing-the-tracking-database-for-messages-in-orchestrations.md)   
 [Scénario 4 : Redimensionnement de la base de données de suivi pour tous les Messages](../core/scenario-4-sizing-the-tracking-database-for-all-messages.md)   
 [Scénario 3 : Dimensionnement de la base de données de suivi des Messages envoyés aux listes de Distribution](../core/scenario-3-size-the-tracking-database-for-messages-sent-to-distribution-lists.md)