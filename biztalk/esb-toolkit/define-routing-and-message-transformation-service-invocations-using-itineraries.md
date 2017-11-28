---
title: "Définition du routage et d’appels de Service de Transformation à l’aide d’itinéraires de Message | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e6f2448e-a5a7-496c-86d3-47f12e6f1251
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 975c830f73e0de362b25f312a8d41c4b15368cfd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="defining-routing-and-message-transformation-service-invocations-using-itineraries"></a><span data-ttu-id="151fc-102">Définition de routage et d’appels de Service de Transformation de Message à l’aide d’itinéraires</span><span class="sxs-lookup"><span data-stu-id="151fc-102">Defining Routing and Message Transformation Service Invocations Using Itineraries</span></span>
<span data-ttu-id="151fc-103">Dans ce cas de figure, un message envoyé pour traitement contient un en-tête SOAP d’itinéraire qui décrit la liste des services d’exécuter et de leurs besoins en résolution.</span><span class="sxs-lookup"><span data-stu-id="151fc-103">In this use case, a message submitted for processing contains an itinerary SOAP header that describes the list of services to execute and their resolution requirements.</span></span> <span data-ttu-id="151fc-104">Plus précisément, une transformation et le service de routage sont définis, chacun éventuellement nécessitant une résolution d’une recherche Universal Description, Discovery et Integration (UDDI), stratégie de moteur de règles d’entreprise, XML Path Language (XPath) ou statique.</span><span class="sxs-lookup"><span data-stu-id="151fc-104">Specifically, a transformation and routing service are defined, each optionally requiring resolution through a Universal Description, Discovery, and Integration (UDDI), Business Rules Engine Policy, XML Path Language (XPath), or STATIC lookup.</span></span> <span data-ttu-id="151fc-105">Ce cas de figure peut être étendu en ajoutant d’autres services à l’itinéraire au moment de la publication des messages.</span><span class="sxs-lookup"><span data-stu-id="151fc-105">This use case can be extended by adding other services to the itinerary at the time of message publication.</span></span>  
  
 <span data-ttu-id="151fc-106">Le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] propose deux types d’écarts d’itinéraire : ceux qui prennent en charge la communication unidirectionnelle et ceux qui prennent en charge les scénarios de requête-réponse.</span><span class="sxs-lookup"><span data-stu-id="151fc-106">The [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] provides two types of itinerary on-ramps: those that support one-way communication and those that support request-response scenarios.</span></span> <span data-ttu-id="151fc-107">Car le mécanisme de résolution dynamique peut utiliser des informations dans la feuille de route pour rechercher des points de terminaison ou de la liaison dynamique aux points de terminaison, il n’est pas nécessaire pour Microsoft BizTalk Server contenir les informations de routage de point de terminaison spécifique.</span><span class="sxs-lookup"><span data-stu-id="151fc-107">Because the dynamic resolution mechanism can use information in the itinerary to look up endpoints or bind dynamically to endpoints, there is no requirement for Microsoft BizTalk Server to contain specific endpoint routing details.</span></span> <span data-ttu-id="151fc-108">La figure 1 illustre une vue schématique du processus.</span><span class="sxs-lookup"><span data-stu-id="151fc-108">Figure 1 illustrates a schematic view of the process.</span></span>  
  
 <span data-ttu-id="151fc-109">![Définir le service de routage appel](../esb-toolkit/media/ch3-definingroutingserviceinvocation.gif "Ch3-DefiningRoutingServiceInvocation")</span><span class="sxs-lookup"><span data-stu-id="151fc-109">![Defining Routing service Invocation](../esb-toolkit/media/ch3-definingroutingserviceinvocation.gif "Ch3-DefiningRoutingServiceInvocation")</span></span>  
  
 <span data-ttu-id="151fc-110">**Figure 1**</span><span class="sxs-lookup"><span data-stu-id="151fc-110">**Figure 1**</span></span>  
  
 <span data-ttu-id="151fc-111">**Définition de message et routage des appels de service de transformation à l’aide d’itinéraires**</span><span class="sxs-lookup"><span data-stu-id="151fc-111">**Defining routing and message transformation service invocations using itineraries**</span></span>  
  
 <span data-ttu-id="151fc-112">L’exemple de feuille de route rampe d’entrée fourni avec le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] illustre ce cas de figure.</span><span class="sxs-lookup"><span data-stu-id="151fc-112">The Itinerary On-Ramp sample included with the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] demonstrates this use case.</span></span> <span data-ttu-id="151fc-113">Il montre comment créer des itinéraires qui contiennent la résolution, le routage, et obtenir des instructions de l’appel de service comme une série d’étapes d’itinéraire qui définissent comment les [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] et BizTalk Server traite le message à l’aide de la publication-s’abonner à des fonctionnalités de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="151fc-113">It shows how to create itineraries that contain resolution, routing, and service invocation instructions as a series of itinerary steps that define how the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] and BizTalk Server will process the message using the publish-subscribe functionality of BizTalk Server.</span></span> <span data-ttu-id="151fc-114">Unidirectionnel et exemples de requête-réponse.</span><span class="sxs-lookup"><span data-stu-id="151fc-114">One-way and request-response samples are included.</span></span>  
  
 <span data-ttu-id="151fc-115">Pour plus d’informations, consultez [l’installation et l’exécution de l’exemple de rampe d’entrée d’itinéraire](../esb-toolkit/installing-and-running-the-itinerary-on-ramp-sample.md).</span><span class="sxs-lookup"><span data-stu-id="151fc-115">For more information, see [Installing and Running the Itinerary On-Ramp Sample](../esb-toolkit/installing-and-running-the-itinerary-on-ramp-sample.md).</span></span>