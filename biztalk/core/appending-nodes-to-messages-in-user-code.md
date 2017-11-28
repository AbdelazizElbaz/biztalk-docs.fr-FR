---
title: "Ajout de nœuds pour les Messages dans le Code utilisateur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- messages, nodes
- messages, cloning
ms.assetid: 636e0064-095e-49d1-850f-eaee0f0ffe77
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b0376094f31478c74a408eacab6c363ce22c9d2a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="appending-nodes-to-messages-in-user-code"></a><span data-ttu-id="7f8d5-102">Ajout de nœuds pour les Messages dans le Code utilisateur</span><span class="sxs-lookup"><span data-stu-id="7f8d5-102">Appending Nodes to Messages in User Code</span></span>
<span data-ttu-id="7f8d5-103">Étant donné la façon dont BizTalk gère les messages, vous ne pouvez pas ajouter directement un nouveau nœud à un message existant.</span><span class="sxs-lookup"><span data-stu-id="7f8d5-103">Because of the way BizTalk Server handles messages, you cannot simply append a new node directly to an existing message.</span></span> <span data-ttu-id="7f8d5-104">Vous devez cloner le message existant comme suit :</span><span class="sxs-lookup"><span data-stu-id="7f8d5-104">Instead, you must clone the existing message, as follows:</span></span>  
  
```  
myXMLDoc = myExistingMsg; // just holding a reference  
// use CloneNode to make a fresh copy of myModifiedMsg  
myXMLDoc = (XMLDocument)myXMLDoc.CloneNode;  
myXMLDoc.append myNode; // here is the node we want to append  
//update temp message   
myModifiedMsg = myXMLDoc;  
```  
  
 <span data-ttu-id="7f8d5-105">Vous pouvez maintenant utiliser myModifiedMsg, qui contient le nouveau nœud.</span><span class="sxs-lookup"><span data-stu-id="7f8d5-105">Now you can use myModifiedMsg, which includes the new node.</span></span> <span data-ttu-id="7f8d5-106">Si vous souhaitez réutiliser myExistingMsg, vous pouvez créer une copie (vide) et lui affecter myModifiedMsg.</span><span class="sxs-lookup"><span data-stu-id="7f8d5-106">If for some reason you want to reuse myExistingMsg, you can construct a new (empty) copy and assign myModifiedMsg to it.</span></span>  
  
```  
myExistingMsg = myModifiedMsg;  
```  
  
## <a name="see-also"></a><span data-ttu-id="7f8d5-107">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7f8d5-107">See Also</span></span>  
 <span data-ttu-id="7f8d5-108">[Construction de Messages dans le Code utilisateur](../core/constructing-messages-in-user-code.md) </span><span class="sxs-lookup"><span data-stu-id="7f8d5-108">[Constructing Messages in User Code](../core/constructing-messages-in-user-code.md) </span></span>  
 [<span data-ttu-id="7f8d5-109">Construction de Messages</span><span class="sxs-lookup"><span data-stu-id="7f8d5-109">Constructing Messages</span></span>](../core/constructing-messages.md)