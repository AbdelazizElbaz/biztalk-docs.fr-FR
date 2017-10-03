---
title: "Mettre à jour les références à la base de données importation principale BAM | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3da3b545-0d81-491b-bc37-0a980a7814b6
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0ba37a32c82967e84b61bb46c58c62af9bf23b1b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="update-references-to-the-bam-primary-import-database"></a><span data-ttu-id="d8a03-102">Mettre à jour les références à la base de données importation principale BAM</span><span class="sxs-lookup"><span data-stu-id="d8a03-102">Update References to the BAM Primary Import Database</span></span>
<span data-ttu-id="d8a03-103">Si vous avez sauvegardé votre base de données d'importation principale BAM, vous pouvez, dans l'éventualité d'une défaillance de données ou du système, restaurer cette sauvegarde sur un ordinateur distinct et la renommer.</span><span class="sxs-lookup"><span data-stu-id="d8a03-103">If you backed up your BAM Primary Import database in the event of a system or data failure, you can restore that backup to a different computer and rename the backup.</span></span>  
  
 <span data-ttu-id="d8a03-104">Le service Bus d'événements BAM déplace les données d'événements de la base de données MessageBox vers la base de données d'importation principale BAM.</span><span class="sxs-lookup"><span data-stu-id="d8a03-104">The BAM Event Bus service moves event data from the MessageBox database to the BAM Primary Import database.</span></span> <span data-ttu-id="d8a03-105">Le service Bus d'événements BAM inclut la logique de tolérance de pannes qui lui permet de récupérer et de redémarrer à partir d'une erreur inattendue sans perdre de données.</span><span class="sxs-lookup"><span data-stu-id="d8a03-105">The BAM Event Bus service includes fault tolerance logic that enables it to recover and restart from an unexpected failure without losing any data.</span></span> <span data-ttu-id="d8a03-106">Pour plus d’informations sur le service Bus d’événements BAM, consultez la rubrique [gestion Service Bus d’événements BAM](http://go.microsoft.com/fwlink/?LinkID=154194) (http://go.microsoft.com/fwlink/?LinkID=154194).</span><span class="sxs-lookup"><span data-stu-id="d8a03-106">For more information about the BAM Event Bus service, see the topic [Managing the BAM Event Bus Service](http://go.microsoft.com/fwlink/?LinkID=154194) (http://go.microsoft.com/fwlink/?LinkID=154194).</span></span>  
  
 <span data-ttu-id="d8a03-107">Pour restaurer la base de données d’importation principale BAM, effectuez les étapes de [la restauration de bases de données dans le travail de sauvegarde de BizTalk Server](../technical-guides/how-to-restore-databases-in-the-backup-biztalk-server-job.md).</span><span class="sxs-lookup"><span data-stu-id="d8a03-107">To restore the BAM Primary Import database, perform the steps in [How to Restore Databases in the Backup BizTalk Server Job](../technical-guides/how-to-restore-databases-in-the-backup-biztalk-server-job.md).</span></span> <span data-ttu-id="d8a03-108">En outre, vous devez mettre à jour les packages BAM SSIS avec le nouveau nom du serveur et le nom de la base de données.</span><span class="sxs-lookup"><span data-stu-id="d8a03-108">In addition, you must update the BAM SSIS packages with the new server name and database name.</span></span>  
  
## <a name="how-to-update-references-to-bam-primary-import-database"></a><span data-ttu-id="d8a03-109">Comment mettre à jour les références à la base de données importation principale BAM</span><span class="sxs-lookup"><span data-stu-id="d8a03-109">How to Update References to BAM Primary Import Database</span></span>  
 <span data-ttu-id="d8a03-110">Pour obtenir des instructions sur la façon de mettre à jour les références à la base de données d’importation principale BAM, [mise à jour des références à la nouvelle base importation principale BAM](../technical-guides/how-to-move-the-bam-primary-import-database2.md#BKMK_BAMPIRef).</span><span class="sxs-lookup"><span data-stu-id="d8a03-110">For instructions on how to update references to BAM Primary Import database, [Updating References to the New BAM Primary Import Database](../technical-guides/how-to-move-the-bam-primary-import-database2.md#BKMK_BAMPIRef).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8a03-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d8a03-111">See Also</span></span>  
 [<span data-ttu-id="d8a03-112">Sauvegarde de l’analyse BAM et le suivi des bases de données Analysis Server</span><span class="sxs-lookup"><span data-stu-id="d8a03-112">Backing Up the BAM Analysis and Tracking Analysis Server Databases</span></span>](../technical-guides/backing-up-the-bam-analysis-and-tracking-analysis-server-databases.md)