---
title: "Création d’un Service d’itinéraire personnalisé à l’aide d’une Orchestration BizTalk | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3bd7ed38-02a3-41b1-9990-754d5539f15e
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 723c0bc93192267f404d42e7fe859bb37ea59895
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="creating-a-custom-itinerary-service-using-a-biztalk-orchestration"></a><span data-ttu-id="48181-102">Création d’un Service d’itinéraire personnalisé à l’aide d’une Orchestration BizTalk</span><span class="sxs-lookup"><span data-stu-id="48181-102">Creating a Custom Itinerary Service Using a BizTalk Orchestration</span></span>
<span data-ttu-id="48181-103">L’infrastructure d’itinéraire qui fait partie de la [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] prend en charge l’exécution des étapes d’itinéraire à l’aide des orchestrations.</span><span class="sxs-lookup"><span data-stu-id="48181-103">The itinerary framework that is part of the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] supports execution of itinerary steps using orchestrations.</span></span> <span data-ttu-id="48181-104">Vous pouvez implémenter un service d’itinéraire personnalisé en tant qu’une orchestration Microsoft BizTalk Server en fonction de vos exigences fonctionnelles, qui peuvent inclure les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="48181-104">You can implement a custom itinerary service as a Microsoft BizTalk Server orchestration based on your functional requirements, which may include the following:</span></span>  
  
-   <span data-ttu-id="48181-105">Plusieurs appels de service (comme indiqué par le [l’installation et l’exécution de l’exemple de ventilation-regroupement](../esb-toolkit/installing-and-running-the-scatter-gather-sample.md))</span><span class="sxs-lookup"><span data-stu-id="48181-105">Multiple service invocations (as demonstrated by the [Installing and Running the Scatter-Gather Sample](../esb-toolkit/installing-and-running-the-scatter-gather-sample.md))</span></span>  
  
-   <span data-ttu-id="48181-106">Médiation et le message de corrélation de protocole (par exemple, HTTP-MQSeries)</span><span class="sxs-lookup"><span data-stu-id="48181-106">Protocol mediation and message correlation (for example, HTTP-MQSeries)</span></span>  
  
-   <span data-ttu-id="48181-107">Les décisions de routage complexes basée sur l’enrichissement de message à partir de données externes des sources</span><span class="sxs-lookup"><span data-stu-id="48181-107">Complex routing decisions based on message enrichment from external data sources</span></span>  
  
-   <span data-ttu-id="48181-108">Logique de traitement</span><span class="sxs-lookup"><span data-stu-id="48181-108">Business processing logic</span></span>  
  
 <span data-ttu-id="48181-109">Chaque service d’itinéraire implémentée à l’aide d’une orchestration BizTalk Server est chargé pour les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="48181-109">Every itinerary service implemented using a BizTalk Server orchestration is responsible for the following:</span></span>  
  
-   <span data-ttu-id="48181-110">Exception et la gestion des erreurs à l’aide de l’infrastructure de gestion d’Exception ESB ou les gestionnaires d’exceptions personnalisées facultatives qui prennent en charge la nouvelle soumission (itinéraires unidirectionnels)</span><span class="sxs-lookup"><span data-stu-id="48181-110">Exception and error handling using the ESB Exception Handling Framework or optional custom exception handlers that support resubmission (one-way itineraries)</span></span>  
  
-   <span data-ttu-id="48181-111">Avancer la feuille de route et la publication de messages sortants via BizTalk Server afin que l’étape suivante de la feuille de route de service peut s’exécuter.</span><span class="sxs-lookup"><span data-stu-id="48181-111">Advancing the itinerary and publishing outbound messages through BizTalk Server so that the next itinerary service step can execute</span></span>  
  
#### <a name="to-create-a-custom-itinerary-service-using-a-biztalk-server-orchestration"></a><span data-ttu-id="48181-112">Pour créer un service d’itinéraire personnalisé à l’aide d’une orchestration BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="48181-112">To create a custom itinerary service using a BizTalk Server orchestration</span></span>  
  
1.  <span data-ttu-id="48181-113">Créer le projet BizTalk Server qui contient une nouvelle orchestration ; par exemple, MyCustomeItineraryService.odx.</span><span class="sxs-lookup"><span data-stu-id="48181-113">Create new BizTalk Server project containing a new orchestration; for example, MyCustomeItineraryService.odx.</span></span>  
  
2.  <span data-ttu-id="48181-114">Ajoutez des références aux assemblys suivants :</span><span class="sxs-lookup"><span data-stu-id="48181-114">Add references to the following assemblies:</span></span>  
  
    -   <span data-ttu-id="48181-115">**Microsoft.Practices.ESB.Itinerary**</span><span class="sxs-lookup"><span data-stu-id="48181-115">**Microsoft.Practices.ESB.Itinerary**</span></span>  
  
    -   <span data-ttu-id="48181-116">**Microsoft.Practices.ESB.Itinerary.Schemas**</span><span class="sxs-lookup"><span data-stu-id="48181-116">**Microsoft.Practices.ESB.Itinerary.Schemas**</span></span>  
  
    -   <span data-ttu-id="48181-117">**Microsoft.Practices.ESB.ExceptionHandling**</span><span class="sxs-lookup"><span data-stu-id="48181-117">**Microsoft.Practices.ESB.ExceptionHandling**</span></span>  
  
    -   <span data-ttu-id="48181-118">**Microsoft.Practices.ESB.ExceptionHandling.Faults**</span><span class="sxs-lookup"><span data-stu-id="48181-118">**Microsoft.Practices.ESB.ExceptionHandling.Faults**</span></span>  
  
