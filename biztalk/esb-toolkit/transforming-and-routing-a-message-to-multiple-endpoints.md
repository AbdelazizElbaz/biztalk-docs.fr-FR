---
title: Transformer et acheminer les messages vers plusieurs points de terminaison | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 544db12c-95fc-4321-b397-ec9e7410e37d
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4c0fc2b3b9893607f760c564d03fc6090a7f1ea0
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="transforming-and-routing-a-message-to-multiple-endpoints"></a><span data-ttu-id="279ef-102">Transformer et acheminer les messages vers plusieurs points de terminaison</span><span class="sxs-lookup"><span data-stu-id="279ef-102">Transforming and Routing a Message to Multiple Endpoints</span></span>
<span data-ttu-id="279ef-103">Dans ce cas de figure, l’architecture ESB effectue une transformation sur un message envoyé via le Web de l’itinéraire service rampe d’entrée.</span><span class="sxs-lookup"><span data-stu-id="279ef-103">In this use case, the ESB performs a transformation on a message submitted through the Itinerary Web service on-ramp.</span></span> <span data-ttu-id="279ef-104">Une recherche de résolution dynamique détermine le nom de mappage et transforme le message entrant.</span><span class="sxs-lookup"><span data-stu-id="279ef-104">A dynamic resolution lookup determines the map name and transforms the inbound message.</span></span> <span data-ttu-id="279ef-105">En outre, l’itinéraire spécifie un nombre n de point de terminaison cible résoudre dynamiquement le service de la feuille de route et à laquelle il achemine le message transformé.</span><span class="sxs-lookup"><span data-stu-id="279ef-105">Additionally, the itinerary specifies n number of target endpoints that the Itinerary service will dynamically resolve and to which it will route the transformed message.</span></span> <span data-ttu-id="279ef-106">Toutes les opérations se produisent au niveau de la couche de messagerie, comme illustré dans la Figure 1.</span><span class="sxs-lookup"><span data-stu-id="279ef-106">All operations occur at the messaging layer, as illustrated in Figure 1.</span></span>  
  
 <span data-ttu-id="279ef-107">![Transformation de plusieurs points de terminaison](../esb-toolkit/media/ch3-transformingmultipleendpoints.gif "Ch3-TransformingMultipleEndpoints")</span><span class="sxs-lookup"><span data-stu-id="279ef-107">![Transforming Multiple Endpoints](../esb-toolkit/media/ch3-transformingmultipleendpoints.gif "Ch3-TransformingMultipleEndpoints")</span></span>  
  
 <span data-ttu-id="279ef-108">**Figure 1**</span><span class="sxs-lookup"><span data-stu-id="279ef-108">**Figure 1**</span></span>  
  
 <span data-ttu-id="279ef-109">**Transformer et acheminer les messages vers plusieurs points de terminaison**</span><span class="sxs-lookup"><span data-stu-id="279ef-109">**Transforming and routing a message to multiple endpoints**</span></span>  
  
 <span data-ttu-id="279ef-110">L’exemple de résolution dynamique fourni avec le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] illustre ce cas de figure.</span><span class="sxs-lookup"><span data-stu-id="279ef-110">The Dynamic Resolution sample included with the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] demonstrates this use case.</span></span> <span data-ttu-id="279ef-111">Il montre comment utiliser les composants de pipeline ESB, spécifiquement le composant désassembleur de Dispatch ESB, dynamiquement résoudre l’emplacement du point de terminaison, définir des propriétés de routage et résoudre et exécuter BizTalk Server mappe au niveau de la messagerie, sans utiliser un orchestration.</span><span class="sxs-lookup"><span data-stu-id="279ef-111">It shows how to use ESB pipeline components, specifically the ESB Dispatch Disassembler component, to dynamically resolve endpoint location, set routing properties, and resolve and execute BizTalk Server maps at the messaging level, without using an orchestration.</span></span> <span data-ttu-id="279ef-112">Il montre également les modèles de messagerie unidirectionnels ou bidirectionnels.</span><span class="sxs-lookup"><span data-stu-id="279ef-112">It also demonstrates both one-way and two-way messaging patterns.</span></span>  
  
 <span data-ttu-id="279ef-113">Pour plus d’informations, consultez [l’installation et l’exécution de l’exemple de résolution dynamique](../esb-toolkit/installing-and-running-the-dynamic-resolution-sample.md) et [installer et exécuter l’exemple de Services Web plusieurs](../esb-toolkit/installing-and-running-the-multiple-web-services-sample.md).</span><span class="sxs-lookup"><span data-stu-id="279ef-113">For more information, see [Installing and Running the Dynamic Resolution Sample](../esb-toolkit/installing-and-running-the-dynamic-resolution-sample.md) and [Installing and Running the Multiple Web Services Sample](../esb-toolkit/installing-and-running-the-multiple-web-services-sample.md).</span></span>