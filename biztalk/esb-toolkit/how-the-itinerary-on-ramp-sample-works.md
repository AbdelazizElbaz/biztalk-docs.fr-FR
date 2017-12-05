---
title: "Fonctionne de l’exemple de rampe d’entrée d’itinéraire | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6f4f318c-b955-4a3d-88db-c0d324b63b21
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b73b4379944db548a30898403239ffcf9704791a
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="how-the-itinerary-on-ramp-sample-works"></a><span data-ttu-id="0c69d-102">Fonctionne de l’exemple de rampe d’entrée d’itinéraire</span><span class="sxs-lookup"><span data-stu-id="0c69d-102">How the Itinerary On-Ramp Sample Works</span></span>
<span data-ttu-id="0c69d-103">L’application génère un ensemble d’en-têtes SOAP qui contiennent l’itinéraire que vous créez à l’aide des contrôles dans la fenêtre d’application client, le Client Test itinéraire exemple charge le fichier de message spécifié à partir du disque, ajoute les en-têtes d’itinéraire pour le message, et envoie à l’architecture ESB via un itinéraire rampe d’entrée pour le traitement.</span><span class="sxs-lookup"><span data-stu-id="0c69d-103">The sample Itinerary Test Client application builds a set of SOAP headers that contain the itinerary that you create using the controls in the client application window, loads the specified message file from disk, appends the itinerary headers to the message, and submits it to the ESB through an Itinerary on-ramp for processing.</span></span> <span data-ttu-id="0c69d-104">Si l’itinéraire génère une réponse, l’application récupère la réponse et l’affiche dans la fenêtre d’application.</span><span class="sxs-lookup"><span data-stu-id="0c69d-104">If the itinerary generates a response, the application collects the response and displays it in the application window.</span></span>  
  
 <span data-ttu-id="0c69d-105">Vous pouvez choisir parmi plusieurs exemples de fichiers de configuration d’itinéraire pour voir les scénarios unidirectionnels et bidirectionnels qui utilisent des orchestrations, messagerie ou une combinaison des deux.</span><span class="sxs-lookup"><span data-stu-id="0c69d-105">You can choose from several sample itinerary configuration files to see one-way and two-way scenarios that use orchestrations, messaging, or a combination of both.</span></span>  
  
 <span data-ttu-id="0c69d-106">Pour vous aider à comprendre comment le service de l’itinéraire utilise les informations d’itinéraire dans un message, le code XML suivant montre l’exemple de fichier de configuration d’itinéraire nommé TwoWay (bidirectionnel)-OrchTransform-OrchRoutingGroup-OrchTwoWayCustom.xml utilisé dans l’exemple précédent.</span><span class="sxs-lookup"><span data-stu-id="0c69d-106">To help you understand how the Itinerary service uses the itinerary information in a message, the following XML shows the sample itinerary configuration file named TwoWay-OrchTransform-OrchRoutingGroup-OrchTwoWayCustom.xml used in the earlier example.</span></span> <span data-ttu-id="0c69d-107">La première section de cet itinéraire spécifie trois étapes d’appel de service.</span><span class="sxs-lookup"><span data-stu-id="0c69d-107">The first section of this itinerary specifies three service invocation steps.</span></span>  
  
```xml  
<Itinerary xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" uuid="" beginTime="" completeTime="" state="Pending" isRequestResponse="false" servicecount="0" xmlns="http://schemas.microsoft.biztalk.practices.esb.com/itinerary">  
  <BizTalkSegment interchangeId="" epmRRCorrelationToken="" receiveInstanceId="" messageId="" xmlns="" />  
  <ServiceInstance name="Microsoft.Practices.ESB.Services.Transform" type="Orchestration" state="Pending" position="0" isRequestResponse="false" xmlns="" />  
  <Services xmlns="">  
    <Service uuid="92d3b293-e6d4-44a1-b27d-c42b48aec667" beginTime="" completeTime="" name="Microsoft.Practices.ESB.Services.Transform" type="Orchestration" state="Pending" isRequestResponse="false" position="0" serviceInstanceId="" />  
  </Services>  
  <Services xmlns="">  
    <Service uuid="774488bc-e5b9-4a4e-9ae7-d25cdf23fd1c" beginTime="" completeTime="" name="Microsoft.Practices.ESB.Services.Routing" type="Orchestration" state="Pending" isRequestResponse="false" position="1" serviceInstanceId="" />  
  </Services>  
  <Services xmlns="">  
    <Service uuid="" beginTime="" completeTime="" name="ProcessAndRespond" type="Orchestration" state="Pending" isRequestResponse="true" position="2" serviceInstanceId="" />  
  </Services>  
  ...  
```  
  
 <span data-ttu-id="0c69d-108">Suivant la liste des étapes d’appel de service dans l’itinéraire correspond à la section contenant les détails des programmes de résolution (représentés par les chaînes de connexion) qui permettent au service de l’itinéraire rechercher ou fournir des informations de résolution pour chaque service défini dans le feuille de route.</span><span class="sxs-lookup"><span data-stu-id="0c69d-108">Following the list of service invocation steps in the itinerary is the section containing details of the resolvers (represented by connection strings) that allow the Itinerary service to locate or provide resolution information for each service defined in the itinerary.</span></span>  
  
