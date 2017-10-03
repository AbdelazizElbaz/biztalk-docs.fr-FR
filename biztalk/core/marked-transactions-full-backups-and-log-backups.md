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
# <a name="marked-transactions-full-backups-and-log-backups"></a><span data-ttu-id="fc414-102">Transactions marquées, sauvegardes complètes et sauvegardes de journal</span><span class="sxs-lookup"><span data-stu-id="fc414-102">Marked Transactions, Full Backups, and Log Backups</span></span>
<span data-ttu-id="fc414-103">Le travail de sauvegarde de BizTalk Server crée des sauvegardes synchronisées de toutes les bases de données BizTalk Server à l’aide de sauvegardes complètes et sauvegardes de journaux de transactions, conjointement avec un type de transaction appelé un *transaction marquée*.</span><span class="sxs-lookup"><span data-stu-id="fc414-103">The Backup BizTalk Server Job creates synchronized backups of all BizTalk Server databases by using full database backups and transaction log backups, in conjunction with a type of transaction known as a *marked transaction*.</span></span> <span data-ttu-id="fc414-104">Les transactions marquées sont des transactions qui insèrent une marque dans le journal des transactions de toutes les bases de données participant à la transaction.</span><span class="sxs-lookup"><span data-stu-id="fc414-104">Marked transactions are transactions that place a mark into the transaction log of all databases participating in the transaction.</span></span> <span data-ttu-id="fc414-105">La transaction marquée empêche le démarrage des nouvelles transactions distribuées, attend la fin de l'exécution des transactions distribuées, puis s'exécute pour placer la marque.</span><span class="sxs-lookup"><span data-stu-id="fc414-105">The marked transaction blocks new distributed transactions from starting, waits for the distributed transactions that are currently running to complete, and then executes to place the mark.</span></span>  
  
 <span data-ttu-id="fc414-106">La marque représente un point de transaction cohérent dans toutes les bases de données. Vous pouvez l'utiliser avec les sauvegardes de journal suivantes pour restaurer vos bases de données à ce point.</span><span class="sxs-lookup"><span data-stu-id="fc414-106">The mark represents a transaction point that is consistent across all databases; you can use the mark with subsequent log backups to restore your databases to that point.</span></span>  
  
 <span data-ttu-id="fc414-107">Pour chaque base de données BizTalk Server, le travail de sauvegarde de BizTalk Server crée une sauvegarde de journal des transactions marquée à chaque exécution, puis crée une sauvegarde complète basée sur une période que vous spécifiez.</span><span class="sxs-lookup"><span data-stu-id="fc414-107">For each BizTalk Server database, the Backup BizTalk Server job creates a marked transaction log backup every time it runs, and it creates a full backup based on a time period that you specify.</span></span>  
  
## <a name="full-backups"></a><span data-ttu-id="fc414-108">Sauvegardes complètes</span><span class="sxs-lookup"><span data-stu-id="fc414-108">Full backups</span></span>  
 <span data-ttu-id="fc414-109">Lorsque vous exécutez la tâche de sauvegarde de BizTalk Server qu’il exécute le processus de sauvegarde en premier, *BackupFull*, une fois par période (pas chaque fois que le travail s’exécute).</span><span class="sxs-lookup"><span data-stu-id="fc414-109">When you run the Backup BizTalk Server job it runs the first backup process, *BackupFull*, once every period (not every time the job runs).</span></span> <span data-ttu-id="fc414-110">Pour plus d’informations sur la façon de planifier le travail de sauvegarde de BizTalk Server, consultez [comment planifier le travail de sauvegarde de BizTalk Server](../core/how-to-schedule-the-backup-biztalk-server-job.md).</span><span class="sxs-lookup"><span data-stu-id="fc414-110">For more information about how to schedule the Backup BizTalk Server job, see [How to Schedule the Backup BizTalk Server Job](../core/how-to-schedule-the-backup-biztalk-server-job.md).</span></span>  
  
 <span data-ttu-id="fc414-111">La première fois que le travail de sauvegarde de BizTalk Server s’exécute pendant une période de nouveau, il effectue une sauvegarde complète.</span><span class="sxs-lookup"><span data-stu-id="fc414-111">The first time the Backup BizTalk Server job runs during a new period, it performs a full backup.</span></span> <span data-ttu-id="fc414-112">Par exemple, si vous planifiez une exécution du travail toutes les heures, mais configurez une période quotidienne, le travail de sauvegarde de BizTalk Server effectue une sauvegarde complète lors de sa première exécution, puis chaque jour à minuit.</span><span class="sxs-lookup"><span data-stu-id="fc414-112">For example, if you schedule the job to run every hour but configure the period to be daily, the Backup BizTalk Server job performs a full backup the first time it runs, and then every day at midnight.</span></span>  
  
## <a name="transaction-log-backups"></a><span data-ttu-id="fc414-113">Journal des transactions</span><span class="sxs-lookup"><span data-stu-id="fc414-113">Transaction log backups</span></span>  
 <span data-ttu-id="fc414-114">Le deuxième processus qui effectue de la tâche de sauvegarde de BizTalk Server est *MarkAndBackupLog*.</span><span class="sxs-lookup"><span data-stu-id="fc414-114">The second process that the Backup BizTalk Server job performs is *MarkAndBackupLog*.</span></span> <span data-ttu-id="fc414-115">Ce processus insère une marque dans toutes les bases de données BizTalk Server et effectue une sauvegarde de journal des transactions à chaque exécution du travail.</span><span class="sxs-lookup"><span data-stu-id="fc414-115">This process places a mark in all BizTalk Server databases and performs a transaction log backup every time the job executes.</span></span>  
  
 <span data-ttu-id="fc414-116">La marque est la chaîne créée à l’aide de  *\<nom_serveur >*_*\<DatabaseName >*journa_l\_*\<LogMarkName >* \_  *\<Timestamp >*.bak, où le  *\<nom de marque de journal >* est configuré dans le travail de l’Agent SQL Server.</span><span class="sxs-lookup"><span data-stu-id="fc414-116">The mark is the string created by using *\<ServerName>*_*\<DatabaseName>*_Log\_*\<LogMarkName>*\_*\<Timestamp>*.bak, where the *\<Log Mark Name>* is configured in the SQL Server Agent job.</span></span> <span data-ttu-id="fc414-117">Cette marque doit être utilisée lors de la restauration du dernier journal dans chaque base de données.</span><span class="sxs-lookup"><span data-stu-id="fc414-117">This mark must be used when restoring the last log to each database.</span></span>  
  
 <span data-ttu-id="fc414-118">Pour plus d'informations, consultez les rubriques « Sauvegardes du journal des transactions » et « Sauvegarde et récupération de bases de données associées » dans la documentation en ligne de SQL Server.</span><span class="sxs-lookup"><span data-stu-id="fc414-118">For more information, see "Transaction Log Backups" and "Backup and Recovery of Related Databases" in SQL Server Books Online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc414-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fc414-119">See Also</span></span>  
 [<span data-ttu-id="fc414-120">Informations avancées sur la sauvegarde et restauration</span><span class="sxs-lookup"><span data-stu-id="fc414-120">Advanced Information About Backup and Restore</span></span>](../core/advanced-information-about-backup-and-restore1.md)