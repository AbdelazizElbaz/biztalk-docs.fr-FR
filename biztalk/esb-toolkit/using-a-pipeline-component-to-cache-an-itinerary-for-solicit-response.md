---
title: "À l’aide d’un composant de Pipeline pour mettre en Cache un itinéraire de sollicitation-réponse | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: add07ebf-785c-4c53-be69-efd40677a758
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 64b6822a4f4ca70e88ee86277e00645982595b47
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="using-a-pipeline-component-to-cache-an-itinerary-for-solicit-response"></a><span data-ttu-id="e00ea-102">À l’aide d’un composant de Pipeline pour mettre en Cache un itinéraire de sollicitation-réponse</span><span class="sxs-lookup"><span data-stu-id="e00ea-102">Using a Pipeline Component to Cache an Itinerary for Solicit-Response</span></span>
<span data-ttu-id="e00ea-103">Messages envoyés via un [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] rampe d’itinéraire peut passer par un itinéraire à sens unique ou d’une feuille de route bidirectionnelle (requête-réponse).</span><span class="sxs-lookup"><span data-stu-id="e00ea-103">Messages submitted through a [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] itinerary on-ramp can go through either a one-way itinerary or a two-way (request-response) itinerary.</span></span> <span data-ttu-id="e00ea-104">Pour prendre en charge les itinéraires de requête-réponse, le mécanisme d’itinéraire doit fournir la mise en cache pour les ports d’envoi BizTalk dynamiques avec sollicitation-réponse.</span><span class="sxs-lookup"><span data-stu-id="e00ea-104">To support request-response itineraries, the itinerary mechanism must provide caching for BizTalk dynamic Solicit-Response send ports.</span></span>  
  
 <span data-ttu-id="e00ea-105">Le composant de pipeline ESB itinéraire Cache place l’itinéraire stocké dans le contexte du message sortant dans le cache et l’attache au message de réponse ; elle est retournée par le port d’envoi à l’aide de la clé de la mise en cache peut être configurée.</span><span class="sxs-lookup"><span data-stu-id="e00ea-105">The ESB Itinerary Cache pipeline component places the itinerary stored in the outbound message context into the cache and attaches it to the response message; it is returned by the send port using the configurable caching key.</span></span> <span data-ttu-id="e00ea-106">Ainsi, le service d’itinéraire traiter et d’exécuter les services suivants définis après le service en cours dans la feuille de route.</span><span class="sxs-lookup"><span data-stu-id="e00ea-106">This allows the itinerary service to process and execute subsequent services defined after the current service in the itinerary.</span></span>  
  
 <span data-ttu-id="e00ea-107">Par défaut, le composant de pipeline ESB itinéraire Cache se trouve dans le pipeline ItineraryReceiveSend BizTalk, comme illustré dans la Figure 1.</span><span class="sxs-lookup"><span data-stu-id="e00ea-107">By default, the ESB Itinerary Cache pipeline component resides in the ItineraryReceiveSend BizTalk pipeline, as shown in Figure 1.</span></span> <span data-ttu-id="e00ea-108">Ce pipeline doit être utilisé uniquement en tant que le pipeline de réception pour un port d’envoi de sollicitation-réponse.</span><span class="sxs-lookup"><span data-stu-id="e00ea-108">This pipeline should be used only as the receive pipeline for a Solicit-Response send port.</span></span>  
  
 <span data-ttu-id="e00ea-109">![Cache du composant de pipeline](../esb-toolkit/media/ch4-pipelinecomponentcache.gif "PipelineComponentCache de chapitre 4")</span><span class="sxs-lookup"><span data-stu-id="e00ea-109">![Pipeline Component Cache](../esb-toolkit/media/ch4-pipelinecomponentcache.gif "Ch4-PipelineComponentCache")</span></span>  
  
 <span data-ttu-id="e00ea-110">**Figure 1**</span><span class="sxs-lookup"><span data-stu-id="e00ea-110">**Figure 1**</span></span>  
  
 <span data-ttu-id="e00ea-111">**Le composant de Pipeline de Cache d’itinéraire ESB**</span><span class="sxs-lookup"><span data-stu-id="e00ea-111">**The ESB Itinerary Cache Pipeline component**</span></span>  
  
 <span data-ttu-id="e00ea-112">Utilisez le composant de Pipeline de Cache d’itinéraire ESB dans BizTalk pipeline de réception pour un port d’envoi de sollicitation-réponse.</span><span class="sxs-lookup"><span data-stu-id="e00ea-112">Use the ESB Itinerary Cache Pipeline component in a BizTalk receive pipeline for a Solicit-Response send port.</span></span>