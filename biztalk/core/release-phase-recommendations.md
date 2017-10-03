---
title: Recommandations sur la Phase de version | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c5ac72aa-decd-4b3e-be34-e585e54568b3
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 46a38a8a06fac8dc35fed4d965ea9b7952c5fdfe
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="release-phase-recommendations"></a>Recommandations sur la phase de lancement
La phase de lancement implique la propagation du système à présent validé vers l'équipement de production.  
  
## <a name="propagate-test-bed-optimizations-to-production-systems"></a>Propagation d'optimisations de bancs d'essais vers des systèmes de production  
 Propager la configuration et les artefacts du système vers l'équipement de production et démarrer ce dernier pour lancer le traitement est un processus relativement simple. Mais en pratique, on a tôt fait d'omettre certains aspects importants relatifs aux performances durant cette phase :  
  
-   **Vérifiez que les optimisations des plateformes sont propagées**. lors de l'implémentation et de la vérification, il est fréquent d'implémenter n'importe quel nombre d'optimisations des performances de niveau plateforme.  
  
     Ainsi, lorsque l'on utilise sur Internet Information Server (IIS) un adaptateur isolé de type HTTP par exemple, on peut recourir à un certain nombre d'optimisations courantes des performances, comme augmenter le nombre des processus IIS dans lesquels les adaptateurs seront exécutés. Ce genre d'optimisations des performances trouvées avant le lancement doivent être suivies et propagées vers l'environnement de production également.  
  
-   **Configurer et automatiser la sauvegarde de données, journal des journaux de transaction, configurations de conservation des données et la purge des tâches**. dans le cadre de la certification de production, la fréquence avec laquelle les bases de données (la base de données des suivis BizTalk et la base de données BAM par exemple) sont sauvegardées et purgées est indispensable à la durabilité. Ces paramètres doivent donc être migrés vers la production s'ils n'y figurent pas déjà.  
  
## <a name="see-also"></a>Voir aussi  
 [Des recommandations par Phase de planification de projet](../core/project-planning-recommendations-by-phase.md)   
 [Recommandations sur la configuration requise Phase](../core/requirements-phase-recommendations.md)   
 [Recommandations de Phase de conception](../core/design-phase-recommendations.md)   
 [Recommandations de Phase d’implémentation](../core/implementation-phase-recommendations.md)   
 [Recommandations de Phase de vérification](../core/verification-phase-recommendations.md)