---
title: "L’exécution d’un Service d’itinéraire | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7d86d228-da28-494f-85c7-4225b54f9b98
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f4a4dc5c201b26ec33ee5666bc0dbeec8f54ccfc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="executing-an-itinerary-service"></a><span data-ttu-id="2da9f-102">L’exécution d’un Service d’itinéraire</span><span class="sxs-lookup"><span data-stu-id="2da9f-102">Executing an Itinerary Service</span></span>
<span data-ttu-id="2da9f-103">Un itinéraire ESB peut contenir n’importe quel service d’itinéraire qui peut-être être implémentés sous la forme d’orchestration ou de messagerie pour effectuer les tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="2da9f-103">An ESB itinerary can contain any itinerary service that may be implemented as orchestration or messaging to perform the following tasks:</span></span>  
  
-   <span data-ttu-id="2da9f-104">Il peut recevoir le message contenant la feuille de route.</span><span class="sxs-lookup"><span data-stu-id="2da9f-104">It can receive the message containing the itinerary.</span></span>  
  
-   <span data-ttu-id="2da9f-105">Elle peut récupérer l’étape actuelle de l’itinéraire.</span><span class="sxs-lookup"><span data-stu-id="2da9f-105">It can retrieve the current itinerary step.</span></span>  
  
-   <span data-ttu-id="2da9f-106">Il peut traiter le service.</span><span class="sxs-lookup"><span data-stu-id="2da9f-106">It can process the service.</span></span>  
  
-   <span data-ttu-id="2da9f-107">Il peut faire avancer l’itinéraire sur le message sortant en appelant le **avance** (méthode).</span><span class="sxs-lookup"><span data-stu-id="2da9f-107">It can advance the itinerary on the outgoing message by calling the **Advance** method.</span></span>  
  
-   <span data-ttu-id="2da9f-108">Il peut publier le message traité dans la base de données MessageBox de BizTalk de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="2da9f-108">It can publish the processed message back into the Microsoft BizTalk Message Box database.</span></span>  
  
 <span data-ttu-id="2da9f-109">Par exemple, une orchestration peut recevoir un message qui contient un itinéraire en implémentant un filtre défini sur la forme réception activé, comme indiqué dans la Figure 1 de [à l’aide d’une Orchestration en tant qu’itinéraire Service abonné](../esb-toolkit/using-an-orchestration-as-an-itinerary-service-subscriber.md).</span><span class="sxs-lookup"><span data-stu-id="2da9f-109">For example, an orchestration can receive a message that contains an itinerary by implementing a filter defined on the activated receive shape, as shown in Figure 1 of [Using an Orchestration as an Itinerary Service Subscriber](../esb-toolkit/using-an-orchestration-as-an-itinerary-service-subscriber.md).</span></span> <span data-ttu-id="2da9f-110">Toutefois, la messagerie est légèrement différente : le composant de pipeline appelle la **GetItineraryStep** méthode pour déterminer si un itinéraire existe dans un message entrant.</span><span class="sxs-lookup"><span data-stu-id="2da9f-110">However, messaging is slightly different: the pipeline component calls the **GetItineraryStep** method to determine whether an itinerary exists in an incoming message.</span></span> <span data-ttu-id="2da9f-111">Il examine également les propriétés de message pour vérifier si elle doit le traiter.</span><span class="sxs-lookup"><span data-stu-id="2da9f-111">It also examines the message properties to check whether it should process it.</span></span>  
  
 <span data-ttu-id="2da9f-112">![Orchestration](../esb-toolkit/media/ch4-orchestration.jpg "chapitre 4-Orchestration")</span><span class="sxs-lookup"><span data-stu-id="2da9f-112">![Orchestration](../esb-toolkit/media/ch4-orchestration.jpg "Ch4-Orchestration")</span></span>  
  
 <span data-ttu-id="2da9f-113">**Figure 1**</span><span class="sxs-lookup"><span data-stu-id="2da9f-113">**Figure 1**</span></span>  
  
 <span data-ttu-id="2da9f-114">**Exemple d’expression de filtre d’une orchestration qui participe à une feuille de route en tant qu’abonné**</span><span class="sxs-lookup"><span data-stu-id="2da9f-114">**Example filter expression for an orchestration that will participate in an itinerary as a subscriber**</span></span>  
  
 <span data-ttu-id="2da9f-115">Une fois que le service Obtient le message, il doit appeler la **GetItineraryStep** méthode qui retourne une instance de la **ItineraryStep** classe.</span><span class="sxs-lookup"><span data-stu-id="2da9f-115">After the service obtains the message, it must call the **GetItineraryStep** method, which returns an instance of the **ItineraryStep** class.</span></span> <span data-ttu-id="2da9f-116">Les listes ci-dessous montrent comment vous pouvez appeler les méthodes de l’API de l’itinéraire à partir d’une orchestration et un composant de pipeline personnalisé.</span><span class="sxs-lookup"><span data-stu-id="2da9f-116">The following listings demonstrate how you can call the methods of the itinerary API from both an orchestration and a custom pipeline component.</span></span> <span data-ttu-id="2da9f-117">Le code suivant exécute la **GetItineraryStep** méthode à partir d’une forme Expression d’orchestration.</span><span class="sxs-lookup"><span data-stu-id="2da9f-117">The following code executes the **GetItineraryStep** method from an orchestration Expression shape.</span></span>  
  
