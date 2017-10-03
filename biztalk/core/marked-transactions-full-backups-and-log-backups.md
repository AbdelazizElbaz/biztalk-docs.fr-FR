---
title: "Transactions marquées, sauvegardes complètes et sauvegardes de journaux | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- backing up, transaction logs
- backing up, full backups
- transaction logs
- backing up, backup jobs
ms.assetid: a383a16d-1e40-4b0b-a515-f1cb90bfb4d2
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 36c7eab426bfc19c082d8c9651cf4d02eae0075a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="marked-transactions-full-backups-and-log-backups"></a>Transactions marquées, sauvegardes complètes et sauvegardes de journal
Le travail de sauvegarde de BizTalk Server crée des sauvegardes synchronisées de toutes les bases de données BizTalk Server à l’aide de sauvegardes complètes et sauvegardes de journaux de transactions, conjointement avec un type de transaction appelé un *transaction marquée*. Les transactions marquées sont des transactions qui insèrent une marque dans le journal des transactions de toutes les bases de données participant à la transaction. La transaction marquée empêche le démarrage des nouvelles transactions distribuées, attend la fin de l'exécution des transactions distribuées, puis s'exécute pour placer la marque.  
  
 La marque représente un point de transaction cohérent dans toutes les bases de données. Vous pouvez l'utiliser avec les sauvegardes de journal suivantes pour restaurer vos bases de données à ce point.  
  
 Pour chaque base de données BizTalk Server, le travail de sauvegarde de BizTalk Server crée une sauvegarde de journal des transactions marquée à chaque exécution, puis crée une sauvegarde complète basée sur une période que vous spécifiez.  
  
## <a name="full-backups"></a>Sauvegardes complètes  
 Lorsque vous exécutez la tâche de sauvegarde de BizTalk Server qu’il exécute le processus de sauvegarde en premier, *BackupFull*, une fois par période (pas chaque fois que le travail s’exécute). Pour plus d’informations sur la façon de planifier le travail de sauvegarde de BizTalk Server, consultez [comment planifier le travail de sauvegarde de BizTalk Server](../core/how-to-schedule-the-backup-biztalk-server-job.md).  
  
 La première fois que le travail de sauvegarde de BizTalk Server s’exécute pendant une période de nouveau, il effectue une sauvegarde complète. Par exemple, si vous planifiez une exécution du travail toutes les heures, mais configurez une période quotidienne, le travail de sauvegarde de BizTalk Server effectue une sauvegarde complète lors de sa première exécution, puis chaque jour à minuit.  
  
## <a name="transaction-log-backups"></a>Journal des transactions  
 Le deuxième processus qui effectue de la tâche de sauvegarde de BizTalk Server est *MarkAndBackupLog*. Ce processus insère une marque dans toutes les bases de données BizTalk Server et effectue une sauvegarde de journal des transactions à chaque exécution du travail.  
  
 La marque est la chaîne créée à l’aide de  *\<nom_serveur >*_*\<DatabaseName >*journa_l\_*\<LogMarkName >* \_  *\<Timestamp >*.bak, où le  *\<nom de marque de journal >* est configuré dans le travail de l’Agent SQL Server. Cette marque doit être utilisée lors de la restauration du dernier journal dans chaque base de données.  
  
 Pour plus d'informations, consultez les rubriques « Sauvegardes du journal des transactions » et « Sauvegarde et récupération de bases de données associées » dans la documentation en ligne de SQL Server.  
  
## <a name="see-also"></a>Voir aussi  
 [Informations avancées sur la sauvegarde et restauration](../core/advanced-information-about-backup-and-restore1.md)