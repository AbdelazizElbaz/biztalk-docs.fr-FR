---
title: "Le Service de mise à l’échelle de la Solution orientée services | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- scaling, service solutions
- service solution tutorial, scaling
ms.assetid: 6c22a68d-03e7-4174-b612-0e2246aa9413
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3026664d3a365630c93bf1c61d7cf635fdd9dc31
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="scaling-the-service-oriented-solution"></a><span data-ttu-id="a7d31-102">Le Service de mise à l’échelle de la Solution orientée services</span><span class="sxs-lookup"><span data-stu-id="a7d31-102">Scaling the Service Oriented Solution</span></span>
<span data-ttu-id="a7d31-103">Pour faire évoluer la solution de manière à ce qu'elle prenne en charge un débit plus élevé tout en conservant une faible latence pour les messages, vous devez utilisez la version Inline de la solution.</span><span class="sxs-lookup"><span data-stu-id="a7d31-103">To scale the solution to support higher throughput while maintaining low message latency requires you to use the inline version of the solution.</span></span> <span data-ttu-id="a7d31-104">Celle-ci contourne la base de données MessageBox lors de l'interaction avec les systèmes principaux.</span><span class="sxs-lookup"><span data-stu-id="a7d31-104">The inline solution bypasses the MessageBox database when interacting with the back-end systems.</span></span>  
  
 <span data-ttu-id="a7d31-105">Vous pouvez également ajouter des serveurs de traitement BizTalk Server destinés à exécuter les orchestrations.</span><span class="sxs-lookup"><span data-stu-id="a7d31-105">You can also add BizTalk Server processing servers to run orchestrations.</span></span> <span data-ttu-id="a7d31-106">Cela permet de réduire l'utilisation de chaque serveur et d'augmenter la rapidité du traitement des nouvelles demandes.</span><span class="sxs-lookup"><span data-stu-id="a7d31-106">This decreases the utilization of each server so that new requests can be processed quickly.</span></span> <span data-ttu-id="a7d31-107">Vous pouvez aussi faire évoluer le serveur MessageBox en augmentant sa capacité de traitement de manière à ce qu'il puisse répondre au débit de messages.</span><span class="sxs-lookup"><span data-stu-id="a7d31-107">You can also scale up the MessageBox server so that it has enough additional capacity to handle the message throughput.</span></span>  
  
 <span data-ttu-id="a7d31-108">Toutefois, la solution d'architecture orientée services ne tire pas profit d'avoir à disposition plusieurs bases de données MessageBox.</span><span class="sxs-lookup"><span data-stu-id="a7d31-108">However, the service oriented architecture solution does not benefit from having multiple MessageBox databases.</span></span> <span data-ttu-id="a7d31-109">En effet, cette situation exige des transactions DTC (Distributed Transaction Coordinator).</span><span class="sxs-lookup"><span data-stu-id="a7d31-109">Multiple MessageBoxes require distributed transaction coordinator (DTC) transactions.</span></span> <span data-ttu-id="a7d31-110">Les transactions augmentent la latence globale au niveau des messages.</span><span class="sxs-lookup"><span data-stu-id="a7d31-110">The transactions increase overall message latency.</span></span>  
  
 <span data-ttu-id="a7d31-111">Vous pouvez améliorer le temps de réponse en supprimant le composant de pipeline qui ajoute des informations d'en-tête MQSeries.</span><span class="sxs-lookup"><span data-stu-id="a7d31-111">You can decrease response time by eliminating the pipeline component that adds MQSeries header information.</span></span> <span data-ttu-id="a7d31-112">Pour plus d’informations, consultez [met en surbrillance de l’implémentation de la Solution orientée services](../core/implementation-highlights-of-the-service-oriented-solution.md).</span><span class="sxs-lookup"><span data-stu-id="a7d31-112">For more information, see [Implementation Highlights of the Service Oriented Solution](../core/implementation-highlights-of-the-service-oriented-solution.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7d31-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a7d31-113">See Also</span></span>  
 [<span data-ttu-id="a7d31-114">Développement d’un Service de la Solution orientée services</span><span class="sxs-lookup"><span data-stu-id="a7d31-114">Developing a Service Oriented Solution</span></span>](../core/developing-a-service-oriented-solution.md)