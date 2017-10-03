---
title: Optimisation des performances | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bafa119b-187e-4595-a673-358dc0a109b7
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4e79c318d7cd12d799459535914046da98819561
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="optimizing-performance"></a><span data-ttu-id="527b9-102">Optimisation des performances</span><span class="sxs-lookup"><span data-stu-id="527b9-102">Optimizing Performance</span></span>
<span data-ttu-id="527b9-103">Une installation par défaut du système d’exploitation Windows, SQL Server, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], et IIS peut être considérablement améliorée pour fournir des performances optimales pour la production [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environnement.</span><span class="sxs-lookup"><span data-stu-id="527b9-103">A default installation of the Windows operating system, SQL Server, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], and IIS can be significantly optimized to provide optimal performance for a production [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment.</span></span> <span data-ttu-id="527b9-104">Paramètres de configuration WCF peuvent également être personnalisées à partir des paramètres par défaut pour fournir des performances significativement accrues.</span><span class="sxs-lookup"><span data-stu-id="527b9-104">WCF configuration parameters can also be tuned from the default settings to provide significantly improved performance.</span></span> <span data-ttu-id="527b9-105">Cette section fournit des optimisations de performances spécifiques qui doivent être respectées lors du déploiement d’une production [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] solution.</span><span class="sxs-lookup"><span data-stu-id="527b9-105">This section provides specific performance optimizations that should be followed when deploying a production [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] solution.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="527b9-106">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="527b9-106">In This Section</span></span>  
  
-   [<span data-ttu-id="527b9-107">Optimisation des performances du système d’exploitation</span><span class="sxs-lookup"><span data-stu-id="527b9-107">Optimizing Operating System Performance</span></span>](../technical-guides/optimizing-operating-system-performance.md)  
  
-   [<span data-ttu-id="527b9-108">Optimisation des performances réseau</span><span class="sxs-lookup"><span data-stu-id="527b9-108">Optimizing Network Performance</span></span>](../technical-guides/optimizing-network-performance.md)  
  
-   [<span data-ttu-id="527b9-109">Optimisation des performances d’IIS</span><span class="sxs-lookup"><span data-stu-id="527b9-109">Optimizing IIS Performance</span></span>](../technical-guides/optimizing-iis-performance.md)  
  
-   [<span data-ttu-id="527b9-110">Optimisation des performances de la base de données</span><span class="sxs-lookup"><span data-stu-id="527b9-110">Optimizing Database Performance</span></span>](../technical-guides/optimizing-database-performance.md)  
  
-   [<span data-ttu-id="527b9-111">Optimisation des performances de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="527b9-111">Optimizing BizTalk Server Performance</span></span>](../technical-guides/optimizing-biztalk-server-performance.md)  
  
-   [<span data-ttu-id="527b9-112">Optimisation des performances de l’Orchestration</span><span class="sxs-lookup"><span data-stu-id="527b9-112">Optimizing Orchestration Performance</span></span>](../technical-guides/optimizing-orchestration-performance.md)  
  
-   [<span data-ttu-id="527b9-113">Optimisation des performances du Service Web WCF</span><span class="sxs-lookup"><span data-stu-id="527b9-113">Optimizing WCF Web Service Performance</span></span>](../technical-guides/optimizing-wcf-web-service-performance.md)  
  
-   [<span data-ttu-id="527b9-114">Optimisation des Applications BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="527b9-114">Optimizing BizTalk Server Applications</span></span>](../technical-guides/optimizing-biztalk-server-applications.md)  
  
-   [<span data-ttu-id="527b9-115">Scripts Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="527b9-115">Windows PowerShell Scripts</span></span>](../technical-guides/windows-powershell-scripts.md)