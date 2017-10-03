---
title: "Expressions de Configuration de l’intercepteur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2695f509-fece-40b8-aa00-fa3c0c0f19c5
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a28af058ac4750426f66dc6e290bc6a02bf2efd6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="interceptor-configuration-expressions"></a><span data-ttu-id="394e8-102">Expressions de configuration d'intercepteur</span><span class="sxs-lookup"><span data-stu-id="394e8-102">Interceptor Configuration Expressions</span></span>
<span data-ttu-id="394e8-103">Le fichier de configuration de l'intercepteur BAM utilise des expressions de filtre pour identifier une activité et des expressions de données pour créer un élément de données pour le stockage, l'utilisation comme ID de corrélation ou jeton de continuation, ou autre.</span><span class="sxs-lookup"><span data-stu-id="394e8-103">The BAM interceptor configuraton file uses filter expressions to identify an activity and uses data expressions to construct a data element for storage, use as a correlation ID or continuation token, or similar purpose.</span></span> <span data-ttu-id="394e8-104">Quelle que soit la finalité, les expressions individuelles sont identifiées dans le fichier de configuration de l'intercepteur par l'élément `expression` et contiennent une ou plusieurs opérations à l'aide de la notation polonaise inverse, également connue sous le nom de notation post-fixée.</span><span class="sxs-lookup"><span data-stu-id="394e8-104">Regardless of the purpose, individual expressions are identified in the interceptor configuration file by the `expression` element and contain one or more operations using Reverse Polish Notation, also known as postfix notation.</span></span>  
  
## <a name="about-reverse-polish-notation"></a><span data-ttu-id="394e8-105">À propos de la notation polonaise inverse</span><span class="sxs-lookup"><span data-stu-id="394e8-105">About Reverse Polish Notation</span></span>  
 <span data-ttu-id="394e8-106">Dans le cadre de la notation polonaise inverse (NPI), les opérandes précèdent l'opérateur, supprimant ainsi le besoin d'utiliser des parenthèses comme opérateurs de priorité.</span><span class="sxs-lookup"><span data-stu-id="394e8-106">In Reverse Polish Notation (RPN), operands precede the operator, thereby removing the need to use parentheses as precedence operators.</span></span> <span data-ttu-id="394e8-107">Une pile sert à maintenir des valeurs et toutes les opérations et pousser des valeurs sur la pile, retirer (supprimer) des valeurs de la pile ou réaliser une combinaison de poussées et de retraits pour effectuer une opération.</span><span class="sxs-lookup"><span data-stu-id="394e8-107">A stack is used to hold values and all operations either push values onto the stack, pop (remove) values from the stack, or perform a combination of pushes and pops to complete an operation.</span></span>  
  
 <span data-ttu-id="394e8-108">Par exemple, si vous souhaitez évaluer l'expression</span><span class="sxs-lookup"><span data-stu-id="394e8-108">For example, if you wanted to evaluate the expression</span></span>  
  
 `5 + (10 - 2)`  
  
 <span data-ttu-id="394e8-109">Conversion en son équivalent NPI résultats dans</span><span class="sxs-lookup"><span data-stu-id="394e8-109">Converting this to the equivalent RPN results in</span></span>  
  
 `5 10 2 - +`  
  
 <span data-ttu-id="394e8-110">Cela serait évalué comme suit :</span><span class="sxs-lookup"><span data-stu-id="394e8-110">This would be evaluated as follows:</span></span>  
  
