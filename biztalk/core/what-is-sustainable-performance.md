---
title: "Comment garantir des performances durables ? | Microsoft Docs"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- reliability, sustainable performance
- performance, goals
- performance, sustainable performance
- planning, performance
- performance, planning
- sustainable performance
ms.assetid: 4b18b976-7714-431f-8976-f40a1016d5f3
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 276ce104d8667166d020b33b2f1fb4e7bfb98dbc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="what-is-sustainable-performance"></a>Comment garantir des performances durables ?
Lorsque vous planifiez et évaluez votre système, il est crucial de vous projeter à long terme pour savoir si le système envisagé est durable. Les principaux points à prendre en compte sont les suivants :  
  
-   **Charger les objectifs de performances et des profils**: vous ne pouvez pas trop de détails lorsqu’il s’agit de profils de charge et les objectifs de performances. Le test et l'aptitude à la certification seront basés sur la capacité à gérer ces charges à long terme.  
  
-   **Autres activités et les processus qui sont en concurrence pour les ressources du serveur**: il n’est pas simplement sur la charge de message. D'autres processus et activités, tels que les opérations de maintenance de la base de données et les requêtes exécutées sur MessageBox, ont lieu sur les serveurs. Ils ont une incidence sur les performances.  
  
-   **Planifiés et temps d’arrêt et les interruptions du système**: événements de saturation et de file d’attente permettre modifier le profil de charge efficace de message.  
  
 Lors de la phase d'ébauche de systèmes durables et des tests permettant de les certifier, veillez à prendre ces facteurs en compte.  
  
## <a name="is-your-performance-sustainable"></a>Les performances de votre système sont-elles durables ?  
 En matière de performances, voici ce que nous considérons être des performances durables maximales pour [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] :  
  
-   la charge maximale de flux de messages qu'un système est capable de gérer indéfiniment dans un environnement de  production ;  
  
 Bien que ceci paraisse simple, vous devez considérer de nombreux facteurs au moment où vous évaluez si une solution, s'exécutant sur un ensemble matériel donné, sera capable ou non de supporter les charges quotidiennes une fois que vous l'aurez mise en production.  
  
 Avant de passer à la phase de mise en production, prenez en compte les facteurs suivants pour déterminer si la solution est capable de gérer indéfiniment la charge de flux de messages maximale :  
  
-   les objectifs de performances et profils de débit/latence souhaités ;  
  
-   les autres processus partageant le même matériel, par exemple :  
  
    -   la surveillance et le dépannage courants ;  
  
    -   les opérations de maintenance de la base de données, telles que l'envoi de journaux, la sauvegarde, la purge, la maintenance des index et les mises à jour des statistiques ;  
  
    -   les autres applications ;  
  
-   les temps d'arrêt et les interruptions du système, notamment :  
  
    -   l'arrêt des sites partenaires qui bloque l'envoi et la réception des messages ;  
  
    -   les arrêts périodiques du système pour effectuer la maintenance.  
  
## <a name="know-your-performance-goals"></a>Connaissez-vous bien vos objectifs en matière de performances ?  
 Avant d'évaluer la durabilité de votre solution, vous devez avoir une vision détaillée des objectifs de production attendus. Si l'objectif n'est pas clair, vous ne pouvez pas savoir si la solution envisagée est adéquate. Il est très important que vous fixiez des objectifs de performances clairs, car ceux-ci vont constituer la base de vos stratégies en matière de test et de certification de votre solution. Vos objectifs devraient comporter les éléments suivants :  
  
-   une courbe qui définit les performances en tant que fonction temporelle. Ces fonctions peuvent aller des plus simples au plus complexes ;  
  
-   associer une exigence de performance à la fonction de performance ;  
  
-   une répartition des fichiers par taille et type.  
  
### <a name="example-1"></a>Exemple 1  
  
-   tous les jours, le flux de messages passe de 0 msgs/sec à 8:00 à 80 msgs/sec à midi, puis redescend à 0 msgs/sec à 21:00. La courbe ressemble à une cloche.  
  
-   Le système n'exige aucun délai de latence pour chaque message, cependant il doit être en mesure de traiter cette charge ainsi que tous les messages des jours précédents (par exemple, si le système a subi une interruption de 24 heures) sans prendre de retard.  
  
-   Il existe trois types de document : panier, différé et la demande de Stock. Les paniers ont une taille qui varie entre 2 et 10 kilo-octets et constituent 75 % du total des messages. Les autres types de documents font environ 1 kilo-octet et constituent, respectivement, 10 % et 15 % du reste des messages.  
  
