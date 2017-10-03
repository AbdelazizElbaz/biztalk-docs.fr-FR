---
title: "Qu'est-ce que l'adaptateur WCF-NetMsmq ? | Microsoft Docs"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: WCF-NetMsmq adapters, about WCF-NetMsmq adapters
ms.assetid: 506c5e2d-6cbe-4788-8e37-49d009dc559a
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1008cc7178c38532f1781890080eacf4b5dfb56c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="what-is-the-wcf-netmsmq-adapter"></a><span data-ttu-id="9a94a-103">Qu'est-ce que l'adaptateur WCF-NetMsmq ?</span><span class="sxs-lookup"><span data-stu-id="9a94a-103">What Is the WCF-NetMsmq Adapter?</span></span>
<span data-ttu-id="9a94a-104">L'adaptateur WCF-NetMsmq permet à des ordinateurs déconnectés de communiquer à l'aide la technologie de mise en file d'attente au sein d'un environnement où les services et les clients sont de type WCF.</span><span class="sxs-lookup"><span data-stu-id="9a94a-104">The WCF-NetMsmq adapter provides disconnected cross-computer communication by using queuing technology in an environment where both the services and clients are WCF based.</span></span> <span data-ttu-id="9a94a-105">Cet adaptateur utilise le transport MSMQ (Message Queuing) et les messages ont un codage binaire.</span><span class="sxs-lookup"><span data-stu-id="9a94a-105">It uses the Message Queuing (MSMQ) transport, and messages have binary encoding.</span></span>  
  
 <span data-ttu-id="9a94a-106">Le tableau suivant répertorie les caractéristiques de l'adaptateur WCF-NetMsmq.</span><span class="sxs-lookup"><span data-stu-id="9a94a-106">The following table summarizes the characteristics for the WCF-NetMsmq adapter.</span></span>  
  
