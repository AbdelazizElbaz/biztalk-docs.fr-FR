---
title: "Modèles de médiation de service | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cfda54db-75fa-4bc2-9f48-11d8b3cde65b
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: af76e6c123a3a273bc2e100b1008f40523762695
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="service-mediation-patterns"></a><span data-ttu-id="f2365-102">Modèles de médiation de service</span><span class="sxs-lookup"><span data-stu-id="f2365-102">Service Mediation Patterns</span></span>
## <a name="vetovetro"></a><span data-ttu-id="f2365-103">VETO/VETRO</span><span class="sxs-lookup"><span data-stu-id="f2365-103">VETO/VETRO</span></span>  
 <span data-ttu-id="f2365-104">Le modèle VETRO est un modèle courant composite qui combine plusieurs actions effectuées sur un message lorsqu’elle est reçue.</span><span class="sxs-lookup"><span data-stu-id="f2365-104">The VETRO pattern is a common composite pattern that combines multiple actions taken on a message when it is received.</span></span> <span data-ttu-id="f2365-105">Le terme VETRO est un acronyme validation, enrichissement, transformation, Route, opérer.</span><span class="sxs-lookup"><span data-stu-id="f2365-105">The term VETRO is an acronym that stands for Validate, Enrich, Transform, Route, Operate.</span></span> <span data-ttu-id="f2365-106">Dans la [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)], ces actions peuvent être gérées comme des étapes individuelles dans le pipeline associé à l’emplacement de réception.</span><span class="sxs-lookup"><span data-stu-id="f2365-106">In the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)], these actions can be handled as individual stages in the pipeline associated with the receive location.</span></span> <span data-ttu-id="f2365-107">Pour plus d’informations sur comment chacune de ces étapes peut être implémenté, consultez les scénarios de clé et les tâches de développement.</span><span class="sxs-lookup"><span data-stu-id="f2365-107">For more information about how each of these stages can be implemented, see Key Scenarios and Development Tasks.</span></span>  
  
## <a name="request-response"></a><span data-ttu-id="f2365-108">Requête-réponse</span><span class="sxs-lookup"><span data-stu-id="f2365-108">Request-Response</span></span>  
 <span data-ttu-id="f2365-109">Le modèle demande-réponse définit une solution dans lequel un service ou de tiers l’envoie une demande de message et attend un message de réponse en retour à partir du service de destination.</span><span class="sxs-lookup"><span data-stu-id="f2365-109">The Request-Response pattern defines a solution in which a service or party sends a request message and expects a reply message in return from the destination service.</span></span> <span data-ttu-id="f2365-110">Pour obtenir une description détaillée de ce modèle, consultez [demande-réponse](http://go.microsoft.com/fwlink/?LinkId=186849) ([http://go.microsoft.com/fwlink/?LinkId=186849](http://go.microsoft.com/fwlink/?LinkId=186849)) sur le site de modèles d’intégration d’entreprise.</span><span class="sxs-lookup"><span data-stu-id="f2365-110">For a detailed description of this pattern, see [Request-Reply](http://go.microsoft.com/fwlink/?LinkId=186849) ([http://go.microsoft.com/fwlink/?LinkId=186849](http://go.microsoft.com/fwlink/?LinkId=186849)) on the Enterprise Integration Patterns site.</span></span>  
  
 <span data-ttu-id="f2365-111">Pour plus d’informations sur la façon d’implémenter ce modèle, consultez les ressources suivantes :</span><span class="sxs-lookup"><span data-stu-id="f2365-111">For more information about how to implement this pattern, see the following resources:</span></span>  
  
-   [<span data-ttu-id="f2365-112">Comment : transformer un Message et un itinéraire vers un point de terminaison de Service à l’aide d’un modèle d’échange de Message demande-réponse</span><span class="sxs-lookup"><span data-stu-id="f2365-112">How to: Transform a Message and Route to a Service Endpoint Using a Request-Response Message Exchange Pattern</span></span>](../esb-toolkit/transform-message-and-route-to-service-endpoint-using-request-response-message.md)  
  
-   [<span data-ttu-id="f2365-113">Installer et exécuter l’exemple de rampe d’entrée d’itinéraire</span><span class="sxs-lookup"><span data-stu-id="f2365-113">Installing and Running the Itinerary On-Ramp Sample</span></span>](../esb-toolkit/installing-and-running-the-itinerary-on-ramp-sample.md)