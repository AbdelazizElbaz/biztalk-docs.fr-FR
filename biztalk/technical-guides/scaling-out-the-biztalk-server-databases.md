---
title: "Mise à l’échelle les bases de données BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 11/29/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 18853ceb-7975-4c30-878f-6b162005f795
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6df08cf225bde08d05a746ee2f0dcddd7cdddfb0
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="scaling-out-the-biztalk-server-databases"></a>Mise à l’échelle des bases de données BizTalk Server
Pour fournir une haute disponibilité pour les bases de données BizTalk Server, configurez deux ordinateurs qui exécutent SQL Server dans un cluster Windows. Ces ordinateurs peuvent exécuter dans un actif/actif, actif/passif ou actif/actif/passif (nécessite trois ordinateurs) configuration pour la redondance et stocker des données sur un lecteur partagé (par exemple un volume RAID 1 + 0 baie de disques SCSI) ou de réseau de zone de stockage (SAN).  
  
Si, pour quelque raison que ce soit, le service de SQL Server est indisponible, le cluster de la base de données transfère les ressources de l'ordinateur actif vers l'ordinateur passif. Lors de ce processus de basculement, les instances du service BizTalk Server rencontrent des problèmes de connexion aux bases de données et relancent automatiquement ces connexions. L'ordinateur contenant la base de données indemne (ordinateur jusqu'alors passif) commence à traiter les connexions de la base de données après avoir pris en charge les ressources durant le basculement.  
  
Mise en cluster les bases de données BizTalk Server est décrite dans [Clustering le Databases2 serveur BizTalk](../technical-guides/clustering-the-biztalk-server-databases2.md). Cette section se concentre sur la montée en charge les bases de données BizTalk Server offre une haute disponibilité.  
  
## <a name="providing-high-availability-for-the-biztalk-messagebox-database"></a>Offrant une haute disponibilité pour la base de données MessageBox de BizTalk  
 Cette section fournit des informations sur la configuration de la base de données MessageBox de BizTalk pour la haute disponibilité.  
  
### <a name="running-multiple-messagebox-databases"></a>Exécution de plusieurs bases de données MessageBox  
Pour améliorer l’évolutivité des bases de données BizTalk Server et à l’adresse utilisation élevée du processeur sur l’ordinateur SQL Server de base de données MessageBox, vous pouvez configurer BizTalk Server pour stocker des données entre plusieurs bases de données MessageBox. Vous créez la première base de données MessageBox lorsque vous exécutez l'Assistant Configuration. Cette base de données est la base de données principale MessageBox. Il existe une seule base de données principale MessageBox dans votre déploiement BizTalk Server. Elle contient les informations d'abonnement principal et achemine les messages vers la base de données MessageBox appropriée. En règle générale, vous souhaitez dédier cette base de données master pour effectuer un routage uniquement et laisser les autres bases de données MessageBox effectuent le traitement. Pour rendre une base de données MessageBox pour effectuer le routage uniquement, sélectionnez **désactiver la publication des nouveaux messages** à partir des propriétés de MessageBox dans la console Administration de BizTalk.  
  
 Un exemple de flux de traitement de la base de données MessageBox est la suivante :  
  
1.  Lorsque la base de données principale MessageBox reçoit un nouveau message d'activation (une nouvelle instance d'un processus d'entreprise ou un message d'abonnement), elle l'envoie à la première base de données MessageBox disponible. Par exemple, lorsque vous disposez d'une base de données principale MessageBox et de deux bases de données secondaires, la base de données principale achemine le premier message d'activation vers la base de données secondaire n° 1, le second vers la base de données n° 2, le troisième vers la base de données n° 1 et ainsi de suite de manière alternée. La base de données principale utilise une logique intégrée pour équilibrer la charge et n'a donc pas besoin d'autre mécanisme d'équilibrage de charge.  
  
