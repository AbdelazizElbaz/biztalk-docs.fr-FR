---
title: "L’examen des goulots d’étranglement | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7ca22d07-d5fe-4dfb-8b52-3be3a95b0d6f
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a6a3cf4630bf3269516537439ed58b464589cf26
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-investigate-bottlenecks"></a>Examen des goulots d'étranglement
Cette rubrique décrit la procédure recommandée pour l'examen des goulots d'étranglement.  
  
## <a name="what-is-the-source-of-the-problem"></a>Quelle est la source du problème ?  
 La source du problème peut provenir du matériel ou du logiciel. Si les ressources sont sous-utilisées, cela signifie généralement qu'il existe un goulot d'étranglement à un emplacement quelconque du système. Les goulots d'étranglement peuvent être imputables à des limites matérielles ou à des configurations logicielles inefficaces ou les deux.  
  
 L'identification des goulots d'étranglement est un processus incrémentiel, où l'élimination d'un goulot d'étranglement peut conduire à la découverte du goulot suivant. L'objectif de cette rubrique est de présenter la méthode qui permet d'identifier et d'éliminer ces goulots d'étranglement. Il est possible pour un système de fonctionner avec des pics d'activité sur de courtes périodes. Toutefois, pour un débit acceptable constant, le système ne peut pas fonctionner plus vite que le plus lent de ses composants.  
  
## <a name="using-a-serial-approach"></a>Approche en série  
 Des goulots d'étranglement peuvent survenir aux points de terminaison (entrée/sortie) du système ou au niveau de points intermédiaires (orchestration/base de données). Une fois que l'emplacement d'un goulot d'étranglement a été isolé, il est possible de mettre en œuvre une approche structurée afin d'en identifier la source. Dès que les goulots d'étranglement ont été éliminés, il est essentiel de mesurer à nouveau les performances afin de s'assurer qu'un nouveau goulot d'étranglement n'a pas été créé à un autre endroit en aval du système.  
  
 La procédure d'identification et de correction des goulots d'étranglement doit être effectuée de manière systématique, en faisant varier un seul paramètre à la fois et en mesurant alors l'impact de cette modification unique. Faire varier plusieurs paramètres simultanément pourrait avoir pour effet de masquer l'impact d'une modification.  
  
 Par exemple, la modification du paramètre 1 pourrait améliorer les performances ; paradoxalement, modifier le paramètre 2 en même temps que le paramètre 1 pourrait avoir un effet négatif qui annulerait alors les bénéfices de la modification du paramètre 1, pour un résultat net égal à zéro. . En fait, ce résultat donnerait à tort une fausse impression négative quant à la modification du paramètre 1 et une fausse impression positive quant à la modification du paramètre 2.  
  
## <a name="testing-consistency"></a>Test de la cohérence  
 Il est impératif de mesurer les caractéristiques de performances après une modification des paramètres afin de pouvoir quantifier les effets de la modification.  
  
-   Matériel : Il est important d’utiliser un matériel cohérent car le changement de matériel peut afficher un comportement incohérent des résultats déroutants de production ; par exemple, n’utilisez pas un ordinateur portable.  
  
-   Durée d’exécution de test : Il est également important de mesurer les performances sur une durée minimale fixe pour vous assurer que les résultats sont durables et pas simplement de pics soudains. Une autre raison qui justifie le test sur des périodes plus longues, c'est qu'il convient de s'assurer que le système a terminé la phase initiale de préchauffage où toutes les mémoires cache sont remplies, que les tables de la base de données ont atteint les tailles attendues et que les procédures de limitation ont eu le temps de se mettre en place et de réguler le débit une fois que les seuils prédéfinis ont été atteints. Cette approche facilite la recherche du débit durable optimal.  
  
-   Paramètres de test : Il est également impératif ne varie ne pas à partir de la série de tests pour tester les paramètres de série de tests. Par exemple, changer la complexité d'un mappage et/ou les tailles de document peut entraîner des débits et des temps de latence différents.  
  
-   État propre : Une fois qu’un test est terminé il est important de nettoyage de l’exécution de tous les États avant d’exécuter le test suivant. Par exemple, les données historiques pourraient s'accumuler dans la base de données et avoir une influence sur le débit d'exécution. Recycler les instances de service facilite la libération des ressources en mémoire cache comme la mémoire, les connexions de base de données et les threads.  
  
