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
# <a name="invoking-the-flat-file-parsing-engine"></a><span data-ttu-id="0dcfb-102">Appeler le moteur d’analyse de fichier plat</span><span class="sxs-lookup"><span data-stu-id="0dcfb-102">Invoking the Flat File Parsing Engine</span></span>
<span data-ttu-id="0dcfb-103">Le moteur d’analyse de fichier plat peut être appelé en appelant le **analyser** méthode de la **IFFDocumentSpec** interface, qui à son tour est convertie à partir la `IDocumentSpec Interface` récupérées à partir de la  **PipelineContext**.</span><span class="sxs-lookup"><span data-stu-id="0dcfb-103">The flat file parsing engine can be invoked by calling the **Parse** method of the **IFFDocumentSpec** interface, which in turn is typecast from the `IDocumentSpec Interface` retrieved from the **PipelineContext**.</span></span> <span data-ttu-id="0dcfb-104">Étant donné que la **XmlReader** retourné à partir de la **analyser** méthode permet aux clients de récupérer un seul nœud à la fois, il s’agit d’une bonne opportunité de personnaliser l’analyseur.</span><span class="sxs-lookup"><span data-stu-id="0dcfb-104">Because the **XmlReader** returned from the **Parse** method allows clients to retrieve one node at a time, this is a good opportunity to customize the parser.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0dcfb-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="0dcfb-105">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0dcfb-106">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0dcfb-106">See Also</span></span>  
 [<span data-ttu-id="0dcfb-107">Utilisation du moteur d’analyse de fichier plat</span><span class="sxs-lookup"><span data-stu-id="0dcfb-107">Using the Flat File Parsing Engine</span></span>](../core/using-the-flat-file-parsing-engine.md)