2.  Une fois que la base de données principale MessageBox a acheminé le message d'activation vers une base de données secondaire (la première, par exemple), le processus d'entreprise est mis en mémoire et exécuté.  
  
3.  Si le processus d’entreprise doit attendre un message et le temps d’attente est plus long que quelques secondes, le processus d’entreprise est rendue persistante dans la base de données MessageBox 1. Le processus d’entreprise est en attente d’un message de corrélation.  
  
4.  Lorsque le message de corrélation arrive à la base de données principale, le moteur de messagerie effectue une opération de recherche dans la base de données pour la base de données qui contient l’état du message de corrélation (dans cet exemple, MessageBox 1). La base de données principale MessageBox remet le message à la base de données qui contient le processus d’entreprise.  
  
5.  Le processus d’entreprise est remis en mémoire pour poursuivre le traitement jusqu'à sa fin ou jusqu'à ce qu’il doit attendre d’un autre message de corrélation.  
  
 BizTalk Server stocke l'intégralité des états dans les bases de données MessageBox qui contiennent toutes les informations d'état des différents processus d'entreprise. Pour une fiabilité accrue, vous devez mettre en cluster toutes les bases de données MessageBox, qu'il s'agisse de la base de données principale ou des bases secondaires.  
  
 Pour configurer plusieurs bases de données MessageBox, vous utilisez la console Administration de BizTalk Server pour ajouter les ordinateurs qui exécutent SQL Server. D'un point de vue administrateur, vous devez juste ajouter les nouvelles bases de données MessageBox. BizTalk Server gère automatiquement la distribution alternée des messages d'activation et l'envoi des messages de corrélation aux bases de données MessageBox appropriées.  
  
 Si vous configurez plusieurs bases de données MessageBox dans votre environnement, vous devez créer au moins trois bases de données MessageBox pour votre groupe BizTalk Server et vous devez désactiver la publication de messages sur la base de données principale. Cette recommandation est effectuée, car l’ajout de bases de données MessageBox supplémentaires entraîne une surcharge de la base de données MessageBox maître pour acheminer les messages entre les bases de données MessageBox. Si vous configurez uniquement deux bases de données MessageBox la plupart des avantages offerts par la base de données MessageBox supplémentaire est décalée par la charge de mémoire consommée par la base de données principale MessageBox pour le routage des messages.  
  
> [!IMPORTANT]  
>  BizTalk Server stocke l'intégralité des états dans les bases de données MessageBox qui contiennent toutes les informations d'état des différents processus d'entreprise. Pour une fiabilité accrue, vous devez mettre en cluster toutes les bases de données MessageBox, qu'il s'agisse de la base de données principale ou des bases secondaires.  
  
### <a name="providing-high-availability-for-multiple-messagebox-databases"></a>Configuration de la haute disponibilité pour plusieurs bases de données MessageBox  
 Lors de l’ajout de bases de données MessageBox à votre déploiement BizTalk Server améliore l’évolutivité, il ne fournit pas de haute disponibilité, car chaque base de données MessageBox est unique et indépendante et qu’il s’agit potentiellement d’un seul point de défaillance de votre serveur BizTalk Server environnement. Afin d'obtenir une redondance renforcée, vous devez configurer un cluster de serveurs pour chaque base de données MessageBox. BizTalk Server répartit les données entre les différentes bases de données MessageBox si bien que ces dernières sont incapables de partager les données et de fournir une redondance sans mise en cluster du serveur.  
  
