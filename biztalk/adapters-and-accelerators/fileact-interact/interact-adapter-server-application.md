---
title: "Application de serveur de l’adaptateur interAct | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8c50b239-0480-449f-aa6d-50bbb892e8a1
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d62e8cfe8f01e200dbb8f752507d0211e4184fe4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="interact-adapter-server-application"></a><span data-ttu-id="eed9f-102">Application de serveur de l’adaptateur interAct</span><span class="sxs-lookup"><span data-stu-id="eed9f-102">InterAct Adapter Server Application</span></span>
<span data-ttu-id="eed9f-103">Cette section présente une description générale de la composition des messages de demande d’application serveur.</span><span class="sxs-lookup"><span data-stu-id="eed9f-103">This section presents a general description of the composition of server application Request messages.</span></span> <span data-ttu-id="eed9f-104">Voici les documents XML provenant du côté serveur SNL à l’application serveur.</span><span class="sxs-lookup"><span data-stu-id="eed9f-104">These are the XML documents passed from the server-side SNL to the server application.</span></span> <span data-ttu-id="eed9f-105">Par conséquent, ces messages sont caractéristique de la première partie des primitives SWIFTNet testés côté serveur.</span><span class="sxs-lookup"><span data-stu-id="eed9f-105">As such, these messages are characteristic of the first part of the SWIFTNet primitives exercised on the server side.</span></span>  
  
 <span data-ttu-id="eed9f-106">La figure suivante illustre le serveur de message de demande.</span><span class="sxs-lookup"><span data-stu-id="eed9f-106">The following figure shows the server request message.</span></span>  
  
 <span data-ttu-id="eed9f-107">![Message de demande de serveur](../../adapters-and-accelerators/fileact-interact/media/05bf7d1b-199c-4806-be91-32ca013e9af8.gif "05bf7d1b-199c-4806-be91-32ca013e9af8")</span><span class="sxs-lookup"><span data-stu-id="eed9f-107">![Server request message](../../adapters-and-accelerators/fileact-interact/media/05bf7d1b-199c-4806-be91-32ca013e9af8.gif "05bf7d1b-199c-4806-be91-32ca013e9af8")</span></span>  
  
 <span data-ttu-id="eed9f-108">L’illustration suivante montre la séquence des messages échangés entre SNL et l’application serveur InterAct.</span><span class="sxs-lookup"><span data-stu-id="eed9f-108">The following figure shows the sequence of messages exchanged between SNL and the InterAct server application.</span></span>  
  
 <span data-ttu-id="eed9f-109">![Application de serveur de l’adaptateur interAct](../../adapters-and-accelerators/fileact-interact/media/33edb889-edfa-4e55-842a-e238950327e6.gif "33edb889-edfa-4e55-842a-e238950327e6")</span><span class="sxs-lookup"><span data-stu-id="eed9f-109">![InterAct adapter server application](../../adapters-and-accelerators/fileact-interact/media/33edb889-edfa-4e55-842a-e238950327e6.gif "33edb889-edfa-4e55-842a-e238950327e6")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eed9f-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="eed9f-110">See Also</span></span>  
 <span data-ttu-id="eed9f-111">[Interagir l’Architecture de l’adaptateur](../../adapters-and-accelerators/fileact-interact/interact-adapter-architecture.md) </span><span class="sxs-lookup"><span data-stu-id="eed9f-111">[InterAct Adapter Architecture](../../adapters-and-accelerators/fileact-interact/interact-adapter-architecture.md) </span></span>  
 <span data-ttu-id="eed9f-112">[Composants d’adaptateur interAct](../../adapters-and-accelerators/fileact-interact/interact-adapter-components.md) </span><span class="sxs-lookup"><span data-stu-id="eed9f-112">[InterAct Adapter Components](../../adapters-and-accelerators/fileact-interact/interact-adapter-components.md) </span></span>  
 <span data-ttu-id="eed9f-113">[Interaction des Messages de la carte pour l’échange](../../adapters-and-accelerators/fileact-interact/interact-adapter-messages-for-business-exchange.md) </span><span class="sxs-lookup"><span data-stu-id="eed9f-113">[InterAct Adapter Messages for Business Exchange](../../adapters-and-accelerators/fileact-interact/interact-adapter-messages-for-business-exchange.md) </span></span>  
 <span data-ttu-id="eed9f-114">[Application cliente de l’adaptateur interAct](../../adapters-and-accelerators/fileact-interact/interact-adapter-client-application.md) </span><span class="sxs-lookup"><span data-stu-id="eed9f-114">[InterAct Adapter Client Application](../../adapters-and-accelerators/fileact-interact/interact-adapter-client-application.md) </span></span>  
 <span data-ttu-id="eed9f-115">[Interagir de magasin de l’adaptateur et le transfert](../../adapters-and-accelerators/fileact-interact/interact-adapter-store-and-forward.md) </span><span class="sxs-lookup"><span data-stu-id="eed9f-115">[InterAct Adapter Store and Forward](../../adapters-and-accelerators/fileact-interact/interact-adapter-store-and-forward.md) </span></span>  
 <span data-ttu-id="eed9f-116">[Interagir l’Architecture de sécurité de carte](../../adapters-and-accelerators/fileact-interact/interact-adapter-security-architecture.md) </span><span class="sxs-lookup"><span data-stu-id="eed9f-116">[InterAct Adapter Security Architecture](../../adapters-and-accelerators/fileact-interact/interact-adapter-security-architecture.md) </span></span>  
 <span data-ttu-id="eed9f-117">[Interagir remise fiable de bout en bout pour l’adaptateur](../../adapters-and-accelerators/fileact-interact/interact-adapter-end-to-end-reliable-delivery.md) </span><span class="sxs-lookup"><span data-stu-id="eed9f-117">[InterAct Adapter End-to-End Reliable Delivery](../../adapters-and-accelerators/fileact-interact/interact-adapter-end-to-end-reliable-delivery.md) </span></span>  
 <span data-ttu-id="eed9f-118">[Interagir l’état de la carte d’analyse](../../adapters-and-accelerators/fileact-interact/interact-adapter-status-monitoring.md) </span><span class="sxs-lookup"><span data-stu-id="eed9f-118">[InterAct Adapter Status Monitoring](../../adapters-and-accelerators/fileact-interact/interact-adapter-status-monitoring.md) </span></span>  
 [<span data-ttu-id="eed9f-119">Interagir carte de non-répudiation</span><span class="sxs-lookup"><span data-stu-id="eed9f-119">InterAct Adapter Non-Repudiation</span></span>](../../adapters-and-accelerators/fileact-interact/interact-adapter-non-repudiation.md)