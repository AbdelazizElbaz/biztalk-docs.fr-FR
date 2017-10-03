---
title: "Montée en charge des bases de données | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- performance, databases [BAM]
- databases [BAM], high availability
- Archive database [BAM]
- Analysis database [BAM], high availability
- high availability, databases [BAM]
- MessageBox database, master database
- scaling, databases [BAM]
- scaling, BizTalk Server
- MessageBox database, multiple databases
- MessageBox database, clustering
- databases [BAM], scaling
- MessageBox database, routing
- Tracking database, scaling
- Primary Import database [BAM], clustering
- high availability, MessageBox database
- databases [BAM], performance
- Star Schema database [BAM]
- MessageBox database, high availability
- messages, disabling
- MSMQT adapters, See MSMQ adapters
- clustering, Analysis database [BAM]
- Windows Message Queuing
- MessageBox database
- Analysis database [BAM], clustering
- DTS packages, scheduling
ms.assetid: e02edc0d-1c51-4b97-be04-0feb787089ac
caps.latest.revision: "33"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0af465c1cd77bfb96cc44e1a3209757ee13129be
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="scaled-out-databases"></a>Bases de données mises à l'échelle
Pour obtenir des bases de données [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] à haute disponibilité, configurez deux ordinateurs exécutant SQL Server dans un cluster Windows. Ces ordinateurs peuvent fonctionner selon une configuration actif/actif ou actif/passif pour la redondance et stocker les données sur un disque partagé tel qu'une baie de stockage RAID 1+0 SCSI ou un SAN (Storage Area Network).  
  
 Si, pour quelque raison que ce soit, le service de SQL Server est indisponible, le cluster de la base de données transfère les ressources de l'ordinateur actif vers l'ordinateur passif. Lors de ce processus de basculement, les instances du service BizTalk Server rencontrent des problèmes de connexion aux bases de données et relancent automatiquement ces connexions. L'ordinateur contenant la base de données indemne (ordinateur jusqu'alors passif) commence à traiter les connexions de la base de données après avoir pris en charge les ressources durant le basculement.  
  
## <a name="running-multiple-messagebox-databases"></a>Exécution de plusieurs bases de données MessageBox  
 Pour renforcer l'évolutivité des bases de données [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], vous pouvez configurer BizTalk Server de sorte qu'il stocke les données sur plusieurs bases de données MessageBox. Vous créez la première base de données MessageBox lorsque vous exécutez l'Assistant Configuration. Cette base de données est la base de données principale MessageBox. Il existe une seule base de données principale MessageBox dans votre déploiement BizTalk Server. Elle contient les informations d'abonnement principal et achemine les messages vers la base de données MessageBox appropriée. En règle générale, vous souhaitez allouer la MessageBox principale pour effectuer un routage uniquement (sélectionnez **désactiver la publication des nouveaux messages**) et laisser les autres bases de données MessageBox effectuent le traitement.  
  
 Lorsque la base de données principale MessageBox reçoit un nouveau message d'activation (une nouvelle instance d'un processus d'entreprise ou un message d'abonnement), elle l'envoie à la première base de données MessageBox disponible. Par exemple, lorsque vous disposez d'une base de données principale MessageBox et de deux bases de données secondaires, la base de données principale achemine le premier message d'activation vers la base de données secondaire n° 1, le second vers la base de données n° 2, le troisième vers la base de données n° 1 et ainsi de suite de manière alternée. La base de données principale utilise une logique intégrée pour équilibrer la charge et n'a donc pas besoin d'autre mécanisme d'équilibrage de charge.  
  
 Une fois que la base de données principale MessageBox a acheminé le message d'activation vers une base de données secondaire (la première, par exemple), le processus d'entreprise est mis en mémoire et exécuté. Si le processus d’entreprise doit attendre un message et le temps d’attente est plus long que quelques secondes, le processus d’entreprise est rendue persistante dans la base de données MessageBox 1. Le processus d’entreprise est en attente d’un message de corrélation. Lorsque le message de corrélation arrive dans la base de données MessageBox principale, il recherche la base de données MessageBox contenant l'état du message de corrélation (dans cet exemple, la base de données MessageBox n° 1). La base de données principale MessageBox transmet ensuite le message à la base de données MessageBox contenant le processus d'entreprise. Ce processus est ensuite remis en mémoire pour continuer le traitement jusqu'à sa fin ou jusqu'à ce qu'il se trouve en attente du prochain message de corrélation.  
  
 BizTalk Server stocke l'intégralité des états dans les bases de données MessageBox qui contiennent toutes les informations d'état des différents processus d'entreprise. Pour une fiabilité accrue, vous devez mettre en cluster toutes les bases de données MessageBox, qu'il s'agisse de la base de données principale ou des bases secondaires.  
  
 Pour configurer plusieurs bases de données MessageBox, vous utilisez la console Administration de BizTalk pour ajouter les ordinateurs exécutant SQL Server. D'un point de vue administrateur, vous devez juste ajouter les nouvelles bases de données MessageBox. BizTalk Server gère automatiquement la distribution alternée des messages d'activation et l'envoi des messages de corrélation aux bases de données MessageBox appropriées.  
  
 Si vous configurez plusieurs bases de données MessageBox dans votre environnement, vous devez créer au moins trois bases de données MessageBox pour le groupe BizTalk Server et désactiver la publication des messages pour la base de données principale MessageBox. Cette recommandation s'explique par le fait que l'ajout de bases de données MessageBox entraîne une charge supplémentaire pour la base de données principale en matière d'acheminement des messages entre les différentes bases de données. Si vous configurez uniquement deux bases de données MessageBox, la plus grande partie du bénéfice obtenu suite à l'ajout d'une base de données se perd dans l'acheminement des messages par la base de données principale MessageBox.  
  
