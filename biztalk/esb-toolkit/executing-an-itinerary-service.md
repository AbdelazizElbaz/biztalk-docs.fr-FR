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
# <a name="executing-an-itinerary-service"></a>L’exécution d’un Service d’itinéraire
Un itinéraire ESB peut contenir n’importe quel service d’itinéraire qui peut-être être implémentés sous la forme d’orchestration ou de messagerie pour effectuer les tâches suivantes :  
  
-   Il peut recevoir le message contenant la feuille de route.  
  
-   Elle peut récupérer l’étape actuelle de l’itinéraire.  
  
-   Il peut traiter le service.  
  
-   Il peut faire avancer l’itinéraire sur le message sortant en appelant le **avance** (méthode).  
  
-   Il peut publier le message traité dans la base de données MessageBox de BizTalk de Microsoft.  
  
 Par exemple, une orchestration peut recevoir un message qui contient un itinéraire en implémentant un filtre défini sur la forme réception activé, comme indiqué dans la Figure 1 de [à l’aide d’une Orchestration en tant qu’itinéraire Service abonné](../esb-toolkit/using-an-orchestration-as-an-itinerary-service-subscriber.md). Toutefois, la messagerie est légèrement différente : le composant de pipeline appelle la **GetItineraryStep** méthode pour déterminer si un itinéraire existe dans un message entrant. Il examine également les propriétés de message pour vérifier si elle doit le traiter.  
  
 ![Orchestration](../esb-toolkit/media/ch4-orchestration.jpg "chapitre 4-Orchestration")  
  
 **Figure 1**  
  
 **Exemple d’expression de filtre d’une orchestration qui participe à une feuille de route en tant qu’abonné**  
  
 Une fois que le service Obtient le message, il doit appeler la **GetItineraryStep** méthode qui retourne une instance de la **ItineraryStep** classe. Les listes ci-dessous montrent comment vous pouvez appeler les méthodes de l’API de l’itinéraire à partir d’une orchestration et un composant de pipeline personnalisé. Le code suivant exécute la **GetItineraryStep** méthode à partir d’une forme Expression d’orchestration.  
  
```  
  
//XLANGs  
// Retrieve the current itinerary step.  
itinerary = new Microsoft.Practices.ESB.Itinerary.SerializableItineraryWrapper();  
step = new Microsoft.Practices.ESB.Itinerary.SerializableItineraryStepWrapper();  
  
itinerary.Itinerary = Microsoft.Practices.ESB.Itinerary.ItineraryOMFactory.Create(InboundMessage);  
step.ItineraryStep = itinerary.Itinerary.GetItineraryStep(InboundMessage);  
```  
  
 Le code suivant montre comment exécuter la méthode de service de messagerie à partir d’un composant de pipeline personnalisé.  
  
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
  
 L’instance de la **IItineraryStep** classe contient toutes les métadonnées pour le service en cours, y compris les propriétés ambiantes de l’environnement d’exécution de service actuel. Deux exemples sont les **ServiceInstanceID** et actuel **MessageDirection** propriétés d’un composant de pipeline.  
  
 Après un service appelle la **GetItineraryStep** (méthode), il peut récupérer associés programmes de résolution. Le **ResolverCollection** propriété de la **ItineraryStep** classe retourne une collection de programmes de résolution que le service peut énumérer par le biais, comme indiqué dans l’exemple suivant.  
  
```csharp  
Microsoft.Practices.ESB.Itinerary.ResolverCollection resolvers;  
resolvers = step.ItineraryStep.ResolverCollection;  
```  
  
 Chaque élément dans le **ResolverCollection** représente une chaîne de connexion du programme de résolution correspondant à l’un des types pris en charge par le programme de résolution et l’infrastructure d’adaptateurs. Par exemple, un élément dans la collection pourrait ressembler à la liste suivante.  
  
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
  
 Le Gestionnaire de programme de résolution dans l’infrastructure de fournisseur de carte et de programme de résolution peut résoudre les points de terminaison et définissez les propriétés de point de terminaison du message. Pour plus d’informations sur la manière dont cela se produit, consultez [à l’aide de la résolution dynamique et routage](../esb-toolkit/using-dynamic-resolution-and-routing.md).  
  
 Une fois que le service a terminé le traitement du message, il doit passer l’itinéraire sur le message sortant et publier le message dans la base de données de la boîte de Message. L’exemple suivant illustre le processus d’une forme Expression d’orchestration.  
  
```xml  
  
//XLANGs  
// Copy the context to the outbound message.  
OutboundMessage = InboundMessage;  
OutboundMessage(*) = InboundMessage(*);  
  
// Call the method of the ItinerarySerializableWrapper to advance to the next step.  
itinerary.Itinerary.Advance(OutboundMessage, step.ItineraryStep);  
```  
  
 L’exemple suivant montre comment indiquer que [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] moteur doit avancer l’itinéraire d’un composant de pipeline personnalisé.  
  
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