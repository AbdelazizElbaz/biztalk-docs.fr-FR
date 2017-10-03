---
title: "S’abonner à et l’extraction des Messages | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4e7fbc17-44d6-4cc5-a266-b54256e7b453
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 22d5a7f6065e8040e390947d44510bb7414e8e10
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="subscribing-to-and-extracting-messages"></a><span data-ttu-id="0716a-102">S’abonner à et l’extraction des Messages</span><span class="sxs-lookup"><span data-stu-id="0716a-102">Subscribing to and Extracting Messages</span></span>
<span data-ttu-id="0716a-103">Orchestration peut contenir du code pour s’abonner et extraire les messages d’un message d’erreur ESB.</span><span class="sxs-lookup"><span data-stu-id="0716a-103">Orchestration can contain code to subscribe to and extract messages from an ESB fault message.</span></span> <span data-ttu-id="0716a-104">Par exemple, le code suivant utilise la **GetMessage** et **GetException** pour extraire deux fortement typée de messages et la **System.Exception** objet à partir d’une architecture ESB message d’erreur.</span><span class="sxs-lookup"><span data-stu-id="0716a-104">For example, the following code uses the **GetMessage** and **GetException** methods to extract two strongly typed messages and the **System.Exception** object from an ESB fault message.</span></span>  
  
```csharp  
// Retrieve two messages from the fault message.  
requestMsg = Microsoft.Practices.ESB.ExceptionHandling.ExceptionMgmt.GetMessage(  
                                    faultMsg, "ApprovedRequest");  
deniedMsg = Microsoft.Practices.ESB.ExceptionHandling.ExceptionMgmt.GetMessage(  
                                    faultMsg, "DeniedRequest");  
  
// Retrieve the System.Exception object.  
newExc = Microsoft.Practices.ESB.ExceptionHandling.ExceptionMgmt.GetException(  
                                    faultMsg);  
```  
  
 <span data-ttu-id="0716a-105">Pour extraire les messages sans type, le code suivant utilise la **GetMessages** méthode pour extraire tous les messages et à les parcourir.</span><span class="sxs-lookup"><span data-stu-id="0716a-105">To extract type-less messages, the following code uses the **GetMessages** method to extract all the messages and then iterate through them.</span></span>  
  
```csharp  
Microsoft.Practices.ESB.ExceptionHandling.MessageCollection msgs;  
msgs = Microsoft.Practices.ESB.ExceptionHandling.ExceptionMgmt.GetMessages(faultMsg);  
System.Xml.XmlDocument tmpMsg;  
while (msgs.MoveNext())  
{  
  tmpMsg = msgs.Current;  
}  
```