---
title: GetContextProperty2 | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2554a210-cfb4-4b63-9afa-ffe2a853ba7b
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f834bf1271f6706c332123d8b1835e0bd730f069
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="getcontextproperty"></a>GetContextProperty
Transmet la propriété de contexte demandée sur la pile.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
<wf:Operation Name="GetContextProperty">  
  <wf:Argument>ContextPropertyName</wf:Argument>  
</wf:Operation>  
```  
  
#### <a name="parameters"></a>Paramètres  
 L'un des noms de propriété de contexte suivants :  
  
|Nom de la propriété de contexte|Description|  
|---------------------------|-----------------|  
|EventTime|Date et heure actuelles.|  
|InstanceId|ID de l'instance de flux de travail|  
  
> [!NOTE]
>  Les noms des propriétés de contexte respectent la casse.  
  
## <a name="pushed-value"></a>Valeur transmise  
 Chaîne contenant la propriété de contexte demandée.  
  
## <a name="remarks"></a>Notes  
 L'heure est stockée au format UTC dans la base de données.  
  
## <a name="example"></a>Exemple  
 Dans l’exemple suivant, une expression pour l’extraction du **InstanceId** utilisé dans un bloc correlationID pour définir l’ID de corrélation.  
  
```  
<ic:CorrelationID>  
  <ic:Expression>  
    <wf:Operation Name="GetContextProperty">  
      <wf:Argument>InstanceId</wf:Argument>  
    </wf:Operation>  
  </ic:Expression>  
</ic:CorrelationID>  
```  
  
 Il s'agit d'un modèle d'utilisation courante de `GetContextProperty`.