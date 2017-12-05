---
title: "Les bases de données de cluster | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1b68bc3f-c0c4-4050-8ca3-df6dd1927637
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0e978c66f903049e566c25f9baf727b6621cbbf2
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="clustering-the-biztalk-server-databases"></a>Mise en cluster des bases de données BizTalk Server
Lorsque les bases de données BizTalk Server sont indisponibles, l'environnement BizTalk Server ne fonctionne pas correctement. Pour qu'elles soient hautement disponibles, vous pouvez créer pour elles un cluster Microsoft SQL Server, comme indiqué sur le schéma suivant.  
  
 ![Niveau de base de données BizTalk Server](../core/media/tdi-highava-sqlcluster.gif "TDI_HighAva_SQLCluster")  
  
 Afin de créer une solution qui soit hautement disponible pour les bases de données BizTalk Server, vous devez disposer d'au moins deux ordinateurs exécutant SQL Server et d'une baie de disques partagée dans le cluster.  
  
## <a name="clustering-options"></a>Options de clustering  
 Il vous est possible de définir la configuration de cluster la mieux adaptée aux bases de données de BizTalk Server et répondant le mieux à vos besoins. Voici une liste des options :  
  
-   **Actif/passif**. Haute disponibilité pour les bases de données BizTalk Server se compose généralement de deux ou plusieurs ordinateurs de base de données configurées dans une configuration de cluster de serveurs actif/passif. Ces ordinateurs partagent une ressource de disque commune (par exemple un volume RAID 1 + 0 SCSI disque tableau ou stockage réseau) et utiliser le Clustering Windows pour fournir la tolérance de pannes de redondance et de sauvegarde.  
  
-   **Actif/actif**. Le Clustering Windows et SQL Server permettent d’exécuter SQL Server en mode actif/actif, où chaque nœud du cluster est en cours d’exécution et de « actifs » instances de SQL Server une ou plusieurs. Par exemple, cela vous permettrait de disposer de la base de données MessageBox sur un nœud et tous les autres bases de données BizTalk Server sur l’autre nœud. Cela vous permet d’optimiser l’utilisation de matériel de cluster, mais une configuration de SQL Server active/active doit être utilisée avec précaution.  
  
     Chaque nœud peut gérer simultanément la charge de toutes les instances de SQL Server pendant un scénario de basculement de nœud de cluster SQL Server ? Y a-t-il suffisamment de ressources processeur ? Y a-t-il suffisamment de mémoire ? Qu’en est-il de la bande passante réseau ? Quel disque contention d’e/s ?  
  
     Voici quelques-unes des questions qui doivent être posées afin de déterminer si un cluster de SQL Server actif/actif est adapté aux besoins de vos applications BizTalk. S’il est déterminé qu’un nœud ne peut pas gérer toutes les instances de SQL Server dans un scénario de basculement, une alternative consiste à utiliser le clustering actif/actif/passif.  
  
-   **Actif/actif/passif**. Les processus d'exécution écrivent dans la base de données de gestion BizTalk, les bases de données MessageBox, la base de données du composant d'analyse des suivis, celle des schémas en étoile BAM, la base de données d'importation principale BAM et celle des archives BAM. Ces bases de données sont donc particulièrement importantes en cas de sinistre et sont prioritaires lorsqu'il s'agit de déterminer les bases de données à mettre en cluster. Seuls les utilisateurs ou les outils écrivent dans les autres bases de données. Pour les bases de données MessageBox, vous pouvez envisager une configuration actif/actif/passif ou actif/actif/actif/passif afin de réduire les besoins en matériel.  
  
> [!NOTE]  
>  SQL Server Standard Edition prend en charge les clusters de basculement à 2 nœuds. Si vous décidez d’utiliser la configuration actif/actif/passif sur SQL Server, vous devez utiliser l’édition Enterprise.  
  
## <a name="procedures-for-clustering-the-databases"></a>Procédures de mise en cluster des bases de données  
 Assurez-vous que les conditions préalables suivantes avant de commencer la mise en cluster les bases de données BizTalk Server.  
  
-   Lorsque vous créez les groupes de domaine pour l'environnement BizTalk Server, vous devez également créer des comptes de domaine.  
  
-   Configurer le cluster SQL Server avant d’installer et configurer BizTalk Server. Consultez [(WSFC) avec SQL Server le Clustering de basculement Windows Server](https://docs.microsoft.com/sql/sql-server/failover-clusters/windows/windows-server-failover-clustering-wsfc-with-sql-server) ou [toujours sur des Instances de Cluster de basculement (SQL Server)](https://docs.microsoft.com/sql/sql-server/failover-clusters/windows/always-on-failover-cluster-instances-sql-server).  
  
-   Si vous envisagez de mettre également en cluster le serveur de secret principal, configurez-le en premier. Consultez [haute disponibilité pour le serveur de secret principal](../technical-guides/high-availability-for-the-master-secret-server.md).  
  
#### <a name="run-biztalk-configuration"></a>Exécuter la Configuration de BizTalk  
  
1.  Installation de BizTalk Server sur un serveur d’exécution.  
  
2. Ouvrez **Configuration de BizTalk Server**.  
  
3.  Pour appliquer une configuration personnalisée, consultez [importer et exporter une Configuration de BizTalk Server](../install-and-config-guides/import-and-export-biztalk-server-configuration.md). Pour spécifier le cluster SQL Server pour les bases de données BizTalk Server, entrez le nom du cluster SQL Server dans le **bases de données** boîte de dialogue de la configuration.  
  
4.  Terminer la configuration de BizTalk Server à l’aide un [Configuration personnalisée](../install-and-config-guides/configure-biztalk-server.md).
  
 Pour plus d’informations sur les clusters de bases de données BizTalk Server, consultez [Improving Fault Tolerance in BizTalk Server à l’aide d’un Cluster de basculement Windows Server 2008 ou un Cluster de serveurs Windows Server 2003](https://www.microsoft.com/download/details.aspx?id=2290).  
  
## <a name="behavior-of-biztalk-host-instances-during-sql-server-failover"></a>Comportement des Instances d’hôte BizTalk au cours de basculement SQL Server  
 Pour plus d’informations sur le comportement des instances d’hôte BizTalk pendant le basculement de SQL Server, consultez [comportement de serveur Instances d’hôte BizTalk au cours de basculement SQL Server](../core/behavior-of-biztalk-server-host-instances-during-sql-server-failover.md).  
  
## <a name="using-sql-server-database-mirroring"></a>Utilisation de la mise en miroir de bases de données SQL Server  
 Pour plus d’informations sur l’utilisation de la mise en miroir de base de données SQL Server en ce qui concerne le clustering de base de données BizTalk Server, consultez [base de données SQL Server mise en miroir, le service VSS et AlwaysOn](../core/sql-server-database-mirroring-volume-shadow-copy-service-and-alwayson.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Montée en charge des bases de données BizTalk Server](../technical-guides/scaling-out-the-biztalk-server-databases.md)