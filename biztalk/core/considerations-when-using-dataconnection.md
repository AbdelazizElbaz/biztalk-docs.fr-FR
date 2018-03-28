---
title: Considérations sur l’utilisation de DataConnection | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Retract function [Business Rules Engine], DataConnection
- RetractByType function [Business Rules Engine], DataConnection
- Business Rules Engine, DataConnection tips
- Assert function [Business Rules Engine], DataConnection
- Update function [Business Rules Engine], DataConnection
ms.assetid: 1b4c8aa5-053f-43d7-9f5f-050383405fed
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1f99110daafa74cb16b6cc5b98e1382049bbb158
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/28/2018
---
# <a name="considerations-when-using-dataconnection"></a><span data-ttu-id="7cfe9-102">Considérations sur l'utilisation de DataConnection</span><span class="sxs-lookup"><span data-stu-id="7cfe9-102">Considerations When Using DataConnection</span></span>
<span data-ttu-id="7cfe9-103">Prenez en compte les éléments suivants lorsque vous utilisez DataConnection avec le moteur des règles d'entreprise.</span><span class="sxs-lookup"><span data-stu-id="7cfe9-103">Consider the following when using DataConnection with the Business Rule Engine.</span></span>  
  
## <a name="use-primary-keys"></a><span data-ttu-id="7cfe9-104">Utilisez des clés primaires</span><span class="sxs-lookup"><span data-stu-id="7cfe9-104">Use primary keys</span></span>  
 <span data-ttu-id="7cfe9-105">Lorsqu'une clé primaire existe, l'égalité des deux lignes est déterminée par le fait que ces lignes contiennent la même clé primaire et non par la comparaison de l'objet.</span><span class="sxs-lookup"><span data-stu-id="7cfe9-105">When there is a primary key, the equality of two rows is determined by whether the rows have the same primary key, rather than by object comparison.</span></span> <span data-ttu-id="7cfe9-106">Si les lignes sont considérées comme identiques, une seule copie est conservée en mémoire et l'autre est libérée.</span><span class="sxs-lookup"><span data-stu-id="7cfe9-106">If the rows are determined to be the same, only one copy is retained in memory, and the other is released.</span></span> <span data-ttu-id="7cfe9-107">Ceci réduit la consommation de mémoire.</span><span class="sxs-lookup"><span data-stu-id="7cfe9-107">This results in less memory consumption.</span></span>  
  
 <span data-ttu-id="7cfe9-108">Lorsqu’un **DataConnection** est déclaré dans le moteur de règles pour la première fois, le moteur essaie toujours de localiser les informations de clé primaire à partir de son schéma.</span><span class="sxs-lookup"><span data-stu-id="7cfe9-108">When a **DataConnection** is asserted into the rule engine for the first time, the engine always tries to locate its primary key information from its schema.</span></span> <span data-ttu-id="7cfe9-109">Si une clé primaire existe, les informations la concernant sont extraites et utilisées dans toutes les évaluations ultérieures.</span><span class="sxs-lookup"><span data-stu-id="7cfe9-109">If a primary key exists, primary key information is then retrieved and used in all subsequent evaluations.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7cfe9-110">Une clé primaire est obligatoire si des changements sont requis dans la base de données.</span><span class="sxs-lookup"><span data-stu-id="7cfe9-110">A primary key is mandatory if changes need to be made to the database.</span></span>  
  
## <a name="provide-a-running-transaction-to-the-dataconnection-whenever-possible"></a><span data-ttu-id="7cfe9-111">Fournissez une transaction d'exécution à DataConnection chaque fois que possible</span><span class="sxs-lookup"><span data-stu-id="7cfe9-111">Provide a running transaction to the DataConnection whenever possible</span></span>  
 <span data-ttu-id="7cfe9-112">Sans une transaction, chaque requête et mettre à jour sur le **DataConnection** lance sa propre transaction locale et différentes requêtes peuvent retourner différents résultats dans les différentes parties des évaluations de règles.</span><span class="sxs-lookup"><span data-stu-id="7cfe9-112">Without a transaction, each query and update on the **DataConnection** initiates its own local transaction, and different queries might return different results in different parts of rule evaluations.</span></span> <span data-ttu-id="7cfe9-113">Les utilisateurs risquent d'obtenir un comportement imprévisible si des changements sont apportés dans la table de base de données sous-jacente.</span><span class="sxs-lookup"><span data-stu-id="7cfe9-113">Users may experience inconsistent behavior if there are changes in the underlying database table.</span></span>  
  
 <span data-ttu-id="7cfe9-114">Bien que vous puissiez utiliser un **DataConnection** sans fournir une transaction lorsque la table ne change pas au fil du temps, il est recommandé d’utiliser qu’une transaction, même lorsque le **DataConnection** est en cours uniquement utilisé pour les opérations de lecture.</span><span class="sxs-lookup"><span data-stu-id="7cfe9-114">Although you can use a **DataConnection** without providing a transaction when the table does not change over time, it is recommended that a transaction be used even when the **DataConnection** is only being used for read operations.</span></span>  
  
 <span data-ttu-id="7cfe9-115">Vous devez, toutefois, utiliser systématiquement une transaction lorsque vous mettez à jour des données.</span><span class="sxs-lookup"><span data-stu-id="7cfe9-115">However, a transaction should always be used when updating data.</span></span>  
  
