---
title: "Qu'est-ce que l'adaptateur WCF-WSHttp ? | Microsoft Docs"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: WCF-WSHttp adapters, about WCF-WSHttp adapters
ms.assetid: 183a19e3-10b1-403f-b274-34a441e774d1
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: eb5d244dcfe26cf10bc4ae10c63374eef0824444
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="what-is-the-wcf-wshttp-adapter"></a><span data-ttu-id="b3c2f-103">Qu'est-ce que l'adaptateur WCF-WSHttp ?</span><span class="sxs-lookup"><span data-stu-id="b3c2f-103">What Is the WCF-WSHttp Adapter?</span></span>
<span data-ttu-id="b3c2f-104">L'adaptateur WCF-WSHttp permet d'établir une communication entre ordinateurs avec les services et clients qui peuvent comprendre les normes de service Web de nouvelle génération, via le transport HTTP ou HTTPS avec le codage Texte ou MTOM (Message Transmission Optimization Mechanism).</span><span class="sxs-lookup"><span data-stu-id="b3c2f-104">You can use the WCF-WSHttp adapter to do cross-computer communication with services and clients that can understand the next-generation Web service standards, using either the HTTP or HTTPS transport with text or Message Transmission Optimization Mechanism (MTOM) encoding.</span></span> <span data-ttu-id="b3c2f-105">Il fournit un accès complet aux fonctionnalités de sécurité, de fiabilité et de transaction SOAP.</span><span class="sxs-lookup"><span data-stu-id="b3c2f-105">The WCF-WSHttp adapter provides full access to the SOAP security, reliability, and transaction features.</span></span>  
  
 <span data-ttu-id="b3c2f-106">Le tableau suivant répertorie les caractéristiques de l'adaptateur WCF-WSHttp.</span><span class="sxs-lookup"><span data-stu-id="b3c2f-106">The following table summarizes the characteristics of the WCF-WSHttp adapter.</span></span>  
  
