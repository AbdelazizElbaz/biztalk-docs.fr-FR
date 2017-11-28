---
title: "Fonctionne de l’exemple de ventilation-regroupement | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5ccfacb7-4fd2-4a1a-bece-27eedd86bbe9
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c1221c038fa2e59636092c5cb49c6cbc40053708
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-the-scatter-gather-sample-works"></a><span data-ttu-id="1debf-102">Fonctionne de l’exemple de ventilation-regroupement</span><span class="sxs-lookup"><span data-stu-id="1debf-102">How the Scatter-Gather Sample Works</span></span>
<span data-ttu-id="1debf-103">Génère un ensemble d’en-têtes SOAP qui contient l’itinéraire chargé à partir du fichier de feuille de route de ventilation-regroupement, charge le fichier de message spécifié à partir du disque, ajoute les en-têtes d’itinéraire pour le message et l’envoie à l’architecture ESB via une rampe d’entrée pour l’exemple d’application lors du traitement.</span><span class="sxs-lookup"><span data-stu-id="1debf-103">The sample application builds a set of SOAP headers containing the itinerary loaded from the Scatter-Gather itinerary file, loads the specified message file from disk, appends the itinerary headers to the message, and submits it to the ESB through an on-ramp for processing.</span></span> <span data-ttu-id="1debf-104">Si l’itinéraire génère une réponse, l’application de cette collecte et affiche dans la fenêtre d’application.</span><span class="sxs-lookup"><span data-stu-id="1debf-104">If the itinerary generates a response, the application collects this and displays it in the application window.</span></span>  
  
 <span data-ttu-id="1debf-105">Pour vous aider à comprendre comment le service de l’itinéraire utilise les informations d’itinéraire dans un message, la liste suivante montre l’exemple de fichier de configuration d’itinéraire nommé ScatterGatherItinerary.xml.</span><span class="sxs-lookup"><span data-stu-id="1debf-105">To help you understand how the Itinerary service uses the itinerary information in a message, the following listing shows the sample itinerary configuration file named ScatterGatherItinerary.xml.</span></span> <span data-ttu-id="1debf-106">La première section de cet itinéraire spécifie deux étapes d’appel de service.</span><span class="sxs-lookup"><span data-stu-id="1debf-106">The first section of this itinerary specifies two service invocation steps.</span></span>  
  
```xml  
<Itinerary xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"   
    xmlns:xsd="http://www.w3.org/2001/XMLSchema" uuid="" beginTime=""   
    completeTime="" state="Pending" isRequestResponse="false"   
    xmlns="http://schemas.microsoft.biztalk.practices.esb.com/itinerary">  
  <ServiceInstance uuid="" name="ScatterGather" type="Orchestration"  
                   state="Pending" position="0"   
                   isRequestResponse="false" xmlns="" />  
  <Services xmlns="">  
    <Service uuid="" beginTime="" completeTime="" name="ScatterGather"  
             type="Orchestration" state="Pending" isRequestResponse="false"  
             position="0" serviceInstanceId="" />  
  </Services>  
  <Services xmlns="">  
    <Service uuid="" beginTime="" completeTime="" name="DynamicTest"  
             type="Messaging" state="Pending" isRequestResponse="false"  
             position="1" serviceInstanceId="" />  
  </Services>  
</Itinerary>  
...  
```  
  
 <span data-ttu-id="1debf-107">La liste des étapes d’appel de service dans l’itinéraire est la section contenant les détails de la résolution et les chaînes de connexion qui permettent au service de l’itinéraire rechercher chaque service défini dans l’itinéraire, comme indiqué dans le code XML suivant.</span><span class="sxs-lookup"><span data-stu-id="1debf-107">Following the list of service invocation steps in the itinerary is the section containing details of the resolvers and connection strings that allow the Itinerary service to locate each service defined in the itinerary, as shown in the following XML.</span></span>  
  
