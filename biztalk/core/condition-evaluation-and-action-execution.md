---
title: "Condition d’évaluation et d’exécution d’Action | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Action stage [Business Rules Engine]
- examples, business rules
- Business Rules Engine, policies
- Match stage [Business Rules Engine]
- business rules, examples
- Business Rules Engine, algorithm
- Business Rules Engine, examples
- conflict resolution [Business Rules Engine]
- Business Rules Engine, stages
ms.assetid: dcaa32c2-3403-4f54-92e2-128686bfc193
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2814a97c1907b1bb29eee2a718d04d14cfe901a6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="condition-evaluation-and-action-execution"></a><span data-ttu-id="55a1b-102">Évaluation de condition et exécution d'action</span><span class="sxs-lookup"><span data-stu-id="55a1b-102">Condition Evaluation and Action Execution</span></span>
<span data-ttu-id="55a1b-103">L'infrastructure des règles d'entreprise fournit un moteur d'inférence très performant, capable de lier des règles à des documents XML, des tables de base de données ou des objets .NET.</span><span class="sxs-lookup"><span data-stu-id="55a1b-103">The Business Rules Framework provides a highly efficient inference engine capable of linking rules to .NET objects, XML documents, or database tables.</span></span>  
  
 <span data-ttu-id="55a1b-104">Le moteur des règles d'entreprise utilise un algorithme en trois étapes pour l'exécution des stratégies.</span><span class="sxs-lookup"><span data-stu-id="55a1b-104">The Business Rule Engine uses a three-stage algorithm for policy execution.</span></span> <span data-ttu-id="55a1b-105">Ces trois étapes sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="55a1b-105">The stages are as follows:</span></span>  
  
-   <span data-ttu-id="55a1b-106">**Correspondance**.</span><span class="sxs-lookup"><span data-stu-id="55a1b-106">**Match**.</span></span> <span data-ttu-id="55a1b-107">À cette étape, les faits sont mis en correspondance avec les prédicats qui utilisent le type de fait (références d'objet conservées dans la mémoire de travail du moteur des règles) en se servant des prédicats définis dans les conditions de règle.</span><span class="sxs-lookup"><span data-stu-id="55a1b-107">In the match stage, facts are matched against the predicates that use the fact type (object references maintained in the rule engine's working memory) using the predicates defined in the rule conditions.</span></span> <span data-ttu-id="55a1b-108">Pour des raisons d'efficacité, la mise correspondance avec un modèle est appliquée à toutes les règles de la stratégie et les conditions partagées par ces règles ne sont mises en correspondance qu'une seule fois.</span><span class="sxs-lookup"><span data-stu-id="55a1b-108">For the sake of efficiency, pattern matching occurs over all the rules in the policy, and conditions that are shared across rules are matched only once.</span></span> <span data-ttu-id="55a1b-109">Des correspondances de condition partielles peuvent être stockées dans la mémoire de travail pour accélérer les opérations ultérieures de mise en correspondance avec un modèle.</span><span class="sxs-lookup"><span data-stu-id="55a1b-109">Partial condition matches may be stored in working memory to expedite subsequent pattern-matching operations.</span></span> <span data-ttu-id="55a1b-110">Le résultat de la phase de mise en correspondance avec un modèle consiste en des mises à jour de l'agenda du moteur des règles.</span><span class="sxs-lookup"><span data-stu-id="55a1b-110">The output of the pattern-matching phase consists of updates to the rule engine agenda.</span></span>  
  
-   <span data-ttu-id="55a1b-111">**Résolution des conflits**.</span><span class="sxs-lookup"><span data-stu-id="55a1b-111">**Conflict resolution**.</span></span> <span data-ttu-id="55a1b-112">Dans la phase de résolution de conflit, les règles qui sont des candidats pour l’exécution sont examinées pour déterminer l’ensemble suivant de l’exécution des actions de règle basée sur un schéma de résolution prédéterminé.</span><span class="sxs-lookup"><span data-stu-id="55a1b-112">In the conflict resolution stage, the rules that are candidates for execution are examined to determine the next set of rule actions to execute based on a predetermined resolution scheme.</span></span> <span data-ttu-id="55a1b-113">Toutes les règles candidates trouvées lors de l'étape de mise en correspondance sont ajoutées à l'agenda du moteur des règles.</span><span class="sxs-lookup"><span data-stu-id="55a1b-113">All candidate rules found during the matching stage are added to the rule engine's agenda.</span></span>  
  
     <span data-ttu-id="55a1b-114">Le schéma de résolution des conflits par défaut est basé sur des priorités de règle dans une stratégie.</span><span class="sxs-lookup"><span data-stu-id="55a1b-114">The default conflict resolution scheme is based on rule priorities within a policy.</span></span> <span data-ttu-id="55a1b-115">La priorité est une propriété configurable d'une règle dans l'Éditeur des règles d'entreprise.</span><span class="sxs-lookup"><span data-stu-id="55a1b-115">The priority is a configurable property of a rule in the Business Rule Composer.</span></span> <span data-ttu-id="55a1b-116">Plus le nombre est grand, plus la priorité est élevée. Par conséquent, si plusieurs règles sont déclenchées, les actions ayant la priorité la plus élevée sont exécutées en premier.</span><span class="sxs-lookup"><span data-stu-id="55a1b-116">The larger the number, the higher the priority; therefore if multiple rules are triggered, the higher-priority actions are executed first.</span></span>  
  
