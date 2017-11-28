---
title: "Considérations relatives aux performances pour la publication d’événements BAM | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- performance, BAM
- publishing, BAM
- BAM, publishing
- events, tracking [BAM]
- BAM, event tracking
- BAM, performance
ms.assetid: 5a99e61a-a3d9-47fd-a933-2297f79817a5
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ebab873c94c0ae17abf9938883662ca8777cef36
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="performance-considerations-for-bam-event-publishing"></a><span data-ttu-id="b1ecd-102">Considérations de performances pour la publication d'événements BAM</span><span class="sxs-lookup"><span data-stu-id="b1ecd-102">Performance Considerations for BAM Event Publishing</span></span>
<span data-ttu-id="b1ecd-103">Le composant d'analyse BAM prend en charge deux formes de publication d'événements commerciaux :</span><span class="sxs-lookup"><span data-stu-id="b1ecd-103">BAM supports two forms of business event publishing:</span></span>  
  
-   <span data-ttu-id="b1ecd-104">Synchrone</span><span class="sxs-lookup"><span data-stu-id="b1ecd-104">Synchronous</span></span>  
  
-   <span data-ttu-id="b1ecd-105">Asynchrone</span><span class="sxs-lookup"><span data-stu-id="b1ecd-105">Asynchronous</span></span>  
  
 <span data-ttu-id="b1ecd-106">Le diagramme suivant illustre ces deux modèles :</span><span class="sxs-lookup"><span data-stu-id="b1ecd-106">The following diagram illustrates the two models.</span></span>  
  
 ![](../core/media/bam-topologies.gif "bam_topologies")  
<span data-ttu-id="b1ecd-107">Topologies BAM</span><span class="sxs-lookup"><span data-stu-id="b1ecd-107">BAM Topologies</span></span>  
  
 <span data-ttu-id="b1ecd-108">L'approche synchrone est beaucoup plus simple pour la gestion et plus facile à utiliser à partir du code. L'approche asynchrone permet, quant à elle, des performances accrues.</span><span class="sxs-lookup"><span data-stu-id="b1ecd-108">The synchronous approach is much simpler for management and using from code, while the asynchronous approach allows for better performance.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b1ecd-109">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="b1ecd-109">In This Section</span></span>  
  
-   [<span data-ttu-id="b1ecd-110">Suivi des événements commerciaux synchrone</span><span class="sxs-lookup"><span data-stu-id="b1ecd-110">Synchronous Business Event Tracking</span></span>](../core/synchronous-business-event-tracking.md)  
  
-   [<span data-ttu-id="b1ecd-111">Suivi des événements commerciaux asynchrone</span><span class="sxs-lookup"><span data-stu-id="b1ecd-111">Asynchronous Business Event Tracking</span></span>](../core/asynchronous-business-event-tracking.md)