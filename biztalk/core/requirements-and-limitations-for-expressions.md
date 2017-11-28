---
title: Configuration requise et Limitations pour les Expressions | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Expression Editor, about Expression Editor
- Expression Editor, requirements
- Orchestration Designer, Expression Editor
- Expression Editor, limitations
- Expression Editor
- Expression Editor, Orchestration Designer
ms.assetid: 1e0353d3-c2f3-4c10-86e3-8620e62dd0d5
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fd819850f62d47c640753e843325c9851da177b5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="requirements-and-limitations-for-expressions"></a><span data-ttu-id="ae57a-102">Impératifs et restrictions des expressions</span><span class="sxs-lookup"><span data-stu-id="ae57a-102">Requirements and Limitations for Expressions</span></span>
<span data-ttu-id="ae57a-103">L'Éditeur d'expression BizTalk du Concepteur d'orchestration est un éditeur de texte Visual Studio standard offrant les options IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="ae57a-103">BizTalk Expression Editor in Orchestration Designer is a standard Visual Studio text editor, which means it offers IntelliSense.</span></span> <span data-ttu-id="ae57a-104">Dans l'Éditeur d'expression BizTalk, il est possible d'entrer une expression sous forme textuelle.</span><span class="sxs-lookup"><span data-stu-id="ae57a-104">You use BizTalk Expression Editor to enter an expression in textual form.</span></span>  
  
 <span data-ttu-id="ae57a-105">Utilisez la zone de texte pour entrer une expression unique sous forme textuelle.</span><span class="sxs-lookup"><span data-stu-id="ae57a-105">Use the text box to enter a single expression in textual form.</span></span> <span data-ttu-id="ae57a-106">L'expression peut s'étendre sur plusieurs lignes et doit se terminer par un seul point-virgule.</span><span class="sxs-lookup"><span data-stu-id="ae57a-106">The expression can span multiple lines, but must end with single semicolon.</span></span>  
  
 <span data-ttu-id="ae57a-107">Voici la liste des limitations applicables aux expressions dans l'Éditeur d'expression BizTalk :</span><span class="sxs-lookup"><span data-stu-id="ae57a-107">The following is a list of limitations when using expressions in the BizTalk Expression Editor:</span></span>  
  
-   <span data-ttu-id="ae57a-108">L'assignation composée de la forme « += », « -= » ou « *= » n'est pas prise en charge.</span><span class="sxs-lookup"><span data-stu-id="ae57a-108">Compound assignment such as "+=", "-=", or "*=" is not supported.</span></span>  
  
-   <span data-ttu-id="ae57a-109">L'utilisation de plus d'un opérateur d'assignation dans une instruction n'est pas prise en charge.</span><span class="sxs-lookup"><span data-stu-id="ae57a-109">More than one assignment operator in a statement is not supported.</span></span>  
  
-   <span data-ttu-id="ae57a-110">L'assignation dans un prédicat « if » ou « while » n'est pas prise en charge.</span><span class="sxs-lookup"><span data-stu-id="ae57a-110">Assignment within an “if” or “while” predicate is not supported.</span></span>  
  
-   <span data-ttu-id="ae57a-111">Les opérateurs d'incrémentation et de décrémentation ne sont pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="ae57a-111">Increment and decrement are not supported.</span></span> <span data-ttu-id="ae57a-112">Par exemple, « ++ » et « -- ».</span><span class="sxs-lookup"><span data-stu-id="ae57a-112">For example, "++" and "--".</span></span>  
  
-   <span data-ttu-id="ae57a-113">Pour les parties de message, les membres sont autorisés à accéder aux méthodes publiques, aux types imbriqués, aux champs de données statiques, aux propriétés .NET en lecture seule annotées Microsoft.XLANGs.BaseTypes.DistinguishedFieldAttribute, à tous les champs de données publics et aux propriétés .NET autres qu'en lecture seule.</span><span class="sxs-lookup"><span data-stu-id="ae57a-113">For message parts, member access is allowed on public methods, nested types, static data fields, read-only .NET properties when annotated with Microsoft.XLANGs.BaseTypes.DistinguishedFieldAttribute, all public data fields, and non-read-only .NET properties.</span></span>  
  
-   <span data-ttu-id="ae57a-114">Les indexeurs et les propriétés .NET paramétrées ne sont pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="ae57a-114">Indexers or parameterized .NET properties are not supported.</span></span>  
  
-   <span data-ttu-id="ae57a-115">Les délégués et les événements ne sont pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="ae57a-115">Delegates and events are not supported.</span></span>  
  
-   <span data-ttu-id="ae57a-116">Les génériques ne sont pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="ae57a-116">Generics are not supported.</span></span>  
  
-   <span data-ttu-id="ae57a-117">Les éléments de syntaxe de contrôle de flux tels que « foreach », « for », « do-while », « break » et « continue » ne sont pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="ae57a-117">Flow control syntax such as "foreach", "for", "do-while", "break", and "continue" are not supported.</span></span>  
  
-   <span data-ttu-id="ae57a-118">Les opérateurs ternaires ne sont pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="ae57a-118">Ternary operations are not supported.</span></span> <span data-ttu-id="ae57a-119">Par exemple, « ?; ».</span><span class="sxs-lookup"><span data-stu-id="ae57a-119">For example, "?:".</span></span>  
  
-   <span data-ttu-id="ae57a-120">Vous pouvez ajouter des commentaires à la forme Expression, mais celle-ci doit contenir au moins une instruction.</span><span class="sxs-lookup"><span data-stu-id="ae57a-120">You can add comments in the Expression shape, but the Expression shape must contain at least one statement.</span></span>  
  
-   <span data-ttu-id="ae57a-121">Les tableaux ne sont pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="ae57a-121">Arrays are not supported.</span></span>  
  
-   <span data-ttu-id="ae57a-122">Lorsque la forme Expression est placée dans une forme Construire un message, vous ne pouvez pas procéder au contrôle de flux.</span><span class="sxs-lookup"><span data-stu-id="ae57a-122">When the Expression shape is placed in a Construct Message shape, you cannot do any control flow.</span></span> <span data-ttu-id="ae57a-123">Par exemple, « if-then-else » ou « while ».</span><span class="sxs-lookup"><span data-stu-id="ae57a-123">For example, "if-then-else" or "while".</span></span>  
  
-   <span data-ttu-id="ae57a-124">Toutes les instructions d'expression valides sont de la forme :</span><span class="sxs-lookup"><span data-stu-id="ae57a-124">All valid expression statements are of the form:</span></span>  
  
    -   <span data-ttu-id="ae57a-125">Dotted-name = expression;</span><span class="sxs-lookup"><span data-stu-id="ae57a-125">Dotted-name = expression;</span></span>  
  
    -   <span data-ttu-id="ae57a-126">Dotted-name = expression;</span><span class="sxs-lookup"><span data-stu-id="ae57a-126">Dotted-name = expression;</span></span>  
  
 <span data-ttu-id="ae57a-127">Vous pouvez utiliser l'Éditeur d'expression BizTalk pour entrer des expressions complexes rapidement et en toute simplicité, mais pas pour entrer une quantité arbitraire de code.</span><span class="sxs-lookup"><span data-stu-id="ae57a-127">Though you can use BizTalk Expression Editor to enter complex expressions easily and quickly, you cannot use it to enter an arbitrary amount of code.</span></span> <span data-ttu-id="ae57a-128">Cela permet de distinguer le code du processus d'entreprise de son code d'implémentation.</span><span class="sxs-lookup"><span data-stu-id="ae57a-128">The reason for this is to keep code for the business process separate from its implementation code.</span></span>