### <a name="example-2"></a>Exemple 2  
  
-   tous les soirs à minuit, un lot de 500 000 messages arrive pour être traité.  
  
-   Tous les messages du lot doivent être entièrement traités dans un délai de 8 heures.  
  
-   Tous les messages sont du même type et sont également répartis en terme de taille (de 10 à 50 kilo-octets, inclus). En outre, le lot contient toujours 10 messages de type catalogue faisant chacun 10 mégaoctets. Pour leur traitement, ils doivent être sous-divisés en entrées de catalogue individuelles.  
  
### <a name="example-3"></a>Exemple 3  
  
-   Sept jours par semaine, 4 000 agents du service clientèle se connectent au système interactif tous les matins à 8:00. Chaque agent effectue en moyenne 4 recherches par minute jusqu'à la fermeture (17:00).  
  
-   Toutes les recherches doivent renvoyer des résultats en moins de 2 secondes.  
  
-   Toutes les recherches sont du même type et sont également réparties en terme de taille (de 500 à 1 000 octets, inclus).  
  
#### <a name="a-performance-requirement-associated-with-the-performance-function"></a>Associer une exigence en matière de performances à une fonction de performance  
 Reprenons les exemples précédents.  
  
-   **Exemple 1 (suite)**: le système ne nécessite aucun délai de latence pour chaque message, mais il doit être en mesure de traiter cette charge, ainsi que tous les messages des jours précédents (par exemple, si une panne système de 24 heures) sans retard.  
  
-   **Exemple 2 (suite)**: tous les messages dans le lot doivent être traités pour la saisie semi-automatique dans les 8 heures.  
  
-   **Exemple 3 (suite)**: toutes les recherches doivent renvoyer des résultats en moins de 2 secondes.  
  
#### <a name="a-distribution-of-file-sizes-and-types"></a>Répartition des fichiers par taille et type  
  
-   **Exemple 1 (suite)**: il existe trois types de document : panier, différé et la demande de Stock. Les paniers ont une taille qui varie entre 2 et 10 kilo-octets et constituent 75 % du total des messages. Les autres types de documents font environ 1 kilo-octet et constituent, respectivement, 10 % et 15 % du reste des messages.  
  
-   **Exemple 2 (suite)**: tous les messages sont du même type et sont réparties entre 10 et 50 kilo-octets, inclus. En outre, le lot contient toujours 10 messages de type catalogue faisant chacun 10 mégaoctets. Pour leur traitement, ils doivent être sous-divisés en entrées de catalogue individuelles.  
  
-   **Exemple 3 (suite)**: toutes les recherches sont du même type et sont réparties entre 500 et 1 000 octets, inclus.  
  
## <a name="accounting-for-other-processes"></a>Prise en compte des autres processus  
 Outre les profils de charge qui transitent directement via le moteur BizTalk, d'autres processus entre en concurrence pour se partager les ressources présentes sur le même matériel.  Ces autres processus réduisent la capacité que le système a à assurer des performances globales durables. La maintenance de la base de données est l'exemple le plus typique de ce genre de processus.  
  
 Toute base de données, qu'elle soit petite ou grande, doit faire l'objet d'opérations de maintenance, telles que l'envoi de journaux, la sauvegarde, l'archivage et la purge. La surveillance et le dépannage sont d'autres exemples d'opérations que vous devez prendre en compte lorsque vous définissez et certifiez un système aux performances durables. Par exemple, les interrogations de la base de données MessageBox (par exemple, par l'intermédiaire de la page Hub du groupe de la console d'administration) réalisées pour connaître le nombre de messages d'un certain type ayant été suspendu au cours des dernières 24 heures font appel à des ressources du serveur SQL Server qui auraient pu être utilisées autrement pour traiter des messages.  
  
 Ci-dessous figure une liste qui répertorie les activités qui ont typiquement le plus d'incidence sur la durabilité globale de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] :  
  
-   **Envoi des journaux et sauvegarde**. dans le cadre de la plupart des plans de récupération d'urgence impliquant SQL Server, vous devez réaliser ces opérations régulièrement sur toutes les bases de données de groupe [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Pour plus d’informations, consultez [sauvegarde et restauration de bases de données BizTalk Server](../core/backing-up-and-restoring-biztalk-server-databases.md). Consultez également [journaux](../core/log-shipping.md).  
  
