---
title: GetActivityType | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 65a5aae3-9688-4c49-a78e-1d9c1cc85fea
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 67e6f31331907e20e810c11e82002fb08b89abe4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="getactivitytype"></a>GetActivityType
Transmet le nom du type d'activité en cours sur la pile.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
<wf:Operation Name="GetActivityType" />  
```  
  
#### <a name="parameters"></a>Paramètres  
 Aucun.  
  
## <a name="pushed-value"></a>Valeur transmise  
 Chaîne contenant le type d'activité en cours dans le format de nom de classe qualifié d'assembly.  
  
## <a name="remarks"></a>Notes  
 L'opération `GetActivityType` récupère le type d'activité en cours et le place sur la pile au format de nom de classe qualifié d'assembly :  
  
```  
TopNamespace.SubNameSpace.ContainingClass+NestedClass, MyAssembly, Version=1.3.0.0, Culture=neutral, PublicKeyToken=b17a5c561934e08, processorArchitecture=MSIL  
```  
  
 Lors de la comparaison, vous pouvez spécifier le type autant que nécessaire pour satisfaire vos besoins de recherche spécifiques. Par exemple, vous pouvez comparer le résultat de GetActivityType avec la constante :  
  
 TopNamespace.SubNameSpace.ContainingClass+NestedClass, MyAssembly, Version=1.3.0.0  
  
 Ceci est moins restrictif que le format de nom de classe qualifié d'assembly.  
  
## <a name="special-filter-behavior"></a>Comportement de filtre spécial  
 Lorsque cette opération est effectuée dans un filtre, les activités dérivées sont également mises en correspondance.  
  
## <a name="example"></a> Exemple  
 L'exemple suivant contient une expression de filtre d'événement qui donne le résultat `true` pour les instances `System.Workflow.ComponentModel.Activity` et les instances des classes dérivées de `System.Workflow.ComponentModel.Activity`.  
  
```  
<ic:Expression>  
  <wf:Operation Name="GetActivityType" />  
  <ic:Operation Name="Constant">  
    <ic:Argument>System.Workflow.ComponentModel.Activity, System.Workflow.ComponentModel, Version=3.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL</ic:Argument>  
  </ic:Operation>  
  <ic:Operation Name="Equals" />  
</ic:Expression>  
```