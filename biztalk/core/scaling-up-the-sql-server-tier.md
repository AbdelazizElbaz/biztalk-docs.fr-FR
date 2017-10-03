---
title: "L’évolution verticale du niveau SQL Server | Documents Microsoft"
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
- SQL Server, scaling
- scaling, scaling up
- scaling, strategies
ms.assetid: 4352c4af-6861-43d9-b433-9ca25668b439
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6c654c4a3b1bba166ae8a49918f6ef31827cf041
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="scaling-up-the-sql-server-tier"></a><span data-ttu-id="a5a00-102">Évolution verticale du niveau serveur SQL Server</span><span class="sxs-lookup"><span data-stu-id="a5a00-102">Scaling Up the SQL Server Tier</span></span>
<span data-ttu-id="a5a00-103">Dans ce modèle, la base de données SQL MessageBox existante est mise à niveau pour évoluer en fonction des exigences en matière de débit et de latence.</span><span class="sxs-lookup"><span data-stu-id="a5a00-103">In this pattern, the existing SQL MessageBox database is upgraded to scale according to the requirements in throughput or latency.</span></span>  
  
 <span data-ttu-id="a5a00-104">La figure suivante montre un scénario dans lequel la base de données principale MessageBox passe d'un serveur à quatre processeurs à un serveur à huit processeurs.</span><span class="sxs-lookup"><span data-stu-id="a5a00-104">The following figure shows a scenario where the master MessageBox database is upgraded from quad processor server to 8 processor server.</span></span>  
  
 <span data-ttu-id="a5a00-105">![Échelle &#45; haut MSGBOX](../core/media/scaleupmsgbox2.gif "ScaleUpMsgBox2")</span><span class="sxs-lookup"><span data-stu-id="a5a00-105">![Scale&#45;up MSGBOX](../core/media/scaleupmsgbox2.gif "ScaleUpMsgBox2")</span></span>  
  
## <a name="when-to-scale-up-the-sql-tier"></a><span data-ttu-id="a5a00-106">Quand faut-il effectuer une évolution verticale du niveau SQL ?</span><span class="sxs-lookup"><span data-stu-id="a5a00-106">When to Scale-up the SQL Tier</span></span>  
  
-   <span data-ttu-id="a5a00-107">Lorsque la base de données principale MessageBox peut évoluer verticalement.</span><span class="sxs-lookup"><span data-stu-id="a5a00-107">When you can scale up the master MessageBox database.</span></span>  
  
-   <span data-ttu-id="a5a00-108">Lorsque la base de données principale MessageBox est à l'origine d'engorgements.</span><span class="sxs-lookup"><span data-stu-id="a5a00-108">When the master MessageBox database becomes the bottleneck.</span></span> <span data-ttu-id="a5a00-109">Ces engorgements peuvent être notamment :</span><span class="sxs-lookup"><span data-stu-id="a5a00-109">Those bottlenecks can be:</span></span>  
  
    -   <span data-ttu-id="a5a00-110">**Processeur** en cas de scénarios d’orchestration très coûteux et complexes, boîte de Message consomme des ressources du processeur élevées.</span><span class="sxs-lookup"><span data-stu-id="a5a00-110">**CPU** In case of very expensive and complex orchestration scenarios, Message box consumes heavy CPU resources.</span></span> <span data-ttu-id="a5a00-111">Faire évoluer le serveur SQL verticalement en ajoutant des UC devrait faire évoluer le scénario.</span><span class="sxs-lookup"><span data-stu-id="a5a00-111">Scaling-up the SQL server by adding more CPUs should scale the scenario.</span></span>  
  
    -   <span data-ttu-id="a5a00-112">**Mémoire ou e/s** mémoire ou e/s peut être goulot d’étranglement et peuvent être mis à niveau.</span><span class="sxs-lookup"><span data-stu-id="a5a00-112">**Memory or I/O** Memory or I/O can be bottleneck and can be upgraded.</span></span>  
  
-   <span data-ttu-id="a5a00-113">Lorsque l'évolution verticale est moins chère que l'évolution horizontale, l'évolution verticale peut résoudre ces goulots d'étranglement.</span><span class="sxs-lookup"><span data-stu-id="a5a00-113">When scaling-up is cheaper than scaling-out and scaling-up can address the bottleneck.</span></span> <span data-ttu-id="a5a00-114">Par exemple, si la base de données principale MessageBox présente un problème de conflit de verrouillage SQL, l'évolutivité verticale ne peut pas résoudre ce problème.</span><span class="sxs-lookup"><span data-stu-id="a5a00-114">For example, if the master MessageBox database has an issue with SQL lock contention, this issue cannot be solved by scaling-up.</span></span>  
  
## <a name="when-do-you-decide-sql-cannot-scale-up"></a><span data-ttu-id="a5a00-115">Quand décidez-vous que SQL ne peut pas faire l'objet d'une évolutivité verticale ?</span><span class="sxs-lookup"><span data-stu-id="a5a00-115">When do you decide SQL cannot scale-up?</span></span>  
 <span data-ttu-id="a5a00-116">L'évolutivité verticale ne peut pas résoudre les engorgements liés à un conflit de verrouillage se produisant sur le niveau SQL.</span><span class="sxs-lookup"><span data-stu-id="a5a00-116">Scale-up cannot address lock contention bottlenecks on the SQL tier.</span></span> <span data-ttu-id="a5a00-117">Si ce type d'engorgement se produit, l'évolutivité horizontale est une meilleure option que l'évolutivité verticale.</span><span class="sxs-lookup"><span data-stu-id="a5a00-117">If these kinds of bottlenecks are hit, scale-out is better option than scale-up.</span></span>  
  
## <a name="strategies-and-considerations-for-scaling-up-the-sql-tier"></a><span data-ttu-id="a5a00-118">Stratégies et considérations pour l'évolutivité verticale du niveau SQL</span><span class="sxs-lookup"><span data-stu-id="a5a00-118">Strategies and Considerations for Scaling Up the SQL Tier</span></span>  
  
-   <span data-ttu-id="a5a00-119">Faites évoluer verticalement la base de données principale MessageBox, puis horizontalement.</span><span class="sxs-lookup"><span data-stu-id="a5a00-119">Scale-up the master MessageBox database first and then scale-out.</span></span>  
  
-   <span data-ttu-id="a5a00-120">La base de données MessageBox maître sera finalement le goulot d’étranglement.</span><span class="sxs-lookup"><span data-stu-id="a5a00-120">The master MessageBox database will eventually be the bottleneck.</span></span> <span data-ttu-id="a5a00-121">Pour cette raison, elle devrait être plus rapide et plus conséquente (par exemple, un ordinateur Itanium 64 bits ou x64 à processeur double).</span><span class="sxs-lookup"><span data-stu-id="a5a00-121">So, the master MessageBox database should be faster and bigger (for example, an Itanium-based 64-bit or x64-based, dual core computer).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5a00-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a5a00-122">See Also</span></span>  
 <span data-ttu-id="a5a00-123">[Évolution horizontale du niveau de BizTalk Server](../core/scaling-out-the-biztalk-server-tier.md) </span><span class="sxs-lookup"><span data-stu-id="a5a00-123">[Scaling Out the BizTalk Server Tier](../core/scaling-out-the-biztalk-server-tier.md) </span></span>  
 <span data-ttu-id="a5a00-124">[Mise à l’échelle verticale du niveau de BizTalk Server](../core/scaling-up-the-biztalk-server-tier.md) </span><span class="sxs-lookup"><span data-stu-id="a5a00-124">[Scaling Up the BizTalk Server Tier](../core/scaling-up-the-biztalk-server-tier.md) </span></span>  
 <span data-ttu-id="a5a00-125">[Montée en puissance parallèle du niveau SQL Server](../core/scaling-out-the-sql-server-tier.md) </span><span class="sxs-lookup"><span data-stu-id="a5a00-125">[Scaling Out the SQL Server Tier](../core/scaling-out-the-sql-server-tier.md) </span></span>  
 <span data-ttu-id="a5a00-126">[Mise à l’échelle des hôtes de réception](../core/scaled-out-receiving-hosts.md) </span><span class="sxs-lookup"><span data-stu-id="a5a00-126">[Scaled-Out Receiving Hosts](../core/scaled-out-receiving-hosts.md) </span></span>  
 <span data-ttu-id="a5a00-127">[Mise à l’échelle des hôtes de traitement](../core/scaled-out-processing-hosts.md) </span><span class="sxs-lookup"><span data-stu-id="a5a00-127">[Scaled-Out Processing Hosts](../core/scaled-out-processing-hosts.md) </span></span>  
 <span data-ttu-id="a5a00-128">[Mise à l’échelle des hôtes d’envoi](../core/scaled-out-sending-hosts.md) </span><span class="sxs-lookup"><span data-stu-id="a5a00-128">[Scaled-Out Sending Hosts](../core/scaled-out-sending-hosts.md) </span></span>  
 <span data-ttu-id="a5a00-129">[À l’aide de Cluster Windows Server pour fournir une haute disponibilité pour BizTalk Server Hosts2](../core/use-windows-cluster-to-provide-high-availability-for-biztalk-hosts.md) </span><span class="sxs-lookup"><span data-stu-id="a5a00-129">[Using Windows Server Cluster to Provide High Availability for BizTalk Server Hosts2](../core/use-windows-cluster-to-provide-high-availability-for-biztalk-hosts.md) </span></span>  
 <span data-ttu-id="a5a00-130">[Bases de données à grande échelle](../core/scaled-out-databases.md) </span><span class="sxs-lookup"><span data-stu-id="a5a00-130">[Scaled-Out Databases](../core/scaled-out-databases.md) </span></span>  
 [<span data-ttu-id="a5a00-131">Mise en cluster les bases de données BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="a5a00-131">Clustering the BizTalk Server Databases</span></span>](../core/clustering-the-biztalk-server-databases1.md)