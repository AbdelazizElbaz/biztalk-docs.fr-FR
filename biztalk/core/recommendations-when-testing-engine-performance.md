---
title: Des performances du moteur de recommandations pour le test | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: maximum sustainable throughput (MST), best practices
ms.assetid: 0aa9d833-0e7d-4347-a6ca-8d658749b4f2
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 06fc2d81ca8121fe625a30258070281d2b3ff4bc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="recommendations-when-testing-engine-performance"></a>Recommandations pour le test des performances du moteur
Suivez les directives ci-après lorsque vous testez les performances du moteur BizTalk :  
  
 **Connaître votre profil** comme les tests de charge de trois ont illustré, il est essentiel de connaître le profil de votre charge en termes de messages traités au fil du temps.  Mieux ce profil est dessiné, plus précisément vous pourrez tester et ajuster la capacité du système. Si vous ne connaissez que le débit maximal requis, l'approche la plus classique consiste à échelonner votre système de sorte que le débit maximal réalisable soit supérieur ou égal à la charge maximale. Toutefois, si vous savez que la charge a des hauts et des bas prévisibles, vous pouvez davantage optimiser votre système de sorte qu'il récupère entre ces pics ; ainsi, vous pouvez réaliser un déploiement global à petite échelle et à moindre coût.  
  
 **Tester les performances tôt** Évitez l’interruption d’un investissement des efforts considérables dans la conception et de test des fonctionnalités de votre solution, mais en attente jusqu'à ce que la dernière minute pour tester les performances sur du matériel de production. Exécutez, dès que possible dans votre cycle de développement, des tests de performance sur votre système qui simulent le profil de charge attendu. Ainsi, vous saurez très tôt si vous devez modifier votre conception ou votre architecture pour atteindre vos objectifs et vous pourrez faire les ajustements et les tests nécessaires.  
  
 **Émuler votre profil de charge attendu lors du test de performances** il existe deux composants principaux pour cela :  
  
1.  émulez le profil de charge dans le temps ;  
  
2.  exécutez le test suffisamment longtemps pour évaluer sa faisabilité.  
  
 Si, comme cela est fréquemment le cas, vous avez des cycles quotidiens en nature, prévoyez d'exécuter des tests de performance pendant au moins un jour pour valider leur faisabilité. Plus vous exécutez les tests longtemps, mieux c'est.  
  
 **Émuler la configuration de la production** par exemple, le nombre et type de ports, l’hôte et l’hôte de l’instance configuration, la configuration de la base de données et le programme d’installation de l’adaptateur. Ne croyez pas que les modifications de la configuration n'auront pas d'impact significatif sur les performances.  
  
 **Utiliser des messages réels** taille et la complexité des messages affectent les performances, ainsi qu’et de test avec les mêmes schémas de message et les instances que vous souhaitez voir en production.  
  
 **Émuler vos opérations normales au cours des tests de performances** si les tests de charge n’incluent pas les activités, les opérations telles que les requêtes périodiques de la base de données, sauvegardes, et les purges affectent le débit durable, par conséquent, assurez-vous que vous Effectuez ces tâches au cours de vos performances et la capacité des séries de tests. Ceci inclut le suivi DTA et BAM si vous comptez les utiliser en production.  
  
 **La vitesse du sous-système d’e/s pour la MessageBox est un facteur clé du succès** les tests de charge qui ont été effectuées utilisaient un réseau de zone de stockage rapide pour les fichiers de base de données MessageBox est dédié à cette build. Même dans ce cas, les fonctions de nettoyage ont permis de ramener la durée d'inactivité à une valeur proche de zéro pour les fichiers de données SQL. Le sous-système d'E/S constitue souvent un goulot d'étranglement dans les systèmes de production. La stratégie classique d'optimisation des E/S SQL consiste à placer le ou les fichiers de base de données et le ou les fichiers journaux sur des lecteurs physiques distincts, dans la mesure du possible.  
  
 **Assurez-vous que l’Agent SQL est en cours d’exécution sur tous les serveurs MessageBox** clairement, les tâches de nettoyage sera jamais s’exécuter si l’Agent SQL n’est pas en cours d’exécution, assurez-vous ces éléments s’exécutent.  
  
 **Profondeur du spouleur est un indicateur clé** indépendamment des autres indicateurs, cette mesure donnera vous un moyen simple et rapide pour évaluer si votre système charge ou non.