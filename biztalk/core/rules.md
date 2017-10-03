---
title: "Règles | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- business rules, actions
- Business Rules Engine, business rules
- business rules, about business rules
- business rules, conditions
- business rules, facts
- business rules
ms.assetid: b288dd07-33f1-42fe-bbfb-02674ef3b3ca
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 35f398cf98181d17833be79fbe9d282e8515e052
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="rules"></a><span data-ttu-id="e5e1e-102">Règles</span><span class="sxs-lookup"><span data-stu-id="e5e1e-102">Rules</span></span>
<span data-ttu-id="e5e1e-103">Les règles d'entreprise sont des instructions déclaratives qui régissent le fonctionnement des processus d'entreprise.</span><span class="sxs-lookup"><span data-stu-id="e5e1e-103">Business rules are declarative statements that govern the conduct of business processes.</span></span> <span data-ttu-id="e5e1e-104">Une règle se compose d'une condition et d'actions.</span><span class="sxs-lookup"><span data-stu-id="e5e1e-104">A rule consists of a condition and actions.</span></span> <span data-ttu-id="e5e1e-105">La condition est évaluée, et si elle a la valeur **true**, le moteur de règles initie une ou plusieurs actions.</span><span class="sxs-lookup"><span data-stu-id="e5e1e-105">The condition is evaluated, and if it evaluates to **true**, the rule engine initiates one or more actions.</span></span>  
  
 <span data-ttu-id="e5e1e-106">Dans l'infrastructure des règles d'entreprise, les règles sont définies selon le format suivant :</span><span class="sxs-lookup"><span data-stu-id="e5e1e-106">Rules in the Business Rules Framework are defined by using the following format:</span></span>  
  
 <span data-ttu-id="e5e1e-107">IF`condition` PUIS`action`</span><span class="sxs-lookup"><span data-stu-id="e5e1e-107">IF`condition` THEN`action`</span></span>  
  
 <span data-ttu-id="e5e1e-108">Prenons l'exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="e5e1e-108">Consider the following example:</span></span>  
  
 <span data-ttu-id="e5e1e-109">IF le montant est inférieur ou égal aux fonds disponibles</span><span class="sxs-lookup"><span data-stu-id="e5e1e-109">IF amount is less than or equal to available funds</span></span>  
  
 <span data-ttu-id="e5e1e-110">THEN exécute la transaction et imprime un reçu</span><span class="sxs-lookup"><span data-stu-id="e5e1e-110">THEN conduct transaction and print receipt</span></span>  
  
 <span data-ttu-id="e5e1e-111">Cette règle détermine si une transaction sera réalisée en appliquant la logique d'entreprise (comparaison de deux valeurs monétaires) à des données ou des faits (montant de transaction et fonds disponibles).</span><span class="sxs-lookup"><span data-stu-id="e5e1e-111">This rule determines whether a transaction will be conducted by applying business logic, in the form of a comparison of two monetary values, to data or facts, in the form of a transaction amount and available funds.</span></span>  
  
 <span data-ttu-id="e5e1e-112">Vous pouvez utiliser l'Éditeur des règles d'entreprise pour créer, modifier, déployer et définir la version des règles d'entreprise.</span><span class="sxs-lookup"><span data-stu-id="e5e1e-112">You can use the Business Rule Composer to create, modify, version, and deploy business rules.</span></span> <span data-ttu-id="e5e1e-113">Vous pouvez également effectuer ces tâches à l'aide d'un programme.</span><span class="sxs-lookup"><span data-stu-id="e5e1e-113">Alternatively, you can perform the preceding tasks programmatically.</span></span>  
  