```  
  
//XLANGs  
// Retrieve the current itinerary step.  
itinerary = new Microsoft.Practices.ESB.Itinerary.SerializableItineraryWrapper();  
step = new Microsoft.Practices.ESB.Itinerary.SerializableItineraryStepWrapper();  
  
itinerary.Itinerary = Microsoft.Practices.ESB.Itinerary.ItineraryOMFactory.Create(InboundMessage);  
step.ItineraryStep = itinerary.Itinerary.GetItineraryStep(InboundMessage);  
```  
  
 <span data-ttu-id="2da9f-118">Le code suivant montre comment exécuter la méthode de service de messagerie à partir d’un composant de pipeline personnalisé.</span><span class="sxs-lookup"><span data-stu-id="2da9f-118">The following code shows how to execute the messaging service method from a custom pipeline component.</span></span>  
  
```csharp  
// Execute messaging step.  
public IBaseMessage Execute(IPipelineContext context, IBaseMessage msg, string resolverString, IItineraryStep step)  
{  
    if (null != step  
    && step.ServiceType == "Messaging"  
    && step.ServiceName == "SomeService")  
    {  
        // If the service name matches the required name, process the message here.  
    }  
    else  
    {  
        // Do not process the message.  
        return pInMsg;  
    }  
}  
```  
  
 <span data-ttu-id="2da9f-119">L’instance de la **IItineraryStep** classe contient toutes les métadonnées pour le service en cours, y compris les propriétés ambiantes de l’environnement d’exécution de service actuel.</span><span class="sxs-lookup"><span data-stu-id="2da9f-119">The instance of the **IItineraryStep** class contains all the metadata for the current service, including ambient properties of the current service execution environment.</span></span> <span data-ttu-id="2da9f-120">Deux exemples sont les **ServiceInstanceID** et actuel **MessageDirection** propriétés d’un composant de pipeline.</span><span class="sxs-lookup"><span data-stu-id="2da9f-120">Two good examples of this are the **ServiceInstanceID** and the current **MessageDirection** properties for a pipeline component.</span></span>  
  
 <span data-ttu-id="2da9f-121">Après un service appelle la **GetItineraryStep** (méthode), il peut récupérer associés programmes de résolution.</span><span class="sxs-lookup"><span data-stu-id="2da9f-121">After a service calls the **GetItineraryStep** method, it can retrieve any associated resolvers.</span></span> <span data-ttu-id="2da9f-122">Le **ResolverCollection** propriété de la **ItineraryStep** classe retourne une collection de programmes de résolution que le service peut énumérer par le biais, comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="2da9f-122">The **ResolverCollection** property of the **ItineraryStep** class returns a collection of resolvers that the service can enumerate through, as shown in the following example.</span></span>  
  
