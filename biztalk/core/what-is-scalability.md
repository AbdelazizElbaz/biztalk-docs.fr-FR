---
title: Qu'est-ce que l'évolutivité ? | Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- scaling, scalability
ms.assetid: ac6acefd-864a-4f22-a136-a1951fe71e96
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8a6208319fb8c195558101433cd1668ab0e0f064
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="what-is-scalability"></a><span data-ttu-id="ee2f6-103">Qu'est-ce que l'évolutivité ?</span><span class="sxs-lookup"><span data-stu-id="ee2f6-103">What Is Scalability?</span></span>
<span data-ttu-id="ee2f6-104">L'évolutivité est la capacité d'un système à se développer en fonction des besoins d'une entreprise.</span><span class="sxs-lookup"><span data-stu-id="ee2f6-104">Scalability is the ability of a system to expand to meet your business needs.</span></span> <span data-ttu-id="ee2f6-105">Le but est de pouvoir ajouter du matériel supplémentaire ou de mettre à niveau le matériel existant sans qu'il soit nécessaire d'effectuer des modifications importantes au niveau de l'application.</span><span class="sxs-lookup"><span data-stu-id="ee2f6-105">You scale a system by adding extra hardware or by upgrading the existing hardware without changing much of the application.</span></span> <span data-ttu-id="ee2f6-106">Dans le contexte d'un système BizTalk Server, l'évolutivité fait référence à la capacité de BizTalk à s'adapter à l'augmentation de vos exigences en termes de débit et à répondre à votre besoin de réduire les temps d'attente.</span><span class="sxs-lookup"><span data-stu-id="ee2f6-106">In the context of a BizTalk Server system, scalability refers to the ability of BizTalk to scale as your throughput needs increase, and if you need to reduce latency times.</span></span>  
  
 <span data-ttu-id="ee2f6-107">Après l'optimisation et la personnalisation de différents composants de BizTalk, des engorgements au niveau des ordinateurs BizTalk ou de la base de données MessageBox restent possibles.</span><span class="sxs-lookup"><span data-stu-id="ee2f6-107">After you optimize and tune various components of BizTalk, you might still encounter bottlenecks on BizTalk computers or on the MessageBox database.</span></span> <span data-ttu-id="ee2f6-108">Dans les environnements BizTalk, les engorgements sont généralement liés à l'UC, à la mémoire, aux E/S et aux conflits de verrouillage.</span><span class="sxs-lookup"><span data-stu-id="ee2f6-108">The types of bottlenecks that usually occur in BizTalk environments are CPU, memory, IO and lock contention bottlenecks.</span></span> <span data-ttu-id="ee2f6-109">Lorsque des engorgements commencent à se produire, vous devez soit mettre à niveau le matériel, soit ajouter de nouveaux équipements à la topologie existante.</span><span class="sxs-lookup"><span data-stu-id="ee2f6-109">When you start to encounter bottlenecks, you may need to either upgrade the hardware or add new hardware into the existing topology.</span></span> <span data-ttu-id="ee2f6-110">Par chance, l'architecture BizTalk Server facilite considérablement ces opérations. Vous pouvez, par exemple, ajouter plusieurs ordinateurs BizTalk Server au groupe et également ajouter des bases de données MessageBox supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="ee2f6-110">Fortunately, BizTalk Server architecture enables you to easily scale-up and scale-out. For example, you can add multiple BizTalk Server computers into the group and also add extra MessageBox databases.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee2f6-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ee2f6-111">See Also</span></span>  
 <span data-ttu-id="ee2f6-112">[Évolution horizontale du niveau de BizTalk Server](../core/scaling-out-the-biztalk-server-tier.md) </span><span class="sxs-lookup"><span data-stu-id="ee2f6-112">[Scaling Out the BizTalk Server Tier](../core/scaling-out-the-biztalk-server-tier.md) </span></span>  
 <span data-ttu-id="ee2f6-113">[Montée en puissance parallèle du niveau SQL Server](../core/scaling-out-the-sql-server-tier.md) </span><span class="sxs-lookup"><span data-stu-id="ee2f6-113">[Scaling Out the SQL Server Tier](../core/scaling-out-the-sql-server-tier.md) </span></span>  
 <span data-ttu-id="ee2f6-114">[Mise à l’échelle verticale du niveau de BizTalk Server](../core/scaling-up-the-biztalk-server-tier.md) </span><span class="sxs-lookup"><span data-stu-id="ee2f6-114">[Scaling Up the BizTalk Server Tier](../core/scaling-up-the-biztalk-server-tier.md) </span></span>  
 <span data-ttu-id="ee2f6-115">[L’évolution verticale du niveau SQL Server](../core/scaling-up-the-sql-server-tier.md) </span><span class="sxs-lookup"><span data-stu-id="ee2f6-115">[Scaling Up the SQL Server Tier](../core/scaling-up-the-sql-server-tier.md) </span></span>  
 <span data-ttu-id="ee2f6-116">[Mise à l’échelle des hôtes de réception](../core/scaled-out-receiving-hosts.md) </span><span class="sxs-lookup"><span data-stu-id="ee2f6-116">[Scaled-Out Receiving Hosts](../core/scaled-out-receiving-hosts.md) </span></span>  
 <span data-ttu-id="ee2f6-117">[Mise à l’échelle des hôtes de traitement](../core/scaled-out-processing-hosts.md) </span><span class="sxs-lookup"><span data-stu-id="ee2f6-117">[Scaled-Out Processing Hosts](../core/scaled-out-processing-hosts.md) </span></span>  
 <span data-ttu-id="ee2f6-118">[Mise à l’échelle des hôtes d’envoi](../core/scaled-out-sending-hosts.md) </span><span class="sxs-lookup"><span data-stu-id="ee2f6-118">[Scaled-Out Sending Hosts](../core/scaled-out-sending-hosts.md) </span></span>  
 <span data-ttu-id="ee2f6-119">[À l’aide de Cluster Windows Server pour fournir une haute disponibilité pour BizTalk Server Hosts2](../core/use-windows-cluster-to-provide-high-availability-for-biztalk-hosts.md) </span><span class="sxs-lookup"><span data-stu-id="ee2f6-119">[Using Windows Server Cluster to Provide High Availability for BizTalk Server Hosts2](../core/use-windows-cluster-to-provide-high-availability-for-biztalk-hosts.md) </span></span>  
 <span data-ttu-id="ee2f6-120">[Bases de données à grande échelle](../core/scaled-out-databases.md) </span><span class="sxs-lookup"><span data-stu-id="ee2f6-120">[Scaled-Out Databases](../core/scaled-out-databases.md) </span></span>  
 [<span data-ttu-id="ee2f6-121">Mise en cluster les bases de données BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="ee2f6-121">Clustering the BizTalk Server Databases</span></span>](../core/clustering-the-biztalk-server-databases1.md)