---
title: "Mise à jour 1 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Update function [Business Rules Engine]
- Update function [Business Rules Engine], TypedXMLDocument
- Update function [Business Rules Engine], TypedData table
- Update function [Business Rules Engine], .NET objects
- .NET objects
- Update function [Business Rules Engine], DataConnection
ms.assetid: 939e45dc-6433-42f3-a336-8f3c247417ac
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3a4ea10e72be2a39eedaafa0e00c8f8ac630393b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="update"></a><span data-ttu-id="529bf-102">Update</span><span class="sxs-lookup"><span data-stu-id="529bf-102">Update</span></span>
<span data-ttu-id="529bf-103">Lorsque **mise à jour** fonction est appelée un objet, l’objet est redéclaré dans le moteur pour être réévalué, basées sur les nouvelles données et l’état.</span><span class="sxs-lookup"><span data-stu-id="529bf-103">When **Update** function is invoked an object, the object is reasserted into the engine to be re-evaluated, based on the new data and state.</span></span> <span data-ttu-id="529bf-104">L’objet peut être de type **TypedXmlDocument** ou classe .NET ou **DataConnection** ou **TypedDataTable**.</span><span class="sxs-lookup"><span data-stu-id="529bf-104">The object can be of type **TypedXmlDocument** or .NET class or **DataConnection** or **TypedDataTable**.</span></span>  
  
 <span data-ttu-id="529bf-105">Vous pouvez également utiliser **mise à jour** fonction pour améliorer les performances du moteur et empêcher les scénarios de boucle sans fin comme décrit dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="529bf-105">You can also use **Update** function to improve engine performance and prevent endless loop scenarios as described in this topic.</span></span>  
  
 <span data-ttu-id="529bf-106">En général, vous utilisez **Assert** pour placer un nouvel objet dans la mémoire de travail du moteur de règles et utiliser **mettre à jour** pour mettre à jour un objet déjà existant dans la mémoire de travail.</span><span class="sxs-lookup"><span data-stu-id="529bf-106">Typically, you use **Assert** to place a new object in the working memory of the rule engine, and use **Update** to update an already existing object in the working memory.</span></span> <span data-ttu-id="529bf-107">Lorsque vous déclarez un nouvel objet, les conditions dans tous les règles sont évaluées.</span><span class="sxs-lookup"><span data-stu-id="529bf-107">When you assert a new object, conditions in all the rules are evaluated.</span></span> <span data-ttu-id="529bf-108">Lorsque vous mettez à jour un objet existant, seules les conditions utilisant le fait mis à jour sont réévaluées, et les actions sont ajoutées à l'agenda si ces conditions ont la valeur True.</span><span class="sxs-lookup"><span data-stu-id="529bf-108">When you update an existing object, only conditions that use the updated fact are reevaluated, and actions are added to the agenda if these conditions are evaluated to true.</span></span>  
  
## <a name="using-update-function-on-net-facts"></a><span data-ttu-id="529bf-109">Utilisation de la fonction Mettre à jour sur les faits .NET</span><span class="sxs-lookup"><span data-stu-id="529bf-109">Using Update function on .NET facts</span></span>  
 <span data-ttu-id="529bf-110">Prenons l'exemple des deux règles suivantes.</span><span class="sxs-lookup"><span data-stu-id="529bf-110">Take the two rules that follow as an example.</span></span> <span data-ttu-id="529bf-111">Supposons que les objets **ItemA** et **ItemB** existent déjà dans la mémoire de travail.</span><span class="sxs-lookup"><span data-stu-id="529bf-111">Suppose that objects **ItemA** and **ItemB** already exist in working memory.</span></span> <span data-ttu-id="529bf-112">Règle 1 évalue la **Id** propriété sur **ItemA**, définit le **Id** propriété sur **ItemB**, puis redéclare **ItemB** après la modification.</span><span class="sxs-lookup"><span data-stu-id="529bf-112">Rule 1 evaluates the **Id** property on **ItemA**, sets the **Id** property on **ItemB**, and then reasserts **ItemB** after the change.</span></span> <span data-ttu-id="529bf-113">Lorsque **ItemB** est redéclaré, il est traité comme un nouvel objet et le moteur réévalue toutes les règles qui utilisent l’objet **ItemB** dans les prédicats ou actions.</span><span class="sxs-lookup"><span data-stu-id="529bf-113">When **ItemB** is reasserted, it is treated as a new object and the engine re-evaluates all rules that use object **ItemB** in the predicates or actions.</span></span> <span data-ttu-id="529bf-114">Cela garantit que la règle 2 est réévaluée en fonction de la nouvelle valeur de **ItemB.Id**, comme dans la règle 1.</span><span class="sxs-lookup"><span data-stu-id="529bf-114">This ensures that Rule 2 is re-evaluated against the new value of **ItemB.Id**, as set in Rule 1.</span></span> <span data-ttu-id="529bf-115">Règle 2 peut avoir échoué la première fois qu’elle a été évaluée, mais prend la valeur de **true** la deuxième fois, elle est évaluée.</span><span class="sxs-lookup"><span data-stu-id="529bf-115">Rule 2 may have failed the first time it was evaluated, but evaluates to **true** the second time it is evaluated.</span></span>  
  
