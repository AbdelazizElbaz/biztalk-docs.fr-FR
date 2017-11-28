---
title: "Interaction des Messages de la carte pour l’échange | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3b443b8a-4e56-47f1-8d91-5c807fd54ccc
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d19e10940e6a83c24e9397f0df94d0fc54e4da38
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="interact-adapter-messages-for-business-exchange"></a><span data-ttu-id="6f913-102">Interaction des Messages de la carte pour l’échange</span><span class="sxs-lookup"><span data-stu-id="6f913-102">InterAct Adapter Messages for Business Exchange</span></span>
<span data-ttu-id="6f913-103">Il existe quatre messages dans le cycle de bout en bout pour l’adaptateur InterAct.</span><span class="sxs-lookup"><span data-stu-id="6f913-103">There are four messages in the InterAct adapter end-to-end cycle.</span></span> <span data-ttu-id="6f913-104">Ces messages sont des primitives de SWIFTNet.</span><span class="sxs-lookup"><span data-stu-id="6f913-104">These messages are SWIFTNet primitives.</span></span> <span data-ttu-id="6f913-105">Le premier et le dernier message constituent les primitives du côté client, SwInt:ExchangeRequest et SwInt:ExchangeResponse.</span><span class="sxs-lookup"><span data-stu-id="6f913-105">The first and last messages comprise the client-side primitives, SwInt:ExchangeRequest and SwInt:ExchangeResponse.</span></span> <span data-ttu-id="6f913-106">Les deux messages central comprennent les primitives du côté serveur, SwInt:HandleRequest et SwInt:HandleResponse.</span><span class="sxs-lookup"><span data-stu-id="6f913-106">The middle two messages comprise the server-side primitives, SwInt:HandleRequest and SwInt:HandleResponse.</span></span>  
  
 <span data-ttu-id="6f913-107">À ce niveau de simplification, il existe six étapes dans le cycle de message de bout en bout :</span><span class="sxs-lookup"><span data-stu-id="6f913-107">At this level of simplification, there are six steps in the end-to-end message cycle:</span></span>  
  
1.  <span data-ttu-id="6f913-108">L’application cliente prépare le message de demande.</span><span class="sxs-lookup"><span data-stu-id="6f913-108">The client application prepares the request message.</span></span>  
  
2.  <span data-ttu-id="6f913-109">L’application cliente transmet le message de demande à SWIFTNet.</span><span class="sxs-lookup"><span data-stu-id="6f913-109">The client application passes the request message to SWIFTNet.</span></span>  
  
3.  <span data-ttu-id="6f913-110">SWIFTNet traite le message de demande et l’envoie à l’application serveur.</span><span class="sxs-lookup"><span data-stu-id="6f913-110">SWIFTNet processes the request message, and sends it to the server application.</span></span>  
  
4.  <span data-ttu-id="6f913-111">L’application serveur reçoit le message de demande à partir de SWIFTNet.</span><span class="sxs-lookup"><span data-stu-id="6f913-111">The server application receives the request message from SWIFTNet.</span></span>  
  
5.  <span data-ttu-id="6f913-112">L’application serveur prépare le message de réponse.</span><span class="sxs-lookup"><span data-stu-id="6f913-112">The server application prepares the response message.</span></span>  
  
6.  <span data-ttu-id="6f913-113">L’application serveur transmet le message de réponse à SWIFTNet.</span><span class="sxs-lookup"><span data-stu-id="6f913-113">The server application passes the response message to SWIFTNet.</span></span>  
  
7.  <span data-ttu-id="6f913-114">SWIFTNet traite le message de réponse et l’envoie à l’application cliente.</span><span class="sxs-lookup"><span data-stu-id="6f913-114">SWIFTNet processes the response message, and sends it to the client application.</span></span>  
  
