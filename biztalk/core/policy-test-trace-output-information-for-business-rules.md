---
title: "Informations de sortie de Trace de Test de stratégie pour des règles d’entreprise | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- testing, business rules
- testing, policies
- business rules, testing
- policies, testing
ms.assetid: 26ff584e-97a1-4d76-a8a9-a55b4c99231f
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c223e8bddae1ff68e77cdf881ea22e6be4cdab9a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="policy-test-trace-output-information-for-business-rules"></a><span data-ttu-id="6c356-102">Informations concernant le résultat du suivi du test de stratégies pour les règles d'entreprise</span><span class="sxs-lookup"><span data-stu-id="6c356-102">Policy Test Trace Output Information for Business Rules</span></span>
<span data-ttu-id="6c356-103">Cette section propose des informations sur les informations de suivi affichées lors du test d'une stratégie dans l'Éditeur des règles d’entreprise.</span><span class="sxs-lookup"><span data-stu-id="6c356-103">This section provides information on the tracking information that is displayed when testing a policy in the Business Rule Composer.</span></span> <span data-ttu-id="6c356-104">Des informations similaires sont visibles lorsque vous affichez les résultats du suivi de l'exécution des stratégies à l'aide des requêtes de suivi des événements de messages et des instances de service dans la page Hub du groupe.</span><span class="sxs-lookup"><span data-stu-id="6c356-104">Very similar information is seen when viewing tracking results for policy execution using the message event and service instance tracking queries on the Group Hub page.</span></span>  
  
 <span data-ttu-id="6c356-105">Quatre types d’instructions sont affichés dans le résultat de suivi :</span><span class="sxs-lookup"><span data-stu-id="6c356-105">There are four statement types that are displayed in the tracking output:</span></span>  
  
-   <span data-ttu-id="6c356-106">Activité des faits</span><span class="sxs-lookup"><span data-stu-id="6c356-106">Fact Activity</span></span>  
  
-   <span data-ttu-id="6c356-107">Évaluation de condition</span><span class="sxs-lookup"><span data-stu-id="6c356-107">Condition Evaluation</span></span>  
  
-   <span data-ttu-id="6c356-108">Mise à jour de l'agenda</span><span class="sxs-lookup"><span data-stu-id="6c356-108">Agenda Update</span></span>  
  
-   <span data-ttu-id="6c356-109">Règle déclenchée</span><span class="sxs-lookup"><span data-stu-id="6c356-109">Rule Fired</span></span>  
  
 <span data-ttu-id="6c356-110">Chaque type d’instruction est décrit ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="6c356-110">Each statement type is described below.</span></span>  
  
## <a name="fact-activity"></a><span data-ttu-id="6c356-111">Activité des faits</span><span class="sxs-lookup"><span data-stu-id="6c356-111">Fact Activity</span></span>  
 <span data-ttu-id="6c356-112">Cette instruction indique les modifications apportées aux faits présents dans la mémoire de travail du moteur.</span><span class="sxs-lookup"><span data-stu-id="6c356-112">This statement indicates changes to the facts present in the working memory of the engine.</span></span> <span data-ttu-id="6c356-113">L’exemple suivant illustre une entrée d’activité des faits :</span><span class="sxs-lookup"><span data-stu-id="6c356-113">The following is an example of a fact activity entry:</span></span>  
  
```  
FACT ACTIVITY 3/16/2004 9:50:28 AM  
Rule Engine Instance Identifier: 9effe3f9-d3ad-4125-99fa-56bb379188f7  
Ruleset Name: LoanProcessing  
Operation: Assert  
Object Type: MyTest.test  
Object Instance Identifier: 872  
```  
  
### <a name="rule-engine-instance-identifier"></a><span data-ttu-id="6c356-114">Identificateur de l'instance du moteur de règles</span><span class="sxs-lookup"><span data-stu-id="6c356-114">Rule Engine Instance Identifier</span></span>  
 <span data-ttu-id="6c356-115">Identificateur unique pour le **RuleEngine** instance qui fournit l’environnement d’exécution pour l’activation de règle.</span><span class="sxs-lookup"><span data-stu-id="6c356-115">Unique identifier for the **RuleEngine** instance that provides the execution environment for the rule firing.</span></span>  
  
