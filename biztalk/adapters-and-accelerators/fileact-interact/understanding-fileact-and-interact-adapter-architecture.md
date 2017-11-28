---
title: "Présentation des adaptateurs FileAct et interagir l’Architecture de l’adaptateur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8f97a7fe-20df-4509-bb6e-53743c3a57df
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c04d0ba8b1c2bbd99a71e3d76c8d7ad60c251147
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="understanding-fileact-and-interact-adapter-architecture"></a><span data-ttu-id="e7c6b-102">Présentation des adaptateurs FileAct et interagir l’Architecture de l’adaptateur</span><span class="sxs-lookup"><span data-stu-id="e7c6b-102">Understanding FileAct and InterAct Adapter Architecture</span></span>
<span data-ttu-id="e7c6b-103">L’adaptateur SWIFT est basée sur l’infrastructure d’adaptateurs BizTalk.</span><span class="sxs-lookup"><span data-stu-id="e7c6b-103">The SWIFT Adapter is based on the BizTalk Adapter Framework.</span></span> <span data-ttu-id="e7c6b-104">Selon les classifications des adaptateurs dans BizTalk Server, les adaptateurs SWIFT, adaptateurs FileAct et InterAct, représentent les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="e7c6b-104">Using the classifications of adapters within BizTalk Server, the SWIFT adapters, FileAct and InterAct, represent the following:</span></span>  
  
-   <span data-ttu-id="e7c6b-105">Adaptateur personnalisé.</span><span class="sxs-lookup"><span data-stu-id="e7c6b-105">Custom Adapter.</span></span> <span data-ttu-id="e7c6b-106">Il s’agit d’un adaptateur personnalisé spécialement conçue pour interagir avec le réseau rapide à l’aide d’une norme propriétaire appelée FileAct et Interact.</span><span class="sxs-lookup"><span data-stu-id="e7c6b-106">This is a custom adapter built specifically to interact with the SWIFT network using a proprietary standard called FileAct and Interact.</span></span>  
  
-   <span data-ttu-id="e7c6b-107">Adaptateur de transport.</span><span class="sxs-lookup"><span data-stu-id="e7c6b-107">Transport Adapter.</span></span> <span data-ttu-id="e7c6b-108">Cet adaptateur permet des applications de logiciels d’entreprise envoyer et recevoir des messages avec le réseau rapide.</span><span class="sxs-lookup"><span data-stu-id="e7c6b-108">This adapter allows business software application to send and receive messages with the SWIFT network.</span></span>  
  
-   <span data-ttu-id="e7c6b-109">Non transactionnel.</span><span class="sxs-lookup"><span data-stu-id="e7c6b-109">Non-transacted.</span></span> <span data-ttu-id="e7c6b-110">L’adaptateur ne fait pas utiliser de n’importe quel objet de transaction pour interagir avec le réseau rapide.</span><span class="sxs-lookup"><span data-stu-id="e7c6b-110">The adapter does not make use of any transaction object to interact with the SWIFT network.</span></span>  
  
-   <span data-ttu-id="e7c6b-111">Isolé.</span><span class="sxs-lookup"><span data-stu-id="e7c6b-111">Isolated.</span></span> <span data-ttu-id="e7c6b-112">L’adaptateur de réception s’exécute dans un processus séparé et les adaptateurs d’envoi régulière dans le processus.</span><span class="sxs-lookup"><span data-stu-id="e7c6b-112">The receive adapter runs in a separate process and regular send adapters run in process.</span></span>  
  
 <span data-ttu-id="e7c6b-113">Pour plus d’informations sur l’infrastructure d’adaptateurs BizTalk, consultez le « quel est l’infrastructure d’adaptateurs ? »</span><span class="sxs-lookup"><span data-stu-id="e7c6b-113">For information about the BizTalk Adapter Framework, see the "What Is the Adapter Framework?"</span></span> <span data-ttu-id="e7c6b-114">rubrique dans l’aide de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="e7c6b-114">topic in BizTalk Server Help.</span></span>  
  
 <span data-ttu-id="e7c6b-115">L’illustration suivante montre une vue d’ensemble de l’architecture d’adaptateurs FileAct et InterAct.</span><span class="sxs-lookup"><span data-stu-id="e7c6b-115">The following figure shows a high-level view of the FileAct and InterAct architecture.</span></span>  
  
 ![](../../adapters-and-accelerators/fileact-interact/media/035ebb05-ce11-447c-b56b-ba8b41e07e50.gif "035ebb05-ce11-447c-b56b-ba8b41e07e50")  
  
> [!NOTE]
>  <span data-ttu-id="e7c6b-116">Microsoft [!INCLUDE[swift_adapter](../../includes/swift-adapter-md.md)] prend en charge uniquement les API de lien SWIFTNet (SNL) en mode strict.</span><span class="sxs-lookup"><span data-stu-id="e7c6b-116">Microsoft [!INCLUDE[swift_adapter](../../includes/swift-adapter-md.md)] supports only strict mode SWIFTNet Link (SNL) API.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e7c6b-117">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="e7c6b-117">In This Section</span></span>  
  
-   [<span data-ttu-id="e7c6b-118">SWIFTNet Client et serveur</span><span class="sxs-lookup"><span data-stu-id="e7c6b-118">SWIFTNet Client and Server</span></span>](../../adapters-and-accelerators/fileact-interact/swiftnet-client-and-server.md)  
  
-   [<span data-ttu-id="e7c6b-119">Architecture de l’adaptateur envoi SWIFT</span><span class="sxs-lookup"><span data-stu-id="e7c6b-119">SWIFT Send Adapter Architecture</span></span>](../../adapters-and-accelerators/fileact-interact/swift-send-adapter-architecture.md)  
  
-   [<span data-ttu-id="e7c6b-120">Architecture de l’adaptateur de réception SWIFT</span><span class="sxs-lookup"><span data-stu-id="e7c6b-120">SWIFT Receive Adapter Architecture</span></span>](../../adapters-and-accelerators/fileact-interact/swift-receive-adapter-architecture.md)  
  
-   [<span data-ttu-id="e7c6b-121">Architecture de l’adaptateur FileAct</span><span class="sxs-lookup"><span data-stu-id="e7c6b-121">FileAct Adapter Architecture</span></span>](../../adapters-and-accelerators/fileact-interact/fileact-adapter-architecture.md)  
  
-   [<span data-ttu-id="e7c6b-122">Interagir l’Architecture de l’adaptateur</span><span class="sxs-lookup"><span data-stu-id="e7c6b-122">InterAct Adapter Architecture</span></span>](../../adapters-and-accelerators/fileact-interact/interact-adapter-architecture.md)