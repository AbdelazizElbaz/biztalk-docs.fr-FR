---
title: "Phase 5 : L’exécution de l’évaluation | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3d40fc64-b6cb-448b-8ea1-a6ad7302ab8b
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2fba6d49d8d69276af4282ad0a941ee1fc4d8068
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="phase-5-executing-the-assessment"></a>Phase 5 : L’exécution de l’évaluation
La phase d’exécution est où les données de performances sont générées via le test de charge automatique et où les goulots d’étranglement de performances sont détectées et traitées. Cette phase est un processus itératif, par laquelle les goulots d’étranglement de performances sont réduites ou éliminées par un test, l’évaluation des performances, l’optimisation et la tester à nouveau.  
  
 Cette rubrique décrit les étapes généralement suivies lors de la phase d’exécution d’une évaluation de performances de BizTalk Server :  
  
## <a name="step-1-run-automated-tests"></a>Étape 1 : Exécuter des tests automatisés  
 Commencer la phase d’exécution en exécutant des tests automatisés. En général, une évaluation des performances BizTalk Server se concentre sur le débit ou la latence de test mais peut inclure les tests fonctionnels et vérification de build. Pour obtenir des informations complètes sur l’exécution de tests automatisés, consultez [mise en œuvre des tests automatisés](../technical-guides/implementing-automated-testing.md).  
  
## <a name="step-2-document-and-evaluate-test-results"></a>Étape 2 : Document et évaluer les résultats des tests  
 À la fin de chaque test, soigneusement documenter les résultats de test et d’évaluer si les objectifs de performance mentionnées ont été remplies.  
  
## <a name="step-3-modify-the-configuration-of-biztalk-server-third-party-systems-or-solution-artifacts-to-tune-for-performance-based-on-the-test-results"></a>Étape 3 : Modifier la configuration de BizTalk Server, les systèmes tiers ou des artefacts de solution pour régler les performances selon les résultats des tests  
 Les résultats des tests permet de prendre des décisions sur l’optimisation de l’environnement d’atteindre les objectifs de débit et de latence.  
  
## <a name="step-4-record-all-changes-made-to-the-environment"></a>Étape 4 : Enregistrement de toutes les modifications apportées à l’environnement  
 Assurez-vous que toutes les modifications apportées à l’environnement sont soigneusement documentées. Un enregistrement des modifications vous permet de facilement appliquer les modifications dans l’environnement de production et prend en charge l’annulation des modifications si besoin.  
  
## <a name="step-5-repeat-this-cycle-until-goals-are-achieved"></a>Étape 5 : Répétez le ce cycle jusqu'à ce que les objectifs sont atteints.  
 Continuer le cycle de test, l’évaluation et documenter les résultats, optimisation de l’environnement et documenter les modifications de l’environnement jusqu'à ce que les objectifs de performance souhaités sont atteints.  
  
## <a name="step-6-summarize-test-results-at-the-end-of-each-day"></a>Étape 6 : Résumer les résultats des tests à la fin de chaque jour  
 Effectuez un « rapport de synthèse » des résultats de test et des progrès réalisés à la fin de chaque jour. Un message électronique qui contient le résumé de la compilation et à envoyer à toutes les parties prenantes dans l’évaluation des performances pour conserver tout le monde informé de la progression est effectuée.  
  
## <a name="step-7-update-the-project-plan-as-timeline-goals-are-met"></a>Étape 7 : Mettre à jour le plan de projet en tant que les objectifs de chronologie  
 La chronologie développée dans la phase de planification est une bonne référence pour la progression globale de l’évaluation des performances. Mettre à jour cette chronologie que nécessaire pour communiquer l’état d’avancement à toutes les parties prenantes.  
  
## <a name="see-also"></a>Voir aussi  
 [Phases d’une évaluation des performances](../technical-guides/phases-of-a-performance-assessment.md)