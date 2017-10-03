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
ms.openlocfilehash: c12a1deff8fea6d769f138aa34bf6dab269a167f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="restoring-the-biztalk-group"></a>Restauration du groupe BizTalk
Le groupe BizTalk est représenté par l’ensemble de [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] et [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] bases de données Analysis Services, les packages SSIS et les travaux de l’Agent SQL. Cette section décrit le processus de restauration du groupe BizTalk.  
  
 Dans le cas où un basculement vers le système de destination (site de récupération d’urgence) est requis, vous devant effectuer les étapes suivantes :  
  
1.  Restaurer [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] et bases de données Analysis Services.  
  
2.  Restaurer [!INCLUDE[prague](../includes/prague-md.md)] runtime serveurs et applications.  
  
 À la fin de ces étapes, le groupe BizTalk a été établi sur le site de récupération d’urgence, le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] runtime serveurs peuvent être configurés, et les applications peuvent être déployées dans le groupe BizTalk. Les rubriques de cette section couvrent les détails de ce processus.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [L’arrêt d’Application de traitement sur le système Source](../technical-guides/stopping-application-processing-on-the-source-system.md)  
  
-   [Comment restaurer des bases de données dans le travail de sauvegarde de BizTalk Server](../technical-guides/how-to-restore-databases-in-the-backup-biztalk-server-job.md)  
  
-   [Restauration des bases de données non incluses dans le travail de sauvegarde de BizTalk Server](../technical-guides/restoring-databases-not-included-in-the-backup-biztalk-server-job.md)