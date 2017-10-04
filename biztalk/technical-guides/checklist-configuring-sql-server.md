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
ms.openlocfilehash: ce0eff1dab6afe81c55f4cffa08c4839762e82ea
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="checklist-configuring-sql-server"></a>Liste de vérification : Configuration de SQL Server
Cette rubrique répertorie les étapes à suivre lorsque vous préparez [!INCLUDE[btsSQLServer2008](../includes/btssqlserver2008-md.md)] ou [!INCLUDE[btsSQLServer2005](../includes/btssqlserver2005-md.md)] pour une utilisation dans un [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environnement de production.  
  
-   [Liste de vérification : Configuration de SQL Server](../technical-guides/checklist-configuring-sql-server.md)  
  
-   [Procédures de Maintenance SQL Server](../technical-guides/checklist-configuring-sql-server.md#BKMK_Maintain)  
  
-   [Sauvegarde des bases de données BizTalk Server](../technical-guides/checklist-configuring-sql-server.md#BKMK_Backup)  
  
-   [À l’aide de SQL Server envoi de journaux pour la récupération d’urgence](../technical-guides/checklist-configuring-sql-server.md#BKMK_Disaster)  
  
-   [Analyse des travaux de l’Agent SQL Server de BizTalk](../technical-guides/checklist-configuring-sql-server.md#BKMK_Jobs)  
  
-   [Purge et archivage des données de suivi](../technical-guides/checklist-configuring-sql-server.md#BKMK_Purge)  
  
<a name="BKMK_Config"></a>   
## <a name="configuring-sql-server"></a>Configuration de SQL Server  
  
|Étapes|Référence|  
|-----------|---------------|  
|Contrôler et réduire [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] contention d’e/s disque pour les fichiers de base de données.|-Nous vous recommandons de proactive surveiller l’utilisation des e/s disque pour les disques qui hébergent les fichiers journaux de transaction et de données.<br />-Il est recommandé que les fichiers de données et les fichiers journaux des transactions pour chacun d’eux être placé sur des lecteurs dédiés pour réduire la probabilité de contention d’e/s disque devient un problème.<br />-Vous pouvez réduire la contention d’e/s de disque en séparant les bases de données MessageBox et de suivi (DTA) et en séparant les fichiers de base de données et les fichiers journaux des transactions sur des disques physiques.<br /><br /> Pour plus d’informations, consultez [analyse et réduire les conflits de base de données e/s](~/technical-guides/monitoring-and-reducing-database-i-o-contention.md)|  
|Vérifiez [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] est configuré sur des partitions correctement aligné|Partitions de disque correctement alignée peut entraîner une diminution considérable de latence, d'où une amélioration le [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] des performances, ce qui à son tour améliore [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] performances. En revanche, les partitions de disque non aligné peuvent nuire aux performances d’e/s, ce qui dégrade le [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] et [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] performances.<br /><br /> Pour plus d’informations sur les partitions de disque comment correctement alignée clairement peut affecter les performances, consultez [« Disque Partition alignement meilleures pratiques pour SQL Server »](http://go.microsoft.com/fwlink/?LinkId=154073) (http://go.microsoft.com/fwlink/?LinkId=154073).|  
|Conserver les événements que vous surveillez avec le Générateur de profils SQL Server|Utiliser SQL Server Profiler pour surveiller uniquement les événements qui vous intéressent. Si les traces deviennent trop volumineux, vous pouvez filtrer en fonction des informations que vous le souhaitez, afin que seul un sous-ensemble des données d’événement est collecté. La surveillance d'un trop grand nombre d'événements s'ajoute à la charge du serveur et du processus de surveillance, et peut considérablement accroître la taille du fichier ou de la table de trace, en particulier si le processus de surveillance se prolonge sur une période importante.|  
|Contrôler et réduire les contentions d’e/s de DTC journal fichier disque.|[Analyse et réduire la Contention d’e/s de DTC journal fichier sur le disque](~/technical-guides/monitoring-and-reducing-dtc-log-file-disk-i-o-contention.md)|  
|Fournir une haute disponibilité pour le [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] bases de données.|[Planification de la disponibilité de base de données](~/technical-guides/planning-for-database-availability.md)|  
|Passez en revue la configuration de cluster actif/actif SQL Server pour les scénarios de basculement.|[Examen et le test de Configuration du Cluster SQL Server pour les scénarios de basculement](~/technical-guides/reviewing-and-testing-sql-server-cluster-configuration-for-failover-scenarios.md)|  
|Utilisez les paramètres de configuration par défaut pour :<br /><br /> -Degré maximal de parallélisme (MDOP).<br />-   [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]statistiques sur les [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] base de données MessageBox.<br />-   [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]les reconstructions d’index de base de données et de la défragmentation.|[Paramètres de SQL Server qui ne doivent pas être modifiés.](~/technical-guides/sql-server-settings-that-should-not-be-changed.md)|  
|Activer l’indicateur de trace 1118 (TF1118) en tant que paramètre de démarrage pour toutes les instances de [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)].|L’implémentation TF1118 permet de réduire les conflits entre les [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] instances en supprimant presque toutes les allocations de page unique. Pour plus d’informations, consultez Base de connaissances Microsoft l’article 328551, [« Améliorations de la concurrence pour la base de données tempdb »](http://go.microsoft.com/fwlink/?LinkId=153694) (http://go.microsoft.com/fwlink/?LinkId=153694). **Remarque :** pour plus d’informations sur, consultez TF1118 [« À tort autour TF1118 »](http://go.microsoft.com/fwlink/?LinkId=158271) (http://go.microsoft.com/fwlink/?LinkId=158271). Notez que le contenu au niveau de ce lien n’est pas détenu par Microsoft et Microsoft ne garantit pas l’exactitude du contenu.|  
|Fractionner la base de données tempdb en plusieurs fichiers de données de taille égale sur chaque [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] instance utilisée par [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].|Assurez-vous que les fichiers de données utilisés pour la base de données tempdb sont de taille égale. Ceci est très important, car l’algorithme de remplissage proportionnel utilisé par [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] est basée sur la taille des fichiers de données. Si les fichiers de données sont créés avec la taille inégale, l’algorithme de remplissage proportionnel utilisera le fichier le plus volumineux plus pour les allocations d’Allocation GAM (Global Map) plutôt qu’en se propageant les allocations entre tous les fichiers, invalidant ainsi le but de créer plusieurs fichiers de données. En règle générale, créez un fichier de données pour chaque UC sur le serveur, puis réglez le nombre de fichiers vers le haut ou vers le bas si nécessaire. Notez qu'une UC à double noyau est traitée comme deux UC distinctes. Dans tous les cas, le nombre de fichiers de données ne doit pas être supérieur à 8, quel que soit le nombre de cœurs supplémentaires sont disponibles sur l’ordinateur. Pour plus d’informations sur les fichiers de tempdb, consultez [optimisation des performances de tempdb](http://go.microsoft.com/fwlink/?LinkId=158272) (http://go.microsoft.com/fwlink/?LinkId=158272) dans le [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] documentation.|  
|Si vous exécutez [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et l’hébergement de vos bases de données sur les ordinateurs exécutant [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] avec suffisamment de mémoire physique, configurer les instances de [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] d’utiliser les Extensions AWE (Address Windowing) de mémoire.|Sur x86 ordinateur, [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] doit être configuré pour utiliser plus de 2 Go de mémoire physique. [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]prend en charge l’utilisation de Microsoft Windows Address Windowing Extensions (AWE) pour adresser jusqu'à 32 Go de mémoire. Avec AWE, [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] peut réserver de la mémoire qui n’est pas en cours d’utilisation pour les autres applications et le système d’exploitation. Cependant, chaque instance qui utilise cette mémoire doit allouer statiquement la mémoire dont il a besoin. [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]peut uniquement utiliser cette mémoire allouée pour le cache de données et non pour les exécutables, les pilotes, les DLL, etc. AWE. Pour plus d'informations, consultez :<br /><br /> -L’article de la Base de connaissances Microsoft 274750, [« Comment configurer SQL Server pour utiliser plus de 2 Go de mémoire physique »](http://go.microsoft.com/fwlink/?LinkId=153718) (http://go.microsoft.com/fwlink/?LinkId=153718).<br />-   [L’utilisation d’AWE](http://go.microsoft.com/fwlink/?LinkId=153720) (http://go.microsoft.com/fwlink/?LinkId=153720) dans le [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] documentation.<br />-   [L’activation de la mémoire AWE pour SQL Server](http://go.microsoft.com/fwlink/?LinkId=158273) (http://go.microsoft.com/fwlink/?LinkId=158273) dans le [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] documentation.|  
|Définir la mémoire minimale et maximale du serveur pour les mêmes valeurs sur le [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] instance(s) qui hébergent le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] bases de données.|Les ordinateurs qui exécutent [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] qui hébergent le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] bases de données doivent être dédiés à l’exécution [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]. Lorsque les ordinateurs qui exécutent [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] qui hébergent le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] bases de données **sont** dédié à en cours d’exécution [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)], nous recommandons que le « min server memory » et les options « max server memory » sur chaque [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] instance soit configuré pour spécifier la quantité fixe de mémoire à allouer à [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]. Dans ce cas, vous devez définir la « min server memory » et « max server memory » sur la même valeur (égal à la quantité maximale de mémoire physique qui utilise SQL Server). Cela va réduire les frais généraux qui serait utilisée sinon par [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] dynamiquement la gestion de ces valeurs. Exécutez les commandes T-SQL suivantes sur chaque ordinateur exécutant [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] pour spécifier la quantité fixe de mémoire à allouer à [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]:<br /><br /> sp_configure ' Max Server memory (Mo) », (taille maximale en Mo) sp_configure 'Min Server de mémoire (Mo)', (min taille en Mo)<br /><br /> Avant de définir la quantité de mémoire pour [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)], déterminer le paramètre approprié de mémoire en soustrayant la mémoire requise pour Windows Server à partir de la mémoire physique totale. C’est la quantité maximale de mémoire que vous pouvez affecter à [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]. **Remarque :** si des ordinateurs qui exécutent [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] qui hébergent le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] bases de données également hébergent le secret principal Enterprise Single Sign-On comme décrit dans la rubrique [Clustering du serveur de secret principal](~/technical-guides/clustering-the-master-secret-server.md) puis Vous devrez peut-être modifier cette valeur pour vous assurer qu’il existe suffisamment de mémoire disponible pour exécuter l’entreprise Sign-On Service unique.|  
|Compte la taille de base de données des suivis BizTalk|-Lors de la détermination de la taille des messages dans la base de données de suivi BizTalk (DTA), ajouter la taille moyenne du contexte de message à la taille de message si elle est importante par rapport à la taille du message.<br />-Pour limiter la taille des messages dans la base de données des suivis BizTalk, limitez le nombre de propriétés que vous promouvez.<br />-Si l’option du débogueur d’orchestration est activée, prendre en compte l’état de chaque forme de l’orchestration est enregistré dans la base de données des suivis BizTalk.|  
  
<a name="BKMK_Maintain"></a>   
## <a name="performing-sql-server-maintenance-procedures"></a>Procédures de Maintenance SQL Server  
  
|Étapes|Référence|  
|-----------|---------------|  
|Définir les paramètres de croissance automatique de la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] bases de données.|-Base de données de la croissance automatique doit être définie pour un nombre fixe de mégaoctets et non un pourcentage, en particulier pour la MessageBox et le suivi des bases de données. Selon votre application BizTalk Server et le débit, la MessageBox et le suivi des bases de données peuvent devenir très volumineux. Si la croissance automatique est définie sur un pourcentage, la croissance automatique peut également être substantielle.<br />-Initialisation instantanée des fichiers peut réduire l’impact sur les performances d’une opération de croissance de fichier.<br />-Dans l’idéal, la taille des fichiers de prise en charge les groupes de fichiers doit être pré-allouée et si possible, affectez à une taille fixe.<br /><br /> Pour plus d’informations, consultez [définition des paramètres de croissance automatique pour les bases de données](~/technical-guides/defining-auto-growth-settings-for-databases.md).|  
|Sauvegardez le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] bases de données|-Nous vous recommandons d’exécuter le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sauvegarde afin d’éviter le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] de base de données de journaux des transactions de croître de manière illimitée.<br />-Vous devez restaurer l’intégralité de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environnement sur une base régulière et que vous devez documenter avec soin le processus.<br />-Il est recommandé d’archiver les anciens fichiers de sauvegarde.<br /><br /> Pour plus d’informations, consultez [sauvegarde des bases de données](~/technical-guides/backing-up-databases.md).|  
|Analyse le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] travaux SQL Agent.|Surveiller l’intégrité de ces travaux et vous assurer qu’elles s’exécutent sans erreur. Pour plus d’informations, consultez [analyse les travaux de l’Agent SQL Server](~/technical-guides/monitoring-sql-server-agent-jobs.md).|  
|Activer [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] le suivi et l’archivage|Le travail de l’Agent SQL de « DTA Purge et archivage » archive et purge les anciennes données à partir de la base de données des suivis BizTalk, évitant ainsi que celui-ci croissants. Ceci est essentiel pour une intégrité [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] système. Pour plus d’informations, consultez [purge et archivage des données de suivi](~/technical-guides/purging-and-archiving-tracking-data.md).|  
  
