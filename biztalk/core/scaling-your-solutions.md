---
title: "Mise à l’échelle de vos Solutions | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- performance, scaling
- scaling, scaling out
- scaling, performance
- scaling, about scaling
- scaling, scaling up
- scaling
ms.assetid: e2acbaa4-29d3-4c89-ac1f-c0641cfa0442
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5417e303ea8486ef5bdee8e57c66d4783fb197ed
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="scaling-your-solutions"></a><span data-ttu-id="46e4c-102">Mise à l'échelle des solutions</span><span class="sxs-lookup"><span data-stu-id="46e4c-102">Scaling Your Solutions</span></span>
<span data-ttu-id="46e4c-103">L'architecture BizTalk Server offre de grandes possibilités d'évolutivité.</span><span class="sxs-lookup"><span data-stu-id="46e4c-103">BizTalk Server architecture provides a very good support for scalability.</span></span> <span data-ttu-id="46e4c-104">Les modèles d'évolutivité que vous choisissez dépendent de la complexité de votre scénario, de votre matériel et de vos exigences en termes de débit et de latence.</span><span class="sxs-lookup"><span data-stu-id="46e4c-104">The scaling patterns that you choose depend on complexity of your scenario, hardware and the throughput/Latency requirements.</span></span> <span data-ttu-id="46e4c-105">Il est préférable de démarrer par une petite topologie, puis d'essayer de procéder à une évolution horizontale ou verticale en suivant les instructions fournies dans cette section.</span><span class="sxs-lookup"><span data-stu-id="46e4c-105">You should start with a smaller topology initially and try to scale-up or down based on the guidelines in this section.</span></span>  
  
## <a name="scaling-out-and-scaling-up"></a><span data-ttu-id="46e4c-106">Évolutions horizontale et verticale</span><span class="sxs-lookup"><span data-stu-id="46e4c-106">Scaling Out and Scaling Up</span></span>  
 <span data-ttu-id="46e4c-107">Il existe deux manières de faire évoluer votre système BizTalk Server :</span><span class="sxs-lookup"><span data-stu-id="46e4c-107">There are two ways to scale your BizTalk Server system:</span></span>  
  
-   <span data-ttu-id="46e4c-108">L'évolution horizontale consiste à ajouter des ordinateurs supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="46e4c-108">Scaling-out is the process of adding additional computers.</span></span> <span data-ttu-id="46e4c-109">Par exemple, si BizTalk Server est engorgé au niveau des ressources d'UC, l'ajout d'un autre serveur double ces ressources et éventuellement le débit.</span><span class="sxs-lookup"><span data-stu-id="46e4c-109">For example, if BizTalk Server is bottlenecked by CPU resources, adding another server provides double the CPU resources which may provide double the throughput.</span></span>  
  
-   <span data-ttu-id="46e4c-110">L'évolution verticale consiste à mettre à niveau l'ordinateur existant.</span><span class="sxs-lookup"><span data-stu-id="46e4c-110">Scaling-up is process of upgrading the existing computer.</span></span> <span data-ttu-id="46e4c-111">Par exemple, vous pouvez transformer un ordinateur 4 processeurs BizTalk Server en un ordinateur 8 processeurs.</span><span class="sxs-lookup"><span data-stu-id="46e4c-111">For example, you can upgrade a BizTalk Server computer from a 4 processor machine to an 8 processor.</span></span>  
  
 <span data-ttu-id="46e4c-112">Un système BizTalk Server possède deux niveaux : le niveau de BizTalk Server et le niveau de SQL Server, qui contient vos bases de données MessageBox.</span><span class="sxs-lookup"><span data-stu-id="46e4c-112">A BizTalk Server system has two tiers: the BizTalk Server tier and the SQL Server tier, which contains your MessageBox databases.</span></span> <span data-ttu-id="46e4c-113">Dans n'importe quel scénario, vous pouvez procéder à l'évolution verticale ou horizontale de chaque niveau.</span><span class="sxs-lookup"><span data-stu-id="46e4c-113">In any scenario, you can scale out or scale up each tier.</span></span> <span data-ttu-id="46e4c-114">Autrement dit, vous pouvez procéder à l'évolution horizontale ou verticale de BizTalk Server et de la base de données MessageBox.</span><span class="sxs-lookup"><span data-stu-id="46e4c-114">That is, you can scale-out BizTalk Server and the MessageBox database, or scale up both of them.</span></span>  
  
 <span data-ttu-id="46e4c-115">Dans de nombreux cas, le niveau BizTalk commence par devenir un engorgement ; vous cherchez alors à en améliorer les performances en procédant à son évolution horizontale. Pourtant, à un certain point, en fonction de la complexité de votre système et du matériel utilisé, vous ne pouvez plus procéder à l'évolution horizontale du niveau BizTalk ; le niveau SQL Server devient alors l'engorgement.</span><span class="sxs-lookup"><span data-stu-id="46e4c-115">In most cases, the BizTalk tier becomes a bottleneck first, and you start improving performance by scaling it out. But, at some point, depending on complexity of your system and the hardware you use, you can’t scale out the BizTalk tier anymore and the SQL Server tier becomes the bottleneck.</span></span> <span data-ttu-id="46e4c-116">Vous procédez alors à l'évolution verticale du niveau SQL Server, puis à son évolution horizontale en lui ajoutant d'autres bases de données MessageBox.</span><span class="sxs-lookup"><span data-stu-id="46e4c-116">Then, you scale up the SQL Server tier, and next scale it out by adding more MessageBox databases.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="46e4c-117">Une nouvelle base de données MessageBox ne signifie pas nécessairement ici un autre serveur.</span><span class="sxs-lookup"><span data-stu-id="46e4c-117">A new MessageBox database does not necessarily mean another server here.</span></span> <span data-ttu-id="46e4c-118">Un même serveur SQL Server peut posséder plusieurs bases de données MessageBox.</span><span class="sxs-lookup"><span data-stu-id="46e4c-118">A single SQL server can have multiple MessageBox databases.</span></span> <span data-ttu-id="46e4c-119">De même, plusieurs bases de données MessageBox engendrent des coûts DTC et un tronçon réseau si elles se trouvent sur des ordinateurs différents.</span><span class="sxs-lookup"><span data-stu-id="46e4c-119">Also, multiple MessageBox databases incur DTC cost and network hop if the databases are on different computers.</span></span>  
  
 <span data-ttu-id="46e4c-120">En théorie, vous pouvez faire évoluer horizontalement le niveau SQL Server indéfiniment tant que la base de données principale MessageBox n'est pas saturée.</span><span class="sxs-lookup"><span data-stu-id="46e4c-120">In theory, the SQL Server tier can scale out indefinitely as long as the master MessageBox database is not saturated.</span></span>  
  
 <span data-ttu-id="46e4c-121">Les rubriques de cette section décrivent ces modèles d'évolution de façon plus détaillée.</span><span class="sxs-lookup"><span data-stu-id="46e4c-121">The topics in this section describe these scaling patterns in more detail.</span></span> <span data-ttu-id="46e4c-122">Elles expliquent également comment adapter chaque modèle et déterminer à partir de quel moment vous ne pouvez plus utiliser un modèle pour faire évoluer votre système.</span><span class="sxs-lookup"><span data-stu-id="46e4c-122">They also explain how to scale each pattern and how to determine when you can no longer use that pattern to scale your system.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="46e4c-123">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="46e4c-123">In This Section</span></span>  
  
