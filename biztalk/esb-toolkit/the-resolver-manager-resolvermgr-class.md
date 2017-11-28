---
title: "La classe de gestionnaire de programme de résolution (ResolverMgr) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 89fa551d-0aca-4777-adbc-2bc46ab8664a
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6621ad0c6b9edb5bf93950f9b9d05a7655f0e36d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="the-resolver-manager-resolvermgr-class"></a><span data-ttu-id="1c6f5-102">La classe de gestionnaire de programme de résolution (ResolverMgr)</span><span class="sxs-lookup"><span data-stu-id="1c6f5-102">The Resolver Manager (ResolverMgr) Class</span></span>
<span data-ttu-id="1c6f5-103">La transformation et le routage de messagerie des services utilisent le **ResolverMgr** classe pour effectuer la résolution.</span><span class="sxs-lookup"><span data-stu-id="1c6f5-103">The Transform and Routing messaging services use the **ResolverMgr** class to perform resolution.</span></span> <span data-ttu-id="1c6f5-104">La transformation dynamique de ESB et les agents de distribution dynamique utilisent également le **ResolverManager** classe pour effectuer une résolution juste-à-temps (JIT).</span><span class="sxs-lookup"><span data-stu-id="1c6f5-104">The ESB dynamic transformation and dynamic delivery agents also use the **ResolverManager** class to perform just-in-time (JIT) resolution.</span></span>  
  
 <span data-ttu-id="1c6f5-105">Le programme d’installation ESB Core installe et enregistre le **Microsoft.Practices.ESB.Resolver.dll** assembly avec le **ResolverMgr** classe dans le global assembly cache.</span><span class="sxs-lookup"><span data-stu-id="1c6f5-105">The ESB Core installer installs and registers the **Microsoft.Practices.ESB.Resolver.dll** assembly with the **ResolverMgr** class in the global assembly cache.</span></span>  
  
 <span data-ttu-id="1c6f5-106">Vous pouvez utiliser cette classe dans votre propre code où vous avez besoin effectuer la résolution dynamique des mappages ou des points de terminaison.</span><span class="sxs-lookup"><span data-stu-id="1c6f5-106">You can use this class in your own code where you need to perform dynamic resolution of endpoints or maps.</span></span> <span data-ttu-id="1c6f5-107">Vous pouvez également étendre cette classe pour utiliser une méthode de résolution personnalisé.</span><span class="sxs-lookup"><span data-stu-id="1c6f5-107">You can also extend this class to use a custom resolution method.</span></span> <span data-ttu-id="1c6f5-108">Toutefois, gardez à l’esprit que la classe prend déjà en charge un mécanisme de résolution que vous pouvez utiliser n’importe quel assembly du programme de résolution personnalisé, qui doit s’adapter à n’importe quel algorithme de résolution autre que vous pouvez avoir besoin.</span><span class="sxs-lookup"><span data-stu-id="1c6f5-108">However, keep in mind that the class already supports a resolution mechanism that can use any custom resolver assembly, which should accommodate any alternative resolution algorithm you may require.</span></span>  
  
 <span data-ttu-id="1c6f5-109">L’exemple de code suivant montre comment utiliser le **ResolverMgr** classe pour résoudre un point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="1c6f5-109">The following code example shows how to use the **ResolverMgr** class to resolve an endpoint.</span></span>  
  
```csharp  
// Move to retrieve the first resolver.  
resolvers = itineraryStep.ResolverCollection;  
resolver = resolvers.Current;  
  
// Pass the resolver configuration to the Resolver Manager for resolution.  
resolverDictionary = Microsoft.Practices.ESB.Resolver.ResolverMgr.Resolve(InboundMessage, resolver);  
  
// Set transport properties.  
transportLocation = resolverDictionary.Item("Resolver.TransportLocation");  
transportType = resolverDictionary.Item("Resolver.TransportType");  
```  
  
 <span data-ttu-id="1c6f5-110">En règle générale, votre chaîne de connexion du programme de résolution spécifie les valeurs de propriété de résolution au moins une méthode, par exemple une stratégie de règles, un assembly personnalisé, une instruction XPath ou un Universal Description, Discovery and Integration (UDDI) étiquette et nom de serveur.</span><span class="sxs-lookup"><span data-stu-id="1c6f5-110">Usually, your resolver connection string specifies the property values for at least one resolution method, such as a rules policy, custom assembly, XPath statement, or Universal Description, Discovery, and Integration (UDDI) label and server name.</span></span> <span data-ttu-id="1c6f5-111">Enfin, elle retourne un objet de dictionnaire avec un ensemble d’informations de programme de résolution, qui peuvent être facilement remplis avec les faits personnalisés à partir d’un programme de résolution concrète.</span><span class="sxs-lookup"><span data-stu-id="1c6f5-111">Finally, it returns a dictionary object with a collection of resolver facts, which can be easily populated with custom facts from a concrete resolver.</span></span>  
  
 <span data-ttu-id="1c6f5-112">Pour plus d’informations sur comment fonctionne le mécanisme de résolution ESB, consultez [à l’aide de la résolution dynamique et routage](../esb-toolkit/using-dynamic-resolution-and-routing.md).</span><span class="sxs-lookup"><span data-stu-id="1c6f5-112">For more information about how the ESB resolution mechanism works, see [Using Dynamic Resolution and Routing](../esb-toolkit/using-dynamic-resolution-and-routing.md).</span></span>