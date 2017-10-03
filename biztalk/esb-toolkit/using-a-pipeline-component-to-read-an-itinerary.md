---
title: "À l’aide d’un composant de Pipeline pour lire un itinéraire | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7e3b40c7-0f17-4d33-a26f-f51346a98be5
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bceec4df732247be043e006b52c7abbfbf6a6b24
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="using-a-pipeline-component-to-read-an-itinerary"></a><span data-ttu-id="74716-102">À l’aide d’un composant de Pipeline pour lire un itinéraire</span><span class="sxs-lookup"><span data-stu-id="74716-102">Using a Pipeline Component to Read an Itinerary</span></span>
<span data-ttu-id="74716-103">Un message qui arrive dans un pipeline de réception peut contenir des métadonnées dans son en-tête SOAP qui définit ses besoins de traitement (itinéraire côté client).</span><span class="sxs-lookup"><span data-stu-id="74716-103">A message that arrives in a receive pipeline can contain metadata in its SOAP header that defines its processing requirements (client-side itinerary).</span></span> <span data-ttu-id="74716-104">La figure 1 illustre l’utilisation de l’itinéraire d’ESB et composants de pipeline ESB répartiteur.</span><span class="sxs-lookup"><span data-stu-id="74716-104">Figure 1 illustrates the use of the ESB Itinerary and ESB Dispatcher pipeline components.</span></span>  
  
 <span data-ttu-id="74716-105">![Lecture de composant de pipeline](../esb-toolkit/media/ch4-pipelinecomponentread.gif "PipelineComponentRead de chapitre 4")</span><span class="sxs-lookup"><span data-stu-id="74716-105">![Pipeline Component Read](../esb-toolkit/media/ch4-pipelinecomponentread.gif "Ch4-PipelineComponentRead")</span></span>  
  
 <span data-ttu-id="74716-106">**Figure 1**</span><span class="sxs-lookup"><span data-stu-id="74716-106">**Figure 1**</span></span>  
  
 <span data-ttu-id="74716-107">**Exemple d’un composant de pipeline ESB itinéraire**</span><span class="sxs-lookup"><span data-stu-id="74716-107">**Example of an ESB Itinerary pipeline component**</span></span>  
  
 <span data-ttu-id="74716-108">Un composant de pipeline ESB itinéraire peut être utilisé pour capturer les métadonnées à partir d’un message en tant que propriétés de contexte qui peuvent définir le traitement appliqué par l’architecture ESB.</span><span class="sxs-lookup"><span data-stu-id="74716-108">An ESB Itinerary pipeline component can be used to capture the metadata from a message as context properties that can define the processing applied by the ESB.</span></span>  
  
 <span data-ttu-id="74716-109">Les sections suivantes décrivent les étapes effectuées par chaque composant.</span><span class="sxs-lookup"><span data-stu-id="74716-109">The following sections describe the steps performed by each component.</span></span>  
  
## <a name="esb-itinerary-pipeline-component-process-steps"></a><span data-ttu-id="74716-110">Étapes de processus de composant de Pipeline d’itinéraire ESB</span><span class="sxs-lookup"><span data-stu-id="74716-110">ESB Itinerary Pipeline Component Process Steps</span></span>  
 <span data-ttu-id="74716-111">Dans l’exemple illustré dans la Figure 1, le composant de pipeline ESB itinéraire exécute les étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="74716-111">In the example shown in Figure 1, the ESB Itinerary pipeline component executes the following steps:</span></span>  
  
