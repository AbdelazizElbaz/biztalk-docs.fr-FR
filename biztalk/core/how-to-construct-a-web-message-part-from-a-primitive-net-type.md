---
title: "Comment construire une partie de Message Web à partir d’un Type .NET primitif | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- creating, Web messages
- Web messages, Message Assignment shape [Orchestration Designer]
- Web messages, creating
- Message Assignment shape [Orchestration Designer], Web messages
- Web messages, parts
- Web messages, .NET types
ms.assetid: 1fe52412-d2bc-484c-8925-c7ff3ca7704b
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 991970d5b0d40da1ec00b54919d2742cfd48353c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-construct-a-web-message-part-from-a-primitive-net-type"></a>Développement d'une partie de message web à partir d'un type .NET primitif
Vous créez une partie de message Web à partir d’un type .NET primitif à l’aide un **assignation du Message** forme. ou à l'aide d'une classe d'assistance .NET pour définir les parties. Pour plus d’informations sur la création de types de messages à l’aide d’une classe .NET, consultez [construction de Messages dans le Code utilisateur](../core/constructing-messages-in-user-code.md).  
  
### <a name="to-construct-a-web-message-part-from-a-primitive-net-type"></a>Pour créer une partie de message Web à partir d'un type .NET primitif  
  
1.  Ouvrez une orchestration, ouvrez le **boîte à outils** et cliquez sur le **Orchestrations BizTalk** onglet.  
  
2.  Faites glisser un **construire un Message** forme à l’orchestration.  
  
3.  Modifier la **Message construit** propriété à inclure l’instance de message que vous avez créé pour le type de message Web.  
  
4.  Faites glisser un **assignation du Message** forme sur le **construire un Message** forme.  
  
5.  Double-cliquez sur le **assignation du Message** forme pour ouvrir l’éditeur d’Expression BizTalk.  
  
6.  Définissez les parties du type de message Web sur les valeurs requises dans la zone Éditeur d'expression BizTalk.  
  
     Par exemple, le code suivant définit l'expression sur une chaîne :  
  
    ```  
    ItemAvailRequestInstance.Item_ID = "This is Item_ID.";  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [Construction de Messages Web](../core/constructing-web-messages.md)