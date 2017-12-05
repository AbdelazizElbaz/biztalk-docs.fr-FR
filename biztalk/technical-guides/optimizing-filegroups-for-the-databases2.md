---
title: "Optimiser les groupes de fichiers de base de données | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8d7fa4c9-e504-4f43-a308-517a4a574c26
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9333a88817e96b52ffe186f0a6a598b225ef5202
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="optimizing-filegroups-for-the-databases"></a>Optimisation des groupes de fichiers pour les bases de données
Fichier d’entrée/sortie (e/s) contention est souvent un facteur de limitation, ou goulot d’étranglement, dans un environnement BizTalk Server de production. BizTalk Server est une application qui consommée beaucoup les bases de données et à son tour, la base de données SQL Server utilisée par BizTalk Server est e/s de fichier très intensive. Cette rubrique décrit comment tirer le meilleur parti de la fonctionnalité de groupes de fichiers de SQL Server pour réduire la fréquence de contention d’e/s de fichier et d’améliorer les performances globales d’une solution BizTalk Server et de fichiers.  
  
## <a name="overview"></a>Vue d'ensemble  
 Chaque solution BizTalk Server rencontrent finalement contention d’e/s de fichier augmentation du débit. Le sous-système d’e/s, ou le moteur de stockage, est un composant essentiel de toute base de données relationnelle. L'implémentation réussie d'une base de données requiert généralement une planification soigneuse dès les premières phases d'un projet. Cette planification doit tenir compte des considérations sur les points suivants :  
  
-   Le type de disque à utiliser, tel que les périphériques RAID (Redundant Array of Independent Disks), par exemple. 
  