```xml  
  ...  
<ResolverGroups xmlns="">  
    <Resolvers serviceId="Microsoft.Practices.ESB.Services.Transform0"><![CDATA[BRE:\\Policy=ResolveMap;Version=1.0;UseMsg=False;]]></Resolvers>  
    <Resolvers serviceId="Microsoft.Practices.ESB.Services.Routing1"><![CDATA[STATIC:\\TransportType=FILE;TransportLocation=C:\Projects\Microsoft.Practices.ESB\Source\Samples\DynamicResolution\Test\Filedrop\OUt\%MessageID%.xml;Action=;EndpointConfig=;JaxRpcResponse=False;MessageExchangePattern=;TargetNamespace=;TransformType=;]]><![CDATA[UDDI3:\\ServerUrl=http://localhost/uddi;SearchQualifiers=andAllKeys;CategorySearch=;BindingKey=uddi:esb:orderfileservicev3.1;]]></Resolvers>  
    <Resolvers serviceId="ProcessAndRespond2" />  
  </ResolverGroups>  
</Itinerary>  
```  
  
> [!NOTE]
>  <span data-ttu-id="0c69d-109">Le contenu réel de chaque  **\<résolveurs\>**  élément ne contient pas les caractères d’espace blanc utilisés pour encapsuler les lignes dans la liste précédente.</span><span class="sxs-lookup"><span data-stu-id="0c69d-109">The actual content of each **\<Resolvers\>** element does not contain the white space characters used to wrap the lines in the preceding listing.</span></span>  
  
 <span data-ttu-id="0c69d-110">Voici les trois étapes définies dans la configuration précédente d’itinéraire :</span><span class="sxs-lookup"><span data-stu-id="0c69d-110">The following are the three steps defined in the itinerary preceding configuration:</span></span>  
  
1.  <span data-ttu-id="0c69d-111">Exécutez l’orchestration Microsoft.Practices.ESB.Services.Transform pour transformer le message avec la stratégie de ResolverMap à l’aide du moteur de règles d’entreprise (BRE) BizTalk.</span><span class="sxs-lookup"><span data-stu-id="0c69d-111">Execute the Microsoft.Practices.ESB.Services.Transform orchestration to transform the message with the ResolverMap policy using BizTalk Business Rules Engine (BRE).</span></span>  
  
2.  <span data-ttu-id="0c69d-112">Exécutez l’orchestration Microsoft.Practices.ESB.Services.Routing pour acheminer le message transformé à plusieurs emplacements à l’aide de la Microsoft.Practices.ESB.Services.Routing1 de routage.</span><span class="sxs-lookup"><span data-stu-id="0c69d-112">Execute the Microsoft.Practices.ESB.Services.Routing orchestration to route the transformed message to multiple locations using the routing Microsoft.Practices.ESB.Services.Routing1.</span></span> <span data-ttu-id="0c69d-113">Le  **\<ResolverGroups\>**  section contient un  **\<résolveurs\>**  élément avec cet identificateur, qui définit les chaînes de connexion.</span><span class="sxs-lookup"><span data-stu-id="0c69d-113">The **\<ResolverGroups\>** section contains a **\<Resolvers\>** element with this identifier, which defines the connection strings.</span></span>  
  
3.  <span data-ttu-id="0c69d-114">Exécutez l’orchestration ProcessAndRespond fournie avec cet exemple.</span><span class="sxs-lookup"><span data-stu-id="0c69d-114">Execute the ProcessAndRespond orchestration provided with this sample.</span></span> <span data-ttu-id="0c69d-115">L’implémentation de cette orchestration envoie une copie du message de demande en tant que la réponse au client de Test d’itinéraire.</span><span class="sxs-lookup"><span data-stu-id="0c69d-115">The implementation of this orchestration sends as the response a copy of the request message back to the Itinerary Test Client.</span></span>  
  
 <span data-ttu-id="0c69d-116">À la fin de chaque service, le service avance l’itinéraire et promeut le prochain service défini dans l’itinéraire à l’instance de service en cours, avec son état la valeur **en attente**.</span><span class="sxs-lookup"><span data-stu-id="0c69d-116">With the completion of each service, the service advances the itinerary and promotes the next service defined in the itinerary to be the current service instance, with its state set to **Pending**.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0c69d-117">L’exemple de feuille de route rampe d’entrée utilise la résolution dynamique pour envoyer des messages dans le dossier de sortie.</span><span class="sxs-lookup"><span data-stu-id="0c69d-117">The Itinerary On-Ramp sample uses dynamic resolution to send messages to the output folder.</span></span> <span data-ttu-id="0c69d-118">Cela est pourquoi il n’est pas statique port d’envoi défini pour cet exemple.</span><span class="sxs-lookup"><span data-stu-id="0c69d-118">This is why there is no static send port defined for this sample.</span></span>  
  
 <span data-ttu-id="0c69d-119">Voici la séquence d’événements qui se produisent après que l’application de client de test envoie le message :</span><span class="sxs-lookup"><span data-stu-id="0c69d-119">The following is the sequence of events that occur after the test client application submits the message:</span></span>  
  
