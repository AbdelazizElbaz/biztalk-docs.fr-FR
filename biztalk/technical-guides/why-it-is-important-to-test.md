---
title: Pourquoi il est Important de Test | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ce91aca5-56d3-4fb8-abe2-af0039804706
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 433a5de8d1f90c02c5b06287252b49fd7209e07b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="why-it-is-important-to-test"></a>Pourquoi il est Important de Test
Cette rubrique fournit une vue d’ensemble de l’état d’esprit qui conduit au test insuffisantes, décrit les risques liés à l’échec tester des solutions BizTalk et l’oppose les pièges de tests manuels avec des avantages des tests automatisés.  
  
## <a name="testing-as-overhead"></a>Test en tant que « surcharge »  
 Malheureusement, avec croissants demandes pour un retour sur investissement (ROI), la phase de test d’un projet est souvent perçue comme un des aspects première d’un plan de projet qui peuvent être mis à l’arrière.  
  
 Un argument sur le test des solutions BizTalk est que « nous n’avez pas besoin tester notre solution, car Microsoft teste comprenez-vous déjà BizTalk Server. » S’il est vrai que Microsoft teste soigneusement de BizTalk Server, différents scénarios d’utilisation l’exiger un numéro d’innombrables presque de permutations de besoins de débit, haute disponibilité, l’utilisation de la carte, la latence, le suivi des exigences, utilisation de l’orchestration et le code personnalisé. Étant donné que BizTalk Server est très flexible et peut prendre en charge les nombreux différents scénarios d’utilisation, il est tout simplement pas possible à prévoir et à tous les tests. En outre, les paramètres par défaut qui sont appliqués dans un environnement BizTalk Server doivent être optimisés pour prendre en charge chaque scénario d’utilisation. La seule façon de déterminer les paramètres optimaux pour un scénario d’utilisation particulier consiste à tester la solution, différents paramètres de mesures, paramétrer l’environnement et testez à nouveau. Envisagez le diagramme suivant, qui illustre un exemple d’architecture physique d’une solution BizTalk Server.  
  
 ![Architecture d’un déploiement de BizTalk Server](../technical-guides/media/5359cf00-e285-4168-a988-8d3b677eb6ba.gif "5359cf00-e285-4168-a988-8d3b677eb6ba")  
Exemple d’Architecture BizTalk physique  
  
 Vous pouvez voir dans le diagramme ci-dessus que la solution BizTalk Server contient de nombreux éléments, y compris plusieurs ordinateurs exécutant BizTalk Server, les ordinateurs exécutant SQL Server, les nœuds de cluster de serveurs et les domaines Active Directory. Une fois que le système est en cours d’exécution, il y aura plusieurs ajustements de configuration appliquées pour optimiser l’application par les besoins de l’entreprise, pour optimiser le retour sur investissement globale de la solution. Ce scénario unique montre qu’il existe plusieurs variables en lecture. Outre l’architecture physique de l’environnement, envisagez le diagramme suivant, qui illustre le flux d’un message via BizTalk Server.  
  
 ![Flux d’un message via BizTalk Server](../technical-guides/media/dea79a42-5f60-49a1-abdb-870988784ffe.gif "dea79a42-5f60-49a1-abdb-870988784ffe")  
Flux de Message BizTalk logique d’exemple  
  
 Lorsque vous examinez le diagramme logique d’un message acheminées dans BizTalk Server, nous voyons les autres variables qui nécessitent le projet de test, y compris personnalisé d’envoyer et de recevoir des composants de pipeline et les classes personnalisées qui peuvent être appelées à partir d’orchestrations BizTalk. Étant donné que la complexité de type et l’utilisation des composants personnalisés et des composants de BizTalk varie d’un projet, il devient plus clairement pourquoi il est important de réaliser des tests pour chaque scénario d’utilisation spécifiques.  
  
## <a name="testing-methodology-and-timelines"></a>Chronologies et méthodologie de test  
 Pour garantir le test est effectué efficacement, l’atelier de test doit être entièrement automatisée qu’il est donc facilement reproductible et réduit le risque d’erreur humaine. En outre, il convient d’attribuer suffisamment de temps lors de la planification du projet de test. Une approche minimaliste au test comprend des étapes manuelles semblables au suivant :  
  
