---
title: "Concaténer | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e21a773d-a9cc-4a6f-b548-46badcd92aab
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4766f65fb0cbe26c8f3c545c38235d83abb283a4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="concatenate"></a>Concaténation
Supprime les deux premiers éléments de la pile, les concatène, puis transmet les résultats sur la pile.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
<ic:Operation Name="Concatenate" />  
```  
  
#### <a name="parameters"></a>Paramètres  
 Deux premiers éléments de la pile.  
  
## <a name="pushed-value"></a>Valeur transmise  
 Chaîne de résultat de l'opération de concaténation.  
  
## <a name="remarks"></a>Notes  
  
## <a name="example"></a>Exemple  
 Dans l’exemple suivant mettre à jour d’expression, la chaîne constante « démarrer : » est concaténée avec la valeur de la propriété de contexte « EventTime » et conservé dans la colonne de base de données NewOrderCreateTime.  
  
```  
<ic:Update DataItemName="NewOrderCreateTime" Type="NVARCHAR">  
  <ic:Expression>  
    <ic:Operation Name="Constant">  
      <ic:Argument>Start:</ic:Argument>  
    </ic:Operation>  
    <wf:Operation Name="GetContextProperty">  
      <wf:Argument>EventTime</wf:Argument>  
    </wf:Operation>  
    <ic:Operation Name="Concatenate" />  
  </ic:Expression>  
</ic:Update>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Opérations de l’intercepteur](../core/interceptor-operations.md)