|<span data-ttu-id="394e8-111">Entrée</span><span class="sxs-lookup"><span data-stu-id="394e8-111">Input</span></span>|<span data-ttu-id="394e8-112">Opération</span><span class="sxs-lookup"><span data-stu-id="394e8-112">Operation</span></span>|<span data-ttu-id="394e8-113">Pile</span><span class="sxs-lookup"><span data-stu-id="394e8-113">Stack</span></span>|  
|-----------|---------------|-----------|  
|<span data-ttu-id="394e8-114">5</span><span class="sxs-lookup"><span data-stu-id="394e8-114">5</span></span>|<span data-ttu-id="394e8-115">Envoi de données (push)</span><span class="sxs-lookup"><span data-stu-id="394e8-115">Push</span></span>|<span data-ttu-id="394e8-116">5</span><span class="sxs-lookup"><span data-stu-id="394e8-116">5</span></span>|  
|<span data-ttu-id="394e8-117">10</span><span class="sxs-lookup"><span data-stu-id="394e8-117">10</span></span>|<span data-ttu-id="394e8-118">Envoi de données (push)</span><span class="sxs-lookup"><span data-stu-id="394e8-118">Push</span></span>|<span data-ttu-id="394e8-119">5, 10</span><span class="sxs-lookup"><span data-stu-id="394e8-119">5, 10</span></span>|  
|<span data-ttu-id="394e8-120">2</span><span class="sxs-lookup"><span data-stu-id="394e8-120">2</span></span>|<span data-ttu-id="394e8-121">Envoi de données (push)</span><span class="sxs-lookup"><span data-stu-id="394e8-121">Push</span></span>|<span data-ttu-id="394e8-122">5, 10, 2</span><span class="sxs-lookup"><span data-stu-id="394e8-122">5, 10, 2</span></span>|  
|-|<span data-ttu-id="394e8-123">Soustraire</span><span class="sxs-lookup"><span data-stu-id="394e8-123">Subtract</span></span>|<span data-ttu-id="394e8-124">5, 8</span><span class="sxs-lookup"><span data-stu-id="394e8-124">5, 8</span></span>|  
|+|<span data-ttu-id="394e8-125">Ajouter</span><span class="sxs-lookup"><span data-stu-id="394e8-125">Add</span></span>|<span data-ttu-id="394e8-126">13</span><span class="sxs-lookup"><span data-stu-id="394e8-126">13</span></span>|  
  
 <span data-ttu-id="394e8-127">En supposant que le système NPI prenne en charge l'opération de concaténation de chaînes, vous pouvez également évaluer l'expression</span><span class="sxs-lookup"><span data-stu-id="394e8-127">Assuming the RPN system supported the string concatenate operation, you could also evaluate the expression</span></span>  
  
 `"The quick brown " + "fox " + "jumped over the lazy " + "dog."`  
  
 <span data-ttu-id="394e8-128">Sa conversion en son équivalent NPI donne :</span><span class="sxs-lookup"><span data-stu-id="394e8-128">Converting this to the equivalent RPN notation yields:</span></span>  
  
 `"The quick brown " "fox " "jumped over the lazy " "dog" + + +`  
  
 <span data-ttu-id="394e8-129">Cela serait évalué comme suit :</span><span class="sxs-lookup"><span data-stu-id="394e8-129">This would be evaluated as follows:</span></span>  
  
