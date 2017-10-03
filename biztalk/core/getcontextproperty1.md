---
title: GetContextProperty1 | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e8867c29-63de-4a13-9ef9-8c6ab8ea3443
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 65b7ffffe4b21e3317b920ac50cdc27b12d708d5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="getcontextproperty"></a>GetContextProperty
Transmet la propriété de contexte demandée sur la pile.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
<wcf:Operation Name ="GetContextProperty">  
  <wcf:Argument>EventTime</wcf:Argument>  
</wcf:Operation>  
```  
  
#### <a name="parameters"></a>Paramètres  
 L'un des noms de propriété de contexte suivants :  
  
|Nom de la propriété de contexte|Description|  
|---------------------------|-----------------|  
|EventTime|Date et heure actuelles.|  
|SessionId|ID de la session de workflow.|  
  
> [!NOTE]
>  Les noms des propriétés de contexte respectent la casse.  
  
## <a name="pushed-value"></a>Valeur transmise  
 Chaîne contenant la propriété de contexte demandée.  
  
## <a name="remarks"></a>Notes  
 L'heure est stockée au format UTC dans la base de données.  
  
## <a name="example"></a> Exemple  
 Dans l'exemple d'expression de mise à jour suivant, la date d'approbation est extraite en récupérant l'heure de l'événement actuel.  
  
```  
<ic:Update DataItemName ="Approval Date" Type ="DATETIME">  
  <ic:Expression>  
    <wcf:Operation Name ="GetContextProperty">  
      <wcf:Argument>EventTime</wcf:Argument>  
    </wcf:Operation>  
  </ic:Expression>  
</ic:Update>  
```  
  
 Il s'agit d'un modèle d'utilisation courante de `GetContextProperty`.  
  
## <a name="see-also"></a>Voir aussi  
 [Opérations dans Windows Communication Foundation](../core/operations-in-windows-communication-foundation.md)