<a name="BKMK_Backup"></a>   
## <a name="backing-up-the-biztalk-server-databases"></a>Sauvegarde des bases de données BizTalk Server  
  
|Étapes|Référence|  
|-----------|---------------|  
|Vérifiez que la sauvegarde [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] travail de l’Agent SQL est configuré.|-Découvrez [« Comment configurer le travail de sauvegarde de BizTalk Server »](http://go.microsoft.com/fwlink/?LinkId=153813) (http://go.microsoft.com/fwlink/?LinkId=153813).<br />-Découvrez [sauvegarde des bases de données](~/technical-guides/backing-up-databases.md).|  
|Configurer la sauvegarde [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] travail Agent SQL pour supprimer les fichiers de sauvegarde qui sont antérieures au nombre de jours spécifié par la @DaysToKeep variable. Si les fichiers de sauvegarde ne sont pas supprimés. ils peuvent devenir non liées au fil du temps, ce qui peut arriver à saturation l’ou les disques qui contiennent les fichiers de sauvegarde et de provoquer des problèmes liés à un espace disque limité.|Consultez 982546 de l’Article de Base de connaissances Microsoft, [le travail « Sauvegarde de BizTalk Server » échoue lorsque les fichiers de sauvegarde s’accumuler au fil du temps dans Microsoft BizTalk Server de base](http://go.microsoft.com/fwlink/?LinkId=202858) (http://go.microsoft.com/fwlink/?LinkId=202858).|  
|Vérifiez que la sauvegarde [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] travail d’Agent SQL est activé et en cours d’exécution.|[Analyse des travaux de l’Agent SQL Server](~/technical-guides/monitoring-sql-server-agent-jobs.md)|  
  
<a name="BKMK_Disaster"></a>   
## <a name="using-sql-server-log-shipping-for-disaster-recovery"></a>À l’aide de SQL Server envoi de journaux pour la récupération d’urgence  
  
|Étapes|Référence|  
|-----------|---------------|  
|Vérifiez que les serveurs de récupération d’urgence ont la capacité de gérer la charge de production.|Consultez [à l’aide des journaux de BizTalk Server pour la récupération d’urgence](~/technical-guides/using-biztalk-server-log-shipping-for-disaster-recovery.md)|  
|Assurez-vous que les spécificités de votre routine de récupération d’urgence sont bien documentées.|Consultez [à l’aide des journaux de BizTalk Server pour la récupération d’urgence](~/technical-guides/using-biztalk-server-log-shipping-for-disaster-recovery.md)|  
|Dans le cadre de régulière test, essai de basculement pour le site de récupération d’urgence, en particulier en tant que nouvelle BizTalk applications sont placées en production.|Consultez [à l’aide des journaux de BizTalk Server pour la récupération d’urgence](~/technical-guides/using-biztalk-server-log-shipping-for-disaster-recovery.md)|  
  
<a name="BKMK_Jobs"></a>   
## <a name="monitoring-biztalk-server-sql-agent-jobs"></a>Analyse des travaux de l’Agent SQL Server de BizTalk  
  
|Étapes|Référence|  
|-----------|---------------|  
|Vérifiez que le service SQL Server Agent est en cours d’exécution.|Consultez [analyse des travaux de l’Agent SQL Server](~/technical-guides/monitoring-sql-server-agent-jobs.md)|  
|Vérifiez que les travaux de l’Agent SQL Server est installé en [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sont activés et en cours d’exécution avec succès.|Consultez [analyse des travaux de l’Agent SQL Server](~/technical-guides/monitoring-sql-server-agent-jobs.md)|  
|Vérifiez que la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] les travaux de l’Agent SQL s’achèvent en temps voulu.|Consultez [analyse des travaux de l’Agent SQL Server](~/technical-guides/monitoring-sql-server-agent-jobs.md)|  
  
<a name="BKMK_Purge"></a>   
## <a name="purging-and-archiving-tracking-data"></a>Purge et archivage des données de suivi  
  
|Étapes|Référence|  
|-----------|---------------|  
|Assurez-vous que le travail de l’Agent SQL « DTA Purge et archivage » est correctement configuré, activé et exécution.|Consultez [« Comment configurer la Purge DTA et archiver le travail »](http://go.microsoft.com/fwlink/?LinkId=153814) (http://go.microsoft.com/fwlink/?LinkId=153814).|  
|Assurez-vous que le travail est en mesure de purger les données de suivi aussi vite que les données de suivi entrantes sont générées.|Consultez [« Mesurer le débit de suivi maximal acceptable »](http://go.microsoft.com/fwlink/?LinkId=153815) (http://go.microsoft.com/fwlink/?LinkId=153815).|  
|Passez en revue la purge normale et les paramètres de purge dur afin de que vous conservez les données pendant la durée optimale.|Consultez [« Archivage et la purge de la base de données de suivi de BizTalk »](http://go.microsoft.com/fwlink/?LinkId=153816) (http://go.microsoft.com/fwlink/?LinkId=153816).|  
|Si vous devez uniquement purger les anciennes données et ne pas pour archiver les modifications tout d’abord, l’Agent SQL la fonction pour appeler la procédure stockée « dtasp_PurgeTrackingDatabase. »|Consultez [« Comment purger les données de base de données de suivi BizTalk »](http://go.microsoft.com/fwlink/?LinkId=153817) (http://go.microsoft.com/fwlink/?LinkId=153817).|  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Paramètres de SQL Server qui ne doivent pas être modifiés.](~/technical-guides/sql-server-settings-that-should-not-be-changed.md)  
  
-   [Surveillance et réduire la Contention d’e/s de base de données](~/technical-guides/monitoring-and-reducing-database-i-o-contention.md)  
  
-   [Examen et le test de Configuration du Cluster SQL Server pour les scénarios de basculement](~/technical-guides/reviewing-and-testing-sql-server-cluster-configuration-for-failover-scenarios.md)  
  
-   [Définition des paramètres de croissance automatique pour les bases de données](~/technical-guides/defining-auto-growth-settings-for-databases.md)  
  
-   [Sauvegarde des bases de données](~/technical-guides/backing-up-databases.md)  
  
-   [À l’aide des journaux de BizTalk Server pour la récupération d’urgence](~/technical-guides/using-biztalk-server-log-shipping-for-disaster-recovery.md)  
  
-   [Analyse des travaux de l’Agent SQL Server](~/technical-guides/monitoring-sql-server-agent-jobs.md)  
  
-   [Purge et archivage des données de suivi](~/technical-guides/purging-and-archiving-tracking-data.md)