|<span data-ttu-id="394e8-130">Entrée</span><span class="sxs-lookup"><span data-stu-id="394e8-130">Input</span></span>|<span data-ttu-id="394e8-131">Opération</span><span class="sxs-lookup"><span data-stu-id="394e8-131">Operation</span></span>|<span data-ttu-id="394e8-132">Pile</span><span class="sxs-lookup"><span data-stu-id="394e8-132">Stack</span></span>|  
|-----------|---------------|-----------|  
|<span data-ttu-id="394e8-133">« Le jeune »</span><span class="sxs-lookup"><span data-stu-id="394e8-133">"The quick brown"</span></span>|<span data-ttu-id="394e8-134">Envoi de données (push)</span><span class="sxs-lookup"><span data-stu-id="394e8-134">Push</span></span>|<span data-ttu-id="394e8-135">« Le jeune »</span><span class="sxs-lookup"><span data-stu-id="394e8-135">"The quick brown "</span></span>|  
|<span data-ttu-id="394e8-136">« renard »</span><span class="sxs-lookup"><span data-stu-id="394e8-136">"fox"</span></span>|<span data-ttu-id="394e8-137">Envoi de données (push)</span><span class="sxs-lookup"><span data-stu-id="394e8-137">Push</span></span>|<span data-ttu-id="394e8-138">« Le jeune »,« renard »</span><span class="sxs-lookup"><span data-stu-id="394e8-138">"The quick brown ", "fox "</span></span>|  
|<span data-ttu-id="394e8-139">« a sauté par-dessus le vieux »</span><span class="sxs-lookup"><span data-stu-id="394e8-139">"jumped over the lazy"</span></span>|<span data-ttu-id="394e8-140">Envoi de données (push)</span><span class="sxs-lookup"><span data-stu-id="394e8-140">Push</span></span>|<span data-ttu-id="394e8-141">« Le jeune »,« renard », « a sauté par-dessus le vieux »</span><span class="sxs-lookup"><span data-stu-id="394e8-141">"The quick brown ", "fox ", "jumped over the lazy "</span></span>|  
|<span data-ttu-id="394e8-142">« chien. »</span><span class="sxs-lookup"><span data-stu-id="394e8-142">"dog."</span></span>|<span data-ttu-id="394e8-143">Envoi de données (push)</span><span class="sxs-lookup"><span data-stu-id="394e8-143">Push</span></span>|<span data-ttu-id="394e8-144">« Le jeune »,« renard », « a sauté par-dessus le vieux », « chien. »</span><span class="sxs-lookup"><span data-stu-id="394e8-144">"The quick brown ", "fox ", "jumped over the lazy ", "dog."</span></span>|  
|+|<span data-ttu-id="394e8-145">Concaténation</span><span class="sxs-lookup"><span data-stu-id="394e8-145">Concatenate</span></span>|<span data-ttu-id="394e8-146">« Le jeune »,« renard », « a sauté par-dessus le vieux chien. »</span><span class="sxs-lookup"><span data-stu-id="394e8-146">"The quick brown ", "fox ", "jumped over the lazy dog."</span></span>|  
|+|<span data-ttu-id="394e8-147">Concaténation</span><span class="sxs-lookup"><span data-stu-id="394e8-147">Concatenate</span></span>|<span data-ttu-id="394e8-148">« Le jeune »,« renard a sauté par-dessus le vieux chien. »</span><span class="sxs-lookup"><span data-stu-id="394e8-148">"The quick brown ", "fox jumped over the lazy dog."</span></span>|  
|+|<span data-ttu-id="394e8-149">Concaténation</span><span class="sxs-lookup"><span data-stu-id="394e8-149">Concatenate</span></span>|<span data-ttu-id="394e8-150">« Le jeune renard a sauté par-dessus le vieux chien. »</span><span class="sxs-lookup"><span data-stu-id="394e8-150">"The quick brown fox jumped over the lazy dog."</span></span>|  
  
 <span data-ttu-id="394e8-151">Comme vous pouvez le constater, un nombre arbitraire d'opérations peut être pris en charge, notamment la comparaison, les opérations booléennes et les opérations personnalisées qui extraient les valeurs appropriées pour les opérations auxquelles elles participent.</span><span class="sxs-lookup"><span data-stu-id="394e8-151">As you can see, an arbitrary number of operations can be supported, including comparison, Boolean operations, and custom operations that retrieve values appropriate for the operations in which they participate.</span></span> <span data-ttu-id="394e8-152">Les valeurs s'accumulent sur la pile et sont poussées et retirées en fonction des opérations individuelles.</span><span class="sxs-lookup"><span data-stu-id="394e8-152">Values accumulate on the stack and are pushed and popped according to individual operations.</span></span>  
  
