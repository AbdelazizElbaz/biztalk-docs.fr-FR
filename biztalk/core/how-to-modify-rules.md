---
title: "Comment modifier les règles | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- business rules, activating
- deactivating business rules
- business rules, priorities
- activating business rules
- business rules, deactivating
- modifying, business rules
- business rules, modifying
ms.assetid: 661b2637-b5d6-4bde-9c42-24cd9e9d241c
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fce3fb78ce67b6c82f2301dfcb4cb2175aee0dde
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-modify-rules"></a><span data-ttu-id="e7069-102">Comment modifier les règles</span><span class="sxs-lookup"><span data-stu-id="e7069-102">How to Modify Rules</span></span>
<span data-ttu-id="e7069-103">La capacité à changer les règles constitue une part importante du paradigme des règles d'entreprise.</span><span class="sxs-lookup"><span data-stu-id="e7069-103">The ability to change rules is an important part of the business rules paradigm.</span></span> <span data-ttu-id="e7069-104">Vous pouvez modifier les règles au sein d’une stratégie de deux manières : soit en créant une nouvelle version de la stratégie, soit en modifiant directement une version non publiée de la stratégie.</span><span class="sxs-lookup"><span data-stu-id="e7069-104">You can modify rules within a policy in two ways: either by creating a new version of the policy, or by directly modifying an unpublished version of the policy.</span></span>  
  
 <span data-ttu-id="e7069-105">Vous pouvez modifier les règles individuellement, ajouter de nouvelles règles ou supprimer les règles existantes.</span><span class="sxs-lookup"><span data-stu-id="e7069-105">You can modify rules individually, add new rules, or delete existing rules.</span></span> <span data-ttu-id="e7069-106">Vous pouvez supprimer les prédicats et les opérateurs logiques d'une condition de règle, supprimer des actions, déplacer les actions vers le haut et vers le bas à l'écran ou déplacer des prédicats et des opérateurs logiques dans une condition.</span><span class="sxs-lookup"><span data-stu-id="e7069-106">You can delete predicates and logical operators from a rule condition, delete actions, move actions up and down in the display, or move predicates and logical operators within a condition.</span></span> <span data-ttu-id="e7069-107">Gardez cependant à l'esprit que l'ordre d'affichage des prédicats et des opérateurs logiques ne détermine pas l'ordre d'évaluation.</span><span class="sxs-lookup"><span data-stu-id="e7069-107">Keep in mind, however, the order in which the predicates and logical operators are displayed does not determine the order of evaluation.</span></span>  
  
 <span data-ttu-id="e7069-108">Vous pouvez désactiver une règle afin qu'elle ne soit pas exécutée lorsque la stratégie l'est, ou réactiver une règle qui a été désactivée.</span><span class="sxs-lookup"><span data-stu-id="e7069-108">You can set a rule to be inactive, so that the rule is not executed when the policy is executed, or you can reactivate a rule that has been deactivated.</span></span>  
  
 <span data-ttu-id="e7069-109">Vous pouvez définir la priorité sur une règle de sorte que ses actions soient exécutées avant ou après les actions des règles d'une priorité différente.</span><span class="sxs-lookup"><span data-stu-id="e7069-109">You can set the priority on a rule so that its actions will be executed before or after the actions of any rule of different priority.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="e7069-110">Si vous devez éteindre votre ordinateur SQL Server, assurez-vous d'enregistrer toutes les versions de vocabulaire ou définitions de vocabulaires qui ne l'auraient pas été et de fermer l'Éditeur des règles d'entreprise afin qu'aucun changement apporté ne soit perdu.</span><span class="sxs-lookup"><span data-stu-id="e7069-110">If you need to stop your SQL Server computer, be sure to save any unsaved vocabulary versions or vocabulary definitions, and close the Business Rule Composer so that no changes are lost.</span></span>  
  
 <span data-ttu-id="e7069-111">Cette rubrique contient les procédures des tâches suivantes :</span><span class="sxs-lookup"><span data-stu-id="e7069-111">This topic contains procedures for the following tasks:</span></span>  
  
-   <span data-ttu-id="e7069-112">Pour changer un argument dans une condition ou une action</span><span class="sxs-lookup"><span data-stu-id="e7069-112">To change an argument in a condition or action</span></span>  
  
-   <span data-ttu-id="e7069-113">Pour déplacer un prédicat dans une condition</span><span class="sxs-lookup"><span data-stu-id="e7069-113">To move a predicate within a condition</span></span>  
  
-   <span data-ttu-id="e7069-114">Pour déplacer un opérateur logique dans une condition</span><span class="sxs-lookup"><span data-stu-id="e7069-114">To move a logical operator within a condition</span></span>  
  
-   <span data-ttu-id="e7069-115">Pour modifier l'ordre des actions dans une règle</span><span class="sxs-lookup"><span data-stu-id="e7069-115">To change the order of actions within a rule</span></span>  
  
-   <span data-ttu-id="e7069-116">Pour supprimer un prédicat, un opérateur logique ou une action</span><span class="sxs-lookup"><span data-stu-id="e7069-116">To delete a predicate, logical operator, or action</span></span>  
  
-   <span data-ttu-id="e7069-117">Pour activer ou désactiver une règle</span><span class="sxs-lookup"><span data-stu-id="e7069-117">To activate or deactivate a rule</span></span>  
  
-   <span data-ttu-id="e7069-118">Pour définir une priorité sur une règle</span><span class="sxs-lookup"><span data-stu-id="e7069-118">To set a priority on a rule</span></span>  
  
