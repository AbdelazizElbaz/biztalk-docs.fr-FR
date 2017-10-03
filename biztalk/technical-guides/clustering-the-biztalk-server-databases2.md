---
title: Clustering du Databases2 BizTalk Server | Documents Microsoft
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
ms.openlocfilehash: 4c84f8f6ef26c567a1bbac44df078f2df58ca9da
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="clustering-the-biztalk-server-databases"></a>Mise en cluster des bases de données BizTalk Server
Si les bases de données [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] deviennent indisponibles, l'environnement [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ne fonctionne pas correctement. Pour fournir une haute disponibilité, vous pouvez créer un Microsoft [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] de cluster pour le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] des bases de données, comme indiqué dans l’illustration suivante.  
  
 ![Niveau de base de données BizTalk Server](../core/media/tdi-highava-sqlcluster.gif "TDI_HighAva_SQLCluster")  
  
 Pour créer une solution hautement disponible pour le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] bases de données, vous devez disposer au moins deux ordinateurs qui exécutent [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] et une baie de disques partagée dans le cluster.  
  
## <a name="clustering-options"></a>Options de clustering  
 Déterminer la meilleure configuration de cluster pour le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] bases de données pour les besoins de votre entreprise. Voici une liste des options :  
  
-   **Actif/passif**. Haute disponibilité pour le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] bases de données se compose généralement de deux ou plusieurs ordinateurs de base de données configurées dans une configuration de cluster de serveurs actif/passif. Ces ordinateurs partagent une ressource de disque commune (par exemple un volume RAID 1 + 0 SCSI disque tableau ou stockage réseau) et utiliser le Clustering Windows pour fournir la tolérance de pannes de redondance et de sauvegarde.  
  
-   **Actif/actif**. Le Clustering Windows et [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] vous permettent d’exécuter [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] en mode actif/actif où chaque nœud du cluster est « actif » et en cours d’exécution un ou plusieurs [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] instances. Par exemple, cela vous permettrait de la base de données MessageBox sur un nœud et tous les autres [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] bases de données sur l’autre nœud. Cela vous permet d’optimiser l’utilisation de matériel de cluster, mais un actif [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] configuration doit être utilisée avec précaution.  
  
     Peut chaque nœud simultanément gérer la charge de tous les [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] instances pendant une [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] scénario de basculement de nœud de cluster ? Y a-t-il suffisamment de ressources processeur ? Y a-t-il suffisamment de mémoire ? Qu’en est-il de la bande passante réseau ? Quel disque contention d’e/s ?  
  
     Voici quelques-unes des questions qui doivent être posées afin de déterminer si un actif [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] cluster est adapté aux besoins de vos applications BizTalk. S’il est déterminé qu’un nœud ne peut pas gérer tous les [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] instances dans un scénario de basculement, une alternative consiste à utiliser le clustering actif/actif/passif.  
  
-   **Actif/actif/passif**. Les processus d'exécution écrivent dans la base de données de gestion BizTalk, les bases de données MessageBox, la base de données du composant d'analyse des suivis, celle des schémas en étoile BAM, la base de données d'importation principale BAM et celle des archives BAM. Ces bases de données sont donc particulièrement importantes en cas de sinistre et sont prioritaires lorsqu'il s'agit de déterminer les bases de données à mettre en cluster. Seuls les utilisateurs ou les outils écrivent dans les autres bases de données. Pour les bases de données MessageBox, vous pouvez envisager une configuration actif/actif/passif ou actif/actif/actif/passif afin de réduire les besoins en matériel.  
  
> [!NOTE]  
>  [!INCLUDE[btsSQLServer2008R2](../includes/btssqlserver2008r2-md.md)]et [!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)] Standard Edition prend en charge les clusters de basculement à 2 nœuds. Si vous décidez d’utiliser la configuration actif/actif/passif sur [!INCLUDE[btsSQLServer2008R2](../includes/btssqlserver2008r2-md.md)] ou [!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)], vous devez utiliser l’édition Enterprise de [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)].  
  