## <a name="reverse-polish-notation-in-the-interceptor-configuration-file"></a><span data-ttu-id="394e8-153">Notation polonaise inverse dans le fichier de configuration de l'intercepteur</span><span class="sxs-lookup"><span data-stu-id="394e8-153">Reverse Polish Notation in the Interceptor Configuration File</span></span>  
 <span data-ttu-id="394e8-154">Vous allez écrire deux types d’expressions dans l’intercepteur de fichier de configuration : filtrer les expressions et les expressions de données.</span><span class="sxs-lookup"><span data-stu-id="394e8-154">You will write two kinds of expressions in the interceptor configuration file: filter expressions and data expressions.</span></span> <span data-ttu-id="394e8-155">Les expressions de filtre s'attendent à ce que le résultat d'une expression NPI soit un booléen `true` ou `false` tandis que les expressions de données attendent une valeur unique sur la pile.</span><span class="sxs-lookup"><span data-stu-id="394e8-155">Filter expressions expect the result of the RPN expression to be a Boolean `true` or `false` while data expressions expect a single value on the stack.</span></span>  
  
### <a name="filter-expressions"></a><span data-ttu-id="394e8-156">Expressions de filtre</span><span class="sxs-lookup"><span data-stu-id="394e8-156">Filter Expressions</span></span>  
 <span data-ttu-id="394e8-157">Les expressions de filtre donnent le booléen `true` ou `false` et sont utilisées pour identifier un événement spécifique à suivre dans l'application WF ou WFC.</span><span class="sxs-lookup"><span data-stu-id="394e8-157">Filter expressions evaluate to Boolean `true` or `false` and are used to identify a specific event to track in the WF or WFC application.</span></span> <span data-ttu-id="394e8-158">Dans les applications WF, il est courant de filtrer en fonction du nom de l'activité et de l'événement.</span><span class="sxs-lookup"><span data-stu-id="394e8-158">In WF applications, it is common to filter based on activity name and event.</span></span> <span data-ttu-id="394e8-159">Par exemple, vous souhaitez sélectionner la **FoodAndDrinksPolicy** activité lorsqu’elle est **fermé**.</span><span class="sxs-lookup"><span data-stu-id="394e8-159">For example, you may want to select the **FoodAndDrinksPolicy** activity when it is **Closed**.</span></span> <span data-ttu-id="394e8-160">À l'aide d'opérations WF, vous pouvez exprimer le filtre comme suit :</span><span class="sxs-lookup"><span data-stu-id="394e8-160">Using WF operations, you could express the filter as:</span></span>  
  
 `(GetActivityName = "FoodAndDrinksPolicy") && (GetActivityEvent = "Closed")`  
  
 <span data-ttu-id="394e8-161">Sa conversion en NPI donne :</span><span class="sxs-lookup"><span data-stu-id="394e8-161">Converting this to RPN yields:</span></span>  
  
 `GetActivityName "FoodAndDrinksPolicy" == GetActivityEvent "Closed" == &&`  
  
 <span data-ttu-id="394e8-162">La conversion de cette expression en son expression équivalente pour le fichier de configuration de l'intercepteur donne le code XML suivant :</span><span class="sxs-lookup"><span data-stu-id="394e8-162">Converting this expression to the equivalent expression for the interceptor configuration file results in the following XML:</span></span>  
  
```  
<ic:Filter>  
  <ic:Expression>  
    <wf:Operation Name="GetActivityName"/>  
    <ic:Operation Name="Constant">  
      <ic:Argument>FoodAndDrinksPolicy</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals"/>  
    <wf:Operation Name="GetActivityEvent"/>  
    <ic:Operation Name="Constant">  
      <ic:Argument>Closed</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals"/>  
    <ic:Operation Name="And"/>  
  </ic:Expression>  
</ic:Filter>  
```  
  
 <span data-ttu-id="394e8-163">Enfin, cette expression est évaluée comme suit en supposant que **GetActivityName** renvoie « DessertPolicy » et **GetActivityEvent** retourné « Closed » :</span><span class="sxs-lookup"><span data-stu-id="394e8-163">Finally, this expression would be evaluated as follows assuming **GetActivityName** returned "DessertPolicy" and **GetActivityEvent** returned "Closed":</span></span>  
  
