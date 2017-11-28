---
title: "Agenda et priorité | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- business rules, executing
- Business Rules Engine, agendas
- Business Rules Engine, priorities
- business rules, priorities
- business rules, examples
- Business Rules Engine, examples
- examples, Business Rules Engine
- Business Rules Engine, rules
ms.assetid: ca54f750-4f2d-4734-8e6e-7af1b4967e6a
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4529753251c2bf7934616b91662bde836c8339e1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="agenda-and-priority"></a><span data-ttu-id="379cb-102">Agenda et priorité</span><span class="sxs-lookup"><span data-stu-id="379cb-102">Agenda and Priority</span></span>
<span data-ttu-id="379cb-103">Pour comprendre comment le moteur de règles d’entreprise évalue les règles et exécute les actions, vous devez comprendre les concepts de *agenda* et *priorité*.</span><span class="sxs-lookup"><span data-stu-id="379cb-103">To understand how the Business Rule engine evaluates rules and executes actions, you need to understand the concepts of *agenda* and *priority*.</span></span>  
  
## <a name="agenda"></a><span data-ttu-id="379cb-104">Agenda</span><span class="sxs-lookup"><span data-stu-id="379cb-104">Agenda</span></span>  
 <span data-ttu-id="379cb-105">L'agenda est une planification dont se sert le moteur pour mettre en file d'attente les règles à exécuter.</span><span class="sxs-lookup"><span data-stu-id="379cb-105">The agenda is a schedule used by the engine to queue rules for execution.</span></span> <span data-ttu-id="379cb-106">L'agenda est lié à une instance de moteur et agit sur une stratégie, pas sur plusieurs.</span><span class="sxs-lookup"><span data-stu-id="379cb-106">The agenda exists for an engine instance, and acts on a single policy, not on a series of policies.</span></span> <span data-ttu-id="379cb-107">Lorsque les conditions d'une règle donnée sont satisfaites et qu'un fait est déclaré en mémoire de travail, la règle est placée sur l'agenda et exécutée selon sa priorité.</span><span class="sxs-lookup"><span data-stu-id="379cb-107">When a fact is asserted into working memory and the conditions of a given rule are satisfied, the rule is placed on the agenda and executed according to priority.</span></span> <span data-ttu-id="379cb-108">Les actions d'une règle sont exécutées dans l'ordre, du haut vers le bas. Les actions de la règle suivante sur l'agenda sont ensuite exécutées.</span><span class="sxs-lookup"><span data-stu-id="379cb-108">A rule's actions are executed in order from top to bottom, and then the actions of the next rule on the agenda are executed.</span></span>  
  
 <span data-ttu-id="379cb-109">Les actions appartenant à une règle sont traitées comme un bloc afin que toutes soient exécutées avant le début de la règle suivante.</span><span class="sxs-lookup"><span data-stu-id="379cb-109">The actions belonging to a rule are treated as a block, so that all actions are executed before moving on to the next rule.</span></span> <span data-ttu-id="379cb-110">Toutes les actions d'un bloc de règle s'exécutent indépendamment les unes des autres.</span><span class="sxs-lookup"><span data-stu-id="379cb-110">All actions in a rule block will execute regardless of other actions in the block.</span></span> <span data-ttu-id="379cb-111">Pour plus d’informations sur les déclarations, consultez [les fonctions de contrôle du moteur](../core/engine-control-functions.md).</span><span class="sxs-lookup"><span data-stu-id="379cb-111">For more information about assertion, see [Engine Control Functions](../core/engine-control-functions.md).</span></span>  
  
 <span data-ttu-id="379cb-112">L'exemple suivant illustre le fonctionnement de l'agenda.</span><span class="sxs-lookup"><span data-stu-id="379cb-112">The following example demonstrates how the agenda works.</span></span>  
  
 <span data-ttu-id="379cb-113">**Règle1**</span><span class="sxs-lookup"><span data-stu-id="379cb-113">**Rule1**</span></span>  
  
```  
IF  
Fact1 == 1  
THEN  
Action1  
Action2  
```  
  
 <span data-ttu-id="379cb-114">**Rule2**</span><span class="sxs-lookup"><span data-stu-id="379cb-114">**Rule2**</span></span>  
  
```  
IF  
Fact1 > 0  
THEN  
Action3  
Action4  
```  
  
 <span data-ttu-id="379cb-115">Nous déclarons le fait Fait1 qui possède la valeur 1 dans le moteur.</span><span class="sxs-lookup"><span data-stu-id="379cb-115">We assert the fact Fact1, which has a value of 1, into the engine.</span></span> <span data-ttu-id="379cb-116">Étant donné que les conditions de Règle 1 et Règle  2 sont satisfaites, ces deux règles sont déplacées dans l'agenda pour que leurs actions puissent être exécutées.</span><span class="sxs-lookup"><span data-stu-id="379cb-116">Because the conditions of both Rule 1 and Rule 2 are satisfied, both rules are moved to the agenda for execution of their actions.</span></span>  
  
