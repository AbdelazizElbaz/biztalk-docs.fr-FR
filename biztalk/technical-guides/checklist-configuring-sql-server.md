---
title: "Liste de vérification : Configuration de SQL Server | Documents Microsoft"
ms.custom: 
ms.date: 06/29/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: edd20f24-8a72-40b7-abee-81fbd3ceefda
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8f6c67fcdee26afd6ec9bb1016e86a98b1cf26e8
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="checklist-configuring-sql-server"></a>Liste de vérification : Configuration de SQL Server
Étapes à suivre lors de la préparation de SQL Server pour les utilisent dans un environnement de production BizTalk Server.    
 
<a name="BKMK_Config"></a>   
## <a name="configuring-sql-server"></a>Configuration de SQL Server  
  
|Étapes|Référence|  
|-----------|---------------|  
|Surveiller et de réduire la contention de disque d’e/s de fichiers de base de données BizTalk Server.|-Nous vous recommandons de proactive surveiller l’utilisation des e/s disque pour les disques qui hébergent les fichiers journaux de transaction et de données.<br />-Il est recommandé que les fichiers de données et les fichiers journaux des transactions pour chacun d’eux être placé sur des lecteurs dédiés pour réduire la probabilité de contention d’e/s disque devient un problème.<br />-Vous pouvez réduire la contention d’e/s de disque en séparant les bases de données MessageBox et de suivi (DTA) et en séparant les fichiers de base de données et les fichiers journaux des transactions sur des disques physiques.<br /><br /> Pour plus d’informations, consultez [analyse et réduire les conflits de base de données e/s](monitoring-and-reducing-database-i-o-contention.md)|  
|Assurez-vous que SQL Server est configuré sur des partitions correctement aligné|Correctement alignée disque partitions peut entraîner une diminution considérable de latence, ce qui améliore les performances de SQL Server, ce qui à son tour améliore les performances de BizTalk Server. En revanche, les partitions de disque non aligné peuvent nuire aux performances d’e/s, ce qui dégrade les performances de SQL Server et BizTalk Server.<br /><br /> Pour plus d’informations sur les partitions de disque comment correctement alignée clairement peut affecter les performances, consultez [disque Partition alignement meilleures pratiques pour SQL Server](http://go.microsoft.com/fwlink/?LinkId=154073).|  
|Conserver les événements que vous surveillez avec le Générateur de profils SQL Server|Utiliser SQL Server Profiler pour surveiller uniquement les événements qui vous intéressent. Si les traces deviennent trop volumineux, vous pouvez filtrer en fonction des informations que vous le souhaitez, afin que seul un sous-ensemble des données d’événement est collecté. La surveillance d'un trop grand nombre d'événements s'ajoute à la charge du serveur et du processus de surveillance, et peut considérablement accroître la taille du fichier ou de la table de trace, en particulier si le processus de surveillance se prolonge sur une période importante.|  
|Contrôler et réduire les contentions d’e/s de DTC journal fichier disque.|[Analyse et réduire la Contention d’e/s de DTC journal fichier sur le disque](monitoring-and-reducing-dtc-log-file-disk-i-o-contention.md)|  
|Fournir une haute disponibilité pour les bases de données SQL Server.|[Planification de la disponibilité des bases de données](planning-for-database-availability.md)|  
|Passez en revue la configuration de cluster actif/actif SQL Server pour les scénarios de basculement.|[Examen et test de la configuration du cluster SQL Server pour les scénarios de basculement](reviewing-and-testing-sql-server-cluster-configuration-for-failover-scenarios.md)|  
|Utilisez les paramètres de configuration par défaut pour :<br /><br /> -Degré maximal de parallélisme (MDOP).<br />-Statistiques SQL Server sur la base de données MessageBox de BizTalk Server.<br />-Les reconstructions d’index de base de données SQL Server et de la défragmentation.|[Paramètres de SQL Server qui ne doivent pas être modifiés](sql-server-settings-that-should-not-be-changed.md)|  
|Activer l’indicateur de trace 1118 (TF1118) en tant que paramètre de démarrage pour toutes les instances de SQL Server.|Implémentation TF1118 permet de réduire la contention parmi les instances de SQL Server en supprimant presque toutes les allocations de page unique. Pour plus d’informations, consultez Base de connaissances Microsoft l’article [améliorations de la concurrence pour la base de données tempdb](https://support.microsoft.com/en-us/help/328551/concurrency-enhancements-for-the-tempdb-database). <br/><br/>**Remarque :** pour plus d’informations sur, consultez TF1118 [à tort autour de TF1118](https://www.sqlskills.com/blogs/paul/misconceptions-around-tf-1118/). Notez que le contenu au niveau de ce lien n’est pas détenu par Microsoft et Microsoft ne garantit pas l’exactitude du contenu.|  
|Fractionner la base de données tempdb en plusieurs fichiers de données de taille égale sur chaque instance de SQL Server utilisée par BizTalk Server.|Assurez-vous que les fichiers de données utilisés pour la base de données tempdb sont de taille égale. Ceci est très important, car l’algorithme de remplissage proportionnel utilisé par SQL Server est basée sur la taille des fichiers de données. Si les fichiers de données sont créés avec la taille inégale, l’algorithme de remplissage proportionnel utilisera le fichier le plus volumineux plus pour les allocations d’Allocation GAM (Global Map) plutôt qu’en se propageant les allocations entre tous les fichiers, invalidant ainsi le but de créer plusieurs fichiers de données. En règle générale, créez un fichier de données pour chaque UC sur le serveur, puis réglez le nombre de fichiers vers le haut ou vers le bas si nécessaire. Notez qu'une UC à double noyau est traitée comme deux UC distinctes. Dans tous les cas, le nombre de fichiers de données ne doit pas être supérieur à 8, quel que soit le nombre de cœurs supplémentaires sont disponibles sur l’ordinateur. Pour plus d’informations sur les fichiers de tempdb, consultez [optimisation des performances de tempdb](https://docs.microsoft.com/sql/relational-databases/databases/tempdb-database).|  
|Définir le Minimum et instance(s) de mémoire maximale du serveur pour les mêmes valeurs sur le serveur SQL Server qui hébergent les bases de données BizTalk Server.|Les ordinateurs exécutant SQL Server qui hébergent les bases de données BizTalk Server doivent être dédiés à l’exécution de SQL Server. Lorsque les ordinateurs exécutant SQL Server qui hébergent le serveur BizTalk Server des bases de données **sont** dédié à l’exécution de SQL Server, il est recommandé que le « min server memory » et « max server memory » options sur chaque instance de SQL Server soit configuré pour spécifier la quantité fixe de mémoire à allouer à SQL Server. Dans ce cas, vous devez définir la « min server memory » et « max server memory » sur la même valeur (égal à la quantité maximale de mémoire physique qui utilise SQL Server). Cela va réduire les frais généraux qui serait sinon utilisé par SQL Server de gestion dynamique de ces valeurs. Exécutez les commandes T-SQL suivantes sur chaque ordinateur exécutant SQL Server pour spécifier la quantité fixe de mémoire à allouer à SQL Server :<br /><br /> sp_configure ' Max Server memory (Mo) », (taille maximale en Mo) sp_configure 'Min Server de mémoire (Mo)', (min taille en Mo)<br /><br /> Avant de définir la quantité de mémoire pour SQL Server, déterminez le paramètre approprié de mémoire en soustrayant la mémoire requise pour Windows Server à partir de la mémoire physique totale. Il s’agit de la quantité maximale de mémoire que pouvant être allouée à SQL Server. **Remarque :** si des ordinateurs qui exécutent SQL Server hébergeant des bases de données BizTalk Server également hébergent le secret principal Enterprise Single Sign-On, comme décrit dans la rubrique [Clustering du serveur de secret principal](clustering-the-master-secret-server.md) vous devrez peut-être Pour ajuster cette valeur pour vous assurer qu’il existe suffisamment de mémoire disponible pour exécuter l’entreprise Sign-On Service unique.|  
|Compte la taille de base de données des suivis BizTalk|-Lors de la détermination de la taille des messages dans la base de données de suivi BizTalk (DTA), ajouter la taille moyenne du contexte de message à la taille de message si elle est importante par rapport à la taille du message.<br />-Pour limiter la taille des messages dans la base de données des suivis BizTalk, limitez le nombre de propriétés que vous promouvez.<br />-Si l’option du débogueur d’orchestration est activée, prendre en compte l’état de chaque forme de l’orchestration est enregistré dans la base de données des suivis BizTalk.|  
  
<a name="BKMK_Maintain"></a>   
## <a name="performing-sql-server-maintenance-procedures"></a>Procédures de Maintenance SQL Server  
  
|Étapes|Référence|  
|-----------|---------------|  
|Définissez les paramètres de croissance automatique pour les bases de données BizTalk Server.|-Base de données de la croissance automatique doit être définie pour un nombre fixe de mégaoctets et non un pourcentage, en particulier pour la MessageBox et le suivi des bases de données. Selon votre application BizTalk Server et le débit, la MessageBox et le suivi des bases de données peuvent devenir très volumineux. Si la croissance automatique est définie sur un pourcentage, la croissance automatique peut également être substantielle.<br />-Initialisation instantanée des fichiers peut réduire l’impact sur les performances d’une opération de croissance de fichier.<br />-Dans l’idéal, la taille des fichiers de prise en charge les groupes de fichiers doit être pré-allouée et si possible, affectez à une taille fixe.<br /><br /> Pour plus d’informations, consultez [définition des paramètres de croissance automatique pour les bases de données](defining-auto-growth-settings-for-databases.md).|  
|Sauvegarder les bases de données BizTalk Server|-Nous vous recommandons de l’exécution du travail de sauvegarde de BizTalk Server pour empêcher les journaux des transactions de base de données BizTalk Server de croître de manière illimitée.<br />-Vous devez restaurer tout l’environnement BizTalk Server régulièrement, et vous devez documenter avec soin le processus.<br />-Il est recommandé d’archiver les anciens fichiers de sauvegarde.<br /><br /> Pour plus d’informations, consultez [sauvegarde des bases de données](backing-up-databases.md).|  
|Surveiller les travaux de l’Agent SQL de BizTalk Server.|Surveiller l’intégrité de ces travaux et vous assurer qu’elles s’exécutent sans erreur. Pour plus d’informations, consultez [analyse les travaux de l’Agent SQL Server](monitoring-sql-server-agent-jobs.md).|  
|Permettre à BizTalk Server, le suivi et l’archivage|Le travail de l’Agent SQL de « DTA Purge et archivage » archive et purge les anciennes données à partir de la base de données des suivis BizTalk, évitant ainsi que celui-ci croissants. Ceci est essentiel pour un système BizTalk Server intègre. Pour plus d’informations, consultez [purge et archivage des données de suivi](purging-and-archiving-tracking-data.md).|  
  
<a name="BKMK_Backup"></a>   
## <a name="backing-up-the-biztalk-server-databases"></a>Sauvegarde des bases de données BizTalk Server  
  
|Étapes|Référence|  
|-----------|---------------|  
|Vérifiez que le travail de l’Agent SQL de sauvegarde BizTalk Server est configuré.|Consultez [configurer le travail de sauvegarde de BizTalk Server](../core/how-to-configure-the-backup-biztalk-server-job.md)|  
|Configurer le travail de l’Agent sauvegarde SQL Server de BizTalk pour supprimer les fichiers de sauvegarde qui sont antérieures au nombre de jours spécifié par la @DaysToKeep variable. Si les fichiers de sauvegarde ne sont pas supprimés. ils peuvent devenir non liées au fil du temps, ce qui peut arriver à saturation l’ou les disques qui contiennent les fichiers de sauvegarde et de provoquer des problèmes liés à un espace disque limité.|Consultez [configurer le travail de sauvegarde de BizTalk Server](../core/how-to-configure-the-backup-biztalk-server-job.md)|  
|Vérifiez que le travail de l’Agent SQL de sauvegarde BizTalk Server est activé et en cours d’exécution.|[Surveillance des tâches de SQL Server Agent](monitoring-sql-server-agent-jobs.md)|  
  
<a name="BKMK_Disaster"></a>   
## <a name="using-sql-server-log-shipping-for-disaster-recovery"></a>À l’aide de SQL Server envoi de journaux pour la récupération d’urgence  
  
|Étapes|Référence|  
|-----------|---------------|  
|Vérifiez que les serveurs de récupération d’urgence ont la capacité de gérer la charge de production.|Consultez [à l’aide des journaux de BizTalk Server pour la récupération d’urgence](using-biztalk-server-log-shipping-for-disaster-recovery.md)|  
|Assurez-vous que les spécificités de votre routine de récupération d’urgence sont bien documentées.|Consultez [à l’aide des journaux de BizTalk Server pour la récupération d’urgence](using-biztalk-server-log-shipping-for-disaster-recovery.md)|  
|Dans le cadre de régulière test, essai de basculement pour le site de récupération d’urgence, en particulier en tant que nouvelle BizTalk applications sont placées en production.|Consultez [à l’aide des journaux de BizTalk Server pour la récupération d’urgence](using-biztalk-server-log-shipping-for-disaster-recovery.md)|  
  
<a name="BKMK_Jobs"></a>   
## <a name="monitoring-biztalk-server-sql-agent-jobs"></a>Analyse des travaux de l’Agent SQL Server de BizTalk  
  
|Étapes|Référence|  
|-----------|---------------|  
|Vérifiez que le service SQL Server Agent est en cours d’exécution.|Consultez [analyse des travaux de l’Agent SQL Server](monitoring-sql-server-agent-jobs.md)|  
|Vérifiez que les travaux de l’Agent SQL Server installés par BizTalk Server sont activées et en cours d’exécution avec succès.|Consultez [analyse des travaux de l’Agent SQL Server](monitoring-sql-server-agent-jobs.md)|  
|Vérifiez que les travaux de l’Agent SQL de BizTalk Server sont achèvent en temps voulu.|Consultez [analyse des travaux de l’Agent SQL Server](monitoring-sql-server-agent-jobs.md)|  
  
<a name="BKMK_Purge"></a>   
## <a name="purging-and-archiving-tracking-data"></a>Purge et archivage des données de suivi  
  
|Étapes|Référence|  
|-----------|---------------|  
|Assurez-vous que le travail de l’Agent SQL « DTA Purge et archivage » est correctement configuré, activé et exécution.|Consultez [configurer la Purge DTA et archiver le travail](../core/how-to-configure-the-dta-purge-and-archive-job.md).|  
|Assurez-vous que le travail est en mesure de purger les données de suivi aussi vite que les données de suivi entrantes sont générées.|Consultez [mesurer le débit de suivi maximal acceptable](../core/measuring-maximum-sustainable-tracking-throughput.md)|  
|Passez en revue la purge normale et les paramètres de purge dur afin de que vous conservez les données pendant la durée optimale.|Consultez [l’archivage et la purge de la base de données de suivi de BizTalk](../core/archiving-and-purging-the-biztalk-tracking-database.md).|  
|Si vous devez uniquement purger les anciennes données et ne pas pour archiver les modifications tout d’abord, l’Agent SQL la fonction pour appeler la procédure stockée « dtasp_PurgeTrackingDatabase. »|Consultez [purger les données de base de données de suivi BizTalk](../core/how-to-purge-data-from-the-biztalk-tracking-database.md).|  
  
## <a name="next"></a>Suivant
  
-   [Paramètres de SQL Server qui ne doivent pas être modifiés](sql-server-settings-that-should-not-be-changed.md)  
  
-   [Surveillance et réduire la Contention d’e/s de base de données](monitoring-and-reducing-database-i-o-contention.md)  
  
-   [Examen et test de la configuration du cluster SQL Server pour les scénarios de basculement](reviewing-and-testing-sql-server-cluster-configuration-for-failover-scenarios.md)  
  
-   [Définition des paramètres de croissance automatique pour les bases de données](defining-auto-growth-settings-for-databases.md)  
  
-   [Sauvegarde des bases de données](backing-up-databases.md)  
  
-   [Utilisation de la copie des journaux de transaction de BizTalk Server pour la récupération d’urgence](using-biztalk-server-log-shipping-for-disaster-recovery.md)  
  
-   [Surveillance des tâches de SQL Server Agent](monitoring-sql-server-agent-jobs.md)  
  
-   [Vidage et archivage des données de suivi](purging-and-archiving-tracking-data.md)