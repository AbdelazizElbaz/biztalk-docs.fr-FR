---
title: "À l’aide d’un composant de Pipeline pour sélectionner un itinéraire existant | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b93c5cb6-071f-485d-b0bb-22f95bafa3d0
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a733da2348de13120ce37a205b77d2e8194c7790
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="using-a-pipeline-component-to-select-an-existing-itinerary"></a><span data-ttu-id="c2f4c-102">À l’aide d’un composant de Pipeline pour sélectionner un itinéraire existant</span><span class="sxs-lookup"><span data-stu-id="c2f4c-102">Using a Pipeline Component to Select an Existing Itinerary</span></span>
## <a name="esb-itinerary-selector-pipeline-component"></a><span data-ttu-id="c2f4c-103">Composant de Pipeline ESB sélecteur d’itinéraire</span><span class="sxs-lookup"><span data-stu-id="c2f4c-103">ESB Itinerary Selector Pipeline Component</span></span>  
 <span data-ttu-id="c2f4c-104">Messages envoyés à l’aide de générique d’itinéraire sur écarts sont envoyées sans un en-tête d’itinéraire.</span><span class="sxs-lookup"><span data-stu-id="c2f4c-104">Messages submitted using generic itinerary on-ramps are submitted without an itinerary header.</span></span> <span data-ttu-id="c2f4c-105">Pour résoudre l’itinéraire approprié et l’attacher au message entrant, le démarrage doit fournir un mécanisme qui peut être configuré pour accéder à des itinéraires à partir d’un référentiel central.</span><span class="sxs-lookup"><span data-stu-id="c2f4c-105">To resolve the appropriate itinerary and attach it to the incoming message, the on-ramp must provide a mechanism that can be configured to access itineraries from a central repository.</span></span>  
  
 <span data-ttu-id="c2f4c-106">Le composant de pipeline ESB itinéraire sélecteur utilise une chaîne de connexion de programme de résolution, conjointement avec les programmes de résolution spécifiques, pour résoudre le contenu d’un itinéraire côté serveur stocké dans un référentiel central (par défaut, SQL Server).</span><span class="sxs-lookup"><span data-stu-id="c2f4c-106">The ESB Itinerary Selector pipeline component uses a resolver connection string, in conjunction with specialized resolvers, to resolve the content of a server-side itinerary stored in a central repository (by default, SQL Server).</span></span>  
  
 <span data-ttu-id="c2f4c-107">Lorsque le composant de pipeline ESB itinéraire sélecteur est utilisé dans WCF les écarts conjointement avec le programme de résolution d’itinéraire statique, le nom et la version de l’itinéraire demandé par le client (comme représenté dans l’en-tête SOAP) sont récupérées à partir du contexte de message et permet de sélectionner l’itinéraire approprié.</span><span class="sxs-lookup"><span data-stu-id="c2f4c-107">When the ESB Itinerary Selector pipeline component is used in WCF on-ramps in conjunction with the ITINERARY-STATIC resolver, the name and version of the itinerary requested by the client (as represented in the SOAP header) is retrieved from the message context and is used to select the appropriate itinerary.</span></span>  
  
 <span data-ttu-id="c2f4c-108">Par défaut, le composant de pipeline ESB itinéraire sélecteur se trouve dans les pipelines suivants :</span><span class="sxs-lookup"><span data-stu-id="c2f4c-108">By default, the ESB Itinerary Selector pipeline component resides in the following pipelines:</span></span>  
  
-   <span data-ttu-id="c2f4c-109">ItinerarySelectReceive</span><span class="sxs-lookup"><span data-stu-id="c2f4c-109">ItinerarySelectReceive</span></span>  
  
-   <span data-ttu-id="c2f4c-110">ItinerarySelectReceivePassthrough</span><span class="sxs-lookup"><span data-stu-id="c2f4c-110">ItinerarySelectReceivePassthrough</span></span>  
  
-   <span data-ttu-id="c2f4c-111">ItinerarySelectReceiveXml</span><span class="sxs-lookup"><span data-stu-id="c2f4c-111">ItinerarySelectReceiveXml</span></span>  
  
