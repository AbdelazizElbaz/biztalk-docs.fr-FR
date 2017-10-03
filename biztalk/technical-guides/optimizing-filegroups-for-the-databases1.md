---
title: Optimisation des groupes de fichiers pour le Databases1 | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f7dbed4d-95d6-4a41-a69e-737a6f2f5a82
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a8d7a9feb1f455a24b397c2dbd0084d08f1cf332
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="optimizing-filegroups-for-the-databases"></a>Optimisation des groupes de fichiers pour les bases de données
Fichier d’entrée/sortie (e/s) contention est souvent un facteur de limitation, ou goulot d’étranglement, dans un environnement BizTalk Server de production. BizTalk Server est une application qui consommée beaucoup les bases de données et à son tour, la base de données SQL Server utilisée par BizTalk Server est e/s de fichier très intensive.  
  
 Cette rubrique décrit comment tirer le meilleur parti de la fonctionnalité de groupes de fichiers de SQL Server pour réduire la fréquence de contention d’e/s de fichier et d’améliorer les performances globales d’une solution BizTalk Server et de fichiers.  
  
## <a name="overview"></a>Vue d'ensemble  
 Chaque solution BizTalk Server rencontrent finalement contention d’e/s de fichier augmentation du débit. Le sous-système d’e/s, ou le moteur de stockage, est un composant essentiel de toute base de données relationnelle. L'implémentation réussie d'une base de données requiert généralement une planification soigneuse dès les premières phases d'un projet. Cette planification doit tenir compte des considérations sur les points suivants :  
  
