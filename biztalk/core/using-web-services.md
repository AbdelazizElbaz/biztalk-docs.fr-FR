---
title: Utilisation des Services Web | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Web services
- Web services, about Web services
- orchestrations, Web services
- Web services, orchestrations
ms.assetid: a54261e3-d8ef-4770-8d9a-147685846051
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 236acb42c010effe5c3d45cde1daaf9a7097ede5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="using-web-services"></a><span data-ttu-id="ac680-102">Utilisation des Services Web</span><span class="sxs-lookup"><span data-stu-id="ac680-102">Using Web Services</span></span>
<span data-ttu-id="ac680-103">Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] assure la prise en charge intégrée des services Web.</span><span class="sxs-lookup"><span data-stu-id="ac680-103">Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] provides built-in support for Web services.</span></span> <span data-ttu-id="ac680-104">BizTalk Server permet la réutilisation et l'agrégation de l'ensemble de vos services web existants dans vos orchestrations.</span><span class="sxs-lookup"><span data-stu-id="ac680-104">BizTalk Server enables the reuse and aggregation of all your existing Web services within your orchestrations.</span></span> <span data-ttu-id="ac680-105">Vous pouvez également publier (exposer) vos orchestrations en tant que services Web afin de séparer la logique du service Web de celle du processus d'entreprise.</span><span class="sxs-lookup"><span data-stu-id="ac680-105">You can also publish (expose) your orchestrations as Web services to separate the Web service logic from the business process logic.</span></span>  
  
 <span data-ttu-id="ac680-106">BizTalk Server assure la prise en charge des adaptateurs natifs dans les services Web.</span><span class="sxs-lookup"><span data-stu-id="ac680-106">BizTalk Server implements support for native adapters in Web services.</span></span> <span data-ttu-id="ac680-107">Une telle prise en charge offre une évolutivité, une tolérance aux pannes et des capacités de suivi pour vos services sans que vous ayez besoin d'écrire du code.</span><span class="sxs-lookup"><span data-stu-id="ac680-107">Native adapter support provides scalability, fault tolerance, and tracking capabilities for Web services without writing a single line of code.</span></span> <span data-ttu-id="ac680-108">Pour plus d’informations sur l’adaptateur SOAP, consultez [adaptateur SOAP](../core/soap-adapter.md).</span><span class="sxs-lookup"><span data-stu-id="ac680-108">For information about the SOAP adapter, see [SOAP Adapter](../core/soap-adapter.md).</span></span>  
  
 <span data-ttu-id="ac680-109">La prise en charge des services Web dans BizTalk Server se répartissent en deux catégories : consommation ou l’appel de services Web et la publication ou la création de services Web.</span><span class="sxs-lookup"><span data-stu-id="ac680-109">The Web services support in BizTalk Server falls into two categories: consuming or calling Web services and publishing or creating Web services.</span></span>  
  
 <span data-ttu-id="ac680-110">Avant d’utiliser ou publier un service Web, vous devez avoir une compréhension des services Web XML dans ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="ac680-110">Before you consume or publish a Web service, you should have an understanding of XML Web services in ASP.NET.</span></span> <span data-ttu-id="ac680-111">Pour plus d’informations sur les principes de base des services Web XML, consultez l’article « XML Web Services Basics » à [http://go.microsoft.com/fwlink/?LinkId=193057](http://go.microsoft.com/fwlink/?LinkId=193057).</span><span class="sxs-lookup"><span data-stu-id="ac680-111">For information about the basics of XML Web services, see the article "XML Web Services Basics" at [http://go.microsoft.com/fwlink/?LinkId=193057](http://go.microsoft.com/fwlink/?LinkId=193057).</span></span>  
  
 <span data-ttu-id="ac680-112">**Utilisation de services Web**</span><span class="sxs-lookup"><span data-stu-id="ac680-112">**Consuming Web services**</span></span>  
  
 <span data-ttu-id="ac680-113">Vous pouvez utiliser (appeler) les services Web à partir d'une orchestration.</span><span class="sxs-lookup"><span data-stu-id="ac680-113">You can consume (call) Web services from within an orchestration.</span></span> <span data-ttu-id="ac680-114">Vous pouvez regrouper plusieurs services Web dans une seule orchestration pour achever un processus d'entreprise dans sa totalité.</span><span class="sxs-lookup"><span data-stu-id="ac680-114">You can aggregate several Web services into single orchestration to complete an entire business process.</span></span>  
  
 <span data-ttu-id="ac680-115">**Publication de services Web**</span><span class="sxs-lookup"><span data-stu-id="ac680-115">**Publishing Web services**</span></span>  
  
 <span data-ttu-id="ac680-116">Vous pouvez publier des services Web à l'aide de l'Assistant Publication de services Web BizTalk.</span><span class="sxs-lookup"><span data-stu-id="ac680-116">You can publish Web services using the BizTalk Web Services Publishing Wizard.</span></span> <span data-ttu-id="ac680-117">Les orchestrations et les adaptateurs d'envoi peuvent utiliser ces services Web publiés.</span><span class="sxs-lookup"><span data-stu-id="ac680-117">Orchestrations and send adapters can use these published Web services.</span></span>  
  
 <span data-ttu-id="ac680-118">**Utilisation des en-têtes SOAP**</span><span class="sxs-lookup"><span data-stu-id="ac680-118">**Using SOAP headers**</span></span>  
  
 <span data-ttu-id="ac680-119">BizTalk Server prend en charge les en-têtes SOAP définis et inconnus.</span><span class="sxs-lookup"><span data-stu-id="ac680-119">BizTalk Server provides support for defined and unknown SOAP headers.</span></span> <span data-ttu-id="ac680-120">BizTalk Server crée une propriété de contexte pour chaque en-tête SOAP défini dans le service Web.</span><span class="sxs-lookup"><span data-stu-id="ac680-120">BizTalk Server creates a context property for each defined SOAP header in the Web service.</span></span>  
  
 <span data-ttu-id="ac680-121">**Normes de Services Web**</span><span class="sxs-lookup"><span data-stu-id="ac680-121">**Web Services standards**</span></span>  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="ac680-122"> doit fonctionner avec toutes les normes de services web lors de l'envoi et de la réception.</span><span class="sxs-lookup"><span data-stu-id="ac680-122"> should work with any Web Services standards when sending and receiving.</span></span> <span data-ttu-id="ac680-123">Les normes n'ont pas toutes été testées.</span><span class="sxs-lookup"><span data-stu-id="ac680-123">Not all standards have been tested.</span></span> <span data-ttu-id="ac680-124">En règle générale, les normes prises en charge par WCF le sont également par [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ac680-124">Typically, the standards supported by WCF are also supported by [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="ac680-125">Voici quelques exemples de normes :</span><span class="sxs-lookup"><span data-stu-id="ac680-125">Sample standards include:</span></span>  
  
-   <span data-ttu-id="ac680-126">WS-ReliableMessaging</span><span class="sxs-lookup"><span data-stu-id="ac680-126">WS-ReliableMessaging</span></span>  
  
-   <span data-ttu-id="ac680-127">WS-Security</span><span class="sxs-lookup"><span data-stu-id="ac680-127">WS-Security</span></span>  
  
-   <span data-ttu-id="ac680-128">WS-SecureConversation</span><span class="sxs-lookup"><span data-stu-id="ac680-128">WS-SecureConversation</span></span>  
  
-   <span data-ttu-id="ac680-129">WS-Trust</span><span class="sxs-lookup"><span data-stu-id="ac680-129">WS-Trust</span></span>  
  
-   <span data-ttu-id="ac680-130">WS-Federation</span><span class="sxs-lookup"><span data-stu-id="ac680-130">WS-Federation</span></span>  
  
-   <span data-ttu-id="ac680-131">WS-Addressing</span><span class="sxs-lookup"><span data-stu-id="ac680-131">WS-Addressing</span></span>  
  
-   <span data-ttu-id="ac680-132">WS-Policy</span><span class="sxs-lookup"><span data-stu-id="ac680-132">WS-Policy</span></span>  
  
-   <span data-ttu-id="ac680-133">WS-MetadataExchange</span><span class="sxs-lookup"><span data-stu-id="ac680-133">WS-MetadataExchange</span></span>  
  
-   <span data-ttu-id="ac680-134">WS-Coordination</span><span class="sxs-lookup"><span data-stu-id="ac680-134">WS-Coordination</span></span>  
  
-   <span data-ttu-id="ac680-135">WS-Atomic</span><span class="sxs-lookup"><span data-stu-id="ac680-135">WS-Atomic</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ac680-136">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="ac680-136">In This Section</span></span>  
  
-   [<span data-ttu-id="ac680-137">Utilisation de Services Web</span><span class="sxs-lookup"><span data-stu-id="ac680-137">Consuming Web Services</span></span>](../core/consuming-web-services.md)  
  
-   [<span data-ttu-id="ac680-138">Publication de Services Web</span><span class="sxs-lookup"><span data-stu-id="ac680-138">Publishing Web Services</span></span>](../core/publishing-web-services.md)  
  
-   [<span data-ttu-id="ac680-139">Utilisation des en-têtes SOAP</span><span class="sxs-lookup"><span data-stu-id="ac680-139">Using SOAP Headers</span></span>](../core/using-soap-headers.md)