-   <span data-ttu-id="c2f4c-112">ItinerarySelectSendReceive</span><span class="sxs-lookup"><span data-stu-id="c2f4c-112">ItinerarySelectSendReceive</span></span>  
  
 <span data-ttu-id="c2f4c-113">Les sections suivantes décrivent les étapes effectuées par chaque composant.</span><span class="sxs-lookup"><span data-stu-id="c2f4c-113">The following sections describe the steps performed by each component.</span></span>  
  
## <a name="esb-itinerary-selector-pipeline-component-processing-steps"></a><span data-ttu-id="c2f4c-114">Étapes de traitement de composant de Pipeline de sélecteur d’itinéraire ESB</span><span class="sxs-lookup"><span data-stu-id="c2f4c-114">ESB Itinerary Selector Pipeline Component Processing Steps</span></span>  
 <span data-ttu-id="c2f4c-115">Le composant de pipeline ESB itinéraire sélecteur exécute les étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="c2f4c-115">The ESB Itinerary Selector pipeline component executes the following steps:</span></span>  
  
-   <span data-ttu-id="c2f4c-116">Le tiers émetteur envoie un message pour le traitement.</span><span class="sxs-lookup"><span data-stu-id="c2f4c-116">The submitting party submits a message for processing.</span></span> <span data-ttu-id="c2f4c-117">Le composant de sélecteur d’itinéraire utilise un programme de résolution spécifié comme une chaîne de connexion propriété configurée par le développeur, pour déterminer et sélectionnez la feuille de route approprié à partir du magasin d’itinéraire, basé sur le contenu du message ou le contexte.</span><span class="sxs-lookup"><span data-stu-id="c2f4c-117">The Itinerary Selector component uses a resolver specified as a property connection string, configured by the developer, to determine and select the appropriate itinerary from the itinerary store, based on message content or context.</span></span>  
  