3.  <span data-ttu-id="48181-119">Définir une liaison directe logique port de réception et une forme réception activée dans l’orchestration.</span><span class="sxs-lookup"><span data-stu-id="48181-119">Define a logical direct-bound receive port and an activated receive shape in the orchestration.</span></span>  
  
4.  <span data-ttu-id="48181-120">Définir un filtre d’abonnement pour activer l’orchestration du contexte de message d’itinéraire afin que l’orchestration exécute la **MyCustomItineraryService** étape.</span><span class="sxs-lookup"><span data-stu-id="48181-120">Define a subscription filter to activate the orchestration from the message itinerary context so that the orchestration executes the **MyCustomItineraryService** step.</span></span> <span data-ttu-id="48181-121">Le code suivant montre un exemple d’un filtre approprié.</span><span class="sxs-lookup"><span data-stu-id="48181-121">The following code shows an example of a suitable filter.</span></span>  
  
    ```csharp  
    (Microsoft.Practices.ESB.Itinerary.Schemas.ServiceName   
        == "MyCustomItineraryService")   
    && (Microsoft.Practices.ESB.Itinerary.Schemas.ServiceState == "Pending")  
    && (Microsoft.Practices.ESB.Itinerary.Schemas.ServiceType   
        == "Orchestration")  
    ```  
  
5.  <span data-ttu-id="48181-122">Définir une orchestration de type **Microsoft.Practices.ESB.Itinerary.ItineraryStep**.</span><span class="sxs-lookup"><span data-stu-id="48181-122">Define an orchestration of type **Microsoft.Practices.ESB.Itinerary.ItineraryStep**.</span></span> <span data-ttu-id="48181-123">Ajouter une activité d’expression à l’orchestration qui remplit cette variable, comme indiqué dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="48181-123">Add an expression activity to the orchestration that populates this variable, as shown in the following code.</span></span>  
  
    ```csharp  
    // Retrieve the current itinerary step.  
    itinerary = new Microsoft.Practices.ESB.Itinerary.SerializableItineraryWrapper();  
    step = new Microsoft.Practices.ESB.Itinerary.SerializableItineraryStepWrapper();  
  
    itinerary.Itinerary = Microsoft.Practices.ESB.Itinerary.ItineraryOMFactory.Create(InboundMessage);  
    step.ItineraryStep = itinerary.Itinerary.GetItineraryStep(InboundMessage);  
  
    ```  
  
6.  <span data-ttu-id="48181-124">Ajoutez votre implémentation personnalisée à l’itinéraire qui crée le message sortant pour les étapes d’itinéraire ; par exemple, OutboundMsg.</span><span class="sxs-lookup"><span data-stu-id="48181-124">Add your custom implementation to the itinerary that creates the outbound message for the next itinerary steps; for example, OutboundMsg.</span></span>  
  
7.  <span data-ttu-id="48181-125">Avance l’itinéraire à l’aide de l’activité d’expression suivant qui utilise le contexte de message à partir du message entrant.</span><span class="sxs-lookup"><span data-stu-id="48181-125">Advance the itinerary using the following expression activity that uses the message context from inbound message.</span></span>  
  
    ```csharp  
    OutboundMessage(*) = InboundMessage(*);   
    itinerary.Itinerary.Advance(OutboundMessage, itineraryStep.ItineraryStep);  
    ```  
  
8.  <span data-ttu-id="48181-126">Envoyer le message sortant avec l’itinéraire de mise à jour via un port d’envoi de la liaison directe pour activer le service d’itinéraire suivant.</span><span class="sxs-lookup"><span data-stu-id="48181-126">Send the outbound message with the updated itinerary through a direct-bound send port to activate the next itinerary service.</span></span>  
  
 <span data-ttu-id="48181-127">Pour plus d’informations sur l’implémentation d’un service d’itinéraire personnalisé à l’aide des orchestrations BizTalk Server, consultez [l’installation et l’exécution de l’exemple de rampe d’entrée d’itinéraire](../esb-toolkit/installing-and-running-the-itinerary-on-ramp-sample.md) et [installer et exécuter la ventilation-regroupement. Exemple](../esb-toolkit/installing-and-running-the-scatter-gather-sample.md).</span><span class="sxs-lookup"><span data-stu-id="48181-127">For more information about implementing a custom itinerary service using BizTalk Server orchestrations, see [Installing and Running the Itinerary On-Ramp Sample](../esb-toolkit/installing-and-running-the-itinerary-on-ramp-sample.md) and [Installing and Running the Scatter-Gather Sample](../esb-toolkit/installing-and-running-the-scatter-gather-sample.md).</span></span>