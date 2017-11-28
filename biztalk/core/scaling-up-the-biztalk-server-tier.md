---
title: "Mise à l’échelle verticale du niveau de BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- examples, scaling
- scaling, examples
- scaling, scaling up
ms.assetid: 9002006a-f301-4e15-94b9-6caffd7c527c
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d55176072cd33e20dd1024bf2d9d1c39bca4567a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="scaling-up-the-biztalk-server-tier"></a><span data-ttu-id="cc50c-102">Montée en puissance par unité du niveau BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="cc50c-102">Scaling Up the BizTalk Server Tier</span></span>
<span data-ttu-id="cc50c-103">Pour faire évoluer verticalement le niveau BizTalk, vous devez mettre à niveau l'unité centrale, la mémoire, les E/S et d'autres ressources.</span><span class="sxs-lookup"><span data-stu-id="cc50c-103">To scale up the BizTalk tier, you upgrade the CPU, memory, IO and other resources.</span></span> <span data-ttu-id="cc50c-104">L'exemple de la figure suivante montre comment procéder depuis un ordinateur biprocesseur vers un ordinateur quadriprocesseur.</span><span class="sxs-lookup"><span data-stu-id="cc50c-104">The following figure shows an example of how you might scale up the BizTalk tier from a two processor computer to a four processor computer.</span></span>  
  
 <span data-ttu-id="cc50c-105">![Échelle &#45; haut BTS](../core/media/scaleupbts.gif "ScaleUpBTS")</span><span class="sxs-lookup"><span data-stu-id="cc50c-105">![Scale&#45;up BTS](../core/media/scaleupbts.gif "ScaleUpBTS")</span></span>  
  
 <span data-ttu-id="cc50c-106">Les scénarios d'évolution verticale du niveau BizTalk sont similaires à ceux utilisés pour l'évolution horizontale :</span><span class="sxs-lookup"><span data-stu-id="cc50c-106">The scenarios for scaling up your BizTalk tier are similar to when you choose to scale out:</span></span>  
  
-   <span data-ttu-id="cc50c-107">BizTalk Server devient un goulot d'étranglement</span><span class="sxs-lookup"><span data-stu-id="cc50c-107">BizTalk Server becomes a bottleneck.</span></span> <span data-ttu-id="cc50c-108">qui peut avoir pour origine un des problèmes suivants :</span><span class="sxs-lookup"><span data-stu-id="cc50c-108">The bottleneck itself may be caused by one of the following problems:</span></span>  
  
-   <span data-ttu-id="cc50c-109">UC : si le scénario utilise des pipelines, des mappages ou des orchestrations qui sollicitent beaucoup l'UC, les serveurs BizTalk Server n'auront pas de marge au niveau de l'UC.</span><span class="sxs-lookup"><span data-stu-id="cc50c-109">CPU: If the scenario uses CPU intensive pipelines, maps, or orchestrations, the BizTalk servers will not have any extra CPU headroom.</span></span>  
  
-   <span data-ttu-id="cc50c-110">Mémoire et E/S : si les ordinateurs existants ont atteint leur limite maximale concernant la mémoire et les E/S, et que l'ordinateur doit être mis à niveau.</span><span class="sxs-lookup"><span data-stu-id="cc50c-110">Memory and I/O: If the existing computers have reached their maximum limit on memory and IO, and the computer needs to be upgraded.</span></span>  
  
-   <span data-ttu-id="cc50c-111">Si l'évolution horizontale est trop onéreuse.</span><span class="sxs-lookup"><span data-stu-id="cc50c-111">Scaling out is too expensive.</span></span>  
  
-   <span data-ttu-id="cc50c-112">Si l'évolution horizontale ne résorbe pas le goulot d'étranglement.</span><span class="sxs-lookup"><span data-stu-id="cc50c-112">If scale-out does not address the bottleneck.</span></span> <span data-ttu-id="cc50c-113">Par exemple, elle n'a pas d'effet sur les goulots d'étranglement suivants :</span><span class="sxs-lookup"><span data-stu-id="cc50c-113">For example, scaling out does not address the following bottlenecks:</span></span>  
  
    -   <span data-ttu-id="cc50c-114">transformations de messages volumineux ;</span><span class="sxs-lookup"><span data-stu-id="cc50c-114">Large Message Transforms</span></span>  
  
    -   <span data-ttu-id="cc50c-115">grand nombre de messages par échange ;</span><span class="sxs-lookup"><span data-stu-id="cc50c-115">Large number of messages per interchange</span></span>  
  
    -   <span data-ttu-id="cc50c-116">mémoire très sollicitée par certains composants BTS comme les pipelines ou les adaptateurs ;</span><span class="sxs-lookup"><span data-stu-id="cc50c-116">High memory utilization by some of BTS components, such as pipelines or adapters</span></span>  
  
    -   <span data-ttu-id="cc50c-117">transport, comme EDI.</span><span class="sxs-lookup"><span data-stu-id="cc50c-117">A transport, such as EDI</span></span>  
  
## <a name="when-you-cant-scale-up-the-biztalk-tier"></a><span data-ttu-id="cc50c-118">Cas dans lesquels l'évolution verticale du niveau BizTalk est impossible</span><span class="sxs-lookup"><span data-stu-id="cc50c-118">When You Can’t Scale Up the BizTalk Tier</span></span>  
  
-   <span data-ttu-id="cc50c-119">La base de données MessageBox est le goulot d'étranglement.</span><span class="sxs-lookup"><span data-stu-id="cc50c-119">The MessageBox database is the bottleneck.</span></span>  
  
-   <span data-ttu-id="cc50c-120">Un adaptateur devient le goulot d'étranglement.</span><span class="sxs-lookup"><span data-stu-id="cc50c-120">An adapter becomes the bottleneck.</span></span> <span data-ttu-id="cc50c-121">Par exemple, si vous utilisez un adaptateur, une fois que vous augmentez le nombre de récepteurs BizTalk, les conflits de verrouillage peut augmenter sur l’application de serveur principal où l’adaptateur BizTalk est extrayant des données à partir de.</span><span class="sxs-lookup"><span data-stu-id="cc50c-121">For example, if you are using an adapter, after you increase the number of BizTalk receivers, lock contention might increase on the backend application where the BizTalk adapter is pulling data from.</span></span> <span data-ttu-id="cc50c-122">Cela limite vos possibilités d'évolution verticale pour cet adaptateur.</span><span class="sxs-lookup"><span data-stu-id="cc50c-122">This limits your ability to scale up the adapter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc50c-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cc50c-123">See Also</span></span>  
 <span data-ttu-id="cc50c-124">[Évolution horizontale du niveau de BizTalk Server](../core/scaling-out-the-biztalk-server-tier.md) </span><span class="sxs-lookup"><span data-stu-id="cc50c-124">[Scaling Out the BizTalk Server Tier](../core/scaling-out-the-biztalk-server-tier.md) </span></span>  
 <span data-ttu-id="cc50c-125">[L’évolution verticale du niveau SQL Server](../core/scaling-up-the-sql-server-tier.md) </span><span class="sxs-lookup"><span data-stu-id="cc50c-125">[Scaling Up the SQL Server Tier](../core/scaling-up-the-sql-server-tier.md) </span></span>  
 <span data-ttu-id="cc50c-126">[Montée en puissance parallèle du niveau SQL Server](../core/scaling-out-the-sql-server-tier.md) </span><span class="sxs-lookup"><span data-stu-id="cc50c-126">[Scaling Out the SQL Server Tier](../core/scaling-out-the-sql-server-tier.md) </span></span>  
 <span data-ttu-id="cc50c-127">[Mise à l’échelle des hôtes de réception](../core/scaled-out-receiving-hosts.md) </span><span class="sxs-lookup"><span data-stu-id="cc50c-127">[Scaled-Out Receiving Hosts](../core/scaled-out-receiving-hosts.md) </span></span>  
 <span data-ttu-id="cc50c-128">[Mise à l’échelle des hôtes de traitement](../core/scaled-out-processing-hosts.md) </span><span class="sxs-lookup"><span data-stu-id="cc50c-128">[Scaled-Out Processing Hosts](../core/scaled-out-processing-hosts.md) </span></span>  
 <span data-ttu-id="cc50c-129">[Mise à l’échelle des hôtes d’envoi](../core/scaled-out-sending-hosts.md) </span><span class="sxs-lookup"><span data-stu-id="cc50c-129">[Scaled-Out Sending Hosts](../core/scaled-out-sending-hosts.md) </span></span>  
 <span data-ttu-id="cc50c-130">[À l’aide de Cluster Windows Server pour fournir une haute disponibilité pour BizTalk Server Hosts2](../core/use-windows-cluster-to-provide-high-availability-for-biztalk-hosts.md) </span><span class="sxs-lookup"><span data-stu-id="cc50c-130">[Using Windows Server Cluster to Provide High Availability for BizTalk Server Hosts2](../core/use-windows-cluster-to-provide-high-availability-for-biztalk-hosts.md) </span></span>  
 <span data-ttu-id="cc50c-131">[Bases de données à grande échelle](../core/scaled-out-databases.md) </span><span class="sxs-lookup"><span data-stu-id="cc50c-131">[Scaled-Out Databases](../core/scaled-out-databases.md) </span></span>  
 [<span data-ttu-id="cc50c-132">Mise en cluster les bases de données BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="cc50c-132">Clustering the BizTalk Server Databases</span></span>](../core/clustering-the-biztalk-server-databases1.md)