## <a name="number-of-queries-may-grow-linearly"></a><span data-ttu-id="7cfe9-116">Le nombre de requêtes peut augmenter de manière linéaire</span><span class="sxs-lookup"><span data-stu-id="7cfe9-116">Number of queries may grow linearly</span></span>  
 <span data-ttu-id="7cfe9-117">Comme les requêtes sur le **DataConnection** sont paramétrées par d’autres objets joints, le nombre de requêtes exécutées sur le **DataConnection** correspond directement au nombre d’objets de jointure Atteindre le **DataConnection**.</span><span class="sxs-lookup"><span data-stu-id="7cfe9-117">As queries against the **DataConnection** are parameterized by other joined objects, the number of queries executed against the **DataConnection** corresponds directly to the number of joining objects reaching the **DataConnection**.</span></span> <span data-ttu-id="7cfe9-118">Par conséquent, si le nombre de jointure objets atteindre le **DataConnection** objet augmente de manière linéaire, le nombre de requêtes sur le **DataConnection** croît proportionnellement au nombre ainsi.</span><span class="sxs-lookup"><span data-stu-id="7cfe9-118">Therefore, if the number of joining objects reaching the **DataConnection** object grows linearly, the number of queries against the **DataConnection** will grow linearly as well.</span></span> <span data-ttu-id="7cfe9-119">aucune optimisation n'est mise en place pour réduire ce nombre de requêtes.</span><span class="sxs-lookup"><span data-stu-id="7cfe9-119">Currently, there is no optimization in place to reduce the number of queries.</span></span>  
  
 <span data-ttu-id="7cfe9-120">Prenons cette règle comme exemple :</span><span class="sxs-lookup"><span data-stu-id="7cfe9-120">An example of this is the rule:</span></span>  
  
```  
IF A.x = 7 AND DC.y = A.y  
THEN  
```  
  
 <span data-ttu-id="7cfe9-121">Un représente un **ObjectBinding**, contrôleur de domaine représente un **DataConnection**, x et y représentent les attributs de A et le contrôleur de domaine.</span><span class="sxs-lookup"><span data-stu-id="7cfe9-121">A represents an **ObjectBinding**, DC represents a **DataConnection**, and x and y represent attributes of A and DC.</span></span>  
  
 <span data-ttu-id="7cfe9-122">Pour chaque instance de A qui réussit le test (x = 7), une requête est générée à l’aide de la **DataConnection**.</span><span class="sxs-lookup"><span data-stu-id="7cfe9-122">For every instance of A that passes the test (x = 7), a query is generated by using the **DataConnection**.</span></span> <span data-ttu-id="7cfe9-123">S'il existe de nombreuses correspondances, vous obtenez le même nombre de requêtes.</span><span class="sxs-lookup"><span data-stu-id="7cfe9-123">If there are many matching instances, the same number of queries results.</span></span>  
  