```xml  
<ResolverGroups xmlns="">  
 <Resolvers serviceId="ScatterGather0"><![CDATA[BRE:\\policy=ResolveEndPointScatterGather;version=;useMsg=;]]><![CDATA[UDDI3:\\serverUrl=http://localhost/uddi;bindingKey=uddi:esb:purchaseordersubmitorderservicebinding;credentialType=Ntlm]]></Resolvers>  
<Resolvers serviceId="DynamicTest1"><![CDATA[UDDI3:\\serverUrl=http://localhost/uddi;bindingKey=uddi:esb:orderfileservicebinding;credentialType=Ntlm]]>  
</Resolvers>  
  </ResolverGroups>  
```  
  
 <span data-ttu-id="1debf-108">Dans cet exemple, l’application exécute le site SubmitPOService Web service deux fois, car les deux chaînes de connexion du programme de résolution résoudre à l’emplacement de ce service (http://localhost/ESB.CanadianServices/SubmitPOService.asmx).</span><span class="sxs-lookup"><span data-stu-id="1debf-108">In this example, the application executes the SubmitPOService Web service twice because both resolver connection strings resolve to the location of this service (http://localhost/ESB.CanadianServices/SubmitPOService.asmx).</span></span> <span data-ttu-id="1debf-109">Le contexte de message Spécifie l’orchestration du courtier comme le premier service d’itinéraire à activer, défini dans l’exemple comme suit.</span><span class="sxs-lookup"><span data-stu-id="1debf-109">The message context specifies the Broker orchestration as the first itinerary service to activate, defined in the sample as the following.</span></span>  
  
```csharp  
(Microsoft.Practices.ESB.Itinerary.Schemas.ServiceName == "ScatterGather")  
     && (Microsoft.Practices.ESB.Itinerary.Schemas.ServiceState ==   
    "Pending") && (Microsoft.Practices.ESB.Itinerary.Schemas.ServiceType   
    == "Orchestration")  
```  
  
 <span data-ttu-id="1debf-110">L’orchestration du courtier analyse les paramètres de l’étape de son itinéraire et récupère une collection de programmes de résolution associé à l’étape de l’itinéraire.</span><span class="sxs-lookup"><span data-stu-id="1debf-110">The Broker orchestration analyzes the settings for its itinerary step and retrieves a collection of resolvers associated with the itinerary step.</span></span> <span data-ttu-id="1debf-111">Pour chacun de ces programmes de résolution, l’orchestration utilise la [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] programme de résolution et infrastructure d’adaptateurs pour résoudre le point de terminaison de service.</span><span class="sxs-lookup"><span data-stu-id="1debf-111">For each of these resolvers, the orchestration uses the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] Resolver and Adapter Framework to resolve the service endpoint.</span></span> <span data-ttu-id="1debf-112">L’orchestration du courtier puis active un nombre n d’orchestrations de distributeur de services en mode asynchrone (où n est le nombre de programmes de résolution associé au service ScatterGather dans la feuille de route) pour distribuer le message de demande avec les paramètres suivants :</span><span class="sxs-lookup"><span data-stu-id="1debf-112">The Broker orchestration then activates n number of ServiceDispatcher orchestrations asynchronously (where n is the number of resolvers associated with the ScatterGather service in the itinerary) to dispatch the request message with following parameters:</span></span>  
  
-   <span data-ttu-id="1debf-113">**TransportLocation**.</span><span class="sxs-lookup"><span data-stu-id="1debf-113">**TransportLocation**.</span></span> <span data-ttu-id="1debf-114">Le programme de résolution remplit ce paramètre.</span><span class="sxs-lookup"><span data-stu-id="1debf-114">The resolver populates this parameter.</span></span>  
  
-   <span data-ttu-id="1debf-115">**Type de transport**.</span><span class="sxs-lookup"><span data-stu-id="1debf-115">**TransportType**.</span></span> <span data-ttu-id="1debf-116">Le programme de résolution remplit ce paramètre.</span><span class="sxs-lookup"><span data-stu-id="1debf-116">The resolver populates this parameter.</span></span>  
  
-   <span data-ttu-id="1debf-117">**ResolverDictionary**.</span><span class="sxs-lookup"><span data-stu-id="1debf-117">**ResolverDictionary**.</span></span> <span data-ttu-id="1debf-118">Ce paramètre contient une collection de faits de programme de résolution remplie par l’instance de programme de résolution concrète.</span><span class="sxs-lookup"><span data-stu-id="1debf-118">This parameter contains a collection of resolver facts populated by the concrete resolver instance.</span></span>  
  
-   <span data-ttu-id="1debf-119">**InboundMessage**.</span><span class="sxs-lookup"><span data-stu-id="1debf-119">**InboundMessage**.</span></span> <span data-ttu-id="1debf-120">Ce paramètre contient le message d’origine qui contient l’itinéraire.</span><span class="sxs-lookup"><span data-stu-id="1debf-120">This parameter contains the original message that contains the itinerary.</span></span>  
  