### <a name="rule-1"></a><span data-ttu-id="529bf-116">Règle 1</span><span class="sxs-lookup"><span data-stu-id="529bf-116">Rule 1</span></span>  
  
```  
IF ItemA.Id == 1  
THEN ItemB.Id = 2  
Assert(ItemB)  
```  
  
### <a name="rule-2"></a><span data-ttu-id="529bf-117">Règle 2</span><span class="sxs-lookup"><span data-stu-id="529bf-117">Rule 2</span></span>  
  
```  
IF ItemB.Id == 2  
THEN ItemB.Value = 100  
```  
  
 <span data-ttu-id="529bf-118">Cette possibilité de redéclarer les objets dans la mémoire de travail donne à l'utilisateur un contrôle explicite sur le fonctionnement des scénarios de chaînage avant.</span><span class="sxs-lookup"><span data-stu-id="529bf-118">This ability to reassert objects into working memory allows the user explicit control over the behavior in forward-chaining scenarios.</span></span> <span data-ttu-id="529bf-119">Dans cet exemple, l'effet secondaire de la nouvelle déclaration est la réévaluation de la règle 1.</span><span class="sxs-lookup"><span data-stu-id="529bf-119">A side effect of the reassertion in this example, however, is that Rule 1 is also re-evaluated.</span></span> <span data-ttu-id="529bf-120">Étant donné que **ItemA.Id** n’a pas changé, règle 1 évalue à nouveau à **true** et **Assert (ITEMB)** action est déclenchée à nouveau.</span><span class="sxs-lookup"><span data-stu-id="529bf-120">Because **ItemA.Id** was not changed, Rule 1 again evaluates to **true** and the **Assert(ItemB)** action fires again.</span></span> <span data-ttu-id="529bf-121">Par conséquent, la règle crée une situation de boucle sans fin.</span><span class="sxs-lookup"><span data-stu-id="529bf-121">As a result, the rule creates an endless loop situation.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="529bf-122">Le nombre de boucles maximale par défaut de la réévaluation de règles est 2 ^ 32.</span><span class="sxs-lookup"><span data-stu-id="529bf-122">The default maximum loop count of re-evaluation of rules is 2^32.</span></span> <span data-ttu-id="529bf-123">Pour certaines règles, l’exécution de la stratégie peut durer longtemps.</span><span class="sxs-lookup"><span data-stu-id="529bf-123">For certain rules, the policy execution could last for a long time.</span></span> <span data-ttu-id="529bf-124">Vous pouvez réduire le nombre en ajustant la **profondeur maximale de la boucle d’exécution** propriété de la version de stratégie.</span><span class="sxs-lookup"><span data-stu-id="529bf-124">You can reduce the count by adjusting the **Maximum Execution Loop Depth** property of the policy version.</span></span>  
  
 <span data-ttu-id="529bf-125">Vous devez pouvoir redéclarer des objets sans créer des boucles sans fin et le **mise à jour** fonction fournit cette fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="529bf-125">You need to be able to reassert objects without creating endless loops, and the **Update** function provides this capability.</span></span> <span data-ttu-id="529bf-126">Comme une fonction de redéclaration, le **mise à jour** fonction effectue **retrait** et **Assert** des instances d’objet associé, qui ont été modifiées à partir d’actions de règle, mais il y a deux principales différences :</span><span class="sxs-lookup"><span data-stu-id="529bf-126">Like a reassert, the **Update** function performs **Retract** and **Assert** of the associated object instances, which have been changed from rule actions, but there are two key differences:</span></span>  
  
