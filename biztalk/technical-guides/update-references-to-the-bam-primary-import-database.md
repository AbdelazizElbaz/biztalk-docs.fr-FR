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
# <a name="update-references-to-the-bam-primary-import-database"></a>Mettre à jour les références à la base de données importation principale BAM
Si vous avez sauvegardé votre base de données d'importation principale BAM, vous pouvez, dans l'éventualité d'une défaillance de données ou du système, restaurer cette sauvegarde sur un ordinateur distinct et la renommer.  
  
 Le service Bus d'événements BAM déplace les données d'événements de la base de données MessageBox vers la base de données d'importation principale BAM. Le service Bus d'événements BAM inclut la logique de tolérance de pannes qui lui permet de récupérer et de redémarrer à partir d'une erreur inattendue sans perdre de données. Pour plus d’informations sur le service Bus d’événements BAM, consultez la rubrique [gestion Service Bus d’événements BAM](http://go.microsoft.com/fwlink/?LinkID=154194) (http://go.microsoft.com/fwlink/?LinkID=154194).  
  
 Pour restaurer la base de données d’importation principale BAM, effectuez les étapes de [la restauration de bases de données dans le travail de sauvegarde de BizTalk Server](../technical-guides/how-to-restore-databases-in-the-backup-biztalk-server-job.md). En outre, vous devez mettre à jour les packages BAM SSIS avec le nouveau nom du serveur et le nom de la base de données.  
  
## <a name="how-to-update-references-to-bam-primary-import-database"></a>Comment mettre à jour les références à la base de données importation principale BAM  
 Pour obtenir des instructions sur la façon de mettre à jour les références à la base de données d’importation principale BAM, [mise à jour des références à la nouvelle base importation principale BAM](../technical-guides/how-to-move-the-bam-primary-import-database2.md#BKMK_BAMPIRef).  
  
## <a name="see-also"></a>Voir aussi  
 [Sauvegarde de l’analyse BAM et le suivi des bases de données Analysis Server](../technical-guides/backing-up-the-bam-analysis-and-tracking-analysis-server-databases.md)