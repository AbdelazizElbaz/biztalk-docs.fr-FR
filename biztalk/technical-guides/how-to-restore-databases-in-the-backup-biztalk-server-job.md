---
title: "Comment restaurer des bases de données dans le travail de sauvegarde de BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9bcac40f-ef0b-4ff0-8743-cf1614e14422
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: eb7c52b810343c1807e982e637372c74baeb84fa
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-restore-databases-in-the-backup-biztalk-server-job"></a><span data-ttu-id="78902-102">Comment restaurer des bases de données dans le travail de sauvegarde de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="78902-102">How to Restore Databases in the Backup BizTalk Server Job</span></span>
<span data-ttu-id="78902-103">Cette section décrit les étapes pour mettre en ligne les bases de données dans le groupe BizTalk qui sont sauvegardés par le travail de sauvegarde de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="78902-103">This section covers the steps to bring online the databases in the BizTalk group that are backed up by the Backup BizTalk Server job.</span></span> <span data-ttu-id="78902-104">Par défaut, toutes les bases de données sont sauvegardées à l’aide de la tâche de sauvegarde de BizTalk Server à l’exception des bases de données BAM.</span><span class="sxs-lookup"><span data-stu-id="78902-104">By default, all databases are backed up by using the Backup BizTalk Server job except for the BAM databases.</span></span> <span data-ttu-id="78902-105">Consultez [restauration Analysis Services et les bases de données prenant en charge](../technical-guides/restoring-analysis-services-and-supporting-databases.md) pour plus d’informations sur la sauvegarde et restauration des bases de données BAM.</span><span class="sxs-lookup"><span data-stu-id="78902-105">See [Restoring Analysis Services and Supporting Databases](../technical-guides/restoring-analysis-services-and-supporting-databases.md) for more information about backup and restore of the BAM databases.</span></span> <span data-ttu-id="78902-106">Vous devez restaurer toutes les bases de données à la même marque afin de garantir un état transactionnel cohérent entre les bases de données.</span><span class="sxs-lookup"><span data-stu-id="78902-106">You must restore all databases to the same mark to ensure a consistent transactional state among the databases.</span></span> <span data-ttu-id="78902-107">Pour plus d’informations, consultez [Transactions marquées, sauvegardes complètes et sauvegardes de journaux](http://go.microsoft.com/fwlink/?LinkId=151565) (http://go.microsoft.com/fwlink/?LinkId=151565).</span><span class="sxs-lookup"><span data-stu-id="78902-107">For more information, see [Marked Transactions, Full Backups, and Log Backups](http://go.microsoft.com/fwlink/?LinkId=151565) (http://go.microsoft.com/fwlink/?LinkId=151565).</span></span>  
  
 <span data-ttu-id="78902-108">Pour plus d’informations et obtenir des instructions sur la restauration de bases de données pour [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], consultez [comment restaurer vos bases de données](http://go.microsoft.com/fwlink/?LinkId=151406) (http://go.microsoft.com/fwlink/?LinkId=151406).</span><span class="sxs-lookup"><span data-stu-id="78902-108">For more information and instructions about restoring databases for [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], see [How to Restore Your Databases](http://go.microsoft.com/fwlink/?LinkId=151406) (http://go.microsoft.com/fwlink/?LinkId=151406).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78902-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="78902-109">See Also</span></span>  
 [<span data-ttu-id="78902-110">Restauration des bases de données non incluses dans le travail de sauvegarde de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="78902-110">Restoring Databases Not Included in the Backup BizTalk Server Job</span></span>](../technical-guides/restoring-databases-not-included-in-the-backup-biztalk-server-job.md)