-   <span data-ttu-id="74716-112">Il lit l’en-tête SOAP de l’itinéraire.</span><span class="sxs-lookup"><span data-stu-id="74716-112">It reads the itinerary SOAP header.</span></span> <span data-ttu-id="74716-113">La partie présentant le définit l’itinéraire en remplissant l’en-tête SOAP lorsqu’il envoie le message.</span><span class="sxs-lookup"><span data-stu-id="74716-113">The submitting party sets the itinerary by populating the SOAP header when he or she submits the message.</span></span> <span data-ttu-id="74716-114">Une série de propriétés de contexte du message BizTalk représentent l’en-tête SOAP ; Ces propriétés varient, selon le type de carte de service Web qui est utilisé.</span><span class="sxs-lookup"><span data-stu-id="74716-114">A series of BizTalk message context properties represent the SOAP header; these properties vary, depending on the type of Web service adapter that is used.</span></span> <span data-ttu-id="74716-115">Les cartes de service Web pertinentes sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="74716-115">The following are the relevant Web service adapters:</span></span>  
  
    -   <span data-ttu-id="74716-116">**Adaptateur WCF.**</span><span class="sxs-lookup"><span data-stu-id="74716-116">**WCF adapter.**</span></span> <span data-ttu-id="74716-117">Cette carte traite les en-têtes SOAP et remplit les propriétés de contexte de message BizTalk répertoriées dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="74716-117">This adapter parses the SOAP headers and populates the BizTalk message context properties listed in the following table.</span></span>  
  
        |<span data-ttu-id="74716-118">Propriétés</span><span class="sxs-lookup"><span data-stu-id="74716-118">Properties</span></span>|  
        |----------------|  
        |<span data-ttu-id="74716-119">**Nom = feuille de route**</span><span class="sxs-lookup"><span data-stu-id="74716-119">**Name = Itinerary**</span></span>|  
        |<span data-ttu-id="74716-120">**Namespace = http://schemas.microsoft.biztalk.practices.esb.com/itinerary**</span><span class="sxs-lookup"><span data-stu-id="74716-120">**Namespace = http://schemas.microsoft.biztalk.practices.esb.com/itinerary**</span></span>|  
  
        > [!NOTE]
        >  <span data-ttu-id="74716-121">Par défaut, l’adaptateur Windows Communication Foundation (WCF) utilise le nom racine du schéma nommé ItineraryDescription.xsd (ce schéma est utilisé pour générer l’en-tête SOAP d’itinéraire ESB) comme contexte BizTalk **nom** argument, et il utilise l’espace de noms cible du schéma en tant que le contexte de BizTalk **Namespace** argument.</span><span class="sxs-lookup"><span data-stu-id="74716-121">By default, the Windows Communication Foundation (WCF) adapter uses the root name of the schema named ItineraryDescription.xsd (this schema is used to generate the ESB Itinerary SOAP header) as the BizTalk context **Name** argument, and it uses the target namespace of the schema as the BizTalk context **Namespace** argument.</span></span>  
  
    -   <span data-ttu-id="74716-122">**Adaptateur SOAP.**</span><span class="sxs-lookup"><span data-stu-id="74716-122">**SOAP adapter.**</span></span> <span data-ttu-id="74716-123">Cette carte traite les en-têtes SOAP et remplit les propriétés de contexte de message BizTalk répertoriées dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="74716-123">This adapter parses the SOAP headers and populates the BizTalk message context properties listed in the following table.</span></span>  
  
        |<span data-ttu-id="74716-124">Propriétés</span><span class="sxs-lookup"><span data-stu-id="74716-124">Properties</span></span>|  
        |----------------|  
        |<span data-ttu-id="74716-125">**Nom = feuille de route**</span><span class="sxs-lookup"><span data-stu-id="74716-125">**Name = Itinerary**</span></span>|  
        |<span data-ttu-id="74716-126">**Namespace = http://schemas.microsoft.com/BizTalk/2003/SOAPHeader**</span><span class="sxs-lookup"><span data-stu-id="74716-126">**Namespace = http://schemas.microsoft.com/BizTalk/2003/SOAPHeader**</span></span>|  
  
        > [!NOTE]
        >  <span data-ttu-id="74716-127">Par défaut, l’adaptateur SOAP utilise le nom racine du schéma nommé Itinerary.xsd (ce schéma est utilisé pour générer l’en-tête SOAP d’itinéraire ESB) comme contexte BizTalk **nom** argument et qu’il utilise l’espace de noms de l’en-tête SOAP, comme le Contexte de BizTalk **Namespace** argument.</span><span class="sxs-lookup"><span data-stu-id="74716-127">By default, the SOAP Adapter uses the root name of the schema named Itinerary.xsd (this schema is used to generate the ESB Itinerary SOAP header) as the BizTalk context **Name** argument, and it uses the namespace of the SOAP header as the BizTalk context **Namespace** argument.</span></span>  
  
-   <span data-ttu-id="74716-128">Il supprime la valeur d’itinéraire d’origine à partir du contexte de message.</span><span class="sxs-lookup"><span data-stu-id="74716-128">It removes the original itinerary value from the message context.</span></span>  
  
