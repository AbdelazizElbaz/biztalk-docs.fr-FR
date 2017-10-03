---
title: "Moteur de persistance et durabilité | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9bd209e9-75d2-422f-b3b2-377986f41f2f
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 13f9f3f1a02ddfe84a963704476e867783f31042
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="engine-persistence-and-durability"></a>Persistance et durabilité du moteur
Cette section explique comment BizTalk Server intègre de manière fiable des processus d'entreprise faiblement couplés en stockant l'état de ces processus sur un disque via SQL Server. En assurant la persistance de l'état des processus aux moments opportuns et en exploitant les transactions, le système garantit qu'aucun état de processus n'est perdu, même en cas de panne matérielle ou logicielle. C'est ce que l'on appelle la durabilité du système.  
  
## <a name="loosely-coupled-business-process-management"></a>Gestion des processus d'entreprise faiblement couplés  
 Intégrer des systèmes existants pour exécuter un seul processus d'entreprise logique nécessite de gérer l'état du processus en dehors de ces systèmes. Quelle que soit la durée de vie du processus, l'état de ce processus doit être géré de façon indépendante pour éviter l'explosion des chemins de communication personnalisés que génère un couplage étroit des systèmes.  
  
 De toute évidence, l'état d'un processus d'entreprise en cours d'exécution doit être fiable si le processus remplit une mission stratégique. Afin de garantir la fiabilité et la durabilité des processus d'entreprise, BizTalk se sert des transactions SQL Server pour stocker sur disque l'état de ces processus et les données, dans la base de données MessageBox. Pour plus d’informations sur la base de données MessageBox, consultez [la base de données MessageBox](../core/the-messagebox-database.md).  
  
 Tous les messages et toutes les instances des processus d'entreprise sauf les plus anecdotiques (les instances d'orchestration, par exemple) de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sont transférés vers la base de données MessageBox, une fois au moins pendant le traitement.  
  
## <a name="persistence-and-sustainability"></a>Persistance et viabilité  
 Le fait que BizTalk Server conserve tous les messages et la plupart des orchestrations a un effet direct sur la durabilité tel qu’indiqué à [Nouveautés des performances durables ?](../core/what-is-sustainable-performance.md) Réception de messages dans la base de données MessageBox, ils sont acheminés aux abonnés en attente (par exemple, orchestrations et envoi des ports) et en file d’attente en ou publiées dans des tables SQL messagebox attendre pour que les abonnés les récupèrent et de les traiter. Certains des messages entrants activent de nouvelles instances d'abonnés. D'autres sont acheminés, par corrélation, vers une instance en attente d'un abonné qui s'exécute déjà, telle une orchestration corrélée.  
  
 Pour que les orchestrations corrélées continuent le traitement, les messages corrélés entrants doivent rester non bloqués. BizTalk s'efforce donc de continuer à recevoir les messages (tant ceux qui activent des instances d'abonnés que les messages corrélés), même si la charge système est importante, de sorte que les abonnés en attente de messages corrélés puissent terminer leurs tâches et faire de la place pour l'exécution de processus supplémentaires. Cela signifie que les messages peuvent être reçus plus vite qu'il n'est possible de les traiter et de les supprimer de la base de données MessageBox, où ceux qui ne sont pas encore traités s'accumulent. BizTalk étant une technologie de stockage et de transfert, il est naturel qu'elle fournisse ce type de mise en mémoire tampon ; toutefois, cela peut engendrer des problèmes si le taux de réception est systématiquement plus élevé que le taux de traitement, auquel cas le nombre de messages non traités devient considérable.  
  
 Le contenu de chaque message reçu ou créé dans BizTalk Server ne peut plus être modifié. En outre, les messages reçus peuvent avoir plusieurs abonnés. Chaque abonné à un message particulier référence la même copie unique du message. Si cette approche minimise l'espace de stockage requis, un compteur de référence doit être associé à chaque message et une maintenance doit être effectuée régulièrement pour supprimer les messages dont le compteur de référence indique la valeur 0.  
  
 Si un certain cumul de messages non traités est autorisé dans la base de données MessageBox, les processus de maintenance de cette base (implémentés sous la forme d'un ensemble de travaux SQL) prendront du retard et si aucune possibilité de rattraper ce retard n'est prévue, cela posera des problèmes à terme comme un manque d'espace disque. Pour éviter cela, BizTalk Server propose un mécanisme de limitation qui réduit le taux de réception des messages quand, dans la base de données MessageBox, le nombre de messages non traités atteint un certain niveau (configurable par l'utilisateur). Pour plus d’informations sur la limitation, consultez [optimisation des ressources d’utilisation via la limitation des hôtes](../core/optimizing-resource-usage-through-host-throttling.md).  
  
 Étant donné la diversité des activités et des processus qui contribuent à la viabilité, la principale mesure pour garantir la viabilité dans la durée est d'interdire l'accumulation indéfinie des messages non traités. En d'autres termes, dans la durée, il faut parvenir à un équilibre entre les niveaux de débit de pointe minimal et maximal afin que la base de données MessageBox puisse conserver un volume moyen de messages non traités constant et gérable. Le principal indicateur du nombre de messages non traités est la profondeur de la table de mise en file d'attente, exprimée par un compteur de performance de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] nommé BizTalk:MessageBox:Compteurs généraux:Taille mise en file d'attente. Pour plus d’informations sur ce compteur de performance, consultez [les compteurs de Performance de boîte de Message](../core/message-box-performance-counters.md).  
  
 Pour plus d’informations sur l’utilisation de la taille de la mise en attente et d’autres compteurs pour déterminer le débit maximal, un système peut admettre, consultez [mesure moteur débit maximal](../core/measuring-maximum-sustainable-engine-throughput.md).  
  
## <a name="recommendations"></a>Recommandations  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] conserve tous les messages et la plupart des orchestrations et peut, en l'absence de contrôle, accumuler des messages non traités, ce qui à terme peut créer des problèmes comme un manque d'espace disque. Le principal indicateur du retard est la profondeur de la table du spouleur messagebox, qui est exposée comme un compteur de performances : taille de compteurs : Spool : général de la MessageBox.  
  
 Pour que le débit reste admissible, la taille de mise en file d'attente doit se maintenir à une valeur moyenne stable. En effet, cette taille ne peut pas augmenter indéfiniment sans contrôle. Dans [mesure moteur débit maximal](../core/measuring-maximum-sustainable-engine-throughput.md), ce comportement est décrit plus en détail et une méthode permettant de déterminer le débit maximal, un système peut admettre est fournie, qui tire parti de la taille de la mise en attente et les performances des autres indicateurs.  
  
## <a name="see-also"></a>Voir aussi  
 [Mesurer le débit de moteur maximal acceptable](../core/measuring-maximum-sustainable-engine-throughput.md)   
 [Nouveautés des performances durables ?](../core/what-is-sustainable-performance.md)   
 [Trucs et astuces](../core/performance-tips-and-tricks.md)   
 [Compteurs de Performance de boîte de message](../core/message-box-performance-counters.md)