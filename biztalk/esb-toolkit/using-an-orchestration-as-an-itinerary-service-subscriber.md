---
title: "À l’aide d’une Orchestration en tant qu’un abonné d’itinéraire Service | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 278564f1-de9f-4fbf-8c7f-09b3e607c28b
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f496884d0aed8d5f351f681ca8cfe59e05684240
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="using-an-orchestration-as-an-itinerary-service-subscriber"></a><span data-ttu-id="aec3c-102">À l’aide d’une Orchestration en tant qu’un abonné d’itinéraire de Service</span><span class="sxs-lookup"><span data-stu-id="aec3c-102">Using an Orchestration as an Itinerary Service Subscriber</span></span>
<span data-ttu-id="aec3c-103">Orchestrations peuvent également agir en tant que services d’itinéraire.</span><span class="sxs-lookup"><span data-stu-id="aec3c-103">Orchestrations can also act as itinerary services.</span></span> <span data-ttu-id="aec3c-104">Pour participer à un itinéraire, vous devez tout d’abord créer l’orchestration en tant que liaison directe ; Pour ce faire, utilisez un abonnement de filtre similaire à celui du port d’envoi dans la rubrique précédente, [à l’aide d’un Port d’envoi en tant qu’itinéraire Service abonné](../esb-toolkit/using-a-send-port-as-an-itinerary-service-subscriber.md).</span><span class="sxs-lookup"><span data-stu-id="aec3c-104">To participate in an itinerary, you must first design the orchestration as direct-bound; to do this, use a filter subscription similar to that of the send port in the previous topic, [Using a Send Port as an Itinerary Service Subscriber](../esb-toolkit/using-a-send-port-as-an-itinerary-service-subscriber.md).</span></span> <span data-ttu-id="aec3c-105">La figure 1 montre un exemple d’une expression de filtre pour une orchestration appropriée récupérer un message qui remplit les conditions suivantes :</span><span class="sxs-lookup"><span data-stu-id="aec3c-105">Figure 1 shows an example of a filter expression for a suitable orchestration to pick up any message that meets the following conditions:</span></span>  
  
-   <span data-ttu-id="aec3c-106">**ServiceName = Microsoft.Practices.ESB.Services.Transform**</span><span class="sxs-lookup"><span data-stu-id="aec3c-106">**ServiceName = Microsoft.Practices.ESB.Services.Transform**</span></span>  
  
-   <span data-ttu-id="aec3c-107">**ServiceState = en attente**</span><span class="sxs-lookup"><span data-stu-id="aec3c-107">**ServiceState = Pending**</span></span>  
  
-   <span data-ttu-id="aec3c-108">**ServiceType = d’Orchestration**</span><span class="sxs-lookup"><span data-stu-id="aec3c-108">**ServiceType = Orchestration**</span></span>  
  
 <span data-ttu-id="aec3c-109">![Orchestration](../esb-toolkit/media/ch4-orchestration.jpg "chapitre 4-Orchestration")</span><span class="sxs-lookup"><span data-stu-id="aec3c-109">![Orchestration](../esb-toolkit/media/ch4-orchestration.jpg "Ch4-Orchestration")</span></span>  
  
 <span data-ttu-id="aec3c-110">**Figure 1**</span><span class="sxs-lookup"><span data-stu-id="aec3c-110">**Figure 1**</span></span>  
  
 <span data-ttu-id="aec3c-111">**Exemple d’expression de filtre d’une orchestration qui participe à une feuille de route en tant qu’abonné**</span><span class="sxs-lookup"><span data-stu-id="aec3c-111">**Example filter expression for an orchestration that will participate in an itinerary as a subscriber**</span></span>  
  
 <span data-ttu-id="aec3c-112">Lorsque des messages arrivent dans Microsoft BizTalk Server via un ESB rampe d’entrée, l’étape de validation dans le pipeline ESB écrit les valeurs de propriété pour les propriétés de filtre dans les propriétés de contexte BizTalk du message entrant ; les promeut dans le contexte du message.</span><span class="sxs-lookup"><span data-stu-id="aec3c-112">When messages arrive in Microsoft BizTalk Server through an ESB on-ramp, the validation step in the ESB pipeline writes the property values for the filter properties into the BizTalk context properties of the incoming message; this promotes them to the message context.</span></span> <span data-ttu-id="aec3c-113">Le service d’itinéraire définit toujours la **ServiceName** propriété pour le service actuellement actif pour le nom du service à traiter suivant et avec un **ServiceState** valeur de propriété  **En attente**.</span><span class="sxs-lookup"><span data-stu-id="aec3c-113">The itinerary service always sets the **ServiceName** property for the currently active service to the name of the service to process next, and with a **ServiceState** property value of **Pending**.</span></span> <span data-ttu-id="aec3c-114">Pour un abonnement, vous devez définir au moins le premier trois propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="aec3c-114">For a subscription, you must set at least the first three of the following properties:</span></span>  
  