-   <span data-ttu-id="74716-129">Il valide l’itinéraire et définit des propriétés spécifiques à prédéfinir des valeurs par défaut s’ils sont null dans l’itinéraire ; par exemple :</span><span class="sxs-lookup"><span data-stu-id="74716-129">It validates the itinerary and sets specific properties to preset default values if they are null in the itinerary; for example:</span></span>  
  
    -   <span data-ttu-id="74716-130">Si le compte de Service est inférieur à 1, le composant lève une exception.</span><span class="sxs-lookup"><span data-stu-id="74716-130">If Service count is less than 1, the component throws an exception.</span></span>  
  
    -   <span data-ttu-id="74716-131">Le composant définit les attributs d’itinéraire racine en utilisant les valeurs pour le compte de Service, l’identificateur (**Uuid**), l’heure de début (**BeginTime**), et s’il s’agit d’une demande unidirectionnelle ou bidirectionnelle (**IsRequestResponse**).</span><span class="sxs-lookup"><span data-stu-id="74716-131">The component sets the itinerary root attributes using the values for the Service count, the identifier (**Uuid**), the start time (**BeginTime**), and whether this is a one-way or two-way request (**IsRequestResponse**).</span></span>  
  
    -   <span data-ttu-id="74716-132">Le composant valide les services, définit les identificateurs, définit l’instance de service en cours (le service à traiter suivant) et valide les programmes de résolution associés.</span><span class="sxs-lookup"><span data-stu-id="74716-132">The component validates the services, sets the identifiers, sets the current service instance (the service to process next), and validates any associated resolvers.</span></span>  
  
    -   <span data-ttu-id="74716-133">Le composant définit le BizTalk Segment de l’itinéraire à l’aide des propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="74716-133">The component sets the BizTalk Segment of the itinerary using the following properties:</span></span>  
  
        -   <span data-ttu-id="74716-134">**correlationToken**</span><span class="sxs-lookup"><span data-stu-id="74716-134">**correlationToken**</span></span>  
  
        -   <span data-ttu-id="74716-135">**reqRespTransmitPipelineID**</span><span class="sxs-lookup"><span data-stu-id="74716-135">**reqRespTransmitPipelineID**</span></span>  
  
        -   <span data-ttu-id="74716-136">**interchangeId**</span><span class="sxs-lookup"><span data-stu-id="74716-136">**interchangeId**</span></span>  
  
        -   <span data-ttu-id="74716-137">**receiveInstanceId**</span><span class="sxs-lookup"><span data-stu-id="74716-137">**receiveInstanceId**</span></span>  
  
        -   <span data-ttu-id="74716-138">**epmRRCorrelationToken**</span><span class="sxs-lookup"><span data-stu-id="74716-138">**epmRRCorrelationToken**</span></span>  
  
    -   <span data-ttu-id="74716-139">Le composant écrit l’itinéraire modifié dans les propriétés de contexte de message BizTalk répertoriées dans le tableau suivant à l’aide des propriétés définies dans le schéma.xsd de système.</span><span class="sxs-lookup"><span data-stu-id="74716-139">The component writes the modified itinerary to the BizTalk message context properties listed in the following table using the properties defined in the System-Properties.xsd schema.</span></span>  
  
        |<span data-ttu-id="74716-140">Propriétés</span><span class="sxs-lookup"><span data-stu-id="74716-140">Properties</span></span>|  
        |----------------|  
        |<span data-ttu-id="74716-141">**Nom = ItineraryHeader**</span><span class="sxs-lookup"><span data-stu-id="74716-141">**Name = ItineraryHeader**</span></span>|  
        |<span data-ttu-id="74716-142">**Namespace = http://schemas.microsoft.biztalk.practices.esb.com/itinerary/system-properties**</span><span class="sxs-lookup"><span data-stu-id="74716-142">**Namespace = http://schemas.microsoft.biztalk.practices.esb.com/itinerary/system-properties**</span></span>|  
  
    -   <span data-ttu-id="74716-143">Le composant promeut les propriétés de contexte BizTalk quatre répertoriées dans le tableau suivant à l’aide des valeurs définies dans le schéma.xsd de système.</span><span class="sxs-lookup"><span data-stu-id="74716-143">The component promotes the four BizTalk context properties listed in the following table using the values defined in the System-Properties.xsd schema.</span></span>  
  
        |<span data-ttu-id="74716-144">Propriété</span><span class="sxs-lookup"><span data-stu-id="74716-144">Property</span></span>|<span data-ttu-id="74716-145">Valeur</span><span class="sxs-lookup"><span data-stu-id="74716-145">Value</span></span>|  
        |--------------|-----------|  
        |<span data-ttu-id="74716-146">**ServiceName**</span><span class="sxs-lookup"><span data-stu-id="74716-146">**ServiceName**</span></span>|<span data-ttu-id="74716-147">Le nom de l’instance actuelle de service défini dans la feuille de route.</span><span class="sxs-lookup"><span data-stu-id="74716-147">The name of the current service instance defined in the itinerary.</span></span>|  
        |<span data-ttu-id="74716-148">**ServiceType**</span><span class="sxs-lookup"><span data-stu-id="74716-148">**ServiceType**</span></span>|<span data-ttu-id="74716-149">La valeur **Orchestration** ou **de messagerie**</span><span class="sxs-lookup"><span data-stu-id="74716-149">Set to either **Orchestration** or **Messaging**</span></span>|  
        |<span data-ttu-id="74716-150">**IsRequestResponse**</span><span class="sxs-lookup"><span data-stu-id="74716-150">**IsRequestResponse**</span></span>|<span data-ttu-id="74716-151">La valeur **True** ou **False**</span><span class="sxs-lookup"><span data-stu-id="74716-151">Set to either **True** or **False**</span></span>|  
        |<span data-ttu-id="74716-152">**ServiceState**</span><span class="sxs-lookup"><span data-stu-id="74716-152">**ServiceState**</span></span>|<span data-ttu-id="74716-153">La valeur **en attente**</span><span class="sxs-lookup"><span data-stu-id="74716-153">Set to **Pending**</span></span>|  
  
