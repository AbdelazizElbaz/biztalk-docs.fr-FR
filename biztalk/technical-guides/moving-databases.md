---
title: "Déplacement de bases de données | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6a0d09a1-90a5-4a5d-a783-b979724e101b
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f5dd25f898890225300f8962e581a38912f36351
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="moving-databases"></a><span data-ttu-id="7371f-102">Déplacement de bases de données</span><span class="sxs-lookup"><span data-stu-id="7371f-102">Moving Databases</span></span>
<span data-ttu-id="7371f-103">La méthode recommandée pour déplacer [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] bases de données (sauf pour les bases de données analyse BAM (Business Activity)) consiste à configurer [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] journaux comme décrit dans la section [la récupération d’urgence](../technical-guides/disaster-recovery.md).</span><span class="sxs-lookup"><span data-stu-id="7371f-103">The recommended method for moving [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases (except for the Business Activity Monitoring (BAM) databases) is to configure [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] log shipping as described in the section [Disaster Recovery](../technical-guides/disaster-recovery.md).</span></span> <span data-ttu-id="7371f-104">À l’exception des bases de données utilisées par l’analyse BAM, tous les [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] bases de données peuvent être sauvegardées à l’aide de la **sauvegarde de BizTalk Server** [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] travail de l’Agent.</span><span class="sxs-lookup"><span data-stu-id="7371f-104">With the exception of the databases used by BAM, all of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases can be backed up by using the **Backup BizTalk Server**[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Agent job.</span></span> <span data-ttu-id="7371f-105">Pour plus d’informations sur cette tâche, consultez [comment planifier le travail de sauvegarde de BizTalk Server](http://go.microsoft.com/fwlink/?LinkId=154674) (http://go.microsoft.com/fwlink/?LinkId=154674) dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] aide.</span><span class="sxs-lookup"><span data-stu-id="7371f-105">For more information about this job, see [How to Schedule the Backup BizTalk Server Job](http://go.microsoft.com/fwlink/?LinkId=154674) (http://go.microsoft.com/fwlink/?LinkId=154674) in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help.</span></span>  
  
 <span data-ttu-id="7371f-106">Cette section décrit comment déplacer les bases de données BAM et comment déplacer les autres [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] bases de données sans configurer au préalable [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] journaux de transaction.</span><span class="sxs-lookup"><span data-stu-id="7371f-106">This section describes how to move the BAM-related databases and how to move the remaining [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases without first configuring [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] log shipping.</span></span> <span data-ttu-id="7371f-107">Cette approche peut être utile lors de la mise à niveau le [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] les ordinateurs qui hébergent le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] bases de données ou dans d’autres scénarios qui ne sont pas liées à la récupération d’urgence.</span><span class="sxs-lookup"><span data-stu-id="7371f-107">This approach may be useful when upgrading the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] computers that house the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases or in other scenarios that are not related to disaster recovery.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7371f-108">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="7371f-108">In This Section</span></span>  
  
-   [<span data-ttu-id="7371f-109">Déplacement de bases de données BAM</span><span class="sxs-lookup"><span data-stu-id="7371f-109">Moving BAM Databases</span></span>](../technical-guides/moving-bam-databases.md)  
  
-   [<span data-ttu-id="7371f-110">Déplacement de bases de données Non-BAM</span><span class="sxs-lookup"><span data-stu-id="7371f-110">Moving Non-BAM Databases</span></span>](../technical-guides/moving-non-bam-databases.md)  
  
## <a name="see-also"></a><span data-ttu-id="7371f-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7371f-111">See Also</span></span>  
 [<span data-ttu-id="7371f-112">La gestion de BizTalk Serveur2</span><span class="sxs-lookup"><span data-stu-id="7371f-112">Managing BizTalk Server2</span></span>](../technical-guides/managing-biztalk-server2.md)