-   <span data-ttu-id="c2f4c-118">Il valide l’itinéraire et définit des propriétés spécifiques à prédéfinir des valeurs par défaut s’ils sont null dans l’itinéraire ; par exemple :</span><span class="sxs-lookup"><span data-stu-id="c2f4c-118">It validates the itinerary and sets specific properties to preset default values if they are null in the itinerary; for example:</span></span>  
  
    -   <span data-ttu-id="c2f4c-119">Si le compte de Service est inférieur à 1, le composant lève une exception.</span><span class="sxs-lookup"><span data-stu-id="c2f4c-119">If Service count is less than 1, the component throws an exception.</span></span>  
  
    -   <span data-ttu-id="c2f4c-120">Le composant définit les attributs d’itinéraire racine en utilisant les valeurs pour le compte de Service, l’identificateur (**Uuid**), l’heure de début (**BeginTime**), et s’il s’agit d’une demande unidirectionnelle ou bidirectionnelle (**IsRequestResponse**).</span><span class="sxs-lookup"><span data-stu-id="c2f4c-120">The component sets the itinerary root attributes using the values for the Service count, the identifier (**Uuid**), the start time (**BeginTime**), and whether this is a one-way or two-way request (**IsRequestResponse**).</span></span>  
  
    -   <span data-ttu-id="c2f4c-121">Le composant valide les services, définit les identificateurs, définit l’instance de service en cours (le service à traiter suivant) et valide les programmes de résolution associés.</span><span class="sxs-lookup"><span data-stu-id="c2f4c-121">The component validates the services, sets the identifiers, sets the current service instance (the service to process next), and validates any associated resolvers.</span></span>  
  
    -   <span data-ttu-id="c2f4c-122">Le composant définit le segment de Microsoft BizTalk Server de l’itinéraire à l’aide des propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="c2f4c-122">The component sets the Microsoft BizTalk Server segment of the itinerary using the following properties:</span></span>  
  
        -   <span data-ttu-id="c2f4c-123">**correlationToken**</span><span class="sxs-lookup"><span data-stu-id="c2f4c-123">**correlationToken**</span></span>  
  
        -   <span data-ttu-id="c2f4c-124">**reqRespTransmitPipelineID**</span><span class="sxs-lookup"><span data-stu-id="c2f4c-124">**reqRespTransmitPipelineID**</span></span>  
  
        -   <span data-ttu-id="c2f4c-125">**interchangeId**</span><span class="sxs-lookup"><span data-stu-id="c2f4c-125">**interchangeId**</span></span>  
  
        -   <span data-ttu-id="c2f4c-126">**receiveInstanceId**</span><span class="sxs-lookup"><span data-stu-id="c2f4c-126">**receiveInstanceId**</span></span>  
  
        -   <span data-ttu-id="c2f4c-127">**epmRRCorrelationToken**</span><span class="sxs-lookup"><span data-stu-id="c2f4c-127">**epmRRCorrelationToken**</span></span>  
  
    -   <span data-ttu-id="c2f4c-128">Le composant écrit l’itinéraire modifié dans les propriétés de contexte de message BizTalk répertoriées dans le tableau suivant à l’aide des propriétés définies dans le schéma.xsd de système.</span><span class="sxs-lookup"><span data-stu-id="c2f4c-128">The component writes the modified itinerary to the BizTalk message context properties listed in the following table using the properties defined in the System-Properties.xsd schema.</span></span>  
  
        |<span data-ttu-id="c2f4c-129">Propriétés</span><span class="sxs-lookup"><span data-stu-id="c2f4c-129">Properties</span></span>|  
        |----------------|  
        |<span data-ttu-id="c2f4c-130">**Nom = ItineraryHeader**</span><span class="sxs-lookup"><span data-stu-id="c2f4c-130">**Name = ItineraryHeader**</span></span>|  
        |<span data-ttu-id="c2f4c-131">**Namespace = http://schemas.microsoft.biztalk.practices.esb.com/itinerary/system-properties**</span><span class="sxs-lookup"><span data-stu-id="c2f4c-131">**Namespace = http://schemas.microsoft.biztalk.practices.esb.com/itinerary/system-properties**</span></span>|  
  
    -   <span data-ttu-id="c2f4c-132">Le composant promeut les propriétés de contexte BizTalk quatre répertoriées dans le tableau suivant à l’aide des valeurs définies dans le schéma.xsd de système.</span><span class="sxs-lookup"><span data-stu-id="c2f4c-132">The component promotes the four BizTalk context properties listed in the following table using the values defined in the System-Properties.xsd schema.</span></span>  
  
        |<span data-ttu-id="c2f4c-133">Propriété</span><span class="sxs-lookup"><span data-stu-id="c2f4c-133">Property</span></span>|<span data-ttu-id="c2f4c-134">Valeur</span><span class="sxs-lookup"><span data-stu-id="c2f4c-134">Value</span></span>|  
        |--------------|-----------|  
        |<span data-ttu-id="c2f4c-135">**ServiceName**</span><span class="sxs-lookup"><span data-stu-id="c2f4c-135">**ServiceName**</span></span>|<span data-ttu-id="c2f4c-136">Le nom de l’instance actuelle de service défini dans la feuille de route.</span><span class="sxs-lookup"><span data-stu-id="c2f4c-136">The name of the current service instance defined in the itinerary.</span></span>|  
        |<span data-ttu-id="c2f4c-137">**ServiceType**</span><span class="sxs-lookup"><span data-stu-id="c2f4c-137">**ServiceType**</span></span>|<span data-ttu-id="c2f4c-138">La valeur **Orchestration** ou **de messagerie**.</span><span class="sxs-lookup"><span data-stu-id="c2f4c-138">Set to either **Orchestration** or **Messaging**.</span></span>|  
        |<span data-ttu-id="c2f4c-139">**IsRequestResponse**</span><span class="sxs-lookup"><span data-stu-id="c2f4c-139">**IsRequestResponse**</span></span>|<span data-ttu-id="c2f4c-140">La valeur **True** ou **False**.</span><span class="sxs-lookup"><span data-stu-id="c2f4c-140">Set to either **True** or **False**.</span></span>|  
        |<span data-ttu-id="c2f4c-141">**ServiceState**</span><span class="sxs-lookup"><span data-stu-id="c2f4c-141">**ServiceState**</span></span>|<span data-ttu-id="c2f4c-142">La valeur **en attente**.</span><span class="sxs-lookup"><span data-stu-id="c2f4c-142">Set to **Pending**.</span></span>|  
  
## <a name="esb-dispatcher-pipeline-component-process-steps"></a><span data-ttu-id="c2f4c-143">Étapes du processus de composant Pipeline ESB répartiteur</span><span class="sxs-lookup"><span data-stu-id="c2f4c-143">ESB Dispatcher Pipeline Component Process Steps</span></span>  
 <span data-ttu-id="c2f4c-144">Le composant de pipeline ESB répartiteur exécute les étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="c2f4c-144">The ESB Dispatcher pipeline component executes the following steps:</span></span>  
  
