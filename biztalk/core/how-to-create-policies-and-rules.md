---
title: "Comment créer des règles et stratégies | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- creating, business rules
- policies, rules
- policies, predicates
- business rules, creating
- creating, policies
- policies, logical operators
- policies, examples
- policies, default actions
- policies
- policies, arguments
- policies, creating
ms.assetid: 59f06a67-edde-443b-9fbb-55ec4429837a
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 52fb3d835b39a4059fc7a4a1644d7653257ea3dc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-create-policies-and-rules"></a><span data-ttu-id="2dbf3-102">Création de stratégies et de règles</span><span class="sxs-lookup"><span data-stu-id="2dbf3-102">How to Create Policies and Rules</span></span>
<span data-ttu-id="2dbf3-103">Vous pouvez créer des règles avec des conditions qui sont des groupements logiques d’opérateurs logiques (**AND**, **OR**, et **pas**) appliqué aux prédicats (intégrées ou définis par l’utilisateur des fonctions ou opérateurs) qui acceptent des arguments (références de faits intégrées ou définies par l’utilisateur).</span><span class="sxs-lookup"><span data-stu-id="2dbf3-103">You can create rules with conditions that are logical groupings of logical operators (**AND**, **OR**, and **NOT**) applied to predicates (built-in or user-defined functions or operators) that take arguments (built-in or user-defined fact references).</span></span> <span data-ttu-id="2dbf3-104">Vous pouvez également cliquer sur **Conditions** ou opérateurs logiques et sélectionnez un opérateur logique ou un prédicat intégré dans le menu contextuel.</span><span class="sxs-lookup"><span data-stu-id="2dbf3-104">You can also right-click **Conditions** or logical operators and select a logical operator or built-in predicate from the context menu.</span></span>  
  
 <span data-ttu-id="2dbf3-105">Vous pouvez définir les actions (fonctions intégrées ou définies par l’utilisateur) à exécuter si la condition de règle a la valeur **true**.</span><span class="sxs-lookup"><span data-stu-id="2dbf3-105">You can define actions (built-in or user-defined functions) to be executed if the rule condition evaluates to **true**.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2dbf3-106">Si vous incluez plusieurs prédicats dans une règle, ils doivent tous apparaître en tant qu'arguments d'un opérateur logique</span><span class="sxs-lookup"><span data-stu-id="2dbf3-106">If you include more than one predicate in a rule, all predicates must appear as arguments to a logical operator.</span></span> <span data-ttu-id="2dbf3-107">(Le niveau supérieur peut être un membre .NET unique, une colonne de base de données ou un champ/attribut XML qui est de type booléen).</span><span class="sxs-lookup"><span data-stu-id="2dbf3-107">(The top level can be a single .NET member, db column, or XML field/attribute that is of boolean type.)</span></span>  
  
### <a name="to-create-a-policy"></a><span data-ttu-id="2dbf3-108">Pour créer une stratégie</span><span class="sxs-lookup"><span data-stu-id="2dbf3-108">To create a policy</span></span>  
  
1.  <span data-ttu-id="2dbf3-109">Dans le volet Explorateur de stratégies, cliquez sur **stratégies**, puis cliquez sur **ajouter une nouvelle stratégie**.</span><span class="sxs-lookup"><span data-stu-id="2dbf3-109">In the Policy Explorer pane, right-click **Policies**, and then click **Add New Policy**.</span></span>  
  
     <span data-ttu-id="2dbf3-110">Un nouveau dossier, **Policy1**, est créé sous **stratégies**.</span><span class="sxs-lookup"><span data-stu-id="2dbf3-110">A new folder, **Policy1**, is created under **Policies**.</span></span> <span data-ttu-id="2dbf3-111">Par défaut, la version 1 d'une nouvelle stratégie est créée pour vous.</span><span class="sxs-lookup"><span data-stu-id="2dbf3-111">By default, version 1 of a new policy is created for you.</span></span>  
  
2.  <span data-ttu-id="2dbf3-112">Cliquez sur **Policy1**.</span><span class="sxs-lookup"><span data-stu-id="2dbf3-112">Click **Policy1**.</span></span>  
  