|<span data-ttu-id="394e8-164">Entrée</span><span class="sxs-lookup"><span data-stu-id="394e8-164">Input</span></span>|<span data-ttu-id="394e8-165">Opération</span><span class="sxs-lookup"><span data-stu-id="394e8-165">Operation</span></span>|<span data-ttu-id="394e8-166">Pile</span><span class="sxs-lookup"><span data-stu-id="394e8-166">Stack</span></span>|  
|-----------|---------------|-----------|  
||<span data-ttu-id="394e8-167">GetActivityName</span><span class="sxs-lookup"><span data-stu-id="394e8-167">GetActivityName</span></span>|<span data-ttu-id="394e8-168">« DessertPolicy »</span><span class="sxs-lookup"><span data-stu-id="394e8-168">"DessertPolicy"</span></span>|  
|<span data-ttu-id="394e8-169">« FoodAndDrinksPolicy »</span><span class="sxs-lookup"><span data-stu-id="394e8-169">"FoodAndDrinksPolicy"</span></span>|<span data-ttu-id="394e8-170">Constante</span><span class="sxs-lookup"><span data-stu-id="394e8-170">Constant</span></span>|<span data-ttu-id="394e8-171">« DessertPolicy », « FoodAndDrinksPolicy »</span><span class="sxs-lookup"><span data-stu-id="394e8-171">"DessertPolicy", "FoodAndDrinksPolicy"</span></span>|  
|<span data-ttu-id="394e8-172">Égal à</span><span class="sxs-lookup"><span data-stu-id="394e8-172">Equals</span></span>|<span data-ttu-id="394e8-173">Comparaison</span><span class="sxs-lookup"><span data-stu-id="394e8-173">Comparison</span></span>|<span data-ttu-id="394e8-174">False</span><span class="sxs-lookup"><span data-stu-id="394e8-174">False</span></span>|  
||<span data-ttu-id="394e8-175">GetActivityEvent</span><span class="sxs-lookup"><span data-stu-id="394e8-175">GetActivityEvent</span></span>|<span data-ttu-id="394e8-176">False, « Closed »</span><span class="sxs-lookup"><span data-stu-id="394e8-176">False, Closed</span></span>|  
|<span data-ttu-id="394e8-177">« Closed »</span><span class="sxs-lookup"><span data-stu-id="394e8-177">"Closed"</span></span>|<span data-ttu-id="394e8-178">Constante</span><span class="sxs-lookup"><span data-stu-id="394e8-178">Constant</span></span>|<span data-ttu-id="394e8-179">False, « Closed », « Closed »</span><span class="sxs-lookup"><span data-stu-id="394e8-179">False, "Closed", "Closed"</span></span>|  
|<span data-ttu-id="394e8-180">Égal à</span><span class="sxs-lookup"><span data-stu-id="394e8-180">Equals</span></span>|<span data-ttu-id="394e8-181">Comparaison</span><span class="sxs-lookup"><span data-stu-id="394e8-181">Comparison</span></span>|<span data-ttu-id="394e8-182">False, True</span><span class="sxs-lookup"><span data-stu-id="394e8-182">False, True</span></span>|  
|<span data-ttu-id="394e8-183">And</span><span class="sxs-lookup"><span data-stu-id="394e8-183">And</span></span>|<span data-ttu-id="394e8-184">AND logique</span><span class="sxs-lookup"><span data-stu-id="394e8-184">Logical And</span></span>|<span data-ttu-id="394e8-185">False</span><span class="sxs-lookup"><span data-stu-id="394e8-185">False</span></span>|  
  
 <span data-ttu-id="394e8-186">La valeur restante sur la pile est le booléen `False`.</span><span class="sxs-lookup"><span data-stu-id="394e8-186">The value left on the stack is Boolean `False`.</span></span> <span data-ttu-id="394e8-187">Cela entraînera le non-déclenchement de l'événement correspondant.</span><span class="sxs-lookup"><span data-stu-id="394e8-187">This will cause the corresponding event to not fire.</span></span> <span data-ttu-id="394e8-188">Si le nom de l'activité avait été « FoodAndDrinksPolicy », alors il aurait donné le booléen `True`.</span><span class="sxs-lookup"><span data-stu-id="394e8-188">If the activity name were "FoodAndDrinksPolicy" then it would have evaluated to Boolean `True`.</span></span>  
  
 <span data-ttu-id="394e8-189">Vous pouvez créer une expression similaire (avec une évaluation similaire) à l'aide des opérations WCF `GetEndpointName` et `GetOperationName`.</span><span class="sxs-lookup"><span data-stu-id="394e8-189">You can construct a similar expression (with a similar evaluation) by using the WCF operations `GetEndpointName` and `GetOperationName`.</span></span>  
  
