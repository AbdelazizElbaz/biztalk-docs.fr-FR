---
title: "Résolution de la perte de données d’Orchestrations d’en cours | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data loss, MessageBox database
- data recovery
- data loss, recovery
- data loss, orchestrations
- data recovery, MessageBox database
- data recovery, orchestrations
- data loss, data recovery
- orchestrations, data recovery
- orchestrations, data loss
ms.assetid: dc6f1fd2-1976-40f2-ab57-41c7db40705e
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5eca757b80e31ee5db829d2d2079bf657d01079b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="resolving-data-loss-of-in-progress-orchestrations"></a>Résolution de la perte de données dans les orchestrations de type In-Progress
Les bases de données MessageBox contiennent l'état des orchestrations actuellement en cours. Bien qu'il n'existe aucune méthode permettant de savoir précisément quelles données ont été perdues dans ces bases de données, procédez comme suit afin de collecter des informations concernant les pertes de données :  
  
-   Déterminez les messages qui ont été envoyés et reçus dans les orchestrations actuelles, ainsi que les systèmes externes qui ont été utilisés après le point de récupération. Par exemple, si votre système conserve un journal externe des messages et des événements, examinez celui-ci. Vous pouvez également consulter manuellement les systèmes externes pour savoir quelles activités se sont produites.  
  
-   Après avoir déterminé la cause de la perte de données, vous pouvez commencer à corriger le système restauré, en choisissant les processus qui peuvent continuer, ceux qui doivent être terminés et redémarrés (en renvoyant les messages d'activation perdus) et ceux qui ont été correctement exécutés et peuvent à présent être fermés. Ce processus repose en grande partie sur l'architecture de votre système : il doit donc être considéré comme partie intégrante de votre stratégie de récupération du système.  
  
## <a name="see-also"></a>Voir aussi  
 [Résolution de la perte de données](../core/resolving-data-loss.md)