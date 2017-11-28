---
title: "Définition de l’exécution du Service d’Orchestration personnalisée à l’aide d’itinéraires | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6089169d-2fa1-4f81-afe1-db9d90a10382
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e40c85daae67928e6fbe3c20e9c6dd61f3634bf0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="defining-custom-orchestration-service-execution-using-itineraries"></a><span data-ttu-id="fe457-102">Définition de l’exécution du Service d’Orchestration personnalisée à l’aide d’itinéraires</span><span class="sxs-lookup"><span data-stu-id="fe457-102">Defining Custom Orchestration Service Execution Using Itineraries</span></span>
<span data-ttu-id="fe457-103">Dans ce cas de figure, un message envoyé pour traitement contient un en-tête SOAP d’itinéraire qui décrit la liste des services d’exécuter et de leurs besoins en résolution.</span><span class="sxs-lookup"><span data-stu-id="fe457-103">In this use case, a message submitted for processing contains an itinerary SOAP header that describes the list of services to execute and their resolution requirements.</span></span> <span data-ttu-id="fe457-104">L’itinéraire spécifie un ou plusieurs orchestrations personnalisées ou les processus via lequel le message sera transmis au cours du cycle de traitement.</span><span class="sxs-lookup"><span data-stu-id="fe457-104">The itinerary specifies one or more custom orchestrations or processes through which the message will pass during the processing cycle.</span></span> <span data-ttu-id="fe457-105">Orchestrations personnalisées ont un contrôle total de l’itinéraire et les autres propriétés personnalisées exposées dans le contexte du message.</span><span class="sxs-lookup"><span data-stu-id="fe457-105">Custom orchestrations have full control of the itinerary and other custom properties exposed in the message context.</span></span> <span data-ttu-id="fe457-106">Si vous le souhaitez, l’itinéraire peut contenir des informations de résolution dynamique qui détermine les spécifications de transformation et de points de terminaison pour le message.</span><span class="sxs-lookup"><span data-stu-id="fe457-106">Optionally, the itinerary can contain dynamic resolution information that determines transformation requirements and endpoints for the message.</span></span> <span data-ttu-id="fe457-107">La figure 1 illustre une vue schématique du processus.</span><span class="sxs-lookup"><span data-stu-id="fe457-107">Figure 1 illustrates a schematic view of the process.</span></span>  
  
 <span data-ttu-id="fe457-108">![Définition d’une Orchestration personnalisée](../esb-toolkit/media/ch3-definingcustomorchestration.gif "Ch3-DefiningCustomOrchestration")</span><span class="sxs-lookup"><span data-stu-id="fe457-108">![Defining Custom Orchestration](../esb-toolkit/media/ch3-definingcustomorchestration.gif "Ch3-DefiningCustomOrchestration")</span></span>  
  
 <span data-ttu-id="fe457-109">**Figure 1**</span><span class="sxs-lookup"><span data-stu-id="fe457-109">**Figure 1**</span></span>  
  
 <span data-ttu-id="fe457-110">**Définition de l’exécution du service d’orchestration personnalisée à l’aide d’itinéraires**</span><span class="sxs-lookup"><span data-stu-id="fe457-110">**Defining custom orchestration service execution using itineraries**</span></span>  
  
 <span data-ttu-id="fe457-111">L’exemple de feuille de route rampe d’entrée fourni avec le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] illustre ce cas de figure.</span><span class="sxs-lookup"><span data-stu-id="fe457-111">The Itinerary On-Ramp sample included with the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] demonstrates this use case.</span></span> <span data-ttu-id="fe457-112">Il montre comment créer des itinéraires qui contiennent la résolution, le routage, et obtenir des instructions de l’appel de service comme une série d’étapes d’itinéraire qui définissent comment le ESB et [!INCLUDE[prague](../includes/prague-md.md)] traite le message d’entrée.</span><span class="sxs-lookup"><span data-stu-id="fe457-112">It shows how to create itineraries that contain resolution, routing, and service invocation instructions as a series of itinerary steps that define how the ESB and [!INCLUDE[prague](../includes/prague-md.md)] will process the input message.</span></span> <span data-ttu-id="fe457-113">Unidirectionnel et exemples de requête-réponse.</span><span class="sxs-lookup"><span data-stu-id="fe457-113">One-way and request-response samples are included.</span></span>  
  
 <span data-ttu-id="fe457-114">Pour plus d’informations, consultez [l’installation et l’exécution de l’exemple de rampe d’entrée d’itinéraire](../esb-toolkit/installing-and-running-the-itinerary-on-ramp-sample.md).</span><span class="sxs-lookup"><span data-stu-id="fe457-114">For more information, see [Installing and Running the Itinerary On-Ramp Sample](../esb-toolkit/installing-and-running-the-itinerary-on-ramp-sample.md).</span></span>