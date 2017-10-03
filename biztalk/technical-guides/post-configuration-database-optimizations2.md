---
title: "À la Configuration de base de données Optimizations2 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 609eda22-8399-4b7c-b860-21b495d2f68d
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 168323f1e7dfdbb796fe29e0025c5d2a6f40c957
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="post-configuration-database-optimizations"></a>Optimisations de la base de données à la Configuration
En plus des recommandations de [Optimizations2 de base de données de Configuration préalable](../technical-guides/pre-configuration-database-optimizations2.md), plusieurs étapes à suivre pour optimiser les performances de base de données BizTalk Server sur SQL Server *après* BizTalk Server a été installé et les bases de données BizTalk Server ont été configurés. Cette rubrique fournit une liste de ces optimisations.  
  
## <a name="consider-setting-the-text-in-row-table-option-on-specific-messagebox-database-tables"></a>Envisagez de définir l’option de table 'text in row' sur des tables de base de données MessageBox spécifiques  
 SQL Server fournit une option de table appelée **texte dans la ligne** pour déclarer que le contenu des champs de type **texte**, **ntext**, ou **image** les données dont les dimensions sont inférieures à celles d’une page de données (8 Ko) doivent être stockées dans une ligne de données. En définissant cette option sur les tables BizTalkMsgBoxDb (table des parties, table du spouleur et DynamicStateInfo Tables), vous pouvez augmenter le débit des messages lorsque vous travaillez avec des messages de petite taille qui ont un contexte de petite et des orchestrations qui ont une taille de la persistance de petits.  
  
-   **Table de pièces**: lorsque la taille du message est plus petit que les dimensions d’une page de données de 8 Ko, appliquer la **texte dans la ligne** option de table sur la table des parties risque d’amélioration des performances de BizTalk Server. La table des parties contient les champs suivants :  
  
    -   **ImgPart**: contient un fragment de partie de message ou de la partie message.  
  
    -   **ImgPropBag**: contient le jeu de propriétés de partie de message.  
  
     De cette manière, lors de la boucle par rapport à la MessageBox, l’Agent des messages en cours d’exécution dans un hôte BizTalk peut récupérer un lot de messages à partir de la table des parties en lisant la petite quantité de pages. Selon le scénario spécifique et la configuration matérielle, cette technique peut réduire l’utilisation du processeur à la fois sur SQL Server et BizTalk Server et fournir une amélioration significative en termes de latence et le débit.  
  
-   **Table de spoule**: lorsque la taille moyenne du contexte de message est inférieure à 8 Ko, l’activation de la **texte dans la ligne** option de table sur la table Spool vous permet de réduire le nombre d’accès lors de la lecture de messages à partir de la MessageBox le long avec leur contexte. Pour appliquer cette option à la table du spouleur, vous devez éliminer les propriétés de contexte inutiles et les champs distinctifs afin de réduire la taille du contexte du message est inférieure à 8 Ko.  
  
-   **Les Tables DynamicStateInfo** ces tables, une pour chaque hôte, contient un champ de type image appelé imgData qui contient l’état de l’orchestration de binaire sérialisé lorsqu’elles rencontrent un point de persistance lors de leur exécution. Lorsque l’état interne d’orchestrations dans un hôte HostA est si petit que sa taille qu’une seule fois sérialisé est inférieure à 8 Ko, le **texte dans la ligne** technique correctement peut être appliquée à la table DynamicStateInfo_HostA. Par conséquent, nous vous recommandons de conserver l’état interne d’orchestrations aussi petite que possible. Cette technique peut réduire considérablement le temps passé par le moteur XLANG à sérialiser, rendre persistants, désérialiser et restaurer l’état interne d’une orchestration en cas de point de persistance.  
  
 Nous avons utilisé les paramètres suivants dans nos tests de laboratoire :  
  
-   EXEC sp_tableoption N'Spool', 'text in row', '6000'  
  
-   EXEC sp_tableoption de N'Parts, 'text in row', '6000'  
  
