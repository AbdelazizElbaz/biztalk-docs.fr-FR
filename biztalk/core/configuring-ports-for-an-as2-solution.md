---
title: Configuration des Ports pour une Solution AS2 | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 715358b1-4226-476b-b0de-2b91434aa24c
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f8f02c5de0edd7956f00e10ce8782e4865033076
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-ports-for-an-as2-solution"></a><span data-ttu-id="3cdd0-102">Configuration des ports pour une solution AS2</span><span class="sxs-lookup"><span data-stu-id="3cdd0-102">Configuring Ports for an AS2 Solution</span></span>
<span data-ttu-id="3cdd0-103">Les ports de réception et d'envoi suivants permettent de transmettre les messages EDI et non-EDI via AS2 :</span><span class="sxs-lookup"><span data-stu-id="3cdd0-103">You can use the following receive and send ports to transmit EDI and non-EDI messages over AS2:</span></span>  
  
 <span data-ttu-id="3cdd0-104">**Ports de réception**</span><span class="sxs-lookup"><span data-stu-id="3cdd0-104">**Receive Ports**</span></span>  
  
|<span data-ttu-id="3cdd0-105">Pour recevoir</span><span class="sxs-lookup"><span data-stu-id="3cdd0-105">To Receive</span></span>|<span data-ttu-id="3cdd0-106">Pour envoyer</span><span class="sxs-lookup"><span data-stu-id="3cdd0-106">To Send</span></span>|<span data-ttu-id="3cdd0-107">Type de Port</span><span class="sxs-lookup"><span data-stu-id="3cdd0-107">Type of Port</span></span>|  
|----------------|-------------|------------------|  
|<span data-ttu-id="3cdd0-108">Un message ou un accusé de réception EDI ou non-EDI</span><span class="sxs-lookup"><span data-stu-id="3cdd0-108">An EDI or non-EDI message or acknowledgment</span></span>|<span data-ttu-id="3cdd0-109">Une réponse MDN (en mode synchrone) ou une réponse HTTP (en mode asynchrone)</span><span class="sxs-lookup"><span data-stu-id="3cdd0-109">An MDN response (if in synchronous mode) or an HTTP response (if in asynchronous mode)</span></span>|<span data-ttu-id="3cdd0-110">Port de réception HTTP bidirectionnel avec requête-réponse</span><span class="sxs-lookup"><span data-stu-id="3cdd0-110">Two-way request-response HTTP receive port</span></span>|  
|<span data-ttu-id="3cdd0-111">Une réponse MDN</span><span class="sxs-lookup"><span data-stu-id="3cdd0-111">An MDN response</span></span>|-|<span data-ttu-id="3cdd0-112">Port de réception HTTP unidirectionnel</span><span class="sxs-lookup"><span data-stu-id="3cdd0-112">One-way HTTP receive port</span></span>|  
  
 <span data-ttu-id="3cdd0-113">**Ports d’envoi**</span><span class="sxs-lookup"><span data-stu-id="3cdd0-113">**Send Ports**</span></span>  
  