-   <span data-ttu-id="0c69d-120">Port de réception le OnRamp.Itinerary reçoit le message.</span><span class="sxs-lookup"><span data-stu-id="0c69d-120">The OnRamp.Itinerary receive port receives the message.</span></span>  
  
-   <span data-ttu-id="0c69d-121">Le pipeline ItineraryReceiveXml extrait l’itinéraire à partir de l’en-tête SOAP, valide et traite des, écrit l’itinéraire sous la forme d’une propriété de contexte de message dans le message entrant et publie le message dans la base de données MessageBox de BizTalk.</span><span class="sxs-lookup"><span data-stu-id="0c69d-121">The ItineraryReceiveXml pipeline extracts the itinerary from the SOAP header, validates and pre-processes it, writes the itinerary as a message context property into the inbound message, and publishes the message to the BizTalk Message Box database.</span></span>  
  
-   <span data-ttu-id="0c69d-122">Un abonnement pour l’orchestration de service Microsoft.Practices.ESB.Services.Transform déclenche l’appel de cette orchestration.</span><span class="sxs-lookup"><span data-stu-id="0c69d-122">A subscription for the Microsoft.Practices.ESB.Services.Transform service orchestration triggers invocation of this orchestration.</span></span> <span data-ttu-id="0c69d-123">L’orchestration récupère d’abord l’étape actuelle de l’itinéraire en passant le message actuel en tant que paramètre, comme indiqué dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="0c69d-123">The orchestration first retrieves the current itinerary step by passing the current message as a parameter, as shown in the following code.</span></span>  
  
    ```csharp  
    itineraryStep =   itinerary.Itinerary.GetItineraryStep(InboundMessage);  
    ```  
  
-   <span data-ttu-id="0c69d-124">Le **ItineraryStep** objet contient toutes les informations sur l’instance de service en cours d’exécution, ainsi que les programmes de résolution associés.</span><span class="sxs-lookup"><span data-stu-id="0c69d-124">The **ItineraryStep** object contains all the information about the current service instance for execution, as well as any resolvers associated with it.</span></span>  
  
-   <span data-ttu-id="0c69d-125">Le **résolveur** objet est récupéré à partir de la **ItineraryStep** instance et le cadre du programme de résolution ESB permet de résoudre le nom complet du plan de transformation, comme indiqué dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="0c69d-125">The **Resolver** object is retrieved from the **ItineraryStep** instance and the ESB Resolver Framework is used to resolve the full name of the transformation map, as shown in the following code.</span></span>  
  
    ```csharp  
    resolverDictionary =   
       Microsoft.Practices.ESB.Resolver.ResolverMgr.Resolve(InboundMessage,  
                                                            resolver);  
  
    // Set the transform type.  
    transformType = resolverDictionary.Item("Resolver.TransformType");  
    ```  
  
-   <span data-ttu-id="0c69d-126">Le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] programme de résolution et l’infrastructure d’adaptateurs accomplit cela en chargeant le programme de résolution approprié à partir du cache (dans cet exemple, le programme de résolution du moteur de règles d’entreprise BizTalk), qui appelle la stratégie ResolverMap et remplit la  **ResolverDictionary** objet.</span><span class="sxs-lookup"><span data-stu-id="0c69d-126">The [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] Resolver and Adapter Framework accomplishes this by loading the appropriate resolver from the cache (in this example, the BizTalk Business Rules Engine resolver), which invokes the ResolverMap policy and populates the **ResolverDictionary** object.</span></span>  
  
-   <span data-ttu-id="0c69d-127">Une fois l’orchestration terminée, le code appelle la **AdvanceItinerary** méthode, comme indiqué dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="0c69d-127">After the orchestration completes, the code calls the **AdvanceItinerary** method, as shown in the following code.</span></span>  
  
    ```csharp  
    // Call the Itinerary helper to advance to the next step.  
    itinerary.Itinerary.Advance(OutboundMessage, itineraryStep.ItineraryStep);  
    ```  
  
