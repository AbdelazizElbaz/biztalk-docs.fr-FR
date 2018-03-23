---
title: Surveiller l’intégrité et les performances à l’aide des outils intégrés | Documents Microsoft
description: Disponibilité, intégrité et performances, analyse des tâches dans BizTalk Server et l’analyse de l’Agent SQL
ms.custom: ''
ms.date: 01/14/2016
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 96e244dc-b826-4a9f-a4e1-6dabc41eb144
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e6652c962d8ef522128dfb4c9febeca55ce42669
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/23/2018
---
# <a name="monitoring-biztalk-server"></a>Analyse de BizTalk Server
L'analyse régulière de votre infrastructure et de vos applications BizTalk Server ainsi que la résolution des problèmes détectés vous permettent d'assurer la disponibilité de vos applications BizTalk Server auprès de vos utilisateurs. L'objectif de cette analyse est de réduire au minimum la durée pendant laquelle une exception n'est pas détectée et, par conséquent, non résolue. Par ailleurs, cette analyse vous permet également de détecter des situations susceptibles de provoquer une exception.  
  
 Lors de l'analyse de BizTalk Server, vous devez rechercher tout comportement inattendu ou anormal. L'analyse peut s'effectuer dans le cadre d'un processus manuel ou automatique. Vous pouvez analyser le fonctionnement de votre infrastructure BizTalk Server à l'aide de la console Administration de BizTalk Server. Celle-ci permet d'analyser le fonctionnement de vos applications BizTalk Server et de procéder à une analyse de la cause profonde afin d'identifier la cause sous-jacente des problèmes. . Lors de l'analyse de BizTalk Server, gardez les points suivants à l'esprit :  
  
-   Votre infrastructure peut fonctionner normalement, mais ce n'est pas nécessairement le cas de vos applications (par exemple, elle reçoivent des messages non valides et ne parviennent pas à les traiter).  
  
-   Votre infrastructure peut ne pas fonctionner normalement, alors que vos applications peuvent s'exécuter sans problème (par exemple, en cas de panne d'un serveur, mais que le nombre de serveurs affectés à l'hôte est suffisant pour gérer la charge).  
  
-   Un problème d'infrastructure peut apparaître sous la forme d'un problème d'application (par exemple, les messages ne sont pas traités assez rapidement car le serveur est en panne).  
  
 L'analyse de votre serveur BizTalk Server et de vos applications concerne trois aspects :  
  
-   analyse de la disponibilité ;  
  
-   analyse du fonctionnement ;  
  
-   analyse des performances.  
  
## <a name="availability-monitoring"></a>Analyse de la disponibilité  
 L'analyse de la disponibilité répond à la question suivante : l'indisponibilité d'une ressource système ou d'application empêche-t-elle vos applications BizTalk Server de fonctionner de manière optimale ? Ces problèmes concernent presqu'exclusivement le système, tels que la disponibilité des services et des connexions. Par exemple, si un adaptateur échoue suite à l'arrêt du service d'authentification unique de l'entreprise, il s'agit d'un problème de disponibilité. Si l'un des serveurs affectés à un hôte a échoué et que votre application prend du retard dans le traitement des messages, il s'agit également d'un problème de disponibilité. De même, si une application est arrêtée et ne parvient pas à traiter les messages, il s'agit d'un problème de disponibilité. Le tableau suivant présente les outils d'analyse de la disponibilité.  
  
|Outil|Tâche|  
|----------|----------|  
|Console Administration de BizTalk Server|La page Hub du groupe de la console Administration de BizTalk Server vous permet de vérifier si des applications ou leurs composants (ports/orchestrations) sont arrêtés.|  
|Observateur d'événements|Cet outil vous permet de recherchez les problèmes de connexion des adaptateurs, les services arrêtés, etc.|  
  
## <a name="health-monitoring"></a>Analyse du fonctionnement  
 L'analyse du fonctionnement répond à la question suivante : mes applications ou ressources fonctionnent-elles de manière inappropriée ? Par exemple, mes applications ou les artefacts qui les composent présentent-ils des conditions d'exception ? Ou bien, des messages sont-ils suspendus en raison de données non valides dans la charge de message ? Le tableau suivant présente les outils d'analyse du fonctionnement.  
  
