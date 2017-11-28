---
title: "À l’aide d’un Port d’envoi en tant qu’un abonné d’itinéraire Service | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 898b461c-4d0d-4703-a8ca-7f52f3f15f70
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5213b22c1bdfaa505dbf4b62a03095bcec5a1746
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="using-a-send-port-as-an-itinerary-service-subscriber"></a><span data-ttu-id="44132-102">À l’aide d’un Port d’envoi en tant qu’un abonné d’itinéraire de Service</span><span class="sxs-lookup"><span data-stu-id="44132-102">Using a Send Port as an Itinerary Service Subscriber</span></span>
<span data-ttu-id="44132-103">Figure 1 montre un exemple montrant comment utiliser un port d’envoi en tant qu’un abonné d’itinéraire de service, les conditions de filtre pour un port d’envoi unidirectionnel dynamique récupère les messages qui répondent aux conditions suivantes :</span><span class="sxs-lookup"><span data-stu-id="44132-103">As an example of how to use a send port as an itinerary service subscriber, Figure 1 shows the filter conditions for a dynamic one-way sent port that picks up messages that meet the following conditions:</span></span>  
  
-   <span data-ttu-id="44132-104">**IsRequestResponse = False**</span><span class="sxs-lookup"><span data-stu-id="44132-104">**IsRequestResponse = False**</span></span>  
  
-   <span data-ttu-id="44132-105">**ServiceName = DynamicTest**</span><span class="sxs-lookup"><span data-stu-id="44132-105">**ServiceName = DynamicTest**</span></span>  
  
-   <span data-ttu-id="44132-106">**ServiceState = en attente**</span><span class="sxs-lookup"><span data-stu-id="44132-106">**ServiceState = Pending**</span></span>  
  
-   <span data-ttu-id="44132-107">**ServiceType = messagerie**</span><span class="sxs-lookup"><span data-stu-id="44132-107">**ServiceType = Messaging**</span></span>  
  
 <span data-ttu-id="44132-108">![Port d’envoi](../esb-toolkit/media/ch4-sendport.gif "chapitre 4-ports d’envoi")</span><span class="sxs-lookup"><span data-stu-id="44132-108">![Send Port](../esb-toolkit/media/ch4-sendport.gif "Ch4-SendPort")</span></span>  
  
 <span data-ttu-id="44132-109">**Figure 1**</span><span class="sxs-lookup"><span data-stu-id="44132-109">**Figure 1**</span></span>  
  
 <span data-ttu-id="44132-110">**Exemple de filtres de port d’envoi**</span><span class="sxs-lookup"><span data-stu-id="44132-110">**Example of send port filters**</span></span>  
  
 <span data-ttu-id="44132-111">Expressions de filtre de port pour spécifier les ensembles de propriété et la valeur de messages, elle reprendra à partir de la base de données de la boîte de Message via l’itinéraire rampe d’entrée d’envoi.</span><span class="sxs-lookup"><span data-stu-id="44132-111">Use send port filter expressions to specify the property and value sets of messages it will pick up from the Message Box database through the itinerary on-ramp.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="44132-112">Il est important d’utiliser des conditions de filtre qui sont aussi spécifique et que la mesure du possible ; Sinon, il est un risque de récupérer des messages inattendus, ce qui peut provoquer des problèmes dans un environnement de haut volume.</span><span class="sxs-lookup"><span data-stu-id="44132-112">It is important to use filter conditions that are as specific and focused as possible; otherwise, there is a risk of picking up unintended messages, which could cause problems in a high-volume environment.</span></span> <span data-ttu-id="44132-113">Le schéma.xsd de système définit les propriétés de filtre d’abonnements.</span><span class="sxs-lookup"><span data-stu-id="44132-113">The schema System-Properties.xsd defines the filter properties of subscriptions.</span></span>