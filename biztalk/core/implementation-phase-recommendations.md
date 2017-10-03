---
title: "Recommandations sur la mise en œuvre Phase | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 04877156-cc32-480b-8410-d26eb073c327
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fce6d7df21f15b40e0312438394859f4b94b7fc2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="implementation-phase-recommendations"></a>Recommandations sur la phase d'implémentation
La phase d'implémentation comprend les produits des phases de conception et de configuration, et les implémente à l'aide des technologies appropriées. Pour un test de validation, c'est au cours de cette phase que les scénarios du test sont réalisés et automatisés. En général, de nombreux tests effectués sur les versions précédentes d'un système sont également réalisés au cours de cette phase, non seulement pour valider le système, mais aussi pour vérifier l'absence de problèmes avec les scénarios de test eux-mêmes.  
  
## <a name="implement-performance-test-cases"></a>Implémentation des scénarios de test de performances  
 Au cours des phases de conception et de configuration, des scénarios de test représentatifs sont définis et conçus afin de prouver que les performances du système répondent aux critères de déclenchement des performances ou les dépassent. Au cours de la phase d'implémentation, les scénarios de test sont implémentés, automatisés et exécutés pour la première fois afin de vérifier que le test est prêt à contrôler les performances, puisque diverses parties du système ont un code complet.  
  
 Il est très important d'automatiser autant que possible la configuration, l'exécution et l'analyse des résultats des tests au cours de la phase d'implémentation. Le nombre de tests de performances peut être élevé et leur exécution peut s'avérer longue. L'automatisation de ces tests permet donc une meilleure efficacité d'exécution, car elle demande moins de ressources humaines. En outre, anticipez en exécutant des tests de vérification plusieurs fois au cours d'un test puisque les goulots d'étranglements des performances sont identifiés et les correctifs fournis. L'automatisation des tests permet d'exécuter de manière plus rapide, plus simple et plus cohérente la vérification des performances entre les versions.  
  
## <a name="build-the-performance-test-bed"></a>Génération du banc d'essai des performances  
 Il est indispensable de réaliser tous les tests de performances de manière cohérente et reproductible. Pour pouvoir comparer les résultats des tests, il est essentiel d'utiliser exactement le même matériel pour établir le niveau de référence et exécuter les tests. En fonction de l'architecture de solution, de nombreuses variables matérielles peuvent affecter les résultats de manière significative.  
  
 Par exemple, nous avons découvert que le cache disponible, même sur des serveurs identiques, affecte les résultats de manière significative, bien qu'il ne soit pas forcément évident, lorsqu'on regarde la configuration des serveurs, que deux serveurs aient des niveaux différents de cache. S'assurer que les tests sont exécutés sur des bancs d'essai qui ne sont pas modifiés entre chaque exécution permet d'éliminer toute question de compatibilité. Si vous modifiez la configuration matérielle, comme lorsque vous adaptez la taille d'un nouveau système, les niveaux de référence doivent être établis de nouveau pour pouvoir comparer les résultats.  
  
## <a name="begin-performance-validation-testing"></a>Début du test de validation des performances  
 Le test de performances débute presque toujours parallèlement à l'implémentation.  Il n'est jamais trop tôt pour commencer de valider les critères de déclenchement, car au plus tôt vous commencez, au plus tôt vous pouvez réagir en cas de problèmes.  
  
 Le point principal à prendre en compte lorsque vous commencez un test est de vous assurer que le système (ou la partie concernée) à tester est prêt. La disponibilité du système est très subjective, mais doit prendre en compte les facteurs suivants :  
  
 Le chemin d'accès du système dont vous allez tester le code est-il complet ? Si du code significatif doit être ajouté au chemin d'accès, vous souhaitez probablement concentrer vos efforts ailleurs jusqu'à ce qu'une masse importante soit prête.  
  
 Les tests fonctionnels ont-ils été correctement exécutés sur le système ? Il peut s'avérer très long et inefficace de configurer et de lancer un test de performances sur un système ou sous-système dans le but unique de rechercher une erreur de fonctionnement qui bloque la réalisation du test de performances. Assurez-vous que le fonctionnement de chemin d'accès a été suffisamment testé avant de lancer le test de performances.  
  
 Quel est le niveau de risque pour le système ou sous-système à tester ? Les premiers chemins d'accès au système à être étudiés doivent être ceux qui comportent le risque maximal en ce qui concerne les critères de déclenchement des performances. Il est impossible de surévaluer l'importance de l'identification des goulots d'étranglement du système suffisamment tôt dans le cycle de vie du projet afin d'avoir le temps de modifier le développement.  
  
## <a name="see-also"></a>Voir aussi  
 [Des recommandations par Phase de planification de projet](../core/project-planning-recommendations-by-phase.md)   
 [Recommandations sur la configuration requise Phase](../core/requirements-phase-recommendations.md)   
 [Recommandations de Phase de conception](../core/design-phase-recommendations.md)   
 [Recommandations de Phase de vérification](../core/verification-phase-recommendations.md)   
 [Recommandations de Phase de mise en production](../core/release-phase-recommendations.md)