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
# <a name="how-to-restore-databases-in-the-backup-biztalk-server-job"></a>Comment restaurer des bases de données dans le travail de sauvegarde de BizTalk Server
Cette section décrit les étapes pour mettre en ligne les bases de données dans le groupe BizTalk qui sont sauvegardés par le travail de sauvegarde de BizTalk Server. Par défaut, toutes les bases de données sont sauvegardées à l’aide de la tâche de sauvegarde de BizTalk Server à l’exception des bases de données BAM. Consultez [restauration Analysis Services et les bases de données prenant en charge](../technical-guides/restoring-analysis-services-and-supporting-databases.md) pour plus d’informations sur la sauvegarde et restauration des bases de données BAM. Vous devez restaurer toutes les bases de données à la même marque afin de garantir un état transactionnel cohérent entre les bases de données. Pour plus d’informations, consultez [Transactions marquées, sauvegardes complètes et sauvegardes de journaux](http://go.microsoft.com/fwlink/?LinkId=151565) (http://go.microsoft.com/fwlink/?LinkId=151565).  
  
 Pour plus d’informations et obtenir des instructions sur la restauration de bases de données pour [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], consultez [comment restaurer vos bases de données](http://go.microsoft.com/fwlink/?LinkId=151406) (http://go.microsoft.com/fwlink/?LinkId=151406).  
  
## <a name="see-also"></a>Voir aussi  
 [Restauration des bases de données non incluses dans le travail de sauvegarde de BizTalk Server](../technical-guides/restoring-databases-not-included-in-the-backup-biztalk-server-job.md)