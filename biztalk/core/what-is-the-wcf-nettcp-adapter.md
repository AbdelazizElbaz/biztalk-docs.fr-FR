---
title: "Qu'est-ce que l'adaptateur WCF-NetTcp ? | Microsoft Docs"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: WCF-NetTcp adapters, about WCF-NetTcp adapters
ms.assetid: 94dc24df-19a1-4701-9012-59d05b0c8abd
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a741d3a4d7b7bcc80405d0fc25e37a31860523b9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="what-is-the-wcf-nettcp-adapter"></a><span data-ttu-id="9d9c3-103">Qu'est-ce que l'adaptateur WCF-NetTcp ?</span><span class="sxs-lookup"><span data-stu-id="9d9c3-103">What Is the WCF-NetTcp Adapter?</span></span>
<span data-ttu-id="9d9c3-104">L'adaptateur WCF-NetTcp permet à des ordinateurs ou à des processus connectés de communiquer au sein d'un environnement dans lequel les services et clients sont de type WCF.</span><span class="sxs-lookup"><span data-stu-id="9d9c3-104">The WCF-NetTcp adapter provides connected cross-computer or cross-process communication in an environment in which both services and clients are WCF based.</span></span> <span data-ttu-id="9d9c3-105">Il fournit un accès total aux fonctionnalités de sécurité, de fiabilité et de transaction SOAP.</span><span class="sxs-lookup"><span data-stu-id="9d9c3-105">It provides full access to SOAP security, reliability, and transaction features.</span></span> <span data-ttu-id="9d9c3-106">Cet adaptateur utilise le transport TCP et les messages ont un codage binaire.</span><span class="sxs-lookup"><span data-stu-id="9d9c3-106">This adapter uses the TCP transport, and messages have binary encoding.</span></span>  
  
 <span data-ttu-id="9d9c3-107">Le tableau suivant répertorie les caractéristiques de l'adaptateur WCF-NetTcp.</span><span class="sxs-lookup"><span data-stu-id="9d9c3-107">The following table summarizes the characteristics of the WCF-NetTcp adapter.</span></span>  
  