-   <span data-ttu-id="529bf-127">Les actions sur l'agenda pour les règles dans lesquelles le type d'instance n'est utilisé que dans les actions (pas les prédicats) resteront dans l'agenda.</span><span class="sxs-lookup"><span data-stu-id="529bf-127">Actions on the agenda for rules where the instance type is only used in the actions (not the predicates) will remain on the agenda.</span></span>  
  
-   <span data-ttu-id="529bf-128">Les règles qui n'utilisent que le type d'instance dans les actions ne seront pas réévaluées.</span><span class="sxs-lookup"><span data-stu-id="529bf-128">Rules that only use the instance type in the actions will not be re-evaluated.</span></span>  
  
 <span data-ttu-id="529bf-129">Par conséquent, les règles qui utilisent les types d'instances dans les prédicats seulement ou dans les prédicats et les actions seront réévaluées et leurs actions seront ajoutées à l'agenda en conséquence.</span><span class="sxs-lookup"><span data-stu-id="529bf-129">Therefore, rules that use the instance types in either the predicates only or both the predicates and actions will be re-evaluated and their actions added to the agenda as appropriate.</span></span>  
  
 <span data-ttu-id="529bf-130">Modification de l’exemple précédent pour utiliser le **mise à jour** fonction garantit que seule la règle 2 est réévaluée car **ItemB** est utilisée dans la condition de règle 2.</span><span class="sxs-lookup"><span data-stu-id="529bf-130">Changing the preceding example to use the **Update** function ensures that only Rule 2 is re-evaluated because **ItemB** is used in the condition of Rule 2.</span></span> <span data-ttu-id="529bf-131">Règle 1 n’est pas réévaluée car **ItemB** est utilisée uniquement dans les actions de la règle 1, en éliminant le scénario de bouclage.</span><span class="sxs-lookup"><span data-stu-id="529bf-131">Rule 1 is not reevaluated because **ItemB** is only used in the actions of Rule 1, eliminating the looping scenario.</span></span>  
  
### <a name="rule-1"></a><span data-ttu-id="529bf-132">Règle 1</span><span class="sxs-lookup"><span data-stu-id="529bf-132">Rule 1</span></span>  
  
```  
IF ItemA.Id == 1  
THEN ItemB.Id = 2  
Update(ItemB)  
```  
  
### <a name="rule-2"></a><span data-ttu-id="529bf-133">Règle 2</span><span class="sxs-lookup"><span data-stu-id="529bf-133">Rule 2</span></span>  
  
```  
IF ItemB.Id == 2  
THEN ItemB.Value = 100  
```  
  
 <span data-ttu-id="529bf-134">Toutefois, il reste possible de créer des scénarios de bouclage.</span><span class="sxs-lookup"><span data-stu-id="529bf-134">However, it is still possible to create looping scenarios.</span></span> <span data-ttu-id="529bf-135">Observez par exemple la règle suivante :</span><span class="sxs-lookup"><span data-stu-id="529bf-135">For example, consider the following rule.</span></span>  
  
### <a name="rule-1"></a><span data-ttu-id="529bf-136">Règle 1</span><span class="sxs-lookup"><span data-stu-id="529bf-136">Rule 1</span></span>  
  
