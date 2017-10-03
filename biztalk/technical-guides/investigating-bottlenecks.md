---
title: "Examen des goulots d’étranglement | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2ab8e485-ffe5-4f71-9ce2-f72c0c939e5d
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e34d01bbfafd1a05f87fff5cda2b21764d43f42b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="investigating-bottlenecks"></a>Examen des goulots d’étranglement
Cette rubrique décrit la procédure recommandée pour l’examen des goulots d’étranglement.  
  
## <a name="what-is-the-source-of-the-problem"></a>Quelle est la source du problème ?  
 La source du goulot d’étranglement peut être matériel ou du logiciel. Lorsque les ressources sont apparaissent, il est généralement une indication d’un goulot d’étranglement. Les goulots d’étranglement peuvent être dû à des limites matérielles, par des configurations logicielles inefficaces ou par les deux.  
  
 L'identification des goulots d'étranglement est un processus incrémentiel, où l'élimination d'un goulot d'étranglement peut conduire à la découverte du goulot suivant. L'objectif de cette rubrique est de présenter la méthode qui permet d'identifier et d'éliminer ces goulots d'étranglement. Il est possible pour un système de fonctionner avec des pics d'activité sur de courtes périodes. Toutefois, pour un débit acceptable constant, le système ne peut pas fonctionner plus vite que le plus lent de ses composants.  
  
## <a name="using-an-iterative-approach-to-testing"></a>À l’aide d’une approche itérative au test  
 Les goulots d’étranglement peuvent se produire sur les points de terminaison (entrée/sortie) du système ou au milieu (orchestration/base de données). Une fois le goulot d’étranglement a été isolé, utilisez une approche structurée pour identifier la source. Une fois le goulot d’étranglement est facilité, il est important de mesurer les performances pour vous assurer qu’un nouveau goulot d’étranglement n’a pas été créé ailleurs dans le système.  
  
 Le processus d’identification et de résolution des goulots d’étranglement doit être effectué de façon itérative. Varier qu’un seul paramètre à la fois, répéter exactement les mêmes étapes au cours de chaque série de tests, puis mesurer les performances pour vérifier l’impact de la modification unique. Faire varier plusieurs paramètres simultanément pourrait avoir pour effet de masquer l'impact d'une modification.  
  
 Par exemple, la modification du paramètre 1 pourrait améliorer les performances. Toutefois, la modification du paramètre 2 conjointement avec la modification du paramètre 1 pourrait avoir un effet négatif et inversent les avantages de la modification du paramètre 1. Cela conduit à un net égal à zéro et génère un faux négatif sur l’effet de la modification du paramètre 1 et un faux positif sur l’effet de la modification du paramètre 2.  
  
## <a name="testing-consistency"></a>Test de la cohérence  
 Après avoir modifié les paramètres de mesure des caractéristiques de performances doit être effectuée pour valider l’effet de la modification.  
  
-   **Matériel -** utiliser un matériel cohérent car le changement de matériel peut provoquer un comportement incohérent et produire des résultats trompeurs. Par exemple, vous utiliseriez pas un ordinateur portable pour tester les performances d’une solution BizTalk.  
  
-   **Tester la durée d’exécution -** mesurer les performances pour une durée minimale fixe pour vous assurer que les résultats sont raisonnables. Exécution de tests pour des périodes plus longues garantit également que le système a subi l’initiale à chaud/rampe période où tous les caches sont remplies, les tables de base de données ont atteint le nombre attendu et la limitation est un délai suffisant pour réguler le débit une fois prédéfinie les seuils sont atteints. Cette approche facilite la recherche du débit durable optimal.  
  
-   **Test des paramètres –** ne varient pas de paramètres de test à partir de la série de tests pour la série de tests. Par exemple, changer la complexité d'un mappage et/ou les tailles de document peut entraîner des débits et des temps de latence différents.  
  