-   **Archivage et la purge des données de suivi**. En plus du journal expédition et de sauvegarde plan global, la base de données des suivis BizTalk (BizTalkDTADb) a son propre archive et purge régimes ; Pour plus d’informations, consultez [l’archivage et la purge de la base de données de suivi BizTalk](../core/archiving-and-purging-the-biztalk-tracking-database.md). La vitesse à laquelle les données peuvent être archivées et purgées au sein de la base de données des suivis BizTalk est particulièrement importante, car cette base de données constitue généralement un goulot d'étranglement lorsque le suivi est actif.  
  
-   **Requêtes système**. À l’aide des API ou l’interface utilisateur des Console Administration de BizTalk Server pour exécuter des requêtes sur le système affecte les performances durables.  
  
-   **Maintenance de la MessageBox**. diverses tâches SQL font partie de la fonctionnalité centrale de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Celles-ci ont pour but d'assurer la maintenance de la base de données MessageBox en nettoyant les messages et les instances dont le traitement est terminé. La vitesse à laquelle ces tâches peuvent s'exécuter est un facteur clé lors de l'estimation de la durabilité du système. Pour plus d’informations sur ces tâches et leur rôle, consultez [en conservant le serveur1 BizTalk](../core/maintaining-biztalk-server1.md).  
  
-   **Les activités de déploiement de solution**. lorsque vous déployez, liez et démarrez de nouvelles applications ou de nouvelles versions d'applications existantes, vous imposez des charges supplémentaires sur BizTalk, comme la création de nouveaux abonnements aux bases de données MessageBox. Une fois que les applications ont été déployées, elles sont en concurrence avec les messages en cours de traitement pour obtenir des ressources système. Ceci a un impact sur les performances des applications existantes.  
  
 Pour chacun de ces domaines, vous devez demander : quelle est votre recommandation pour minimiser l’impact de ces activités ? Par exemple, devraient-elles s'exécuter à 3:00 du matin ?  
  
## <a name="considering-planned-and-unplanned-outages"></a>Prise en compte des interruptions planifiées ou non  
 L'impact que les interruptions peuvent avoir sur les performances du système varie selon le système. Cependant, les conséquences les plus courantes sont les suivantes :  
  
-   **Événements de saturation**. lorsque les systèmes sont arrêtés pendant une période prolongée, des messages peuvent s'accumuler et arriver tous en même temps pour être traités une fois que les systèmes sont de nouveau opérationnels.  Par exemple, si une application  qui s'exécute sur BizTalk reçoit des messages via MSMQ, et qu'elle est momentanément arrêtée, des messages peuvent s'accumuler dans les files d'attente. Lorsque l'application est redémarrée, c'est comme si un grand nombre de messages arrivait tous en même temps.  
  
-   **Messages en souffrance**. lorsque les systèmes destinataires des messages sont arrêtés, un cycle de tentatives a généralement lieu. Ce cycle utilise des ressources supplémentaires. Au terme du cycle, les messages sont en général suspendus. Lorsque les systèmes reviennent en ligne, ils sont parfois inondés si un volume important de messages peut alors être à nouveau traités et/ou envoyés correctement.  
  
 Il est évident que vous devez prendre en compte les interruptions planifiées, telles les opérations de maintenance lorsque vous concevez et certifiez un système. Nous vous recommandons également d'analyser les interruptions non planifiées ainsi que leurs conséquences.  
  
 Vous aurez une meilleure idée du type de capacité système voulu en identifiant les types d'interruptions pouvant se produire, en les classant par niveau de risque (à savoir, la probabilité de la gravité), en évaluant leur durée et incidence (par exemple, les événements de saturation, le volume de messages suspendus et en souffrance, etc.) pour les interruptions qui présentent le plus de risque. Tout système de stockage-transfert basé sur une messagerie, tel que [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], devrait être conçu avec une marge suffisante pour supporter les interruptions planifiées et non planifiées.  
  
## <a name="see-also"></a>Voir aussi  
 [La durabilité et la persistance du moteur](../core/engine-persistence-and-durability.md)   
 [Des recommandations par Phase de planification de projet](../core/project-planning-recommendations-by-phase.md)   
 [Mesurer le débit de moteur maximal acceptable](../core/measuring-maximum-sustainable-engine-throughput.md)   
 [Mesurer le débit de suivi maximal acceptable](../core/measuring-maximum-sustainable-tracking-throughput.md)   
 [Mise à l’échelle de vos Solutions](../core/scaling-your-solutions.md)   
 [Identification des goulots d’étranglement de performances](../core/identifying-performance-bottlenecks.md)   
 [Capacité et performances du moteur](../core/engine-performance-and-capacity.md)