## <a name="use-or-conditions-with-caution"></a><span data-ttu-id="7cfe9-124">Utilisez les conditions OR avec précaution</span><span class="sxs-lookup"><span data-stu-id="7cfe9-124">Use OR conditions with caution</span></span>  
 <span data-ttu-id="7cfe9-125">Si la règle utilise uniquement conjonctives (**AND**) conditions, les tests et les requêtes seront exécutés dès que possible, afin d’instances d’objets seront réduits.</span><span class="sxs-lookup"><span data-stu-id="7cfe9-125">If the rule uses only conjunctive (**AND**) conditions, tests and queries will be executed as early as possible, so instances of objects passing through will be reduced.</span></span> <span data-ttu-id="7cfe9-126">Par conséquent, le nombre de requêtes sur les **DataConnection** est réduit proportionnellement.</span><span class="sxs-lookup"><span data-stu-id="7cfe9-126">As a result, the number of queries against the subsequent **DataConnection** will be reduced proportionally.</span></span> <span data-ttu-id="7cfe9-127">Si disjonctive (**ou**) conditions et un **DataConnection** sont utilisées ensemble dans une règle, la condition de toutes les évaluations seront poussées vers la dernière requête.</span><span class="sxs-lookup"><span data-stu-id="7cfe9-127">If disjunctive (**OR**) conditions and a **DataConnection** are used together in a rule, all condition evaluations will be pushed to the final query.</span></span> <span data-ttu-id="7cfe9-128">Si plusieurs **DataConnection** est utilisé dans une règle, toutes les requêtes, sauf la dernière deviennent effectivement une instruction de requête Select-ALL.</span><span class="sxs-lookup"><span data-stu-id="7cfe9-128">If more than one **DataConnection** is used in a rule, all queries except the last one will effectively become a Select-ALL query statement.</span></span>  
  
 <span data-ttu-id="7cfe9-129">En général, il vaut mieux fractionner en deux ou en plusieurs règles discrètes une règle avec une condition OR parce que, par comparaison avec la définition de règles plus atomiques, les conditions OR réduisent les performances.</span><span class="sxs-lookup"><span data-stu-id="7cfe9-129">In general, it is better to split any rule with an OR condition into two or more discrete rules, because the use of OR conditions will decrease performance compared to the definition of more atomic rules.</span></span> <span data-ttu-id="7cfe9-130">Ceci est vrai que vous utilisiez ou non des DataConnections.</span><span class="sxs-lookup"><span data-stu-id="7cfe9-130">This is true whether DataConnections are used or not.</span></span>  
  
 <span data-ttu-id="7cfe9-131">Vous pouvez envisager d’utiliser des règles distinctes composées uniquement de conditions conjonctives à la place d’une règle avec **ou** conditions.</span><span class="sxs-lookup"><span data-stu-id="7cfe9-131">You may also consider using separate rules that consist only of conjunctive conditions instead of one rule with **OR** conditions.</span></span> <span data-ttu-id="7cfe9-132">Avec **ou** conditions, le nombre de requêtes augmente la vitesse de multiplication des instances de tous les objets de jointure.</span><span class="sxs-lookup"><span data-stu-id="7cfe9-132">With **OR** conditions, the number of queries grows at the speed of multiplication of instances of all joining objects.</span></span> <span data-ttu-id="7cfe9-133">Cela est illustré par l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="7cfe9-133">This is shown in the following example.</span></span>  
  
```  
IF (A.x ==7 OR A.x == 8) AND DC.y == A.y  
THEN DC.z = 10  
```  
  
 <span data-ttu-id="7cfe9-134">Dans cet exemple, A représente un **ObjectBinding**; Contrôleur de domaine représente un **DataConnection**et x, y et z des attributs de A et le contrôleur de domaine.</span><span class="sxs-lookup"><span data-stu-id="7cfe9-134">In this example, A represents an **ObjectBinding**; DC represents a **DataConnection**, and x, y, and z represent attributes of A and DC.</span></span> <span data-ttu-id="7cfe9-135">Si A contient 100 instances et x est 1 dans le premier objet, 2 dans le deuxième objet, et 100 dans l’objet de 100, 100 requêtes doivent exécuter sur le **DataConnection**.</span><span class="sxs-lookup"><span data-stu-id="7cfe9-135">If A has 100 instances, and x is 1 in the first object, 2 in the second object, through 100 in the 100th object, 100 queries have to run against the **DataConnection**.</span></span>  
  
 <span data-ttu-id="7cfe9-136">Il vaut mieux réécrire la règle précédente en la fractionnant en deux règles.</span><span class="sxs-lookup"><span data-stu-id="7cfe9-136">It is better to rewrite the preceding rule by splitting it in to two rules.</span></span>  
  
 <span data-ttu-id="7cfe9-137">**Règle 1**</span><span class="sxs-lookup"><span data-stu-id="7cfe9-137">**Rule 1**</span></span>  
  
```  
IF A.x =7 AND DC.y = A.y  
THEN DC.z = 10  
```  
  
 <span data-ttu-id="7cfe9-138">**Règle 2**</span><span class="sxs-lookup"><span data-stu-id="7cfe9-138">**Rule 2**</span></span>  
  
```  
IF A.x = 8 AND DC.y = A.y  
THEN DC.z = 10  
```  
  
## <a name="sql-does-not-support-some-predicates-and-functions"></a><span data-ttu-id="7cfe9-139">SQL ne prend pas en charge certains prédicats et fonctions.</span><span class="sxs-lookup"><span data-stu-id="7cfe9-139">SQL does not support some predicates and functions</span></span>  
 <span data-ttu-id="7cfe9-140">Certains prédicats et fonctions pris en charge par le moteur de règles ne le sont pas par SQL.</span><span class="sxs-lookup"><span data-stu-id="7cfe9-140">Some predicates and functions that the rule engine supports are not supported by SQL.</span></span> <span data-ttu-id="7cfe9-141">Si vous utilisez ces prédicats et fonctions non pris en charge dans les conditions de règle, ils ne peuvent pas être intégrés à la requête.</span><span class="sxs-lookup"><span data-stu-id="7cfe9-141">If these unsupported predicates and functions are used in the rule conditions, it cannot be incorporated into the query.</span></span> <span data-ttu-id="7cfe9-142">Les conditions suivantes ne peuvent pas être optimisées en tant que requêtes SQL.</span><span class="sxs-lookup"><span data-stu-id="7cfe9-142">The following terms cannot be optimized as an SQL query:</span></span>  
  
