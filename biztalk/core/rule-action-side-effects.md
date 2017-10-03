---
title: "Effets d’Action de règle | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Business Rules Engine, side effects
ms.assetid: 1ef65014-9c0a-40d3-b941-2a67c20b54d3
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d2ed890ca8efca6fdd1403c4ec89f4c0c5d32eaa
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="rule-action-side-effects"></a>Effets secondaires d'une action de règle
Si l'exécution d'une action affecte l'état d'un objet ou un terme d'une condition, cette action est considérée comme ayant un effet secondaire sur l'objet.  
  
 Supposons que les règles suivantes existent :  
  
## <a name="rule-1"></a>Règle 1  
  
```  
IF OrderForm.ItemCount > 100   
THEN OrderForm.Status = "important"  
```  
  
## <a name="rule-2"></a>Règle 2  
  
```  
IF OrderList.IsFromMember = true   
THEN OrderForm.UpdateStatus("important")  
```  
  
 Dans ce cas, **OrderForm.UpdateStatus** a un effet secondaire **OrderForm.Status**. Cela ne signifie pas que **OrderForm.UpdateStatus** a des effets secondaires ; au lieu de cela, **OrderForm.Status** est potentiellement affecté par une ou plusieurs actions.  
  
 Par défaut, le **SideEffects** propriété pour les membres de classe .NET est **true**, ce qui empêche le moteur de règles de mise en cache le membre avec effets secondaires. Dans notre exemple, le moteur de règles ne met pas en cache **OrderForm.Status** dans la mémoire de travail ; à la place il obtient la valeur la plus récente de **OrderForm.Status** chaque fois que 1 de la règle est évaluée. Si le **SideEffects** est définie sur **false**, le moteur de règles met en cache la valeur de la première fois qu’il évalue **OrderForm.Status**, mais pour les évaluations ultérieures (dans scénarios chaînage avant), il utilise la valeur mise en cache.  
  
 Actuellement l’éditeur des règles d’entreprise ne fournit pas un moyen pour les utilisateurs à modifier **SideEffects**, toutefois, vous pouvez uniquement définir la **SideEffects** propriété par programme par le biais de l’infrastructure des règles d’entreprise . Vous ceci à la liaison, à l’aide de la [ClassMemberBinding](https://msdn.microsoft.com/library/microsoft.ruleengine.classmemberbinding.aspx) classe pour spécifier les méthodes d’objet, les propriétés et les champs utilisés dans les conditions de règle et les actions. **ClassMemberBinding** a une propriété, [SideEffects](https://msdn.microsoft.com/library/microsoft.ruleengine.classmemberbinding.sideeffects.aspx#P:Microsoft.RuleEngine.ClassMemberBinding.SideEffects), qui contient une valeur booléenne indiquant si l’accès au membre change sa valeur.  
  
## <a name="see-also"></a>Voir aussi  
 [Moteur de règles](../core/rule-engine.md)