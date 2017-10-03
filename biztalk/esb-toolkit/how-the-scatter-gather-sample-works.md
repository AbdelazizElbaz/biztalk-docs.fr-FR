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
# <a name="how-the-scatter-gather-sample-works"></a>Fonctionne de l’exemple de ventilation-regroupement
Génère un ensemble d’en-têtes SOAP qui contient l’itinéraire chargé à partir du fichier de feuille de route de ventilation-regroupement, charge le fichier de message spécifié à partir du disque, ajoute les en-têtes d’itinéraire pour le message et l’envoie à l’architecture ESB via une rampe d’entrée pour l’exemple d’application lors du traitement. Si l’itinéraire génère une réponse, l’application de cette collecte et affiche dans la fenêtre d’application.  
  
 Pour vous aider à comprendre comment le service de l’itinéraire utilise les informations d’itinéraire dans un message, la liste suivante montre l’exemple de fichier de configuration d’itinéraire nommé ScatterGatherItinerary.xml. La première section de cet itinéraire spécifie deux étapes d’appel de service.  
  
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
  
 La liste des étapes d’appel de service dans l’itinéraire est la section contenant les détails de la résolution et les chaînes de connexion qui permettent au service de l’itinéraire rechercher chaque service défini dans l’itinéraire, comme indiqué dans le code XML suivant.  
  
```xml  
<ResolverGroups xmlns="">  
 <Resolvers serviceId="ScatterGather0"><![CDATA[BRE:\\policy=ResolveEndPointScatterGather;version=;useMsg=;]]><![CDATA[UDDI3:\\serverUrl=http://localhost/uddi;bindingKey=uddi:esb:purchaseordersubmitorderservicebinding;credentialType=Ntlm]]></Resolvers>  
<Resolvers serviceId="DynamicTest1"><![CDATA[UDDI3:\\serverUrl=http://localhost/uddi;bindingKey=uddi:esb:orderfileservicebinding;credentialType=Ntlm]]>  
</Resolvers>  
  </ResolverGroups>  
```  
  
 Dans cet exemple, l’application exécute le site SubmitPOService Web service deux fois, car les deux chaînes de connexion du programme de résolution résoudre à l’emplacement de ce service (http://localhost/ESB.CanadianServices/SubmitPOService.asmx). Le contexte de message Spécifie l’orchestration du courtier comme le premier service d’itinéraire à activer, défini dans l’exemple comme suit.  
  
```csharp  
(Microsoft.Practices.ESB.Itinerary.Schemas.ServiceName == "ScatterGather")  
     && (Microsoft.Practices.ESB.Itinerary.Schemas.ServiceState ==   
    "Pending") && (Microsoft.Practices.ESB.Itinerary.Schemas.ServiceType   
    == "Orchestration")  
```  
  
 L’orchestration du courtier analyse les paramètres de l’étape de son itinéraire et récupère une collection de programmes de résolution associé à l’étape de l’itinéraire. Pour chacun de ces programmes de résolution, l’orchestration utilise la [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] programme de résolution et infrastructure d’adaptateurs pour résoudre le point de terminaison de service. L’orchestration du courtier puis active un nombre n d’orchestrations de distributeur de services en mode asynchrone (où n est le nombre de programmes de résolution associé au service ScatterGather dans la feuille de route) pour distribuer le message de demande avec les paramètres suivants :  
  
-   **TransportLocation**. Le programme de résolution remplit ce paramètre.  
  
-   **Type de transport**. Le programme de résolution remplit ce paramètre.  
  
-   **ResolverDictionary**. Ce paramètre contient une collection de faits de programme de résolution remplie par l’instance de programme de résolution concrète.  
  
-   **InboundMessage**. Ce paramètre contient le message d’origine qui contient l’itinéraire.  
  
-   **ServiceResponsePort**. Ce paramètre est le nom du port de réponse autocorrélation pour recevoir les réponses à partir des instances de l’orchestration de distributeur de services.  
  
 Chaque instance de l’orchestration de distributeur de services utilise la stratégie ResolveMapScatterGather pour résoudre les types de mappage de Microsoft BizTalk pour le message de demande et de réponse, en fonction de **TransportType** et  **TransportLocation** propriétés. Les instances d’orchestration utilisent les mappages résolus pour transformer le message entrant dans le message de demande pour l’appel de service Web.  
  
 Le Gestionnaire d’adaptateur ESB définit des propriétés de contexte du transport sortant sur le message de demande, les transfère vers le port de sollicitation-réponse ensuite le BizTalk nommé ServiceRequestPort.  
  
 Lorsqu’il reçoit un message de réponse d’un service, l’orchestration de distributeur de services utilise les informations de mappage résolu pour transformer le message de réponse entrant dans un format canonique. Ensuite, il encapsule la réponse modifiée dans l’enveloppe ServiceResponse et transmet à l’orchestration du courtier via le port d’autocorrélation. L’orchestration du courtier regroupe toutes les réponses entrantes et prépare le dernier message de réponse à l’aide de GlobalBank.ESB.ScatterGather.Processes.AggregatingPipeline, comme indiqué dans le code suivant.  
  
```csharp  
AggregatedResponse.Body = null;  
AggregatedResponse(*) = InboundMessage(*);  
Microsoft.XLANGs.Pipeline.XLANGPipelineManager.ExecuteSendPipeline(  
    typeof(GlobalBank.ESB.ScatterGather.Processes.AggregatingPipeline),  
    messageAggregator,AggregatedResponse);  
```  
  
 Ce code encapsule la totalité du traitement des réponses dans une enveloppe prédéfinie. L’orchestration du courtier puis avance la route le **DynamicTest** étape de l’itinéraire, comme indiqué dans le code suivant.  
  
```csharp  
// Copy the context and advance the itinerary.  
OutboundMessage = AggregatedResponse.Body;  
OutboundMessage(*) = AggregatedResponse(*);  
// Advance the Itinerary to the next step.  
itinerary.Itinerary.Advance(OutboundMessage, itineraryStep);  
```  
  
 Étant donné que l’attribut de type de service nommé **DynamicTest** a la valeur **messagerie**, le **ItineraryHelper** classe promeut les propriétés du programme de résolution dans le contexte de la message nommé **OutboundMessage**. L’orchestration du courtier envoie ce message à un port de liaison directe de BizTalk. BizTalk transmet le message au port d’envoi dynamique représenté par le **ServiceName** abonnement, qui est **DynamicTest**. Ce port d’envoi sérialise la réponse finale agrégée dans le dossier \Source\Samples\DynamicResolution\Test\Filedrop\Out.