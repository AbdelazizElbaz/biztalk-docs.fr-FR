---
title: "Suivi des événements - Définition | Microsoft Docs"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- configuring [HAT tracking], events
- DTA_Services audit table [HAT]
- HAT, events
- events, tracking
- tracking, events
- Tracking database, DTA_Services audit table
- events, HAT
ms.assetid: dd211752-d1af-4287-967a-908b8d067ebb
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: faa53881cf42ae2769621e10ce21e1160f9b7be0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="what-is-event-tracking"></a>Suivi des événements - Définition
Les données d'événements de messages suivis sont basées sur les événements (par exemple, le démarrage ou l'arrêt d'un service, ou l'envoi ou la réception d'un message). Le processus de suivi des événements de message renvoie la liste des événements qui se sont produits, ce qui vous permet de voir tout ce qui s'est passé sur la base des filtres de suivi définis.  
  
 Vous pouvez suivre le démarrage et l'arrêt des orchestrations et des ports, les heures d'envoi et de réception des messages ou encore l'exécution de chaque forme d'une orchestration.  
  
 La base de données des suivis BizTalk (BizTalkDTADb) comporte une table d'audit dénommée DTA_Services. Celle-ci contient l'historique de tous les services déployés (pipelines, transports et orchestrations). Elle ne conserve pas de trace des annulations de déploiement.  
  
 Vous pouvez suivre le contenu et les propriétés promues d'un message. Suivi des événements de message présente ces actions comme **le corps du Message** suivi et **propriété de Message** de suivi. Il affiche les enveloppes, mais ne vous permet pas de suivre les propriétés des messages à partir de celles-ci.  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration du suivi à l’aide de la Console Administration de BizTalk Server](http://msdn.microsoft.com/en-us/49b7f9d3-60b5-41bd-ba8b-029253926bef)