---
title: "Restauration des bases de données non incluses dans le travail de sauvegarde de BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c7141980-d4a6-4409-be9b-c94a7f733376
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3277886207e04a30fec8bb61f29b5fe8c5ec3545
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="restoring-databases-not-included-in-the-backup-biztalk-server-job"></a>Restauration des bases de données non incluses dans le travail de sauvegarde de BizTalk Server
Cette section explique comment restaurer des bases de données qui font partie de la solution BizTalk globale, mais ne sont pas sauvegardés par le travail de sauvegarde de BizTalk Server. Toutes les bases de données qui font partie d’une solution BizTalk seront sauvegardés à l’aide de la tâche de sauvegarde de BizTalk Server à l’exception des opérations suivantes :  
  
-   [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]Bases de données Analysis Services  
  
-   Bases de données BAM lors de l’analyse BAM est activé et configuré à l’aide de BM.exe  
  
 Cette section décrit comment mettre à jour les références de base de données après la restauration de bases de données répertoriées ci-dessus également et inclut des informations sur la résolution des instances d’activité BAM incomplètes.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Restauration des Services d’analyse et la prise en charge des bases de données](../technical-guides/restoring-analysis-services-and-supporting-databases.md)  
  
-   [Mise à jour des références de base de données](../technical-guides/updating-database-references.md)  
  
-   [Comment résoudre les Instances d’activité BAM incomplète](../technical-guides/how-to-resolve-incomplete-bam-activity-instances.md)