-   <span data-ttu-id="55a1b-117">**Action**.</span><span class="sxs-lookup"><span data-stu-id="55a1b-117">**Action**.</span></span> <span data-ttu-id="55a1b-118">Dans cette étape, les actions de la règle résolue sont exécutées.</span><span class="sxs-lookup"><span data-stu-id="55a1b-118">In the action stage, the actions in the resolved rule are executed.</span></span> <span data-ttu-id="55a1b-119">Notez que des actions de règle peuvent déclarer de nouveaux faits dans le moteur des règles, ce qui engendre la poursuite du cycle.</span><span class="sxs-lookup"><span data-stu-id="55a1b-119">Note that rule actions can assert new facts into the rule engine, which causes the cycle to continue.</span></span> <span data-ttu-id="55a1b-120">Ceci est également connu sous le nom de chaînage avant.</span><span class="sxs-lookup"><span data-stu-id="55a1b-120">This is also known as forward chaining.</span></span> <span data-ttu-id="55a1b-121">Il est important de noter que l'algorithme ne prévaut jamais sur la règle en cours d'exécution.</span><span class="sxs-lookup"><span data-stu-id="55a1b-121">It is important to note that the algorithm never preempts the currently executing rule.</span></span> <span data-ttu-id="55a1b-122">Toutes les actions de la règle actuellement en cours seront exécutées avant que la phase de correspondance soit répétée.</span><span class="sxs-lookup"><span data-stu-id="55a1b-122">All actions for the rule that is currently firing will be executed before the match phase is repeated.</span></span> <span data-ttu-id="55a1b-123">Toutefois, les autres règles de l'agenda ne seront pas déclenchées tant que la phase de correspondance n'aura pas recommencé.</span><span class="sxs-lookup"><span data-stu-id="55a1b-123">However, other rules on the agenda will not be fired before the match phase begins again.</span></span> <span data-ttu-id="55a1b-124">La phase de correspondance peut provoquer la suppression des règles de l'agenda avant même leur déclenchement.</span><span class="sxs-lookup"><span data-stu-id="55a1b-124">The match phase may cause those rules on the agenda to be removed from the agenda before they ever fire.</span></span>  
  
 <span data-ttu-id="55a1b-125">L'exemple suivant illustre l'algorithme en trois étapes (correspondance, résolution des conflits, action).</span><span class="sxs-lookup"><span data-stu-id="55a1b-125">The following example shows the three-stage algorithm of match-conflict resolution-action.</span></span>  
  
 <span data-ttu-id="55a1b-126">**Règle 1 : Évaluation des revenus**</span><span class="sxs-lookup"><span data-stu-id="55a1b-126">**Rule 1: Evaluate income**</span></span>  
  
-   <span data-ttu-id="55a1b-127">Représentation déclarative :</span><span class="sxs-lookup"><span data-stu-id="55a1b-127">Declarative representation:</span></span>  
  
     <span data-ttu-id="55a1b-128">Un client ne peut prétendre à des conditions de crédit que si son taux de solvabilité est inférieur à 0,2.</span><span class="sxs-lookup"><span data-stu-id="55a1b-128">An applicant's credit rating should be obtained only if the applicant's income-to-loan ratio is less than 0.2.</span></span>  
  
-   <span data-ttu-id="55a1b-129">Représentation IF—THEN à l'aide d'objets métier :</span><span class="sxs-lookup"><span data-stu-id="55a1b-129">IF—THEN representation using business objects:</span></span>  
  
    ```  
    IF Application.Income / Property.Price < 0.2    
    THEN Assert new CreditRating( Application)   
    ```  
  
 <span data-ttu-id="55a1b-130">**Règle 2 : Évaluer les conditions de crédit**</span><span class="sxs-lookup"><span data-stu-id="55a1b-130">**Rule 2: Evaluate credit rating**</span></span>  
  