### <a name="to-change-an-argument-in-a-condition-or-action"></a><span data-ttu-id="e7069-119">Pour changer un argument dans une condition ou une action</span><span class="sxs-lookup"><span data-stu-id="e7069-119">To change an argument in a condition or action</span></span>  
  
1.  <span data-ttu-id="e7069-120">Dans la fenêtre des faits et des définitions, cliquez sur l'onglet approprié et naviguez jusqu'au terme que vous souhaitez utiliser comme argument.</span><span class="sxs-lookup"><span data-stu-id="e7069-120">In the Facts and Definitions window, click the appropriate tab, and navigate to the term you want to use as an argument.</span></span> <span data-ttu-id="e7069-121">Le terme doit être d'un type attendu par le prédicat ou la fonction.</span><span class="sxs-lookup"><span data-stu-id="e7069-121">The term must be of a type expected by the predicate or function.</span></span>  
  
2.  <span data-ttu-id="e7069-122">Cliquez sur le terme et faites-le glisser sur un argument de prédicat dans une condition ou sur un argument de fonction dans une action.</span><span class="sxs-lookup"><span data-stu-id="e7069-122">Click the term and drag it onto a predicate argument in a condition or a function argument in an action.</span></span>  
  
### <a name="to-move-a-predicate-within-a-condition"></a><span data-ttu-id="e7069-123">Pour déplacer un prédicat dans une condition</span><span class="sxs-lookup"><span data-stu-id="e7069-123">To move a predicate within a condition</span></span>  
  
-   <span data-ttu-id="e7069-124">Cliquez sur le prédicat, puis faites-le glisser vers un autre opérateur logique.</span><span class="sxs-lookup"><span data-stu-id="e7069-124">Click the predicate, and drag it to another logical operator.</span></span>  
  
### <a name="to-move-a-logical-operator-within-a-condition"></a><span data-ttu-id="e7069-125">Pour déplacer un opérateur logique dans une condition</span><span class="sxs-lookup"><span data-stu-id="e7069-125">To move a logical operator within a condition</span></span>  
  
-   <span data-ttu-id="e7069-126">Cliquez sur l’opérateur logique et faites-le glisser sur un autre opérateur logique ou sur **Conditions**.</span><span class="sxs-lookup"><span data-stu-id="e7069-126">Click the logical operator, and drag it onto another logical operator or onto **Conditions**.</span></span>  
  
### <a name="to-change-the-order-of-actions-within-a-rule"></a><span data-ttu-id="e7069-127">Pour modifier l'ordre des actions dans une règle</span><span class="sxs-lookup"><span data-stu-id="e7069-127">To change the order of actions within a rule</span></span>  
  
-   <span data-ttu-id="e7069-128">Cliquez sur l’action, puis **monter action** ou **descendre l’action**.</span><span class="sxs-lookup"><span data-stu-id="e7069-128">Click the action and then click **Move action up** or **Move action down**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e7069-129">Les actions de chaque règle seront exécutées dans l'ordre indiqué, à l'exception des fonctions de contrôle du moteur, dont l'exécution s'effectue après celle des autres actions.</span><span class="sxs-lookup"><span data-stu-id="e7069-129">The actions of a rule will be executed in the order specified with the exception of engine control functions which are executed after the other actions.</span></span>  
  
### <a name="to-delete-a-predicate-logical-operator-or-action"></a><span data-ttu-id="e7069-130">Pour supprimer un prédicat, un opérateur logique ou une action</span><span class="sxs-lookup"><span data-stu-id="e7069-130">To delete a predicate, logical operator, or action</span></span>  
  
-   <span data-ttu-id="e7069-131">Cliquez sur le prédicat, un opérateur logique ou une action, puis cliquez sur **supprimer**.</span><span class="sxs-lookup"><span data-stu-id="e7069-131">Click the predicate, logical operator, or action, and then click **Delete**.</span></span>  
  
### <a name="to-activate-or-deactivate-a-rule"></a><span data-ttu-id="e7069-132">Pour activer ou désactiver une règle</span><span class="sxs-lookup"><span data-stu-id="e7069-132">To activate or deactivate a rule</span></span>  
  
-   <span data-ttu-id="e7069-133">Cliquez sur la règle et, dans la fenêtre Propriétés, définissez **Active** soit **True** ou **False**.</span><span class="sxs-lookup"><span data-stu-id="e7069-133">Click the rule, and then in the Properties window, set **Active** to either **True** or **False**.</span></span>  
  
### <a name="to-set-a-priority-on-a-rule"></a><span data-ttu-id="e7069-134">Pour définir une priorité sur une règle</span><span class="sxs-lookup"><span data-stu-id="e7069-134">To set a priority on a rule</span></span>  
  
-   <span data-ttu-id="e7069-135">Cliquez sur la règle et, dans la fenêtre Propriétés, définissez **priorité** sur une valeur entière.</span><span class="sxs-lookup"><span data-stu-id="e7069-135">Click the rule, and then in the Properties window, set **Priority** to an integer value.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e7069-136">Les priorités sont relatives et toutes les actions d'une règle d'une priorité donnée seront exécutées dans l'ordre avant les actions d'une règle ayant une valeur de priorité inférieure.</span><span class="sxs-lookup"><span data-stu-id="e7069-136">Priorities are relative, and all of the actions of a rule of a given priority will be executed in order before any of the actions of a rule with a lower value for priority.</span></span> <span data-ttu-id="e7069-137">Par défaut, la valeur de priorité est égale à zéro, mais elle peut aussi être positive ou négative.</span><span class="sxs-lookup"><span data-stu-id="e7069-137">The priority value defaults to zero, but it can be positive or negative.</span></span>