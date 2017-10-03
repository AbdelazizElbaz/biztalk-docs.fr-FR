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
# <a name="the-resolverdictionary-class"></a>La classe ResolverDictionary
Le **ResolverDictionary** classe est un **dictionnaire**-basé sur la classe qui peut stocker des instances de la **résolveur** classe en tant que **chaîne** nom / paires de valeur. Lors de la création d’instances de la **ResolverDictionary** (classe), vous devez fournir une référence à un fichier **dictionnaire** instance. Le **ResolverDictionary** classe fournit les données qui le **résolveur** classe utilise lorsqu’elle effectue la résolution de l’exécution.  
  
 Le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] programme d’installation installe et enregistre le **Microsoft.Practices.ESB.Resolver.dll** assembly avec le **ResolverDictionary** classe dans le global assembly cache.  
  
 Le **ResolverDictionary** classe expose une méthode et une propriété :  
  
-   **Élément (** clé **)**. Cette méthode prend une valeur de chaîne qui contient un nom de clé. Elle retourne la valeur de chaîne correspondante ou une chaîne vide si l’élément n’existe pas dans l’objet sous-jacent **dictionnaire** instance.  
  
-   **BaseDictionary**. Cette propriété retourne une référence à l’objet sous-jacent **dictionnaire** instance.