## <a name="providing-high-availability-for-the-biztalk-tracking-database"></a>Configuration de la haute disponibilité pour la base de données des suivis BizTalk  
 Selon les besoins de votre déploiement, il se peut que vous vouliez améliorer les performances du suivi en isolant la base de données des suivis BizTalk sur un ordinateur SQL Server distinct et en créant un hôte BizTalk séparé, consacré au suivi des hôtes. La figure suivante illustre un hôte de suivi dédié avec deux instances d’hôte et les bases de données en cluster.  
  
 ![Montée en charge les bases de données de suivi](../technical-guides/media/4fc1d448-2a6c-4cea-ac17-96c1263dfb68.gif "4fc1d448-2a6c-4cea-ac17-96c1263dfb68")  
  
 Si votre déploiement implique un débit élevé et un suivi pour des données de message très nombreuses, la surcharge de travail due au suivi est susceptible d'utiliser énormément de ressources sur l'ordinateur SQL Server. Si cette situation se produit et continue à un taux élevé de messages entrants, BizTalk Server atteint un point où il ne peut pas traiter les nouveaux messages, car les ressources nécessaires au suivi des messages sont supérieures aux ressources requises pour exécuter le serveur BizTalk Server composants (par exemple, la réception des messages et de les conserver la base de données MessageBox).  
  
 Afin d'améliorer les performances et la sécurité de votre déploiement, il est recommandé de consacrer un hôte ne contenant aucun autre élément (emplacements de réception, orchestrations, pipelines, etc.) au suivi et de désactiver le suivi dans les hôtes de réception, de traitement et d'envoi. Pour rendre l'hôte de suivi hautement disponible, créez plusieurs instances pour cet hôte. Consultez [créer un nouvel hôte](../core/how-to-create-a-new-host.md).
  
 Pour chaque base de données MessageBox, BizTalk Server utilise le suivi qu’une seule instance d’hôte pour déplacer les messages à partir de la base de données MessageBox vers la base de données des suivis BizTalk (BizTalkDTADb). Lorsque des ordinateurs supplémentaires exécutent des instances de l'hôte des suivis, BizTalk Server met automatiquement à l'échelle la gestion de chaque base de données MessageBox en la transférant à une instance de l'hôte de suivi distincte. Si le nombre de bases de données MessageBox est supérieur au nombre d'instances de l'hôte de suivi, une ou plusieurs instances de l'hôte de suivi fonctionnent pour plusieurs bases de données MessageBox.  
  
 Pour disposer de bases de données des suivis BizTalk hautement disponibles, servez-vous du clustering Windows et configurez deux ordinateurs dédiés aux bases de données et fonctionnant sous SQL Server sur un modèle de type actif/passif.  
  
## <a name="providing-high-availability-for-the-bam-databases"></a>Configuration de la haute disponibilité pour des bases de données BAM  
 *L’analyse BAM* (BAM) assure la visibilité des processus d’entreprise indépendamment de l’implémentation informatique ou sur une implémentation informatique hétérogène. Les bases de données SQL Server BAM (schémas en étoile BAM, importation principale BAM et archives BAM) et Analyse BAM conservent les données de l'activité de l'entreprise lorsqu'elles sont différentes des données d'analyse opérationnelle. Le diagramme suivant illustre l’infrastructure de base de données BAM.  
  
 ![Infrastructure de base de données BAM](../technical-guides/media/769c3b7c-fe16-4260-967e-6af003c4f08d.gif "769c3b7c-fe16-4260-967e-6af003c4f08d")  
  
 Afin de vous assurer que votre infrastructure BAM est hautement disponible, procédez comme suit :  
  
-   **Mettre en cluster la base de données d’importation principale BAM et de la base de données analyse BAM.** La base de données d'importation principale BAM constitue le cœur du système BAM (Business Activity Monitoring). Il est donc important qu'elle soit hautement disponible par le biais du clustering Windows et que vous respectiez bien les deux recommandations suivantes afin d'éviter qu'elle n'arrive à saturation. La base de données Analyse BAM est une base de données Analysis Services stockant les données et dont les analystes d'entreprise se servent pour créer des agrégations d'activité et des cubes OLAP. Tout temps d'arrêt de cette base de données a donc des conséquences sur la productivité. Pendant que vous n’êtes pas obligé de cluster de la base de données des archives BAM, nous vous recommandons de surveiller les erreurs dans le journal des événements lors de l’exécution des packages SQL Server Integration Services (SSIS) pour vous assurer que les données ont été correctement transférées et contrôler la taille de la base de données afin que vous pouvez la remplacer avant qu’il remplit les.  
  
