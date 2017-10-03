---
title: "À la Configuration de base de données Optimizations1 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 763b5358-97ed-4ada-8318-0ad07388ba89
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: eeb1c5c8bbb93bce5eb69462585c2da69d587dad
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="post-configuration-database-optimizations"></a>Optimisations de la base de données à la Configuration
En plus des recommandations de [optimisations de base de données de Configuration préalable](../technical-guides/post-configuration-database-optimizations1.md), plusieurs étapes à suivre pour optimiser les performances de base de données BizTalk Server sur SQL Server *après* BizTalk Server a été installé et les bases de données BizTalk Server ont été configurés. Cette rubrique fournit une liste de ces optimisations.  
  
## <a name="pre-allocate-space-for-biztalk-server-databases-and-define-auto-growth-settings-for-biztalk-server-databases-to-a-fixed-value-instead-of-a-percentage-value"></a>Préallouer de l’espace pour les bases de données BizTalk Server et de définir les paramètres de croissance automatique pour les bases de données BizTalk Server sur une valeur fixe au lieu d’une valeur de pourcentage  
  
-   Croissance automatique de base de données SQL Server est une opération de blocage qui entraîne une dégradation des performances de base de données BizTalk Server. Par conséquent, il est important d’en allouer suffisamment d’espace pour les bases de données BizTalk Server à l’avance afin de réduire la fréquence de croissance automatique de la base de données.  
  
-   La croissance automatique de la base de données doit être définie sur un nombre fixe de mégaoctets au lieu d’un pourcentage (spécifier la croissance des fichiers **en mégaoctets**). Cela doit être fait donc si la croissance automatique se produit, il le fait de façon mesurée ce qui réduit la probabilité d’une croissance excessive de la base de données. L’incrément de croissance doit généralement pas être supérieur à 100 Mo (pour les fichiers volumineux), 10 Mo (pour les fichiers de taille moyenne) ou 1 Mo (pour les petits fichiers).  
  
