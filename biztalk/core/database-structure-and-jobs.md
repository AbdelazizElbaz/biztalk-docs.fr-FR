---
title: "Structure et les travaux de base de données | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- PurgeSubscriptionsJob_BizTalkMsgBoxDb job
- MessageBox database, jobs [SQL Server Agent]
- DTA Purge and Archive (BizTalkDTADb) job
- TrackedMessages_Copy_BizTalkMsgBoxDb job
- MessageBox_Message_Cleanup_BizTalkMsgBoxDb job
- MessageBox_Message_ManageRefCountLog_BizTalkMsgBoxDb job
- Operations_OperateOnInstances_OnMaster_BizTalkMsgBoxDb job
- jobs [SQL Server Agent], MessageBox database
- CleanupBTFExpiredEntriesJob_BizTalkMgmtDb job
- databases, structure
- Tracking database, jobs [SQL Server Agent]
- jobs [SQL Server Agent], Management database
- Backup BizTalk Server (BizTalkMgmtDb) job
- databases, SQL Server Agent jobs
- Business Rules Engine, jobs [SQL Server Agent]
- jobs, databases
- Management database, jobs [SQL Server Agent]
- MessageBox_UpdateStats_BizTalkMsgBoxDb job
- jobs [SQL Server Agent], Business Rules Engine
- Rules_Database_Cleanup_BizTalkRuleEngineDb job
- MessageBox_Parts_Cleanup_BizTalkMsgBoxDb job
- jobs [SQL Server Agent], Tracking database
- MessageBox_DeadProcesses_Cleanup_BizTalkMsgBoxDb job
ms.assetid: f5f6b17d-0f5e-4821-a7eb-c345234ffc65
caps.latest.revision: "23"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bf98ef7fe236261fd3ee65ac6f4695455ba8c704
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="database-structure-and-jobs"></a>Structure et travaux de base de données
Cette rubrique présente la structure et les travaux de base de données de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
## <a name="database-write-diagram"></a>Schéma d'écriture dans une base de données  
 L'illustration ci-dessous montre les processus et entités qui écrivent dans les bases de données BizTalk Server.  
  
 ![Processus d’écriture dans les bases de données BizTalk Server](../core/media/ebiz-ops-backup.gif "ebiz_ops_backup")  
  
        Database write diagram showing the processes and entities that write to the BizTalk Server databases  
  
## <a name="biztalk-server-database-jobs"></a>Travaux de base de données BizTalk Server  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] inclut les travaux d'Agent SQL Server suivants pour faciliter la gestion des bases de données BizTalk Server :  
  
> [!NOTE]
>  Les noms des travaux changent en fonction des noms de base de données donnés pendant la configuration. Si vous avez déployé plusieurs bases de données MessageBox dans votre environnement, il existera plusieurs travaux pour chaque MessageBox.  
  
> [!WARNING]
>  Dans la base de données de gestion BizTalk (BizTalkMgmtDb), il existe une procédure stockée nommée **adm_CleanupMgmtDB**. **N’EXÉCUTEZ PAS CETTE PROCÉDURE STOCKÉE !** Si vous l'exécutez, toutes les entrées de la base de données seront supprimées.  
  
|Travail| Description|  
|---------|-----------------|  
|Backup BizTalk Server (BizTalkMgmtDb)|Ce travail effectue des sauvegardes complètes des bases et fichiers journaux des bases de données BizTalk Server. Pour plus d’informations sur la configuration et l’exécution de cette tâche, consultez [sauvegarde et restauration de bases de données BizTalk Server](../core/backing-up-and-restoring-biztalk-server-databases.md).|  
|CleanupBTFExpiredEntriesJob_BizTalkMgmtDb|Ce travail nettoie les anciennes entrées BizTalk Framework (BTF) de la base de données de gestion BizTalk (BizTalkMgmtDb).|  
|DTA Purge and Archive (BizTalkDTADb)|Ce travail archive automatiquement les données dans la base de données des suivis BizTalk (BizTalkDTADb) et purge les données obsolètes. Pour plus d’informations sur la configuration et l’exécution de cette tâche, consultez [l’archivage et la purge de la base de données de suivi BizTalk](../core/archiving-and-purging-the-biztalk-tracking-database.md).|  
|MessageBox_DeadProcesses_Cleanup_BizTalkMsgBoxDb|Ce travail détecte le moment où une instance d'hôte BizTalk Server (service NT) s'arrête et libère le travail qu'elle a effectué pour qu'une autre instance d'hôte puisse à son tour travailler dessus.|  
|MessageBox_Message_Cleanup_BizTalkMsgBoxDb|Ce travail supprime tous les messages qui ne sont plus référencés par aucun abonné dans les tables de base de données MessageBox BizTalk (BizTalkMsgBoxDb). **Attention :** il s’agit d’un travail non planifié, qui est lancé par le travail MessageBox_Message_ManageRefCountLog_BizTalkMsgBoxDb. Ne lancez pas ce travail manuellement.|  
|MessageBox_Message_ManageRefCountLog_BizTalkMsgBoxDb|Ce travail gère les journaux des compteurs de références des messages et détermine le moment à partir duquel un message n'est plus référencé par aucun abonné. **Remarque :** bien que ce travail de l’Agent SQL Server est planifié pour exécuter une fois par minute, la procédure stockée qui est appelée par ce travail contient la logique pour vous assurer que la procédure stockée s’exécute en permanence. Il s'agit d'un comportement par défaut qui ne doit pas être modifié.|  
|MessageBox_Parts_Cleanup_BizTalkMsgBoxDb|Ce travail supprime toutes les parties des messages qui ne sont plus référencées par aucun message dans les tables de base de données MessageBox BizTalk (BizTalkMsgBoxDb). Tous les messages se composent d'une ou plusieurs parties qui contiennent véritablement les données des messages.|  
|MessageBox_UpdateStats_BizTalkMsgBoxDb|Ce travail met manuellement à jour les statistiques de la base de données MessageBox BizTalk (BizTalkMsgBoxDb).|  
|Analyser BizTalk Server|Ce travail analyse les bases de données BizTalkMgmtDb, BizTalkMsgBoxDb et BizTalkDTADb pour détecter les problèmes connus, y compris les instances orphelines.|  
|Operations_OperateOnInstances_OnMaster_BizTalkMsgBoxDb|Ce travail est nécessaire pour les déploiements de la base de données MessageBox multiples. Il effectue de façon asynchrone des actions opérationnelles, telles qu'un arrêt en bloc sur la MessageBox principale une fois ces modifications appliquées à la MessageBox subordonnée.|  
|PurgeSubscriptionsJob_BizTalkMsgBoxDb|Ce travail purge les prédicats d'abonnement inutilisés dans la base de données MessageBox BizTalk Server (BizTalkMsgBoxDb).|  
|Rules_Database_Cleanup_BizTalkRuleEngineDb|Ce travail purge automatiquement les anciennes données d'audit de la base de données du moteur de règles (BizTalkRuleEngineDb) tous les 90 jours. Ce travail purge également les anciennes données d'historique (notifications de déploiement/d'annulation de déploiement) de la base de données du moteur de règles (BizTalkRuleEngineDb) tous les 3 jours.|  
  
## <a name="see-also"></a>Voir aussi  
 [Le moteur de messagerie](../core/the-messaging-engine.md)