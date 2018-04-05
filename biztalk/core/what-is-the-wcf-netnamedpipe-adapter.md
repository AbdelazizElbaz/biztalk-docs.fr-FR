---
title: Qu'est-ce que l'adaptateur WCF-NetNamedPipe ? | Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WCF-NetNamedPipe adapters, about WCF-NetNamedPipe adapters
ms.assetid: b9f84256-e49d-4ee2-b0fa-d3f692ade1d4
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 43c73a670139690c4a27d4784c6ad23225492f17
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="what-is-the-wcf-netnamedpipe-adapter"></a><span data-ttu-id="68561-103">Qu'est-ce que l'adaptateur WCF-NetNamedPipe ?</span><span class="sxs-lookup"><span data-stu-id="68561-103">What Is the WCF-NetNamedPipe Adapter?</span></span>
<span data-ttu-id="68561-104">L'adaptateur WCF-NetNamedPipe permet une communication entre processus sur un ordinateur au sein d'un environnement où les services et les clients sont de type WCF.</span><span class="sxs-lookup"><span data-stu-id="68561-104">The WCF-NetNamedPipe adapter provides cross-process communication on the same computer in an environment in which both services and clients are WCF based.</span></span> <span data-ttu-id="68561-105">Il fournit un accès total aux fonctionnalités de fiabilité et de transaction SOAP.</span><span class="sxs-lookup"><span data-stu-id="68561-105">It provides full access to SOAP reliability and transaction features.</span></span> <span data-ttu-id="68561-106">Il utilise le transport de canal nommé et les messages relèvent d'un codage binaire.</span><span class="sxs-lookup"><span data-stu-id="68561-106">The adapter uses the named pipe transport, and messages have binary encoding.</span></span> <span data-ttu-id="68561-107">Vous ne devez pas utiliser cet adaptateur dans une communication entre ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="68561-107">This adapter cannot be used in cross-computer communication.</span></span>  
  
 <span data-ttu-id="68561-108">Le tableau suivant répertorie les caractéristiques de l'adaptateur WCF-NetNamedPipe.</span><span class="sxs-lookup"><span data-stu-id="68561-108">The following table summarizes the characteristics for the WCF-NetNamedPipe adapter.</span></span>  
  
