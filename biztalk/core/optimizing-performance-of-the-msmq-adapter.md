---
title: "Optimisation des performances de l’adaptateur MSMQ | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MSMQ adapters, performance
- performance, MSMQ adapters
- configuring [MSMQ adapters], performance
ms.assetid: f8537ea8-a96e-4874-bcaf-cd1442a50bd4
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7c5624eb6cf88f45d1ecad0b68fee3f5f7b8a8ba
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="optimizing-performance-of-the-msmq-adapter"></a><span data-ttu-id="4bd29-102">Optimisation des performances de l’adaptateur MSMQ</span><span class="sxs-lookup"><span data-stu-id="4bd29-102">Optimizing Performance of the MSMQ Adapter</span></span>
<span data-ttu-id="4bd29-103">L'optimisation de l'adaptateur MSMQ diffère entre les côtés envoi et réception.</span><span class="sxs-lookup"><span data-stu-id="4bd29-103">Optimization of the MSMQ adapter differs between the send and receive sides.</span></span> <span data-ttu-id="4bd29-104">Vous contrôlez l'optimisation côté réception en définissant une propriété sur l'emplacement de réception.</span><span class="sxs-lookup"><span data-stu-id="4bd29-104">You control optimization on the receive side by setting a property on the receive location.</span></span> <span data-ttu-id="4bd29-105">Côté envoi, vous pouvez contrôler l'optimisation à l'aide d'une orchestration.</span><span class="sxs-lookup"><span data-stu-id="4bd29-105">On the send side, you can control optimization by using an orchestration.</span></span>  
  
## <a name="receive-optimization"></a><span data-ttu-id="4bd29-106">Optimisation de la réception</span><span class="sxs-lookup"><span data-stu-id="4bd29-106">Receive Optimization</span></span>  
 <span data-ttu-id="4bd29-107">Côté réception, vous pouvez configurer l'adaptateur pour qu'il n'utilise qu'un seul thread d'exécution.</span><span class="sxs-lookup"><span data-stu-id="4bd29-107">On the receive side, you can have the adapter use a single execution thread.</span></span> <span data-ttu-id="4bd29-108">Indique si l’adaptateur utilise un thread unique ou plusieurs threads varie selon le paramètre de la **traitement chronologique** propriété sur l’emplacement de réception, comme suit :</span><span class="sxs-lookup"><span data-stu-id="4bd29-108">Whether the adapter uses a single thread or multiple threads depends on the setting of the **Ordered Processing** property on the receive location, as follows:</span></span>  
  
-   <span data-ttu-id="4bd29-109">Lorsque la propriété est **True**, l’adaptateur ne fonctionne que sur un seul thread.</span><span class="sxs-lookup"><span data-stu-id="4bd29-109">When the property is **True**, the adapter operates on a single thread.</span></span> <span data-ttu-id="4bd29-110">Ceci limite l'adaptateur à un message à la fois et permet d'économiser de la mémoire.</span><span class="sxs-lookup"><span data-stu-id="4bd29-110">This limits the adapter to one message at a time and conserves memory.</span></span> <span data-ttu-id="4bd29-111">Notez qu’il définit efficacement **taille de lot** à un (1), quelle que soit la valeur affectée à ce dernier dans la feuille de propriétés.</span><span class="sxs-lookup"><span data-stu-id="4bd29-111">Notice that this effectively sets **Batch Size** to one (1), regardless of the value assigned to it in the property sheet.</span></span>  
  
-   <span data-ttu-id="4bd29-112">Lorsque **traitement chronologique** est **False**, l’adaptateur s’exécute plusieurs threads et peut traiter plusieurs messages à la fois, augmentant ainsi les performances.</span><span class="sxs-lookup"><span data-stu-id="4bd29-112">When **Ordered Processing** is **False**, the adapter runs multiple threads and can process multiple messages at a time, therefore increasing performance.</span></span>  
  
 <span data-ttu-id="4bd29-113">Vous devez définir **traitement chronologique** à **True** si vous placez une prime sur la gestion des ressources du serveur, ou si le nombre ou la taille des messages peut saturer la mémoire disponible.</span><span class="sxs-lookup"><span data-stu-id="4bd29-113">You must set **Ordered Processing** to **True** if you put a premium on managing server resources, or if the number or size of messages might exhaust available memory.</span></span>  
  
 <span data-ttu-id="4bd29-114">Vous pouvez également contrôler l’utilisation de la mémoire en réduisant la valeur de **taille de lot** sur l’emplacement de réception.</span><span class="sxs-lookup"><span data-stu-id="4bd29-114">You can also control memory use by reducing the value of **Batch Size** on the receive location.</span></span> <span data-ttu-id="4bd29-115">Une taille de lot réduite conserve un plus petit nombre de messages en mémoire, et utilise donc moins de mémoire.</span><span class="sxs-lookup"><span data-stu-id="4bd29-115">A smaller batch size keeps fewer messages in memory and therefore uses less memory.</span></span>  
  
 <span data-ttu-id="4bd29-116">Le placement des ports d'envoi et des emplacements de réception sur des ordinateurs distincts peut également réduire l'utilisation de la mémoire.</span><span class="sxs-lookup"><span data-stu-id="4bd29-116">Placing send ports and receive locations on separate computers can also reduce memory use.</span></span>  
  
