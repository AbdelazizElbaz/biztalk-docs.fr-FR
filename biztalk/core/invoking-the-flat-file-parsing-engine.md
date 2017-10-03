---
title: "Moteur d’analyse du fichier appeler le plat | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pipeline components [custom], code samples
- IFFDocumentSpec interface
- pipeline components [custom], flat file documents
- pipeline components [custom], engines
ms.assetid: 9c5d325e-2fae-4291-af13-3fb06657ec0e
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 90108ff2ade354c51f87499a388ae54135f14c7f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="invoking-the-flat-file-parsing-engine"></a>Appeler le moteur d’analyse de fichier plat
Le moteur d’analyse de fichier plat peut être appelé en appelant le **analyser** méthode de la **IFFDocumentSpec** interface, qui à son tour est convertie à partir la `IDocumentSpec Interface` récupérées à partir de la  **PipelineContext**. Étant donné que la **XmlReader** retourné à partir de la **analyser** méthode permet aux clients de récupérer un seul nœud à la fois, il s’agit d’une bonne opportunité de personnaliser l’analyseur.  
  
## <a name="example"></a>Exemple  
  
```  
XmlReader xr = docspec.Parse(new DataReader());  
while (xr.Read())  
{  
   switch(xr.NodeType)  
   {  
      case XmlNodeType.Element :  
         // Customize the element  
         //   
         break;  
      case XmlNodeType.Attribute :  
         // Customize the attribute  
         //   
         break;  
      // Customize other types of nodes  
      //   
   }  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation du moteur d’analyse de fichier plat](../core/using-the-flat-file-parsing-engine.md)