|<span data-ttu-id="379cb-117">Mémoire de travail</span><span class="sxs-lookup"><span data-stu-id="379cb-117">Working memory</span></span>|<span data-ttu-id="379cb-118">Agenda</span><span class="sxs-lookup"><span data-stu-id="379cb-118">Agenda</span></span>|  
|--------------------|------------|  
|<span data-ttu-id="379cb-119">Fait1 ( valeur = 1 )</span><span class="sxs-lookup"><span data-stu-id="379cb-119">Fact1 (value=1)</span></span>|<span data-ttu-id="379cb-120">**Règle1**</span><span class="sxs-lookup"><span data-stu-id="379cb-120">**Rule1**</span></span><br /><br /> <span data-ttu-id="379cb-121">-Action1</span><span class="sxs-lookup"><span data-stu-id="379cb-121">-   Action1</span></span><br /><span data-ttu-id="379cb-122">-Action2</span><span class="sxs-lookup"><span data-stu-id="379cb-122">-   Action2</span></span><br /><br /> <span data-ttu-id="379cb-123">**Rule2**</span><span class="sxs-lookup"><span data-stu-id="379cb-123">**Rule2**</span></span><br /><br /> <span data-ttu-id="379cb-124">-Action3</span><span class="sxs-lookup"><span data-stu-id="379cb-124">-   Action3</span></span><br /><span data-ttu-id="379cb-125">-Action4</span><span class="sxs-lookup"><span data-stu-id="379cb-125">-   Action4</span></span>|  
  
## <a name="priority"></a><span data-ttu-id="379cb-126">Priorité</span><span class="sxs-lookup"><span data-stu-id="379cb-126">Priority</span></span>  
 <span data-ttu-id="379cb-127">Une priorité d'exécution est définie pour chaque règle, avec une priorité par défaut de 0 pour toutes.</span><span class="sxs-lookup"><span data-stu-id="379cb-127">Priority for execution is set on each individual rule, with a default priority of 0 for all rules.</span></span> <span data-ttu-id="379cb-128">La priorité peut être positive ou négative ; les nombres les plus élevés correspondent aux priorités les plus importantes.</span><span class="sxs-lookup"><span data-stu-id="379cb-128">The priority can range on either side of 0, with larger numbers having higher priority.</span></span> <span data-ttu-id="379cb-129">Les actions sont exécutées de la priorité la plus élevée à la priorité la plus faible.</span><span class="sxs-lookup"><span data-stu-id="379cb-129">Actions are executed in order from highest priority to lowest priority.</span></span>  
  
 <span data-ttu-id="379cb-130">L'exemple suivant montre l'incidence de la priorité sur l'ordre d'exécution des règles.</span><span class="sxs-lookup"><span data-stu-id="379cb-130">The following example shows how priority affects the order of execution for the rules.</span></span>  
  
 <span data-ttu-id="379cb-131">**Règle1 (priorité = 0)**</span><span class="sxs-lookup"><span data-stu-id="379cb-131">**Rule1 (priority = 0)**</span></span>  
  
```  
IF  
Fact1 == 1  
THEN  
Discount = 10%  
```  
  
 <span data-ttu-id="379cb-132">**Règle2 (priorité = 10)**</span><span class="sxs-lookup"><span data-stu-id="379cb-132">**Rule2 (priority = 10)**</span></span>  
  
```  
IF  
Fact1 > 0  
THEN  
Discount = 15%  
```  
  
 <span data-ttu-id="379cb-133">Les conditions des deux règles sont satisfaites, mais Règle2 est exécutée en premier car elle a la priorité la plus importante.</span><span class="sxs-lookup"><span data-stu-id="379cb-133">The conditions for both rules have been met, but Rule2 is executed first because it has higher priority.</span></span> <span data-ttu-id="379cb-134">La remise finale est de 10 % car il s'agit du résultat de l'action exécutée pour Règle1, comme l'illustre le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="379cb-134">The final discount is 10 percent, because it is the result of the action executed for Rule1, as shown in the following table.</span></span>  
  
|<span data-ttu-id="379cb-135">Mémoire de travail</span><span class="sxs-lookup"><span data-stu-id="379cb-135">Working memory</span></span>|<span data-ttu-id="379cb-136">Agenda</span><span class="sxs-lookup"><span data-stu-id="379cb-136">Agenda</span></span>|  
|--------------------|------------|  
|<span data-ttu-id="379cb-137">Fait1 ( valeur = 1 )</span><span class="sxs-lookup"><span data-stu-id="379cb-137">Fact1 (value=1)</span></span>|<span data-ttu-id="379cb-138">**Rule2**</span><span class="sxs-lookup"><span data-stu-id="379cb-138">**Rule2**</span></span><br /><br /> <span data-ttu-id="379cb-139">Remise = 15 %</span><span class="sxs-lookup"><span data-stu-id="379cb-139">Discount = 15%</span></span><br /><br /> <span data-ttu-id="379cb-140">**Règle1**</span><span class="sxs-lookup"><span data-stu-id="379cb-140">**Rule1**</span></span><br /><br /> <span data-ttu-id="379cb-141">Remise  = 10 %</span><span class="sxs-lookup"><span data-stu-id="379cb-141">Discount = 10%</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="379cb-142">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="379cb-142">See Also</span></span>  
 [<span data-ttu-id="379cb-143">Moteur de règles</span><span class="sxs-lookup"><span data-stu-id="379cb-143">Rule Engine</span></span>](../core/rule-engine.md)