### <a name="data-expressions"></a><span data-ttu-id="394e8-190">Expressions de données</span><span class="sxs-lookup"><span data-stu-id="394e8-190">Data Expressions</span></span>  
 <span data-ttu-id="394e8-191">Les expressions de données permettent de définir une valeur de données de chaîne unique.</span><span class="sxs-lookup"><span data-stu-id="394e8-191">Data expressions are used to define a single string data value.</span></span> <span data-ttu-id="394e8-192">Une expression de données est une expression qui n'est pas incluse par un élément `Filter`.</span><span class="sxs-lookup"><span data-stu-id="394e8-192">A data expression is any expression that is not enclosed by a `Filter` element.</span></span> <span data-ttu-id="394e8-193">Les expressions de données sont utilisées par les éléments `OnEvent`, `CorrelationID`, `ContinuationToken`, `Reference` et `Update`.</span><span class="sxs-lookup"><span data-stu-id="394e8-193">Data expressions are used by the `OnEvent` elements `CorrelationID`, `ContinuationToken`, `Reference`, and `Update`.</span></span>  
  
 <span data-ttu-id="394e8-194">Il est courant de devoir mettre à jour la base de données des activités BAM avec un horodatage étiqueté.</span><span class="sxs-lookup"><span data-stu-id="394e8-194">It is a common requirement to update the BAM activity database with a labeled time stamp.</span></span> <span data-ttu-id="394e8-195">Par exemple, vous pourriez capturer l’heure de début d’un événement avec une chaîne sous la forme « Démarrer : \<EventTime > ».</span><span class="sxs-lookup"><span data-stu-id="394e8-195">For example, you might want to capture the time an event starts with a string formatted as "Start: \<EventTime>".</span></span> <span data-ttu-id="394e8-196">Pour ce faire, vous devez utiliser une expression semblable à celle qui suit (où + représente une concaténation) :</span><span class="sxs-lookup"><span data-stu-id="394e8-196">To do this, you need to use an expression similar to the following (where + represents concatenation):</span></span>  
  
 `"Start: " + GetContextProperty(EventTime)`  
  
 <span data-ttu-id="394e8-197">Sa conversion en NPI donne :</span><span class="sxs-lookup"><span data-stu-id="394e8-197">Converting this to RPN yields:</span></span>  
  
 `"Start: " GetContextProperty(EventTime) +`  
  
 <span data-ttu-id="394e8-198">La conversion de cette expression en son expression équivalente pour un élément `Update` du fichier de configuration de l'intercepteur donne le code XML suivant :</span><span class="sxs-lookup"><span data-stu-id="394e8-198">Converting this expression to the equivalent expression for an `Update` element in the interceptor configuration file results in the following XML:</span></span>  
  
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
  
 <span data-ttu-id="394e8-199">Le tableau suivant montre comment cette expression serait interprétée si l'heure de l'événement était minuit (« 12:00 PM »).</span><span class="sxs-lookup"><span data-stu-id="394e8-199">The following table shows how this expression would be interpreted if the event time was "12:00 PM".</span></span>  
  