## <a name="define-auto-growth-settings-for-biztalk-server-databases-to-a-fixed-value-instead-of-a-percentage-value"></a>Définir les paramètres de croissance automatique pour les bases de données BizTalk Server sur une valeur fixe au lieu d’une valeur de pourcentage  
  
-   Croissance automatique de base de données SQL Server est une opération de blocage, ce qui entraîne une dégradation des performances de base de données BizTalk Server. Par conséquent, il est important d’en allouer suffisamment d’espace pour les bases de données BizTalk Server à l’avance afin de réduire la fréquence de croissance automatique de la base de données.  
  
-   La croissance automatique de la base de données doit être définie sur un nombre fixe de mégaoctets au lieu d’un pourcentage (spécifier la croissance des fichiers **en mégaoctets**). Cela doit être effectuée, afin que, si la croissance automatique se produit, il le fait de manière mesuré. Cela réduit la probabilité d’une croissance excessive de la base de données. L’incrément de croissance pour les bases de données BizTalk Server doit généralement être non inférieure à 100 Mo.  
  
## <a name="pre-size-biztalk-server-databases-to-appropriate-size-with-multiple-data-files"></a>La taille des bases de données BizTalk Server de taille appropriées avec plusieurs fichiers de données  
 Lorsque SQL Server augmente la taille d’un fichier, il doit d’abord initialiser le nouvel espace avant de pouvoir être utilisé. Il s’agit d’une opération de blocage qui implique le remplissage du nouvel espace de pages vides. SQL Server 2005 ou version ultérieure sur Windows Server 2003 ou version ultérieure prend en charge le « initialisation instantanée des fichiers. » Cela peut considérablement réduire l’impact sur les performances d’une opération de croissance de fichier. Pour plus d’informations, consultez [l’initialisation des fichiers de base de données](http://go.microsoft.com/fwlink/?LinkId=132063) (http://go.microsoft.com/fwlink/?LinkId=132063) dans la documentation en ligne de SQL Server. Cette rubrique explique comment activer l’initialisation instantanée des fichiers.  
  
 La liste suivante décrit les configurations de base de données BizTalk Server utilisées dans nos tests de laboratoire :  
  
-   **BizTalk DTADB (fichiers de base de données des suivis BizTalk) :** le fichier de données ayant une taille de 2 048 Mo, avec une croissance de 100 Mo et un fichier journal de 1 024 Mo avec une croissance de 100 Mo.  
  
-   **BizTalkMgmtdb (fichiers de base de données de gestion BizTalk) :** le fichier de données ayant une taille de fichier de 512 Mo, avec une croissance de 100 Mo et un fichier journal de 512 Mo avec une croissance de 100 Mo.  
  
-   **SSODB :** le fichier de données ayant une taille de fichier de 512 Mo, avec une croissance de 100 Mo et un fichier journal de 512 Mo avec une croissance de 100 Mo.  
  
-   **BizTalkMsgBoxDb (bases de données BizTalk MessageBox) :** les fichiers de données de 8, chacun ayant une taille de 2 Go avec une croissance de 100 Mo et un fichier journal de 20 Go avec une croissance de 100 Mo. Étant donné que les bases de données BizTalk MessageBox sont les plus actifs, nous vous recommandons de que vous placez les fichiers de données et les fichiers journaux des transactions sur des lecteurs dédiés pour réduire le risque de problèmes de contention d’e/s de disque. Dans notre environnement de laboratoire, nous avons utilisé un lecteur pour chacun des éléments suivants :  
  
    -   Fichiers de données MessageBox  
  
    -   Fichiers journaux des transactions MessageBox  
  
 Le script SQL suivant peut servir à la taille des BizTalkMsgBoxDb ayant initialement un fichier de données sur le lecteur J (J:\BizTalkMsgBoxDb.mdf) et un fichier journal sur le lecteur K (K:\BizTalkMsgBoxDb_log. LDF) :  
  
> [!IMPORTANT]  
>  Ce script est fourni « en l’état, » est destinée uniquement à titre éducatif de démonstration ou et doit être utilisé à vos propres risques. Utilisation de ce script n’est pas prise en charge par Microsoft et Microsoft n’apporte aucune garantie quant à l’adéquation de ce script.  
  
```  
EXEC dbo.sp_helpdb BizTalkMsgBoxDb  
ALTER DATABASE BizTalkMsgBoxDb MODIFY FILE (NAME = BizTalkMsgBoxDb , FILENAME = 'J:\BizTalkMsgBoxDb.mdf' , SIZE = 2GB , FILEGROWTH = 100MB)  
ALTER DATABASE BizTalkMsgBoxDb ADD FILE    (NAME = BizTalkMsgBoxDb_2 , FILENAME = 'J:\BizTalkMsgBoxDb_2.ndf' , SIZE = 2GB , FILEGROWTH = 100MB)  
ALTER DATABASE BizTalkMsgBoxDb ADD FILE    (NAME = BizTalkMsgBoxDb_3 , FILENAME = 'J:\BizTalkMsgBoxDb_3.ndf' , SIZE = 2GB , FILEGROWTH = 100MB)  
ALTER DATABASE BizTalkMsgBoxDb ADD FILE    (NAME = BizTalkMsgBoxDb_4 , FILENAME = 'J:\BizTalkMsgBoxDb_4.ndf' , SIZE = 2GB , FILEGROWTH = 100MB)  
ALTER DATABASE BizTalkMsgBoxDb ADD FILE    (NAME = BizTalkMsgBoxDb_5 , FILENAME = 'J:\BizTalkMsgBoxDb_5.ndf' , SIZE = 2GB , FILEGROWTH = 100MB)  
ALTER DATABASE BizTalkMsgBoxDb ADD FILE    (NAME = BizTalkMsgBoxDb_6 , FILENAME = 'J:\BizTalkMsgBoxDb_6.ndf' , SIZE = 2GB , FILEGROWTH = 100MB)  
ALTER DATABASE BizTalkMsgBoxDb ADD FILE    (NAME = BizTalkMsgBoxDb_7 , FILENAME = 'J:\BizTalkMsgBoxDb_7.ndf' , SIZE = 2GB , FILEGROWTH = 100MB)  
ALTER DATABASE BizTalkMsgBoxDb ADD FILE    (NAME = BizTalkMsgBoxDb_8 , FILENAME = 'J:\BizTalkMsgBoxDb_8.ndf' , SIZE = 2GB , FILEGROWTH = 100MB)  
GO  
ALTER DATABASE BizTalkMsgBoxDb MODIFY FILE (NAME = BizTalkMsgBoxDb_log , FILENAME = 'K:\BizTalkMsgBoxDb_log.LDF', SIZE =  20GB , FILEGROWTH = 100MB)  
GO  
```  
  
## <a name="move-the-backup-biztalk-server-output-directory-to-a-dedicated-lun"></a>Déplacer le répertoire de sortie de sauvegarde de BizTalk Server à un numéro d’unité logique dédié  
 Déplacer le répertoire de sortie de sauvegarde de BizTalk (sauvegarde complète et de journal) à un numéro d’unité logique dédié, puis modifiez la tâche de sauvegarde de BizTalk Server pour pointer vers le numéro d’unité logique dédié. Déplacer le répertoire de sortie de sauvegarde de BizTalk Server à un numéro d’unité logique dédié réduira la contention d’e/s de disque lors de l’exécution du travail en écrivant sur un disque différent de celui de la tâche de lecture à partir de. Pour plus d’informations sur la configuration de la tâche de sauvegarde de BizTalk Server, consultez [comment configurer le travail de sauvegarde de BizTalk Server](http://go.microsoft.com/fwlink/?LinkID=153813) (http://go.microsoft.com/fwlink/?LinkID=153813) dans l’aide de BizTalk Server 2010.  
  
## <a name="verify-that-the-biztalk-server-sql-agent-jobs-are-running"></a>Vérifiez que les travaux de l’Agent SQL de BizTalk Server sont en cours d’exécution.  
 BizTalk Server inclut plusieurs travaux de l’Agent SQL Server qui exécutent des fonctions importantes pour conserver vos serveurs de fonctionnement. Vous devez surveiller l’intégrité de ces travaux et assurez-vous qu’ils sont en cours d’exécution sans erreurs. Une des causes plus courantes des problèmes de performances dans BizTalk Server est les travaux de l’Agent SQL de BizTalk Server ne sont pas en cours d’exécution, ce qui à son tour la peut entraîner la MessageBox et suivi des bases de données à croissance est désactivée. Suivez ces étapes pour vérifier que les travaux de l’Agent SQL de BizTalk Server s’exécutent sans problème :  
  
1.  **Vérifiez que le service SQL Server Agent est en cours d’exécution**.  
  
2.  **Vérifiez que les travaux de l’Agent SQL Server installés par BizTalk Server sont activés et en cours d’exécution avec succès**.  
    Les travaux de SQL Server Agent BizTalk Server sont cruciaux : s’ils n’exécutent pas, les performances du système se dégradent au fil du temps.  
  
3.  **Vérifiez que les travaux de SQL Server Agent BizTalk Server sont achèvent en temps voulu**.   
    Configurer la version la plus récente de Microsoft System Center Operations Manager pour surveiller les travaux.  
    Vous devez être conscient des planifications qui sont spécifiques à certaines tâches :  
  
    -   Le travail MessageBox_Message_ManageRefCountLog_BizTalkMsgBoxDb s’exécute en continu par défaut. Logiciel de surveillance doit tenir compte de cette planification et pas génèrent des avertissements.  
  
    -   Le travail MessageBox_Message_Cleanup_BizTalkMsgBoxDb n’est pas activé ou planifié, mais elle est démarrée par le travail MessageBox_Message_ManageRefCountLog_BizTalkMsgBoxDb toutes les 10 secondes. Par conséquent, cette tâche de ne doit pas être activée, planifiée ou démarrée manuellement.  
  
4.  **Vérifiez que le type de démarrage du service SQL Server Agent est configuré correctement**.  
    Vérifiez que le service SQL Server Agent est configuré avec un **type de démarrage** de **automatique** , sauf si le service de l’Agent SQL Server est configuré en tant que ressource de cluster sur un cluster Windows Server. Si le service de l’Agent SQL Server est configuré en tant que ressource de cluster, vous devez configurer le **type de démarrage** en tant que **manuel** , car le service est géré par le service de Cluster.  
  
## <a name="configure-purging-and-archiving-of-tracking-data"></a>Configurer l’archivage des données de suivi et la purge  
 Suivez ces étapes pour vous assurer que la purge et d’archivage de données de suivi sont configuré correctement :  
  
1.  Vérifiez que le travail de l’Agent SQL « DTA Purge et archivage » est correctement configuré, activé et exécution. Pour plus d’informations, consultez [la configuration de la Purge et archivage](http://go.microsoft.com/fwlink/?LinkID=153814) (http://go.microsoft.com/fwlink/?LinkID=153814) dans la documentation de BizTalk Server.  
  
2.  Vérifiez que le travail est en mesure de purger les données de suivi aussi vite que les données de suivi entrantes sont générées. Pour plus d’informations, consultez [mesure de débit maximal acceptable de suivi](http://go.microsoft.com/fwlink/?LinkID=153815) (http://go.microsoft.com/fwlink/?LinkID=153815) dans la documentation de BizTalk Server.  
  
3.  Passez en revue la purge normale et les paramètres de purge dur afin de que vous conservez les données pendant la durée optimale. Pour plus d’informations, consultez [l’archivage et la purge de la base de données de suivi BizTalk](http://go.microsoft.com/fwlink/?LinkID=153816) (http://go.microsoft.com/fwlink/?LinkID=153816) dans la documentation de BizTalk Server.  
  
4.  Si vous devez uniquement purger les anciennes données et ne pas pour archiver les modifications tout d’abord, l’Agent SQL la fonction pour appeler la procédure stockée « dtasp_PurgeTrackingDatabase. » Pour plus d’informations, consultez [comment vider les données à partir de la base de données de suivi BizTalk](http://go.microsoft.com/fwlink/?LinkID=153817) (http://go.microsoft.com/fwlink/?LinkID=153817) dans la documentation de BizTalk Server.  
  
## <a name="monitor-and-reduce-dtc-log-file-disk-io-contention"></a>Contrôler et réduire la contention d’e/s de DTC journal fichier sur le disque  
 Le fichier journal de coordinateur de transactions distribuées (DTC, Distributed Transaction Coordinator) peut devenir un goulot d’étranglement d’e/s de disque dans des environnements riches en transactions. Cela est particulièrement vrai lors de l’utilisation des adaptateurs qui prennent en charge les transactions, telles que SQL Server, MSMQ ou MQSeries, ou dans un environnement multi-MessageBox. Adaptateurs transactionnels utilisent les transactions DTC et les environnements de multi-MessageBox utilisent beaucoup des transactions DTC. Pour garantir que le fichier journal DTC ne devient-elle pas un goulet d’étranglement d’e/s de disque, vous devez surveiller l’utilisation d’e/s pour le disque contenant le fichier journal DTC sur les serveurs de base de données SQL Server du disque. Si le disque, l’utilisation des e/s pour le disque où se trouve le fichier journal DTC devient excessive, déplacez le fichier journal DTC sur un disque plus rapide. Dans un environnement où SQL Server est en cluster, il n’est pas autant d’un critère important, car le fichier journal sera déjà sur un lecteur partagé, qui sera probablement un lecteur SAN rapide avec plusieurs piles. Vous devez néanmoins toujours surveiller l’utilisation des e/s disque. Il s’agit, car il peut devenir un goulot d’étranglement dans les environnements non cluster ou lorsque le fichier journal DTC est sur un disque partagé avec d’autres fichiers de disques de manière intensive.  
  
## <a name="separate-the-messagebox-and-tracking-databases"></a>Séparer la MessageBox et le suivi des bases de données  
 Étant donné que les bases de données BizTalk MessageBox et des suivis BizTalk sont les plus actifs, nous vous recommandons de que vous placez les fichiers de données et les fichiers journaux des transactions pour chacun d’eux sur des lecteurs dédiés pour réduire le risque de problèmes de contention d’e/s de disque. Par exemple, vous devez quatre disques pour les fichiers de base de données MessageBox et des suivis BizTalk, un pour chacun des éléments suivants :  
  
-   Fichiers de données MessageBox  
  
-   Fichiers journaux des transactions MessageBox  
  
-   Fichiers de données de suivi BizTalk (DTA)  
  
-   Fichiers journaux des transactions de suivi BizTalk (DTA)  
  
 Séparer les bases de données BizTalk MessageBox et des suivis BizTalk et en séparant les fichiers de base de données et les fichiers journaux des transactions sur des disques différents sont considérés comme des meilleures pratiques pour réduire la contention d’e/s disque. Essayez afin de répartir l’e/s disque piles de disques physiques autant que possible. Vous pouvez également réduire la contention d’e/s de disque en plaçant la base de données des suivis BizTalk sur un serveur SQL dédié ; Toutefois, vous devez toujours suivre les pratiques ci-dessus en ce qui concerne la séparation des fichiers de données et fichiers journaux des transactions.  
  
## <a name="optimize-filegroups-for-the-biztalk-server-databases"></a>Optimiser les groupes de fichiers pour les bases de données BizTalk Server  
 Suivez les étapes de [optimisation de groupes de fichiers pour le Databases2](../technical-guides/optimizing-filegroups-for-the-databases2.md) et [l’optimisation de base de données BizTalk Server](http://go.microsoft.com/fwlink/?LinkId=101578) livre blanc ([http://go.microsoft.com/fwlink/? LinkId = 101578](http://go.microsoft.com/fwlink/?LinkId=101578)) pour créer des groupes de fichiers supplémentaires et des fichiers pour les bases de données BizTalk Server. Cela augmente considérablement les performances des bases de données BizTalk Server à partir d’une configuration de disque unique.  
  
## <a name="see-also"></a>Voir aussi  
 [Optimisation des performances de la base de données](../technical-guides/optimizing-database-performance.md)