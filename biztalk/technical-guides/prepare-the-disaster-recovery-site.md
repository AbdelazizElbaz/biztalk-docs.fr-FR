---
title: "Préparer le Site de récupération d’urgence | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0b66f3c8-afe0-4ac0-b925-8f780d14bd4b
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7a60be6d04d0f73013f67c5fe8e5b0144357fd1f
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="prepare-the-disaster-recovery-site"></a><span data-ttu-id="bac8c-102">Préparer le Site de récupération d’urgence</span><span class="sxs-lookup"><span data-stu-id="bac8c-102">Prepare the Disaster Recovery Site</span></span>
<span data-ttu-id="bac8c-103">Journaux de BizTalk Server expédition a deux scénarios pris en charge.</span><span class="sxs-lookup"><span data-stu-id="bac8c-103">BizTalk Server log shipping has two supported scenarios.</span></span> <span data-ttu-id="bac8c-104">Un est où des journaux pour toutes les bases de données sur toutes les instances de production de [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] est appliqué à une instance de la récupération d’urgence unique de [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bac8c-104">One is where log shipping for all databases on all production instances of [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] is applied to a single disaster recovery instance of [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)].</span></span> <span data-ttu-id="bac8c-105">L’autre scénario est où des journaux pour les bases de données pour chaque instance de production de [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] est appliqué à une instance correspondante de [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] sur le site de récupération d’urgence.</span><span class="sxs-lookup"><span data-stu-id="bac8c-105">The other scenario is where log shipping for the databases for each production instance of [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] is applied to a corresponding instance of [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] at the disaster recovery site.</span></span> <span data-ttu-id="bac8c-106">Notez qu’il est entièrement pris en charge pour avoir le même nombre de [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] de la base de données d’instances dans le site de récupération d’urgence comme il y a en production, mais moins de serveurs physiques.</span><span class="sxs-lookup"><span data-stu-id="bac8c-106">Note that it is fully supported to have the same number of [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] database instances in the disaster recovery site as there is in production but on fewer physical servers.</span></span> <span data-ttu-id="bac8c-107">Cette section fournit des conseils sur ces préparatifs.</span><span class="sxs-lookup"><span data-stu-id="bac8c-107">This section provides guidance on these preparations.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="bac8c-108">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="bac8c-108">In This Section</span></span>  
  
-   [<span data-ttu-id="bac8c-109">Préparation des serveurs SQL Server de récupération d’urgence</span><span class="sxs-lookup"><span data-stu-id="bac8c-109">Preparing the Disaster Recovery SQL Servers</span></span>](../technical-guides/preparing-the-disaster-recovery-sql-servers.md)  
  
-   [<span data-ttu-id="bac8c-110">Sauvegarde des bases de données Analysis Server d’analyse et de suivi BAM</span><span class="sxs-lookup"><span data-stu-id="bac8c-110">Backing Up the BAM Analysis and Tracking Analysis Server Databases</span></span>](../technical-guides/backing-up-the-bam-analysis-and-tracking-analysis-server-databases.md)  
  
-   [<span data-ttu-id="bac8c-111">Préparation des serveurs BizTalk de récupération d’urgence</span><span class="sxs-lookup"><span data-stu-id="bac8c-111">Preparing the Disaster Recovery BizTalk Servers</span></span>](../technical-guides/preparing-the-disaster-recovery-biztalk-servers.md)  
  
-   [<span data-ttu-id="bac8c-112">Préparation des applications pour la récupération d’urgence</span><span class="sxs-lookup"><span data-stu-id="bac8c-112">Preparing Applications for Disaster Recovery</span></span>](../technical-guides/preparing-applications-for-disaster-recovery.md)  
  
-   [<span data-ttu-id="bac8c-113">Comment restaurer le serveur de secret principal</span><span class="sxs-lookup"><span data-stu-id="bac8c-113">How to Restore the Master Secret Server</span></span>](../technical-guides/how-to-restore-the-master-secret-server.md)