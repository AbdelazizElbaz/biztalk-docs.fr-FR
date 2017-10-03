---
title: "Interagir l’état de l’adaptateur analyse | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2bbc6a45-8d3a-444e-b760-aef0dfa7218a
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 32cf2f197508c0cd703a05780804c6bc880b5f32
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="interact-adapter-status-monitoring"></a><span data-ttu-id="995fb-102">Interagir l’état de la carte d’analyse</span><span class="sxs-lookup"><span data-stu-id="995fb-102">InterAct Adapter Status Monitoring</span></span>
<span data-ttu-id="995fb-103">Le lien SWIFTNet (SNL-C) conserve l’état local sur SWIFTNet magasin et vers l’avant (msng) sessions acquises sur ce SNL.</span><span class="sxs-lookup"><span data-stu-id="995fb-103">SWIFTNet Link (SNL-C) retains a local status about SWIFTNet store and forward (SnF) sessions acquired on that SNL.</span></span> <span data-ttu-id="995fb-104">Pour obtenir les informations sur la session, utilisez SwCall() avec la primitive suivante :</span><span class="sxs-lookup"><span data-stu-id="995fb-104">To get the information about the session, use SwCall() with the following primitive:</span></span>  
  
 <span data-ttu-id="995fb-105">![Obtention d’informations de session](../../adapters-and-accelerators/fileact-interact/media/b7feb4b4-de92-4bb9-bcfe-363a127d0ed2.gif "b7feb4b4-de92-4bb9-bcfe-363a127d0ed2")</span><span class="sxs-lookup"><span data-stu-id="995fb-105">![Getting session information](../../adapters-and-accelerators/fileact-interact/media/b7feb4b4-de92-4bb9-bcfe-363a127d0ed2.gif "b7feb4b4-de92-4bb9-bcfe-363a127d0ed2")</span></span>  
  
 <span data-ttu-id="995fb-106">Notez que vous ne sont pas requis pour fournir une AuthorizationContext.</span><span class="sxs-lookup"><span data-stu-id="995fb-106">Notice that you are not required to provide an AuthorizationContext.</span></span> <span data-ttu-id="995fb-107">Les informations présentées par le SNL local sont retournées, comme indiqué dans l’illustration suivante.</span><span class="sxs-lookup"><span data-stu-id="995fb-107">The information seen by the local SNL is returned, as shown in the following figure.</span></span>  
  
 <span data-ttu-id="995fb-108">![Informations d’état de session](../../adapters-and-accelerators/fileact-interact/media/afd46393-a11d-4b4a-a66b-eba5f049f306.gif "afd46393-a11d-4b4a-a66b-eba5f049f306")</span><span class="sxs-lookup"><span data-stu-id="995fb-108">![Session status information](../../adapters-and-accelerators/fileact-interact/media/afd46393-a11d-4b4a-a66b-eba5f049f306.gif "afd46393-a11d-4b4a-a66b-eba5f049f306")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="995fb-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="995fb-109">See Also</span></span>  
 <span data-ttu-id="995fb-110">[Interagir l’Architecture de l’adaptateur](../../adapters-and-accelerators/fileact-interact/interact-adapter-architecture.md) </span><span class="sxs-lookup"><span data-stu-id="995fb-110">[InterAct Adapter Architecture](../../adapters-and-accelerators/fileact-interact/interact-adapter-architecture.md) </span></span>  
 <span data-ttu-id="995fb-111">[Composants d’adaptateur interAct](../../adapters-and-accelerators/fileact-interact/interact-adapter-components.md) </span><span class="sxs-lookup"><span data-stu-id="995fb-111">[InterAct Adapter Components](../../adapters-and-accelerators/fileact-interact/interact-adapter-components.md) </span></span>  
 <span data-ttu-id="995fb-112">[Interaction des Messages de la carte pour l’échange](../../adapters-and-accelerators/fileact-interact/interact-adapter-messages-for-business-exchange.md) </span><span class="sxs-lookup"><span data-stu-id="995fb-112">[InterAct Adapter Messages for Business Exchange](../../adapters-and-accelerators/fileact-interact/interact-adapter-messages-for-business-exchange.md) </span></span>  
 <span data-ttu-id="995fb-113">[Application cliente de l’adaptateur interAct](../../adapters-and-accelerators/fileact-interact/interact-adapter-client-application.md) </span><span class="sxs-lookup"><span data-stu-id="995fb-113">[InterAct Adapter Client Application](../../adapters-and-accelerators/fileact-interact/interact-adapter-client-application.md) </span></span>  
 <span data-ttu-id="995fb-114">[Application de serveur de l’adaptateur interAct](../../adapters-and-accelerators/fileact-interact/interact-adapter-server-application.md) </span><span class="sxs-lookup"><span data-stu-id="995fb-114">[InterAct Adapter Server Application](../../adapters-and-accelerators/fileact-interact/interact-adapter-server-application.md) </span></span>  
 <span data-ttu-id="995fb-115">[Interagir de magasin de l’adaptateur et le transfert](../../adapters-and-accelerators/fileact-interact/interact-adapter-store-and-forward.md) </span><span class="sxs-lookup"><span data-stu-id="995fb-115">[InterAct Adapter Store and Forward](../../adapters-and-accelerators/fileact-interact/interact-adapter-store-and-forward.md) </span></span>  
 <span data-ttu-id="995fb-116">[Interagir l’Architecture de sécurité de carte](../../adapters-and-accelerators/fileact-interact/interact-adapter-security-architecture.md) </span><span class="sxs-lookup"><span data-stu-id="995fb-116">[InterAct Adapter Security Architecture](../../adapters-and-accelerators/fileact-interact/interact-adapter-security-architecture.md) </span></span>  
 <span data-ttu-id="995fb-117">[Interagir remise fiable de bout en bout pour l’adaptateur](../../adapters-and-accelerators/fileact-interact/interact-adapter-end-to-end-reliable-delivery.md) </span><span class="sxs-lookup"><span data-stu-id="995fb-117">[InterAct Adapter End-to-End Reliable Delivery](../../adapters-and-accelerators/fileact-interact/interact-adapter-end-to-end-reliable-delivery.md) </span></span>  
 [<span data-ttu-id="995fb-118">Interagir carte de non-répudiation</span><span class="sxs-lookup"><span data-stu-id="995fb-118">InterAct Adapter Non-Repudiation</span></span>](../../adapters-and-accelerators/fileact-interact/interact-adapter-non-repudiation.md)