-   Le type de disque à utiliser, tel que les périphériques RAID (Redundant Array of Independent Disks), par exemple. Pour plus d’informations sur l’utilisation d’une solution de matériel RAID, consultez « À propos des solutions matérielles » dans la documentation SQL Server en ligne à [http://go.microsoft.com/fwlink/?LinkID=113944](http://go.microsoft.com/fwlink/?LinkID=113944).  
  
-   Comment répartir les données sur les disques à l’aide de fichiers et groupes de fichiers. Pour plus d’informations sur l’utilisation des fichiers et groupes de fichiers dans SQL Server 2008, consultez « À l’aide de fichiers et groupes de fichiers » dans la documentation en ligne de SQL Server à [http://go.microsoft.com/fwlink/? LinkID = 69369](http://go.microsoft.com/fwlink/?LinkID=69369) et « Présentation des fichiers et groupes de fichiers » dans la documentation en ligne de SQL Server à [http://go.microsoft.com/fwlink/? LinkID = 96447](http://go.microsoft.com/fwlink/?LinkID=96447).  
  
-   Implémentation de la conception des index optimaux pour améliorer les performances lors de l’accès aux données. Pour plus d’informations sur la conception d’index, consultez « Conception d’index » dans la documentation en ligne de SQL Server à [http://go.microsoft.com/fwlink/?LinkID=96457](http://go.microsoft.com/fwlink/?LinkID=96457).  
  
-   Comment définir les paramètres de configuration SQL Server pour des performances optimales. Pour plus d’informations sur la définition des paramètres de configuration optimale pour SQL Server, consultez « Optimisation des performances du serveur » dans la documentation en ligne de SQL Server à [http://go.microsoft.com/fwlink/?LinkID=71418](http://go.microsoft.com/fwlink/?LinkID=71418).  
  
 Un des principaux objectifs de création de BizTalk Server est de garantir qu’un message est **jamais** perdues. Afin de limiter le risque de perdre des messages, messages sont souvent écrits dans la base de données MessageBox que le message est traité. Lorsque des messages sont traités par une Orchestration, le message est écrit dans la base de données MessageBox à chaque point de persistance dans l’orchestration. Ces points de persistance provoquent la MessageBox écrire le message et l’état sur le disque physique. À des débits plus importants, cette persistance peut entraîner contention de disque considérable et peut potentiellement devenir un goulot d’étranglement.  
  
 Rendre optimale d’utiliser des fichiers et fonctionnalité de groupes de fichiers dans SQL Server a été indiquée pour résoudre les goulots d’étranglement des e/s de fichier et d’améliorer les performances globales dans les solutions BizTalk Server efficacement. Cette optimisation doit être effectuée par un administrateur de base de données SQL Server expérimenté et uniquement après que tous les bases de données BizTalk Server ont été correctement sauvegardés. Cette optimisation doit être effectuée sur tous les ordinateurs SQL Server dans l’environnement BizTalk Server.  
  
 Groupes de fichiers et fichiers de SQL Server peuvent être utilisées pour améliorer les performances de la base de données, car cette fonctionnalité permet de créer une base de données sur plusieurs disques, contrôleurs de disque ou (baie redondante de disques indépendants) systèmes RAID. Par exemple, si votre ordinateur est équipé de quatre disques, vous pouvez créer une base de données comprenant trois fichiers de données et un fichier journal que vous distribuerez à raison d'un fichier par disque. Comme l’accès aux données, quatre têtes de lecture/écriture peuvent accéder simultanément aux données en parallèle. Cela accélère considérablement les opérations de base de données. Pour plus d’informations sur l’implémentation des solutions matérielles pour les disques de SQL Server, consultez « Base de données de performances » dans la documentation en ligne de SQL Server à [http://go.microsoft.com/fwlink/?LinkID=71419](http://go.microsoft.com/fwlink/?LinkID=71419).  
  
 En outre, les fichiers et groupes de fichiers activer placement des données, car les tables peuvent être créés dans les groupes de fichiers spécifiques. Cela améliore les performances, car toutes les e/s de fichier pour une table donnée peuvent être dirigées vers un disque spécifique. Par exemple, une table beaucoup utilisée peut être placée dans un fichier dans un groupe de fichiers situé sur un disque, et les autres tables moins sollicitées dans la base de données peuvent se trouver sur différents fichiers dans un autre groupe stocké sur un deuxième disque.  
  
 Goulots d’étranglement des e/s de fichier considérable en détail dans la rubrique « Identifiant les goulots d’étranglement dans la base de données niveau » sont présentées dans les [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] documentation à l’adresse [http://go.microsoft.com/fwlink/?LinkId=147626](http://go.microsoft.com/fwlink/?LinkId=147626). Le symptôme le plus courant que les e/s de fichier (e/s disque) est un goulot d’étranglement est la valeur du compteur « Longueur de file d’attente de disque : moyenne du disque physique ». Lorsque la valeur du compteur « Longueur de file d’attente de disque : moyenne du disque physique » est supérieure à environ 3 pour tout disque donné sur les serveurs SQL, e/s de fichier est probablement un goulot d’étranglement.  
  
 Si l’application de l’optimisation de fichier ou groupe de fichiers ne résout pas un problème de goulot d’étranglement d’e/s de fichier, il peut être nécessaire d’augmenter le débit du sous-système de disque en ajoutant physiques supplémentaires ou des lecteurs de SAN.  
  
 Cette rubrique décrit comment appliquer manuellement des fichiers et des optimisations, mais ces optimisations peuvent également être scriptées. Un exemple de script SQL est fourni à la fin de cette rubrique. Il est important de noter que ce script doit être modifiée pour prendre en charge le fichier, le groupe de fichiers et la configuration de disque utilisé par les bases de données SQL Server pour une solution BizTalk Server donnée.  
  
> [!NOTE]  
>  Cette rubrique décrit comment créer plusieurs fichiers et groupes de fichiers pour la base de données MessageBox de BizTalk. Pour obtenir une liste exhaustive des recommandée et groupes de fichiers pour toutes les bases de données BizTalk Server, consultez **annexe B** de l’excellent livre blanc sur « Optimisation de base de données BizTalk Server » disponible à l’adresse [http:// go.Microsoft.com/fwlink/ ? LinkID = 101578](http://go.microsoft.com/fwlink/?LinkID=101578).  
  
## <a name="databases-created-with-a-default-biztalk-server-configuration"></a>Bases de données créées avec la configuration de BizTalk Server par défaut  
 Selon les fonctionnalités sont activées lors de la configuration de BizTalk Server, jusqu'à 13 différentes bases de données peut-être être créé dans SQL Server et de toutes ces bases de données sont créés dans le groupe de fichiers par défaut. Le groupe de fichiers par défaut pour SQL Server est le groupe de fichiers primaire, sauf si le groupe de fichiers par défaut est modifié à l’aide de la commande ALTER DATABASE. Le tableau ci-dessous répertorie les bases de données qui sont créés dans SQL Server si toutes les fonctionnalités sont activées lors de la configuration de BizTalk Server.  
  
### <a name="biztalk-server-databases"></a>Bases de données BizTalk Server  
  
||||  
|-|-|-|  
|**Base de données**|**Nom de base de données par défaut**|**Description**|  
|Base de données de configuration|BizTalkMgmtDb|La centrale de méta-informations stocker toutes les instances de BizTalk Server dans le groupe BizTalk Server.|  
|Base de données MessageBox de BizTalk|BizTalkMsgBoxDb|Stocke les prédicats d’abonnement. Il est une plateforme hôte et conserve les files d’attente et les tables d’état de chaque hôte de BizTalk Server. La base de données MessageBox stocke également les messages et les propriétés de message.|  
|Base de données des suivis BizTalk|BizTalkDTADb|Stocke les données suivies par le moteur de suivis BizTalk Server d’analyse de fonctionnement et d’entreprise.|  
|Base de données d'analyse BAM|BAMAnalysis|Base de données SQL Server Analysis Services qui conserve les données historiques agrégées des activités d’entreprise.|  
|Base de données de schémas en étoile BAM|BAMStarSchema|Transforme les données collectées à partir de l’analyse BAM pour traitement OLAP. Cette base de données est requise lors de l’utilisation de la base de données analyse BAM.|  
|Base de données d'importation principale BAM|BAMPrimaryImport|Stocke les événements à partir des activités d’entreprise, puis des requêtes pour la progression et les données après les instances d’activité. Cette base de données effectue également des agrégations en temps réel.|  
|Base de données des archives de l'analyse BAM|BAMArchive|Stocke les prédicats d’abonnement. La base de données des archives BAM permet de réduire l’accumulation des données d’activité d’entreprise dans la base de données d’importation principale BAM.|  
|Base de données SSO|SSODB|Stocke en toute sécurité la configuration des informations pour les emplacements de réception. Stocke des informations pour l’authentification unique applications associées à des applications, ainsi que les informations d’identification chiffrées de l’utilisateur pour toutes les applications associées.|  
|Base de données du moteur de règles|BizTalkRuleEngineDb|Référentiel pour :<br /><br /> -Les stratégies, qui sont des ensembles de règles associées.<br />-Les vocabulaires, qui sont des collections de noms conviviaux spécifique à un domaine pour référencer des données dans les règles.|  
|Base de données de suivi Analysis Server Administration|BizTalkAnalysisDb|Stocke à la fois les cubes OLAP d’analyse de fonctionnement et d’entreprise.|  
  
## <a name="separation-of-data-files-and-log-files"></a>Séparation des fichiers de données et fichiers journaux  
 Comme indiqué ci-dessus, une configuration de BizTalk Server par défaut place la base de données MessageBox dans un seul fichier dans le groupe de fichiers par défaut. Par défaut, les journaux de transaction et de données pour la base de données MessageBox sont placés sur le même lecteur et le chemin d’accès. Pour cela, pour prendre en charge les systèmes avec un seul disque. Une configuration de fichier unique/groupe de fichiers/disque est **pas optimales** dans un environnement de production. Pour des performances optimales, les fichiers de données et fichiers journaux doivent être placés sur des disques distincts.  
  
> [!NOTE]  
>  Les fichiers journaux ne font jamais partie d'un groupe de fichiers. L'espace qui leur est réservé est géré indépendamment de l'espace réservé aux données.  
  
## <a name="the-8020-rule-of-distributing-biztalk-server-databases"></a>La règle des 80/20 de la distribution des bases de données BizTalk Server  
 La principale source de conflits dans la plupart des solutions BizTalk Server, soit en raison de la contention d’e/s disque ou de contention de la base de données, est la base de données MessageBox de BizTalk Server. Cela est vrai dans les scénarios à la fois unique et multi-MessageBox. Il est raisonnable de penser que 80 % de la valeur de la distribution des bases de données BizTalk est dérivée d’optimiser les fichiers de données MessageBox et le fichier journal. L’exemple de scénario détaillée ci-dessous est axé sur l’optimisation des fichiers de données de base de données MessageBox. Ces étapes peuvent ensuite être suivis pour les autres bases de données si nécessaire, par exemple, si la solution requiert un suivi complet, alors la base de données de suivi peut également être optimisé.  
  
## <a name="manually-adding-files-to-the-messagebox-database-step-by-step"></a>Ajout manuel de fichiers à la base de données MessageBox, étape par étape  
 Cette section décrit les étapes à suivre pour ajouter manuellement des fichiers à la base de données MessageBox. Dans cet exemple, trois groupes de fichiers sont ajoutés et un fichier est ajouté à chaque groupe de fichiers pour distribuer les fichiers de la MessageBox sur plusieurs disques. Dans cet exemple, les étapes sont effectuées sur SQL Server 2005 et SQL Server 2008.  
  
> [!NOTE]  
>  À des fins de tests de performances pour ce guide, les groupes de fichiers ont été optimisées via l’utilisation d’un script qui sera publié dans le cadre de la [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] Guide des optimisations des performances. Les étapes ci-dessous sont fournis uniquement à des fins de référence.  
  
### <a name="manually-adding-files-to-the-messagebox-database-on-sql-server-2005-or-sql-server-2008"></a>Ajout manuel de fichiers à la base de données MessageBox sur SQL Server 2005 ou SQL Server 2008  
 **Suivez ces étapes pour ajouter manuellement des fichiers à la base de données MessageBox sur [!INCLUDE[btsSQLServer2005](../includes/btssqlserver2005-md.md)] ou [!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)]:**  
  
> [!NOTE]  
>  Bien qu’il existe de légères différences dans l’interface utilisateur entre [!INCLUDE[btsSQLServer2005](../includes/btssqlserver2005-md.md)] et [!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)], suivez la procédure ci-dessous s’appliquent aux deux versions de [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)].  
  
1.  Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft SQL Server 2005** ou **Microsoft SQL Server 2008**, puis cliquez sur  **SQL Server Management Studio** pour afficher les **se connecter au serveur** boîte de dialogue.  
  
     ![Écran de connexion d’Administration SQL Server 2005](../technical-guides/media/641a03f4-362c-4dde-8c9d-ac313d8881e3.gif "641a03f4-362c-4dde-8c9d-ac313d8881e3")  
  
2.  Dans le **nom du serveur** champ le **se connecter au serveur** boîte de dialogue, entrez le nom de l’instance de SQL Server qui héberge les bases de données MessageBox de BizTalk Server, puis cliquez sur le **se connecter**  bouton pour afficher la **Microsoft SQL Server Management Studio** boîte de dialogue.  
  
     Dans le **l’Explorateur d’objets** volet de SQL Server Management Studio, développez **bases de données** pour afficher les bases de données pour cette instance de [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)].  
  
     ![SQL Server 2005 Management Studio, l’Explorateur d’objets](../technical-guides/media/81f13912-fedc-48c3-9669-c18863e637b1.gif "81f13912-fedc-48c3-9669-c18863e637b1")  
  
3.  Avec le bouton droit de la base de données pour laquelle ajouter les fichiers, puis cliquez sur **propriétés** pour afficher les **propriétés de la base de données** boîte de dialogue de la base de données.  
  
     ![Boîte de dialogue Propriétés de base de données SQL Server 2005](../technical-guides/media/82ae7c11-5b3a-4312-876c-70876abdd65c.gif "82ae7c11-5b3a-4312-876c-70876abdd65c")  
  
4.  Dans le **propriétés de la base de données** boîte de dialogue, sélectionnez le **groupes de fichiers** page. Cliquez sur le **ajouter** bouton permettant de créer des groupes de fichiers supplémentaires pour les bases de données BizTalkMsgBoxDb. Dans l’exemple ci-dessous, trois groupes de fichiers supplémentaires sont ajoutés.  
  
     ![SQL Server 2005, ajout de groupes de fichiers à une base de données](../technical-guides/media/6be47c0e-06c3-45d9-bce2-a42453da7d19.gif "6be47c0e-06c3-45d9-bce2-a42453da7d19")  
  
5.  Dans la boîte de dialogue **Propriétés de la base de données** , sélectionnez la page **Fichiers** .  
  
     Cliquez sur le **ajouter** bouton pour créer des fichiers supplémentaires à ajouter aux groupes de fichiers, puis cliquez sur **OK**. La base de données MessageBox est désormais répartie sur plusieurs disques, qui fourniront un avantage significative des performances de configuration de disque unique.  
  
     Dans l’exemple ci-dessous, un fichier est créé pour chacun des groupes de fichiers qui ont été créés précédemment et chaque fichier est placé sur un disque distinct.  
  
     ![SQL Server 2005, ajout de fichiers à un groupe de fichiers](../technical-guides/media/d5d5c5df-d483-4f01-8128-f98228de51b9.gif "d5d5c5df-d483-4f01-8128-f98228de51b9")  
  
## <a name="sample-sql-script-for-adding-filegroups-and-files-to-the-biztalk-messagebox-database"></a>Exemple de script SQL pour l’ajout de fichiers et groupes de fichiers à la base de données MessageBox de BizTalk  
 L’exemple de script SQL ci-dessous effectue les mêmes tâches qui ont été effectuées manuellement dans la section précédente.  
Cet exemple de script suppose l’existence de lecteurs logiques distincts G à J. Le script crée des fichiers et groupes de fichiers pour chaque groupe de fichiers et place les fichiers journaux sur le lecteur J.  
  
> [!NOTE]  
>  Étant donné que SQL Server écrit séquentiellement à ses fichiers journaux, il n’existe aucun avantage de performances réalisé en créant plusieurs fichiers journaux pour une base de données SQL Server.  
  
```  
-- Filegroup changes are made using the master database  
USE [master]  
GO  
  
-- Script-wide declarations  
DECLARE @CommandBuffer nvarchar(2048)  
DECLARE @FG1_Path nvarchar(1024)  
DECLARE @FG2_Path nvarchar(1024)  
DECLARE @FG3_Path nvarchar(1024)  
DECLARE @Log_Path nvarchar(1024)  
  
-- Set the default path for all filegroups  
SET @FG1_Path = N'G:\BizTalkMsgBoxDATA\'  
SET @FG2_Path = N'H:\BizTalkMsgBoxDATA\'  
SET @FG3_Path = N'I:\BizTalkMsgBoxDATA\'  
SET @Log_Path = N'J:\BizTalkMsgBoxLog\'  
  
ALTER DATABASE [BizTalkMsgBoxDb] ADD FILEGROUP [BTS_MsgBox_FG1]  
SET @CommandBuffer = N'ALTER DATABASE [BizTalkMsgBoxDb] ADD FILE ( NAME = N''BizTalkMsgBoxDb_FG1'', FILENAME = N''' + @FG1_Path +   
N'BizTalkMsgBoxDb_FG1.ndf'' , SIZE = 102400KB , MAXSIZE = UNLIMITED, FILEGROWTH = 10240KB ) TO FILEGROUP [BTS_MsgBox_FG1]'  
EXECUTE (@CommandBuffer)  
  
ALTER DATABASE [BizTalkMsgBoxDb] ADD FILEGROUP [BTS_MsgBox_FG2]  
SET @CommandBuffer = N'ALTER DATABASE [BizTalkMsgBoxDb] ADD FILE ( NAME = N''BizTalkMsgBoxDb_FG1'', FILENAME = N''' + @FG2_Path +   
N'BizTalkMsgBoxDb_FG2.ndf'' , SIZE = 102400KB , MAXSIZE = UNLIMITED, FILEGROWTH = 10240KB ) TO FILEGROUP [BTS_MsgBox_FG2]'  
EXECUTE (@CommandBuffer)  
  
ALTER DATABASE [BizTalkMsgBoxDb] ADD FILEGROUP [BTS_MsgBox_FG3]  
SET @CommandBuffer = N'ALTER DATABASE [BizTalkMsgBoxDb] ADD FILE ( NAME = N''BizTalkMsgBoxDb_FG1'', FILENAME = N''' + @FG3_Path +   
N'BizTalkMsgBoxDb_FG3.ndf'' , SIZE = 102400KB , MAXSIZE = UNLIMITED, FILEGROWTH = 10240KB ) TO FILEGROUP [BTS_MsgBox_FG3]'  
EXECUTE (@CommandBuffer)  
  
ALTER DATABASE [BizTalkMsgBoxDb] MODIFY FILE ( NAME = N'BizTalkMsgBoxDb_log', SIZE = 10240KB , MAXSIZE = UNLIMITED, FILEGROWTH = 10240KB )  
  
GO -- Completes the previous batch, as necessary  
```  
  
 L’exemple de script SQL ci-dessous peut être utilisé pour définir un groupe de fichiers particulier en tant que le groupe de fichiers par défaut :  
  
```  
USE [BizTalkMsgBoxDb]  
GO  
declare @isdefault bit  
SELECT @isdefault=convert(bit, (status & 0x10)) FROM sysfilegroups WHERE groupname=N'BTS_MsgBox_FG1'  
if(@isdefault=0)  
ALTER DATABASE [BizTalkMsgBoxDb] MODIFY FILEGROUP [BTS_MsgBox_FG1] DEFAULT  
GO  
```  
  
 L’avantage de script est que les scripts peuvent effectuer plusieurs tâches rapidement et peuvent être reproduites avec précision et réduisent le risque d’erreur humaine. L’inconvénient d’un script est que l’exécution d’un script écrit correctement peut entraîner de graves problèmes, lesquels nécessitent les bases de données BizTalk Server être reconfigurée à partir de zéro. Par conséquent, il est extrêmement important que les scripts SQL tels que l’exemple de script répertoriées dans cette rubrique sont soigneusement testé avant d’être exécutées dans un environnement de production.