3.  <span data-ttu-id="2dbf3-113">Tapez un nom dans le volet de propriétés Nom.</span><span class="sxs-lookup"><span data-stu-id="2dbf3-113">In the Name property pane, type a name.</span></span>  
  
### <a name="to-add-a-rule-to-a-policy-version"></a><span data-ttu-id="2dbf3-114">Pour ajouter une règle à une version de stratégie</span><span class="sxs-lookup"><span data-stu-id="2dbf3-114">To add a rule to a policy version</span></span>  
  
-   <span data-ttu-id="2dbf3-115">Dans le volet Explorateur de stratégies, développez [**votre stratégie**], avec le bouton droit **Version 1.0 (non enregistrée)**, puis sélectionnez **ajouter une nouvelle règle**.</span><span class="sxs-lookup"><span data-stu-id="2dbf3-115">In the Policy Explorer pane, expand [**your policy**], right-click **Version 1.0 (not saved)**, and then select **Add New Rule**.</span></span>  
  
### <a name="to-add-a-logical-operator-to-a-rule-condition"></a><span data-ttu-id="2dbf3-116">Pour ajouter un opérateur logique à une condition de règle</span><span class="sxs-lookup"><span data-stu-id="2dbf3-116">To add a logical operator to a rule condition</span></span>  
  
-   <span data-ttu-id="2dbf3-117">Dans la fenêtre de définition de règle, cliquez sur **Conditions**, puis cliquez sur un des **ajouter le AND logique**, **ajouter le OR logique**, ou **ajouter le NOT logique**.</span><span class="sxs-lookup"><span data-stu-id="2dbf3-117">In the Rule Definition window, right-click **Conditions**, and then click one of **Add Logical AND**, **Add Logical OR**, or **Add Logical NOT**.</span></span>  
  
### <a name="to-add-a-built-in-predicate-to-a-rule-condition-or-logical-operator"></a><span data-ttu-id="2dbf3-118">Pour ajouter un prédicat intégré à une condition de règle ou un opérateur logique</span><span class="sxs-lookup"><span data-stu-id="2dbf3-118">To add a built-in predicate to a rule condition or logical operator</span></span>  
  
1.  <span data-ttu-id="2dbf3-119">Dans la fenêtre Explorateur de faits, cliquez sur le **vocabulaires** onglet, puis cliquez sur le **prédicats** dossier.</span><span class="sxs-lookup"><span data-stu-id="2dbf3-119">In the Facts Explorer window, click the **Vocabularies** tab, and then click the **Predicates** folder.</span></span>  
  
2.  <span data-ttu-id="2dbf3-120">Développez une version publiée d'un vocabulaire de prédicat, puis cliquez sur le prédicat voulu.</span><span class="sxs-lookup"><span data-stu-id="2dbf3-120">Expand a published version of a predicate vocabulary, and click the predicate you want.</span></span>  
  
3.  <span data-ttu-id="2dbf3-121">Faites glisser le prédicat sur l’opérateur logique, ou sur **Conditions** si votre règle doit contenir qu’un seul prédicat.</span><span class="sxs-lookup"><span data-stu-id="2dbf3-121">Drag the predicate onto the logical operator, or onto **Conditions** if your rule will contain only one predicate.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="2dbf3-122">Vous pouvez également ajouter un prédicat directement à partir d’une source de données, si l’élément de données agit en tant que prédicat (prend la valeur de **true** ou **false**).</span><span class="sxs-lookup"><span data-stu-id="2dbf3-122">You can also add a predicate directly from a data source, provided that the data element acts as a predicate (evaluates to **true** or **false**).</span></span>  
  
### <a name="to-add-a-built-in-action-to-a-rule"></a><span data-ttu-id="2dbf3-123">Pour ajouter une action intégrée à une règle</span><span class="sxs-lookup"><span data-stu-id="2dbf3-123">To add a built-in action to a rule</span></span>  
  
