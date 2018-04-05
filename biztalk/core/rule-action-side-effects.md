---
title: Effets d’Action de règle | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Business Rules Engine, side effects
ms.assetid: 1ef65014-9c0a-40d3-b941-2a67c20b54d3
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d2ed890ca8efca6fdd1403c4ec89f4c0c5d32eaa
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="rule-action-side-effects"></a><span data-ttu-id="c2f97-102">Effets secondaires d'une action de règle</span><span class="sxs-lookup"><span data-stu-id="c2f97-102">Rule Action Side Effects</span></span>
<span data-ttu-id="c2f97-103">Si l'exécution d'une action affecte l'état d'un objet ou un terme d'une condition, cette action est considérée comme ayant un effet secondaire sur l'objet.</span><span class="sxs-lookup"><span data-stu-id="c2f97-103">If the execution of an action affects the state of an object or a term used in conditions, that action is considered to have a side effect on the object.</span></span>  
  
 <span data-ttu-id="c2f97-104">Supposons que les règles suivantes existent :</span><span class="sxs-lookup"><span data-stu-id="c2f97-104">Assume we have the following rules.</span></span>  
  
## <a name="rule-1"></a><span data-ttu-id="c2f97-105">Règle 1</span><span class="sxs-lookup"><span data-stu-id="c2f97-105">Rule 1</span></span>  
  
```  
IF OrderForm.ItemCount > 100   
THEN OrderForm.Status = "important"  
```  
  
## <a name="rule-2"></a><span data-ttu-id="c2f97-106">Règle 2</span><span class="sxs-lookup"><span data-stu-id="c2f97-106">Rule 2</span></span>  
  
```  
IF OrderList.IsFromMember = true   
THEN OrderForm.UpdateStatus("important")  
```  
  
 <span data-ttu-id="c2f97-107">Dans ce cas, **OrderForm.UpdateStatus** a un effet secondaire **OrderForm.Status**.</span><span class="sxs-lookup"><span data-stu-id="c2f97-107">In this case, **OrderForm.UpdateStatus** is said to have a side effect on **OrderForm.Status**.</span></span> <span data-ttu-id="c2f97-108">Cela ne signifie pas que **OrderForm.UpdateStatus** a des effets secondaires ; au lieu de cela, **OrderForm.Status** est potentiellement affecté par une ou plusieurs actions.</span><span class="sxs-lookup"><span data-stu-id="c2f97-108">This does not mean that **OrderForm.UpdateStatus** has side effects; instead, **OrderForm.Status** is potentially affected by one or more actions.</span></span>  
  
 <span data-ttu-id="c2f97-109">Par défaut, le **SideEffects** propriété pour les membres de classe .NET est **true**, ce qui empêche le moteur de règles de mise en cache le membre avec effets secondaires.</span><span class="sxs-lookup"><span data-stu-id="c2f97-109">By default, the **SideEffects** property for .NET class members is **true**, which prevents the rule engine from caching the member with side effects.</span></span> <span data-ttu-id="c2f97-110">Dans notre exemple, le moteur de règles ne met pas en cache **OrderForm.Status** dans la mémoire de travail ; à la place il obtient la valeur la plus récente de **OrderForm.Status** chaque fois que 1 de la règle est évaluée.</span><span class="sxs-lookup"><span data-stu-id="c2f97-110">In our example, the rule engine does not cache **OrderForm.Status** in the working memory; instead it gets the most up-to-date value of **OrderForm.Status** every time Rule 1 is evaluated.</span></span> <span data-ttu-id="c2f97-111">Si le **SideEffects** est définie sur **false**, le moteur de règles met en cache la valeur de la première fois qu’il évalue **OrderForm.Status**, mais pour les évaluations ultérieures (dans scénarios chaînage avant), il utilise la valeur mise en cache.</span><span class="sxs-lookup"><span data-stu-id="c2f97-111">If the **SideEffects** property is set to **false**, the rule engine caches the value first time it evaluates **OrderForm.Status**, but for later evaluations (in forward-chaining scenarios), it uses the cached value.</span></span>  
  
 <span data-ttu-id="c2f97-112">Actuellement l’éditeur des règles d’entreprise ne fournit pas un moyen pour les utilisateurs à modifier **SideEffects**, toutefois, vous pouvez uniquement définir la **SideEffects** propriété par programme par le biais de l’infrastructure des règles d’entreprise .</span><span class="sxs-lookup"><span data-stu-id="c2f97-112">Currently the Business Rule Composer does not provide a way for users to modify **SideEffects**, however, you can only set the **SideEffects** property programmatically through the Business Rules Framework.</span></span> <span data-ttu-id="c2f97-113">Vous ceci à la liaison, à l’aide de la [ClassMemberBinding](https://msdn.microsoft.com/library/microsoft.ruleengine.classmemberbinding.aspx) classe pour spécifier les méthodes d’objet, les propriétés et les champs utilisés dans les conditions de règle et les actions.</span><span class="sxs-lookup"><span data-stu-id="c2f97-113">You set do this at binding, using the [ClassMemberBinding](https://msdn.microsoft.com/library/microsoft.ruleengine.classmemberbinding.aspx) class to specify object methods, properties, and fields used in rule conditions and actions.</span></span> <span data-ttu-id="c2f97-114">**ClassMemberBinding** a une propriété, [SideEffects](https://msdn.microsoft.com/library/microsoft.ruleengine.classmemberbinding.sideeffects.aspx#P:Microsoft.RuleEngine.ClassMemberBinding.SideEffects), qui contient une valeur booléenne indiquant si l’accès au membre change sa valeur.</span><span class="sxs-lookup"><span data-stu-id="c2f97-114">**ClassMemberBinding** has a property, [SideEffects](https://msdn.microsoft.com/library/microsoft.ruleengine.classmemberbinding.sideeffects.aspx#P:Microsoft.RuleEngine.ClassMemberBinding.SideEffects), which contains a Boolean value indicating whether accessing the member changes its value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2f97-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c2f97-115">See Also</span></span>  
 [<span data-ttu-id="c2f97-116">Moteur de règles</span><span class="sxs-lookup"><span data-stu-id="c2f97-116">Rule Engine</span></span>](../core/rule-engine.md)