1.  Charger manuellement un ou plusieurs messages à un point de terminaison de réception, telles que la suppression de fichier ou à l’aide d’un client SOAP pour appeler un service Web.  
  
2.  Valider manuellement le contenu et la structure d’un message. Étant donné que plusieurs schémas figurent souvent dans un projet, les messages peuvent être un mélange de fichier plat et XML et peuvent également contenir des dépendances de champ croisé.  
  
    > [!NOTE]  
    >  Un exemple serait tout projet impliquant des messages SWIFT. Il s’agit de messages de fichier plat qui ont des dépendances de champ croisé. Autrement dit, valeur un champ la dépend d’un autre – simple validation XSD ne produit pas. Par conséquent, l’accélérateur SWIFT utilise le moteur de règles BizTalk pour la validation des messages. Pour plus d’informations sur la [SWIFT accélérateur](http://go.microsoft.com/fwlink/?LinkID=79657), consultez [SWIFT accélérateur](http://go.microsoft.com/fwlink/?LinkID=79657) (http://go.microsoft.com/fwlink/?LinkID=79657).  
  
3.  Vérifier manuellement les journaux des événements sur les ordinateurs BizTalk Server pour les erreurs.  
  
4.  Vérifier manuellement les bases de données BAM (si utilisé) pour valider que les informations d’activité sont enregistrées correctement.  
  
 À l’aide d’un processus manuel comme décrit ci-dessus pour le test est subjective et sujet aux erreurs. Envisagez d’avoir à examiner des messages de ligne de cent SWIFT avec des dépendances de champ 10 différents cas de test entre. Projet de la plupart des développeurs ne serait pas en mesure d’ou même si elles n’ont pas pu, ne seraient pas subir de s’engager dans une telle tâche, avec précision et de manière fiable. Implémentation d’une erreur subjective, manuelle, test susceptible d’engendrer des processus augmente le risque d’un projet et augmente la probabilité de défaillance.  
  
 Les risques de défaillance sont souvent amplifié par chronologies qui n’intègrent pas de suffisamment de temps pour le test de la planification du projet. Trop souvent, un projet de test charnières de stratégie sur un passage unique de test manuel qui est planifiée pendant une semaine ou, avant la date de mise en production. Ces tests limités de place le projet exposés. Étant donné une chronologie limitée de ce type de test, si des problèmes sont détectés, puis le projet peut être différé, car aucun temps n’a été alloué pour résoudre les problèmes. En outre, si un problème est détecté et résolu, il est possible d’effectuer les tests suivants avant que le système ne fonctionne pas suffisamment de temps.  
  
 La réalité de « version finale unique, passe de test unique, prenez le projet live » le test est qu’elle entraîne souvent dans le projet retardé, le projet dépasse le budget ou pire, le projet échoue complètement ! Pour les systèmes essentiels, ce type de méthodologie de test est un incident en attente de se produire.  
  
## <a name="testing-effectively-and-efficiently"></a>Efficacement et de test  
 Étant donné que le test approprié est souvent considéré comme un luxe coûteuse au lieu d’une exigence intégrale, il est trop souvent ajouté à la fin d’un projet. Étant donné la complexité de la pile de logiciels et matériels utilisée dans les environnements d’entreprise hétérogènes, cette approche est irréaliste. Implémentation d’une approche de test automatisé qui peut être réexécutée sur la demande est la meilleure façon de tester efficacement et est un composant intégral de projets réussies d’apporter un retour sur investissement excellent pour l’entreprise. En faisant l’acquisition au début du projet dans les tests fonctionnels de bout en bout complète pour chaque chemin d’accès du code via le système vous générez des ressources de test. Ces ressources nécessitent un investissement (c'est-à-dire le temps de développement) afin de profiter des avantages d’augmenter l’efficacité de test ultérieurement. Pour minimiser l’investissement nécessaire à partir du projet pour dériver une telle infrastructure nous vous recommandons d’utiliser l’infrastructure de test de charge de Visual Studio 2010. Visual Studio 2010 inclut la plupart des étapes de tests communes requis pour le test réussit et l’infrastructure utilisée dans les scénarios de test présentés plus loin dans ce guide.  
  
## <a name="see-also"></a>Voir aussi  
 [Implémentation d’un test automatisé](../technical-guides/implementing-automated-testing.md)