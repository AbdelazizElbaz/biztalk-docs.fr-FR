---
title: "Suivi des événements commerciaux synchrone | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- performance, BAM
- events, tracking [BAM]
- BAM, event tracking
- BAM, performance
ms.assetid: 302c7918-bc62-46f1-a949-fbf94a7073e3
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 84223714e2e04cec6c079862693a09786cb19a7f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="synchronous-business-event-tracking"></a>Suivi synchrone des événements commerciaux
La façon la plus simple d'envoyer des données d'événements à BAM consiste à utiliser une instance de la classe DirectEventStream. Cette classe enregistre les données d'événement directement dans la Base de données d'importation principale BAM dans le contexte de la transaction en cours de l'application (le cas échéant).  
  
 Si une erreur se produit pendant cette opération, l'appel de méthode utilisé renvoie une exception dans l'application appelante. C'est le cas lorsque le nom d'un élément traité par l'activité de mise à jour ne correspond pas à la définition de l'activité BAM ou si vous n'avez pas encore déployé cette définition. Cela permet à l'application appelante d'intercepter et de résoudre n'importe quelle erreur se produisant lors de l'enregistrement des données de l'analyse BAM. La gestion ultérieure de ces données s'en trouve facilitée.  
  
 L'enregistrement des données de manière synchrone peut avoir un impact sur les performances du système, car l'application appelante doit attendre que le composant d'analyse BAM ait exécuté toutes les procédures et tous les déclencheurs stockés.  
  
## <a name="see-also"></a>Voir aussi  
 [Suivi des événements commerciaux asynchrone](../core/asynchronous-business-event-tracking.md)