-   <span data-ttu-id="c2f4c-145">Il gère l’exécution de toutes les étapes d’itinéraire de type **messagerie** et avance la route.</span><span class="sxs-lookup"><span data-stu-id="c2f4c-145">It manages the execution of any itinerary steps of type **Messaging** and advances the itinerary.</span></span> <span data-ttu-id="c2f4c-146">Le composant ESB répartiteur est sensible à l’emplacement et exécute la logique en fonction de son emplacement dans le cycle de traitement messagerie, ce qui pourrait être **de réception entrant**, **envoyer transmettre**, **d’envoi Trafic entrant**, ou **de réception sortant**.</span><span class="sxs-lookup"><span data-stu-id="c2f4c-146">The ESB Dispatcher component is location-aware and executes logic based on its location in the messaging processing cycle, which could be **Receive Inbound**, **Send Transmit**, **Send Inbound**, or **Receive Outbound**.</span></span> <span data-ttu-id="c2f4c-147">Le composant de pipeline ESB répartiteur appelle ESB feuille de route des services de messagerie spécifiées dans le fichier Esb.config.</span><span class="sxs-lookup"><span data-stu-id="c2f4c-147">The ESB Dispatcher pipeline component invokes ESB itinerary messaging services specified in the Esb.config file.</span></span> <span data-ttu-id="c2f4c-148">Par défaut, les propriétés de configuration de ce composant pour le routage et la transformation sont associées avec les services suivants :</span><span class="sxs-lookup"><span data-stu-id="c2f4c-148">By default, the configuration properties of this component for routing and transformation are associated with the following services:</span></span>  
  
    -   <span data-ttu-id="c2f4c-149">**Microsoft.Practices.ESB.Services.Transform**.</span><span class="sxs-lookup"><span data-stu-id="c2f4c-149">**Microsoft.Practices.ESB.Services.Transform**.</span></span> <span data-ttu-id="c2f4c-150">Ce service exécute les mappages BizTalk par rapport à la charge utile d’un message entrant.</span><span class="sxs-lookup"><span data-stu-id="c2f4c-150">This service executes BizTalk maps against the payload of an inbound message.</span></span> <span data-ttu-id="c2f4c-151">Le service valide les exigences de transformation et met à jour les propriétés de contexte BizTalk qui contiennent le nom de spécification de document et le type de message.</span><span class="sxs-lookup"><span data-stu-id="c2f4c-151">The service validates transform requirements and updates the BizTalk context properties that contain the document specification name and the message type.</span></span> <span data-ttu-id="c2f4c-152">Le répartiteur ESB exécute ce service uniquement s’il s’agit du nom du service de transformation tel qu’il apparaît dans la propriété correspondante du composant de pipeline ESB répartiteur.</span><span class="sxs-lookup"><span data-stu-id="c2f4c-152">The ESB Dispatcher executes this service only if this is the name of the transform service as it appears in the corresponding property of the ESB Dispatcher pipeline component.</span></span>  
  
    -   <span data-ttu-id="c2f4c-153">**Microsoft.Practices.ESB.Services.Routing.**</span><span class="sxs-lookup"><span data-stu-id="c2f4c-153">**Microsoft.Practices.ESB.Services.Routing.**</span></span> <span data-ttu-id="c2f4c-154">Ce service utilise le programme de résolution et le fournisseur d’infrastructure d’adaptateurs pour définir les informations de routage de point de terminaison approprié.</span><span class="sxs-lookup"><span data-stu-id="c2f4c-154">This service uses the Resolver and Adapter Provider Framework to set the appropriate endpoint routing information.</span></span> <span data-ttu-id="c2f4c-155">Le répartiteur ESB exécute ce service uniquement s’il s’agit du nom du service de routage tel qu’il apparaît dans la propriété correspondante du composant de pipeline ESB répartiteur.</span><span class="sxs-lookup"><span data-stu-id="c2f4c-155">The ESB Dispatcher executes this service only if this is the name of the routing service as it appears in the corresponding property of the ESB Dispatcher pipeline component.</span></span>