### <a name="ruleset-name"></a><span data-ttu-id="6c356-116">Nom de l'ensemble des règles</span><span class="sxs-lookup"><span data-stu-id="6c356-116">Ruleset Name</span></span>  
 <span data-ttu-id="6c356-117">Nom de l’ensemble de règles (stratégie).</span><span class="sxs-lookup"><span data-stu-id="6c356-117">The name of the rule set (policy).</span></span>  
  
### <a name="operation"></a><span data-ttu-id="6c356-118">Opération</span><span class="sxs-lookup"><span data-stu-id="6c356-118">Operation</span></span>  
 <span data-ttu-id="6c356-119">Il existe trois types d’opérations pouvant intervenir dans une activité de faits :</span><span class="sxs-lookup"><span data-stu-id="6c356-119">There are three types of operation that can occur in a fact activity:</span></span>  
  
 <span data-ttu-id="6c356-120">Assert</span><span class="sxs-lookup"><span data-stu-id="6c356-120">Assert</span></span>  
  
 <span data-ttu-id="6c356-121">Le fait est ajouté à la mémoire de travail.</span><span class="sxs-lookup"><span data-stu-id="6c356-121">The fact is being added to the working memory.</span></span>  
  
 <span data-ttu-id="6c356-122">Update</span><span class="sxs-lookup"><span data-stu-id="6c356-122">Update</span></span>  
  
 <span data-ttu-id="6c356-123">Le fait est mis à jour par une règle et doit être redéclaré dans le moteur pour être ré-évalué, à partir des nouvelles données et du nouvel état.</span><span class="sxs-lookup"><span data-stu-id="6c356-123">The fact is being updated by a rule and then needs to be reasserted into the engine to be re-evaluated, based on the new data and state.</span></span>  
  
 <span data-ttu-id="6c356-124">Retract</span><span class="sxs-lookup"><span data-stu-id="6c356-124">Retract</span></span>  
  
 <span data-ttu-id="6c356-125">Le fait est supprimé de la mémoire de travail.</span><span class="sxs-lookup"><span data-stu-id="6c356-125">The fact is being removed from the working memory.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6c356-126">Si un fait est déclaré dont le type ne correspond pas à un des types utilisés dans la stratégie, l’opération déclarer affiche « Déclarer-fait non reconnu ».</span><span class="sxs-lookup"><span data-stu-id="6c356-126">If a fact is asserted whose type does not match any of the types used in the policy, the Assert operation will display "Assert – Fact Unrecognized".</span></span>  
  
### <a name="object-type"></a><span data-ttu-id="6c356-127">Type d'objet</span><span class="sxs-lookup"><span data-stu-id="6c356-127">Object Type</span></span>  
 <span data-ttu-id="6c356-128">Type de fait d'une activité particulière :</span><span class="sxs-lookup"><span data-stu-id="6c356-128">The type of fact for a particular activity:</span></span>  
  
-   <span data-ttu-id="6c356-129">DataConnection</span><span class="sxs-lookup"><span data-stu-id="6c356-129">DataConnection</span></span>  
  
-   <span data-ttu-id="6c356-130">TypedDataTable</span><span class="sxs-lookup"><span data-stu-id="6c356-130">TypedDataTable</span></span>  
  
-   <span data-ttu-id="6c356-131">TypedDataRow</span><span class="sxs-lookup"><span data-stu-id="6c356-131">TypedDataRow</span></span>  
  
     <span data-ttu-id="6c356-132">Lorsqu’un TypedDataTable est déclaré, toutes les lignes contenues sont déclarées en tant que TypedDataRows.</span><span class="sxs-lookup"><span data-stu-id="6c356-132">When a TypedDataTable is asserted all of the contained rows are asserted as TypedDataRows.</span></span>  <span data-ttu-id="6c356-133">Les TypedDataRows associés à une DataConnection ne sont pas déclarés, jusqu’à ce qu’une condition soit évaluée et que la requête qui en résulte soit exécutée.</span><span class="sxs-lookup"><span data-stu-id="6c356-133">TypedDataRows associated with a DataConnection are not asserted until a condition is evaluated and the resulting query is executed.</span></span>  
  
