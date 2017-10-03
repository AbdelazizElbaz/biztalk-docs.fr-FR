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
# <a name="the-resolver-manager-resolvermgr-class"></a>La classe de gestionnaire de programme de résolution (ResolverMgr)
La transformation et le routage de messagerie des services utilisent le **ResolverMgr** classe pour effectuer la résolution. La transformation dynamique de ESB et les agents de distribution dynamique utilisent également le **ResolverManager** classe pour effectuer une résolution juste-à-temps (JIT).  
  
 Le programme d’installation ESB Core installe et enregistre le **Microsoft.Practices.ESB.Resolver.dll** assembly avec le **ResolverMgr** classe dans le global assembly cache.  
  
 Vous pouvez utiliser cette classe dans votre propre code où vous avez besoin effectuer la résolution dynamique des mappages ou des points de terminaison. Vous pouvez également étendre cette classe pour utiliser une méthode de résolution personnalisé. Toutefois, gardez à l’esprit que la classe prend déjà en charge un mécanisme de résolution que vous pouvez utiliser n’importe quel assembly du programme de résolution personnalisé, qui doit s’adapter à n’importe quel algorithme de résolution autre que vous pouvez avoir besoin.  
  
 L’exemple de code suivant montre comment utiliser le **ResolverMgr** classe pour résoudre un point de terminaison.  
  
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
  
 En règle générale, votre chaîne de connexion du programme de résolution spécifie les valeurs de propriété de résolution au moins une méthode, par exemple une stratégie de règles, un assembly personnalisé, une instruction XPath ou un Universal Description, Discovery and Integration (UDDI) étiquette et nom de serveur. Enfin, elle retourne un objet de dictionnaire avec un ensemble d’informations de programme de résolution, qui peuvent être facilement remplis avec les faits personnalisés à partir d’un programme de résolution concrète.  
  
 Pour plus d’informations sur comment fonctionne le mécanisme de résolution ESB, consultez [à l’aide de la résolution dynamique et routage](../esb-toolkit/using-dynamic-resolution-and-routing.md).