-   **Définissez une fenêtre en ligne.** Pour autoriser des meilleures performances et éviter les temps d’arrêt, BAM partitionne les données dans la base de données d’importation principale BAM dans des tables en fonction de l’horodatage lorsque l’activité a été terminée. Le composant BAM réalise cette opération en remplaçant régulièrement la table remplie par une table vide de format identique. Les activités supplémentaires terminées sont ensuite placées dans la nouvelle partition (table) tandis que l'analyse BAM conserve les anciennes partitions pendant la période indiquée dans la fenêtre en ligne. Il faut définir une telle fenêtre afin de vous assurer que le nombre de partitions de la base de données d'importation principale BAM ne devient pas trop important. Pour plus d’informations sur la planification en ligne de windows, consultez [archivage des données primaires importation de base de données](../core/archiving-primary-import-database-data.md).
  
-   **Planifier des packages SSIS pour s’exécuter périodiquement.** La définition d'une fenêtre en ligne garantit que votre base de données d'importation principale BAM n'arrive pas à saturation à cause d'anciennes partitions d'activité. Vous devez également planifier des packages SSIS pour s’exécuter périodiquement pour créer une nouvelle partition pour les données d’activité et déplacer les données à partir d’anciennes partitions de la base de données d’importation principale BAM dans la base de données des archives BAM. Pour plus d’informations sur la planification des packages SSIS, consultez [planification des Packages SQL Server Integration Services](../core/scheduling-sql-server-integration-services-packages.md).
  
-   **Soigneusement sélectionner de petits ensembles d’éléments de données (points de contrôle) et évitez d’inclure des éléments de données inutiles lors de la définition d’une activité.**  
  
-   **Comprendre les compromis entre les agrégations planifiées et en temps réel lorsque vous concevez vos agrégations.** Les agrégations RTA sont gérées de façon automatique par les déclencheurs SQL Server et ne rencontrent aucune latence. Ils sont parfaitement pour certains scénarios de faible latence critiques, mais elles entraînent une baisse chaque fois que les événements sont écrits dans la base de données d’importation principale BAM des performances. Agrégations planifiées s’appuient sur les packages SSIS planifiées cubes pour mettre à jour leurs données d’agrégation. Leur temps de latence est égale ou supérieure à l’intervalle de planification SSIS, mais ensemble, ils ont un impact sur les performances plus petites sur la base de données d’importation principale BAM.  
  
-   **Si vous choisissez d’agrégations planifiées, assurez-vous que vous planifiez des cubes pour SSIS pour exécuter plus fréquemment que SSIS d’archivage.** Il s’agit, car l’archivage SSIS ne déplacera pas les données d’activité qui a été traitées d’agrégation planifiée dans la base de données des archives BAM.  
  
-   **Activez le service de Bus d’événements BAM sur plusieurs ordinateurs pour obtenir des fonctionnalités de basculement.**  
  
## <a name="providing-high-availability-for-the-other-biztalk-server-databases"></a>Configuration de la haute disponibilité pour les autres bases de données BizTalk Server  
 Pour fournir une haute disponibilité pour les autres bases de données BizTalk Server, configurez deux ordinateurs qui exécutent SQL Server dans un cluster Windows. Ces ordinateurs peut s’exécuter dans une configuration actif/actif ou actif/passif pour la redondance et stocker des données sur un lecteur partagé (par exemple un volume RAID 1 + 0 baie de disques SCSI) ou de réseau de zone de stockage (SAN).  
  
## <a name="see-also"></a>Voir aussi  
 [Clustering du Databases2 de BizTalk Server](../technical-guides/clustering-the-biztalk-server-databases2.md)