|<span data-ttu-id="68561-109"> Description</span><span class="sxs-lookup"><span data-stu-id="68561-109">Description</span></span>|<span data-ttu-id="68561-110">Caractéristique</span><span class="sxs-lookup"><span data-stu-id="68561-110">Characteristic</span></span>|  
|-----------------|--------------------|  
|<span data-ttu-id="68561-111">Niveau d'interopérabilité</span><span class="sxs-lookup"><span data-stu-id="68561-111">Interoperability level</span></span>|<span data-ttu-id="68561-112">Profil .NET</span><span class="sxs-lookup"><span data-stu-id="68561-112">.NET-Profile</span></span>|  
|<span data-ttu-id="68561-113">Codage du message</span><span class="sxs-lookup"><span data-stu-id="68561-113">Message encoding</span></span>|<span data-ttu-id="68561-114">Binaire</span><span class="sxs-lookup"><span data-stu-id="68561-114">Binary</span></span>|  
|<span data-ttu-id="68561-115">Limite</span><span class="sxs-lookup"><span data-stu-id="68561-115">Boundary</span></span>|<span data-ttu-id="68561-116">Interprocessus</span><span class="sxs-lookup"><span data-stu-id="68561-116">Cross-process</span></span>|  
|<span data-ttu-id="68561-117">Protocole de transport</span><span class="sxs-lookup"><span data-stu-id="68561-117">Transport protocol</span></span>|<span data-ttu-id="68561-118">Canal nommé</span><span class="sxs-lookup"><span data-stu-id="68561-118">Named pipe</span></span>|  
|<span data-ttu-id="68561-119">Mode de sécurité</span><span class="sxs-lookup"><span data-stu-id="68561-119">Security mode</span></span>|<span data-ttu-id="68561-120">None et Transport</span><span class="sxs-lookup"><span data-stu-id="68561-120">None and Transport</span></span>|  
|<span data-ttu-id="68561-121">Mécanisme d'authentification du client</span><span class="sxs-lookup"><span data-stu-id="68561-121">Client authentication mechanism</span></span>|<span data-ttu-id="68561-122">Sécurité du transport et sécurité des messages</span><span class="sxs-lookup"><span data-stu-id="68561-122">Transport Security and Message Security</span></span>|  
|<span data-ttu-id="68561-123">Prise en charge de WS-ReliableMessaging</span><span class="sxs-lookup"><span data-stu-id="68561-123">Support for WS-ReliableMessaging</span></span>|<span data-ttu-id="68561-124">Non</span><span class="sxs-lookup"><span data-stu-id="68561-124">No</span></span>|  
|<span data-ttu-id="68561-125">Prise en charge de WS-AtomicTransaction</span><span class="sxs-lookup"><span data-stu-id="68561-125">Support for WS-AtomicTransaction</span></span>|<span data-ttu-id="68561-126">Oui</span><span class="sxs-lookup"><span data-stu-id="68561-126">Yes</span></span>|  
|<span data-ttu-id="68561-127">Prise en charge de la messagerie unidirectionnelle</span><span class="sxs-lookup"><span data-stu-id="68561-127">Support for one-way messaging</span></span>|<span data-ttu-id="68561-128">Oui</span><span class="sxs-lookup"><span data-stu-id="68561-128">Yes</span></span>|  
|<span data-ttu-id="68561-129">Prise en charge de la messagerie bidirectionnelle</span><span class="sxs-lookup"><span data-stu-id="68561-129">Support for two-way messaging</span></span>|<span data-ttu-id="68561-130">Oui</span><span class="sxs-lookup"><span data-stu-id="68561-130">Yes</span></span>|  
|<span data-ttu-id="68561-131">Type d'hôte pour l'adaptateur de réception</span><span class="sxs-lookup"><span data-stu-id="68561-131">Host type for receive adapter</span></span>|<span data-ttu-id="68561-132">In-process</span><span class="sxs-lookup"><span data-stu-id="68561-132">In-process</span></span>|  
|<span data-ttu-id="68561-133">Type d'hôte pour l'adaptateur d'envoi</span><span class="sxs-lookup"><span data-stu-id="68561-133">Host type for send adapter</span></span>|<span data-ttu-id="68561-134">In-process</span><span class="sxs-lookup"><span data-stu-id="68561-134">In-process</span></span>|  
  
 <span data-ttu-id="68561-135">L'adaptateur WCF-NetNamedPipe est constitué de deux adaptateurs : un adaptateur de réception et un adaptateur d'envoi.</span><span class="sxs-lookup"><span data-stu-id="68561-135">The WCF-NetNamedPipe adapter consists of two adapters—a receive adapter and a send adapter.</span></span>  
  
 <span data-ttu-id="68561-136">**Adaptateur de réception WCF-NetNamedPipe**</span><span class="sxs-lookup"><span data-stu-id="68561-136">**WCF-NetNamedPipe Receive Adapter**</span></span>  
  
 <span data-ttu-id="68561-137">L'adaptateur de réception WCF-NetNamedPipe permet de recevoir des demandes de service WCF via le transport de canal nommé.</span><span class="sxs-lookup"><span data-stu-id="68561-137">You use the WCF-NetNamedPipe receive adapter to receive WCF service requests over the named pipe transport.</span></span> <span data-ttu-id="68561-138">Un emplacement de réception qui utilise l'adaptateur de réception NetNamedPipe peut être configuré comme emplacement de réception unidirectionnel ou de requête-réponse (bidirectionnel).</span><span class="sxs-lookup"><span data-stu-id="68561-138">A receive location that uses the WCF-NetNamedPipe receive adapter can be configured as one-way or request-response (two-way).</span></span>  
  
 <span data-ttu-id="68561-139">**Adaptateur d’envoi WCF-NetNamedPipe**</span><span class="sxs-lookup"><span data-stu-id="68561-139">**WCF-NetNamedPipe Send Adapter**</span></span>  
  
 <span data-ttu-id="68561-140">L'adaptateur d'envoi WCF-NetNamedPipe permet d'appeler un service WCF à l'aide du contrat sans type via le transport de canal nommé.</span><span class="sxs-lookup"><span data-stu-id="68561-140">You use the WCF-NetNamedPipe send adapter to call a WCF service through the typeless contract over the named pipe transport.</span></span>  
  
 <span data-ttu-id="68561-141">Pour plus d’informations sur WCF de réception et les adaptateurs d’envoi, consultez [quelles sont les adaptateurs WCF ?](../core/what-are-the-wcf-adapters.md).</span><span class="sxs-lookup"><span data-stu-id="68561-141">For more information about WCF receive and send adapters, see [What Are the WCF Adapters?](../core/what-are-the-wcf-adapters.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68561-142">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="68561-142">See Also</span></span>  
 <span data-ttu-id="68561-143">[Configuration de l’adaptateur WCF-NetNamedPipe](../core/configuring-the-wcf-netnamedpipe-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="68561-143">[Configuring the WCF-NetNamedPipe Adapter](../core/configuring-the-wcf-netnamedpipe-adapter.md) </span></span>  
 [<span data-ttu-id="68561-144">Adaptateurs WCF</span><span class="sxs-lookup"><span data-stu-id="68561-144">WCF Adapters</span></span>](../core/wcf-adapters.md)