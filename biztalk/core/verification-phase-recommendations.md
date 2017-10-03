---
title: "Recommandations de Phase de vérification | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 00663354-ce5d-4391-b835-89940c92c1ce
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 25344eafc37f492474b3f0bb36318afaf566829a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="verification-phase-recommendations"></a>Recommandations sur la phase de vérification
Une fois que le système dispose de tout le code, vous pouvez le stabiliser complètement et vérifier les critères de déclenchement. Cette phase est généralement appelée phase de stabilisation. Le dernier objectif de cette phase est d'identifier et de résoudre les bogues, ainsi que de prouver que le système est prêt pour la production. Par conséquent, cette phase implique un dernier test sur une version d'évaluation du système.  
  
 Une version d'évaluation est une version du système (en général la plus récente) considérée comme complète et suffisamment stable pour devenir la version finale, si tous les tests de vérification sont réussis. La preuve est apportée ensuite par la réussite de toute une batterie de tests de fonctionnement, de performances et de contraintes qui permettent de vérifier qu'elle est réellement prête.  
  
## <a name="test-to-verify-sustainable-throughput-and-latency"></a>Test de vérification du débit acceptable constant et de latence  
 Le test de vérification des performances est démarré parallèlement à la phase d'implémentation. Toutefois, il doit être finalisé sur une version d'évaluation qui a résisté à l'ensemble complet du test des critères de déclenchement. L'idéal est de n'apporter aucune modification de la version d'évaluation au cours du test final. Ainsi, le risque d'introduction de régressions est inexistant. En réalité, cela s'avère plutôt difficile et, étant donné que les modifications sont vérifiées au sein même de la version, les évaluations doivent être réalisées corrélativement au risque de régression.  
  
 Par exemple, si une modification importante est apportée à un artefact de système, comme un pipeline ou une orchestration, il vous faudra probablement réexécuter les tests de performances afin de valider cette nouvelle version d'évaluation.  
  
 Pour vous assurer que le système est prêt pour la production, vous devez vérifier qu'il a été testé de bout en bout de manière soutenue. Cela signifie que toutes les activités d’opérations telles que la base de données Gestion des opérations de requêtes planifiées et les arrêts doivent être testées, tel que défini dans la rubrique [Nouveautés des performances durables ?](../core/what-is-sustainable-performance.md) Il s’agit de la dernière possibilité de certifier est prêt pour le système, il est donc important de combiner l’ensemble des tests de performances durables dans du test final.  
  
## <a name="identify-bottlenecks-and-adjust-hardware-or-solution-to-remove-goal-blockers"></a>Identification des engorgements et réglage du matériel ou de la solution afin de supprimer les bloqueurs d'objectif  
 Dans la pratique, il est courant que le banc d’essai pour du test final est proche de production en ce qui concerne le matériel que le développement des bancs d’essais.  Par conséquent, il est important, à utiliser l’opportunité au cours du test final pour identifier les goulots d’étranglement nouveau ou existants dans le système et déterminer s’ils amplitude suffisante pour nécessiter des réglages matériels. Même si le matériel ne peut pas être réglé immédiatement, l'identification des engorgements les plus répandus fournit des informations intéressantes sur la planification et le fonctionnement.  
  
 Par exemple, si le système supporte le profil de charge de production, mais que la durée d'inactivité du disque physique du serveur MessageBox soit basse (par exemple, au-dessous de 20 %), la surveillance de ce disque au cours de la production peut être identifiée comme un indicateur clé de bon fonctionnement. En outre, tous les plans d'amélioration de la capacité de charge du système peuvent désormais intégrer la nécessité d'amélioration du sous-système.  
  
## <a name="see-also"></a>Voir aussi  
 [Des recommandations par Phase de planification de projet](../core/project-planning-recommendations-by-phase.md)   
 [Recommandations sur la configuration requise Phase](../core/requirements-phase-recommendations.md)   
 [Recommandations de Phase de conception](../core/design-phase-recommendations.md)   
 [Recommandations de Phase d’implémentation](../core/implementation-phase-recommendations.md)   
 [Recommandations de Phase de mise en production](../core/release-phase-recommendations.md)