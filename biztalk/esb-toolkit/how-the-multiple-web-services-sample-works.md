---
title: "Comment les plusieurs Services Web fonctionnement de l’exemple | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 16680ca7-16cc-47df-8c39-a3311d468a46
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6b3d9faf350654be69015ea940b6b4f034d4de74
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-the-multiple-web-services-sample-works"></a><span data-ttu-id="59575-102">Comment les Services Web de plusieurs exemples de fonctionnement</span><span class="sxs-lookup"><span data-stu-id="59575-102">How the Multiple Web Services Sample Works</span></span>
<span data-ttu-id="59575-103">L’exemple de plusieurs Services Web utilise deux techniques distinctes pour appeler plusieurs services Web en série tout en étant en mesure de retourner un résultat incorrect à l’appelant d’origine.</span><span class="sxs-lookup"><span data-stu-id="59575-103">The Multiple Web Services sample uses two separate techniques to call multiple Web services in serial while still being able to return a proper result to the original caller.</span></span> <span data-ttu-id="59575-104">Une méthode utilise un composant de pipeline personnalisé dans le pipeline de réponse, et l’autre méthode utilise un bidirectionnels routage basé sur l’orchestration d’itinéraire service personnalisé qui ignore la configuration requise de l’appel d’une rampe pour effectuer un appel de demande/réponse à un site Web service.</span><span class="sxs-lookup"><span data-stu-id="59575-104">One method uses a custom pipeline component in the response pipeline, and the other method uses a custom two-way routing orchestration-based itinerary service that bypasses the requirement of an off-ramp invocation to complete a request/response call to a Web service.</span></span>  
  
 <span data-ttu-id="59575-105">La méthode de composant de pipeline personnalisé utilise le composant de Pipeline du redirecteur.</span><span class="sxs-lookup"><span data-stu-id="59575-105">The custom pipeline component method uses the Forwarder Pipeline component.</span></span> <span data-ttu-id="59575-106">Ce composant conditionnellement promeut les propriétés pour empêcher le routage du message vers le pipeline d’envoi de la bande jusqu'à ce que tous les services d’itinéraire sont traitées de Microsoft BizTalk.</span><span class="sxs-lookup"><span data-stu-id="59575-106">This component conditionally promotes properties to keep Microsoft BizTalk from routing the message back to the send pipeline of the on-ramp until all the itinerary services are processed.</span></span>  
  
 <span data-ttu-id="59575-107">La méthode de service personnalisé de basée sur l’orchestration utilise l’orchestration TwoWayRouting contenue dans l’architecture ESB. Projet MultipleWebServices.Orchestrations dans le \Source\Samples\MultipleWebSerivces\Source\ESB. MultipleWebServices.Orchestrations dossier.</span><span class="sxs-lookup"><span data-stu-id="59575-107">The custom orchestration-based service method uses the TwoWayRouting orchestration contained in the ESB.MultipleWebServices.Orchestrations project in the \Source\Samples\MultipleWebSerivces\Source\ESB.MultipleWebServices.Orchestrations folder.</span></span> <span data-ttu-id="59575-108">Ce service traite un résolveur associé pour déterminer l’adresse de point de terminaison d’un service Web bidirectionnel.</span><span class="sxs-lookup"><span data-stu-id="59575-108">This service processes an associated resolver to determine the endpoint address of a two-way Web service.</span></span> <span data-ttu-id="59575-109">Il configure ensuite un Port d’envoi dynamique Solict-réponse nommé RoutingPort pour envoyer le message au service Web et retourner le résultat à l’orchestration.</span><span class="sxs-lookup"><span data-stu-id="59575-109">It then configures a Dynamic Solict-Response Send Port named RoutingPort to send the message to the Web service and return the result to the orchestration.</span></span> <span data-ttu-id="59575-110">Ensuite, l’orchestration avance l’itinéraire et retourne le message résultant dans la MessageBox.</span><span class="sxs-lookup"><span data-stu-id="59575-110">The orchestration then advances the itinerary and returns the resulting message to the MessageBox.</span></span>  
  
 <span data-ttu-id="59575-111">Les itinéraires inclus dans l’exemple utilisent au moins une de ces méthodes afin de conserver le flux de message suivant l’itinéraire.</span><span class="sxs-lookup"><span data-stu-id="59575-111">The itineraries included with the sample use one or both of these methods to ensure message flow following the itinerary is maintained.</span></span> <span data-ttu-id="59575-112">Pour plus d’informations, consultez [l’exemple plusieurs Web Services itinéraires](../esb-toolkit/the-sample-multiple-web-services-itineraries.md).</span><span class="sxs-lookup"><span data-stu-id="59575-112">For more information, see [The Sample Multiple Web Services Itineraries](../esb-toolkit/the-sample-multiple-web-services-itineraries.md).</span></span>