## <a name="procedures-for-clustering-the-databases"></a>Procédures de mise en cluster des bases de données  
 Assurez-vous que les conditions préalables suivantes avant de commencer la mise en cluster le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] bases de données.  
  
-   Lorsque vous créez les groupes de domaine pour votre [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environnement, vous devez créer des comptes de domaine.  
  
-   Configurer le [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] de cluster avant d’installer et configurer [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Pour plus d’informations sur le clustering [!INCLUDE[btsSQLServer2008R2](../includes/btssqlserver2008r2-md.md)], consultez [mise en route avec le Clustering de basculement SQL Server 2008 R2](http://go.microsoft.com/fwlink/?LinkId=156820) (http://go.microsoft.com/fwlink/?LinkId=156820).  
  
-   Si vous envisagez de mettre également en cluster le serveur de secret principal, configurez-le en premier. Pour plus d’informations sur la haute disponibilité pour Enterprise Single Sign-On, consultez [haute disponibilité pour le serveur de secret principal](../technical-guides/high-availability-for-the-master-secret-server.md).  
  
#### <a name="to-run-the-biztalk-server-configuration-wizard"></a>Pour exécuter l'Assistant Configuration de BizTalk Server  
  
1.  Installez [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] sur un serveur d'exécution.  
  
2.  Lancer le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] programme de Configuration. Cliquez sur **Démarrer**, pointez sur **programmes**, pointez sur **Microsoft [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]** , puis cliquez sur **Configuration de BizTalk Server**.  
  
3.  Pour appliquer une configuration personnalisée, suivez les étapes de [utilisation du Gestionnaire de Configuration personnalisé](http://go.microsoft.com/fwlink/?LinkId=156822) (http://go.microsoft.com/fwlink/?LinkId=156822) dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] aide. Pour spécifier le cluster SQL Server pour les bases de données BizTalk Server, entrez le nom du cluster SQL Server dans le **bases de données** boîte de dialogue de la configuration.  
  
4.  Terminer la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] configuration en suivant les instructions de [Configuration personnalisée](http://go.microsoft.com/fwlink/?LinkId=156823) (http://go.microsoft.com/fwlink/?LinkId=156823) dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] aide.  
  
 Pour plus d’informations sur le clustering [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] bases de données, consultez [Improving Fault Tolerance in BizTalk Server à l’aide d’un Cluster de basculement Windows Server 2008 ou un Cluster de serveurs Windows Server 2003](http://go.microsoft.com/fwlink/?LinkId=156819) (http://go.microsoft.com/fwlink/?LinkId=156819).  
  
## <a name="behavior-of-biztalk-host-instances-during-sql-server-failover"></a>Comportement des Instances d’hôte BizTalk au cours de basculement SQL Server  
 Pour plus d’informations sur le comportement des instances d’hôte BizTalk pendant le basculement de SQL Server, consultez [comportement de serveur Instances d’hôte BizTalk au cours de basculement SQL Server](http://go.microsoft.com/fwlink/?LinkId=151287) (http://go.microsoft.com/fwlink/?LinkId=151287).  
  
## <a name="using-sql-server-database-mirroring"></a>Utilisation de la mise en miroir de bases de données SQL Server  
 Pour plus d’informations sur l’utilisation de la mise en miroir de base de données SQL Server en ce qui concerne le clustering de base de données BizTalk Server, consultez [utilisation de SQL Server mise en miroir de base de données ou le service de cliché instantané de Volume](http://go.microsoft.com/fwlink/?LinkId=151288) (http://go.Microsoft.com/fwlink/?) LinkId = 151288) dans l’aide de BizTalk Server.  
  
## <a name="see-also"></a>Voir aussi  
 [Mise à l’échelle des bases de données BizTalk Server](../technical-guides/scaling-out-the-biztalk-server-databases.md)