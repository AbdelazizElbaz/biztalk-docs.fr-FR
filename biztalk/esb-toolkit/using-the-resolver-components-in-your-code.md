---
title: "Utiliser les composants du programme de résolution dans votre Code | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d197cb28-78a9-4c8a-872b-f61ef15e6622
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 220ae4983f2fcbf60f6de02f818095fe5c0c50a7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="using-the-resolver-components-in-your-code"></a>Utiliser les composants du programme de résolution dans votre Code
Le fragment de code suivant à partir de l’agent de la transformation dynamique montre la fonctionnalité de résolution par défaut juste-à-temps (JIT). Vous pouvez facilement implémenter résolution dans votre application à l’aide d’un code similaire.  
  
```  
  
//XLANGs  
itinerary = new Microsoft.Practices.ESB.Itinerary.SerializableItineraryWrapper();  
step = new Microsoft.Practices.ESB.Itinerary.SerializableItineraryStepWrapper();  
  
itinerary.Itinerary = Microsoft.Practices.ESB.Itinerary.ItineraryOMFactory.Create(InboundMessage);  
step.ItineraryStep = itinerary.Itinerary.GetItineraryStep(InboundMessage);  
resolvers = step.ItineraryStep.ResolverCollection;  
resolvers.MoveNext();  
resolver = resolvers.Current;  
  
// Pass the resolver configuration to the Resolver mgr for resolution.  
resolverDictionary = Microsoft.Practices.ESB.Resolver.ResolverMgr.Resolve(InboundMessage, resolver);  
  
// Set the transform type.  
transformType = resolverDictionary.Item("Resolver.TransformType");  
```  
  
 Dans la liste précédente, le **résoudre** méthode de la **ResolverMgr** classe retourne un **dictionnaire** objet qui contient toutes les propriétés de la résolution par défaut et leurs valeurs résolues. N’importe quel programme de résolution personnalisé peut ajouter des propriétés personnalisées pour le **dictionnaire** objet ; faire cela rend ces propriétés sont disponibles pour tout service personnalisé de l’itinéraire.  
  
 Le tableau suivant présente les propriétés qui peuvent être éventuellement remplies par les programmes de résolution inclus dans le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]. Tout itinéraire service peut récupérer ces valeurs de propriété en les extrayant de retourné **dictionnaire** objet.  
  
 **Propriétés**:  
  
||||  
|-|-|-|  
|**Resolver.Action**|**Resolver.ActionField**|**Resolver.DocumentSpecName**|  
|**Resolver.Success**|**Resolver.EndpointConfig**|**Resolver.DocumentSpecStrongName**|  
|**Resolver.FixJaxRpc**|**Resolver.InboundTransportType**|**Resolver.EpmRRCorrelationToken**|  
|**Resolver.InterchangeId**|**Resolver.IsRequestResponse**|**Resolver.InboundTransportLocation**|  
|**Resolver.MessageType**|**Resolver.MethodName**|**Resolver.MessageExchangePattern**|  
|**Resolver.ReceivePortName**|**Resolver.TransportLocation**|**Resolver.OutboundTransportCLSID**|  
|**Resolver.TransformType**|**Resolver.TargetNamespace**|**Resolver.ReceiveLocationName**|  
|**Resolver.TransportType**|**Resolver.TransportNamespace**|**Resolver.WindowUserField**|  
|**Resolver.CacheTimeout**|||  
  
 Une fois le programme de résolution manager renvoie le **dictionnaire** instance d’objet, le Gestionnaire d’adaptateur définit les propriétés de contexte de l’adaptateur BizTalk spécifiques du message. Le fragment de code suivant à partir de l’agent de routage montre comment vous pouvez utiliser le Gestionnaire d’adaptateur pour définir les propriétés de point de terminaison du message sortant.  
  
```  
  
//XLANGs  
// Set the transport properties.  
transportLocation = resolverDictionary.Item("Resolver.TransportLocation");  
transportType = resolverDictionary.Item("Resolver.TransportType");  
  
// Create the delivery message.  
DeliveryMessage = InboundMessage;  
  
// Call the adapter manager to set all necessary properties on the message.  
Microsoft.Practices.ESB.Adapter.AdapterMgr.SetEndpoint(  
                                resolverDictionary,DeliveryMessage);  
  
// Set the delivery port address.  
DeliveryPort(Microsoft.XLANGs.BaseTypes.Address) = transportLocation;  
DeliveryPort(Microsoft.XLANGs.BaseTypes.TransportType) = transportType;  
```  
  
 Le fragment de code suivant à partir de l’agent de routage montre comment utiliser le Gestionnaire d’adaptateur à partir d’un composant de pipeline personnalisé pour définir les propriétés de point de terminaison d’un message sortant.  
  
```csharp  
// Resolve the configuration for routing.  
ResolverDictionary = ResolverMgr.Resolve(info, pInMsg, pContext);  
  
// Call the adapter manager to set all required message properties.  
AdapterMgr.SetEndpoint(ResolverDictionary, pInMsg.Context);  
```