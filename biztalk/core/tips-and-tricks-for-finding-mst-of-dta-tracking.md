---
title: "Trucs et astuces pour trouver le débit maximal acceptable du suivi DTA | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7d72e4ac-d952-4cff-9a65-491e20945d40
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9faaaf7ebb47ac7ec18d8df6d8cb7c6ebd48d7f8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="tips-and-tricks-for-finding-mst-of-dta-tracking"></a>Conseils et astuces pour trouver le débit maximal acceptable du suivi DTA
Par définition, le débit maximal acceptable permet de reproduire des mesures de performances du système avec une charge constante. La connaissance du débit maximal acceptable est particulièrement utile dans les situations suivantes :  
  
1.  **Lorsque vous avez besoin de la latence la plus faible à partir du système**. Le dépassement du débit maximal acceptable entraîne une accumulation des travaux dans le système, ce qui augmente la latence pour les messages. Même si cette accumulation n'est que temporaire, elle a un effet immédiat et négatif sur la latence. Par conséquent, connaître le débit maximal acceptable de vos systèmes vous indique le débit maximal que vous pouvez espérer atteindre avant que la latence de traitement des différents messages n'augmente dans des proportions considérables (par exemple, de quelques secondes à quelques minutes selon votre configuration).  
  
2.  **Lors de la comparaison avec d’autres systèmes**. Par exemple, si vous souhaitez vérifier que vous atteignez le débit maximal acceptable attendu par rapport à un autre système (par exemple, le scénario de cette rubrique, une étude de cas ou un autre système de votre environnement); la mesure du débit maximal acceptable à l'aide d'une entrée constante offre un standard de comparaison reproductible et non ambigu.  
  
 Il est inutile de préciser que la mesure du débit maximal acceptable peut faire perdre beaucoup de temps. Par conséquent, avant de vous lancer dans un exercice fastidieux de mesure, estimez-en bien les bénéfices potentiels au préalable. La plupart des systèmes de production ne connaissent pas des entrées constantes (comme dans un exercice de mesure du débit maximal acceptable) mais plutôt une variation de charge dans le temps. C'est ce profil de charge qui doit en fin de compte être testé pour certifier un système avant de l'utiliser en production. Heureusement, vous pouvez utiliser la même technique pour mesurer le débit maximal acceptable et pour évaluer la durabilité du profil de charge en production. Il suffit d'exécuter le profil de charge sur une durée suffisante pour pouvoir inclure une ou plusieurs fenêtres de conservation des données de la base de données BizTalkDTADb et observer les indicateurs de performances clés (KPI).  
  
 Il est important de lancer vos tests, qu'il s'agisse de la mesure du débit maximal acceptable ou des profils de charge, sur une base de données BizTalkDTADb vide. Le temps est un facteur crucial pour les données qui sont stockées dans la base de données BizTalkDTADb et, si elles ne sont pas ré-acquises en partant de rien après chaque test, les résultats s'en trouveront faussés. Selon la fenêtre de conservation des données, le temps nécessaire pour obtenir le débit maximal acceptable peut varier considérablement. Pour atténuer cet écart, l'ajustement de la charge « à la volée » en cours de test peut être utile pour amener plus rapidement à zéro le débit maximal acceptable.  
  
 Par exemple, si vous voyez que vous avez dépassé la durée de la première fenêtre de conservation des données et que les indicateurs de performances clés dénotent que vous avez encore de la marge pour augmenter le débit (par exemple, si le temps d'inactivité du disque est encore au-dessus de zéro), vous pouvez augmenter la charge de manière incrémentale et en mesurer les effets. Toutefois, après avoir affiné de cette manière le débit maximal acceptable, il est important d'effectuer un nouveau test en partant avec une base de données BizTalkDTADb vide afin de confirmer votre estimation.  
  
## <a name="recommendations"></a>Recommandations  
 L'architecture du système de suivi de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] permet de suivre une grande variété d'informations et doit être géré et surveillé avec beaucoup de soin. Les facteurs qui influent le plus sur les performances du système, comme indiqués par le débit maximal acceptable, sont les suivants :  
  
-   Le débit souhaité pour le système.  
  
-   Les volume des informations suivies pour chaque message et instance de service du système. Ce volume détermine la vitesse de croissance de la base de données BizTalkDTADb et, en dernier lieu, la fréquence à laquelle la base de données BizTalkDTADb doit être purgée pour éviter de passer au-delà.  
  
-   La durée de conservation des données dans la base BizTalkDTADb, en d'autres termes la fenêtre de conservation des données. Plus la fenêtre est longue, plus la base de données BizTalkDTADb va grossir, ce qui affectera le débit.  
  
-   Le fait que vous archiviez la base de données BizTalkDTADb avant de la purger, ou que vous la purgiez simplement afin de contenir sa taille.  
  
 La procédure de recherche du débit maximal acceptable pour le suivi dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] fait intervenir trois indicateurs de performances clés :  
  
