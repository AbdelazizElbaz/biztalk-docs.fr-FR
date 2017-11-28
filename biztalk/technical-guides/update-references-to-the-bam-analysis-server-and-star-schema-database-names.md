---
title: "Mettre à jour les références pour le serveur d’analyse BAM et les noms de base de données de schéma en étoile | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 319caa26-1292-4453-a316-efca4fbffdb6
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 184ab156770b0a62208a8e24c7870afa43d3a128
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="update-references-to-the-bam-analysis-server-and-star-schema-database-names"></a><span data-ttu-id="663da-102">Mise à jour des références pour le serveur d’analyse BAM et les noms de base de données de schéma en étoile</span><span class="sxs-lookup"><span data-stu-id="663da-102">Update References to the BAM Analysis Server and Star Schema Database Names</span></span>
<span data-ttu-id="663da-103">Si vous avez sauvegardé votre base de données analyse BAM, en cas de défaillance du système ou des données, vous pouvez restaurer cette sauvegarde vers un autre ordinateur, et vous pouvez renommer la sauvegarde.</span><span class="sxs-lookup"><span data-stu-id="663da-103">If you backed up your BAM Analysis database, in the event of a system or data failure you can restore that backup to a different computer and you can rename the backup.</span></span>  
  
 <span data-ttu-id="663da-104">Pour restaurer les bases de données analyse BAM et des schémas en étoile, effectuez les étapes de [la restauration de bases de données dans le travail de sauvegarde de BizTalk Server](../technical-guides/how-to-restore-databases-in-the-backup-biztalk-server-job.md).</span><span class="sxs-lookup"><span data-stu-id="663da-104">To restore the BAM Analysis and Star Schema databases, perform the steps in [How to Restore Databases in the Backup BizTalk Server Job](../technical-guides/how-to-restore-databases-in-the-backup-biztalk-server-job.md).</span></span> <span data-ttu-id="663da-105">En outre, vous devez mettre à jour l’analyse BAM [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] packages Integration Services (SSIS) avec le nouveau nom du serveur et le nom de la base de données.</span><span class="sxs-lookup"><span data-stu-id="663da-105">In addition, you must update the BAM [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Integration Services (SSIS) packages with the new server name and database name.</span></span>  
  
## <a name="how-to-update-references-to-bam-analysis-server-and-star-schema-database-names"></a><span data-ttu-id="663da-106">Comment mettre à jour les références à un serveur d’analyse BAM et les noms de base de données de schéma en étoile</span><span class="sxs-lookup"><span data-stu-id="663da-106">How to Update References to BAM Analysis Server and Star Schema Database Names</span></span>  
 <span data-ttu-id="663da-107">Pour obtenir des instructions sur la façon de mettre à jour les références aux bases de données de serveur analyse BAM, consultez [mise à jour des références à la nouvelle base de données analyse BAM](../technical-guides/how-to-move-the-bam-analysis-database1.md#BKMK_AnalyUpdate).</span><span class="sxs-lookup"><span data-stu-id="663da-107">For instructions on how to update references to BAM Analysis server databases, see [Updating References to the New BAM Analysis Database](../technical-guides/how-to-move-the-bam-analysis-database1.md#BKMK_AnalyUpdate).</span></span> <span data-ttu-id="663da-108">Pour obtenir des instructions sur la façon de mettre à jour les références aux bases de données de schémas en étoile BAM, consultez [mise à jour des références à la nouvelle base de schéma en étoile BAM](../technical-guides/how-to-move-the-bam-star-schema-database2.md#BKMK_StarUpdate).</span><span class="sxs-lookup"><span data-stu-id="663da-108">For instructions on how to update references to the BAM Star Schema databases, see [Updating References to the New BAM Star Schema Database](../technical-guides/how-to-move-the-bam-star-schema-database2.md#BKMK_StarUpdate).</span></span>