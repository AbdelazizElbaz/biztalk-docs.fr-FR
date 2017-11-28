---
title: "Encapsule le moteur d’analyse | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pipeline components [custom], wrapping
- pipeline components [custom], code samples
ms.assetid: e00994de-bb86-40c0-a891-3f202147b5fe
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 99d6960ba2f5f795a37bb336dab227f23eb12353
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="wrapping-the-parsing-engine"></a><span data-ttu-id="13ed0-102">Encapsule le moteur d’analyse</span><span class="sxs-lookup"><span data-stu-id="13ed0-102">Wrapping the Parsing Engine</span></span>
<span data-ttu-id="13ed0-103">Vous pouvez créer vos propres **XmlReader** qui incorpore le lecteur retourné par le **analyser** (méthode) et permet une personnalisation.</span><span class="sxs-lookup"><span data-stu-id="13ed0-103">You can create your own **XmlReader** that embeds the reader returned by the **Parse** method and provides customization.</span></span>  
  
## <a name="example"></a><span data-ttu-id="13ed0-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="13ed0-104">Example</span></span>  
  
```  
class MyXmlReader : XmlReader  
{  
   public MyXmlReader(XmlReader xr)  
   {  
      _xr = xr;  
   }  
  
   // Overrides XmlReader and provides customized functionality of _xr  
   // ...  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="13ed0-105">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="13ed0-105">See Also</span></span>  
 [<span data-ttu-id="13ed0-106">Utilisation du moteur d’analyse de fichier plat</span><span class="sxs-lookup"><span data-stu-id="13ed0-106">Using the Flat File Parsing Engine</span></span>](../core/using-the-flat-file-parsing-engine.md)