```  
IF ItemA.Id == 1  
THEN ItemA.Value = 20  
Update(ItemA)  
```  
  
 <span data-ttu-id="529bf-137">Étant donné que **ItemA** est utilisée dans le prédicat, il est réévalué quand **mise à jour** est appelée sur **ItemA**.</span><span class="sxs-lookup"><span data-stu-id="529bf-137">Because **ItemA** is used in the predicate, it is re-evaluated when **Update** is called on **ItemA**.</span></span> <span data-ttu-id="529bf-138">Si la valeur de **ItemA.Id** n’est pas modifiée nulle part, règle 1 continue à évaluer à **true**, ce qui provoque **mise à jour** à appeler une fois encore sur A. Le Concepteur de la règle doit garantir que les scénarios de bouclage comme celui-ci ne sont pas créés.</span><span class="sxs-lookup"><span data-stu-id="529bf-138">If the value of **ItemA.Id** is not changed elsewhere, Rule 1 continues to evaluate to **true**, causing **Update** to once again be called on A. The rule designer must ensure that looping scenarios such as this are not created.</span></span>  
  
 <span data-ttu-id="529bf-139">L'approche à adopter dépendra de la nature des règles.</span><span class="sxs-lookup"><span data-stu-id="529bf-139">The appropriate approach for this will differ based on the nature of the rules.</span></span> <span data-ttu-id="529bf-140">Le mécanisme suivant permet de résoudre facilement le problème qui se pose dans l'exemple précédent.</span><span class="sxs-lookup"><span data-stu-id="529bf-140">The following is a simple mechanism to solve the problem in the preceding example.</span></span>  
  
 <span data-ttu-id="529bf-141">Le **mise à jour** fonction peut être utilisée dans l’éditeur des règles d’entreprise avec une référence à la classe, comme avec la **Assert**, **retrait**, ou **RetractByType** fonctions.</span><span class="sxs-lookup"><span data-stu-id="529bf-141">The **Update** function may be used in the Business Rule Composer with a reference to the class, as with the **Assert**, **Retract**, or **RetractByType** functions.</span></span>  
  
### <a name="rule-1"></a><span data-ttu-id="529bf-142">Règle 1</span><span class="sxs-lookup"><span data-stu-id="529bf-142">Rule 1</span></span>  
  
```  
IF ItemA.Id == 1 and ItemA.Value != 20  
THEN ItemA.Value = 20  
Update(ItemA)  
```  
  
 <span data-ttu-id="529bf-143">Ajouter le contrôle sur **ItemA.Value** empêche de l’évaluation de la règle 1 **true** à nouveau après l’exécution d’actions de règle 1, la première fois.</span><span class="sxs-lookup"><span data-stu-id="529bf-143">Adding the check on **ItemA.Value** prevents Rule 1 from evaluating to **true** again after the actions of Rule 1 are executed the first time.</span></span>  
  
## <a name="using-update-function-on-xml-facts"></a><span data-ttu-id="529bf-144">Utilisation de la fonction Mettre à jour sur les faits XML</span><span class="sxs-lookup"><span data-stu-id="529bf-144">Using Update function on XML facts</span></span>  
 <span data-ttu-id="529bf-145">Prenons l'exemple des deux règles suivantes.</span><span class="sxs-lookup"><span data-stu-id="529bf-145">Take the two rules that follow as an example.</span></span> <span data-ttu-id="529bf-146">Supposons que</span><span class="sxs-lookup"><span data-stu-id="529bf-146">Suppose that.</span></span> <span data-ttu-id="529bf-147">la règle 1 évalue le nombre total d'articles dans un message de bon de commande et la règle 2 définit l'état sur « Needs approval » si le nombre total est supérieur ou égal à 10.</span><span class="sxs-lookup"><span data-stu-id="529bf-147">Rule 1 evaluates the total count of the items in a purchase order message, and rule2 sets the status to "Needs approval" if the total count is greater than or equal to 10.</span></span>  
  
### <a name="rule-1"></a><span data-ttu-id="529bf-148">Règle 1</span><span class="sxs-lookup"><span data-stu-id="529bf-148">Rule 1</span></span>  
  
```  
IF 1 == 1  
THEN ProcessPO.Order:/Order/Items/TotalCount = (ProcessPO.Order:/Order/Items/TotalCount + ProcessPO:/Order/Items/Item/Count)  
```  
  
### <a name="rule-2"></a><span data-ttu-id="529bf-149">Règle 2</span><span class="sxs-lookup"><span data-stu-id="529bf-149">Rule 2</span></span>  
  