## <a name="esb-dispatcher-pipeline-component-process-steps"></a><span data-ttu-id="74716-154">Étapes du processus de composant Pipeline ESB répartiteur</span><span class="sxs-lookup"><span data-stu-id="74716-154">ESB Dispatcher Pipeline Component Process Steps</span></span>  
 <span data-ttu-id="74716-155">Dans l’exemple illustré dans la Figure 1, le composant de pipeline ESB répartiteur exécute les étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="74716-155">In the example shown in Figure 1, the ESB Dispatcher pipeline component executes the following steps:</span></span>  
  
-   <span data-ttu-id="74716-156">Il gère l’exécution de toutes les étapes d’itinéraire de type **messagerie** et avance la route.</span><span class="sxs-lookup"><span data-stu-id="74716-156">It manages the execution of any itinerary steps of type **Messaging** and advances the itinerary.</span></span> <span data-ttu-id="74716-157">Le composant ESB répartiteur est sensible à l’emplacement et exécute la logique en fonction de son emplacement dans le cycle de traitement messagerie, ce qui pourrait être **de réception entrant, d’envoi de transmission**, **envoyer le trafic entrant**, ou **De réception sortant**.</span><span class="sxs-lookup"><span data-stu-id="74716-157">The ESB Dispatcher component is location-aware and executes logic based on its location in the messaging processing cycle, which could be **Receive Inbound, Send Transmit**, **Send Inbound**, or **Receive Outbound**.</span></span> <span data-ttu-id="74716-158">Le composant de pipeline ESB répartiteur appelle ESB feuille de route des services de messagerie spécifiées dans le fichier Esb.config.</span><span class="sxs-lookup"><span data-stu-id="74716-158">The ESB Dispatcher pipeline component invokes ESB itinerary messaging services specified in the Esb.config file.</span></span> <span data-ttu-id="74716-159">Par défaut, les propriétés de configuration de ce composant pour le routage et la transformation sont associées avec les services suivants :</span><span class="sxs-lookup"><span data-stu-id="74716-159">By default, the configuration properties of this component for routing and transformation are associated with the following services:</span></span>  
  
    -   <span data-ttu-id="74716-160">**Microsoft.Practices.ESB.Services.Transform.**</span><span class="sxs-lookup"><span data-stu-id="74716-160">**Microsoft.Practices.ESB.Services.Transform.**</span></span> <span data-ttu-id="74716-161">Ce service exécute les mappages BizTalk par rapport à la charge utile d’un message entrant.</span><span class="sxs-lookup"><span data-stu-id="74716-161">This service executes BizTalk maps against the payload of an inbound message.</span></span> <span data-ttu-id="74716-162">Le service valide les exigences de transformation et met à jour les propriétés de contexte BizTalk qui contiennent le nom de spécification de document et le type de message.</span><span class="sxs-lookup"><span data-stu-id="74716-162">The service validates transform requirements and updates the BizTalk context properties that contain the document specification name and the message type.</span></span> <span data-ttu-id="74716-163">Le répartiteur ESB exécute ce service uniquement s’il s’agit du nom du service de transformation tel qu’il apparaît dans la propriété correspondante du composant de pipeline ESB répartiteur.</span><span class="sxs-lookup"><span data-stu-id="74716-163">The ESB Dispatcher executes this service only if this is the name of the transform service as it appears in the corresponding property of the ESB Dispatcher pipeline component.</span></span>  
  
    -   <span data-ttu-id="74716-164">**Microsoft.Practices.ESB.Services.Routing.** Ce service utilise le programme de résolution et le fournisseur d’infrastructure d’adaptateurs pour définir les informations de routage de point de terminaison approprié.</span><span class="sxs-lookup"><span data-stu-id="74716-164">**Microsoft.Practices.ESB.Services.Routing.**This service uses the Resolver and Adapter Provider Framework to set the appropriate endpoint routing information.</span></span> <span data-ttu-id="74716-165">Le répartiteur ESB exécute ce service uniquement s’il s’agit du nom du service de routage tel qu’il apparaît dans la propriété correspondante du composant de pipeline ESB répartiteur.</span><span class="sxs-lookup"><span data-stu-id="74716-165">The ESB Dispatcher executes this service only if this is the name of the routing service as it appears in the corresponding property of the ESB Dispatcher pipeline component.</span></span>