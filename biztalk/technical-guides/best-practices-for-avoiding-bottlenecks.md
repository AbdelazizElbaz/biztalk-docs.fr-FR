---
title: "Meilleures pratiques pour éviter les goulots d’étranglement | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 81da2e31-dce0-43fb-841f-e65ff99e80a7
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 08f2291d6aa4d16c251a110bc6f94c6288dc5064
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="best-practices-for-avoiding-bottlenecks"></a>Pratiques recommandées pour éviter les goulots d’étranglement
Même si les paramètres par défaut de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] garantissent des performances optimales pour la plupart des configurations matérielles et logicielles, il peut être préférable, dans certains scénarios, de les modifier ou de repenser la configuration de déploiement. Lors de la configuration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], prenez en compte les éléments suivants afin d'obtenir les meilleures performances :  
  
-   Pour éviter les conflits de ressources, isoler la réception de l’orchestration et l’envoi sur des hôtes distincts. Pour réduire au maximum les conflits, séparez le service de suivi des autres hôtes.  
  
-   Si le traitement sur l’ordinateur exécutant BizTalk Server par processeur est le goulot d’étranglement, à l’échelle de l’ordinateur exécutant BizTalk Server en ajoutant des processeurs ou de mise à niveau vers un processeur plus rapide.  
  
## <a name="sql-server-guidelines"></a>Instructions relatives au serveur SQL Server  
 Lors de la configuration du serveur Microsoft SQL Server avec [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], prenez en compte les éléments suivants afin d'obtenir les meilleures performances :  
  
-   Utilisez, autant que possible, un sous-système de disque rapide avec le serveur SQL Server. Utiliser une baie redondante de disques indépendants type 10 (RAID10 / 0 + 1) ou un réseau de stockage (SAN) avec alimentation de secours.  
  
-   Isoler chaque base de données MessageBox sur un serveur distinct de la base de données des suivis BizTalk (BizTalkDTADb). Pour les déploiements plus petits si les ressources de processeur sont disponibles, il peut suffire à isoler la base de données MessageBox sur un disque physique distinct à partir de la base de données des suivis BizTalk.  
  
-   La base de données principale MessageBox peut être le goulet d’étranglement en raison d’une saturation du processeur du processeur ou de la latence des opérations de disque (longueur de file d’attente moyenne du disque). Si tel est le goulot d’étranglement, ajoutez des processeurs à la MessageBox principale. Si ce n’est pas le cas, essayez de désactiver la publication sur la base de données principale. Ainsi, la base de données principale MessageBox peuvent plus gérer efficacement le routage des messages aux autres bases de données MessageBox. L’option pour désactiver la publication est valide lorsque vous utilisez plusieurs bases de données MessageBox.  
  
-   Si le goulot d’étranglement des opérations de disque, déplacez la base de données des suivis BizTalk sur un ordinateur SQL Server dédié et/ou un disque dédié. Si les opérations de disque et de traitement du processeur sur la base de données principale MessageBox ne sont pas le goulot d’étranglement, vous pouvez créer des nouvelles bases de données MessageBox sur le même ordinateur SQL Server pour tirer parti de votre matériel existant.  
  
-   Suivez les recommandations de [optimisation de groupes de fichiers pour le Databases2](../technical-guides/optimizing-filegroups-for-the-databases2.md)pour isoler le journal des transactions et les données des fichiers pour les bases de données MessageBox et des suivis BizTalk sur des disques physiques distincts.  
  
-   Allocation d’espace de stockage pour les fichiers journaux et de données. Sinon, SQL Server prenne automatiquement tout l’espace disponible sur les disques dans lequel les fichiers journaux sont conservés. La taille initiale des fichiers journaux dépend de la configuration requise spécifique dans votre scénario. Faites une estimation de la taille moyenne des fichiers dans votre déploiement en fonction des résultats des tests et ajustez l'espace de stockage avant d'implémenter votre solution.  
  
-   Allouer un espace suffisant pour utilisation de disque hautes bases de données, telles que la MessageBox, l’intégrité et activité de suivi du fonctionnement (HAT) et analyse BAM (Business Activity). Si votre solution utilise le protocole de messagerie BizTalk Framework, prévoyez un espace de stockage suffisant pour la base de données de configuration BizTalk (BizTalkMgmtDb).  
  
-   En fonction de l’entreprise a besoin, telles que les périodes de rétention de données et le volume de données traitées dans votre scénario, configurez le travail « DTA Archive et Purge » de l’Agent SQL Server sur la base de données de suivi HAT telles que la base de données des suivis BizTalk n’augmente pas trop. La croissance de cette base de données peut dégrader les performances, car il est atteint la capacité totale de la base de données impose une limite sur le taux d’insertion de données. Cela est particulièrement vrai lorsqu’une base de données des suivis BizTalk prend en charge plusieurs bases de données MessageBox.  
  
-   Mettre à l’échelle des serveurs hébergeant les bases de données MessageBox et des suivis BizTalk s’ils sont le goulot d’étranglement. Vous pouvez monter le matériel par l’ajout de processeurs, l’ajout de mémoire, la mise à niveau vers un processeur plus rapide et à l’aide de disques dédiés à grande vitesse.  
  
-   Fractionnement de fichiers TempDB dans plusieurs fichiers peut résoudre les problèmes de performances liés aux opérations d’e/s. En règle générale, créez un fichier de données de fichier par processeur et utiliser la même taille pour tous les fichiers créés.  
  
-   Modification de la base de données, la croissance automatique paramètres une valeur fixe, par exemple 100-150 Mo. Par défaut de que la croissance de la base de données est configurée à 10 %, ce qui peut entraîner des retards lors du développement de bases de données volumineuses.  
  
-   Mémoire de SQL Server doit être définie sur une valeur fixe en affectant à la même valeur Min Server Memory et Max Server Memory. En règle générale, allouez 75 % de la mémoire physique à SQL Server et laissez 25 % pour le reste du système d’exploitation et les applications. S’il s’agit d’un serveur SQL dédié, vous pouvez réduire le montant réservé au système d’exploitation à un minimum de 1 Go.  
  
## <a name="see-also"></a>Voir aussi  
 [Recherche et suppression des goulots d’étranglement](../technical-guides/finding-and-eliminating-bottlenecks.md)