-   <span data-ttu-id="7cfe9-143">Certaines des fonctions intégrées du moteur n'ont pas d'équivalent dans une requête SQL.</span><span class="sxs-lookup"><span data-stu-id="7cfe9-143">Some of the engine built-in functions have no equivalent in an SQL query.</span></span> <span data-ttu-id="7cfe9-144">Il s’agit **Power**, **FindFirst**, et **FindAll**.</span><span class="sxs-lookup"><span data-stu-id="7cfe9-144">These are **Power**, **FindFirst**, and **FindAll**.</span></span> <span data-ttu-id="7cfe9-145">À l’aide un **DataConnection** colonne en tant qu’un ou plusieurs de leurs arguments ne peut pas être optimisée dans le cadre d’une requête ; par exemple, Power (2, contrôleur de domaine. (Column1).</span><span class="sxs-lookup"><span data-stu-id="7cfe9-145">Using a **DataConnection** column as one or more of their arguments cannot be optimized as part of a query; for example, Power( 2, dc.Column1).</span></span>  
  
-   <span data-ttu-id="7cfe9-146">Prédicat intégré Match utilisant une **DataConnection** colonne comme argument d’expression régulière (le premier argument).</span><span class="sxs-lookup"><span data-stu-id="7cfe9-146">Built-in predicate Match that uses a **DataConnection** column as its regular expression argument (the first argument).</span></span> <span data-ttu-id="7cfe9-147">Par exemple, Match("abc\*", dc1.Column2) est valide, mais Match(dc1.Column1, dc1.Column2) ne peut pas être traduit.</span><span class="sxs-lookup"><span data-stu-id="7cfe9-147">For example, Match("abc\*", dc1.Column2) is valid, but Match(dc1.Column1, dc1.Column2) cannot be translated.</span></span>  
  
-   <span data-ttu-id="7cfe9-148">À l’aide d’une fonction de l’utilisateur qui a un **DataConnection** colonne en tant qu’un de ses paramètres.</span><span class="sxs-lookup"><span data-stu-id="7cfe9-148">Using a user function that has a **DataConnection** column as one of its parameters.</span></span> <span data-ttu-id="7cfe9-149">Par exemple, c1.M(dc.Column1) ne peut pas être optimisé parce que la fonction utilisateur ne peut pas être exécutée par le serveur de base de données, mais par le moteur des règles d'entreprise.</span><span class="sxs-lookup"><span data-stu-id="7cfe9-149">For example, c1.M(dc.Column1) cannot be optimized because the user function cannot execute on the database server, but must be executed by the Business Rule Engine.</span></span>  
  
-   <span data-ttu-id="7cfe9-150">Les fonctions utilisateur qui représentent les opérations définies sur le **DataConnection**; par exemple, contrôleur de domaine. Column1(5).</span><span class="sxs-lookup"><span data-stu-id="7cfe9-150">User functions that represent set operations on the **DataConnection**; for example, dc.Column1(5).</span></span>  
  
-   <span data-ttu-id="7cfe9-151">Fonctions qui utilisent un **ObjectReference** à la **DataConnection**; par exemple, objecref (DC).</span><span class="sxs-lookup"><span data-stu-id="7cfe9-151">Functions that use an **ObjectReference** to the **DataConnection**; for example, ObjecRef(dc).</span></span>  
  
-   <span data-ttu-id="7cfe9-152">Si un ou plusieurs arguments d'une fonction ne peuvent pas être traduits, l'appel de fonction devient aussi intraduisible ; par exemple, Add(c1.M(dc.Column1), 5).</span><span class="sxs-lookup"><span data-stu-id="7cfe9-152">If one or more of a function's arguments is untranslatable, the function call becomes untranslatable; for example, Add(c1.M(dc.Column1), 5).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7cfe9-153">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7cfe9-153">See Also</span></span>  
 [<span data-ttu-id="7cfe9-154">Accès aux données dans le moteur des règles d’entreprise</span><span class="sxs-lookup"><span data-stu-id="7cfe9-154">Data Access in the Business Rule Engine</span></span>](../core/data-access-in-the-business-rule-engine.md)