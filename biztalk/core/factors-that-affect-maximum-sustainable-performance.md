---
title: Les facteurs qui affectent les performances maximales admissibles | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- maximum sustainable throughput (MST), maintenance
- monitoring, maximum sustainable thoughput (MST)
- maintaining, maximum sustainable thoughput (MST)
- maximum sustainable throughput (MST), monitoring
- maximum sustainable throughput (MST), load patterns
- maximum sustainable throughput (MST), sustainable load test
- sustainable performance
ms.assetid: 99b99655-bc77-425c-a133-204781d7c430
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: be96ad552abef66e2a401e334da1c27ee0e08cd5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="factors-that-affect-maximum-sustainable-performance"></a>Facteurs affectant les performances maximales admissibles
Le débit maximal admissible dépend directement d'un large éventail de facteurs comme les ressources serveur disponibles, le type des composants utilisés dans la solution, la taille des messages et la charge globale que représentent les messages. D'autres facteurs auxquels on ne pense pas forcément doivent être pris en compte. Les facteurs suivants doivent être considérés lors de l'estimation des performances maximales admissibles :  
  
## <a name="load-patterns"></a>Modèles de charge  
 En général, les messages ne sont pas acheminés dans un environnement BizTalk Server de production à un rythme prévisible et constant. Souvent, ce sont les besoins de l'entreprise qui imposent à BizTalk Server de traiter les messages selon un rythme variable avec des pics et des creux. Quand un pic survient, les besoins de BizTalk Server en matière de traitement peuvent évoluer très vite et, alors qu'ils étaient négligeables, entraîner soudain une suractivité quand les messages sont reçus plus rapidement qu'ils ne sont traités. Dans ce scénario, les messages publiés s'accumulent dans la base de données MessageBox jusqu'à ce que BizTalk les remette aux abonnés appropriés. Tant que BizTalk Server est capable de traiter les messages accumulés entre des pics, il n'y a pas de problème.  
  
 Le modèle de flux des messages étant variable dans un environnement BizTalk Server, il convient d'exécuter des scénarios de test sur une longue durée pour s'assurer que la solution peut absorber les pics et fournir le débit souhaité indéfiniment.  
  
## <a name="monitoring-and-maintenance-activities"></a>Activités de surveillance et de maintenance  
 Pendant la vie d'une solution de production, une multitude d'activités de surveillance et de maintenance peuvent avoir un impact sur les performances de BizTalk et doivent être prises en compte dans les scénarios de test. Il s'agit notamment des activités suivantes :  
  
-   **Requêtes de la Console Administration de BizTalk** ces requêtes consomment des ressources et affectent le débit global, selon le type et la fréquence des requêtes.  
  
-   **Sauvegarde, l’archivage et la purge des activités** également, ces activités consomment des ressources et doivent être prises en compte dans les scénarios de test. Toutes les bases de données BizTalk Server doivent être sauvegardées régulièrement et leurs journaux des transactions doivent être réduits. Sinon, la taille de ces journaux risque d'augmenter de manière incontrôlée, ce qui consommera tout l'espace disque disponible pour la base de données de transactions. Si le suivi est utilisé, la base de données des suivis doit être purgée régulièrement et éventuellement archivée pour éviter que sa taille augmente trop. Pour plus d’informations sur la maintenance des bases de données BizTalk Server, consultez [sauvegarde et restauration de bases de données BizTalk Server](../core/backing-up-and-restoring-biztalk-server-databases.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Mesurer le débit de suivi maximal acceptable](../core/measuring-maximum-sustainable-tracking-throughput.md)