8.  <span data-ttu-id="6f913-115">L’application cliente reçoit le message de réponse de SWIFTNet.</span><span class="sxs-lookup"><span data-stu-id="6f913-115">The client application receives the response message from SWIFTNet.</span></span>  
  
 <span data-ttu-id="6f913-116">La figure suivante illustre l’échange de messages InterAct.</span><span class="sxs-lookup"><span data-stu-id="6f913-116">The following figure shows the InterAct message exchange.</span></span>  
  
 <span data-ttu-id="6f913-117">![Échange de messages interAct](../../adapters-and-accelerators/fileact-interact/media/12fbebc6-5ab7-4d7f-9f94-4069b22161fa.gif "12fbebc6-5ab7-4d7f-9f94-4069b22161fa")</span><span class="sxs-lookup"><span data-stu-id="6f913-117">![InterAct message exchange](../../adapters-and-accelerators/fileact-interact/media/12fbebc6-5ab7-4d7f-9f94-4069b22161fa.gif "12fbebc6-5ab7-4d7f-9f94-4069b22161fa")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f913-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6f913-118">See Also</span></span>  
 <span data-ttu-id="6f913-119">[Interagir l’Architecture de l’adaptateur](../../adapters-and-accelerators/fileact-interact/interact-adapter-architecture.md) </span><span class="sxs-lookup"><span data-stu-id="6f913-119">[InterAct Adapter Architecture](../../adapters-and-accelerators/fileact-interact/interact-adapter-architecture.md) </span></span>  
 <span data-ttu-id="6f913-120">[Composants d’adaptateur interAct](../../adapters-and-accelerators/fileact-interact/interact-adapter-components.md) </span><span class="sxs-lookup"><span data-stu-id="6f913-120">[InterAct Adapter Components](../../adapters-and-accelerators/fileact-interact/interact-adapter-components.md) </span></span>  
 <span data-ttu-id="6f913-121">[Application cliente de l’adaptateur interAct](../../adapters-and-accelerators/fileact-interact/interact-adapter-client-application.md) </span><span class="sxs-lookup"><span data-stu-id="6f913-121">[InterAct Adapter Client Application](../../adapters-and-accelerators/fileact-interact/interact-adapter-client-application.md) </span></span>  
 <span data-ttu-id="6f913-122">[Application de serveur de l’adaptateur interAct](../../adapters-and-accelerators/fileact-interact/interact-adapter-server-application.md) </span><span class="sxs-lookup"><span data-stu-id="6f913-122">[InterAct Adapter Server Application](../../adapters-and-accelerators/fileact-interact/interact-adapter-server-application.md) </span></span>  
 <span data-ttu-id="6f913-123">[Interagir de magasin de l’adaptateur et le transfert](../../adapters-and-accelerators/fileact-interact/interact-adapter-store-and-forward.md) </span><span class="sxs-lookup"><span data-stu-id="6f913-123">[InterAct Adapter Store and Forward](../../adapters-and-accelerators/fileact-interact/interact-adapter-store-and-forward.md) </span></span>  
 <span data-ttu-id="6f913-124">[Interagir l’Architecture de sécurité de carte](../../adapters-and-accelerators/fileact-interact/interact-adapter-security-architecture.md) </span><span class="sxs-lookup"><span data-stu-id="6f913-124">[InterAct Adapter Security Architecture](../../adapters-and-accelerators/fileact-interact/interact-adapter-security-architecture.md) </span></span>  
 <span data-ttu-id="6f913-125">[Interagir remise fiable de bout en bout pour l’adaptateur](../../adapters-and-accelerators/fileact-interact/interact-adapter-end-to-end-reliable-delivery.md) </span><span class="sxs-lookup"><span data-stu-id="6f913-125">[InterAct Adapter End-to-End Reliable Delivery](../../adapters-and-accelerators/fileact-interact/interact-adapter-end-to-end-reliable-delivery.md) </span></span>  
 <span data-ttu-id="6f913-126">[Interagir l’état de la carte d’analyse](../../adapters-and-accelerators/fileact-interact/interact-adapter-status-monitoring.md) </span><span class="sxs-lookup"><span data-stu-id="6f913-126">[InterAct Adapter Status Monitoring](../../adapters-and-accelerators/fileact-interact/interact-adapter-status-monitoring.md) </span></span>  
 [<span data-ttu-id="6f913-127">Interagir carte de non-répudiation</span><span class="sxs-lookup"><span data-stu-id="6f913-127">InterAct Adapter Non-Repudiation</span></span>](../../adapters-and-accelerators/fileact-interact/interact-adapter-non-repudiation.md)