## <a name="expectations-throughput-versus-latency"></a>Attentes : Débit par rapport à latence  
 Il est raisonnable d'attendre un certain débit et une certaine latence à partir du système déployé. Essayer d'obtenir à la fois un débit élevé et une latence faible revient à tirer dans deux directions opposées. Toutefois, on peut espérer atteindre un juste équilibre entre un débit optimal et une latence raisonnable. À mesure que le débit augmente, le système subit une pression accrue (consommation d'UC plus élevée, conflits d'E/S sur les disques plus nombreux, surcharge de la mémoire, conflits de verrouillage plus fréquents) qui peut avoir un impact négatif sur le délai de latence. Pour trouver la capacité optimale d'un système, il est impératif d'identifier et d'éliminer tous les goulots d'étranglement.  
  
 Les goulots d'étranglement peuvent provenir de données héritées (instances terminées) qui résident dans la base de données et n'ont pas été nettoyées. Lorsque cela se produit, on assiste à une dégradation des performances. Offrir au système le temps nécessaire pour se purger peut aider à résoudre le problème. Cependant, découvrir la cause de l'accumulation des travaux en retard et aider à y remédier est important.  
  
 Pour découvrir la cause de l'accumulation des travaux en retard, il est important d'analyser les données historiques et de surveiller les compteurs de l'Analyseur de performances (pour identifier les modèles d'utilisation et diagnostiquer la source de l'accumulation). Cette situation est fréquente lorsque des volumes importants de données sont traités par lots, la nuit. Découvrir la capacité du système et son aptitude à récupérer suite à une accumulation peut être utile pour estimer les besoins matériels pour la gestion des scénarios de surcharge, ainsi que la quantité d'espace tampon à prévoir dans un système pour assumer les pics imprévus de débit.  
  
 Affiner le système en vue d'obtenir un débit durable optimal nécessite une connaissance approfondie de l'application à déployer, des forces et faiblesses du système et des modèles d'utilisation du scénario spécifique. La seule manière de découvrir les goulots d'étranglement et de prévoir avec certitude le débit durable optimal consiste à effectuer un test rigoureux d'une topologie se rapprochant le plus de celle qui sera utilisée en production.  
  
 D'autres rubriques de cette section vous guident pour la définition de cette topologie et fournissent des conseils sur la manière d'éliminer les goulots d'étranglement existants et, si possible, d'éviter qu'ils ne se créent dès l'origine.  
  
## <a name="scaling"></a>mise à l’échelle  
 Des goulots d'étranglement peuvent se produire à différents niveaux de la topologie déployée. Certains d'entre eux peuvent être résolus par une mise à niveau du matériel. Le matériel peut faire l'objet soit d'une évolution verticale (augmentation du nombre d'UC, de la capacité de la mémoire ou du cache) soit d'une évolution horizontale (serveurs supplémentaires). Le choix entre une évolution verticale ou horizontale dépend du type de goulot d'étranglement rencontré et de l'application en cours de configuration. Les informations suivantes fournissent des conseils quant à la manière de modifier les topologies de déploiement matérielles en fonction des goulots d'étranglement rencontrés. Une application doit être élaborée en partant de zéro pour pouvoir tirer parti d'une évolution verticale ou horizontale. Exemple :  
  
-   Faire évoluer verticalement un serveur en lui ajoutant des UC supplémentaires ou de la mémoire n'éliminera pas forcément le problème si l'application est sérialisée et dépendante d'un seul thread d'exécution.  
  
-   Faire évoluer horizontalement un système en ajoutant des serveurs ne sera d'aucune utilité si les serveurs supplémentaires se contentent de créer de nouveaux conflits pour l'utilisation d'une ressource commune qui ne peut évoluer. Toutefois, l'évolution horizontale offre d'autres atouts. Un déploiement sur deux serveurs à processeurs doubles au lieu d'un serveur à processeur quadruple permet d'obtenir un serveur redondant qui a une double fonction : répondre aux besoins d'évolution en gérant un débit supplémentaire et offrir une topologie haute disponibilité.