|Outil|Tâche|  
|----------|----------|  
|Outil de BizTalk Health Monitor (BHM)|Un composant logiciel enfichable MMC pour les utilisateurs à surveiller l’intégrité des environnements de BizTalk Server, détecter les problèmes critiques et non critiques et exécuter des tâches de maintenance.  [Télécharger BizTalk Health Monitor](https://www.microsoft.com/download/details.aspx?id=43716).|  
|Console Administration de BizTalk Server|Les pages de requête et Hub du groupe de la console Administration de BizTalk Server vous permettent d'identifier les problèmes de fonctionnement des applications et d'analyser leur(s) cause(s).|  
|Observateur d'événements|Cet outil vous permet de détecter les problèmes qui surviennent pendant le traitement des messages et des orchestrations.|  
  
## <a name="performance-monitoring"></a>Analyse des performances  
 L'analyse des performances répond à la question suivante : le système exécute-t-il ses tâches de manière efficace ? Ce type d'analyse se concentre essentiellement sur la charge des ressources physiques telles que les bases de données et les disques. Par exemple, si l'utilisation de l'UC est constamment entre 90 et 100 % et qu'une accumulation des messages se forme, il s'agit d'un problème de performance de l'ordinateur. Le tableau suivant présente les outils d'analyse des performances.  
  
|Outil|Tâche|  
|----------|----------|  
|Analyseur de requêtes SQL|Cet outil vous permet d'analyser le contenu et la taille des bases de données afin de diagnostiquer les problèmes système.|  
|Console Administration de BizTalk Server|La page Hub du groupe affiche des indicateurs de performance clés (KPI) tels que le nombre d'instances de service actuellement actives, mises en attente, exécutables, planifiées, suspendues, etc. dans vos applications BizTalk Server.|  
|BAM (Business Activity Monitoring)|Vous pouvez spécifier des étapes spécifiques dans votre processus de suivi des indicateurs de performance clés pertinents pour votre application.|  
  
## <a name="biztalk-server-monitoring"></a>Surveillance de BizTalk Server  
 Vous pouvez exécuter la **analyser BizTalk Server** travail Agent SQL pour identifier des problèmes connus dans les bases de données de gestion, MessageBox ou DTA. La fonction est créée lorsque vous configurez un groupe BizTalk dans la console Administration de BizTalk Server ou procédez à une mise à niveau de BizTalk à partir d'une version antérieure.  
  
 La fonction Analyser BizTalk Server recherche les problèmes suivants dans les bases de données Gestion, MessageBox ou DTA :  
  
> [!NOTE]
>  La fonction Analyser BizTalk Server recherche uniquement d'éventuels problèmes. Elle ne corrige pas les problèmes trouvés.  
  
-   Messages sans références  
  
-   Messages sans nombres de références  
  
-   Messages avec un nombre de références inférieur à 0  
  
-   Références de messages sans lignes de mise en file d'attente  
  
-   Références de messages sans instances  
  
-   État d'instance sans instances  
  
-   Abonnements d'instance sans instances correspondantes  
  
-   Instances de service DTA orphelines  
  
-   Exceptions d'instances de service DTA orphelines  
  
-   Le service TDDS ne s'exécute sur aucune instance de l'hôte lorsque l'option de suivi global est activée.  
  
 La fonction Analyser BizTalk Server est configurée et automatisée pour s'exécuter une fois par semaine. Comme l'exécution de la fonction nécessite une capacité de calcul importante, nous vous recommandons de la planifier pendant des périodes de temps d'arrêt ou de faible trafic.  
  
 L'exécution de la fonction échoue si elle rencontre des problèmes ; une chaîne contient le nombre de problèmes trouvés. Sinon, elle réussit. Vous pouvez voir les détails dans l'historique de la fonction. Si vous exécutez la fonction avec des privilèges d'administrateur, une chaîne d'erreur est également consignée dans l'Observateur d'événements (avec l'historique de la fonction).  
  
## <a name="troubleshooting"></a>Dépannage  
 Une fois informé de l'existence d'un problème de fonctionnement de vos applications BizTalk Server (et non pas de votre infrastructure), utilisez les pages de requête et Hub du groupe de la console Administration de BizTalk Server pour analyser celui-ci. Cette console permet de procéder à la configuration intégrée, au déploiement, ainsi qu'au dépannage de vos applications, et de résoudre les problèmes relatifs à la configuration et au déploiement une fois ceux-ci identifiés. Généralement, la plupart des problèmes d'application sont dus au fait que les messages ne sont pas traités comme prévu (cela peut se manifester par des instances de service suspendues, la relance des ports, des instances mises en attente qui n'ont pas été réactivées, etc.).  
  
 Vous pouvez utiliser la page Hub du groupe et les pages de requête pour regrouper vos instances de service (quel que soit leur état : en cours d’exécution, suspendu, en attente, etc.) par Application, type d’erreur, Type de Service, hôte, etc., pour isoler les différentes erreurs, recherchez un par un et corriger les. Vous pouvez également analyser les données de suivi via la console Administration de BizTalk Server afin d'analyser l'historique d'un flux de messages ou celui d'un ensemble d'orchestrations ou de règles. Ces données de suivi contiennent des données historiques sur vos applications BizTalk Server.  
  
 Si vous avez activé le suivi dans la console Administration de BizTalk, le suivi vous permet de localiser le flux de messages et les instances de service à l'aide d'une requête. Cela s'avère particulièrement utile si vous souhaitez localiser un message et que, par exemple, vous connaissez uniquement son type (schéma), une propriété et sa valeur (par exemple, nom de client), etc.  
  
 Les rubriques suivantes portent sur l'analyse et le dépannage à l'aide de la console Administration de BizTalk Server, de la page Hub du groupe et des pages de requête. Cette section porte également sur le suivi vous permettant d'analyser la cause profonde et de résoudre les problèmes.  
  
## <a name="more-good-stuff"></a>Autre contenu intéressant  
  
-   [Utilisation de la console Administration de BizTalk Server](../core/using-the-biztalk-server-administration-console.md)  
  
-   [Affichage des messages suivis et les données d’Instance](../core/viewing-tracked-message-and-instance-data.md)  
  
-   [Surveillance des solutions EDI et AS2](../core/monitoring-edi-and-as2-solutions.md)  
  
-   [Suivi des dépendances entre les artefacts dans une application BizTalk Server](../core/tracking-dependencies-between-artifacts-in-a-biztalk-server-application.md)

- [Compteurs de performance](performance-counters.md)