|<span data-ttu-id="3cdd0-114">Pour envoyer</span><span class="sxs-lookup"><span data-stu-id="3cdd0-114">To Send</span></span>|<span data-ttu-id="3cdd0-115">Pour recevoir</span><span class="sxs-lookup"><span data-stu-id="3cdd0-115">To Receive</span></span>|<span data-ttu-id="3cdd0-116">Type de Port</span><span class="sxs-lookup"><span data-stu-id="3cdd0-116">Type of Port</span></span>|  
|-------------|----------------|------------------|  
|<span data-ttu-id="3cdd0-117">Un message ou un accusé de réception EDI ou non-EDI</span><span class="sxs-lookup"><span data-stu-id="3cdd0-117">An EDI or non-EDI message or acknowledgment</span></span><br /><br /> <span data-ttu-id="3cdd0-118">(routage basé sur un accord)</span><span class="sxs-lookup"><span data-stu-id="3cdd0-118">(agreement-based routing)</span></span>|-|<span data-ttu-id="3cdd0-119">Port d'envoi HTTP unidirectionnel statique</span><span class="sxs-lookup"><span data-stu-id="3cdd0-119">Static one-way HTTP send port</span></span>|  
|<span data-ttu-id="3cdd0-120">Un message ou un accusé de réception EDI ou non-EDI</span><span class="sxs-lookup"><span data-stu-id="3cdd0-120">An EDI or non-EDI message or acknowledgment</span></span><br /><br /> <span data-ttu-id="3cdd0-121">(routage basé sur le contenu)</span><span class="sxs-lookup"><span data-stu-id="3cdd0-121">(content-based routing)</span></span>|<span data-ttu-id="3cdd0-122">Une réponse MDN</span><span class="sxs-lookup"><span data-stu-id="3cdd0-122">An MDN response</span></span>|<span data-ttu-id="3cdd0-123">Port d'envoi HTTP bidirectionnel dynamique avec sollicitation-réponse</span><span class="sxs-lookup"><span data-stu-id="3cdd0-123">Dynamic two-way solicit-response HTTP send port</span></span>|  
|<span data-ttu-id="3cdd0-124">Un message ou un accusé de réception EDI ou non-EDI</span><span class="sxs-lookup"><span data-stu-id="3cdd0-124">An EDI or non-EDI message or acknowledgment</span></span><br /><br /> <span data-ttu-id="3cdd0-125">(routage basé sur le contenu)</span><span class="sxs-lookup"><span data-stu-id="3cdd0-125">(content-based routing)</span></span>|-|<span data-ttu-id="3cdd0-126">Port d'envoi HTTP unidirectionnel dynamique</span><span class="sxs-lookup"><span data-stu-id="3cdd0-126">Dynamic one-way HTTP send port</span></span>|  
|<span data-ttu-id="3cdd0-127">Une réponse MDN asynchrone</span><span class="sxs-lookup"><span data-stu-id="3cdd0-127">An asynchronous MDN response</span></span><br /><br /> <span data-ttu-id="3cdd0-128">(routage basé sur le contenu)</span><span class="sxs-lookup"><span data-stu-id="3cdd0-128">(content-based routing)</span></span>|-|<span data-ttu-id="3cdd0-129">Port d'envoi unidirectionnel dynamique</span><span class="sxs-lookup"><span data-stu-id="3cdd0-129">Dynamic one-way send port</span></span>|  
|<span data-ttu-id="3cdd0-130">Une réponse MDN asynchrone</span><span class="sxs-lookup"><span data-stu-id="3cdd0-130">An asynchronous MDN response</span></span>|-|<span data-ttu-id="3cdd0-131">Port d'envoi unidirectionnel statique</span><span class="sxs-lookup"><span data-stu-id="3cdd0-131">Static one-way send port</span></span>|  
  
## <a name="in-this-section"></a><span data-ttu-id="3cdd0-132">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="3cdd0-132">In This Section</span></span>  
  
-   [<span data-ttu-id="3cdd0-133">Configuration d’un Port de réception des Messages via AS2</span><span class="sxs-lookup"><span data-stu-id="3cdd0-133">Configuring a Receive Port for Messages over AS2</span></span>](../core/configuring-a-receive-port-for-messages-over-as2.md)  
  
-   [<span data-ttu-id="3cdd0-134">Configuration d’un Port de réception pour les MDN entrants</span><span class="sxs-lookup"><span data-stu-id="3cdd0-134">Configuring a Receive Port for Incoming MDNs</span></span>](../core/configuring-a-receive-port-for-incoming-mdns.md)  
  
-   [<span data-ttu-id="3cdd0-135">Configuration d’un Port d’envoi statique pour les Messages via AS2</span><span class="sxs-lookup"><span data-stu-id="3cdd0-135">Configuring a Static Send Port for Messages over AS2</span></span>](../core/configuring-a-static-send-port-for-messages-over-as2.md)  
  
-   [<span data-ttu-id="3cdd0-136">Configuration d’un Port d’envoi dynamique pour les Messages via AS2</span><span class="sxs-lookup"><span data-stu-id="3cdd0-136">Configuring a Dynamic Send Port for Messages over AS2</span></span>](../core/configuring-a-dynamic-send-port-for-messages-over-as2.md)  
  
-   [<span data-ttu-id="3cdd0-137">Configuration d’un Port d’envoi statique pour les MDN asynchrones via AS2</span><span class="sxs-lookup"><span data-stu-id="3cdd0-137">Configuring a Static Send Port for Asynchronous MDNs over AS2</span></span>](../core/configuring-a-static-send-port-for-asynchronous-mdns-over-as2.md)  
  
-   [<span data-ttu-id="3cdd0-138">Configuration d’un Port d’envoi dynamique pour les MDN asynchrones via AS2</span><span class="sxs-lookup"><span data-stu-id="3cdd0-138">Configuring a Dynamic Send Port for Asynchronous MDNs over AS2</span></span>](../core/configuring-a-dynamic-send-port-for-asynchronous-mdns-over-as2.md)  
  
## <a name="see-also"></a><span data-ttu-id="3cdd0-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3cdd0-139">See Also</span></span>  
 [<span data-ttu-id="3cdd0-140">Développement et la configuration des Solutions AS2 BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="3cdd0-140">Developing and Configuring BizTalk Server AS2 Solutions</span></span>](../core/developing-and-configuring-biztalk-server-as2-solutions.md)