|<span data-ttu-id="b3c2f-107"> Description</span><span class="sxs-lookup"><span data-stu-id="b3c2f-107">Description</span></span>|<span data-ttu-id="b3c2f-108">Caractéristique</span><span class="sxs-lookup"><span data-stu-id="b3c2f-108">Characteristic</span></span>|  
|-----------------|--------------------|  
|<span data-ttu-id="b3c2f-109">Niveau d'interopérabilité</span><span class="sxs-lookup"><span data-stu-id="b3c2f-109">Interoperability level</span></span>|<span data-ttu-id="b3c2f-110">WS-Profile</span><span class="sxs-lookup"><span data-stu-id="b3c2f-110">WS-Profile</span></span>|  
|<span data-ttu-id="b3c2f-111">Codage du message</span><span class="sxs-lookup"><span data-stu-id="b3c2f-111">Message encoding</span></span>|<span data-ttu-id="b3c2f-112">Texte ou MTOM</span><span class="sxs-lookup"><span data-stu-id="b3c2f-112">Text or MTOM</span></span>|  
|<span data-ttu-id="b3c2f-113">Limite</span><span class="sxs-lookup"><span data-stu-id="b3c2f-113">Boundary</span></span>|<span data-ttu-id="b3c2f-114">Entre ordinateurs</span><span class="sxs-lookup"><span data-stu-id="b3c2f-114">Cross-computer</span></span>|  
|<span data-ttu-id="b3c2f-115">Protocole de transport</span><span class="sxs-lookup"><span data-stu-id="b3c2f-115">Transport protocol</span></span>|<span data-ttu-id="b3c2f-116">HTTP ou HTTPS</span><span class="sxs-lookup"><span data-stu-id="b3c2f-116">HTTP or HTTPS</span></span>|  
|<span data-ttu-id="b3c2f-117">Mode de sécurité</span><span class="sxs-lookup"><span data-stu-id="b3c2f-117">Security mode</span></span>|<span data-ttu-id="b3c2f-118">None, Message, Transport et TransportWithMessageCredential.</span><span class="sxs-lookup"><span data-stu-id="b3c2f-118">None, Message, Transport, and TransportWithMessageCredential.</span></span>|  
|<span data-ttu-id="b3c2f-119">Mécanisme d'authentification du client</span><span class="sxs-lookup"><span data-stu-id="b3c2f-119">Client authentication mechanism</span></span>|<span data-ttu-id="b3c2f-120">Sécurité du transport et sécurité des messages</span><span class="sxs-lookup"><span data-stu-id="b3c2f-120">Transport Security and Message Security</span></span>|  
|<span data-ttu-id="b3c2f-121">Prise en charge de WS-ReliableMessaging</span><span class="sxs-lookup"><span data-stu-id="b3c2f-121">Support for WS-ReliableMessaging</span></span>|<span data-ttu-id="b3c2f-122">Non</span><span class="sxs-lookup"><span data-stu-id="b3c2f-122">No</span></span>|  
|<span data-ttu-id="b3c2f-123">Prise en charge de WS-AtomicTransaction</span><span class="sxs-lookup"><span data-stu-id="b3c2f-123">Support for WS-AtomicTransaction</span></span>|<span data-ttu-id="b3c2f-124">Oui</span><span class="sxs-lookup"><span data-stu-id="b3c2f-124">Yes</span></span>|  
|<span data-ttu-id="b3c2f-125">Prise en charge de la messagerie unidirectionnelle</span><span class="sxs-lookup"><span data-stu-id="b3c2f-125">Support for one-way messaging</span></span>|<span data-ttu-id="b3c2f-126">Oui</span><span class="sxs-lookup"><span data-stu-id="b3c2f-126">Yes</span></span>|  
|<span data-ttu-id="b3c2f-127">Prise en charge de la messagerie bidirectionnelle</span><span class="sxs-lookup"><span data-stu-id="b3c2f-127">Support for two-way messaging</span></span>|<span data-ttu-id="b3c2f-128">Oui</span><span class="sxs-lookup"><span data-stu-id="b3c2f-128">Yes</span></span>|  
|<span data-ttu-id="b3c2f-129">Type d'hôte pour l'adaptateur de réception</span><span class="sxs-lookup"><span data-stu-id="b3c2f-129">Host type for receive adapter</span></span>|<span data-ttu-id="b3c2f-130">Isolé</span><span class="sxs-lookup"><span data-stu-id="b3c2f-130">Isolated</span></span>|  
|<span data-ttu-id="b3c2f-131">Type d'hôte pour l'adaptateur d'envoi</span><span class="sxs-lookup"><span data-stu-id="b3c2f-131">Host type for send adapter</span></span>|<span data-ttu-id="b3c2f-132">In-process</span><span class="sxs-lookup"><span data-stu-id="b3c2f-132">In-process</span></span>|  
  
 <span data-ttu-id="b3c2f-133">L'adaptateur WCF-WSHttp est constitué de deux adaptateurs : un adaptateur de réception et un adaptateur d'envoi.</span><span class="sxs-lookup"><span data-stu-id="b3c2f-133">The WCF-WSHttp adapter consists of two adapters—a receive adapter and a send adapter.</span></span>  
  
 <span data-ttu-id="b3c2f-134">**Adaptateur de réception WCF-WSHttp**</span><span class="sxs-lookup"><span data-stu-id="b3c2f-134">**WCF-WSHttp Receive Adapter**</span></span>  
  
 <span data-ttu-id="b3c2f-135">L'adaptateur de réception WCF-WSHttp permet de recevoir des demandes de service WCF via le protocole HTTP ou HTTPS.</span><span class="sxs-lookup"><span data-stu-id="b3c2f-135">You use the WCF-WSHttp receive adapter to receive WCF service requests through the HTTP or HTTPS protocol.</span></span> <span data-ttu-id="b3c2f-136">Un emplacement de réception qui utilise l'adaptateur de réception WCF-WSHttp peut être configuré comme emplacement de réception unidirectionnel ou de requête-réponse (bidirectionnel).</span><span class="sxs-lookup"><span data-stu-id="b3c2f-136">A receive location that uses the WCF-WSHttp receive adapter can be configured as one-way or request-response (two-way).</span></span>  
  
 <span data-ttu-id="b3c2f-137">**Adaptateur d’envoi WCF-WSHttp**</span><span class="sxs-lookup"><span data-stu-id="b3c2f-137">**WCF-WSHttp Send Adapter**</span></span>  
  
 <span data-ttu-id="b3c2f-138">L'adaptateur d'envoi WCF-WSHttp permet d'appeler un service WCF à l'aide du contrat sans type via le protocole HTTP ou HTTPS.</span><span class="sxs-lookup"><span data-stu-id="b3c2f-138">You use the WCF-WSHttp send adapter to call a WCF service through the typeless contract by using the HTTP or HTTPS protocol.</span></span>  
  
 <span data-ttu-id="b3c2f-139">Pour plus d’informations sur WCF de réception et les adaptateurs d’envoi, consultez [quelles sont les adaptateurs WCF ?](../core/what-are-the-wcf-adapters.md).</span><span class="sxs-lookup"><span data-stu-id="b3c2f-139">For more information about WCF receive and send adapters, see [What Are the WCF Adapters?](../core/what-are-the-wcf-adapters.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3c2f-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b3c2f-140">See Also</span></span>  
 <span data-ttu-id="b3c2f-141">[Configuration de l’adaptateur WCF-WSHttp](../core/configuring-the-wcf-wshttp-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="b3c2f-141">[Configuring the WCF-WSHttp Adapter](../core/configuring-the-wcf-wshttp-adapter.md) </span></span>  
 [<span data-ttu-id="b3c2f-142">Adaptateurs WCF</span><span class="sxs-lookup"><span data-stu-id="b3c2f-142">WCF Adapters</span></span>](../core/wcf-adapters.md)