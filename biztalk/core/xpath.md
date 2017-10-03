---
title: XPath | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 444b5eb9-0c00-4225-918e-b973532c67d0
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2ee46838596a55512df5d1476f2c3ba34b1f5cb9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="xpath"></a>XPath
Transmet la valeur indiquée par une instruction XPath.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
<wcf:Operation Name="XPath">  
  <wcf:Argument>//po:POID</wcf:Argument>  
</wcf:Operation>  
```  
  
#### <a name="parameters"></a>Paramètres  
 Instruction XPath valide.  
  
## <a name="pushed-value"></a>Valeur transmise  
 Valeur de chaîne du résultat obtenu en exécutant l'instruction XPath.  
  
## <a name="remarks"></a>Notes  
 Vous devez utiliser une instruction XPath valide.  
  
 Si plusieurs correspondances sont trouvées, seule la première est utilisée.  
  
## <a name="example"></a> Exemple  
 L'exemple d'expression suivant construit une valeur de corrélation par la concaténation d'une constante « C_ » avec l'ID de bon de commande du message actuel. L'ID de bon de commande est récupéré via l'opération XPath.  
  
```  
<ic:CorrelationID>  
  <ic:Expression>  
    <ic:Operation Name="Constant">  
      <ic:Argument>C_</ic:Argument>  
    </ic:Operation>  
    <wcf:Operation Name="XPath">  
      <wcf:Argument>//po:POID</wcf:Argument>  
    </wcf:Operation>  
    <ic:Operation Name="Concatenate" />  
  </ic:Expression>  
</ic:CorrelationID>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Opérations dans Windows Communication Foundation](../core/operations-in-windows-communication-foundation.md)