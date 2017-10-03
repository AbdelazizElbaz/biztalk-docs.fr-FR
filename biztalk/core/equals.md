---
title: "Est égal à | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ac93031a-9d18-443d-9e38-71ef9edd5a30
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2b82ac5c779dc6b4d3624b48cebe9df1bc3d1966
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="equals"></a>Égal à
Supprime les deux premiers éléments de la pile, les compare, puis transmet les résultats sur la pile.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
<ic:Operation Name="Equals" />  
```  
  
#### <a name="parameters"></a>Paramètres  
 Deux premiers éléments de la pile.  
  
## <a name="pushed-value"></a>Valeur transmise  
 Chaîne de résultat de l'opération de comparaison.  
  
## <a name="remarks"></a>Notes  
  
## <a name="example"></a>Exemple  
 L’exemple d’expression de filtre suivant utilise le **est égal à** opération à comparer le nom de l’activité actuelle à la constante « CheckPO ». Si les deux valeurs sont égales, l'expression prend la valeur `true`.  
  
```  
<ic:Filter>  
  <ic:Expression>  
    <wf:Operation Name="GetActivityName"/>  
    <ic:Operation Name="Constant">  
      <ic:Argument>CheckPO</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals"/>  
  </ic:Expression>  
</ic:Filter>  
```  
  
 Vous pouvez être tenté de définir votre expression comme vous écririez une déclaration en langage C# en vue d'effectuer une comparaison. Par exemple, vous pouvez comparer trois valeurs en écrivant le code C# suivant :  
  
```  
bool res = a == b == c;  
```  
  
 Un tel modèle pour votre expression de filtre reste toutefois insuffisant. Envisagez plutôt d'utiliser la déclaration modifiée (mais équivalente) suivante :  
  
```  
Bool res = (a == b) && (a == c);  
```  
  
 Cette déclaration correspond davantage à l'expression de filtre que vous utiliseriez pour effectuer la comparaison. Pour plus d’informations et obtenir un exemple, consultez [et](../core/and.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Opérations de l’intercepteur](../core/interceptor-operations.md)