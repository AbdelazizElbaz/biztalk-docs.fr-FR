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
# <a name="using-the-resolver-components-in-your-code"></a><span data-ttu-id="3b05e-102">Utiliser les composants du programme de résolution dans votre Code</span><span class="sxs-lookup"><span data-stu-id="3b05e-102">Using the Resolver Components in Your Code</span></span>
<span data-ttu-id="3b05e-103">Le fragment de code suivant à partir de l’agent de la transformation dynamique montre la fonctionnalité de résolution par défaut juste-à-temps (JIT).</span><span class="sxs-lookup"><span data-stu-id="3b05e-103">The following code fragment from the dynamic transformation agent shows the default just-in-time (JIT) resolution functionality.</span></span> <span data-ttu-id="3b05e-104">Vous pouvez facilement implémenter résolution dans votre application à l’aide d’un code similaire.</span><span class="sxs-lookup"><span data-stu-id="3b05e-104">You can easily implement resolution in your own application by using similar code.</span></span>  
  
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
  
 <span data-ttu-id="3b05e-105">Dans la liste précédente, le **résoudre** méthode de la **ResolverMgr** classe retourne un **dictionnaire** objet qui contient toutes les propriétés de la résolution par défaut et leurs valeurs résolues.</span><span class="sxs-lookup"><span data-stu-id="3b05e-105">In the preceding listing, the **Resolve** method of the **ResolverMgr** class returns a **Dictionary** object that contains all the default resolution properties and their resolved values.</span></span> <span data-ttu-id="3b05e-106">N’importe quel programme de résolution personnalisé peut ajouter des propriétés personnalisées pour le **dictionnaire** objet ; faire cela rend ces propriétés sont disponibles pour tout service personnalisé de l’itinéraire.</span><span class="sxs-lookup"><span data-stu-id="3b05e-106">Any custom resolver can add custom properties to the **Dictionary** object; doing this makes those properties available to any custom itinerary service.</span></span>  
  
 <span data-ttu-id="3b05e-107">Le tableau suivant présente les propriétés qui peuvent être éventuellement remplies par les programmes de résolution inclus dans le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3b05e-107">The following table shows the properties that can be optionally populated by the resolvers included in the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)].</span></span> <span data-ttu-id="3b05e-108">Tout itinéraire service peut récupérer ces valeurs de propriété en les extrayant de retourné **dictionnaire** objet.</span><span class="sxs-lookup"><span data-stu-id="3b05e-108">Any itinerary service can retrieve these property values by extracting them from the returned **Dictionary** object.</span></span>  
  
 <span data-ttu-id="3b05e-109">**Propriétés**:</span><span class="sxs-lookup"><span data-stu-id="3b05e-109">**Properties**:</span></span>  
  
