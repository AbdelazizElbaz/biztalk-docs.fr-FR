---
title: Comprendre le comportement des performances de suivi DTA | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b1a70951-bfed-435c-97f4-0b28a8e4e4dc
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 278d1e3c4b52c14c68d692ce3d3a3179d15bb10b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="understanding-dta-tracking-performance-behavior"></a>Présentation du comportement des performances de suivi DTA
Les principaux facteurs qui déterminent le débit maximal acceptable pour le suivi DTA sont les suivants :  
  
-   Débit des messages souhaité, c'est-à-dire les messages reçus par unité de temps, pour le système.  
  
-   Quantité des données suivies pour chaque message.  
  
-   Durée de conservation des données dans la base BizTalkDTADb avant la purge, c'est-à-dire la fenêtre de conservation des données.  
  
-   Si les données de la base BizTalkDTADb sont ou non archivées et purgées. L'archivage est facultatif, mais la purge doit être effectuée régulièrement.  
  
 Une chose que tous ces facteurs ont en commun : la vitesse à laquelle le DTA peut accepter et traiter des données (archive et purge).  
  
## <a name="how-the-biztalkdtadb-insert-and-processing-speed-affects-your-system"></a>Effets de la vitesse de traitement et d'insertion de BizTalkDTADb sur votre système  
 À présent, examinons le suivi des parcours de données qui est décrit dans [mesure de débit maximal acceptable de suivi](../core/measuring-maximum-sustainable-tracking-throughput.md)et d’évaluer l’impact de la vitesse de traitement et d’insertion de BizTalkDTADb sur les différents composants du système.  
  
 Concernant les tables du spouleur et trackingdata, nous pouvons imaginer que, si les processus qui déplacent les données de ces tables vers la base de données BizTalkDTADb ne sont pas en mesure de les insérer dans la base au moins aussi rapidement que la vitesse à laquelle l'exécution les insère dans les tables du spouleur et trackingdata, alors ces dernières commenceront à accumuler du retard. Ce n'est pas nécessairement une mauvaise chose à court terme si vous savez que le débit des messages sera réduit pour permettre par la suite de rattraper le retard. Cependant, tant que les données se trouveront dans les tables du spouleur ou trackingdata, elles ne seront pas disponibles dans la base de données BizTalkDTADb pour interrogation par les requêtes de suivi de la page Hub du groupe ou tout autre outil.  Ainsi, elles ne seront pas utiles pour la résolution de problèmes. Par conséquent, les périodes de retard attendues doivent être suffisamment courtes pour que les informations suivies soient toujours disponibles de manière appropriée en cas de problème nécessitant une analyse à l'aide des données de la base BizTalkDTADb.  
  
 Concernant le test, nous savons que ce ne sont pas les processus qui déplacent les données de suivi vers la base BizTalkDTADb (à savoir, TDDS et TrackedMessages_Copy_BizTalkMsgBoxDb) qui sont le facteur déterminant en cas d'accumulation de retard, mais la vitesse à laquelle la base de données BizTalkDTADb accepte les entrées. Généralement, c'est le fichier de données de la base BizTalkDTADb qui est lié aux E/S. En effet, c'est la vitesse du lecteur sur lequel le fichier de données de la base BizTalkDTADb réside qui déterminera la vitesse du suivi DTA global.  
  
## <a name="how-the-amount-of-data-in-biztalkdtadb-affects-io-speed"></a>Effets de la quantité de données de la base BizTalkDTADb sur la vitesse d'E/S  
 Un autre facteur clé lié à la vitesse d’e/s est la quantité de données dans la base de données BizTalkDTADb : en tant que la quantité de données suivies dans l’augmentation de la base de données BizTalkDTADb, la vitesse d’entrée et de traitement de la base de données BizTalkDTADb diminue car il est simplement plus de données Pour trier que de nouvelles données insérées, et cela affecte la quantité d’e/s requise pour chaque insertion.  
  
 C'est là que l'archivage et la purge entrent en jeu car ces processus empêchent l'augmentation trop importante de la taille de la base de données BizTalkDTADb. L'idée de base est de s'assurer que la taille de la base de données BizTalkDTADb reste inférieure au niveau auquel le retard commence à s'accumuler dans les tables du spouleur et trackingdata. Cependant, les processus de purge et d'archivage implémentés dans le travail SQL de purge et d'archivage de la base de données des suivis (BizTalkDTADb) requièrent également des ressources (UC, mémoire, et en particulier E/S) de la part du serveur de la base de données BizTalkDTADb, qui doivent être prises en compte lors de la mesure du débit maximal acceptable avec suivi.  
  
## <a name="see-also"></a>Voir aussi  
 [Mesurer le débit de suivi maximal acceptable](../core/measuring-maximum-sustainable-tracking-throughput.md)   
 [Scénarios de test pour mesurer le débit maximal acceptable du suivi DTA](../core/test-scenarios-for-measuring-mst-of-dta-tracking.md)   
 [Trucs et astuces pour trouver le débit maximal acceptable du suivi DTA](../core/tips-and-tricks-for-finding-mst-of-dta-tracking.md)   
 [Instructions pour le dimensionnement de la base de données de suivi](../core/tracking-database-sizing-guidelines.md)