-   Lorsque SQL Server augmente la taille d’un fichier, le nouvel espace doit tout d’abord être initialisé avant de pouvoir être utilisé. Il s’agit d’une opération de blocage qui implique le remplissage du nouvel espace de pages vides. SQL Server 2005 sur Windows Server 2003 ou version ultérieure prend en charge le « initialisation instantanée des fichiers. » Cela peut considérablement réduire l’impact sur les performances d’une opération de croissance de fichier. Pour plus d’informations, consultez « Initialisation du fichier de base de données » dans la documentation de SQL Server 2008 à [http://go.microsoft.com/fwlink/?LinkId=132063](http://go.microsoft.com/fwlink/?LinkId=132063). Cette rubrique explique comment activer l’initialisation instantanée des fichiers.  
  
## <a name="move-the-backup-biztalk-server-output-directory-to-a-dedicated-lun"></a>Déplacer le répertoire de sortie de sauvegarde de BizTalk Server à un numéro d’unité logique dédié  
 Déplacer le répertoire de sortie de sauvegarde de BizTalk Server (sauvegarde complète et de journal) au numéro d’unité logique dédié, modifiez les étapes 1 et 2 (Insérer nouveau chemin de sortie) de la tâche de sauvegarde de BizTalk Server [BizTalkMgmtDb]. Déplacer le répertoire de sortie de sauvegarde de BizTalk Server à un numéro d’unité logique dédié réduira la contention d’e/s de disque lors de l’exécution du travail en écrivant sur un disque différent de celui de la tâche de lecture à partir de.  
  
## <a name="verify-the-biztalk-server-sql-agent-jobs-are-running"></a>Vérifiez que les travaux de l’Agent SQL de BizTalk Server sont en cours d’exécution.  
 BizTalk Server inclut plusieurs travaux de l’Agent SQL Server qui exécutent des fonctions importantes pour conserver vos serveurs de fonctionnement. Vous devez surveiller l’intégrité de ces travaux et assurez-vous qu’ils sont en cours d’exécution sans erreurs. Une des causes plus courantes des problèmes de performances dans BizTalk Server est les travaux de l’Agent SQL de BizTalk Server ne sont pas en cours d’exécution, ce qui à son tour la peut entraîner la MessageBox et suivi des bases de données à croissance est désactivée. Suivez ces étapes pour vérifier que les travaux de l’Agent SQL de BizTalk Server s’exécutent sans problème :  
  
 Une des causes plus courantes des problèmes de performances dans BizTalk Server est les travaux de l’Agent SQL de BizTalk Server ne sont pas en cours d’exécution, ce qui à son tour la peut entraîner la MessageBox et suivi des bases de données à croissance est désactivée. Suivez ces étapes pour vérifier que les travaux de l’Agent SQL de BizTalk Server s’exécutent sans problème :  
  
-   **Vérifiez que le service SQL Server Agent est en cours d’exécution**.  
  
-   **Vérifiez que les travaux de l’Agent SQL Server installés par BizTalk Server sont activés et en cours d’exécution avec succès**.  
  
     Les travaux de SQL Server Agent BizTalk Server sont essentiels, s’ils n’exécutent pas, les performances du système se dégradent au fil du temps.  
  
-   **Vérifiez que les travaux de SQL Server Agent BizTalk Server sont achèvent en temps voulu**.  
  
     Configurer Microsoft Operations Manager (MOM) 2005 ou Microsoft System Center Operations Manager 2007 pour surveiller les travaux.  
  
     Vous devez être conscient des planifications qui sont spécifiques à certaines tâches :  
  
    -   Le travail MessageBox_Message_ManageRefCountLog_BizTalkMsgBoxDb s’exécute en continu par défaut. Logiciel de surveillance doit tenir compte de cette planification et pas génèrent des avertissements.  
  
    -   Le travail MessageBox_Message_Cleanup_BizTalkMsgBoxDb n’est pas activé ou planifié, mais elle est démarrée par le travail MessageBox_Message_ManageRefCountLog_BizTalkMsgBoxDb toutes les 10 secondes. Par conséquent, cette tâche de ne doit pas être activée, planifiée ou démarrée manuellement.  
  
-   **Vérifiez le type de démarrage du service SQL Server Agent est configuré correctement**.  
  
     Vérifiez que le service SQL Server Agent est configuré avec un **type de démarrage** de **automatique** , sauf si le service de l’Agent SQL Server est configuré en tant que ressource de cluster sur un cluster Windows Server. Si le service de l’Agent SQL Server est configuré en tant que ressource de cluster, vous devez configurer le **type de démarrage** en tant que **manuel** , car le service est géré par le service de Cluster.  
  
## <a name="configure-purging-and-archiving-of-tracking-data"></a>Configurer l’archivage des données de suivi et la purge  
 Suivez ces étapes pour vous assurer que la purge et d’archivage de données de suivi sont configuré correctement :  
  
-   Vérifiez que le travail de l’Agent SQL « DTA Purge et archivage » est correctement configuré, activé et exécution. Pour plus d’informations, consultez « Comment pour configurer le DTA Purge et Archive la tâche » dans la documentation de BizTalk Server à [http://go.microsoft.com/fwlink/?LinkId=104908](http://go.microsoft.com/fwlink/?LinkId=104908).  
  
-   Vérifiez que le travail est en mesure de purger les données de suivi aussi vite que les données de suivi entrantes sont générées. Pour plus d’informations, consultez « Mesure de débit maximal acceptable de suivi » dans la documentation de BizTalk Server 2006 R2 à [http://go.microsoft.com/fwlink/?LinkId=104909](http://go.microsoft.com/fwlink/?LinkId=104909).  
  
-   Passez en revue la purge normale et les paramètres de purge dur afin de que vous conservez les données pendant la durée optimale. Pour plus d’informations, consultez « L’archivage et purge le suivi des base de données BizTalk » dans la documentation de BizTalk Server à [http://go.microsoft.com/fwlink/?LinkId=101585](http://go.microsoft.com/fwlink/?LinkId=101585).  
  
-   Si vous devez uniquement purger les anciennes données et ne pas pour archiver les modifications tout d’abord, l’Agent SQL la fonction pour appeler la procédure stockée « dtasp_PurgeTrackingDatabase. » Pour plus d’informations, consultez « Comment purger les données à partir de la BizTalk suivi base de données » dans la documentation de BizTalk Server à [http://go.microsoft.com/fwlink/?LinkId=101584](http://go.microsoft.com/fwlink/?LinkId=101584).  
  
## <a name="monitor-and-reduce-dtc-log-file-disk-io-contention"></a>Contrôler et réduire la contention d’e/s de DTC journal fichier sur le disque  
 Le fichier journal de Microsoft Distributed Transaction Coordinator (MS DTC) peut devenir un goulot d’étranglement d’e/s de disque dans des environnements riches en transactions. Cela est particulièrement vrai lors de l’utilisation des adaptateurs qui prennent en charge les transactions, telles que SQL Server, MSMQ ou MQSeries, ou dans un environnement multi-MessageBox. Adaptateurs transactionnels utilisent les transactions DTC et les environnements de multi-MessageBox utilisent beaucoup des transactions DTC. Pour garantir que le fichier journal DTC ne devient-elle pas un goulet d’étranglement d’e/s de disque, vous devez surveiller l’utilisation d’e/s pour le disque contenant le fichier journal DTC sur les serveurs de base de données SQL Server du disque. Si le disque, l’utilisation des e/s pour le disque où se trouve le fichier journal DTC devient excessive puis déplacez le fichier journal DTC sur un disque plus rapide. Dans un environnement où SQL Server est en cluster, il n’est pas autant d’un critère important, car le fichier journal sera déjà sur un lecteur partagé, qui sera probablement un lecteur SAN rapide avec plusieurs piles. Vous devez néanmoins toujours surveiller l’utilisation des e/s disque, car il peut devenir un goulot d’étranglement dans les environnements non cluster ou quand le service DTC se fichier se trouve sur un disque partagé avec d’autres fichiers de disques de manière intensive.  
  
 Pour garantir que le fichier journal DTC ne devient-elle pas un goulet d’étranglement d’e/s de disque, vous devez surveiller l’utilisation d’e/s pour le disque contenant le fichier journal DTC sur les serveurs de base de données SQL Server du disque. Si le disque, l’utilisation des e/s pour le disque où se trouve le fichier journal DTC devient excessive, puis déplacez le fichier journal DTC vers un disque plus rapide.  
  
 Dans un environnement où SQL Server est en cluster, il n’est pas autant d’un critère important, car le fichier journal sera déjà sur un lecteur partagé, qui sera probablement un lecteur SAN rapide avec plusieurs piles. Vous devez néanmoins toujours surveiller l’utilisation des e/s disque, car il peut devenir un goulot d’étranglement dans les environnements non cluster ou quand le service DTC se fichier se trouve sur un disque partagé avec d’autres fichiers de disques de manière intensive.  
  
## <a name="separate-the-messagebox-and-tracking-databases"></a>Séparer la MessageBox et le suivi des bases de données  
 Étant donné que les bases de données BizTalk MessageBox et des suivis BizTalk sont les plus actifs, nous vous recommandons de que vous placez les fichiers de données et les fichiers journaux des transactions pour chacun d’eux sur des lecteurs dédiés pour réduire le risque de problèmes de contention d’e/s de disque. Par exemple, vous devez quatre disques pour les fichiers de base de données MessageBox et des suivis BizTalk, un pour chacun des éléments suivants :  
  
-   Fichiers de données MessageBox  
  
-   Fichiers de journaux de transactions de MessageBox  
  
-   Fichiers de données de suivi BizTalk (DTA)  
  
-   Fichiers journaux de transactions de suivi BizTalk (DTA)  
  
 Séparer les bases de données BizTalk MessageBox et des suivis BizTalk et en séparant les fichiers de base de données et les fichiers journaux des transactions sur des disques différents sont considérés comme des meilleures pratiques pour réduire la contention d’e/s disque. Essayez afin de répartir l’e/s disque piles de disques physiques autant que possible. Vous pouvez également réduire la contention d’e/s de disque en plaçant la base de données des suivis BizTalk sur un serveur SQL dédié, toutefois, vous devez toujours de suivre les pratiques ci-dessus en ce qui concerne la séparation des fichiers de données et fichiers journaux des transactions.  
  
## <a name="optimize-filegroups-for-the-biztalk-server-databases"></a>Optimiser les groupes de fichiers pour les bases de données BizTalk Server  
 Suivez les étapes de [optimisation de groupes de fichiers pour le Databases1](../technical-guides/optimizing-filegroups-for-the-databases1.md) et le livre blanc « Optimisation de base de données BizTalk Server » [http://go.microsoft.com/fwlink/? LinkId = 101578](http://go.microsoft.com/fwlink/?LinkId=101578) pour créer des groupes de fichiers supplémentaires et des fichiers pour les bases de données BizTalk Server. Cela augmente considérablement les performances des bases de données BizTalk Server à partir d’une configuration de disque unique.