---
title: Constante | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0af49bf5-e7de-41da-ac27-70301b8ee4d4
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 674307acea439bc260399cc01da4165eedaa2da5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="constant"></a>Constante
Transmet une seule valeur constante sur la pile.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
<ic:Operation Name="Constant">  
  <ic:Argument>val</ic:Argument>  
</ic:Operation>  
```  
  
#### <a name="parameters"></a>Paramètres  
 Valeur constante.  
  
## <a name="pushed-value"></a>Valeur transmise  
 Chaîne contenant la valeur constante.  
  
## <a name="remarks"></a>Notes  
  
## <a name="example"></a>Exemple  
 L’exemple d’expression de filtre suivant utilise le **constante** opération pour transmettre une valeur qui sera ensuite utilisée dans une **est égal à** opération pour vous assurer que le nom de l’activité actuelle est « FoodAndDrinksPolicy ».  
  
```  
<ic:Filter>  
  <ic:Expression>  
    <wf:Operation Name="GetActivityName"/>  
    <ic:Operation Name="Constant">  
      <ic:Argument>FoodAndDrinksPolicy</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals"/>  
  </ic:Expression>  
</ic:Filter>  
```  
  
 Il s’agit d’un modèle d’utilisation commun pour le **constante** opération.  
  
## <a name="see-also"></a>Voir aussi  
 [Opérations de l’intercepteur](../core/interceptor-operations.md)