## <a name="providing-high-availability-for-multiple-messagebox-databases"></a>Configuration de la haute disponibilité pour plusieurs bases de données MessageBox  
 En ajoutant des bases de données MessageBox à votre déploiement [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], vous améliorez son évolutivité sans pour autant le rendre hautement disponible. En effet, chaque base de données MessageBox, unique et indépendante, constitue un point faible potentiel pour votre environnement BizTalk Server. Afin d'obtenir une redondance renforcée, vous devez configurer un cluster de serveurs pour chaque base de données MessageBox. BizTalk Server répartit les données entre les différentes bases de données MessageBox si bien que ces dernières sont incapables de partager les données et de fournir une redondance sans mise en cluster du serveur.  
  
## <a name="providing-high-availability-for-the-biztalk-tracking-database"></a>Configuration de la haute disponibilité pour la base de données des suivis BizTalk  
 Selon les besoins de votre déploiement, il se peut que vous vouliez améliorer les performances du suivi en isolant la base de données des suivis BizTalk sur un ordinateur SQL Server distinct et en créant un hôte BizTalk séparé, consacré au suivi des hôtes. Si votre déploiement implique un débit élevé et un suivi pour des données de message très nombreuses, la surcharge de travail due au suivi est susceptible d'utiliser énormément de ressources sur l'ordinateur SQL Server. Si tel est le cas et qu'un grand nombre de messages entrants continuent d'être reçus, il peut arriver que [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ne puisse plus traiter les nouveaux messages, car la quantité des ressources nécessaires au suivi de ces messages est supérieure aux ressources requises pour l'exécution des autres composants BizTalk Server (composants de réception des messages et de conservation de ceux-ci dans une base de données MessageBox par exemple).  
  
 Afin d'améliorer les performances et la sécurité de votre déploiement, il est recommandé de consacrer un hôte ne contenant aucun autre élément (emplacements de réception, orchestrations, pipelines, etc.) au suivi et de désactiver le suivi dans les hôtes de réception, de traitement et d'envoi. Pour rendre l'hôte de suivi hautement disponible, créez plusieurs instances pour cet hôte.  
  
 Pour chaque base de données MessageBox, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] utilise uniquement une instance de l'hôte de suivi afin de placer les messages de la base de données MessageBox dans la base de données des suivis BizTalk (BizTalkDTADb). Lorsque des ordinateurs supplémentaires exécutent des instances de l'hôte des suivis, BizTalk Server met automatiquement à l'échelle la gestion de chaque base de données MessageBox en la transférant à une instance de l'hôte de suivi distincte. Si le nombre de bases de données MessageBox est supérieur au nombre d'instances de l'hôte de suivi, une ou plusieurs instances de l'hôte de suivi fonctionnent pour plusieurs bases de données MessageBox.  
  
 Pour disposer de bases de données des suivis BizTalk hautement disponibles, servez-vous du clustering Windows et configurez deux ordinateurs dédiés aux bases de données et fonctionnant sous SQL Server sur un modèle de type actif/passif.  
  
## <a name="providing-high-availability-for-the-bam-databases"></a>Configuration de la haute disponibilité pour des bases de données BAM  
 L'analyse BAM assure la visibilité des processus d'entreprise indépendamment de l'implémentation informatique ou par le biais d'une implémentation informatique hétérogène. Les bases de données SQL Server BAM (schémas en étoile BAM, importation principale BAM et archives BAM) et Analyse BAM conservent les données de l'activité de l'entreprise lorsqu'elles sont différentes des données d'analyse opérationnelle. Afin de vous assurer que votre infrastructure BAM est hautement disponible, procédez comme suit :  
  
