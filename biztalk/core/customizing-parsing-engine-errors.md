---
title: "Personnalisation des erreurs du moteur d’analyse | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pipeline components [custom], errors
- pipeline components [custom], code samples
ms.assetid: d9a0060b-49c0-4690-956b-d31668f23c41
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1d0bd99d1cad6703e16ba8536625539881ae4c0d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="customizing-parsing-engine-errors"></a><span data-ttu-id="3b42c-102">Personnalisation des erreurs du moteur d’analyse</span><span class="sxs-lookup"><span data-stu-id="3b42c-102">Customizing Parsing Engine Errors</span></span>
<span data-ttu-id="3b42c-103">Vous pouvez définir votre propre rappel de gestion des erreurs grâce au moteur d'analyse approprié.</span><span class="sxs-lookup"><span data-stu-id="3b42c-103">You can register your own error-handling callback with the parsing engine to handle errors.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3b42c-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="3b42c-104">Example</span></span>  
  
```  
bool MyErrorHandler(ErrorContext ctx)  
{  
   // Handle the error  
   return true;  
   // true=continue parsing, false=stop  
}  
  
FFReader ffr = (FFReader)docspec.Parse(new DataReader());  
ffr.OnErrorEvent += MyErrorHandler;  
```  
  
## <a name="see-also"></a><span data-ttu-id="3b42c-105">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3b42c-105">See Also</span></span>  
 [<span data-ttu-id="3b42c-106">Utilisation du moteur d’analyse de fichier plat</span><span class="sxs-lookup"><span data-stu-id="3b42c-106">Using the Flat File Parsing Engine</span></span>](../core/using-the-flat-file-parsing-engine.md)