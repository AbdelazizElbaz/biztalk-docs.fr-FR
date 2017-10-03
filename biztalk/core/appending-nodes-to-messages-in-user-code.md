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
# <a name="appending-nodes-to-messages-in-user-code"></a>Ajout de nœuds pour les Messages dans le Code utilisateur
Étant donné la façon dont BizTalk gère les messages, vous ne pouvez pas ajouter directement un nouveau nœud à un message existant. Vous devez cloner le message existant comme suit :  
  
```  
myXMLDoc = myExistingMsg; // just holding a reference  
// use CloneNode to make a fresh copy of myModifiedMsg  
myXMLDoc = (XMLDocument)myXMLDoc.CloneNode;  
myXMLDoc.append myNode; // here is the node we want to append  
//update temp message   
myModifiedMsg = myXMLDoc;  
```  
  
 Vous pouvez maintenant utiliser myModifiedMsg, qui contient le nouveau nœud. Si vous souhaitez réutiliser myExistingMsg, vous pouvez créer une copie (vide) et lui affecter myModifiedMsg.  
  
```  
myExistingMsg = myModifiedMsg;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Construction de Messages dans le Code utilisateur](../core/constructing-messages-in-user-code.md)   
 [Construction de Messages](../core/constructing-messages.md)