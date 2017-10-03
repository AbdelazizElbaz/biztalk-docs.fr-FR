---
title: "Composants d’adaptateur interAct | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: aad60b57-4cc8-44b9-98f5-e5a2ba3a41e2
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e909e49713377172d01540f4c8e660756d68ed72
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="interact-adapter-components"></a><span data-ttu-id="84d04-102">Composants d’adaptateur interAct</span><span class="sxs-lookup"><span data-stu-id="84d04-102">InterAct Adapter Components</span></span>
<span data-ttu-id="84d04-103">L’adaptateur InterAct a un client et un composant serveur.</span><span class="sxs-lookup"><span data-stu-id="84d04-103">The InterAct adapter has a client and a server component.</span></span> <span data-ttu-id="84d04-104">Notez qu’il peut y avoir une installation (minimale) A4SWIFT sur le même ordinateur en tant que la passerelle de Alliance SWIFT (trous) s’il exécute Windows Server.</span><span class="sxs-lookup"><span data-stu-id="84d04-104">Note that there may be an A4SWIFT (minimal) installation on the same computer as the SWIFT Alliance Gateway (SAG) if it is running Windows Server.</span></span> <span data-ttu-id="84d04-105">Notez également que le lien SWIFTNet (SNL) peut se trouver sur un ordinateur distinct dans les trous.</span><span class="sxs-lookup"><span data-stu-id="84d04-105">Also note that the SWIFTNet Link (SNL) may be on a separate computer from the SAG.</span></span> <span data-ttu-id="84d04-106">L’adaptateur d’API (interface) fournie par SWIFT de programmation d’applications à distance sont utilisée pour communiquer à partir d’A4SWIFT avec les trous, quel que soit l’emplacement des composants.</span><span class="sxs-lookup"><span data-stu-id="84d04-106">The remote application programming interface (API) host adapter provided by SWIFT is used to communicate from A4SWIFT to the SAG, regardless of the location of the components.</span></span>  
  
 <span data-ttu-id="84d04-107">La figure ci-dessous illustre l’emplacement où résident les composants comprenant la chaîne entière d’adaptateur et les communications liée à l’adaptateur InterAct.</span><span class="sxs-lookup"><span data-stu-id="84d04-107">The figure below shows where the components comprising the entire adapter and communications chain related to the InterAct adapter reside.</span></span>  
  
 <span data-ttu-id="84d04-108">![Composants interAct](../../adapters-and-accelerators/fileact-interact/media/cf257c5a-3668-4aff-bce9-7acc6eb672bd.gif "cf257c5a-3668-4aff-bce9-7acc6eb672bd")</span><span class="sxs-lookup"><span data-stu-id="84d04-108">![InterAct components](../../adapters-and-accelerators/fileact-interact/media/cf257c5a-3668-4aff-bce9-7acc6eb672bd.gif "cf257c5a-3668-4aff-bce9-7acc6eb672bd")</span></span>  
  
 <span data-ttu-id="84d04-109">Dans l’illustration suivante, l’application cliente utilise A4SWIFT et l’adaptateur InterAct.</span><span class="sxs-lookup"><span data-stu-id="84d04-109">In the following figure, the client application uses A4SWIFT and the InterAct adapter.</span></span> <span data-ttu-id="84d04-110">BizTalk Server est l’intergiciel (middleware), qui communique avec l’adaptateur hôte API à distance via TCP/IP.</span><span class="sxs-lookup"><span data-stu-id="84d04-110">BizTalk Server is the middleware, which communicates to the remote API host adapter over TCPIP.</span></span>  
  
 <span data-ttu-id="84d04-111">![Application cliente interAct](../../adapters-and-accelerators/fileact-interact/media/7aeada39-6264-498b-92e8-303eb0cf369b.gif "7aeada39-6264-498b-92e8-303eb0cf369b")</span><span class="sxs-lookup"><span data-stu-id="84d04-111">![InterAct client application](../../adapters-and-accelerators/fileact-interact/media/7aeada39-6264-498b-92e8-303eb0cf369b.gif "7aeada39-6264-498b-92e8-303eb0cf369b")</span></span>  
  
 <span data-ttu-id="84d04-112">Dans l’illustration suivante, l’application serveur utilise A4SWIFT et l’adaptateur InterAct.</span><span class="sxs-lookup"><span data-stu-id="84d04-112">In the following figure, the server application uses A4SWIFT and the InterAct adapter.</span></span> <span data-ttu-id="84d04-113">BizTalk Server est l’intergiciel (middleware), qui communique avec l’adaptateur hôte API à distance via TCP/IP.</span><span class="sxs-lookup"><span data-stu-id="84d04-113">BizTalk Server is the middleware, which communicates to the remote API host adapter over TCPIP.</span></span>  
  
 <span data-ttu-id="84d04-114">![Application serveur interAct](../../adapters-and-accelerators/fileact-interact/media/51cbae6a-41e9-4a50-9574-5e86bc04ddba.gif "51cbae6a-41e9-4a50-9574-5e86bc04ddba")</span><span class="sxs-lookup"><span data-stu-id="84d04-114">![InterAct server application](../../adapters-and-accelerators/fileact-interact/media/51cbae6a-41e9-4a50-9574-5e86bc04ddba.gif "51cbae6a-41e9-4a50-9574-5e86bc04ddba")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84d04-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="84d04-115">See Also</span></span>  
 <span data-ttu-id="84d04-116">[Interagir l’Architecture de l’adaptateur](../../adapters-and-accelerators/fileact-interact/interact-adapter-architecture.md) </span><span class="sxs-lookup"><span data-stu-id="84d04-116">[InterAct Adapter Architecture](../../adapters-and-accelerators/fileact-interact/interact-adapter-architecture.md) </span></span>  
 <span data-ttu-id="84d04-117">[Interaction des Messages de la carte pour l’échange](../../adapters-and-accelerators/fileact-interact/interact-adapter-messages-for-business-exchange.md) </span><span class="sxs-lookup"><span data-stu-id="84d04-117">[InterAct Adapter Messages for Business Exchange](../../adapters-and-accelerators/fileact-interact/interact-adapter-messages-for-business-exchange.md) </span></span>  
 <span data-ttu-id="84d04-118">[Application cliente de l’adaptateur interAct](../../adapters-and-accelerators/fileact-interact/interact-adapter-client-application.md) </span><span class="sxs-lookup"><span data-stu-id="84d04-118">[InterAct Adapter Client Application](../../adapters-and-accelerators/fileact-interact/interact-adapter-client-application.md) </span></span>  
 <span data-ttu-id="84d04-119">[Application de serveur de l’adaptateur interAct](../../adapters-and-accelerators/fileact-interact/interact-adapter-server-application.md) </span><span class="sxs-lookup"><span data-stu-id="84d04-119">[InterAct Adapter Server Application](../../adapters-and-accelerators/fileact-interact/interact-adapter-server-application.md) </span></span>  
 <span data-ttu-id="84d04-120">[Interagir de magasin de l’adaptateur et le transfert](../../adapters-and-accelerators/fileact-interact/interact-adapter-store-and-forward.md) </span><span class="sxs-lookup"><span data-stu-id="84d04-120">[InterAct Adapter Store and Forward](../../adapters-and-accelerators/fileact-interact/interact-adapter-store-and-forward.md) </span></span>  
 <span data-ttu-id="84d04-121">[Interagir l’Architecture de sécurité de carte](../../adapters-and-accelerators/fileact-interact/interact-adapter-security-architecture.md) </span><span class="sxs-lookup"><span data-stu-id="84d04-121">[InterAct Adapter Security Architecture](../../adapters-and-accelerators/fileact-interact/interact-adapter-security-architecture.md) </span></span>  
 <span data-ttu-id="84d04-122">[Interagir remise fiable de bout en bout pour l’adaptateur](../../adapters-and-accelerators/fileact-interact/interact-adapter-end-to-end-reliable-delivery.md) </span><span class="sxs-lookup"><span data-stu-id="84d04-122">[InterAct Adapter End-to-End Reliable Delivery](../../adapters-and-accelerators/fileact-interact/interact-adapter-end-to-end-reliable-delivery.md) </span></span>  
 <span data-ttu-id="84d04-123">[Interagir l’état de la carte d’analyse](../../adapters-and-accelerators/fileact-interact/interact-adapter-status-monitoring.md) </span><span class="sxs-lookup"><span data-stu-id="84d04-123">[InterAct Adapter Status Monitoring](../../adapters-and-accelerators/fileact-interact/interact-adapter-status-monitoring.md) </span></span>  
 [<span data-ttu-id="84d04-124">Interagir carte de non-répudiation</span><span class="sxs-lookup"><span data-stu-id="84d04-124">InterAct Adapter Non-Repudiation</span></span>](../../adapters-and-accelerators/fileact-interact/interact-adapter-non-repudiation.md)