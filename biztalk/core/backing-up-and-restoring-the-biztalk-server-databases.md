---
title: "Sauvegarde et restauration des bases de données BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- backing up, BizTalk Server
- backing up, transaction logs
- maintaining, restoring
- restoring, BizTalk Server
- maintaining, backing up
- transaction logs
ms.assetid: 7c08ce19-614c-4728-8dde-c40d4052339e
caps.latest.revision: "23"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 44bbb9316f1d036551acba5441424bcce65c2549
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="backing-up-and-restoring-the-biztalk-server-databases"></a><span data-ttu-id="dd8aa-102">Sauvegarde et restauration des bases de données BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="dd8aa-102">Backing Up and Restoring the BizTalk Server Databases</span></span>
<span data-ttu-id="dd8aa-103">Cette section fournit des informations sur la sauvegarde et la restauration des bases de données de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="dd8aa-103">This section provides information about how to back up and restore the BizTalk Server databases.</span></span> <span data-ttu-id="dd8aa-104">Vous devez suivre les procédures de cette section pour être certain de pouvoir restaurer un environnement BizTalk Server cohérent en cas de défaillance matérielle.</span><span class="sxs-lookup"><span data-stu-id="dd8aa-104">You should follow the procedures in this section to ensure your ability to restore a consistent BizTalk Server environment in the event of a hardware failure.</span></span> <span data-ttu-id="dd8aa-105">BizTalk Server exécute des transactions distribuées entre les bases de données, de sorte qu'il est essentiel de sauvegarder et restaurer toutes les bases de données.</span><span class="sxs-lookup"><span data-stu-id="dd8aa-105">BizTalk Server performs distributed transactions across databases, so it is critical that you back up and then restore all databases.</span></span>  
  
 <span data-ttu-id="dd8aa-106">BizTalk Server requiert un processus de sauvegarde personnalisé basé sur des sauvegardes de base de données complètes et des sauvegardes de journal avec le marquage de journal transactionnel.</span><span class="sxs-lookup"><span data-stu-id="dd8aa-106">BizTalk Server requires a customized backup process that uses full database backups and log backups in conjunction with transactional log marking.</span></span> <span data-ttu-id="dd8aa-107">Pour plus d’informations sur ce processus, consultez [Transactions marquées, sauvegardes complètes et sauvegardes de journal](../core/marked-transactions-full-backups-and-log-backups.md).</span><span class="sxs-lookup"><span data-stu-id="dd8aa-107">For information about this process, see [Marked Transactions, Full Backups, and Log Backups](../core/marked-transactions-full-backups-and-log-backups.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="dd8aa-108">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="dd8aa-108">In This Section</span></span>  
  
-   [<span data-ttu-id="dd8aa-109">Liste de vérification : Sauvegarder et restaurer des bases de données BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="dd8aa-109">Checklist: Back Up and Restore BizTalk Server Databases</span></span>](../core/checklist-back-up-and-restore-biztalk-server-databases.md)  
  
-   [<span data-ttu-id="dd8aa-110">Meilleures pratiques pour la sauvegarde et restauration des bases de données</span><span class="sxs-lookup"><span data-stu-id="dd8aa-110">Best Practices for Backing Up and Restoring Databases</span></span>](../core/best-practices-for-backing-up-and-restoring-databases.md)  
  
-   [<span data-ttu-id="dd8aa-111">Sauvegarde et restauration des bases de données BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="dd8aa-111">Backing Up and Restoring BizTalk Server Databases</span></span>](../core/backing-up-and-restoring-biztalk-server-databases.md)  
  
-   [<span data-ttu-id="dd8aa-112">Sauvegarde et restauration BAM</span><span class="sxs-lookup"><span data-stu-id="dd8aa-112">Backing Up and Restoring BAM</span></span>](../core/backing-up-and-restoring-bam.md)  
  
-   [<span data-ttu-id="dd8aa-113">Résolution de la perte de données</span><span class="sxs-lookup"><span data-stu-id="dd8aa-113">Resolving Data Loss</span></span>](../core/resolving-data-loss.md)  
  
-   [<span data-ttu-id="dd8aa-114">Informations avancées sur la sauvegarde et restauration</span><span class="sxs-lookup"><span data-stu-id="dd8aa-114">Advanced Information About Backup and Restore</span></span>](../core/advanced-information-about-backup-and-restore1.md)