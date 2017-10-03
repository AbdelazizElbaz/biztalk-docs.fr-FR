---
title: "À l’aide de schémas | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pipeline components [custom], examples
- pipeline components [custom], code samples
- pipeline components [custom], schemas
ms.assetid: 07e60532-1032-422d-865e-0bd65c45dab6
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6a7cb71319fef61d3b6cb854b04b41e3815a6129
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="using-schemas"></a><span data-ttu-id="5dc35-102">À l’aide de schémas</span><span class="sxs-lookup"><span data-stu-id="5dc35-102">Using Schemas</span></span>
<span data-ttu-id="5dc35-103">Cette section présente des exemples de codes correspondant aux tâches communes associées à l'utilisation de schémas.</span><span class="sxs-lookup"><span data-stu-id="5dc35-103">This section contains code examples for common tasks associated with using schemas.</span></span>  
  
## <a name="using-xsd-schemas"></a><span data-ttu-id="5dc35-104">Utilisation des schémas XSD</span><span class="sxs-lookup"><span data-stu-id="5dc35-104">Using XSD schemas</span></span>  
 <span data-ttu-id="5dc35-105">Le `IDocumentSpec Interface` interface représente une forme de document définie par un schéma XML Schema definition language (XSD) ; associé à la forme par un élément de niveau supérieur du langage XSD.</span><span class="sxs-lookup"><span data-stu-id="5dc35-105">The `IDocumentSpec Interface` interface represents a document shape defined by an XML Schema definition language (XSD) schema; the shape is rooted by a top-level element of the XSD.</span></span> <span data-ttu-id="5dc35-106">Une fois que le schéma est installé, il peut être récupéré en appelant le `IPipelineContext.GetDocumentSpecByType Method` ou `IPipelineContext.GetDocumentSpecByName Method` méthodes dans le **IPipelineContext** interface.</span><span class="sxs-lookup"><span data-stu-id="5dc35-106">After the schema is installed, it can be retrieved by calling the `IPipelineContext.GetDocumentSpecByType Method` or `IPipelineContext.GetDocumentSpecByName Method` methods in the **IPipelineContext** interface.</span></span>  
  
```  
IDocumentSpec docspec = pipeineContext.GetDocumentSpecByType("myschema#root");  
```  
  
## <a name="using-xsd-flat-file-schemas"></a><span data-ttu-id="5dc35-107">Utilisation des schémas de fichier plat XSD</span><span class="sxs-lookup"><span data-stu-id="5dc35-107">Using XSD flat file schemas</span></span>  
 <span data-ttu-id="5dc35-108">Les deux le **GetDocumentSpecByType** et **GetDocumentSpecByName** méthodes retournent le **IDocumentSpec** interface.</span><span class="sxs-lookup"><span data-stu-id="5dc35-108">Both the **GetDocumentSpecByType** and **GetDocumentSpecByName** methods return the **IDocumentSpec** interface.</span></span> <span data-ttu-id="5dc35-109">Si le schéma est effectivement un schéma de fichier plat (celui qui a des annotations supplémentaires spécifiques au fichier plat), vous pouvez convertir le **IDocumentSpec** dans **IFFDocumentSpec** et lancer l’analyse et de sérialisation séquences à partir de là.</span><span class="sxs-lookup"><span data-stu-id="5dc35-109">If the schema is actually a flat file schema (one that has additional flat file-specific annotations), you can typecast the **IDocumentSpec** into **IFFDocumentSpec** and initiate parsing and serializing sequences from there.</span></span>  
  
```  
IFFDocumentSpec docspec = (IFFDocumentSpec) pipeineContext.GetDocumentSpecByType("myschema#root");  
```  
  
## <a name="see-also"></a><span data-ttu-id="5dc35-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5dc35-110">See Also</span></span>  

[<span data-ttu-id="5dc35-111">À l’aide de moteurs d’analyse et de sérialisation</span><span class="sxs-lookup"><span data-stu-id="5dc35-111">Using the Parsing and Serializing Engines</span></span>](../core/using-the-parsing-and-serializing-engines.md)