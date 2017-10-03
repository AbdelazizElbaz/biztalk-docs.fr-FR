---
title: "ID de corrélation | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b4faf210-7e7f-450d-8bb1-84d3d31c3022
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1192de4a49c300220ce0b297bbc1ee02ce64c6dc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="correlationid"></a>CorrelationID
L'élément `CorrelationID` permet de spécifier un ID de corrélation pour un message.  
  
## <a name="format"></a>Format  
 L'élément `CorrelationID` se compose d'un élément `Expression` qui fait appel à un ou plusieurs éléments `Operation` pour spécifier la chaîne à utiliser en tant qu'ID de corrélation.  
  
```  
<ic:CorrelationID>  
  <ic:Expression>  
    <!-- Operations -->  
  </ic:Expression>  
</ic:CorrelationID>  
```  
  
## <a name="remarks"></a>Notes  
 Les opérations communes suivantes ne sont pas autorisées dans les expressions d'ID de corrélation :  
  
-   And  
  
-   Égal à  
  
## <a name="example"></a>Exemple  
 Le bloc de configuration de l'exemple d'intercepteur WF (Workflow Foundation) suivant utilise « OrderNum » pour définir un ID de corrélation. À l'aide de WF et d'opérations communes, vous pouvez créer des expressions d'une grande complexité afin de construire un ID de corrélation approprié à votre workflow.  
  
```  
<ic:CorrelationID>  
  <ic:Expression>  
    <wf:Operation Name="GetWorkflowProperty">  
      <wf:Argument>OrderNum</wf:Argument>  
    </wf:Operation>  
  </ic:Expression>  
</ic:CorrelationID>  
```  
  
 Pour les applications WCF (Windows Communication Foundation), vous pouvez utiliser des opérations communes et d'autres spécifiques à WCF afin de construire un ID de corrélation. L’exemple suivant utilise le **XPath** opération et XPath pour récupérer un numéro de carte de crédit à partir d’un message pour une utilisation en tant qu’un ID de corrélation :  
  
```  
<ic:CorrelationID>  
  <ic:Expression>  
    <wcf:Operation Name ="XPath">  
      <wcf:Argument>//s:Body/creditCard:CreditCardNumber</wcf:Argument>  
    </wcf:Operation>  
  </ic:Expression>  
</ic:CorrelationID>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Élément OnEvent de l’intercepteur](../core/interceptor-onevent-element.md)