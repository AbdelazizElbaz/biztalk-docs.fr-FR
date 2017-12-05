---
title: "Création d’abonnés d’itinéraire | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 84a76aeb-8d40-490a-8ae6-7abfdd2d2573
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5f470ed5268c445ab3b7175f1cba07ff1de52a27
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="creating-itinerary-subscribers"></a><span data-ttu-id="5f1bd-102">Création d’abonnés d’itinéraire</span><span class="sxs-lookup"><span data-stu-id="5f1bd-102">Creating Itinerary Subscribers</span></span>
<span data-ttu-id="5f1bd-103">BizTalk Server publie automatiquement les messages qui arrivent via un pipeline de réception pour la base de données de la boîte de Message ; Cela rend les messages attend par l’abonné approprié.</span><span class="sxs-lookup"><span data-stu-id="5f1bd-103">BizTalk Server automatically publishes messages arriving through a receive pipeline to the Message Box database; this makes the messages ready for pick-up by the relevant subscriber.</span></span> <span data-ttu-id="5f1bd-104">Cette approche découplée est la meilleure façon de développer des solutions BizTalk, car elle fournit une flexibilité maximale, évolutif et utilise la publication-abonnement.</span><span class="sxs-lookup"><span data-stu-id="5f1bd-104">This decoupled approach is the preferred way to develop BizTalk solutions because it provides maximum flexibility, scales well, and uses the publish-subscribe mechanism.</span></span>  
  
 <span data-ttu-id="5f1bd-105">Il existe deux façons de créer un abonné d’itinéraire de service :</span><span class="sxs-lookup"><span data-stu-id="5f1bd-105">There are two ways to create an itinerary service subscriber:</span></span>  
  
-   [<span data-ttu-id="5f1bd-106">Utilisation d’un port d’envoi en tant qu’abonné au service d’itinéraire</span><span class="sxs-lookup"><span data-stu-id="5f1bd-106">Using a Send Port as an Itinerary Service Subscriber</span></span>](../esb-toolkit/using-a-send-port-as-an-itinerary-service-subscriber.md)  
  
-   [<span data-ttu-id="5f1bd-107">Utilisation d’une orchestration en tant qu’abonné au service d’itinéraire</span><span class="sxs-lookup"><span data-stu-id="5f1bd-107">Using an Orchestration as an Itinerary Service Subscriber</span></span>](../esb-toolkit/using-an-orchestration-as-an-itinerary-service-subscriber.md)