```csharp  
Microsoft.Practices.ESB.Itinerary.ResolverCollection resolvers;  
resolvers = step.ItineraryStep.ResolverCollection;  
```  
  
 <span data-ttu-id="2da9f-123">Chaque élément dans le **ResolverCollection** représente une chaîne de connexion du programme de résolution correspondant à l’un des types pris en charge par le programme de résolution et l’infrastructure d’adaptateurs.</span><span class="sxs-lookup"><span data-stu-id="2da9f-123">Each item in the **ResolverCollection** represents a resolver connection string that matches one of the types supported by the Resolver and Adapter Framework.</span></span> <span data-ttu-id="2da9f-124">Par exemple, un élément dans la collection pourrait ressembler à la liste suivante.</span><span class="sxs-lookup"><span data-stu-id="2da9f-124">For example, an item in the collection could look like the following listing.</span></span>  
  
```idl  
BRE:\\policy=GetCanadaPurchaseEndPoint;version=;useMsg=;  
UDDI:\\serverUrl=http://localhost/uddi;serviceName=OrderFileServiceWBindings;  
STATIC:\\TransportLocation=http://localhost/ESB.CanadianServices/SubmitPOService.asmx;  
TargetNamespace=http://globalbank.esb.dynamicresolution.com/canadianservices/;  
XPATH:\\TransportType=; TransportLocation=/*[local-name()='OrderDoc' and namespace-  
uri()='http://globalbank.esb.dynamicresolution.com/northamericanservices/']/*  
[local-name()='ID' and namespace-  
uri()='http://globalbank.esb.dynamicresolution.com/northamericanservices/'];  
TargetNamespace=/*[local-name()='OrderDoc' and namespace-  
uri()='http://globalbank.esb.dynamicresolution.com/northamericanservices/']/*  
[local-name()='customerName' and namespace-  
uri()='http://globalbank.esb.dynamicresolution.com/northamericanservices/'];  
```  
  
 <span data-ttu-id="2da9f-125">Le Gestionnaire de programme de résolution dans l’infrastructure de fournisseur de carte et de programme de résolution peut résoudre les points de terminaison et définissez les propriétés de point de terminaison du message.</span><span class="sxs-lookup"><span data-stu-id="2da9f-125">The resolver manager in the Resolver and Adapter Provider Framework can resolve the endpoints and set the endpoint properties of the message.</span></span> <span data-ttu-id="2da9f-126">Pour plus d’informations sur la manière dont cela se produit, consultez [à l’aide de la résolution dynamique et routage](../esb-toolkit/using-dynamic-resolution-and-routing.md).</span><span class="sxs-lookup"><span data-stu-id="2da9f-126">For more information about how this occurs, see [Using Dynamic Resolution and Routing](../esb-toolkit/using-dynamic-resolution-and-routing.md).</span></span>  
  
 <span data-ttu-id="2da9f-127">Une fois que le service a terminé le traitement du message, il doit passer l’itinéraire sur le message sortant et publier le message dans la base de données de la boîte de Message.</span><span class="sxs-lookup"><span data-stu-id="2da9f-127">After the service finishes processing the message, it must advance the itinerary on the outgoing message and publish the message back to the Message Box database.</span></span> <span data-ttu-id="2da9f-128">L’exemple suivant illustre le processus d’une forme Expression d’orchestration.</span><span class="sxs-lookup"><span data-stu-id="2da9f-128">The following example shows the process for an orchestration Expression shape.</span></span>  
  
```xml  
  
//XLANGs  
// Copy the context to the outbound message.  
OutboundMessage = InboundMessage;  
OutboundMessage(*) = InboundMessage(*);  
  
// Call the method of the ItinerarySerializableWrapper to advance to the next step.  
itinerary.Itinerary.Advance(OutboundMessage, step.ItineraryStep);  
```  
  
 <span data-ttu-id="2da9f-129">L’exemple suivant montre comment indiquer que [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] moteur doit avancer l’itinéraire d’un composant de pipeline personnalisé.</span><span class="sxs-lookup"><span data-stu-id="2da9f-129">The following example shows how to indicate that [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] core engine should advance itinerary for a custom pipeline component.</span></span>  
  
```csharp  
// Advance Itinerary  
// <summary>  
// Signals that the step should be advanced immediately following execution of the service.  
// </summary>  
// <param name="step">Current step</param>  
// <param name="msg">Current message</param>  
// <returns>True to advance the itinerary.</returns>  
public bool ShouldAdvanceStep(IItineraryStep step, IBaseMessage msg)  
{  
    return true;  
}  
```