## <a name="send-optimization"></a><span data-ttu-id="4bd29-117">Optimisation côté envoi</span><span class="sxs-lookup"><span data-stu-id="4bd29-117">Send Optimization</span></span>  
 <span data-ttu-id="4bd29-118">Côté envoi, vous pouvez obtenir un traitement par message unique à l'aide de l'exemple d'orchestration.</span><span class="sxs-lookup"><span data-stu-id="4bd29-118">On the send side, you can achieve the equivalent single-message processing by using the sample orchestration.</span></span> <span data-ttu-id="4bd29-119">Celui-ci envoie un message unique, puis attend de recevoir un accusé de réception pour envoyer le message suivant.</span><span class="sxs-lookup"><span data-stu-id="4bd29-119">The sample sends a single message and then waits to send the next message until it receives an acknowledgment.</span></span> <span data-ttu-id="4bd29-120">Pour plus d’informations, consultez [comment créer des emplacements de réception MSMQ et les Ports d’envoi à partir de Code](../core/how-to-create-msmq-receive-locations-and-send-ports-from-code.md).</span><span class="sxs-lookup"><span data-stu-id="4bd29-120">For more information, see [How to Create MSMQ Receive Locations and Send Ports from Code](../core/how-to-create-msmq-receive-locations-and-send-ports-from-code.md).</span></span>  
  
## <a name="remote-transactional-read-operations"></a><span data-ttu-id="4bd29-121">Opérations de lectures transactionnelles distantes</span><span class="sxs-lookup"><span data-stu-id="4bd29-121">Remote Transactional Read Operations</span></span>  
 <span data-ttu-id="4bd29-122">Adaptateur MSMQ de BizTalk Server est capable d’effectuer des opérations de lecture à distance à partir des files d’attente MSMQ transactionnelles.</span><span class="sxs-lookup"><span data-stu-id="4bd29-122">With BizTalk Server the MSMQ adapter is capable of making remote read operations from transactional MSMQ queues.</span></span>  <span data-ttu-id="4bd29-123">Cela est dû au fait que MSMQ 4.0 et les versions ultérieures prennent en charge les opérations de lectures transactionnelles distantes.</span><span class="sxs-lookup"><span data-stu-id="4bd29-123">This is because MSMQ 4.0 and later versions support remote transactional read operations.</span></span>  <span data-ttu-id="4bd29-124">Cependant, les opérations de lectures transactionnelles sont des opérations généralement lentes.</span><span class="sxs-lookup"><span data-stu-id="4bd29-124">However, transactional read operations are typically slow operations.</span></span> <span data-ttu-id="4bd29-125">Pour optimiser les performances, elles ne doivent être utilisées qu'en dernier recours.</span><span class="sxs-lookup"><span data-stu-id="4bd29-125">To optimize performance they should be used only when there is no other option.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4bd29-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4bd29-126">See Also</span></span>  
 <span data-ttu-id="4bd29-127">[Pour configurer un MSMQ emplacement de réception](../core/how-to-configure-an-msmq-receive-location.md) </span><span class="sxs-lookup"><span data-stu-id="4bd29-127">[How to Configure an MSMQ Receive Location](../core/how-to-configure-an-msmq-receive-location.md) </span></span>  
 <span data-ttu-id="4bd29-128">[Comment configurer un Port d’envoi MSMQ](../core/how-to-configure-an-msmq-send-port.md) </span><span class="sxs-lookup"><span data-stu-id="4bd29-128">[How to Configure an MSMQ Send Port](../core/how-to-configure-an-msmq-send-port.md) </span></span>  
 [<span data-ttu-id="4bd29-129">Configuration de l’adaptateur MSMQ</span><span class="sxs-lookup"><span data-stu-id="4bd29-129">Configuring the MSMQ Adapter</span></span>](../core/configuring-the-msmq-adapter.md)