---
title: "Instructions pour éviter les goulots d’étranglement | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 640ab399-b22d-4f71-b41d-ea8d778e064a
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e78f637c2fd6919b4182f2a58b5f16fbd23f0170
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="guidelines-for-avoiding-bottlenecks"></a>Instructions pour éviter les goulots d'étranglement
Même si les paramètres par défaut de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] garantissent des performances optimales pour la plupart des configurations matérielles et logicielles, il peut être préférable, dans certains scénarios, de les modifier ou de repenser la configuration de déploiement. Lors de la configuration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], prenez en compte les éléments suivants afin d'obtenir les meilleures performances :  
  
-   Afin d'éviter tout conflit de ressources, séparez la réception de l'orchestration et de l'envoi en les associant à des hôtes distincts. Pour réduire au maximum les conflits, séparez le service de suivi des autres hôtes.  
  
-   Si le goulot d'étranglement se situe au niveau du processeur sur BizTalk Server, procédez à l'évolution verticale de ce dernier en ajoutant des processeurs ou en effectuant une mise à niveau à l'aide de processeurs plus rapides.  
  
## <a name="sql-server-guidelines"></a>Instructions relatives au serveur SQL Server  
 Lors de la configuration du serveur Microsoft SQL Server avec [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], prenez en compte les éléments suivants afin d'obtenir les meilleures performances :  
  
-   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]bases de données doivent être configurés pour s’exécuter sur une instance dédiée de SQL Server chaque fois que possible. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]est une application qui consommée beaucoup de bases de données de sorte que la séparation du [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou les ordinateurs et les ordinateurs SQL Server qui hébergent le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] améliore les performances de bases de données et doit être considérée comme une meilleure pratique dans une production [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environnement.  
  
-   Utilisez, autant que possible, un sous-système de disque rapide avec le serveur SQL Server. Utilisez un RAID (Redundant Array of Independent Disks) de type 5 (RAID5/10) ou un réseau SAN avec alimentation de secours.  
  
-   Utilisez la procédure de récupération d'urgence du serveur SQL Server pour sauvegarder vos bases de données de façon régulière. Le service BizTalk Server récupère automatiquement vos données en cas de dysfonctionnement de connexion au niveau du serveur SQL Server.  
  
-   Associez chaque boîte de message à un serveur distinct à partir de la base de données des suivis BizTalk (BizTalkDTADb). Pour les déploiements à moins grande échelle, si les ressources d'UC sont disponibles, isoler la boîte de message de la base de données BizTalkDTADb sur un disque séparé peut s'avérer suffisant.  
  
-   La base de données MessageBox principale peut constituer le goulot d'étranglement en raison d'une saturation ou d'une latence du processeur de l'UC lors d'opérations de disque (longueur moyenne de la file d'attente du disque). Si tel est le cas, ajoutez des processeurs à la base de données MessageBox principale. Si ce n’est pas le cas, essayez de désactiver la publication sur la MessageBox principale, ainsi que la MessageBox principale peut gérer plus efficacement le routage des messages vers d’autres bases de données MessageBox.  
  
-   Si le goulot d'étranglement se situe au niveau des opérations de disque, déplacez la base de données BizTalkDTADb vers un ordinateur SQL Server dédié et/ou un disque dédié. Si le goulot d'étranglement ne concerne ni le processeur de l'UC, ni les opérations de disque de la base de données MessageBox principale, vous pouvez créer d'autres bases de données MessageBox sur le même ordinateur SQL Server afin d'exploiter le matériel dont vous disposez.  
  
-   Reportez-vous aux recommandations SQL Server pour placer sur des disques distincts la transaction et les fichiers journaux de données des bases de données MessageBox et BizTalkDTADb.  
  
-   Prévoyez un espace de stockage suffisant pour les fichiers de données et les fichiers journaux, afin d'éviter que le serveur SQL Server ne prenne automatiquement tout l'espace disponible des disques où les fichiers journaux sont stockés. La taille initiale des fichiers journaux sera fonction des conditions spécifiques requises par votre scénario. Faites une estimation de la taille moyenne des fichiers dans votre déploiement en fonction des résultats des tests et ajustez l'espace de stockage avant d'implémenter votre solution.  
  
-   Allouez un espace de stockage suffisant aux bases de données utilisant le disque de façon intensive, telles que les bases de données MessageBox, BAM (Business Activity Monitoring) et les bases de données des suivis. Si votre solution utilise le protocole de messagerie BizTalk Framework, prévoyez un espace de stockage suffisant pour la base de données de configuration BizTalk (BizTalkMgmtDb).  
  
-   En fonction des besoins de votre entreprise [durée de conservation des données] et du volume de données traitées dans votre scénario, configurez les travaux d'archivage et de purge sur la base de données des suivis afin d'empêcher que la base de données BizTalkDTADb ne devienne trop lourde. Plus cette base de données devient importante, plus les performances sont susceptibles de se dégrader (notamment lorsqu'une base de données BizTalkDTADb prend en charge de nombreuses boîtes de message) ; en effet, la capacité maximale de cette base de données, lorsqu'elle est atteinte, limite la fréquence d'insertion des données.  
  
-   Procédez à l'évolution verticale des serveurs hébergeant les bases de données MessageBox et BizTalkDTADb, si ces dernières constituent le goulot d'étranglement. Vous pouvez faire évoluer votre matériel verticalement en ajoutant des processeurs et de la mémoire, en effectuant une mise à niveau grâce à des processeurs plus rapides ou en utilisant des disques durs à haute vitesse dédiés.