||||  
|-|-|-|  
|<span data-ttu-id="3b05e-110">**Resolver.Action**</span><span class="sxs-lookup"><span data-stu-id="3b05e-110">**Resolver.Action**</span></span>|<span data-ttu-id="3b05e-111">**Resolver.ActionField**</span><span class="sxs-lookup"><span data-stu-id="3b05e-111">**Resolver.ActionField**</span></span>|<span data-ttu-id="3b05e-112">**Resolver.DocumentSpecName**</span><span class="sxs-lookup"><span data-stu-id="3b05e-112">**Resolver.DocumentSpecName**</span></span>|  
|<span data-ttu-id="3b05e-113">**Resolver.Success**</span><span class="sxs-lookup"><span data-stu-id="3b05e-113">**Resolver.Success**</span></span>|<span data-ttu-id="3b05e-114">**Resolver.EndpointConfig**</span><span class="sxs-lookup"><span data-stu-id="3b05e-114">**Resolver.EndpointConfig**</span></span>|<span data-ttu-id="3b05e-115">**Resolver.DocumentSpecStrongName**</span><span class="sxs-lookup"><span data-stu-id="3b05e-115">**Resolver.DocumentSpecStrongName**</span></span>|  
|<span data-ttu-id="3b05e-116">**Resolver.FixJaxRpc**</span><span class="sxs-lookup"><span data-stu-id="3b05e-116">**Resolver.FixJaxRpc**</span></span>|<span data-ttu-id="3b05e-117">**Resolver.InboundTransportType**</span><span class="sxs-lookup"><span data-stu-id="3b05e-117">**Resolver.InboundTransportType**</span></span>|<span data-ttu-id="3b05e-118">**Resolver.EpmRRCorrelationToken**</span><span class="sxs-lookup"><span data-stu-id="3b05e-118">**Resolver.EpmRRCorrelationToken**</span></span>|  
|<span data-ttu-id="3b05e-119">**Resolver.InterchangeId**</span><span class="sxs-lookup"><span data-stu-id="3b05e-119">**Resolver.InterchangeId**</span></span>|<span data-ttu-id="3b05e-120">**Resolver.IsRequestResponse**</span><span class="sxs-lookup"><span data-stu-id="3b05e-120">**Resolver.IsRequestResponse**</span></span>|<span data-ttu-id="3b05e-121">**Resolver.InboundTransportLocation**</span><span class="sxs-lookup"><span data-stu-id="3b05e-121">**Resolver.InboundTransportLocation**</span></span>|  
|<span data-ttu-id="3b05e-122">**Resolver.MessageType**</span><span class="sxs-lookup"><span data-stu-id="3b05e-122">**Resolver.MessageType**</span></span>|<span data-ttu-id="3b05e-123">**Resolver.MethodName**</span><span class="sxs-lookup"><span data-stu-id="3b05e-123">**Resolver.MethodName**</span></span>|<span data-ttu-id="3b05e-124">**Resolver.MessageExchangePattern**</span><span class="sxs-lookup"><span data-stu-id="3b05e-124">**Resolver.MessageExchangePattern**</span></span>|  
|<span data-ttu-id="3b05e-125">**Resolver.ReceivePortName**</span><span class="sxs-lookup"><span data-stu-id="3b05e-125">**Resolver.ReceivePortName**</span></span>|<span data-ttu-id="3b05e-126">**Resolver.TransportLocation**</span><span class="sxs-lookup"><span data-stu-id="3b05e-126">**Resolver.TransportLocation**</span></span>|<span data-ttu-id="3b05e-127">**Resolver.OutboundTransportCLSID**</span><span class="sxs-lookup"><span data-stu-id="3b05e-127">**Resolver.OutboundTransportCLSID**</span></span>|  
|<span data-ttu-id="3b05e-128">**Resolver.TransformType**</span><span class="sxs-lookup"><span data-stu-id="3b05e-128">**Resolver.TransformType**</span></span>|<span data-ttu-id="3b05e-129">**Resolver.TargetNamespace**</span><span class="sxs-lookup"><span data-stu-id="3b05e-129">**Resolver.TargetNamespace**</span></span>|<span data-ttu-id="3b05e-130">**Resolver.ReceiveLocationName**</span><span class="sxs-lookup"><span data-stu-id="3b05e-130">**Resolver.ReceiveLocationName**</span></span>|  
|<span data-ttu-id="3b05e-131">**Resolver.TransportType**</span><span class="sxs-lookup"><span data-stu-id="3b05e-131">**Resolver.TransportType**</span></span>|<span data-ttu-id="3b05e-132">**Resolver.TransportNamespace**</span><span class="sxs-lookup"><span data-stu-id="3b05e-132">**Resolver.TransportNamespace**</span></span>|<span data-ttu-id="3b05e-133">**Resolver.WindowUserField**</span><span class="sxs-lookup"><span data-stu-id="3b05e-133">**Resolver.WindowUserField**</span></span>|  
|<span data-ttu-id="3b05e-134">**Resolver.CacheTimeout**</span><span class="sxs-lookup"><span data-stu-id="3b05e-134">**Resolver.CacheTimeout**</span></span>|||  
  
 <span data-ttu-id="3b05e-135">Une fois le programme de résolution manager renvoie le **dictionnaire** instance d’objet, le Gestionnaire d’adaptateur définit les propriétés de contexte de l’adaptateur BizTalk spécifiques du message.</span><span class="sxs-lookup"><span data-stu-id="3b05e-135">After the resolver manager returns the **Dictionary** object instance, the adapter manager sets the specific BizTalk Adapter Context properties of the message.</span></span> <span data-ttu-id="3b05e-136">Le fragment de code suivant à partir de l’agent de routage montre comment vous pouvez utiliser le Gestionnaire d’adaptateur pour définir les propriétés de point de terminaison du message sortant.</span><span class="sxs-lookup"><span data-stu-id="3b05e-136">The following code fragment from the routing agent demonstrates how you can use the adapter manager to set the endpoint properties of the outgoing message.</span></span>  
  
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
  
 <span data-ttu-id="3b05e-137">Le fragment de code suivant à partir de l’agent de routage montre comment utiliser le Gestionnaire d’adaptateur à partir d’un composant de pipeline personnalisé pour définir les propriétés de point de terminaison d’un message sortant.</span><span class="sxs-lookup"><span data-stu-id="3b05e-137">The following code fragment from the routing agent demonstrates how to use the adapter manager from within a custom pipeline component to set the endpoint properties of an outgoing message.</span></span>  
  
```csharp  
// Resolve the configuration for routing.  
ResolverDictionary = ResolverMgr.Resolve(info, pInMsg, pContext);  
  
// Call the adapter manager to set all required message properties.  
AdapterMgr.SetEndpoint(ResolverDictionary, pInMsg.Context);  
```