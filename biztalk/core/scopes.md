---
title: "Étendues | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- scopes, exception handling
- Scope shape [Orchestration Designer], nesting
- scopes, variables
- scopes, Scope shape [Orchestration Designer]
- Scope shape [Orchestration Designer], exception handling
- scopes, transactions
- scopes, synchronization
- scopes, nesting
- Scope shape [Orchestration Designer], transactions
ms.assetid: 51d81ce4-0034-4415-b6ab-4c952737c1bd
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2bc4d1b5d926540477293591ade8123126be1b84
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="scopes"></a><span data-ttu-id="a8d7a-102">Étendues</span><span class="sxs-lookup"><span data-stu-id="a8d7a-102">Scopes</span></span>
<span data-ttu-id="a8d7a-103">Une étendue est une structure de regroupement des actions.</span><span class="sxs-lookup"><span data-stu-id="a8d7a-103">A scope is a framework for grouping actions.</span></span> <span data-ttu-id="a8d7a-104">Elle est utilisée principalement pour l'exécution transactionnelle et la gestion des exceptions.</span><span class="sxs-lookup"><span data-stu-id="a8d7a-104">It is primarily used for transactional execution and exception handling.</span></span>  
  
 <span data-ttu-id="a8d7a-105">Une étendue contient un ou plusieurs blocs.</span><span class="sxs-lookup"><span data-stu-id="a8d7a-105">A scope contains one or more blocks.</span></span> <span data-ttu-id="a8d7a-106">Elle se compose d'un corps et peut se voir éventuellement associée à un certain nombre de blocs de gestion d'exception.</span><span class="sxs-lookup"><span data-stu-id="a8d7a-106">It has a body and can optionally have appended to it any number of exception-handling blocks.</span></span> <span data-ttu-id="a8d7a-107">Elle peut également comporter un bloc de compensation facultatif, en fonction de sa nature.</span><span class="sxs-lookup"><span data-stu-id="a8d7a-107">It may have an optional compensation block as well, depending on the nature of the scope.</span></span> <span data-ttu-id="a8d7a-108">Certaines étendues, entièrement destinées à la gestion d'exception, ne requièrent pas de compensation.</span><span class="sxs-lookup"><span data-stu-id="a8d7a-108">Some scopes will be purely for exception handling, and will not require compensation.</span></span> <span data-ttu-id="a8d7a-109">D'autres, explicitement transactionnelles, comportent toujours un gestionnaire de compensation par défaut, ainsi qu'un gestionnaire de compensation facultatif créé par vos soins.</span><span class="sxs-lookup"><span data-stu-id="a8d7a-109">Other scopes will be explicitly transactional, and will always have a default compensation handler, along with an optional compensation handler that you create for it.</span></span> <span data-ttu-id="a8d7a-110">Une étendue transactionnelle dispose, enfin, d'un gestionnaire d'exception par défaut, et d'un certain nombre de gestionnaires d'exception supplémentaires que vous aurez créés.</span><span class="sxs-lookup"><span data-stu-id="a8d7a-110">A transactional scope will also have a default exception handler and any number of additional exception handlers that you create for it.</span></span>  
  
## <a name="synchronized-scopes"></a><span data-ttu-id="a8d7a-111">Étendues synchronisées</span><span class="sxs-lookup"><span data-stu-id="a8d7a-111">Synchronized scopes</span></span>  
 <span data-ttu-id="a8d7a-112">Les étendues peuvent être ou non synchronisées.</span><span class="sxs-lookup"><span data-stu-id="a8d7a-112">You can specify that scopes are synchronized or not synchronized.</span></span> <span data-ttu-id="a8d7a-113">La synchronisation d'une étendue permet de garantir que, lorsqu'un processus accède aux données partagées qu'elle contient, aucune des actions parallèles de votre orchestration ne peut y accéder en écriture. De même, aucun accès en écriture n'est possible lorsqu'une autre action y accède en lecture.</span><span class="sxs-lookup"><span data-stu-id="a8d7a-113">By synchronizing a scope, you ensure that any shared data that is accessed within it will not be written to by one or more parallel actions in your orchestration, nor will it be written to while another action is reading it.</span></span>  
  
 <span data-ttu-id="a8d7a-114">Les étendues de transaction atomique sont toujours synchronisées.</span><span class="sxs-lookup"><span data-stu-id="a8d7a-114">Atomic transaction scopes are always synchronized.</span></span> <span data-ttu-id="a8d7a-115">Toutes les actions au sein d'une étendue synchronisée sont considérées comme synchronisées, tout comme les actions de ses gestionnaires d'exception.</span><span class="sxs-lookup"><span data-stu-id="a8d7a-115">All actions within a synchronized scope are considered synchronized, as are all actions in any of its exception handlers.</span></span> <span data-ttu-id="a8d7a-116">Les actions du gestionnaire de compensation d'une étendue transactionnelle, quant à elles, ne sont pas synchronisées.</span><span class="sxs-lookup"><span data-stu-id="a8d7a-116">Actions in the compensation handler for a transactional scope are not synchronized.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="a8d7a-117">Notez que vous pouvez rencontrer une situation de blocage si vos processus ne sont pas correctement conçus.</span><span class="sxs-lookup"><span data-stu-id="a8d7a-117">Note that you can still run into a deadlock condition if you do not design your processes carefully.</span></span> <span data-ttu-id="a8d7a-118">Par exemple, deux branches d'une action parallèle dans une orchestration A accèdent au même message, la première pour l'envoyer, la seconde pour le recevoir. Leur étendue doit donc être synchronisée.</span><span class="sxs-lookup"><span data-stu-id="a8d7a-118">For example: two branches of a parallel in orchestration A access the same message, one to send it and one to receive it, so both must have a synchronized scope.</span></span> <span data-ttu-id="a8d7a-119">Une deuxième orchestration reçoit le message et le renvoie.</span><span class="sxs-lookup"><span data-stu-id="a8d7a-119">A second orchestration receives the message and sends it back.</span></span> <span data-ttu-id="a8d7a-120">Il est possible que la branche chargée de l'envoi dans l'orchestration A reçoive ses verrous avant la branche de réception, aboutissant à une situation de blocage.</span><span class="sxs-lookup"><span data-stu-id="a8d7a-120">It is possible that the sending branch in orchestration A will receive its locks before the receiving branch, and you will end up with a deadlock.</span></span>  
  