-   **Nettoyer l’état -** après un test est terminé, vérifiez que l’état de l’environnement de test est propre avant d’exécuter le test suivant. Par exemple, les données d’historique peuvent s’accumuler dans la base de données qui affectent le débit d’exécution. Recyclage des instances de service permet de libérer des ressources mises en cache, comme la mémoire, les connexions de base de données et les threads. Dans votre environnement de test, vous souhaiterez créer et exécuter la procédure stockée bts_CleanupMsgbox comme décrit dans [comment vider les données manuellement à partir de la base de données MessageBox dans un environnement de Test](http://go.microsoft.com/fwlink/?LinkId=158064) (http://go.microsoft.com/fwlink/?LinkId=158064). Ce script est destiné à votre environnement de test de BizTalk Server de retour à un nouvel état en ce qui concerne la boîte de Message entre les exécutions. Le script supprime toutes les instances en cours d’exécution et toutes les informations sur ces instances, y compris l’état, des messages et des abonnements, mais laisse tous les abonnements d’activation pour ne pas avoir à réinscrire vos orchestrations ou des ports d’envoi. Notez que cet outil n’est pas pris en charge sur les systèmes de production.  
  
-   **Tests de performances et de réglage -** l’objectif de cette catégorie de test consiste à optimiser les performances et le débit de votre application et de trouver le Maximum acceptable débit acceptable de votre système.  Pour plus d’informations sur la planification et de mesure des performances maximales admissibles consultez [planification des performances de débit soutenu](http://go.microsoft.com/fwlink/?LinkId=158065) (http://go.microsoft.com/fwlink/?LinkId=158065) et [Nouveautés des performances durables ?](http://go.microsoft.com/fwlink/?LinkId=132304) (http://go.microsoft.com/fwlink/?LinkId=132304).  
  
     Le débit maximal acceptable est la plus grande charge de messages qu’un système capable de gérer indéfiniment dans un environnement de production. Toutes les applications BizTalk doivent être testées pour des performances et débit avant de passer en production. Au minimum, vous devez exécuter un jeu représentatif de cas de test qui représentent les scénarios d’utilisation les plus courants. Nous vous recommandons de tester des charges attendus et les pointes de charge dans un environnement distinct qui correspond aux caractéristiques de l’environnement de production. Cet environnement doit avoir tous les services d’entreprise standards installé et en cours d’exécution, telles que les agents d’analyse et le logiciel antivirus.  
  
-   Nous vous recommandons également de tester des applications BizTalk sur le même matériel de production en même temps que les autres applications BizTalk qui sont en cours d’exécution. Ces applications BizTalk placer une charge supplémentaire sur BizTalk Server, SQL Server, e/s réseau, les e/s disque. En outre, une application BizTalk peut entraîner une autre limite (lorsque la profondeur du spouleur devient trop importante, par exemple). Toutes les applications BizTalk doivent être de performances / contrainte testé avant de passer en production. En outre, vous devez déterminer le temps pris par le système pour récupérer des pics de charge. Si le système ne récupère pas entièrement à partir d’une charge de pointe avant de la charge maximale suivante se produit, vous avez un problème. Obtenir davantage du système et de retard supplémentaire et ne jamais être en mesure de récupérer entièrement.  
  
## <a name="expectations-throughput-vs-latency"></a>Attentes : le débit et la latence  
 Vous pouvez vous attendre un certain débit ou de temps de latence entre le système déployé. Tente d’atteindre un débit élevé et une faible latence de simultanément place les demandes opposés sur le système. Vous pouvez vous attendre à un débit optimal avec une latence raisonnable. Mesure que le débit, contrainte (par exemple, une consommation plus élevée du processeur, contention d’e/S de disque supérieure, la sollicitation de la mémoire et contention de verrouillage supérieure) sur le système augmente. Cette situation peut avoir un impact négatif sur la latence. Pour découvrir la capacité optimale d’un système, nous vous recommandons d’identifier et de réduire les goulots d’étranglement.  
  
 Les instances terminées résidant dans la base de données peuvent provoquer des goulots d’étranglement. Lorsque les goulots d’étranglement se produisent, les performances peuvent se dégrader. En donnant le système suffisamment de temps pour purger peut aider à résoudre le problème. Découvrir la cause de l’accumulation de retard et aider à résoudre le problème sont important.  
  
 Pour découvrir la cause de la file d’attente, vous pouvez analyser les données historiques et surveiller les compteurs de performances (pour découvrir des modèles d’utilisation et diagnostiquer l’origine de la file d’attente). En règle générale, les retards de traitement peuvent se produire lors du traitement des volumes importants de données par lots, chaque nuit. Vous pouvez s’avérer utile pour détecter la capacité du système et de sa capacité à récupérer à partir d’une file d’attente. Ces informations peuvent vous aider à estimer les besoins en matériel de gestion des scénarios de surcharge et la quantité d’espace de mémoire tampon à prévoir dans un système à gérer les pics imprévus de débit.  
  
 Surveillance des compteurs de performances peut aider à différencier les goulots d’étranglement potentiels susceptibles de survenir lors de l’exécution. Toutefois, lorsque nous pensez que la cause du problème de goulot d’étranglement du processeur ou de la mémoire peut être un des composants personnalisés qui composent la solution, nous fortement vous recommandons d’utiliser les outils de profilage ces profileur Visual Studio ou le profileur ANTS pendant un test de performances Pour affiner et différencier avec certitude de la classe qui génère le problème. Évidemment, le profilage d’une application interfère avec des performances. Par conséquent, ces tests doivent se concentrer sur individuating les composants qui provoquent la consommation de mémoire, l’utilisation du processeur ou la latence et chiffres collectés pendant ces tests doivent être ignorées.  
  
 Le système de réglage pour un débit durable optimal nécessite une profondeur en comprendre le fonctionnement de l’application déployée, des forces et faiblesses du système et les modèles d’utilisation du scénario spécifique. La seule manière de découvrir les goulots d'étranglement et de prévoir avec certitude le débit durable optimal consiste à effectuer un test rigoureux d'une topologie se rapprochant le plus de celle qui sera utilisée en production. Lors de l’exécution de charge et tests de stress par rapport à un certain cas d’usage, isolation des artefacts uniques (emplacements de réception, ports d’envoi, orchestrations) dans les instances d’hôte distinct et en définissant les compteurs de droite à l’intérieur de l’outil Analyseur de performances sont cruciale pour limiter le cause d’un goulot d’étranglement.  
  
 Les autres rubriques de cette section vous guident dans le processus de définition de cette topologie et fournissent des conseils sur la façon de réduire et d’éviter les goulots d’étranglement.  
  
## <a name="scaling"></a>mise à l’échelle  
 Les goulots d’étranglement peuvent se produire à différents stades d’une topologie de déploiement. Certains d'entre eux peut être adressés par l’évolution verticale ou montée en puissance parallèle de l’environnement. L’évolution verticale est le processus de mise à niveau de l’ordinateur existant. Par exemple, vous pouvez mettre à niveau un ordinateur BizTalk Server à partir d’un ordinateur à quatre processeurs à un ordinateur équipé de huit processeurs, ainsi qu’en remplaçant les processeurs existants et en ajoutant davantage de RAM. De cette façon, vous pouvez accélérer les tâches gourmandes en ressources telles que l’analyse et de mappage de document. Montée en puissance est le processus d’ajout de serveurs à votre déploiement. La décision à l’échelle de façon horizontale ou verticale varie selon le type de goulot d’étranglement et de l’application en cours de configuration. Une application doit être générée de toutes pièces pour être en mesure de tirer parti de la mise à l’échelle de façon horizontale ou verticale. Le guide suivant explique comment modifier les topologies de déploiement de matériel basés sur les goulots d’étranglement rencontrés.  
  
 **L’évolution verticale** signifie une solution BizTalk en cours d’exécution mise à niveau matérielle (par exemple, ajout de l’UC et mémoire). Vous devez examiner l’évolution verticale lorsque 1) montée en puissance parallèle est trop cher ou (2) montée en puissance parallèle ne permettra pas de résoudre un goulot d’étranglement. Par exemple, vous pouvez réduire considérablement le temps de transformation et de traitement d’un message volumineux si vous exécutez la tâche sur un ordinateur plus rapide.  
  
 **Montée en puissance** la plate-forme d’application se compose de l’ajout de nœuds de BizTalk pour le groupe BizTalk Server et de les utiliser pour exécuter une ou plusieurs parties de la solution. Vous devez examiner de montée en puissance parallèle lorsque (1) vous devez isoler l’envoi, réception, traitement, le suivi des hôtes ou (2) lors de la mémoire, les ressources d’e/s ou e/s réseau sont surexploités pour un seul serveur. La charge peut être répartie sur plusieurs serveurs. Toutefois, l’ajout de nouveaux nœuds pour le groupe BizTalk Server peut augmenter la contention de verrouillage de la base de données MessageBox.  
  
 Par conséquent, doit évoluer ou monter en charge ? Mise à l’échelle de votre plateforme peut réduire la latence d’une solution BizTalk, car elle rend les tâches uniques (par exemple, mappage des messages) s’exécuter plus rapidement. Montée en puissance parallèle peut améliorer le débit durable maximal et l’évolutivité de votre solution BizTalk, car il permet de répartir la charge de travail sur plusieurs ordinateurs.  
  
## <a name="see-also"></a>Voir aussi  
 [Recherche et suppression des goulots d’étranglement](../technical-guides/finding-and-eliminating-bottlenecks.md)