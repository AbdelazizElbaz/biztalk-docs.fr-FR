---
title: Direction de communication | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- port types, communication direction
- communication direction [port types]
ms.assetid: b278325e-a1da-49a6-8332-80a5f640cc22
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9d6c664643629971366805d08600677d22d7c419
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="communication-direction"></a>Direction de la communication
Chaque *port* a sa propre direction de communication. La direction de communication est utilisée en association avec le modèle de communication du type du port pour compléter la définition de la manière dont un port peut être utilisé. La direction de communication, ou polarité, détermine la direction dans laquelle les messages seront transmis via le port.  
  
 Si le type du port a un modèle de communication unidirectionnel, sa direction de communication est soit Envoi, soit Réception. Si le type du port a un modèle de communication bidirectionnel (requête-réponse), sa direction de communication est soit Envoi-Réception, par laquelle une requête est envoyée et une réponse est reçue, soit Réception-Envoi, par laquelle une requête est reçue et une réponse est envoyée.  
  
## <a name="see-also"></a>Voir aussi  
 [Modèle de communication](../core/communication-pattern.md)  
 [Comment exécuter l’Assistant Configuration du Port](../core/how-to-run-the-port-configuration-wizard.md)   
 [L’utilisation de Ports dans les Orchestrations](../core/using-ports-in-orchestrations.md)