## <a name="conditions"></a><span data-ttu-id="e5e1e-114">Conditions</span><span class="sxs-lookup"><span data-stu-id="e5e1e-114">Conditions</span></span>  
 <span data-ttu-id="e5e1e-115">Une condition est une expression de type vrai/faux (booléenne) composée d'un ou plusieurs prédicats qui sont appliqués à des faits.</span><span class="sxs-lookup"><span data-stu-id="e5e1e-115">A condition is a true/false (Boolean) expression that consists of one or more predicates that are applied to facts.</span></span>  
  
 <span data-ttu-id="e5e1e-116">Dans notre exemple, le prédicat **inférieure ou égale à** est appliqué aux faits **quantité** et **fonds disponibles**.</span><span class="sxs-lookup"><span data-stu-id="e5e1e-116">In our example, the predicate **less than or equal to** is applied to the facts **amount** and **available funds**.</span></span> <span data-ttu-id="e5e1e-117">Cette condition sera toujours la valeur **true** ou **false**.</span><span class="sxs-lookup"><span data-stu-id="e5e1e-117">This condition will always evaluate to either **true** or **false**.</span></span>  
  
 <span data-ttu-id="e5e1e-118">Les prédicats peuvent être combinées avec les opérateurs logiques **AND**, **ou**, et **pas** pour former une expression logique potentiellement volumineuse, mais sera toujours évaluée en soit **true** ou **false**.</span><span class="sxs-lookup"><span data-stu-id="e5e1e-118">Predicates can be combined with the logical operators **AND**, **OR**, and **NOT** to form a logical expression that is potentially quite large, but will always evaluate to either **true** or **false**.</span></span>  
  
## <a name="actions"></a><span data-ttu-id="e5e1e-119">Actions</span><span class="sxs-lookup"><span data-stu-id="e5e1e-119">Actions</span></span>  
 <span data-ttu-id="e5e1e-120">Les actions sont les conséquences fonctionnelles de l'évaluation des conditions.</span><span class="sxs-lookup"><span data-stu-id="e5e1e-120">Actions are the functional consequences of condition evaluation.</span></span> <span data-ttu-id="e5e1e-121">Si une condition de règle est satisfaite, une ou plusieurs actions correspondantes sont exécutées.</span><span class="sxs-lookup"><span data-stu-id="e5e1e-121">If a rule condition is met, a corresponding action or actions are initiated.</span></span>  
  
 <span data-ttu-id="e5e1e-122">Dans notre exemple, « exécuter la transaction » et « imprimer un reçu » sont les actions exécutées si et seulement si la condition (« IF le montant est inférieur ou égal aux fonds disponibles ») a la valeur vrai.</span><span class="sxs-lookup"><span data-stu-id="e5e1e-122">In our example, "conduct transaction" and "print receipt" are actions that are carried out when, and only when, the condition (in this case, "IF amount is less than or equal to available funds") is true.</span></span>  
  
 <span data-ttu-id="e5e1e-123">Les actions sont représentées dans l'infrastructure des règles d'entreprise en appelant des méthodes ou en définissant des propriétés pour des objets, ou en exécutant des opérations de définition sur des documents XML ou des tables de base de données.</span><span class="sxs-lookup"><span data-stu-id="e5e1e-123">Actions are represented in the Business Rules Framework by invoking methods or setting properties on objects, or by performing set operations on XML documents or database tables.</span></span>  
  
## <a name="facts"></a><span data-ttu-id="e5e1e-124">Faits</span><span class="sxs-lookup"><span data-stu-id="e5e1e-124">Facts</span></span>  
 <span data-ttu-id="e5e1e-125">Les faits sont les données auxquelles les règles s'appliquent.</span><span class="sxs-lookup"><span data-stu-id="e5e1e-125">Facts are the data upon which rules operate.</span></span> <span data-ttu-id="e5e1e-126">Dans notre exemple, les faits sont « montant » et « fonds disponibles ».</span><span class="sxs-lookup"><span data-stu-id="e5e1e-126">In our example, "amount" and "available funds" are facts.</span></span> <span data-ttu-id="e5e1e-127">Pour plus d’informations, consultez [faits](../core/facts.md).</span><span class="sxs-lookup"><span data-stu-id="e5e1e-127">For more information, see [Facts](../core/facts.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5e1e-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e5e1e-128">See Also</span></span>  
 [<span data-ttu-id="e5e1e-129">Comment créer des règles et stratégies</span><span class="sxs-lookup"><span data-stu-id="e5e1e-129">How to Create Policies and Rules</span></span>](../core/how-to-create-policies-and-rules.md)