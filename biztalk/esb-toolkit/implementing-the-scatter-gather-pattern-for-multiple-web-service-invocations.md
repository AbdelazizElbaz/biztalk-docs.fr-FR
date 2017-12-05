---
title: "Implémentation du modèle de ventilation-regroupement pour plusieurs appels de Service Web | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 912512a4-9649-40df-bb82-b8f4b85c8ca6
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2682418922c17fd4c6fbe8a6bffbac51051f7841
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="implementing-the-scatter-gather-pattern-for-multiple-web-service-invocations"></a><span data-ttu-id="434c8-102">Implémentation du modèle de ventilation-regroupement pour plusieurs appels de Service Web</span><span class="sxs-lookup"><span data-stu-id="434c8-102">Implementing the Scatter-Gather Pattern for Multiple Web Service Invocations</span></span>
<span data-ttu-id="434c8-103">Dans ce cas de figure, un message contient une étape de service d’itinéraire qui spécifie plusieurs services externes qui doivent accéder à BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="434c8-103">In this use case, a message contains an itinerary service step that specifies more than one external service that BizTalk Server should access.</span></span> <span data-ttu-id="434c8-104">Il utilise la résolution dynamique pour déterminer les emplacements de service et mappe les points de terminaison et de n’importe quel BizTalk Service facultatif pour la transformation des données retournées.</span><span class="sxs-lookup"><span data-stu-id="434c8-104">It uses dynamic resolution to determine service locations and endpoints and any optional BizTalk Service maps for transforming the returned data.</span></span> <span data-ttu-id="434c8-105">L’orchestration qui implémente ce service effectue la transformation et des appels, et tous les appels de service se produisent de façon asynchrone.</span><span class="sxs-lookup"><span data-stu-id="434c8-105">The orchestration implementing this service performs the transformation and invocations, and all service invocations occur asynchronously.</span></span> <span data-ttu-id="434c8-106">Une fois que tous les appels de service terminé, le service d’itinéraire regroupe des réponses dans un message de réponse unique et envoie le message au client via un point de terminaison affecté dynamiquement.</span><span class="sxs-lookup"><span data-stu-id="434c8-106">After all service invocations complete, the itinerary service aggregates the responses into a single response message and sends the message to the client through a dynamically assigned endpoint.</span></span> <span data-ttu-id="434c8-107">La figure 1 illustre ce cas de figure.</span><span class="sxs-lookup"><span data-stu-id="434c8-107">Figure 1 illustrates this use case.</span></span>  
  
 <span data-ttu-id="434c8-108">![Nuage de points de mise en œuvre de rassembler modèle](../esb-toolkit/media/ch3-implementingscatter.gif "Ch3-ImplementingScatter")</span><span class="sxs-lookup"><span data-stu-id="434c8-108">![Implementing Scatter Gather Pattern](../esb-toolkit/media/ch3-implementingscatter.gif "Ch3-ImplementingScatter")</span></span>  
  
 <span data-ttu-id="434c8-109">**Figure 1**</span><span class="sxs-lookup"><span data-stu-id="434c8-109">**Figure 1**</span></span>  
  
 <span data-ttu-id="434c8-110">**Implémentation du modèle de ventilation-regroupement pour plusieurs appels de service Web**</span><span class="sxs-lookup"><span data-stu-id="434c8-110">**Implementing the Scatter-Gather pattern for multiple Web service invocations**</span></span>  
  
 <span data-ttu-id="434c8-111">L’exemple de ventilation-regroupement fourni avec le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] illustre ce cas de figure.</span><span class="sxs-lookup"><span data-stu-id="434c8-111">The Scatter-Gather sample included with the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] demonstrates this use case.</span></span>  
  
 <span data-ttu-id="434c8-112">Pour plus d’informations, consultez [l’installation et l’exécution de l’exemple de ventilation-regroupement](../esb-toolkit/installing-and-running-the-scatter-gather-sample.md).</span><span class="sxs-lookup"><span data-stu-id="434c8-112">For more information, see [Installing and Running the Scatter-Gather Sample](../esb-toolkit/installing-and-running-the-scatter-gather-sample.md).</span></span>