-   Comment répartir les données sur les disques à l’aide de fichiers et groupes de fichiers. Pour plus d’informations sur l’utilisation des fichiers et groupes de fichiers dans SQL Server, consultez [base de données et groupes de fichiers](https://docs.microsoft.com/sql/relational-databases/databases/database-files-and-filegroups).
  
-   Implémentation de la conception des index optimaux pour améliorer les performances lors de l’accès aux données. Pour plus d’informations sur la conception d’index, consultez [conception des index](https://docs.microsoft.com/sql/relational-databases/sql-server-index-design-guide).
  
-   Comment définir les paramètres de configuration SQL Server pour des performances optimales. Pour plus d’informations sur la définition des paramètres de configuration optimale pour SQL Server, consultez [les Options de Configuration de serveur](https://docs.microsoft.com/sql/database-engine/configure-windows/server-configuration-options-sql-server).
  
 Un des principaux objectifs de création de BizTalk Server est de garantir qu’un message est **jamais** perdues. Afin de limiter le risque de perdre des messages, messages sont souvent écrits dans la base de données MessageBox que le message est traité. Lorsque des messages sont traités par une orchestration, le message est écrit dans la base de données MessageBox à chaque point de persistance dans l’orchestration. Ces points de persistance provoquent la MessageBox écrire le message et l’état sur le disque physique. À des débits plus importants, cette persistance peut entraîner contention de disque considérable et peut potentiellement devenir un goulot d’étranglement.  
  
 Rendre optimale d’utiliser des fichiers et fonctionnalité de groupes de fichiers dans SQL Server a été indiquée pour résoudre les goulots d’étranglement des e/s de fichier et d’améliorer les performances globales dans les solutions BizTalk Server efficacement.  
  
> [!NOTE]  
>  Cette optimisation doit être effectuée par un administrateur de base de données SQL Server expérimenté et uniquement après que tous les bases de données BizTalk Server ont été correctement sauvegardés. Cette optimisation doit être effectuée sur tous les ordinateurs SQL Server dans l’environnement BizTalk Server.  
  
 Groupes de fichiers et fichiers de SQL Server peut être utilisé pour améliorer les performances de la base de données, car cette fonctionnalité permet à une base de données doit être créé sur plusieurs disques, contrôleurs de disque ou (baie redondante de disques indépendants) systèmes RAID. Par exemple, si votre ordinateur est équipé de quatre disques, vous pouvez créer une base de données comprenant trois fichiers de données et un fichier journal que vous distribuerez à raison d'un fichier par disque. Comme l’accès aux données, quatre têtes de lecture/écriture peuvent accéder simultanément aux données en parallèle. Cela accélère considérablement les opérations de base de données. Pour plus d’informations sur l’implémentation des solutions matérielles pour les disques de SQL Server, consultez [les performances de base de données](http://go.microsoft.com/fwlink/?LinkID=71419) (http://go.microsoft.com/fwlink/?LinkID=71419) dans la documentation en ligne de SQL Server.  
  
 En outre, les fichiers et groupes de fichiers activer placement des données, car les tables peuvent être créés dans les groupes de fichiers spécifiques. Cela améliore les performances, car toutes les e/s de fichier pour une table donnée peuvent être dirigées vers un disque spécifique. Par exemple, une table beaucoup utilisée peut être placée dans un fichier dans un groupe de fichiers situé sur un disque, et les autres tables moins sollicitées dans la base de données peuvent se trouver sur différents fichiers dans un autre groupe stocké sur un deuxième disque.  
  
 Les goulots d’étranglement d’e/s de fichier sont décrites en détail considérable dans [les goulots d’étranglement au niveau de la base de données](../technical-guides/bottlenecks-in-the-database-tier.md). Le symptôme le plus courant que les e/s de fichier (e/s disque) est un goulot d’étranglement est la valeur du compteur « Longueur de file d’attente de disque : moyenne du disque physique ». Lorsque la valeur du compteur « Longueur de file d’attente de disque : moyenne du disque physique » est supérieure à environ 3 pour tout disque donné sur les ordinateurs exécutant SQL Server, e/s de fichier est probablement un goulot d’étranglement.  
  
 Si l’application de l’optimisation de fichier ou groupe de fichiers ne résout pas un problème de goulot d’étranglement d’e/s de fichier, il peut être nécessaire d’augmenter le débit du sous-système de disque en ajoutant physiques supplémentaires ou des lecteurs de SAN.  
  
 Cette rubrique décrit comment appliquer manuellement des fichiers et des optimisations, mais ces optimisations peuvent également être scriptées. Un exemple de script SQL est fourni dans [Script SQL des groupes de fichiers de base de données BizTalk Server MessageBox](../technical-guides/biztalk-server-messagebox-database-filegroups-sql-script.md).  
  
> [!NOTE]  
>  Il est important de noter que ce script doit être modifiée pour prendre en charge le fichier, le groupe de fichiers et la configuration de disque utilisé par les bases de données SQL Server pour une solution BizTalk Server donnée.  
  
> [!NOTE]  
>  Cette rubrique décrit également comment créer plusieurs fichiers et groupes de fichiers pour la base de données MessageBox de BizTalk. Pour obtenir une liste exhaustive des recommandée et groupes de fichiers pour toutes les bases de données BizTalk Server, consultez « Annexe B » de la [l’optimisation de base de données BizTalk Server](http://go.microsoft.com/fwlink/?LinkID=101578) le livre blanc (http://go.microsoft.com/fwlink/?LinkID=101578).  
  
> [!NOTE]  
>  Bien que le [l’optimisation de base de données BizTalk Server](http://go.microsoft.com/fwlink/?LinkID=101578) le livre blanc (http://go.microsoft.com/fwlink/?LinkID=101578) a été écrit avec [!INCLUDE[btsbiztalkserver2006r2](../includes/btsbiztalkserver2006r2-md.md)] à l’esprit les mêmes principes s’appliquent à BizTalk Server.  
  
## <a name="databases-created-with-a-default-biztalk-server-configuration"></a>Bases de données créées avec la configuration de BizTalk Server par défaut  
 Selon les fonctionnalités sont activées lors de la configuration de BizTalk Server, jusqu'à 13 différentes bases de données peut-être être créé dans SQL Server et de toutes ces bases de données sont créés dans le groupe de fichiers par défaut. Le groupe de fichiers par défaut pour SQL Server est le groupe de fichiers primaire, sauf si le groupe de fichiers par défaut est modifié à l’aide de la commande ALTER DATABASE. Le tableau suivant répertorie les bases de données qui sont créés dans SQL Server si toutes les fonctionnalités sont activées lors de la configuration de BizTalk Server.  
  
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
|Base de données EDI de base BizTalk|BizTalkEDIDb|Stocke le suivi et le traitement des données des documents EDI.|  
|Base de données Administration des Services HWS|BizTalkHwsDb|Stocke les informations d’administration requises par les Services HWS BizTalk.|  
|base de données de gestion des partenaires commerciaux|TPM|Stocke des données de partenaires d’échange pour les Services BAS (Business Activity).|  
|Base de données de suivi Analysis Server Administration|BizTalkAnalysisDb|Stocke à la fois les cubes OLAP d’analyse de fonctionnement et d’entreprise.|  
  
## <a name="separation-of-data-files-and-log-files"></a>Séparation des fichiers de données et fichiers journaux  
 Comme indiqué précédemment, une valeur par défaut de configuration de BizTalk Server place la base de données MessageBox dans un seul fichier dans le groupe de fichiers par défaut. Par défaut, les journaux de transaction et de données pour la base de données MessageBox sont placés sur le même lecteur et le chemin d’accès. Pour cela, pour prendre en charge les systèmes avec un seul disque. Une configuration de fichier unique/groupe de fichiers/disque est **pas optimales** dans un environnement de production. Pour des performances optimales, les fichiers de données et fichiers journaux doivent être placés sur des disques distincts.  
  
> [!NOTE]  
>  Les fichiers journaux ne font jamais partie d'un groupe de fichiers. L'espace qui leur est réservé est géré indépendamment de l'espace réservé aux données.  
  
## <a name="the-8020-rule-of-distributing-biztalk-server-databases"></a>La règle des 80/20 de la distribution des bases de données BizTalk Server  
 La principale source de conflits dans la plupart des solutions BizTalk Server, soit en raison de la contention d’e/s disque ou de contention de la base de données, est la base de données MessageBox de BizTalk Server. Cela est vrai dans les scénarios à la fois unique et multi-MessageBox. Il est raisonnable de penser que 80 % de la valeur de la distribution des bases de données BizTalk est dérivée d’optimiser les fichiers de données MessageBox et le fichier journal. L’exemple de scénario détaillée ci-dessous est axé sur l’optimisation des fichiers de données de base de données MessageBox. Ces étapes peuvent ensuite être suivis pour d’autres bases de données en fonction des besoins. Par exemple, si la solution nécessite un suivi étendues, la base de données de suivi peut également être optimisé.  
  
## <a name="manually-adding-files-to-the-messagebox-database-step-by-step"></a>Ajout manuel de fichiers à la base de données MessageBox, étape par étape  
 Cette section de la rubrique décrit les étapes à suivre pour ajouter manuellement des fichiers à la base de données MessageBox. Dans cet exemple, trois groupes de fichiers sont ajoutés et un fichier est ajouté à chaque groupe de fichiers pour distribuer les fichiers de la MessageBox sur plusieurs disques.
  
### <a name="manually-adding-files-to-the-messagebox-database-on-sql-server"></a>Ajout manuel de fichiers à la base de données MessageBox sur SQL Server
   
1.  Ouvrez **SQL Server Management Studio** pour afficher les **se connecter au serveur** boîte de dialogue.  
  
     ![Écran de connexion à SQL Server](../technical-guides/media/sqlserver2008r2-loginscreen.gif "SQLServer2008R2-Loginscreen")  
  
2.  Dans le **nom du serveur** zone de modification de la **se connecter au serveur** boîte de dialogue zone, entrez le nom de l’instance de SQL Server qui héberge les bases de données MessageBox de BizTalk Server, cliquez sur **Connect** pour afficher de SQL Server Management Studio. Dans le **l’Explorateur d’objets** volet de SQL Server Management Studio, développez **bases de données** pour afficher les bases de données pour cette instance de SQL Server.  
  
     ![SQL Server 2005 Management Studio, l’Explorateur d’objets](../technical-guides/media/81f13912-fedc-48c3-9669-c18863e637b1.gif "81f13912-fedc-48c3-9669-c18863e637b1")  
  
3.  Avec le bouton droit de la base de données auquel vous souhaitez ajouter les fichiers, puis cliquez sur **propriétés** pour afficher les **propriétés de la base de données** boîte de dialogue de la base de données.  
  
     ![Boîte de dialogue Propriétés de base de données SQL Server 2005](../technical-guides/media/82ae7c11-5b3a-4312-876c-70876abdd65c.gif "82ae7c11-5b3a-4312-876c-70876abdd65c")  
  
4.  Dans le **propriétés de la base de données** boîte de dialogue, sélectionnez le **groupes de fichiers** page. Pour créer des groupes de fichiers supplémentaires pour les bases de données BizTalkMsgBoxDb, cliquez sur **ajouter** . Dans l’exemple suivant, trois groupes de fichiers supplémentaires sont ajoutés.  
  
     ![SQL Server 2005, ajout de groupes de fichiers à une base de données](../technical-guides/media/6be47c0e-06c3-45d9-bce2-a42453da7d19.gif "6be47c0e-06c3-45d9-bce2-a42453da7d19")  
  
5.  Dans la boîte de dialogue **Propriétés de la base de données** , sélectionnez la page **Fichiers** .  
  
     Pour créer des fichiers supplémentaires à ajouter aux groupes de fichiers, cliquez sur **ajouter** , puis cliquez sur **OK**. La base de données MessageBox est désormais répartie sur plusieurs disques, qui fourniront un avantage significative des performances de configuration de disque unique.  
  
     Dans l’exemple suivant, un fichier est créé pour chacun des groupes de fichiers qui ont été créés précédemment et chaque fichier est placé sur un disque distinct.  
  
     ![SQL Server 2005, ajout de fichiers à un groupe de fichiers](../technical-guides/media/d5d5c5df-d483-4f01-8128-f98228de51b9.gif "d5d5c5df-d483-4f01-8128-f98228de51b9")  
  
## <a name="sample-sql-script-for-adding-filegroups-and-files-to-the-biztalk-messagebox-database"></a>Exemple de script SQL pour l’ajout de fichiers et groupes de fichiers à la base de données MessageBox de BizTalk  
 Ce guide inclut un script SQL pour l’ajout de fichiers et groupes de fichiers à la base de données MessageBox de BizTalk Server.  
  
> [!NOTE]  
>  Étant donné que SQL Server écrit séquentiellement à ses fichiers journaux, il n’existe aucun avantage de performances réalisé en créant plusieurs fichiers journaux pour une base de données SQL Server.  
  
 Pour exécuter ce script, procédez comme suit :  
  
1.  Ouvrez **SQL Server Management Studio** pour afficher les **se connecter au serveur** boîte de dialogue.  
  
2.  Dans le **nom du serveur** zone de modification de la **se connecter au serveur** boîte de dialogue zone, entrez le nom de l’instance de SQL Server qui héberge les bases de données MessageBox de BizTalk Server, cliquez sur **Connect** pour afficher la boîte de dialogue SQL Server Management Studio.  
  
3.  Dans SQL Server Management Studio, cliquez sur le **fichier** menu, pointez sur **nouveau**, puis cliquez sur **requête avec la connexion actuelle** pour démarrer l’éditeur de requête SQL.  
  
4.  Copiez l’exemple de script à partir de [Script SQL des groupes de fichiers de base de données BizTalk Server MessageBox](../technical-guides/biztalk-server-messagebox-database-filegroups-sql-script.md) dans l’éditeur de requête.  
  
5.  Modifiez les paramètres dans le script à votre environnement BizTalk Server et exécutez le script.  
  
 L’avantage de script est que les scripts peuvent effectuer plusieurs tâches rapidement et peuvent être reproduites avec précision et réduisent le risque d’erreur humaine. L’inconvénient d’un script est que l’exécution d’un script écrit correctement peut entraîner de graves problèmes, lesquels nécessitent les bases de données BizTalk Server être reconfigurée à partir de zéro.  
  
> [!IMPORTANT]  
>  Il s’agit d’une importance capitale que SQL scripts tels que l’exemple de script dans ce guide sont testées avant d’être exécutées dans un environnement de production.  
  
## <a name="see-also"></a>Voir aussi  
 [Optimisation des performances des bases de données](../technical-guides/optimizing-database-performance.md)