|<span data-ttu-id="394e8-200">Entrée</span><span class="sxs-lookup"><span data-stu-id="394e8-200">Input</span></span>|<span data-ttu-id="394e8-201">Opération</span><span class="sxs-lookup"><span data-stu-id="394e8-201">Operation</span></span>|<span data-ttu-id="394e8-202">Pile</span><span class="sxs-lookup"><span data-stu-id="394e8-202">Stack</span></span>|  
|-----------|---------------|-----------|  
|<span data-ttu-id="394e8-203">« Start:  »</span><span class="sxs-lookup"><span data-stu-id="394e8-203">"Start: "</span></span>|<span data-ttu-id="394e8-204">Constante</span><span class="sxs-lookup"><span data-stu-id="394e8-204">Constant</span></span>|<span data-ttu-id="394e8-205">« Start:  »</span><span class="sxs-lookup"><span data-stu-id="394e8-205">"Start: "</span></span>|  
|<span data-ttu-id="394e8-206">GetContextProperty(EventTime)</span><span class="sxs-lookup"><span data-stu-id="394e8-206">GetContextProperty(EventTime)</span></span>|<span data-ttu-id="394e8-207">Envoi de données (push)</span><span class="sxs-lookup"><span data-stu-id="394e8-207">Push</span></span>|<span data-ttu-id="394e8-208">« Start:  », « 2006-09-27T12:00:34.000Z »</span><span class="sxs-lookup"><span data-stu-id="394e8-208">"Start: ", "2006-09-27T12:00:34.000Z"</span></span>|  
|<span data-ttu-id="394e8-209">Concaténation</span><span class="sxs-lookup"><span data-stu-id="394e8-209">Concatenate</span></span>|<span data-ttu-id="394e8-210">Concaténation</span><span class="sxs-lookup"><span data-stu-id="394e8-210">Concatenate</span></span>|<span data-ttu-id="394e8-211">« Start: 2006-09-27T12:00:34.000Z »</span><span class="sxs-lookup"><span data-stu-id="394e8-211">"Start: 2006-09-27T12:00:34.000Z"</span></span>|  
  
 <span data-ttu-id="394e8-212">La valeur utilisée par la commande de mise à jour serait « Start: 2006-09-27T12:00:34.000Z ».</span><span class="sxs-lookup"><span data-stu-id="394e8-212">The value used by the update command would be "Start: 2006-09-27T12:00:34.000Z".</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="394e8-213">N'utilisez pas les opérations de comparaison « And » ou « Égal à » dans les expressions de données.</span><span class="sxs-lookup"><span data-stu-id="394e8-213">Do not use the comparison operations "And" or "Equals" in data expressions.</span></span> <span data-ttu-id="394e8-214">Sinon, vous obtenez une erreur lors du déploiement de votre fichier de configuration de l'intercepteur.</span><span class="sxs-lookup"><span data-stu-id="394e8-214">If you do, you will receive an error when deploying your interceptor configuration file.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="394e8-215">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="394e8-215">In This Section</span></span>  
 [<span data-ttu-id="394e8-216">Opérations de l’intercepteur</span><span class="sxs-lookup"><span data-stu-id="394e8-216">Interceptor Operations</span></span>](../core/interceptor-operations.md)  
  
## <a name="see-also"></a><span data-ttu-id="394e8-217">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="394e8-217">See Also</span></span>  
 [<span data-ttu-id="394e8-218">Structure d’un fichier de Configuration de l’intercepteur</span><span class="sxs-lookup"><span data-stu-id="394e8-218">Structure of an Interceptor Configuration File</span></span>](../core/structure-of-an-interceptor-configuration-file.md)