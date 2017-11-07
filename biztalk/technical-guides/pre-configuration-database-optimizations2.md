---
title: "Base de données de la Configuration préalable Optimizations2 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8c525c3a-249c-4694-b287-a8c35a6aa524
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2f863ae780dd99a7f0aa7d9acc3884f860686c86
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2017
---
# <a name="pre-configuration-database-optimizations"></a>Optimisations de la base de données de la Configuration préalable
Le rôle critique que SQL Server joue dans n’importe quel environnement BizTalk Server, il est vital que SQL Server soit configuré/paramétrés pour des performances optimales. Si SQL Server n’est pas paramétrée pour effectuer correctement, puis les bases de données utilisées par BizTalk Server devient un goulot d’étranglement et les performances globales de l’environnement BizTalk Server seront affectées. Cette rubrique décrit plusieurs optimisations de performances de SQL Server qui doivent être suivies avant d’installer BizTalk Server et de configurer les bases de données BizTalk Server.  
  
## <a name="set-ntfs-file-allocation-unit"></a>Définir l’unité d’Allocation de fichier NTFS  
 SQL Server stocke ses données dans **étendues**, qui sont des collections de huit pages physiquement contiguës de 8 Ko, soit 64 Ko. Par conséquent, pour optimiser les performances du disque, définir la taille d’unité d’Allocation NTFS à 64 Ko comme décrit dans le « disque meilleures pratiques de Configuration » à [meilleures pratiques de déploiement préalable d’e/s](https://msdn.microsoft.com/library/cc966412.aspx).  
  
## <a name="considerations-for-the-version-and-edition-of-sql-server"></a>Considérations relatives à la version et l’édition de SQL Server  
 Différentes versions et éditions de [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] fournissent des fonctionnalités différentes qui peuvent affecter les performances de votre [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environnement. Par exemple, dans des conditions de forte charge, le nombre de verrous de base de données qui sont disponibles pour la version 32 bits de [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] risque d’être dépassée, c'est-à-dire nuit aux performances de la solution BizTalk. Envisagez d’héberger votre base de données MessageBox sur une version 64 bits de SQL Server si vous rencontrez des erreurs « insuffisant de verrous » dans votre environnement de test. Le nombre de verrous disponibles est nettement supérieur sur cette version.  
  
 Examinez le tableau suivant lorsque vous choisissez les fonctionnalités du moteur de base de données dont vous aurez besoin pour votre environnement BizTalk. Pour à grande échelle, solutions au niveau de l’entreprise qui nécessitent de clustering prennent en charge, la prise en charge, de copie des journaux de BizTalk Server ou Analysis Services prend en charge, puis vous avez besoin de SQL Server Enterprise Edition pour héberger le [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] bases de données.   

 Pour obtenir une liste complète des fonctionnalités prises en charge par les éditions de SQL Server, consultez [éditions de SQL Server et les fonctionnalités prises en charge](https://docs.microsoft.com/sql/sql-server/editions-and-components-of-sql-server-2016).
  
## <a name="database-planning-considerations"></a>Planification des considérations relatives à la base de données  
 Nous vous recommandons d’héberger vos bases de données SQL Server sur un stockage rapide (par exemple, des disques SAN rapides ou des disques SCSI rapides). Nous vous recommandons de RAID 10 (1 + 0) au lieu de RAID 5 étant donné que raid 5 est plus lente à l’écriture. Des disques SAN plus récentes ont les caches mémoire très importantes, dans ces cas, la sélection raid n’est pas aussi importante. Pour améliorer les performances, les bases de données et leurs fichiers journaux peuvent résider sur différents disques physiques.  
  
 Envisagez également de réglage de la profondeur de file d’attente host bus adapter (HBA) si vous utilisez un réseau de zone de stockage (SAN). Cela peut affecter considérablement le débit d’e/s et les valeurs hors de la zone peuvent être insuffisants pour SQL Server. Test est requis pour déterminer la valeur optimale, bien que la profondeur de file d’attente de 64 est généralement considéré comme un bon point de départ en l’absence de recommandations de n’importe quel fournisseur spécifique  
  
## <a name="install-the-latest-service-pack-and-cumulative-updates-for-sql-server"></a>Installez le dernier service pack et les mises à jour cumulatives pour SQL Server  
 Installez les derniers service packs et dernières mises à jour cumulatives pour SQL Server, ainsi que les derniers service packs pour .NET Framework.  
  
## <a name="install-sql-service-packs-and-cumulative-updates-on-both-biztalk-server-and-sql-server"></a>Installer les mises à jour cumulatives et les Service Packs SQL sur BizTalk Server et SQL Server  
 Lors de l’installation des service packs ou mises à jour cumulatives pour SQL Server, également installer le service pack ou une mise à jour cumulative sur l’ordinateur BizTalk Server. BizTalk Server utilise les composants du Client SQL sont mises à jour par SQL Server service packs et mises à jour cumulatives.  
  
## <a name="consider-using-a-fast-solid-state-drive-ssd-to-house-the-sql-server-tembdb"></a>Envisagez d’utiliser un lecteur d’accélérée solid state Drive (SSD) pour héberger le tembdb de SQL Server  
 Envisagez d’utiliser un ou plusieurs lecteurs de disque d’état solide (SSD) pour héberger la base de données TempDB. Lecteurs SSD offrent les avantages de performances sur les disques durs traditionnels déposer sont rapidement dans prix lorsqu’ils entrent des marchés grand public. Étant donné que les performances de TempDB sont souvent un facteur clé global [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] les performances, le coût initial ajouté des lecteurs est souvent être rapidement amorti par globaux augmenté [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] des performances, surtout lors de l’exécution d’applications d’entreprise pour lequel [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] performances sont critiques.  
  
## <a name="consider-implementing-the-sql-server-2008-r2-data-collector-and-management-data-warehouse"></a>Envisagez d’implémenter le collecteur de données SQL Server 2008 R2 et l’entrepôt de données de gestion  
 SQL Server 2008 R2 prend en charge l’utilisation du nouveau collecteur de données et de l’entrepôt de données de gestion pour collecter les performances de l’environnement/base de données des données de test et analyse des tendances liées. Le collecteur de données persistantes toutes les données collectées dans l’entrepôt de données de gestion spécifié. Bien que cela ne soit pas une optimisation des performances, cela sera utile pour l’analyse des problèmes de performances.  
  
## <a name="grant-the-account-which-is-used-for-sql-server-the-windows-lock-pages-in-memory-privilege"></a>Accordez au compte qui est utilisé pour le verrouillage de Windows des Pages dans le privilège de la mémoire de SQL Server  
 Accordez le verrouillage de Pages dans le privilège de la mémoire pour le compte de service SQL Server. Cela doit être effectuée pour empêcher le système d’exploitation Windows à partir de la pagination de la mémoire de pool de mémoire tampon du processus SQL Server en verrouillant la mémoire allouée pour le pool de mémoires tampons en mémoire physique.  
  
 Dans notre environnement de laboratoire, la stratégie Windows **Lock Pages in Memory** option a été activée par défaut. Consultez [activer l’Option Lock Pages in mémoire](https://docs.microsoft.com/sql/database-engine/configure-windows/enable-the-lock-pages-in-memory-option-windows).  
  
> [!IMPORTANT]  
>  Certaines limitations s’appliquent lorsque vous accordez le compte de service SQL Server le verrouillage de Pages dans le privilège de la mémoire. Consultez les rubriques suivantes : 
>   
> - [Extension du pool de mémoires tampons](https://docs.microsoft.com/sql/database-engine/configure-windows/buffer-pool-extension)  
> - [Activer les Lock Pages in Memory (Option)](https://docs.microsoft.com/sql/database-engine/configure-windows/enable-the-lock-pages-in-memory-option-windows)  
  
## <a name="grant-the-semanagevolumename-right-to-the-sql-server-service-account"></a>Accorder l’autorisation SE_MANAGE_VOLUME_NAME à droite pour le compte de Service SQL Server  
 Vérifiez le compte exécutant le service SQL Server dispose du privilège « Effectuer des tâches de Maintenance de Volume » Windows ou de vous assurer qu’il appartient à un groupe. Cela permettra instantanée des fichiers d’initialisation garantir des performances optimales si une base de données à croissance automatique.  
  
## <a name="set-min-and-max-server-memory"></a>Valeur Min et Max Server Memory  
 Les ordinateurs exécutant SQL Server qui hébergent les bases de données BizTalk Server doivent être dédiés à l’exécution de SQL Server. Lorsque les ordinateurs exécutant SQL Server qui hébergent les bases de données BizTalk Server sont dédiés à SQL Server en cours d’exécution, nous recommandons de définir les options « max server memory » sur chaque instance de SQL Server « min server memory » pour spécifier la quantité fixe de mémoire à allouer à SQL Server. Dans ce cas, vous devez définir la « min server memory » et « max server memory » sur la même valeur (égal à la quantité maximale de mémoire physique qui utilise SQL Server). Cela va réduire les frais généraux qui serait sinon utilisé par SQL Server de gestion dynamique de ces valeurs. Exécutez les commandes T-SQL suivantes sur chaque ordinateur exécutant SQL Server pour spécifier la quantité fixe de mémoire à allouer à SQL Server :  
  
```  
sp_configure ‘Max Server memory (MB)’,(max size in MB)  
sp_configure ‘Min Server memory (MB)’,(min size in MB)  
```  
  
 Avant de définir la quantité de mémoire pour SQL Server, déterminez le paramètre approprié de mémoire en soustrayant la mémoire requise pour Windows Server à partir de la mémoire physique totale. Il s’agit de la quantité maximale de mémoire que pouvant être allouée à SQL Server.  
  
> [!NOTE]  
>  Si les ordinateurs exécutant SQL Server qui hébergent les bases de données BizTalk Server hébergent également l’entreprise seule l’authentification serveur de secret principal, il vous faudra peut-être modifier cette valeur pour vous assurer qu’il existe suffisamment de mémoire disponible pour exécuter l’Enterprise Single Sign-On Service. Il n’est pas une pratique peu courante pour exécuter une instance en cluster du service Enterprise Single Sign-On sur un cluster de SQL Server pour fournir une haute disponibilité pour le serveur de secret principal. Consultez [Clustering du serveur de secret principal](../technical-guides/clustering-the-master-secret-server.md)  
  
## <a name="split-the-tempdb-database-into-multiple-data-files-of-equal-size-on-each-sql-server-instance-used-by-biztalk-server"></a>Fractionner la base de données tempdb en plusieurs fichiers de données de taille égale sur chaque instance de SQL Server utilisée par BizTalk Server  
 Il est essentiel de s’assurer que les fichiers de données utilisés pour la base de données tempdb sont de taille égale, car l’algorithme de remplissage proportionnel utilisé par SQL Server est basée sur la taille des fichiers de données. Si les fichiers de données sont créés avec la taille inégale, l’algorithme de remplissage proportionnel utilisera le plus grand fichier plus pour les allocations GAM plutôt qu’en se propageant les allocations entre tous les fichiers, invalidant ainsi le but de créer plusieurs fichiers de données. Le nombre optimal de fichiers de données tempdb varie selon le degré de contention de verrou dans tempdb. En règle générale, le nombre de fichiers de données doit être inférieur ou égal au nombre de cœurs de processeur/processeurs où le nombre de processeurs est 8. Pour les serveurs avec plus de 8 processeurs, créer des fichiers de données pour la moitié du nombre de processeurs (là encore, seulement vous avez une contention de verrouillage).  
  
 Dans notre environnement de laboratoire, nous avons utilisé le script ci-dessous pour créer des fichiers de données TempDB 8 chacune d’elles a une taille de 1 024 Mo, avec une croissance de 100 Mo et un fichier journal de 512 Mo avec une croissance de 100 Mo. Les fichiers de données sont déplacées vers le lecteur H: et fichier journal sont déplacées vers le lecteur i.  
  
> [!IMPORTANT]  
>  Ce script est fourni « en l’état, » est destinée uniquement à titre éducatif de démonstration ou et doit être utilisé à vos propres risques. Utilisation de ce script n’est pas prise en charge par Microsoft et Microsoft n’apporte aucune garantie quant à l’adéquation de ce script.  
  
```  
--<<<<<<<<<<----------------------------------------------------------------->>>>>>>>>>--  
-- Use of included script samples are subject to the terms specified at   
-- http://www.microsoft.com/info/cpyright.htm  
--<<<<<<<<<<----------------------------------------------------------------->>>>>>>>>>--  
--***Instructions***  
-- 1. If running the script from a remote server, change the context in SSMS to target instance  
-- 2. Enable SQLCMD mode (add & click toolbar button or toggle by clicking Query > SQLCMD Mode)  
-- 3. Commence execution of scripts (recommend running statements discretely to more easily remedy potential problems)  
-- 4. Examine servername & temp configuration  
-- 5. If necessary, 1) Replace instance name in path to reflect target instance *all throughout script*  
      --            2) Modify root drives to reflect drives designated for data & log (folder creation *and* ALTER DB statements)  
-- 6. Resume script execution  
-- 7. If necessary, create new folders  
-- 8. Modify/Add data & log files   
-- 9. Recycle SQL service using sqlservermanager10.msc  
--10. Examine results & if appropriate, delete original tempdb data log files   
 --(if they were "moved", the original files aren't automatically deleted)  
  
--<<<<<<<<<<----------------------------------------------------------------->>>>>>>>>>--  
--1. If running the script from a remote server, change the context in SSMS to target instance  
--2. Enable SQLCMD mode (add & click toolbar button or toggle by clicking Query > SQLCMD Mode)  
--3. Commence execution of scripts (recommend running statements discretely to more easily remedy potential problems)  
--4. Examine servername & temp configuration  
SELECT @@SERVERNAME  
EXEC dbo.sp_helpdb tempdb  
--tempdev   1   C:\tempdb.mdf   PRIMARY  8192 KB  Unlimited  10%  data only  
--templog   2   C:\templog.ldf  NULL      512 KB  Unlimited  10%  log only  
GO  
--5. If necessary, 1) Replace instance name in path to reflect target instance *all throughout script*  
     --            2) Modify root drives to reflect drives designated for data & log (folder creation *and* ALTER DB statements)  
--6. Resume script execution  
--7. If necessary, create new folders  
--!!md H:\MSSQL10.<instance>  
--!!md H:\MSSQL10.<instance>\MSSQL  
--!!md H:\MSSQL10.<instance>\MSSQL\DATA  
GO  
-- 8. Modify/Add data & log files   
 --note: even if the out-of-box mdf is already where it needs to be,   
   --the first command is necessary to modify size & filegrowth  
ALTER DATABASE tempdb MODIFY FILE (NAME = tempdev  , FILENAME = 'H:\tempdb.mdf'   , SIZE = 1024MB , FILEGROWTH = 100MB)  
ALTER DATABASE tempdb ADD FILE    (NAME = tempdat2 , FILENAME = 'H:\tempdat2.ndf' , SIZE = 1024MB , FILEGROWTH = 100MB)  
ALTER DATABASE tempdb ADD FILE    (NAME = tempdat3 , FILENAME = 'H:\tempdat3.ndf' , SIZE = 1024MB , FILEGROWTH = 100MB)  
ALTER DATABASE tempdb ADD FILE    (NAME = tempdat4 , FILENAME = 'H:\tempdat4.ndf' , SIZE = 1024MB , FILEGROWTH = 100MB)  
ALTER DATABASE tempdb ADD FILE    (NAME = tempdat5 , FILENAME = 'H:\tempdat5.ndf' , SIZE = 1024MB , FILEGROWTH = 100MB)  
ALTER DATABASE tempdb ADD FILE    (NAME = tempdat6 , FILENAME = 'H:\tempdat6.ndf' , SIZE = 1024MB , FILEGROWTH = 100MB)  
ALTER DATABASE tempdb ADD FILE    (NAME = tempdat7 , FILENAME = 'H:\tempdat7.ndf' , SIZE = 1024MB , FILEGROWTH = 100MB)  
ALTER DATABASE tempdb ADD FILE    (NAME = tempdat8 , FILENAME = 'H:\tempdat8.ndf' , SIZE = 1024MB , FILEGROWTH = 100MB)  
GO  
ALTER DATABASE tempdb MODIFY FILE (NAME = templog , FILENAME = 'I:\templog.ldf', SIZE =  512MB , FILEGROWTH = 100MB)  
GO  
--8b. Modify log file:  modify drive & instance name to reflect designated destination for tempdb log   
--!!md I:\MSSQL10.<instance>  
--!!md I:\MSSQL10.<instance>\MSSQL  
--!!md I:\MSSQL10.<instance>\MSSQL\DATA  
GO  
-- 9. Recycle SQL service in SQL Server Services node of sqlservermanager10.msc  
    --note, if running script from a UNC share, SSMS will report an error,   
      --but SQL Server Configuration Manager will open if its location is in %path%  
!!sqlservermanager10.msc  
  
--10. Examine results & if appropriate, delete original tempdb data log files   
 --(if they were "moved", the original files aren't automatically deleted)  
EXEC dbo.sp_helpdb tempdb  
--!!del C:\tempdb.mdf     
--!!del C:\templog.ldf  
GO  
  
```  
  
 Utiliser le moniteur d’activité SQL Server 2008 ou les rapports du tableau de bord SQL Server 2005 performances décrits dans [d’analyse des performances SQL Server](../technical-guides/monitoring-sql-server-performance.md) pour identifier les problèmes de contention de verrou.  
  
## <a name="manually-set-sql-server-process-affinity"></a>Définir manuellement l’affinité de processus SQL Server  
 L’option d’affinité de processus peut fournir des améliorations des performances dans les environnements de haut de gamme, de niveau entreprise de SQL Server qui sont exécutent sur des ordinateurs non-NUMA avec 16 processeurs ou plus. Cela est particulièrement vrai dans les environnements de BizTalk à débit élevé où vous avez à une contention sur les tables partagées dans la base de données MessageBox. Étant donné que les ordinateurs SQL Server qui ont été utilisés dans notre environnement de laboratoire n’ont pas étaient prenant en charge NUMA et avaient 16 cœurs, pour optimiser les performances, nous avons utilisé les commandes ci-dessous pour définir l’affinité du processus :  
  
 **Pour définir manuellement l’affinité du processus SQL Server à partir de 0 à 15**  
  
```  
ALTER SERVER CONFIGURATION  
SET PROCESS AFFINITY CPU = 0 to 15  
```  
  
 Pour plus d’informations, consultez [ALTER SERVER CONFIGURATION (Transact-SQL)](https://docs.microsoft.com/sql/t-sql/statements/alter-server-configuration-transact-sql).
  
## <a name="configure-msdtc"></a>Configurer MSDTC  
 Pour faciliter les transactions entre SQL Server et BizTalk Server, vous devez activer Microsoft Distributed Transaction Coordinator (MS DTC). Pour configurer MSDTC sur SQL Server, consultez la rubrique [recommandations générales pour améliorer les performances de système d’exploitation](../technical-guides/general-guidelines-for-improving-operating-system-performance.md).  
  
## <a name="enable-trace-flag-t1118-as-a-startup-parameter-for-all-instances-of-sql-server"></a>Activer T1118 d’indicateur de Trace en tant que paramètre de démarrage pour toutes les instances de SQL Server  
 Mise en œuvre de la Trace à l’indicateur-T1118 permet de réduire la contention parmi les instances de SQL Server en supprimant presque toutes les allocations de page unique. Pour plus d’informations, consultez [Ko 328551 : PRB : améliorations de la concurrence pour la base de données tempdb](https://support.microsoft.com/help/328551/concurrency-enhancements-for-the-tempdb-database).
  
## <a name="do-not-change-default-sql-server-settings-for-max-degree-of-parallelism-sql-server-statistics-or-database-index-rebuilds-and-defragmentation"></a>Ne modifiez pas les paramètres de SQL Server par défaut pour le degré maximal de parallélisme, les statistiques SQL Server, ou les reconstructions d’index de base de données et la défragmentation  
 Si une instance de SQL Server va héberger les bases de données BizTalk Server, il existe certains paramètres de SQL Server ne doivent pas être modifiés. Plus précisément, les statistiques de SQL Server sur la base de données MessageBox et les paramètres pour l’index de base de données de le SQL Server max degree of parallelism, reconstruit et défragmentation ne doit pas être modifiée. Consultez [des paramètres SQL Server ne doivent pas être modifiés](../technical-guides/sql-server-settings-that-should-not-be-changed.md).
  
## <a name="see-also"></a>Voir aussi  
 [Optimisation des performances des bases de données](../technical-guides/optimizing-database-performance.md)
