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
# <a name="update-references-to-the-bam-analysis-server-and-star-schema-database-names"></a>Mise à jour des références pour le serveur d’analyse BAM et les noms de base de données de schéma en étoile
Si vous avez sauvegardé votre base de données analyse BAM, en cas de défaillance du système ou des données, vous pouvez restaurer cette sauvegarde vers un autre ordinateur, et vous pouvez renommer la sauvegarde.  
  
 Pour restaurer les bases de données analyse BAM et des schémas en étoile, effectuez les étapes de [la restauration de bases de données dans le travail de sauvegarde de BizTalk Server](../technical-guides/how-to-restore-databases-in-the-backup-biztalk-server-job.md). En outre, vous devez mettre à jour l’analyse BAM [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] packages Integration Services (SSIS) avec le nouveau nom du serveur et le nom de la base de données.  
  
## <a name="how-to-update-references-to-bam-analysis-server-and-star-schema-database-names"></a>Comment mettre à jour les références à un serveur d’analyse BAM et les noms de base de données de schéma en étoile  
 Pour obtenir des instructions sur la façon de mettre à jour les références aux bases de données de serveur analyse BAM, consultez [mise à jour des références à la nouvelle base de données analyse BAM](../technical-guides/how-to-move-the-bam-analysis-database1.md#BKMK_AnalyUpdate). Pour obtenir des instructions sur la façon de mettre à jour les références aux bases de données de schémas en étoile BAM, consultez [mise à jour des références à la nouvelle base de schéma en étoile BAM](../technical-guides/how-to-move-the-bam-star-schema-database2.md#BKMK_StarUpdate).