## <a name="nesting-of-scopes"></a><span data-ttu-id="a8d7a-121">Imbrication d'étendues</span><span class="sxs-lookup"><span data-stu-id="a8d7a-121">Nesting of scopes</span></span>  
 <span data-ttu-id="a8d7a-122">Vous pouvez imbriquer des **étendue** formes dans les autres **étendue** formes.</span><span class="sxs-lookup"><span data-stu-id="a8d7a-122">You can nest **Scope** shapes inside other **Scope** shapes.</span></span> <span data-ttu-id="a8d7a-123">Les règles d'imbrication sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="a8d7a-123">The rules for nesting scopes are as follows:</span></span>  
  
-   <span data-ttu-id="a8d7a-124">Il n'est pas possible d'imbriquer des étendues transactionnelles et/ou synchronisées dans des étendues synchronisées, y compris les gestionnaires d'exception des étendues synchronisées.</span><span class="sxs-lookup"><span data-stu-id="a8d7a-124">Transactional and/or synchronized scopes cannot be nested inside synchronized scopes, including the exception handlers of synchronized scopes.</span></span>  
  
-   <span data-ttu-id="a8d7a-125">Aucune étendue transactionnelle ne peut être imbriquée dans une étendue de transaction atomique.</span><span class="sxs-lookup"><span data-stu-id="a8d7a-125">Atomic transaction scopes cannot have any other transactional scopes nested inside them.</span></span>  
  
-   <span data-ttu-id="a8d7a-126">Aucune étendue transactionnelle ne peut être imbriquée dans une orchestration ou une étendue non transactionnelle.</span><span class="sxs-lookup"><span data-stu-id="a8d7a-126">Transactional scopes cannot be nested inside nontransactional scopes or orchestrations.</span></span>  
  
-   <span data-ttu-id="a8d7a-127">L'imbrication peut atteindre une profondeur maximale de 21 niveaux.</span><span class="sxs-lookup"><span data-stu-id="a8d7a-127">You can nest scopes up to 21 levels deep.</span></span>  
  
-   <span data-ttu-id="a8d7a-128">**Appeler Orchestration** formes peuvent être inclus dans les étendues, mais les orchestrations appelées sont traitées le même que toute autre instruction transaction imbriquée, et les mêmes règles s’appliquent.</span><span class="sxs-lookup"><span data-stu-id="a8d7a-128">**Call Orchestration** shapes can be included inside scopes, but the called orchestrations are treated the same as any other nested transaction, and the same rules apply.</span></span>  
  
-   <span data-ttu-id="a8d7a-129">**Démarrer l’Orchestration** formes peuvent être inclus dans les étendues.</span><span class="sxs-lookup"><span data-stu-id="a8d7a-129">**Start Orchestration** shapes can be included inside scopes.</span></span> <span data-ttu-id="a8d7a-130">Les orchestrations démarrées ne sont concernées par aucune des limitations d'imbrication.</span><span class="sxs-lookup"><span data-stu-id="a8d7a-130">Nesting limitations do not apply to started orchestrations.</span></span>  
  
## <a name="scope-variables"></a><span data-ttu-id="a8d7a-131">Variables de l'étendue</span><span class="sxs-lookup"><span data-stu-id="a8d7a-131">Scope variables</span></span>  
 <span data-ttu-id="a8d7a-132">Vous pouvez déclarer des variables, telles que des messages et des ensembles de corrélations, au niveau de l'étendue.</span><span class="sxs-lookup"><span data-stu-id="a8d7a-132">You can declare variables such as messages and correlation sets at the scope level.</span></span> <span data-ttu-id="a8d7a-133">Une variable d'étendue et une variable d'orchestration ne peuvent toutefois pas porter le même nom. Le masquage de nom n'est pas autorisé.</span><span class="sxs-lookup"><span data-stu-id="a8d7a-133">You cannot use the same name for a scope variable as for an orchestration variable, however; name hiding is not allowed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8d7a-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a8d7a-134">See Also</span></span>  
 <span data-ttu-id="a8d7a-135">[L’utilisation de Transactions et la gestion des Exceptions](../core/using-transactions-and-handling-exceptions.md) </span><span class="sxs-lookup"><span data-stu-id="a8d7a-135">[Using Transactions and Handling Exceptions](../core/using-transactions-and-handling-exceptions.md) </span></span>  
 [<span data-ttu-id="a8d7a-136">Transactions atomiques</span><span class="sxs-lookup"><span data-stu-id="a8d7a-136">Atomic Transactions</span></span>](../core/atomic-transactions.md)