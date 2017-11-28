---
title: "Moteur de règles | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- RuleEngine object
- Business Rules Engine, ruleset executor
- Business Rules Engine, ruleset translator
- Business Rules Engine, ruleset tracking interceptor
- Business Rules Engine, Business Rules Engine
ms.assetid: c4043a1f-357f-47bc-84e1-5e4bd9f8b5b8
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b0dc2d293697ccbb64851591037440d0371c1346
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="rule-engine"></a><span data-ttu-id="887ef-102">Moteur de règles</span><span class="sxs-lookup"><span data-stu-id="887ef-102">Rule Engine</span></span>
<span data-ttu-id="887ef-103">Cette section décrit plusieurs composants, fonctionnalités et fonctionnements du moteur de règles d'entreprise.</span><span class="sxs-lookup"><span data-stu-id="887ef-103">This section describes several components, functionalities, and operations of the Business Rule engine.</span></span> <span data-ttu-id="887ef-104">Le moteur de règles fournit le contexte d'exécution d'un ensemble de règles.</span><span class="sxs-lookup"><span data-stu-id="887ef-104">The rule engine provides the execution context for a rule set.</span></span> <span data-ttu-id="887ef-105">Le **RuleEngine** objet pour l’implémentation utilise les composants plug-in suivants :</span><span class="sxs-lookup"><span data-stu-id="887ef-105">The **RuleEngine** object uses the following plug–in components for implementation:</span></span>  
  
-   <span data-ttu-id="887ef-106">**Exécuteur d’ensemble de règles (moteur d’inférence)**.</span><span class="sxs-lookup"><span data-stu-id="887ef-106">**Ruleset executor (inference engine)**.</span></span> <span data-ttu-id="887ef-107">Implémente l'algorithme responsable de l'évaluation des conditions de règle et de l'exécution des actions.</span><span class="sxs-lookup"><span data-stu-id="887ef-107">Implements the algorithm responsible for rule condition evaluation and action execution.</span></span> <span data-ttu-id="887ef-108">L'exécuteur d'ensemble de règles par défaut est un moteur d'inférence de discrimination en réseau à chaînage avant qui est conçu pour optimiser les opérations en mémoire.</span><span class="sxs-lookup"><span data-stu-id="887ef-108">The default rule set executor is a discrimination network-based forward-chaining inference engine designed to optimize in-memory operation.</span></span>  
  
-   <span data-ttu-id="887ef-109">**Convertisseur d’ensemble de règles**.</span><span class="sxs-lookup"><span data-stu-id="887ef-109">**Ruleset translator**.</span></span> <span data-ttu-id="887ef-110">Prend comme entrée un **RuleSet** de l’objet et produit une représentation exécutable de l’ensemble de règles.</span><span class="sxs-lookup"><span data-stu-id="887ef-110">Takes as input a **RuleSet** object and produces an executable representation of the rule set.</span></span> <span data-ttu-id="887ef-111">Le convertisseur en mémoire par défaut crée un réseau de discrimination compilé à partir de la définition de l'ensemble de règles.</span><span class="sxs-lookup"><span data-stu-id="887ef-111">The default in-memory translator creates a compiled discrimination network from the rule set definition.</span></span>  
  
-   <span data-ttu-id="887ef-112">**L’intercepteur de suivi d’ensemble de règles**.</span><span class="sxs-lookup"><span data-stu-id="887ef-112">**Rule set tracking interceptor**.</span></span> <span data-ttu-id="887ef-113">reçoit le résultat de l'exécuteur de l'ensemble de règles (moteur d'inférence) et le transmet aux outils de suivi et de contrôle de l'ensemble de règles.</span><span class="sxs-lookup"><span data-stu-id="887ef-113">Receives output from the rule set executor (inference engine) and forwards it to rule set tracking and monitoring tools.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="887ef-114">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="887ef-114">In This Section</span></span>  
  
-   [<span data-ttu-id="887ef-115">Évaluation de la condition et exécution d’Action</span><span class="sxs-lookup"><span data-stu-id="887ef-115">Condition Evaluation and Action Execution</span></span>](../core/condition-evaluation-and-action-execution.md)  
  
-   [<span data-ttu-id="887ef-116">Agenda et priorité</span><span class="sxs-lookup"><span data-stu-id="887ef-116">Agenda and Priority</span></span>](../core/agenda-and-priority.md)  
  
-   [<span data-ttu-id="887ef-117">Fonctions de contrôle du moteur</span><span class="sxs-lookup"><span data-stu-id="887ef-117">Engine Control Functions</span></span>](../core/engine-control-functions.md)  
  
-   [<span data-ttu-id="887ef-118">Accès aux données dans le moteur de règles d’entreprise</span><span class="sxs-lookup"><span data-stu-id="887ef-118">Data Access in the Business Rule Engine</span></span>](../core/data-access-in-the-business-rule-engine.md)  
  
-   [<span data-ttu-id="887ef-119">Action de règle effets</span><span class="sxs-lookup"><span data-stu-id="887ef-119">Rule Action Side Effects</span></span>](../core/rule-action-side-effects.md)  
  
-   [<span data-ttu-id="887ef-120">Prise en charge de l’héritage de classes dans le moteur de règles d’entreprise</span><span class="sxs-lookup"><span data-stu-id="887ef-120">Support for Class Inheritance in the Business Rule Engine</span></span>](../core/support-for-class-inheritance-in-the-business-rule-engine.md)  
  
-   [<span data-ttu-id="887ef-121">Paramètres de réglage et de Configuration du moteur de règles</span><span class="sxs-lookup"><span data-stu-id="887ef-121">Rule Engine Configuration and Tuning Parameters</span></span>](../core/rule-engine-configuration-and-tuning-parameters.md)  
  
-   [<span data-ttu-id="887ef-122">Considérations sur les performances lors de l’utilisation du moteur de règles</span><span class="sxs-lookup"><span data-stu-id="887ef-122">Performance Considerations When Using the Rule Engine</span></span>](../core/performance-considerations-when-using-the-rule-engine.md)  
  
## <a name="see-also"></a><span data-ttu-id="887ef-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="887ef-123">See Also</span></span>  
 [<span data-ttu-id="887ef-124">Moteur des règles d’entreprise</span><span class="sxs-lookup"><span data-stu-id="887ef-124">Business Rules Engine</span></span>](../core/business-rules-engine.md)