|<span data-ttu-id="9a94a-107"> Description</span><span class="sxs-lookup"><span data-stu-id="9a94a-107">Description</span></span>|<span data-ttu-id="9a94a-108">Caractéristique</span><span class="sxs-lookup"><span data-stu-id="9a94a-108">Characteristic</span></span>|  
|-----------------|--------------------|  
|<span data-ttu-id="9a94a-109">Niveau d'interopérabilité</span><span class="sxs-lookup"><span data-stu-id="9a94a-109">Interoperability level</span></span>|<span data-ttu-id="9a94a-110">Profil .NET</span><span class="sxs-lookup"><span data-stu-id="9a94a-110">.NET-Profile</span></span>|  
|<span data-ttu-id="9a94a-111">Codage du message</span><span class="sxs-lookup"><span data-stu-id="9a94a-111">Message encoding</span></span>|<span data-ttu-id="9a94a-112">Binaire</span><span class="sxs-lookup"><span data-stu-id="9a94a-112">Binary</span></span>|  
|<span data-ttu-id="9a94a-113">Limite</span><span class="sxs-lookup"><span data-stu-id="9a94a-113">Boundary</span></span>|<span data-ttu-id="9a94a-114">Entre ordinateurs</span><span class="sxs-lookup"><span data-stu-id="9a94a-114">Cross-computer</span></span>|  
|<span data-ttu-id="9a94a-115">Protocole de transport</span><span class="sxs-lookup"><span data-stu-id="9a94a-115">Transport protocol</span></span>|<span data-ttu-id="9a94a-116">MSMQ</span><span class="sxs-lookup"><span data-stu-id="9a94a-116">MSMQ</span></span>|  
|<span data-ttu-id="9a94a-117">Mode de sécurité</span><span class="sxs-lookup"><span data-stu-id="9a94a-117">Security mode</span></span>|<span data-ttu-id="9a94a-118">None, Message, Transport et Both.</span><span class="sxs-lookup"><span data-stu-id="9a94a-118">None, Message, Transport, and Both.</span></span>|  
|<span data-ttu-id="9a94a-119">Mécanisme d'authentification du client</span><span class="sxs-lookup"><span data-stu-id="9a94a-119">Client authentication mechanism</span></span>|<span data-ttu-id="9a94a-120">Sécurité du transport et sécurité des messages</span><span class="sxs-lookup"><span data-stu-id="9a94a-120">Transport Security and Message Security</span></span>|  
|<span data-ttu-id="9a94a-121">Prise en charge de WS-ReliableMessaging</span><span class="sxs-lookup"><span data-stu-id="9a94a-121">Support for WS-ReliableMessaging</span></span>|<span data-ttu-id="9a94a-122">Non applicable</span><span class="sxs-lookup"><span data-stu-id="9a94a-122">Not applicable</span></span>|  
|<span data-ttu-id="9a94a-123">Prise en charge de WS-AtomicTransaction</span><span class="sxs-lookup"><span data-stu-id="9a94a-123">Support for WS-AtomicTransaction</span></span>|<span data-ttu-id="9a94a-124">Oui</span><span class="sxs-lookup"><span data-stu-id="9a94a-124">Yes</span></span>|  
|<span data-ttu-id="9a94a-125">Prise en charge de la messagerie unidirectionnelle</span><span class="sxs-lookup"><span data-stu-id="9a94a-125">Support for one-way messaging</span></span>|<span data-ttu-id="9a94a-126">Oui</span><span class="sxs-lookup"><span data-stu-id="9a94a-126">Yes</span></span>|  
|<span data-ttu-id="9a94a-127">Prise en charge de la messagerie bidirectionnelle</span><span class="sxs-lookup"><span data-stu-id="9a94a-127">Support for two-way messaging</span></span>|<span data-ttu-id="9a94a-128">Non</span><span class="sxs-lookup"><span data-stu-id="9a94a-128">No</span></span>|  
|<span data-ttu-id="9a94a-129">Type d'hôte pour l'adaptateur de réception</span><span class="sxs-lookup"><span data-stu-id="9a94a-129">Host type for receive adapter</span></span>|<span data-ttu-id="9a94a-130">In-process</span><span class="sxs-lookup"><span data-stu-id="9a94a-130">In-process</span></span>|  
|<span data-ttu-id="9a94a-131">Type d'hôte pour l'adaptateur d'envoi</span><span class="sxs-lookup"><span data-stu-id="9a94a-131">Host type for send adapter</span></span>|<span data-ttu-id="9a94a-132">In-process</span><span class="sxs-lookup"><span data-stu-id="9a94a-132">In-process</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="9a94a-133">Les files d'attente à partir desquelles l'adaptateur de réception WCF-NetMsmq récupère les messages doivent être créées à l'avance.</span><span class="sxs-lookup"><span data-stu-id="9a94a-133">The queues from which the WCF-NetMsmq receive adapter pulls messages must be created in advance.</span></span> <span data-ttu-id="9a94a-134">Les messages se trouvant dans les files d'attente doivent être du type WCF, sinon ils seront envoyés dans la file d'attente des messages non distribués.</span><span class="sxs-lookup"><span data-stu-id="9a94a-134">The messages in the queues must be WCF based; otherwise, these messages will be sent to the dead-letter queue.</span></span>  
  
 <span data-ttu-id="9a94a-135">L'adaptateur WCF-NetMsmq est constitué de deux adaptateurs : un adaptateur de réception et un adaptateur d'envoi.</span><span class="sxs-lookup"><span data-stu-id="9a94a-135">The WCF-NetMsmq adapter consists of two adapters—a receive adapter and a send adapter.</span></span>  
  
 <span data-ttu-id="9a94a-136">**Adaptateur de réception WCF-NetMsmq**</span><span class="sxs-lookup"><span data-stu-id="9a94a-136">**WCF-NetMsmq Receive Adapter**</span></span>  
  
 <span data-ttu-id="9a94a-137">L'adaptateur de réception WCF-NetMsmq permet de recevoir des demandes de service WCF via MSMQ.</span><span class="sxs-lookup"><span data-stu-id="9a94a-137">You use the WCF-NetMsmq receive adapter to receive WCF service requests over MSMQ.</span></span> <span data-ttu-id="9a94a-138">Un emplacement de réception qui utilise l'adaptateur de réception WCF-NetMsmq peut uniquement être configuré comme emplacement de réception unidirectionnel.</span><span class="sxs-lookup"><span data-stu-id="9a94a-138">A receive location that uses the WCF-NetMsmq receive adapter can only be configured as one-way receive.</span></span>  
  
 <span data-ttu-id="9a94a-139">**Adaptateur d’envoi WCF-NetMsmq**</span><span class="sxs-lookup"><span data-stu-id="9a94a-139">**WCF-NetMsmq Send Adapter**</span></span>  
  
 <span data-ttu-id="9a94a-140">L'adaptateur d'envoi WCF-NetMsmq permet d'appeler un service WCF à l'aide du contrat sans type via MSMQ.</span><span class="sxs-lookup"><span data-stu-id="9a94a-140">You use the WCF-NetMsmq send adapter to call a WCF service through the typeless contract over MSMQ.</span></span>  
  
 <span data-ttu-id="9a94a-141">Pour plus d’informations sur WCF de réception et les adaptateurs d’envoi, consultez [quelles sont les adaptateurs WCF ?](../core/what-are-the-wcf-adapters.md).</span><span class="sxs-lookup"><span data-stu-id="9a94a-141">For more information about WCF receive and send adapters, see [What Are the WCF Adapters?](../core/what-are-the-wcf-adapters.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a94a-142">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9a94a-142">See Also</span></span>  
 <span data-ttu-id="9a94a-143">[Configuration de l’adaptateur WCF-NetMsmq](../core/configuring-the-wcf-netmsmq-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="9a94a-143">[Configuring the WCF-NetMsmq Adapter](../core/configuring-the-wcf-netmsmq-adapter.md) </span></span>  
 [<span data-ttu-id="9a94a-144">Adaptateurs WCF</span><span class="sxs-lookup"><span data-stu-id="9a94a-144">WCF Adapters</span></span>](../core/wcf-adapters.md)