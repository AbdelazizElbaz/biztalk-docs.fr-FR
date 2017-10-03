---
title: GetOperationName | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f858269c-d412-43e3-85e1-398afa9375ab
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 04e22020add39840b0d2fe4c2fd88156321a18c7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="getoperationname"></a>GetOperationName
Transmet le nom de l'opération actuelle sur la pile.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
<wcf:Operation Name="GetOperationName" />  
```  
  
#### <a name="parameters"></a>Paramètres  
 Aucun.  
  
## <a name="pushed-value"></a>Valeur transmise  
 Chaîne contenant le nom de l'opération actuelle.  
  
## <a name="remarks"></a>Notes  
 Lors de l'utilisation de GetOperationName, veillez à comparer le nom de l'opération tel qu'il est appelé par votre application. Par exemple, si vous utilisez l'attribut de nom d'un contrat de service pour affecter un nom personnalisé, le serveur proxy par défaut du client se verra attribuer le nom personnalisé de la méthode. Toutefois, l'application serveur utilisera les noms de méthodes réels des opérations correspondantes, et non ceux spécifiés dans l'attribut de nom.  
  
## <a name="example"></a> Exemple  
 Dans l'exemple suivant, `GetOperationName` permet de créer une expression qui effectue un filtre sur l'opération nommée « AuthorizePayment ».  
  
```  
<ic:Filter>  
  <ic:Expression>  
    <wcf:Operation Name="GetOperationName" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>AuthorizePayment</ic:Argument>  
    </ic:Operation>  
  </ic:Expression>  
</ic:Filter>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Opérations dans Windows Communication Foundation](../core/operations-in-windows-communication-foundation.md)