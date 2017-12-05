---
title: Restauration du groupe BizTalk | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 14a9af44-d6de-49c7-9600-21ece389727f
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8e8d1741d89e8326cc68906644cf34e71bfcc8e1
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="restoring-the-biztalk-group"></a>Restauration du groupe BizTalk
Le groupe BizTalk est représenté par l’ensemble de [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] et [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] bases de données Analysis Services, les packages SSIS et les travaux de l’Agent SQL. Cette section décrit le processus de restauration du groupe BizTalk.  
  
 Dans le cas où un basculement vers le système de destination (site de récupération d’urgence) est requis, vous devant effectuer les étapes suivantes :  
  
1.  Restaurer [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] et bases de données Analysis Services.  
  
2.  Restaurer les applications et les serveurs d’exécution de BizTalk Server.  
  
 À la fin de ces étapes, le groupe BizTalk a été établi sur le site de récupération d’urgence, le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] runtime serveurs peuvent être configurés, et les applications peuvent être déployées dans le groupe BizTalk. Les rubriques de cette section couvrent les détails de ce processus.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Arrêt du traitement des applications sur le système source](../technical-guides/stopping-application-processing-on-the-source-system.md)  
  
-   [Comment restaurer des bases de données dans la tâche BizTalk Server de sauvegarde](../technical-guides/how-to-restore-databases-in-the-backup-biztalk-server-job.md)  
  
-   [Restauration des bases de données non incluses dans la tâche BizTalk Server de sauvegarde](../technical-guides/restoring-databases-not-included-in-the-backup-biztalk-server-job.md)