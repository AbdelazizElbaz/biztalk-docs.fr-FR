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
# <a name="restoring-the-biztalk-group"></a><span data-ttu-id="6fab5-102">Restauration du groupe BizTalk</span><span class="sxs-lookup"><span data-stu-id="6fab5-102">Restoring the BizTalk Group</span></span>
<span data-ttu-id="6fab5-103">Le groupe BizTalk est représenté par l’ensemble de [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] et [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] bases de données Analysis Services, les packages SSIS et les travaux de l’Agent SQL.</span><span class="sxs-lookup"><span data-stu-id="6fab5-103">The BizTalk group is represented by the set of [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] and [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Analysis Services databases, SSIS packages, and SQL Agent Jobs.</span></span> <span data-ttu-id="6fab5-104">Cette section décrit le processus de restauration du groupe BizTalk.</span><span class="sxs-lookup"><span data-stu-id="6fab5-104">This section describes the process for restoring the BizTalk group.</span></span>  
  
 <span data-ttu-id="6fab5-105">Dans le cas où un basculement vers le système de destination (site de récupération d’urgence) est requis, vous devant effectuer les étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="6fab5-105">In the event that a switchover to the destination system (disaster recovery site) is required, the following steps must be completed:</span></span>  
  
1.  <span data-ttu-id="6fab5-106">Restaurer [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] et bases de données Analysis Services.</span><span class="sxs-lookup"><span data-stu-id="6fab5-106">Restore [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] and Analysis Services databases.</span></span>  
  
2.  <span data-ttu-id="6fab5-107">Restaurer [!INCLUDE[prague](../includes/prague-md.md)] runtime serveurs et applications.</span><span class="sxs-lookup"><span data-stu-id="6fab5-107">Restore [!INCLUDE[prague](../includes/prague-md.md)] runtime servers and applications.</span></span>  
  
 <span data-ttu-id="6fab5-108">À la fin de ces étapes, le groupe BizTalk a été établi sur le site de récupération d’urgence, le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] runtime serveurs peuvent être configurés, et les applications peuvent être déployées dans le groupe BizTalk.</span><span class="sxs-lookup"><span data-stu-id="6fab5-108">Upon completion of these steps, the BizTalk group has been established at the disaster recovery site, the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] runtime servers can be configured, and the applications can be deployed into the BizTalk group.</span></span> <span data-ttu-id="6fab5-109">Les rubriques de cette section couvrent les détails de ce processus.</span><span class="sxs-lookup"><span data-stu-id="6fab5-109">The topics in this section cover the details of this process.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6fab5-110">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="6fab5-110">In This Section</span></span>  
  
-   [<span data-ttu-id="6fab5-111">L’arrêt d’Application de traitement sur le système Source</span><span class="sxs-lookup"><span data-stu-id="6fab5-111">Stopping Application Processing on the Source System</span></span>](../technical-guides/stopping-application-processing-on-the-source-system.md)  
  
-   [<span data-ttu-id="6fab5-112">Comment restaurer des bases de données dans le travail de sauvegarde de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="6fab5-112">How to Restore Databases in the Backup BizTalk Server Job</span></span>](../technical-guides/how-to-restore-databases-in-the-backup-biztalk-server-job.md)  
  
-   [<span data-ttu-id="6fab5-113">Restauration des bases de données non incluses dans le travail de sauvegarde de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="6fab5-113">Restoring Databases Not Included in the Backup BizTalk Server Job</span></span>](../technical-guides/restoring-databases-not-included-in-the-backup-biztalk-server-job.md)