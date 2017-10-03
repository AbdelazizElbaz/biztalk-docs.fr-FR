---
title: Et | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 80bd8f1f-edae-476d-b488-78e6c5ee70bf
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 676940dfa5cbc23d0c8127923d292e382a4e3cad
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="and"></a>And
Supprime les deux premiers éléments de la pile, réalise une opération booléenne **et** de deux éléments et exécute un push du résultat dans la pile.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
<ic:Operation Name="And" />  
```  
  
#### <a name="parameters"></a>Paramètres  
 Deux premiers éléments de la pile.  
  
## <a name="pushed-value"></a>Valeur transmise  
 Chaîne de résultat de la valeur booléenne **AND** opération.  
  
## <a name="remarks"></a>Notes  
  
## <a name="example"></a>Exemple  
 Le **et** opération est utile lorsque vous avez besoin évaluer plusieurs instructions. L’exemple d’expression de filtre suivante vérifie si le nom de l’activité est « CheckPO » et que l’événement d’activité est fermé à l’aide de la **et** opération.  
  
```  
<ic:Filter>  
  <ic:Expression>  
    <wf:Operation Name="GetActivityName"/>  
    <ic:Operation Name="Constant">  
      <ic:Argument>CheckPO</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals"/>  
    <wf:Operation Name="GetActivityEvent"/>  
    <ic:Operation Name="Constant">  
      <ic:Argument>Closed</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals"/>  
    <ic:Operation Name="And"/>  
  </ic:Expression>  
</ic:Filter>  
```  
  
 Dans cet exemple **et** est la dernière opération dans l’expression, car elle s’appuie sur les résultats des comparaisons (et les affiche à partir de la pile pour effectuer la comparaison). Vous pouvez étendre cette idée à la réalisation **et** opérations sur plus de deux éléments. Par exemple, pour évaluer si une condition A, une condition B et une condition  C se réalisent, vous utilisez une expression similaire à la suivante :  
  
```  
<ic:Filter>  
  <ic:Expression>  
    <wf:Operation Name="GetActivityName"/>  
    <ic:Operation Name="Constant">  
      <ic:Argument>CheckPO</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals"/>  
    <wf:Operation Name="GetActivityEvent"/>  
    <ic:Operation Name="Constant">  
      <ic:Argument>Closed</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals"/>  
    <wf:Operation Name="GetActivityType"/>  
    <ic:Operation Name="Constant">  
      <ic:Argument>MyType</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals"/>  
    <ic:Operation Name="And"/>  
    <ic:Operation Name="And"/>  
  </ic:Expression>  
</ic:Filter>   
```  
  
## <a name="see-also"></a>Voir aussi  
 [Opérations de l’intercepteur](../core/interceptor-operations.md)