-   <span data-ttu-id="1debf-121">**ServiceResponsePort**.</span><span class="sxs-lookup"><span data-stu-id="1debf-121">**ServiceResponsePort**.</span></span> <span data-ttu-id="1debf-122">Ce paramètre est le nom du port de réponse autocorrélation pour recevoir les réponses à partir des instances de l’orchestration de distributeur de services.</span><span class="sxs-lookup"><span data-stu-id="1debf-122">This parameter is the name of the self-correlating response port that will receive responses from the instances of the ServiceDispatcher orchestration.</span></span>  
  
 <span data-ttu-id="1debf-123">Chaque instance de l’orchestration de distributeur de services utilise la stratégie ResolveMapScatterGather pour résoudre les types de mappage de Microsoft BizTalk pour le message de demande et de réponse, en fonction de **TransportType** et  **TransportLocation** propriétés.</span><span class="sxs-lookup"><span data-stu-id="1debf-123">Each instance of the ServiceDispatcher orchestration uses the ResolveMapScatterGather policy to resolve the Microsoft BizTalk map types for the request and response message, based on **TransportType** and **TransportLocation** properties.</span></span> <span data-ttu-id="1debf-124">Les instances d’orchestration utilisent les mappages résolus pour transformer le message entrant dans le message de demande pour l’appel de service Web.</span><span class="sxs-lookup"><span data-stu-id="1debf-124">The orchestration instances use the resolved maps to transform the inbound message into the request message for the Web service call.</span></span>  
  
 <span data-ttu-id="1debf-125">Le Gestionnaire d’adaptateur ESB définit des propriétés de contexte du transport sortant sur le message de demande, les transfère vers le port de sollicitation-réponse ensuite le BizTalk nommé ServiceRequestPort.</span><span class="sxs-lookup"><span data-stu-id="1debf-125">The ESB Adapter Manager sets the outbound transport context properties on the request message, which BizTalk then forwards to the solicit-response port named ServiceRequestPort.</span></span>  
  
 <span data-ttu-id="1debf-126">Lorsqu’il reçoit un message de réponse d’un service, l’orchestration de distributeur de services utilise les informations de mappage résolu pour transformer le message de réponse entrant dans un format canonique.</span><span class="sxs-lookup"><span data-stu-id="1debf-126">When it receives a response message from a service, the ServiceDispatcher orchestration uses the resolved map information to transform the inbound response message to a canonical format.</span></span> <span data-ttu-id="1debf-127">Ensuite, il encapsule la réponse modifiée dans l’enveloppe ServiceResponse et transmet à l’orchestration du courtier via le port d’autocorrélation.</span><span class="sxs-lookup"><span data-stu-id="1debf-127">It then wraps the modified response within the ServiceResponse envelope and forwards it to the Broker orchestration through the self-correlating port.</span></span> <span data-ttu-id="1debf-128">L’orchestration du courtier regroupe toutes les réponses entrantes et prépare le dernier message de réponse à l’aide de GlobalBank.ESB.ScatterGather.Processes.AggregatingPipeline, comme indiqué dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="1debf-128">The Broker orchestration aggregates all incoming responses and prepares the final response message using GlobalBank.ESB.ScatterGather.Processes.AggregatingPipeline, as shown in the following code.</span></span>  
  
```csharp  
AggregatedResponse.Body = null;  
AggregatedResponse(*) = InboundMessage(*);  
Microsoft.XLANGs.Pipeline.XLANGPipelineManager.ExecuteSendPipeline(  
    typeof(GlobalBank.ESB.ScatterGather.Processes.AggregatingPipeline),  
    messageAggregator,AggregatedResponse);  
```  
  
 <span data-ttu-id="1debf-129">Ce code encapsule la totalité du traitement des réponses dans une enveloppe prédéfinie.</span><span class="sxs-lookup"><span data-stu-id="1debf-129">This code wraps the entire batch of responses within a predefined envelope.</span></span> <span data-ttu-id="1debf-130">L’orchestration du courtier puis avance la route le **DynamicTest** étape de l’itinéraire, comme indiqué dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="1debf-130">The Broker orchestration then advances the itinerary to the **DynamicTest** itinerary step, as shown in the following code.</span></span>  
  
```csharp  
// Copy the context and advance the itinerary.  
OutboundMessage = AggregatedResponse.Body;  
OutboundMessage(*) = AggregatedResponse(*);  
// Advance the Itinerary to the next step.  
itinerary.Itinerary.Advance(OutboundMessage, itineraryStep);  
```  
  
 <span data-ttu-id="1debf-131">Étant donné que l’attribut de type de service nommé **DynamicTest** a la valeur **messagerie**, le **ItineraryHelper** classe promeut les propriétés du programme de résolution dans le contexte de la message nommé **OutboundMessage**.</span><span class="sxs-lookup"><span data-stu-id="1debf-131">Because the service type attribute named **DynamicTest** is set to **Messaging**, the **ItineraryHelper** class promotes the resolver properties into the context of the message named **OutboundMessage**.</span></span> <span data-ttu-id="1debf-132">L’orchestration du courtier envoie ce message à un port de liaison directe de BizTalk.</span><span class="sxs-lookup"><span data-stu-id="1debf-132">The Broker orchestration sends this message to a BizTalk direct-bound port.</span></span> <span data-ttu-id="1debf-133">BizTalk transmet le message au port d’envoi dynamique représenté par le **ServiceName** abonnement, qui est **DynamicTest**.</span><span class="sxs-lookup"><span data-stu-id="1debf-133">BizTalk then forwards the message to the dynamic send port represented by the **ServiceName** subscription, which is **DynamicTest**.</span></span> <span data-ttu-id="1debf-134">Ce port d’envoi sérialise la réponse finale agrégée dans le dossier \Source\Samples\DynamicResolution\Test\Filedrop\Out.</span><span class="sxs-lookup"><span data-stu-id="1debf-134">This send port serializes the final aggregated response to the \Source\Samples\DynamicResolution\Test\Filedrop\Out folder.</span></span>