-   **Mettre en cluster la base de données d’importation principale BAM et de la base de données analyse BAM.** La base de données d'importation principale BAM constitue le cœur du système BAM (Business Activity Monitoring). Il est donc important qu'elle soit hautement disponible par le biais du clustering Windows et que vous respectiez bien les deux recommandations suivantes afin d'éviter qu'elle n'arrive à saturation. La base de données Analyse BAM est une base de données Analysis Services stockant les données et dont les analystes d'entreprise se servent pour créer des agrégations d'activité et des cubes OLAP. Tout temps d'arrêt de cette base de données a donc des conséquences sur la productivité. Il n'est pas nécessaire de mettre en cluster la base de données des archives BAM, mais il est recommandé de vérifier que le journal des événements ne contient pas d'erreur lorsque les lots DTS (Data Transformation Services) sont en cours d'exécution. Ainsi, vous pouvez vous assurer que les données ont été correctement transférées et contrôler la taille de la base de données afin de la remplacer dans le cas où elle serait arrivée à saturation.  
  
-   **Définissez une fenêtre en ligne.** Afin de disposer de performances élevées et d'éviter les temps d'arrêt, BAM partitionne les données de la base d'importation principale en tables selon la date et l'heure de fin d'activité. Le composant BAM réalise cette opération en remplaçant régulièrement la table remplie par une table vide de format identique. Les activités supplémentaires terminées sont ensuite placées dans la nouvelle partition (table) tandis que l'analyse BAM conserve les anciennes partitions pendant la période indiquée dans la fenêtre en ligne. Il faut définir une telle fenêtre afin de vous assurer que le nombre de partitions de la base de données d'importation principale BAM ne devient pas trop important. Pour plus d'informations sur la planification des fenêtres en ligne, consultez la rubrique « Archivage des données dans la base de données d'importation principale » de l'aide de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
-   **Planifier les packages DTS pour s’exécuter périodiquement.** La définition d'une fenêtre en ligne garantit que votre base de données d'importation principale BAM n'arrive pas à saturation à cause d'anciennes partitions d'activité. Vous devez également planifier une exécution régulière des lots DTS afin de créer une nouvelle partition pour les données d'activité et pour placer les données provenant d'anciennes partitions de la base de données d'importation principale BAM dans la base de données des archives BAM. Pour plus d'informations sur la planification des lots DTS, consultez la rubrique « Planification des lots DTS » de l'aide de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
-   **Soigneusement sélectionner de petits ensembles d’éléments de données (points de contrôle) et évitez d’inclure des éléments de données inutiles lors de la définition d’une activité.**  
  
-   **Comprendre les compromis entre les agrégations planifiées et en temps réel lorsque vous concevez vos agrégations.** Les agrégations RTA sont gérées de façon automatique par les déclencheurs SQL Server et ne rencontrent aucune latence. Ce type d'agrégation est idéal dans des scénarios où la faible latence est essentielle. Cependant, il entraîne une baisse des performances chaque fois que des événements sont écrits dans la base de données d'importation principale BAM. Pour mettre à jour leurs données, les agrégations planifiées s'appuient sur la création planifiée des cubes pour les lots DTS. Leur temps de latence est supérieur ou égal à l'intervalle de planification DTS, mais leur impact global sur les performances de la base de données d'importation principale BAM est moins important.  
  
-   **Si vous choisissez d’agrégations planifiées, assurez-vous que vous planifiez pour les cubes DTS pour exécuter plus fréquemment que les DTS d’archivage.** En effet, les DTS d'archivage ne placent pas les données d'activité passées par un processus d'agrégation planifiée dans la base de données des archives BAM.  
  
-   **Activer le Service de Bus d’événements de BAM sur plusieurs ordinateurs obtenir des fonctionnalités de basculement.**  
  
## <a name="providing-high-availability-for-the-other-biztalk-server-databases"></a>Configuration de la haute disponibilité pour les autres bases de données BizTalk Server  
 Pour obtenir d'autres bases de données [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] à haute disponibilité, configurez deux ordinateurs exécutant SQL Server dans un cluster Windows. Ces ordinateurs peuvent fonctionner selon une configuration actif/actif ou actif/passif pour la redondance et stocker les données sur un disque partagé tel qu'une baie de stockage RAID 1+0 SCSI ou un SAN (Storage Area Network).  
  
## <a name="see-also"></a>Voir aussi  
 [Offrant une haute disponibilité pour les hôtes BizTalk](../core/providing-high-availability-for-biztalk-hosts.md)   
 [Offrant une haute disponibilité pour les bases de données BizTalk Server](../core/providing-high-availability-for-biztalk-server-databases.md)   
 [Exemples de scénarios de haute disponibilité BizTalk Server](../core/sample-biztalk-server-high-availability-scenarios.md)