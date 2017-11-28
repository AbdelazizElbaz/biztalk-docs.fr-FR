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
# <a name="restoring-databases-not-included-in-the-backup-biztalk-server-job"></a><span data-ttu-id="0fef9-102">Restauration des bases de données non incluses dans le travail de sauvegarde de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="0fef9-102">Restoring Databases Not Included in the Backup BizTalk Server Job</span></span>
<span data-ttu-id="0fef9-103">Cette section explique comment restaurer des bases de données qui font partie de la solution BizTalk globale, mais ne sont pas sauvegardés par le travail de sauvegarde de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="0fef9-103">This section describes how to restore databases that are part of the overall BizTalk solution but are not backed up by the Backup BizTalk Server job.</span></span> <span data-ttu-id="0fef9-104">Toutes les bases de données qui font partie d’une solution BizTalk seront sauvegardés à l’aide de la tâche de sauvegarde de BizTalk Server à l’exception des opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="0fef9-104">All databases that are part of a BizTalk solution will be backed up by using the Backup BizTalk Server job except for the following:</span></span>  
  
-   [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]<span data-ttu-id="0fef9-105">Bases de données Analysis Services</span><span class="sxs-lookup"><span data-stu-id="0fef9-105"> Analysis Services databases</span></span>  
  
-   <span data-ttu-id="0fef9-106">Bases de données BAM lors de l’analyse BAM est activé et configuré à l’aide de BM.exe</span><span class="sxs-lookup"><span data-stu-id="0fef9-106">BAM databases when BAM is enabled and configured using BM.exe</span></span>  
  
 <span data-ttu-id="0fef9-107">Cette section décrit comment mettre à jour les références de base de données après la restauration de bases de données répertoriées ci-dessus également et inclut des informations sur la résolution des instances d’activité BAM incomplètes.</span><span class="sxs-lookup"><span data-stu-id="0fef9-107">This section also describes how to update database references after restoring the databases listed above and includes information about resolving incomplete BAM activity instances.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0fef9-108">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="0fef9-108">In This Section</span></span>  
  
-   [<span data-ttu-id="0fef9-109">Restauration des Services d’analyse et la prise en charge des bases de données</span><span class="sxs-lookup"><span data-stu-id="0fef9-109">Restoring Analysis Services and Supporting Databases</span></span>](../technical-guides/restoring-analysis-services-and-supporting-databases.md)  
  
-   [<span data-ttu-id="0fef9-110">Mise à jour des références de base de données</span><span class="sxs-lookup"><span data-stu-id="0fef9-110">Updating Database References</span></span>](../technical-guides/updating-database-references.md)  
  
-   [<span data-ttu-id="0fef9-111">Comment résoudre les Instances d’activité BAM incomplète</span><span class="sxs-lookup"><span data-stu-id="0fef9-111">How to Resolve Incomplete BAM Activity Instances</span></span>](../technical-guides/how-to-resolve-incomplete-bam-activity-instances.md)