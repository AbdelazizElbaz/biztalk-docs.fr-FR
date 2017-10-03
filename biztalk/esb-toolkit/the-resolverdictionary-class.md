---
title: La classe ResolverDictionary | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 46deb8a0-0523-4a5c-ac6b-45c506de7a72
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a2dfe0082ffc7f7b68c5c56811a28d5ccd20e93e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="the-resolverdictionary-class"></a><span data-ttu-id="e8d0f-102">La classe ResolverDictionary</span><span class="sxs-lookup"><span data-stu-id="e8d0f-102">The ResolverDictionary Class</span></span>
<span data-ttu-id="e8d0f-103">Le **ResolverDictionary** classe est un **dictionnaire**-basé sur la classe qui peut stocker des instances de la **résolveur** classe en tant que **chaîne** nom / paires de valeur.</span><span class="sxs-lookup"><span data-stu-id="e8d0f-103">The **ResolverDictionary** class is a **Dictionary**-based class that can store instances of the **Resolver** class as **String** name/value pairs.</span></span> <span data-ttu-id="e8d0f-104">Lors de la création d’instances de la **ResolverDictionary** (classe), vous devez fournir une référence à un fichier **dictionnaire** instance.</span><span class="sxs-lookup"><span data-stu-id="e8d0f-104">When creating instances of the **ResolverDictionary** class, you must provide a reference to an existing **Dictionary** instance.</span></span> <span data-ttu-id="e8d0f-105">Le **ResolverDictionary** classe fournit les données qui le **résolveur** classe utilise lorsqu’elle effectue la résolution de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="e8d0f-105">The **ResolverDictionary** class provides the data that the **Resolver** class uses when it performs run-time resolution.</span></span>  
  
 <span data-ttu-id="e8d0f-106">Le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] programme d’installation installe et enregistre le **Microsoft.Practices.ESB.Resolver.dll** assembly avec le **ResolverDictionary** classe dans le global assembly cache.</span><span class="sxs-lookup"><span data-stu-id="e8d0f-106">The [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] installer installs and registers the **Microsoft.Practices.ESB.Resolver.dll** assembly with the **ResolverDictionary** class in the global assembly cache.</span></span>  
  
 <span data-ttu-id="e8d0f-107">Le **ResolverDictionary** classe expose une méthode et une propriété :</span><span class="sxs-lookup"><span data-stu-id="e8d0f-107">The **ResolverDictionary** class exposes one method and one property:</span></span>  
  
-   <span data-ttu-id="e8d0f-108">**Élément (** clé **)**.</span><span class="sxs-lookup"><span data-stu-id="e8d0f-108">**Item(** key **)**.</span></span> <span data-ttu-id="e8d0f-109">Cette méthode prend une valeur de chaîne qui contient un nom de clé.</span><span class="sxs-lookup"><span data-stu-id="e8d0f-109">This method takes a string value that contains a key name.</span></span> <span data-ttu-id="e8d0f-110">Elle retourne la valeur de chaîne correspondante ou une chaîne vide si l’élément n’existe pas dans l’objet sous-jacent **dictionnaire** instance.</span><span class="sxs-lookup"><span data-stu-id="e8d0f-110">It returns the corresponding string value or an empty string if the item does not exist in the underlying **Dictionary** instance.</span></span>  
  
-   <span data-ttu-id="e8d0f-111">**BaseDictionary**.</span><span class="sxs-lookup"><span data-stu-id="e8d0f-111">**BaseDictionary**.</span></span> <span data-ttu-id="e8d0f-112">Cette propriété retourne une référence à l’objet sous-jacent **dictionnaire** instance.</span><span class="sxs-lookup"><span data-stu-id="e8d0f-112">This property returns a reference to the underlying **Dictionary** instance.</span></span>