-   <span data-ttu-id="55a1b-131">Représentation déclarative :</span><span class="sxs-lookup"><span data-stu-id="55a1b-131">Declarative representation:</span></span>  
  
     <span data-ttu-id="55a1b-132">Un candidat ne peut être approuvé que si ses conditions de crédit sont supérieures à 725.</span><span class="sxs-lookup"><span data-stu-id="55a1b-132">An applicant should be approved only if the applicant's credit rating is more than 725.</span></span>  
  
-   <span data-ttu-id="55a1b-133">IF, puis la représentation sous forme de l’utilisation des objets métier :</span><span class="sxs-lookup"><span data-stu-id="55a1b-133">IF—THEN Representation using business objects:</span></span>  
  
    ```  
    IF Application.SSN = CreditRating.SSN AND CreditRating.Value > 725    
    THEN SendApprovalLetter(Application)    
    ```  
  
 <span data-ttu-id="55a1b-134">Les faits sont synthétisés dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="55a1b-134">The facts are summarized in the following table.</span></span>  
  
|<span data-ttu-id="55a1b-135">Fait</span><span class="sxs-lookup"><span data-stu-id="55a1b-135">Fact</span></span>|<span data-ttu-id="55a1b-136">Champs</span><span class="sxs-lookup"><span data-stu-id="55a1b-136">Fields</span></span>|  
|----------|------------|  
|<span data-ttu-id="55a1b-137">Application – Document XML représentant une demande de prêt immobilier</span><span class="sxs-lookup"><span data-stu-id="55a1b-137">Application – An XML document representing a home loan application</span></span>|<span data-ttu-id="55a1b-138">-Income = $65,000</span><span class="sxs-lookup"><span data-stu-id="55a1b-138">-   Income = $65,000</span></span><br /><span data-ttu-id="55a1b-139">-SSN = XXX-XX-XXXX</span><span class="sxs-lookup"><span data-stu-id="55a1b-139">-   SSN = XXX-XX-XXXX</span></span>|  
|<span data-ttu-id="55a1b-140">Property – Document XML représentant le bien acheté</span><span class="sxs-lookup"><span data-stu-id="55a1b-140">Property – An XML document representing the property being purchased</span></span>|<span data-ttu-id="55a1b-141">-Prix = $225,000</span><span class="sxs-lookup"><span data-stu-id="55a1b-141">-   Price = $225,000</span></span>|  
|<span data-ttu-id="55a1b-142">CreditRating –Document XML contenant les conditions de crédit du candidat</span><span class="sxs-lookup"><span data-stu-id="55a1b-142">CreditRating – An XML document containing the loan applicant's credit rating</span></span>|<span data-ttu-id="55a1b-143">-Valeur = 0-800</span><span class="sxs-lookup"><span data-stu-id="55a1b-143">-   Value = 0 – 800</span></span><br /><span data-ttu-id="55a1b-144">-SSN = XXX-XX-XXXX</span><span class="sxs-lookup"><span data-stu-id="55a1b-144">-   SSN = XXX-XX-XXXX</span></span>|  
  
 <span data-ttu-id="55a1b-145">L'agenda et la mémoire de travail du moteur de règles sont initialement vides.</span><span class="sxs-lookup"><span data-stu-id="55a1b-145">Initially the rule engine working memory and agenda are empty.</span></span> <span data-ttu-id="55a1b-146">Une fois que l'application a ajouté les faits Application et Property, l'agenda et la mémoire de travail du moteur de règles sont mis à jour comme suit.</span><span class="sxs-lookup"><span data-stu-id="55a1b-146">After the application adds the Application and Property facts, the rule engine working memory and agenda are updated as follows.</span></span>  
  
