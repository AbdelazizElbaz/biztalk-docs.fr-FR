---
title: "Offrant une haute disponibilité pour les bases de données BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- clustering, SQL Servers
- databases, architecture
- SQL Server, clustering
- servers, clustering
- databases, high availability
- architecture
- databases, clustering
- BizTalk Server, architecture
- Windows clustering
- high availability, databases
- clustering, databases
- data, persistence
- SQL Server Analysis Services
ms.assetid: 47fbc402-9e46-41dd-bc12-d1cde1982576
caps.latest.revision: "41"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3648a8f6d48bbfd6cf67995e1d314511b70db7bd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="providing-high-availability-for-biztalk-server-databases"></a>Configuration de la haute disponibilité pour les bases de données BizTalk Server
En matière de persistance des données, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] s'appuie en grande partie sur [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]. Tous les autres composants et hôtes de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] jouent un rôle précis dans le processus d'intégration d'applications d'entreprise hétérogènes (par exemple : la réception, le traitement ou le routage des messages) tandis que l'ordinateur hébergeant les bases de données enregistre ces travaux pour les conserver sur le disque.  
  
 Pour fournir une haute disponibilité pour le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] bases de données, utilisez le Clustering de basculement Windows Server pour configurer deux ordinateurs de la base de données qui exécutent SQL Server pour créer un cluster de serveurs. Ce cluster vous garantit la redondance et la tolérance de pannes nécessaires aux bases de données de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Dans un cluster à équilibrage de charge, plusieurs ordinateurs forment un groupe et fonctionnent ensemble dans le but d'augmenter la disponibilité et l'évolutivité de l'installation. En revanche, dans un cluster de serveurs, deux ordinateurs dédiés aux bases de données sont configurés sur un modèle actif/passif où l'une des machines fournit les ressources de sauvegarde à l'autre.  
  
 Le schéma suivant représente un niveau de base de données [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] hautement disponible grâce à un cluster de serveurs actif/passif.  
  
 ![Niveau de base de données BizTalk Server](../core/media/tdi-highava-sqlcluster.gif "TDI_HighAva_SQLCluster")  
  
 Si la machine de base de données active rencontre des problèmes ou s'arrête, la machine passive devient active et reprend le contrôle des ressources de base de données jusqu'à ce que la machine défaillante soit de nouveau opérationnelle. Le service de base de données bascule vers l'ordinateur actif où une récupération des connexions de données a lieu de manière à ce que l'application [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] continue à fonctionner correctement.  
  
 Pour plus d’informations sur les bases de données qui sont installés par [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], consultez [bases de données BizTalk Server](../core/databases-in-biztalk-server.md).  
  
 Pour plus d’informations sur la sauvegarde votre [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] bases de données, consultez [sauvegarde et restauration de bases de données BizTalk Server](../core/backing-up-and-restoring-biztalk-server-databases.md).  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Bases de données à grande échelle](../core/scaled-out-databases.md)  
  
-   [Mise en cluster les bases de données BizTalk Server](../core/clustering-the-biztalk-server-databases1.md)  
  
-   [Comportement des Instances d’hôte BizTalk Server au cours de basculement SQL Server](../core/behavior-of-biztalk-server-host-instances-during-sql-server-failover.md)  
  
-   [Base de données SQL Server mise en miroir, le service VSS et AlwaysOn](../core/sql-server-database-mirroring-volume-shadow-copy-service-and-alwayson.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Offrant une haute disponibilité pour les hôtes BizTalk](../core/providing-high-availability-for-biztalk-hosts.md)   
 [Exemples de scénarios de haute disponibilité BizTalk Server](../core/sample-biztalk-server-high-availability-scenarios.md)