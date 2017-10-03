---
title: Configuration requise de Phase recommandations | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0b510313-c3a7-42bc-9c9b-336c927a5d4a
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d945e50d9c7b8f0a9feae5e0f93a4766d108c695
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="requirements-phase-recommendations"></a>Recommandations sur la phase de configuration requise
Le premier élément livrable associé à la phase de configuration est une spécification de configuration, ou une spécification fonctionnelle qui inclut une configuration fondée sur les objectifs de performances. Il est essentiel que les utilisateurs finaux et les propriétaires corporatifs du système soient impliqués dans la détermination de ces objectifs afin de s'assurer qu'un profil de performance précis en est déduit.  
  
## <a name="establish-performance-criteria"></a>Établissement de critères de performance  
 Du point de vue de la performance, la partie la plus importante de la spécification fonctionnelle créée durant cette phase est la définition d'objectifs de performances détaillés pour le projet et l'établissement de critères de déclenchement des performances. La définition des critères de performance comporte trois composants critiques :  
  
-   une courbe qui définit les performances en tant que fonction temporelle.  
  
-   associer une exigence de performance à la fonction de performance ;  
  
-   une répartition des fichiers par taille et type.  
  
 Ces critères sont présentés dans [Nouveautés des performances durables ?](../core/what-is-sustainable-performance.md)  
  
 Vous pouvez déduire les critères de déclenchement des performances d'une application à partir des objectifs de performances. Ces critères représentent un comportement réalisable et mesurable que vous pouvez vérifier à l'aide d'un test. L'application n'atteindra pas la version finale avant que tous les critères de déclenchement n'aient été satisfaits ou, si cela n'est pas réalisable, qu'ils n'aient été identifiés comme des exceptions aux critères de déclenchement.  
  
 Il est essentiel que les critères de déclenchement soient définis dans les premières phases du cycle du produit. Ainsi, toutes les personnes impliquées connaissent les objectifs et les conséquences de leur non-réalisation avant la fin de la conception et de l'implémentation.  
  
 De plus, les scénarios de test des performances seront fondés sur la manière dont les critères de déclenchement seront mesurés ; les critères doivent donc être suffisamment détaillés pour éviter toute confusion. Par exemple, un critère indiquant qu'un débit spécifique doit être atteint devrait inclure :  
  
-   le matériel sur lequel il doit être réalisé, c'est-à-dire le nombre et le type de serveurs, la vitesse et le type de disque, etc. ;  
  
-   le scénario à tester, détaillant par exemple les chemins d'accès suivis par les messages dans l'application ;  
  
-   la manière dont il sera mesuré, par exemple à l'aide de compteurs de performance, d'un code personnalisé, en mesurant le temps que met un message pour arriver dans un dossier de partage, etc.  
  
 Un critère de déclenchement est correctement défini si toute personne l'étudiant le trouve suffisamment documenté et comprend comment concevoir un scénario de test vérifiant ce critère.  
  
## <a name="identify-performance-risks"></a>Identification des risques d'exécution  
 Une fois les objectifs et critères de déclenchement des performances suffisamment détaillés, il est possible d'effectuer une évaluation initiale des risques d'exécution. Cette analyse a pour but d'identifier les parties de l'application qui nécessitent une attention particulière lors de la conception, des solutions alternatives ou une élimination afin de répondre aux critères sélectionnés.  
  
 Par exemple, chaque type d'adaptateur de transport présente des caractéristiques de performance et d'échelle qui lui sont propres. Si le débit souhaité est supérieur à la capacité d'un ou plusieurs types d'adaptateurs (de réception ou d'envoi), il peut être nécessaire d'envisager des solutions alternatives de mise à l'échelle de l'adaptateur.  
  
## <a name="estimate-sizing"></a>Estimation du dimensionnement  
 Il n'est jamais trop tôt pour entamer le processus d'estimation du dimensionnement du matériel requis, en fonction des objectifs et critères établis. Les estimations doivent toujours être fondées sur les résultats de tests fiables. Dans les premières phases d'un projet, ces résultats doivent provenir de sources externes. Vous pouvez lire des études de cas dans le centre de développement BizTalk Server, au [http://go.microsoft.com/fwlink/?LinkId=49339](http://go.microsoft.com/fwlink/?LinkId=49339). Les études de cas fournissent des détails au sujet des scénarios testés, le matériel sur lequel les tests ont été effectués et la configuration des tests. Vous pouvez extrapoler une estimation initiale du dimensionnement de votre système à partir des performances obtenues dans ces scénarios de test.  
  
 N’oubliez pas qu’il n’existe aucun modèle ou simulation de précision la dimension système pour toute application arbitraire exécutée [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]est une plateforme sur laquelle de nombreuses solutions d’application peut être déployée, chacun avec son propre comportement de performances. C'est pourquoi la dimension finale du système devra vraisemblablement être ajustée pour toutes les architectures applicatives, à l'exception des plus simples, même si une estimation dérivée des résultats d'une étude de cas fournit un point de départ acceptable pour le processus de planification.  
  
## <a name="plan-for-sufficient-testing"></a>Planification de tests suffisants  
 Comme indiqué ci-dessus, il n'existe actuellement aucun modèle ou simulation permettant de prédire avec précision les besoins en matériel requis pour la réalisation des objectifs de performances. Cela signifie que le seul moyen de prouver qu'un système est réellement capable de réaliser les objectifs est de le tester sur un matériel de niveau production. Il s'agit donc de mener des tests sur un matériel se rapprochant autant que possible de la configuration de production.  
  
 Cette étape de la planification est essentielle et fait appel aux principes des performances durables, à la compréhension approfondie des profils de débit, ainsi qu'aux critères de déclenchement des performances. À l'aide des profils de débit obtenus par l'extrapolation des données existantes, il faut déduire des scénarios de test qui mesureront de manière cohérente les critères de déclenchement. Les scénarios de test doivent être exécutés en tenant compte de la durabilité. Pour consulter des exemples de tests durables, voir les rubriques suivantes :  
  
-   [Mesurer le débit de moteur maximal acceptable](../core/measuring-maximum-sustainable-engine-throughput.md)  
  
-   [Mesurer le débit de suivi maximal acceptable](../core/measuring-maximum-sustainable-tracking-throughput.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Des recommandations par Phase de planification de projet](../core/project-planning-recommendations-by-phase.md)   
 [Recommandations de Phase de conception](../core/design-phase-recommendations.md)   
 [Recommandations de Phase d’implémentation](../core/implementation-phase-recommendations.md)   
 [Recommandations de Phase de vérification](../core/verification-phase-recommendations.md)   
 [Recommandations de Phase de mise en production](../core/release-phase-recommendations.md)