---
title: "Définition du routage et de Transformation via plusieurs Orchestrations à l’aide d’itinéraires des messages | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 63141b83-798e-40d0-908d-6b7649923e69
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1c5a87b06700794dca6c4aae9588c3068b98d995
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="defining-routing-and-message-transformation-through-multiple-orchestrations-using-itineraries"></a><span data-ttu-id="41744-102">Définition de routage et de Transformation des messages via plusieurs Orchestrations à l’aide d’itinéraires</span><span class="sxs-lookup"><span data-stu-id="41744-102">Defining Routing and Message Transformation Through Multiple Orchestrations Using Itineraries</span></span>
<span data-ttu-id="41744-103">Dans ce cas de figure, un message envoyé pour traitement contient un en-tête SOAP d’itinéraire qui décrit la liste des services d’exécuter et de leurs besoins en résolution.</span><span class="sxs-lookup"><span data-stu-id="41744-103">In this use case, a message submitted for processing contains an itinerary SOAP header that describes the list of services to execute and their resolution requirements.</span></span> <span data-ttu-id="41744-104">L’itinéraire spécifie une ou plusieurs orchestrations Microsoft BizTalk Server par le biais duquel le message sera transmis au cours du cycle de traitement.</span><span class="sxs-lookup"><span data-stu-id="41744-104">The itinerary specifies one or more Microsoft BizTalk Server orchestrations through which the message will pass during the processing cycle.</span></span> <span data-ttu-id="41744-105">Si vous le souhaitez, l’itinéraire peut contenir des informations de routage dynamique permet de déterminer les points de terminaison ou des spécifications de transformation pour le message.</span><span class="sxs-lookup"><span data-stu-id="41744-105">Optionally, the itinerary can contain dynamic routing information used to determine endpoints or transformation requirements for the message.</span></span> <span data-ttu-id="41744-106">La figure 1 illustre une vue schématique du processus.</span><span class="sxs-lookup"><span data-stu-id="41744-106">Figure 1 illustrates a schematic view of the process.</span></span>  
  
 <span data-ttu-id="41744-107">![Définition du routage de plusieurs Orchestrations](../esb-toolkit/media/ch3-definingroutingmultipleorchestrations.gif "Ch3-DefiningRoutingMultipleOrchestrations")</span><span class="sxs-lookup"><span data-stu-id="41744-107">![Defining Routing Multiple Orchestrations](../esb-toolkit/media/ch3-definingroutingmultipleorchestrations.gif "Ch3-DefiningRoutingMultipleOrchestrations")</span></span>  
  
 <span data-ttu-id="41744-108">**Figure 1**</span><span class="sxs-lookup"><span data-stu-id="41744-108">**Figure 1**</span></span>  
  
 <span data-ttu-id="41744-109">**Définition de transformation de routage et le message via plusieurs orchestrations à l’aide d’itinéraires**</span><span class="sxs-lookup"><span data-stu-id="41744-109">**Defining routing and message transformation through multiple orchestrations using itineraries**</span></span>  
  
 <span data-ttu-id="41744-110">L’exemple de feuille de route rampe d’entrée fourni avec le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] illustre ce cas de figure.</span><span class="sxs-lookup"><span data-stu-id="41744-110">The Itinerary On-Ramp sample included with the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] demonstrates this use case.</span></span> <span data-ttu-id="41744-111">Il montre comment créer des itinéraires qui contiennent la résolution, le routage, et obtenir des instructions de l’appel de service comme une série d’étapes d’itinéraire qui définissent comment les [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] et BizTalk Server traite le message d’entrée.</span><span class="sxs-lookup"><span data-stu-id="41744-111">It shows how to create itineraries that contain resolution, routing, and service invocation instructions as a series of itinerary steps that define how the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] and BizTalk Server will process the input message.</span></span> <span data-ttu-id="41744-112">Unidirectionnel et exemples de requête-réponse.</span><span class="sxs-lookup"><span data-stu-id="41744-112">One-way and request-response samples are included.</span></span>  
  
 <span data-ttu-id="41744-113">Pour plus d’informations, consultez [l’installation et l’exécution de l’exemple de rampe d’entrée d’itinéraire](../esb-toolkit/installing-and-running-the-itinerary-on-ramp-sample.md).</span><span class="sxs-lookup"><span data-stu-id="41744-113">For more information, see [Installing and Running the Itinerary On-Ramp Sample](../esb-toolkit/installing-and-running-the-itinerary-on-ramp-sample.md).</span></span>