```  
IF ProcessPO.Order:/Order/Items/TotalCount >= 10  
THEN ProcessPO.Order:/Order/Status = "Needs approval"  
```  
  
 <span data-ttu-id="529bf-150">Si vous passez le message de bon de commande fournisseur suivant comme entrée pour cette stratégie, vous remarquez que l’état n’est pas définie sur « Needs approval » même si le nombre total d’éléments est 14.</span><span class="sxs-lookup"><span data-stu-id="529bf-150">If you pass the following purchase order (PO) message as an input to this policy, you notice that the status is not set to "Needs approval" even though the total item count is 14.</span></span> <span data-ttu-id="529bf-151">C’est parce que le règle2 est évaluée uniquement au début lorsque la valeur de la **TotalCount** est de 0, et la règle n’est pas évaluée chaque fois que le nombre total est mis à jour.</span><span class="sxs-lookup"><span data-stu-id="529bf-151">It is because that the rule2 is evaluated only at the beginning when the value of the **TotalCount** field is 0, and the rule is not evaluated each time the total available count is updated.</span></span> <span data-ttu-id="529bf-152">Pour que les conditions soient réévaluées à chaque le **TotalCount** est mis à jour, vous devez appeler la **mise à jour** fonctionnent sur le nœud parent (**éléments**) du nœud modifié ( **TotalCount**).</span><span class="sxs-lookup"><span data-stu-id="529bf-152">To have the conditions reevaluated each time the **TotalCount** is updated, you need to call the **Update** function on the parent node (**Items**) of the modified node (**TotalCount**).</span></span> <span data-ttu-id="529bf-153">Si vous modifiez la règle 1 comme illustré ci-dessous et testez cette règle une nouvelle fois, la valeur du champ État doit être définie sur « Needs Approval ».</span><span class="sxs-lookup"><span data-stu-id="529bf-153">If you change the Rule1 as shown below, and test it one more time, you should see the value of the Status field set to "Needs Approval".</span></span>  
  
```  
<ns0:Order xmlns:ns0="http://ProcessPO.Order">  
    <Items>  
        <Item>  
            <Id>ITM1</Id>  
            <Count>2</Count>  
        </Item>  
        <Item>  
            <Id>ITM2</Id>  
            <Count>5</Count>  
        </Item>  
        <Item>  
            <Id>ITM3</Id>  
            <Count>7</Count>  
        </Item>  
        <TotalCount>0</TotalCount>  
    </Items>  
    <Status>No approval needed</Status>  
</ns0:Order>  
```  
  
 <span data-ttu-id="529bf-154">Modifié **règle 1** est comme suit :</span><span class="sxs-lookup"><span data-stu-id="529bf-154">The modified **Rule 1** is as follows:</span></span>  
  
### <a name="rule-1"></a><span data-ttu-id="529bf-155">Règle 1</span><span class="sxs-lookup"><span data-stu-id="529bf-155">Rule 1</span></span>  
  
```  
IF 1 == 1  
THEN ProcessPO.Order:/Order/Items/TotalCount = (ProcessPO.Order:/Order/Items/TotalCount + ProcessPO:/Order/Items/Item/Count) AND  
Update(ProcessPO.Order:/Order/Items)  
```  
  
## <a name="using-update-function-on-database-facts"></a><span data-ttu-id="529bf-156">Utilisation de la fonction Mettre à jour sur les faits de base de données</span><span class="sxs-lookup"><span data-stu-id="529bf-156">Using Update function on database facts</span></span>  
  
### <a name="typeddatatable"></a><span data-ttu-id="529bf-157">TypedDataTable</span><span class="sxs-lookup"><span data-stu-id="529bf-157">TypedDataTable</span></span>  
 <span data-ttu-id="529bf-158">Si **mise à jour** est appelée sur une **TypedDataTable**, **mise à jour** est appelée par le moteur sur tous associés **TypedDataRows**.</span><span class="sxs-lookup"><span data-stu-id="529bf-158">If **Update** is called on a **TypedDataTable**, **Update** is called by the engine on all associated **TypedDataRows**.</span></span> <span data-ttu-id="529bf-159">**Mise à jour** peut également être appelée sur individuels **TypedDataRows**.</span><span class="sxs-lookup"><span data-stu-id="529bf-159">**Update** may also be called on individual **TypedDataRows**.</span></span>  
  
### <a name="dataconnection"></a><span data-ttu-id="529bf-160">DataConnection</span><span class="sxs-lookup"><span data-stu-id="529bf-160">DataConnection</span></span>  
 <span data-ttu-id="529bf-161">Mise à jour d’un **DataConnection** n’est pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="529bf-161">Update of a **DataConnection** is not supported.</span></span> <span data-ttu-id="529bf-162">Utilisez **Assert** à la place.</span><span class="sxs-lookup"><span data-stu-id="529bf-162">Use **Assert** instead.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="529bf-163">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="529bf-163">See Also</span></span>  
 [<span data-ttu-id="529bf-164">Fonctions de contrôle du moteur</span><span class="sxs-lookup"><span data-stu-id="529bf-164">Engine Control Functions</span></span>](../core/engine-control-functions.md)