-   <span data-ttu-id="0c69d-128">Cela avance l’itinéraire actuel de mise à jour de ses propriétés et de promouvoir le prochain service défini dans la feuille de route en tant que celui à exécuter ensuite.</span><span class="sxs-lookup"><span data-stu-id="0c69d-128">This advances the current itinerary by updating its properties and promoting the next service defined in the itinerary as the one to execute next.</span></span> <span data-ttu-id="0c69d-129">La méthode de copie de la feuille de route dans le message sortant, ce qui est le service publie dans la base de données de la boîte de Message via un port d’envoi de la liaison directe.</span><span class="sxs-lookup"><span data-stu-id="0c69d-129">The method copies the itinerary into the outbound message, which the service publishes back into the Message Box database through a direct-bound send port.</span></span>  
  
-   <span data-ttu-id="0c69d-130">Un abonnement pour l’orchestration de service Microsoft.Practices.ESB.Services.Delivery déclenche l’appel de cette orchestration.</span><span class="sxs-lookup"><span data-stu-id="0c69d-130">A subscription for the Microsoft.Practices.ESB.Services.Delivery service orchestration triggers invocation of this orchestration.</span></span> <span data-ttu-id="0c69d-131">Cette orchestration suit un processus similaire à la première, obtention de l’étape actuelle de la feuille de route.</span><span class="sxs-lookup"><span data-stu-id="0c69d-131">This orchestration follows a similar process to the first one, obtaining the current Itinerary step.</span></span> <span data-ttu-id="0c69d-132">Toutefois, cette orchestration itère sur une collection de programmes de résolution retourné par le **ItineraryStep** instance.</span><span class="sxs-lookup"><span data-stu-id="0c69d-132">However, this orchestration iterates through a collection of resolvers returned by the **ItineraryStep** instance.</span></span> <span data-ttu-id="0c69d-133">Pour chaque programme de résolution dans la collection, l’orchestration de remise utilise le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] programme de résolution et infrastructure d’adaptateurs pour résoudre les emplacements de transport et de les promouvoir en tant que propriétés de contexte dans le message sortant, comme indiqué dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="0c69d-133">For each resolver in the collection, the delivery orchestration uses the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] Resolver and Adapter Framework to resolve the transport locations and promote them as context properties within the outgoing message, as shown in the following code.</span></span>  
  
    ```csharp  
    // Move to retrieve the first resolver.  
    resolver = resolvers.Current;  
  
    // Pass the resolver configuration to the Resolver Manager   
    // for resolution.  
    resolverDictionary =  
       Microsoft.Practices.ESB.Resolver.ResolverMgr.Resolve(InboundMessage,  
                                                            resolver);  
  
    // Set the transport properties.  
    transportLocation =   
       resolverDictionary.Item("Resolver.TransportLocation");  
    transportType =   
       resolverDictionary.Item("Resolver.TransportType");  
  
    // Call the Adapter Manager to set all necessary properties.  
    Microsoft.Practices.ESB.Adapter.AdapterMgr.SetEndpoint(  
                                    resolverDictionary, DeliveryMessage);  
  
    // Set the delivery port address and type.  
    DeliveryPort(Microsoft.XLANGs.BaseTypes.Address) = transportLocation;  
    DeliveryPort(Microsoft.XLANGs.BaseTypes.TransportType) = transportType;  
    ```  
  
-   <span data-ttu-id="0c69d-134">Un abonnement pour l’orchestration ProcessAndRespond déclenche l’appel de cette orchestration en raison d’une correspondance des propriétés de contexte de message définis pour les propriétés de l’expression de filtre.</span><span class="sxs-lookup"><span data-stu-id="0c69d-134">A subscription for the ProcessAndRespond orchestration triggers invocation of this orchestration because of a match of the message context properties defined for the filter expression properties.</span></span>  
  
    ```  
    (Microsoft.Practices.ESB.Itinerary.Schemas.ServiceName == :"ProcessAndRespond")   
    && Microsoft.Practices.ESB.Itinerary.Schemas.ServiceState == "Pending")  
    && (Microsoft.Practices.ESB.Itinerary.Schemas.ServiceType == "Orchestration")  
    ```  
  
-   <span data-ttu-id="0c69d-135">L’orchestration ProcessAndRespond avance l’itinéraire et envoie le message d’origine de la demande au service rampe d’entrée à l’application de Client de Test d’itinéraire dans la réponse.</span><span class="sxs-lookup"><span data-stu-id="0c69d-135">The ProcessAndRespond orchestration advances the itinerary and sends the original request message back to the on-ramp service to the Itinerary Test Client application as the response.</span></span>