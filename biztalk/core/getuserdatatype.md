---
title: GetUserDataType | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b0605919-a733-4a9d-a725-109346db11a2
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5525dba034571acd91d1f3dd99f2b56069f81fc2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="getuserdatatype"></a>GetUserDataType
Transmet le nom du type de données utilisateur actuel sur la pile.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
<wf:Operation Name="GetUserDataType" />  
```  
  
#### <a name="parameters"></a>Paramètres  
 Aucun.  
  
## <a name="pushed-value"></a>Valeur transmise  
 Chaîne contenant le type de données utilisateur actuel au format qualifié pour les assemblys.  
  
## <a name="remarks"></a>Notes  
 Contrairement aux **GetActivityType**, cette opération n’utilise pas le format du nom de classe qualifié d’assembly ; au lieu de cela, il transmet uniquement le nom du type :  
  
```  
MyLibrary.MyObject  
```  
  
> [!NOTE]
>  Si vous utilisez le format de nom de classe qualifié pour les assemblys comme une constante lors de la comparaison de valeurs, le résultat donnera toujours `false`.  
  
## <a name="special-filter-behavior"></a>Comportement de filtre spécial  
 Lorsque cette opération est effectuée dans un filtre, les types de données utilisateur dérivés sont également mis en correspondance.  
  
## <a name="example"></a>Exemple  
 L'exemple suivant contient une expression de filtre d'événements qui donne le résultat `true` pour les instances `MyLibrary.MyObject` et pour toutes les instances de classes qui dérivent de `MyLibrary.MyObject`.  
  
```  
<ic:Filter>  
  <ic:Expression>  
    <wf:Operation Name="GetUserDataType" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>MyLibrary.MyObject</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
  </ic:Expression>  
</ic:Filter>  
```