|<span data-ttu-id="55a1b-147">Mémoire de travail</span><span class="sxs-lookup"><span data-stu-id="55a1b-147">Working memory</span></span>|<span data-ttu-id="55a1b-148">Agenda</span><span class="sxs-lookup"><span data-stu-id="55a1b-148">Agenda</span></span>|  
|--------------------|------------|  
|<span data-ttu-id="55a1b-149">-Application</span><span class="sxs-lookup"><span data-stu-id="55a1b-149">-   Application</span></span><br /><span data-ttu-id="55a1b-150">-Propriété</span><span class="sxs-lookup"><span data-stu-id="55a1b-150">-   Property</span></span>|<span data-ttu-id="55a1b-151">Règle 1</span><span class="sxs-lookup"><span data-stu-id="55a1b-151">Rule 1</span></span>|  
  
 <span data-ttu-id="55a1b-152">Règle 1 est ajoutée à l’agenda car sa condition (application.Income/Property.Price / considérée comme < 0,2) évaluée à **true** pendant la phase de correspondance.</span><span class="sxs-lookup"><span data-stu-id="55a1b-152">Rule 1 is added to the agenda because its condition (Application.Income / Property.Price < 0.2) evaluated to **true** during the match phase.</span></span> <span data-ttu-id="55a1b-153">Aucun fait CreditRating n'est dans la mémoire de travail. La condition de Règle 2 n'a donc pas été évaluée.</span><span class="sxs-lookup"><span data-stu-id="55a1b-153">There is no CreditRating fact in working memory, so the condition for Rule 2 was not evaluated.</span></span> <span data-ttu-id="55a1b-154">Dans la mesure où la seule règle présente dans l'agenda est Règle 1, la règle est exécutée, puis disparaît de l'agenda.</span><span class="sxs-lookup"><span data-stu-id="55a1b-154">Because the only rule in the agenda is Rule 1, the rule is executed and then disappears from the agenda.</span></span> <span data-ttu-id="55a1b-155">La seule action définie pour Règle 1 entraîne l'ajout d'un nouveau fait (document CreditRating pour le candidat) dans la mémoire de travail.</span><span class="sxs-lookup"><span data-stu-id="55a1b-155">The single action defined for Rule 1 results in a new fact (CreditRating document for the applicant) being added to working memory.</span></span> <span data-ttu-id="55a1b-156">Lorsque l'exécution de Règle 1 est terminée, le contrôle revient à la phase de correspondance.</span><span class="sxs-lookup"><span data-stu-id="55a1b-156">After the execution of Rule 1 completes, control returns to the match phase.</span></span> <span data-ttu-id="55a1b-157">Dans la mesure où le seul nouvel objet correspondant est le fait CreditRating, le résultat de la phase de correspondance est le suivant.</span><span class="sxs-lookup"><span data-stu-id="55a1b-157">Because the only new object to match is the CreditRating fact, the results of the match phase are as follows.</span></span>  
  
|<span data-ttu-id="55a1b-158">Mémoire de travail</span><span class="sxs-lookup"><span data-stu-id="55a1b-158">Working memory</span></span>|<span data-ttu-id="55a1b-159">Agenda</span><span class="sxs-lookup"><span data-stu-id="55a1b-159">Agenda</span></span>|  
|--------------------|------------|  
|<span data-ttu-id="55a1b-160">-Application</span><span class="sxs-lookup"><span data-stu-id="55a1b-160">-   Application</span></span><br /><span data-ttu-id="55a1b-161">-Propriété</span><span class="sxs-lookup"><span data-stu-id="55a1b-161">-   Property</span></span><br /><span data-ttu-id="55a1b-162">-CreditRating</span><span class="sxs-lookup"><span data-stu-id="55a1b-162">-   CreditRating</span></span>|<span data-ttu-id="55a1b-163">Règle 2</span><span class="sxs-lookup"><span data-stu-id="55a1b-163">Rule 2</span></span>|  
  
 <span data-ttu-id="55a1b-164">À ce stade, Règle 2 est exécutée, ce qui entraîne l'appel d'une fonction qui envoie une lettre d'approbation au candidat.</span><span class="sxs-lookup"><span data-stu-id="55a1b-164">At this point Rule 2 is executed, resulting in the invocation of a function that sends an approval letter to the applicant.</span></span> <span data-ttu-id="55a1b-165">Une fois Règle 2 terminée, l'exécution de l'algorithme à chaînage avant revient à la phase de correspondance.</span><span class="sxs-lookup"><span data-stu-id="55a1b-165">After Rule 2 has completed, execution of the forward-chaining algorithm returns to the match phase.</span></span> <span data-ttu-id="55a1b-166">Comme il n'existe plus aucun nouveau fait à mettre en correspondance et que l'agenda est vide, le chaînage avant s'arrête et l'exécution de la stratégie se termine.</span><span class="sxs-lookup"><span data-stu-id="55a1b-166">Because there are no longer new facts to match and the agenda is empty, forward chaining terminates and policy execution is complete.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55a1b-167">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="55a1b-167">See Also</span></span>  
 [<span data-ttu-id="55a1b-168">Moteur de règles</span><span class="sxs-lookup"><span data-stu-id="55a1b-168">Rule Engine</span></span>](../core/rule-engine.md)