-   Durée d'inactivité du disque physique pour le sous-système de disque du fichier de données DTAdb.  
  
-   Profondeur de spool  
  
-   Profondeur de la base BizTalkDTADbData  
  
 Pour trouver le débit maximal acceptable pour vos systèmes ou confirmer le débit de votre profil de production, surveillez ces indicateurs de performances clés en recherchant notamment :  
  
-   Une profondeur de table trackingdata et de spool stable.  
  
-   Une durée d'inactivité du disque physique pour le sous-système de disque du fichier de données BizTalkDTADb proche de, mais pas « bloquée à » zéro.  
  
 L'utilisation des fonctions de suivi DTA a un impact sur les performances.  Le suivi par défaut peut suivre plus de paramètres que nécessaires une fois qu'une solution est en production, mais il facilite le développement, les tests initiaux et le débogage car les informations permettant de résoudre les problèmes sont plus nombreuses. Nous recommandons par conséquent de conserver le suivi par défaut pendant toute la phase de développement et de test initiale. Lorsque la solution déployée sur BizTalk est stable et prête à recevoir la certification de production, y compris les tests de performances, il est conseillé de vérifier soigneusement la quantité d'informations qui doivent être suivies en production, ainsi que la durée pendant laquelle elles devront être conservées dans la base de données BizTalkDTADb et de les définir en conséquence.  
  
 Par exemple, si les corps de message ne sont pas utiles pour la non-répudiation ou la résolution des problèmes, n'activez pas le suivi du corps des messages. Pour illustrer ce point, dans l’exemple de scénario décrit dans [des scénarios de Test pour la mesure de débit maximal acceptable de données des suivis DTA](../core/test-scenarios-for-measuring-mst-of-dta-tracking.md), lorsque le corps du message suivi de composant de la configuration de suivi a été éliminé, le débit maximal acceptable a doublé pour atteindre 40 messages par seconde.  
  
 Par ailleurs, gardez présent à l'esprit que même si des problèmes se produisent, dans la plupart des cas (mais pas systématiquement), les messages sont suspendus dans la base de données MessageBox et peuvent être récupérés et inspectés sans recourir aux corps de messages suivis.  
  
 Concentrez-vous sur la durabilité de la charge que vous imposez au système:  
  
-   Votre système est-il en mesure de supporter ce profil de charge en production de manière illimitée, même avec les activités de maintenance normales ?  
  
-   Que va-t-il se passer si un événement oblige le système à gérer une accumulation de travaux, par exemple une interruption, planifiée ou non, de la base de données BizTalkDTADb ?  
  
 Ce peut être une bonne idée de fixer des objectifs basés sur les pires scénarios possibles et de les tester. Par exemple, si vous savez qu'un cycle périodique de maintenance est planifié et qu'il nécessitera la déconnexion de la base de données BizTalkDTADb, émulez cette interruption lors d'une phase de test et évaluez la capacité du système à reprendre les opérations normales après l'accumulation de travaux résultante.  
  
## <a name="see-also"></a>Voir aussi  
 [Mesurer le débit de suivi maximal acceptable](../core/measuring-maximum-sustainable-tracking-throughput.md)   
 [Comprendre le comportement de performances de suivi DTA](../core/understanding-dta-tracking-performance-behavior.md)   
 [Scénarios de test pour mesurer le débit maximal acceptable du suivi DTA](../core/test-scenarios-for-measuring-mst-of-dta-tracking.md)   
 [Instructions pour le dimensionnement de la base de données de suivi](../core/tracking-database-sizing-guidelines.md)