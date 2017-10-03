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
# <a name="using-schemas"></a>À l’aide de schémas
Cette section présente des exemples de codes correspondant aux tâches communes associées à l'utilisation de schémas.  
  
## <a name="using-xsd-schemas"></a>Utilisation des schémas XSD  
 Le `IDocumentSpec Interface` interface représente une forme de document définie par un schéma XML Schema definition language (XSD) ; associé à la forme par un élément de niveau supérieur du langage XSD. Une fois que le schéma est installé, il peut être récupéré en appelant le `IPipelineContext.GetDocumentSpecByType Method` ou `IPipelineContext.GetDocumentSpecByName Method` méthodes dans le **IPipelineContext** interface.  
  
```  
IDocumentSpec docspec = pipeineContext.GetDocumentSpecByType("myschema#root");  
```  
  
## <a name="using-xsd-flat-file-schemas"></a>Utilisation des schémas de fichier plat XSD  
 Les deux le **GetDocumentSpecByType** et **GetDocumentSpecByName** méthodes retournent le **IDocumentSpec** interface. Si le schéma est effectivement un schéma de fichier plat (celui qui a des annotations supplémentaires spécifiques au fichier plat), vous pouvez convertir le **IDocumentSpec** dans **IFFDocumentSpec** et lancer l’analyse et de sérialisation séquences à partir de là.  
  
```  
IFFDocumentSpec docspec = (IFFDocumentSpec) pipeineContext.GetDocumentSpecByType("myschema#root");  
```  
  
## <a name="see-also"></a>Voir aussi  

[À l’aide de moteurs d’analyse et de sérialisation](../core/using-the-parsing-and-serializing-engines.md)