1.  <span data-ttu-id="2dbf3-124">Dans la fenêtre Explorateur de faits, cliquez sur le **vocabulaires** onglet, puis cliquez sur le **fonctions** dossier.</span><span class="sxs-lookup"><span data-stu-id="2dbf3-124">In the Facts Explorer window, click the **Vocabularies** tab, and then click the **Functions** folder.</span></span>  
  
2.  <span data-ttu-id="2dbf3-125">Développez une version publiée du vocabulaire de fonction, puis cliquez sur la fonction voulue.</span><span class="sxs-lookup"><span data-stu-id="2dbf3-125">Expand a published version of the function vocabulary, and click the function you want.</span></span>  
  
3.  <span data-ttu-id="2dbf3-126">Faites glisser la fonction sur **Actions**.</span><span class="sxs-lookup"><span data-stu-id="2dbf3-126">Drag the function onto **Actions**.</span></span> <span data-ttu-id="2dbf3-127">Vous pouvez également cliquer sur **Actions**, puis sélectionnez une action intégrée dans le menu contextuel.</span><span class="sxs-lookup"><span data-stu-id="2dbf3-127">You can also right-click **Actions**, and select a built-in action from the context menu.</span></span>  
  
### <a name="to-add-an-argument-to-a-condition-or-action"></a><span data-ttu-id="2dbf3-128">Pour ajouter un argument à une condition ou une action</span><span class="sxs-lookup"><span data-stu-id="2dbf3-128">To add an argument to a condition or action</span></span>  
  
1.  <span data-ttu-id="2dbf3-129">Dans la fenêtre Explorateur de faits, cliquez sur le **vocabulaires** onglet, puis cliquez sur un dossier de vocabulaire.</span><span class="sxs-lookup"><span data-stu-id="2dbf3-129">In the Facts Explorer window, click the **Vocabularies** tab, and then click a vocabulary folder.</span></span>  
  
2.  <span data-ttu-id="2dbf3-130">Développez une version publiée du vocabulaire, puis cliquez sur le terme voulu.</span><span class="sxs-lookup"><span data-stu-id="2dbf3-130">Expand a published version of the vocabulary, and click the term you want.</span></span> <span data-ttu-id="2dbf3-131">Le terme doit être d'un type attendu par le prédicat ou la fonction.</span><span class="sxs-lookup"><span data-stu-id="2dbf3-131">The term must be of a type expected by the predicate or function.</span></span>  
  
3.  <span data-ttu-id="2dbf3-132">Faites glisser le terme sur un argument de prédicat dans une condition, ou sur un argument de fonction dans une action.</span><span class="sxs-lookup"><span data-stu-id="2dbf3-132">Drag the term onto a predicate argument in a condition or a function argument in an action.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="2dbf3-133">Vous pouvez aussi ajouter un argument directement à partir d'une source de données ou, dans le cas d'XML, spécifier le type de fichier dans les propriétés lorsque vous sélectionnez un champ. Cela doit bien sûr être compatible avec les données elles-mêmes et l'élément de données doit être d'un type attendu par le prédicat ou l'action.</span><span class="sxs-lookup"><span data-stu-id="2dbf3-133">You can also add an argument directly from a data source or in the case of XML you can specify the field type in the properties when selecting a field; this must of course be compatible with the data itself , provided that the data element is of a type expected by the predicate or action.</span></span> <span data-ttu-id="2dbf3-134">Pour ajouter un argument directement à partir d'une source de données, cliquez sur l'onglet approprié de la fenêtre Explorateur de faits, accédez à l'élément souhaité, puis faites-le glisser sur un argument de prédicat ou un argument de fonction.</span><span class="sxs-lookup"><span data-stu-id="2dbf3-134">To add an argument directly from a data source, click the appropriate tab in the Facts Explorer window, navigate to the item you want, and drag it onto a predicate argument or function argument.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="2dbf3-135">Vous pouvez ajouter une valeur constante à un argument directement en cliquant sur ce dernier, puis en entrant la valeur constante désirée.</span><span class="sxs-lookup"><span data-stu-id="2dbf3-135">You can add a constant value to an argument directly by clicking the argument and entering the constant value you want.</span></span>