-   <span data-ttu-id="6c356-134">TypedXmlDocument</span><span class="sxs-lookup"><span data-stu-id="6c356-134">TypedXmlDocument</span></span>  
  
     <span data-ttu-id="6c356-135">Les assertions sont affichées à la fois pour les instances TypedXmlDocument parentes et enfants.</span><span class="sxs-lookup"><span data-stu-id="6c356-135">Assertions will be seen for both parent and child TypedXmlDocument instances.</span></span>  
  
### <a name="object-instance-identifier"></a><span data-ttu-id="6c356-136">Identificateur de l'instance d'objet</span><span class="sxs-lookup"><span data-stu-id="6c356-136">Object Instance Identifier</span></span>  
 <span data-ttu-id="6c356-137">ID d'instance unique de la référence de fait.</span><span class="sxs-lookup"><span data-stu-id="6c356-137">Unique instance ID of the fact reference.</span></span>  
  
## <a name="condition-evaluation"></a><span data-ttu-id="6c356-138">Évaluation de condition</span><span class="sxs-lookup"><span data-stu-id="6c356-138">Condition Evaluation</span></span>  
 <span data-ttu-id="6c356-139">Cette activité indique le résultat de l’évaluation des prédicats individuels.</span><span class="sxs-lookup"><span data-stu-id="6c356-139">This activity indicates the result of evaluating individual predicates.</span></span> <span data-ttu-id="6c356-140">L’exemple suivant illustre une évaluation de condition :</span><span class="sxs-lookup"><span data-stu-id="6c356-140">The following is an example of a condition evaluation entry:</span></span>  
  
```  
CONDITION EVALUATION TEST (MATCH) 1/07/2004 5:33:13 PM  
Rule Engine Instance Identifier: f1dd3ff2-b4a8-4fe1-8d46-4d9b3e2502d3  
Ruleset Name: LoanProcessing  
Test Expression: TypedXmlDocument:Microsoft.Samples.BizTalk.LoansProcessor.Case:Root.EmploymentType/TimeInMonths >= 18  
Left Operand Value: 31  
Right Operand Value: 18  
Test Result: True  
```  
  
 <span data-ttu-id="6c356-141">Voici la description de certains des termes de l'exemple précédent :</span><span class="sxs-lookup"><span data-stu-id="6c356-141">The descriptions for some of the terms in the preceding example are as follows:</span></span>  
  
-   <span data-ttu-id="6c356-142">**Expression de test.**</span><span class="sxs-lookup"><span data-stu-id="6c356-142">**Test Expression.**</span></span> <span data-ttu-id="6c356-143">expression simple (unaire ou binaire) au sein d’un règle.</span><span class="sxs-lookup"><span data-stu-id="6c356-143">A simple (unary or binary) expression within a rule.</span></span>  
  
-   <span data-ttu-id="6c356-144">**Valeur de l’opérande de gauche.**</span><span class="sxs-lookup"><span data-stu-id="6c356-144">**Left Operand Value.**</span></span> <span data-ttu-id="6c356-145">valeur du terme situé à gauche d’une expression.</span><span class="sxs-lookup"><span data-stu-id="6c356-145">The value of the term on the left side of an expression.</span></span>  
  
-   <span data-ttu-id="6c356-146">**Valeur de l’opérande de droite.**</span><span class="sxs-lookup"><span data-stu-id="6c356-146">**Right Operand Value.**</span></span> <span data-ttu-id="6c356-147">valeur du terme situé à droite d’une expression.</span><span class="sxs-lookup"><span data-stu-id="6c356-147">The value of the term on the right side of an expression.</span></span>  
  
