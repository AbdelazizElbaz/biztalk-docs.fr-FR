---
title: "Instructions de dimensionnement de la base de données de suivi | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Tracking database, performance
- Tracking database, size
- Tracking Analysis Server database [BAM]
- performance, Tracking database
ms.assetid: 2188bee5-c0dd-4448-bd4a-4ffb2a0c79f1
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1c0293ff0a03583e51ee447ec1bd6283f1b02164
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="tracking-database-sizing-guidelines"></a>Instructions pour le dimensionnement de la base de données des suivis
Cette section traite du dimensionnement de la base de données des suivis BizTalk (BizTalkDTADb) dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Elle explique comment utiliser des équations et des variables de message pour déterminer quelle taille la base de données des suivis BizTalk va avoir sur une période donnée et fournit des exemples concrets d'application de ces équations. Ceci établit la corrélation globale qui existe entre les messages BizTalk, les paramètres de suivi et la taille de la base de données des suivis, mais ne prend pas en compte d'autres facteurs SQL Server comme la taille des index des tables de suivi. Prévoyez des multiplicateurs raisonnables pour tenir compte de ces facteurs.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [À l’aide de Variables de Message à la taille de la base de données de suivi](../core/using-message-variables-to-size-the-tracking-database.md)  
  
-   [Dimensionnement de la base de données de suivi pour suivre les corps de Message](../core/sizing-the-tracking-database-to-track-message-bodies.md)  
  
-   [Scénario 1 : Dimensionnement de la base de données de suivi pour les Messages BizTalk simples](../core/scenario-1-sizing-the-tracking-database-for-simple-biztalk-messages.md)  
  
-   [Scénario 2 : Dimensionnement de la base de données de suivi pour les Messages dans les Orchestrations](../core/scenario-2-sizing-the-tracking-database-for-messages-in-orchestrations.md)  
  
-   [Scénario 3 : Dimensionnement de la base de données de suivi des Messages envoyés aux listes de Distribution](../core/scenario-3-size-the-tracking-database-for-messages-sent-to-distribution-lists.md)  
  
-   [Scénario 4 : Redimensionnement de la base de données de suivi pour tous les Messages](../core/scenario-4-sizing-the-tracking-database-for-all-messages.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Taille de l’enregistrement dans les bases de données de suivi](../core/record-size-in-tracking-databases.md)   
 [Sauvegarde et restauration des bases de données BizTalk Server](../core/backing-up-and-restoring-biztalk-server-databases.md)