-   <span data-ttu-id="aec3c-115">**ServiceName.**</span><span class="sxs-lookup"><span data-stu-id="aec3c-115">**ServiceName.**</span></span> <span data-ttu-id="aec3c-116">Ceci est le nom du service, tel que stocké dans la feuille de route ESB et peut être n’importe quel nom.</span><span class="sxs-lookup"><span data-stu-id="aec3c-116">This is the name of the service, as stored in the ESB itinerary, and can be any name.</span></span> <span data-ttu-id="aec3c-117">L’itinéraire utilise ce nom pour identifier le service à exécuter.</span><span class="sxs-lookup"><span data-stu-id="aec3c-117">The itinerary uses this name to identify which service to execute.</span></span>  
  
-   <span data-ttu-id="aec3c-118">**ServiceState.**</span><span class="sxs-lookup"><span data-stu-id="aec3c-118">**ServiceState.**</span></span> <span data-ttu-id="aec3c-119">Il s’agit de l’état de l’étape actuelle de la feuille de route de service à exécuter.</span><span class="sxs-lookup"><span data-stu-id="aec3c-119">This is the state of the current itinerary service step to execute.</span></span> <span data-ttu-id="aec3c-120">L’étape de service en cours (pour le traitement suivant) ont toujours la valeur **en attente**, défini par l’ESB d’itinéraire composant de pipeline, le composant de pipeline ESB itinéraire sélecteur, ou de code qui appelle la méthode le **avance**  (méthode) de l’API de l’itinéraire.</span><span class="sxs-lookup"><span data-stu-id="aec3c-120">The current service step (for processing next) will always have the value **Pending**, set by either the ESB itinerary pipeline component, the ESB Itinerary Selector pipeline component, or code that calls the **Advance** method of the itinerary API.</span></span>  
  
-   <span data-ttu-id="aec3c-121">**ServiceType.**</span><span class="sxs-lookup"><span data-stu-id="aec3c-121">**ServiceType.**</span></span> <span data-ttu-id="aec3c-122">Cette propriété définit le type de service, qui indique si elle provenance de l’orchestration ou le sous-système de messagerie dans BizTalk.</span><span class="sxs-lookup"><span data-stu-id="aec3c-122">This property defines the type of service, indicating whether it originates from the orchestration or the messaging subsystem in BizTalk.</span></span>  
  
-   <span data-ttu-id="aec3c-123">**IsRequestResponse.**</span><span class="sxs-lookup"><span data-stu-id="aec3c-123">**IsRequestResponse.**</span></span> <span data-ttu-id="aec3c-124">Cette propriété facultative doit avoir la même valeur que la **IsRequestResponse** propriété du service.</span><span class="sxs-lookup"><span data-stu-id="aec3c-124">This optional property must have the same value as the **IsRequestResponse** property of the service.</span></span>