-   [<span data-ttu-id="46e4c-124">Quelle est l’évolutivité ?</span><span class="sxs-lookup"><span data-stu-id="46e4c-124">What Is Scalability?</span></span>](../core/what-is-scalability.md)  
  
-   [<span data-ttu-id="46e4c-125">Évolution horizontale du niveau de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="46e4c-125">Scaling Out the BizTalk Server Tier</span></span>](../core/scaling-out-the-biztalk-server-tier.md)  
  
-   [<span data-ttu-id="46e4c-126">Mise à l’échelle verticale du niveau de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="46e4c-126">Scaling Up the BizTalk Server Tier</span></span>](../core/scaling-up-the-biztalk-server-tier.md)  
  
-   [<span data-ttu-id="46e4c-127">Montée en puissance parallèle du niveau SQL Server</span><span class="sxs-lookup"><span data-stu-id="46e4c-127">Scaling Out the SQL Server Tier</span></span>](../core/scaling-out-the-sql-server-tier.md)  
  
-   [<span data-ttu-id="46e4c-128">L’évolution verticale du niveau SQL Server</span><span class="sxs-lookup"><span data-stu-id="46e4c-128">Scaling Up the SQL Server Tier</span></span>](../core/scaling-up-the-sql-server-tier.md)  
  
## <a name="see-also"></a><span data-ttu-id="46e4c-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="46e4c-129">See Also</span></span>  
 <span data-ttu-id="46e4c-130">[Mise à l’échelle des hôtes de réception](../core/scaled-out-receiving-hosts.md) </span><span class="sxs-lookup"><span data-stu-id="46e4c-130">[Scaled-Out Receiving Hosts](../core/scaled-out-receiving-hosts.md) </span></span>  
 <span data-ttu-id="46e4c-131">[Mise à l’échelle des hôtes de traitement](../core/scaled-out-processing-hosts.md) </span><span class="sxs-lookup"><span data-stu-id="46e4c-131">[Scaled-Out Processing Hosts](../core/scaled-out-processing-hosts.md) </span></span>  
 <span data-ttu-id="46e4c-132">[Mise à l’échelle des hôtes d’envoi](../core/scaled-out-sending-hosts.md) </span><span class="sxs-lookup"><span data-stu-id="46e4c-132">[Scaled-Out Sending Hosts](../core/scaled-out-sending-hosts.md) </span></span>  
 <span data-ttu-id="46e4c-133">[À l’aide de Cluster Windows Server pour fournir une haute disponibilité pour BizTalk Server Hosts2](../core/use-windows-cluster-to-provide-high-availability-for-biztalk-hosts.md) </span><span class="sxs-lookup"><span data-stu-id="46e4c-133">[Using Windows Server Cluster to Provide High Availability for BizTalk Server Hosts2](../core/use-windows-cluster-to-provide-high-availability-for-biztalk-hosts.md) </span></span>  
 <span data-ttu-id="46e4c-134">[Bases de données à grande échelle](../core/scaled-out-databases.md) </span><span class="sxs-lookup"><span data-stu-id="46e4c-134">[Scaled-Out Databases](../core/scaled-out-databases.md) </span></span>  
 [<span data-ttu-id="46e4c-135">Mise en cluster les bases de données BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="46e4c-135">Clustering the BizTalk Server Databases</span></span>](../core/clustering-the-biztalk-server-databases1.md)