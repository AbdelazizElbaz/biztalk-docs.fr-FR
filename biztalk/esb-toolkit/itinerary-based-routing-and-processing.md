---
title: "Itinéraire basée sur Routage et de traitement | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e8354538-e45c-487d-a380-59f497ea060f
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7600408837ed2ef40e11bc179bf0739fb15c5a61
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="itinerary-based-routing-and-processing"></a><span data-ttu-id="53c21-102">Le routage basé sur la feuille de route et traitement</span><span class="sxs-lookup"><span data-stu-id="53c21-102">Itinerary-Based Routing and Processing</span></span>
<span data-ttu-id="53c21-103">Le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] implémente un modèle de bordereau de routage via l’utilisation de composants de pipeline personnalisés.</span><span class="sxs-lookup"><span data-stu-id="53c21-103">The [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] implements a routing slip pattern through the use of custom pipeline components.</span></span> <span data-ttu-id="53c21-104">Métadonnées du message et autres facteurs sont utilisés pour déterminer le bordereau de routage approprié, également appelé un itinéraire à utiliser pour chaque message.</span><span class="sxs-lookup"><span data-stu-id="53c21-104">Message metadata and other factors are used to determine the appropriate routing slip, also known as an itinerary, to be used for each message.</span></span> <span data-ttu-id="53c21-105">Ce routage peut effectuer la transformation des messages, appeler des services d’orchestration et définir message routage étapes BizTalk Server s’exécute, de découplage efficacement les instructions de traitement de message à partir du moteur de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="53c21-105">This routing slip can perform message transformation, invoke orchestration services, and define message routing steps that BizTalk Server will execute, effectively decoupling message processing instructions from the core BizTalk Server engine.</span></span>  
  
 <span data-ttu-id="53c21-106">Pour plus d’informations sur le mode de traitement des itinéraires, consultez [principaux scénarios et tâches de développement](../esb-toolkit/key-scenarios-and-development-tasks.md).</span><span class="sxs-lookup"><span data-stu-id="53c21-106">For more information on how itineraries are processed, see [Key Scenarios and Development Tasks](../esb-toolkit/key-scenarios-and-development-tasks.md).</span></span>