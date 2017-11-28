---
title: "Méthode Policy.Dispose | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: db37c6b9-acf0-42ee-9356-4d1567934862
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ba4713616edf55c149a215a6f7842cd5d0353dfe
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="policydispose-method"></a><span data-ttu-id="045cd-102">Méthode Policy.Dispose</span><span class="sxs-lookup"><span data-stu-id="045cd-102">Policy.Dispose Method</span></span>
<span data-ttu-id="045cd-103">Le **Policy.Dispose** méthode libère les ressources utilisées par le **stratégie** classe, puis retourne également le **stratégie** objet au cache.</span><span class="sxs-lookup"><span data-stu-id="045cd-103">The **Policy.Dispose** method releases resources used by the **Policy** class, and also returns the **Policy** object to the cache.</span></span> <span data-ttu-id="045cd-104">Lorsque la même stratégie est à nouveau appelée, la mise en cache **stratégie** objet est utilisé, ce qui permet d’économiser le temps nécessaire à la création d’un **stratégie** objet.</span><span class="sxs-lookup"><span data-stu-id="045cd-104">When the same policy is invoked again, the cached **Policy** object is used, which saves the time needed for creating a new **Policy** object.</span></span>  
  
 <span data-ttu-id="045cd-105">Si vous n’avez pas explicitement appelez la **Policy.Dispose** (méthode), puis la stratégie n’est pas retourné dans le cache jusqu'à ce que le runtime .NET permet de libérer l’objet pendant le processus de garbage collection.</span><span class="sxs-lookup"><span data-stu-id="045cd-105">If you do not explicitly call the **Policy.Dispose** method, then the policy is not returned to the cache until the .NET runtime frees up the object during the garbage collection process.</span></span> <span data-ttu-id="045cd-106">Par conséquent, vous devez appeler **Policy.Dispose** lorsque vous avez terminé avec le **stratégie** objet.</span><span class="sxs-lookup"><span data-stu-id="045cd-106">Therefore, you should call **Policy.Dispose** when you are finished with the **Policy** object.</span></span>  
  
 <span data-ttu-id="045cd-107">L’exemple de code pour l’utilisation de la **Policy.Dispose** méthode est la suivante :</span><span class="sxs-lookup"><span data-stu-id="045cd-107">The sample code for using the **Policy.Dispose** method is as follows:</span></span>  
  
```  
xmlDocument = IncomingXMLMessage.XMLCase;  
typedXmlDocument = new Microsoft.RuleEngine.TypedXmlDocument("Microsoft.Samples.BizTalk.LoansProcessor.Case",xmlDocument);  
policy = new Microsoft.RuleEngine.Policy("LoanProcessing");  
policy.Execute(typedXmlDocument);  
OutgoingXMLMessage.XMLCase = xmlDocument;  
policy.Dispose();  
```