|<span data-ttu-id="9d9c3-108"> Description</span><span class="sxs-lookup"><span data-stu-id="9d9c3-108">Description</span></span>|<span data-ttu-id="9d9c3-109">Caractéristique</span><span class="sxs-lookup"><span data-stu-id="9d9c3-109">Characteristic</span></span>|  
|-----------------|--------------------|  
|<span data-ttu-id="9d9c3-110">Niveau d'interopérabilité</span><span class="sxs-lookup"><span data-stu-id="9d9c3-110">Interoperability level</span></span>|<span data-ttu-id="9d9c3-111">Profil .NET</span><span class="sxs-lookup"><span data-stu-id="9d9c3-111">.NET-Profile</span></span>|  
|<span data-ttu-id="9d9c3-112">Codage du message</span><span class="sxs-lookup"><span data-stu-id="9d9c3-112">Message encoding</span></span>|<span data-ttu-id="9d9c3-113">Binaire</span><span class="sxs-lookup"><span data-stu-id="9d9c3-113">Binary</span></span>|  
|<span data-ttu-id="9d9c3-114">Limite</span><span class="sxs-lookup"><span data-stu-id="9d9c3-114">Boundary</span></span>|<span data-ttu-id="9d9c3-115">Entre ordinateurs ou entre processus</span><span class="sxs-lookup"><span data-stu-id="9d9c3-115">Cross-computer or cross-process</span></span>|  
|<span data-ttu-id="9d9c3-116">Protocole de transport</span><span class="sxs-lookup"><span data-stu-id="9d9c3-116">Transport protocol</span></span>|<span data-ttu-id="9d9c3-117">TCP</span><span class="sxs-lookup"><span data-stu-id="9d9c3-117">TCP</span></span>|  
|<span data-ttu-id="9d9c3-118">Mode de sécurité</span><span class="sxs-lookup"><span data-stu-id="9d9c3-118">Security mode</span></span>|<span data-ttu-id="9d9c3-119">None, Message, Transport et TransportWithMessageCredential.</span><span class="sxs-lookup"><span data-stu-id="9d9c3-119">None, Message, Transport, and TransportWithMessageCredential.</span></span>|  
|<span data-ttu-id="9d9c3-120">Mécanisme d'authentification du client</span><span class="sxs-lookup"><span data-stu-id="9d9c3-120">Client authentication mechanism</span></span>|<span data-ttu-id="9d9c3-121">Sécurité du transport et sécurité des messages</span><span class="sxs-lookup"><span data-stu-id="9d9c3-121">Transport Security and Message Security</span></span>|  
|<span data-ttu-id="9d9c3-122">Prise en charge de WS-ReliableMessaging</span><span class="sxs-lookup"><span data-stu-id="9d9c3-122">Support for WS-ReliableMessaging</span></span>|<span data-ttu-id="9d9c3-123">Non</span><span class="sxs-lookup"><span data-stu-id="9d9c3-123">No</span></span>|  
|<span data-ttu-id="9d9c3-124">Prise en charge de WS-AtomicTransaction</span><span class="sxs-lookup"><span data-stu-id="9d9c3-124">Support for WS-AtomicTransaction</span></span>|<span data-ttu-id="9d9c3-125">Oui</span><span class="sxs-lookup"><span data-stu-id="9d9c3-125">Yes</span></span>|  
|<span data-ttu-id="9d9c3-126">Prise en charge de la messagerie unidirectionnelle</span><span class="sxs-lookup"><span data-stu-id="9d9c3-126">Support for one-way messaging</span></span>|<span data-ttu-id="9d9c3-127">Oui</span><span class="sxs-lookup"><span data-stu-id="9d9c3-127">Yes</span></span>|  
|<span data-ttu-id="9d9c3-128">Prise en charge de la messagerie bidirectionnelle</span><span class="sxs-lookup"><span data-stu-id="9d9c3-128">Support for two-way messaging</span></span>|<span data-ttu-id="9d9c3-129">Oui</span><span class="sxs-lookup"><span data-stu-id="9d9c3-129">Yes</span></span>|  
|<span data-ttu-id="9d9c3-130">Type d'hôte pour l'adaptateur de réception</span><span class="sxs-lookup"><span data-stu-id="9d9c3-130">Host type for receive adapter</span></span>|<span data-ttu-id="9d9c3-131">In-process</span><span class="sxs-lookup"><span data-stu-id="9d9c3-131">In-process</span></span>|  
|<span data-ttu-id="9d9c3-132">Type d'hôte pour l'adaptateur d'envoi</span><span class="sxs-lookup"><span data-stu-id="9d9c3-132">Host type for send adapter</span></span>|<span data-ttu-id="9d9c3-133">In-process</span><span class="sxs-lookup"><span data-stu-id="9d9c3-133">In-process</span></span>|  
  
 <span data-ttu-id="9d9c3-134">L'adaptateur WCF-NetTcp est constitué de deux adaptateurs : un adaptateur de réception et un adaptateur d'envoi.</span><span class="sxs-lookup"><span data-stu-id="9d9c3-134">The WCF-NetTcp adapter consists of two adapters—a receive adapter and a send adapter.</span></span>  
  
 <span data-ttu-id="9d9c3-135">**Adaptateur de réception WCF-NetTcp**</span><span class="sxs-lookup"><span data-stu-id="9d9c3-135">**WCF-NetTcp Receive Adapter**</span></span>  
  
 <span data-ttu-id="9d9c3-136">L'adaptateur de réception WCF-NetTcp permet de recevoir des demandes de service WCF via le protocole TCP.</span><span class="sxs-lookup"><span data-stu-id="9d9c3-136">You use the WCF-NetTcp receive adapter to receive WCF service requests through the TCP protocol.</span></span> <span data-ttu-id="9d9c3-137">Un emplacement de réception qui utilise l'adaptateur de réception WCF-NetTcp peut être configuré comme emplacement de réception unidirectionnel ou de requête-réponse (bidirectionnel).</span><span class="sxs-lookup"><span data-stu-id="9d9c3-137">A receive location that uses the WCF-NetTcp receive adapter can be configured as one-way or request-response (two-way).</span></span>  
  
 <span data-ttu-id="9d9c3-138">**Adaptateur d’envoi WCF-NetTcp**</span><span class="sxs-lookup"><span data-stu-id="9d9c3-138">**WCF-NetTcp Send Adapter**</span></span>  
  
 <span data-ttu-id="9d9c3-139">L'adaptateur d'envoi WCF-NetTcp permet d'appeler un service WCF à l'aide du contrat sans type via le protocole TCP.</span><span class="sxs-lookup"><span data-stu-id="9d9c3-139">You use the WCF-NetTcp send adapter to call a WCF service through the typeless contract by using the TCP protocol.</span></span>  
  
 <span data-ttu-id="9d9c3-140">Pour plus d’informations sur WCF de réception et les adaptateurs d’envoi, consultez [quelles sont les adaptateurs WCF ?](../core/what-are-the-wcf-adapters.md).</span><span class="sxs-lookup"><span data-stu-id="9d9c3-140">For more information about WCF receive and send adapters, see [What Are the WCF Adapters?](../core/what-are-the-wcf-adapters.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d9c3-141">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9d9c3-141">See Also</span></span>  
 <span data-ttu-id="9d9c3-142">[Configuration de l’adaptateur WCF-NetTcp](../core/configuring-the-wcf-nettcp-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="9d9c3-142">[Configuring the WCF-NetTcp Adapter](../core/configuring-the-wcf-nettcp-adapter.md) </span></span>  
 [<span data-ttu-id="9d9c3-143">Adaptateurs WCF</span><span class="sxs-lookup"><span data-stu-id="9d9c3-143">WCF Adapters</span></span>](../core/wcf-adapters.md)