---
title: GetUserKey | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9353a7f0-9bbd-4cfa-92e6-ed2b86e3a88e
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0701ff1df912cc113205bad573b6cebc0f02a13a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="getuserkey"></a>GetUserKey
Transmet la clé utilisateur actuelle sur la pile.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
<wf:Operation Name="GetUserKey" />  
```  
  
#### <a name="parameters"></a>Paramètres  
 Aucun.  
  
## <a name="pushed-value"></a>Valeur transmise  
 Chaîne contenant la clé utilisateur actuelle.  
  
## <a name="remarks"></a>Notes  
 Cette opération est valide uniquement dans les points de suivi d'utilisateur.  
  
## <a name="example"></a> Exemple  
 L'exemple suivant contient une expression de filtre d'événement qui donne le résultat `true` lorsque la clé utilisateur est égale à « DocumentUrl ».  
  
```  
<ic:Filter>  
  <ic:Expression>  
    <wf:Operation Name="GetUserKey" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>DocumentUrl</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
  </ic:Expression>  
</ic:Filter>  
```