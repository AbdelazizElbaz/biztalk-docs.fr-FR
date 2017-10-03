---
title: "Base de données de la Configuration préalable Optimizations1 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ebd0b32a-490d-4db2-a1fc-bf3bef93aeea
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3c1333f956afc4411ff8b105c777214467155ae7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="pre-configuration-database-optimizations"></a>Optimisations de la base de données de la Configuration préalable
BizTalk Server est une application de beaucoup de ressources de base de données qui peut-être nécessiter la création de bases de données distinctes jusqu'à 13 dans Microsoft SQL Server. Le rôle critique que SQL Server joue dans n’importe quel environnement BizTalk Server, il est vital que SQL Server est configuré/paramétrés pour des performances optimales. Si SQL Server n’est pas paramétrée pour effectuer correctement, puis les bases de données utilisées par BizTalk Server devient un goulot d’étranglement et les performances globales de l’environnement BizTalk Server seront affectées. Cette rubrique décrit plusieurs optimisations de performances de SQL Server qui doivent être suivies avant d’installer BizTalk Server et de configurer les bases de données BizTalk Server.  
  
## <a name="set-ntfs-file-allocation-unit"></a>Définir l’unité d’Allocation de fichier NTFS  
 SQL Server stocke ses données dans **étendues**, qui sont des groupes de huit pages de 8 Ko. Par conséquent, pour optimiser les performances du disque, définir la taille d’unité d’Allocation NTFS à 64 Ko comme décrit dans la section « Disque meilleures pratiques de Configuration » de SQL Server meilleures pratiques de l’article « Prédéploiement d’e/s meilleures pratiques » disponible à l’adresse [http:// go.Microsoft.com/fwlink/ ? LinkId = 140818](http://go.microsoft.com/fwlink/?LinkId=140818). Pour plus d’informations sur les pages de SQL Server et les extensions, consultez le [!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)] rubrique de la documentation en ligne [présentation des Pages et étendues](http://go.microsoft.com/fwlink/?LinkId=148939) (lien hypertexte « http://go.microsoft.com/fwlink/?LinkId=148939 » http://go.microsoft.com/fwlink/?LinkId=148939).  
  
## <a name="database-planning-considerations"></a>Planification des considérations relatives à la base de données  
 Nous vous recommandons d’héberger votre [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] bases de données sur un stockage rapide (par exemple, des disques SAN rapides ou des disques SCSI rapides). Nous vous recommandons de RAID 10 (1 + 0) au lieu de RAID 5 étant donné que raid 5 est plus lente à l’écriture. Des disques SAN plus récentes ont des caches de la mémoire de très grande taille, dans que ces cas, la sélection RAID n’est pas aussi importante. Pour améliorer les performances, les bases de données et leurs fichiers journaux peuvent résider sur différents disques physiques.  
  
## <a name="install-the-latest-service-pack-and-cumulative-updates-for-sql-server"></a>Installez le dernier service pack et les mises à jour cumulatives pour SQL Server  
 Installez les derniers service packs et dernières mises à jour cumulatives pour SQL Server 2005 et SQL Server 2008, ainsi que les derniers service packs pour .NET Framework.  
  
## <a name="install-sql-service-packs-on-both-biztalk-server-and-sql-server"></a>Installer les Service Packs SQL sur BizTalk Server et SQL Server  
 Lorsque vous installez les service packs pour SQL Server, vous devez également installer le service pack sur l’ordinateur BizTalk Server. BizTalk Server utilise les composants du Client SQL sont mises à jour par les service packs SQL Server.  
  
## <a name="consider-implementing-the-sql-server-2008-data-collector-and-management-data-warehouse"></a>Envisagez d’implémenter le collecteur de données SQL Server 2008 et l’entrepôt de données de gestion  
 SQL Server 2008 prend en charge l’utilisation du nouveau collecteur de données et de l’entrepôt de données de gestion pour collecter les performances de l’environnement/base de données des données de test et analyse des tendances liées. Le collecteur de données persistantes toutes les données collectées dans l’entrepôt de données de gestion spécifié. Bien que cela ne soit pas une optimisation des performances, ce sera utile pour l’analyse des problèmes de performances.  
  
## <a name="grant-the-account-which-is-used-for-sql-server-the-windows-lock-pages-in-memory-privilege"></a>Accordez au compte qui est utilisé pour le verrouillage de Windows des Pages dans le privilège de la mémoire de SQL Server  
 Accorder des privilèges Windows « Verrouiller les Pages en mémoire » pour le compte de service SQL Server. Cela doit être effectuée pour empêcher le système d’exploitation Windows à partir de la pagination de la mémoire de pool de mémoire tampon du processus SQL Server en verrouillant la mémoire allouée pour le pool de mémoires tampons en mémoire physique. Pour plus d’informations, consultez Base de connaissances Microsoft l’article 914483 « comment réduire la pagination de la mémoire tampon dans la version 64 bits de SQL Server 2005 » à [http://go.microsoft.com/fwlink/?LinkId=148948](http://go.microsoft.com/fwlink/?LinkId=148948).  
  
## <a name="grant-the-semanagevolumename-right-to-the-sql-server-service-account"></a>Accorder l’autorisation SE_MANAGE_VOLUME_NAME droit au compte de Service SQL Server  
 Vérifiez que le compte exécutant le service SQL Server dispose du privilège « Effectuer des tâches de Maintenance de Volume » Windows ou assurez-vous qu’il appartient à un groupe de sécurité qui. Cela autorise l’initialisation instantanée des fichiers en garantissant des performances optimales si une base de données à croissance automatique.  
  
## <a name="set-min-and-max-server-memory"></a>Valeur Min et Max Server Memory  
 Les ordinateurs qui exécutent [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] qui hébergent les bases de données BizTalk Server doivent être dédiés à l’exécution de SQL Server. Nous recommandons de définir les options « max server memory » sur chaque instance de SQL Server « min server memory » pour spécifier la quantité fixe de mémoire à allouer à SQL Server. Dans ce cas, vous devez définir la « min server memory » et « max server memory » sur la même valeur (égal à la quantité maximale de mémoire physique qui utilise SQL Server). Cela va réduire les frais généraux qui serait sinon utilisé par SQL Server de gestion dynamique de ces valeurs. Exécutez les commandes T-SQL suivantes sur chaque ordinateur SQL Server pour spécifier la quantité fixe de mémoire à allouer à SQL Server :  
  
```  
sp_configure ‘Max Server memory (MB)’,(max size in MB)  
sp_configure ‘Min Server memory (MB)’,(min size in MB)  
```  
  
 Avant de définir la quantité de mémoire pour SQL Server, déterminez le paramètre approprié de mémoire en soustrayant la mémoire requise pour Windows Server à partir de la mémoire physique totale. Il s’agit de la quantité maximale de mémoire que pouvant être allouée à SQL Server.  
  
> [!NOTE]  
>  Si l’ou les ordinateurs exécutant SQL Server qui hébergent les bases de données BizTalk Server hébergent également l’entreprise seule l’authentification serveur de secret principal, il vous faudra peut-être ajuster cette valeur pour vous assurer qu’il existe suffisamment de mémoire disponible pour exécuter l’Enterprise Single Sign-On Service. Il n’est pas une pratique peu courante pour exécuter une instance en cluster du service Enterprise Single Sign-On sur un cluster de SQL Server pour fournir une haute disponibilité pour le serveur de secret principal. Pour plus d’informations sur le clustering de l’entreprise seule l’authentification serveur de secret principal, consultez la rubrique « Comment au Cluster le serveur de secret principal » dans le [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]documentation à l’adresse [http://go.microsoft.com/fwlink/?LinkID=106874](http://go.microsoft.com/fwlink/?LinkID=106874).  
  
## <a name="split-the-tempdb-database-into-multiple-data-files-of-equal-size-on-each-sql-server-instance-used-by-biztalk-server"></a>Fractionner la base de données tempdb en plusieurs fichiers de données de taille égale sur chaque instance de SQL Server utilisée par BizTalk Server  
 S’assurer que les fichiers de données utilisés pour la base de données tempdb sont de taille égale est critique, car l’algorithme de remplissage proportionnel utilisé par [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] est basée sur la taille des fichiers de données. Cet algorithme tente de s’assurer que [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] remplit chaque fichier en fonction de l’espace libre restant dans ce fichier afin qu’ils atteignent leur capacité maximale en même temps. Si les fichiers de données sont créés avec la taille inégale, l’algorithme de remplissage proportionnel utilisera le plus grand fichier plus pour les allocations GAM plutôt qu’en se propageant les allocations entre tous les fichiers, invalidant ainsi le but de créer plusieurs fichiers de données. Le nombre de fichiers de données pour la base de données tempdb doit être configuré pour être au moins égal au nombre de processeurs affectées pour SQL Server.  
  
## <a name="enable-trace-flag-t1118-as-a-startup-parameter-for-all-instances-of-sql-server"></a>Activer T1118 d’indicateur de Trace en tant que paramètre de démarrage pour toutes les instances de SQL Server  
 Mise en œuvre de la Trace à l’indicateur-T1118 permet de réduire la contention parmi les instances de SQL Server en supprimant presque toutes les allocations de page unique. Pour plus d’informations, consultez l’article 328551 de la Base de connaissances Microsoft « PRB : améliorations de la concurrence pour la base de données tempdb » à [http://go.microsoft.com/fwlink/?LinkID=103713](http://go.microsoft.com/fwlink/?LinkID=103713).  
  
## <a name="do-not-change-default-sql-server-settings-for-max-degree-of-parallelism-sql-server-statistics-or-database-index-rebuilds-and-defragmentation"></a>Ne modifiez pas les paramètres de SQL Server par défaut pour le degré maximal de parallélisme, les statistiques SQL Server, ou les reconstructions d’index de base de données et la défragmentation  
 Si une instance de SQL Server va héberger les bases de données BizTalk Server, certains paramètres de SQL Server ne doivent pas être modifiées. Plus précisément, les statistiques de SQL Server sur la base de données MessageBox et les paramètres pour l’index de base de données de le SQL Server max degree of parallelism, reconstruit et défragmentation ne doit pas être modifiée. Pour plus d’informations, consultez la rubrique « SQL Server paramètres que doit pas être modifiée » dans le Guide des opérations BizTalk Server à [http://go.microsoft.com/fwlink/?LinkId=114358](http://go.microsoft.com/fwlink/?LinkId=114358).