-   <span data-ttu-id="6c356-148">**Résultat de test.**</span><span class="sxs-lookup"><span data-stu-id="6c356-148">**Test Result.**</span></span> <span data-ttu-id="6c356-149">résultat de l’évaluation, True ou False.</span><span class="sxs-lookup"><span data-stu-id="6c356-149">The result of the evaluation, which is either True or False.</span></span>  
  
## <a name="agenda-update"></a><span data-ttu-id="6c356-150">Mise à jour de l'agenda</span><span class="sxs-lookup"><span data-stu-id="6c356-150">Agenda Update</span></span>  
 <span data-ttu-id="6c356-151">Cette activité indique les règles qui sont ajoutées à l’agenda du moteur de règles pour être exécutées ultérieurement.</span><span class="sxs-lookup"><span data-stu-id="6c356-151">This activity indicates rules that are added to the rule engine agenda for subsequent execution.</span></span> <span data-ttu-id="6c356-152">L’exemple suivant illustre une entrée de mise à jour d’agenda :</span><span class="sxs-lookup"><span data-stu-id="6c356-152">The following is an example of an agenda update entry:</span></span>  
  
```  
AGENDA UPDATE 1/07/2004 5:33:13 PM  
Rule Engine Instance Identifier: f1dd3ff2-b4a8-4fe1-8d46-4d9b3e2502d3  
Ruleset Name: LoanProcessing  
Operation: Add  
Rule Name: Employment Status Rule  
Conflict Resolution Criteria: 0  
```  
  
 <span data-ttu-id="6c356-153">Voici la description de certains des termes de l'exemple précédent :</span><span class="sxs-lookup"><span data-stu-id="6c356-153">The descriptions for some of the terms in the preceding example are as follows:</span></span>  
  
-   <span data-ttu-id="6c356-154">**Opération.**</span><span class="sxs-lookup"><span data-stu-id="6c356-154">**Operation.**</span></span> <span data-ttu-id="6c356-155">des règles peuvent être ajoutées ou supprimées d'un agenda.</span><span class="sxs-lookup"><span data-stu-id="6c356-155">Rules can be added or removed from the agenda.</span></span>  
  
-   <span data-ttu-id="6c356-156">**Nom de la règle.**</span><span class="sxs-lookup"><span data-stu-id="6c356-156">**Rule Name.**</span></span> <span data-ttu-id="6c356-157">nom de la règle qui est ajoutée à l’agenda.</span><span class="sxs-lookup"><span data-stu-id="6c356-157">The name of the rule that is being added to the agenda.</span></span>  
  
-   <span data-ttu-id="6c356-158">**Critères de résolution des conflits.**</span><span class="sxs-lookup"><span data-stu-id="6c356-158">**Conflict Resolution Criteria.**</span></span> <span data-ttu-id="6c356-159">priorité d'une règle, qui détermine l'ordre relatif dans lequel les actions sont exécutées (les actions avec la priorité la plus élevée sont exécutées en premier).</span><span class="sxs-lookup"><span data-stu-id="6c356-159">The priority of a rule, which determines the relative order in which actions are executed (higher-priority actions are executed first).</span></span>  
  
## <a name="rule-fired"></a><span data-ttu-id="6c356-160">Règle déclenchée</span><span class="sxs-lookup"><span data-stu-id="6c356-160">Rule Fired</span></span>  
 <span data-ttu-id="6c356-161">Cette activité indique l’exécution des actions d’une règle.</span><span class="sxs-lookup"><span data-stu-id="6c356-161">This activity indicates the execution of a rule's actions.</span></span> <span data-ttu-id="6c356-162">L’exemple suivant illustre une entrée de règle déclenchée :</span><span class="sxs-lookup"><span data-stu-id="6c356-162">The following is an example of a rule fired entry:</span></span>  
  
```  
RULE FIRED 1/07/2004 5:33:13 PM  
Rule Engine Instance Identifier: f1dd3ff2-b4a8-4fe1-8d46-4d9b3e2502d3  
Ruleset Name: LoanProcessing  
Rule Name: Residency Status Rule  
Conflict Resolution Criteria: 10  
```