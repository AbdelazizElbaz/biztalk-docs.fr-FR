---
title: Conversions de Type XLANG-s en BPEL4WS | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XLANG/s
- XLANG/s, warning
- XLANG/s, BPEL4WS
- XLANG/s, converting
ms.assetid: a35d4dba-9344-43c8-86e6-a373a4452579
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 02412b86b8649b73cadb4715793f085682a1de74
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="xlang-s-to-bpel4ws-type-conversions"></a><span data-ttu-id="2fc50-102">XLANG-s pour les Conversions de Type BPEL4WS</span><span class="sxs-lookup"><span data-stu-id="2fc50-102">XLANG-s to BPEL4WS Type Conversions</span></span>
<span data-ttu-id="2fc50-103">Les tableaux suivants présentent les conversions entre diverses constructions XLANG/s et BPEL4WS.</span><span class="sxs-lookup"><span data-stu-id="2fc50-103">The following tables detail the conversions between various XLANG/s constructs and BPEL4WS constructs.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="2fc50-104">XPath 1.1 ne prend pas en charge les nombres au format exponentiel ou double.</span><span class="sxs-lookup"><span data-stu-id="2fc50-104">XPath 1.1 does not support numbers in exponential or double formats.</span></span> <span data-ttu-id="2fc50-105">Les valeurs littérales de ces formats dans les orchestrations XLANG/s sont exportées vers BPEL4WS à l'aide du format %f, et une perte de précision peut en résulter.</span><span class="sxs-lookup"><span data-stu-id="2fc50-105">Literal values in these formats in XLANG/s orchestrations are exported to BPEL4WS using the %f format, and a loss of precision might result.</span></span>  
  
## <a name="literals-if-the-literal-is-part-of-an-expression"></a><span data-ttu-id="2fc50-106">Littéraux (si le littéral fait partie d'une expression)</span><span class="sxs-lookup"><span data-stu-id="2fc50-106">Literals (if the literal is part of an expression)</span></span>  
  
|<span data-ttu-id="2fc50-107">XLANG/s</span><span class="sxs-lookup"><span data-stu-id="2fc50-107">XLANG/s</span></span>|<span data-ttu-id="2fc50-108">BPEL4WS</span><span class="sxs-lookup"><span data-stu-id="2fc50-108">BPEL4WS</span></span>|  
|--------------|-------------|  
|<span data-ttu-id="2fc50-109">Chaîne, caractère</span><span class="sxs-lookup"><span data-stu-id="2fc50-109">String, character</span></span>|<span data-ttu-id="2fc50-110">Chaîne XPath</span><span class="sxs-lookup"><span data-stu-id="2fc50-110">XPath string</span></span>|  
|<span data-ttu-id="2fc50-111">Entier, réel</span><span class="sxs-lookup"><span data-stu-id="2fc50-111">Integer, real</span></span>|<span data-ttu-id="2fc50-112">Nombre XPath</span><span class="sxs-lookup"><span data-stu-id="2fc50-112">XPath number</span></span>|  
|<span data-ttu-id="2fc50-113">Booléen "true", "false"</span><span class="sxs-lookup"><span data-stu-id="2fc50-113">Boolean "true", "false"</span></span>|<span data-ttu-id="2fc50-114">Fonctions XPath true(), false()</span><span class="sxs-lookup"><span data-stu-id="2fc50-114">XPath true(), false() functions</span></span>|  
  
## <a name="literals-standalone-assignment"></a><span data-ttu-id="2fc50-115">Littéraux (assignation autonome)</span><span class="sxs-lookup"><span data-stu-id="2fc50-115">Literals (standalone assignment)</span></span>  
  
|<span data-ttu-id="2fc50-116">XLANG/s</span><span class="sxs-lookup"><span data-stu-id="2fc50-116">XLANG/s</span></span>|<span data-ttu-id="2fc50-117">BPEL4WS</span><span class="sxs-lookup"><span data-stu-id="2fc50-117">BPEL4WS</span></span>|  
|--------------|-------------|  
|<span data-ttu-id="2fc50-118">Constante littérale</span><span class="sxs-lookup"><span data-stu-id="2fc50-118">Literal constant</span></span>|<span data-ttu-id="2fc50-119">Équivalent XSD</span><span class="sxs-lookup"><span data-stu-id="2fc50-119">XSD equivalent</span></span>|  
  
## <a name="variables"></a><span data-ttu-id="2fc50-120">Variables</span><span class="sxs-lookup"><span data-stu-id="2fc50-120">Variables</span></span>  
  
|<span data-ttu-id="2fc50-121">XLANG/s</span><span class="sxs-lookup"><span data-stu-id="2fc50-121">XLANG/s</span></span>|<span data-ttu-id="2fc50-122">BPEL4WS</span><span class="sxs-lookup"><span data-stu-id="2fc50-122">BPEL4WS</span></span>|  
|--------------|-------------|  
|<span data-ttu-id="2fc50-123">Référence de variable</span><span class="sxs-lookup"><span data-stu-id="2fc50-123">Variable reference</span></span>|<span data-ttu-id="2fc50-124">bpws:getContainerData(%varName%,  part, %locationPath%)</span><span class="sxs-lookup"><span data-stu-id="2fc50-124">bpws:getContainerData(%varName%,  part, %locationPath%)</span></span>|  
|<span data-ttu-id="2fc50-125">Référence de message (type .NET)</span><span class="sxs-lookup"><span data-stu-id="2fc50-125">Message reference (.NET type)</span></span>|<span data-ttu-id="2fc50-126">getContainerData(%msgName%, part, %locationPath%)</span><span class="sxs-lookup"><span data-stu-id="2fc50-126">bpws:getContainerData(%msgName%, part, %locationPath%)</span></span>|  
|<span data-ttu-id="2fc50-127">Référence de partie de message</span><span class="sxs-lookup"><span data-stu-id="2fc50-127">Message-part reference</span></span>|<span data-ttu-id="2fc50-128">bpws:getContainerData(%msgName%, %locationPath%)</span><span class="sxs-lookup"><span data-stu-id="2fc50-128">bpws:getContainerData(%msgName%, %locationPath%)</span></span>|  
|<span data-ttu-id="2fc50-129">Référence de champ distinctif</span><span class="sxs-lookup"><span data-stu-id="2fc50-129">Distinguished-field reference</span></span>|<span data-ttu-id="2fc50-130">bpws:getContainerData(%msgName%, %partName%, %locationPath%)</span><span class="sxs-lookup"><span data-stu-id="2fc50-130">bpws:getContainerData(%msgName%, %partName%, %locationPath%)</span></span>|  
|<span data-ttu-id="2fc50-131">Référence de propriété de données de message</span><span class="sxs-lookup"><span data-stu-id="2fc50-131">Message data-property reference</span></span>|<span data-ttu-id="2fc50-132">bpws:getContainerProperty(%msgName%, %propertyQName%)</span><span class="sxs-lookup"><span data-stu-id="2fc50-132">bpws:getContainerProperty(%msgName%, %propertyQName%)</span></span>|  
  
## <a name="operators"></a><span data-ttu-id="2fc50-133">Opérateurs</span><span class="sxs-lookup"><span data-stu-id="2fc50-133">Operators</span></span>  
  
|<span data-ttu-id="2fc50-134">XLANG/s</span><span class="sxs-lookup"><span data-stu-id="2fc50-134">XLANG/s</span></span>|<span data-ttu-id="2fc50-135">BPEL4WS</span><span class="sxs-lookup"><span data-stu-id="2fc50-135">BPEL4WS</span></span>|  
|--------------|-------------|  
|<span data-ttu-id="2fc50-136">Unaire +</span><span class="sxs-lookup"><span data-stu-id="2fc50-136">Unary +</span></span>|<span data-ttu-id="2fc50-137">Ignoré</span><span class="sxs-lookup"><span data-stu-id="2fc50-137">Ignored</span></span>|  
|<span data-ttu-id="2fc50-138">Opérateur unaire -</span><span class="sxs-lookup"><span data-stu-id="2fc50-138">Unary -</span></span>|<span data-ttu-id="2fc50-139">Moins unaire XPath</span><span class="sxs-lookup"><span data-stu-id="2fc50-139">XPath unary -</span></span>|  
|<span data-ttu-id="2fc50-140">Unaire !</span><span class="sxs-lookup"><span data-stu-id="2fc50-140">Unary !</span></span>|<span data-ttu-id="2fc50-141">Fonction XPath not()</span><span class="sxs-lookup"><span data-stu-id="2fc50-141">XPath not() function</span></span>|  
|<span data-ttu-id="2fc50-142">Binaire & &, &#124; &#124;</span><span class="sxs-lookup"><span data-stu-id="2fc50-142">Binary &&, &#124;&#124;</span></span>|<span data-ttu-id="2fc50-143">Opérateurs XPath 'and', 'or'</span><span class="sxs-lookup"><span data-stu-id="2fc50-143">XPath 'and', 'or' operators</span></span>|  
|<span data-ttu-id="2fc50-144">Binaire ==, !=, <=, <, >=, ></span><span class="sxs-lookup"><span data-stu-id="2fc50-144">Binary ==, !=, <=, <, >=, ></span></span>|<span data-ttu-id="2fc50-145">XPath '=', '!</span><span class="sxs-lookup"><span data-stu-id="2fc50-145">XPath '=', '!</span></span> <span data-ttu-id="2fc50-146">=', ' < =', ' <', ' > =', ' >' opérateurs</span><span class="sxs-lookup"><span data-stu-id="2fc50-146">=', '<=', '<', '>=', '>' operators</span></span>|  
|<span data-ttu-id="2fc50-147">Binaire +, -, *, % avec les deux opérandes de type intégral</span><span class="sxs-lookup"><span data-stu-id="2fc50-147">Binary +, -, *, % with both integral operands</span></span>|<span data-ttu-id="2fc50-148">Opérateurs XPath '+', '-', '*', 'mod'</span><span class="sxs-lookup"><span data-stu-id="2fc50-148">XPath '+', '-', '*', 'mod' operators</span></span>|  
  
## <a name="xlangs-constructs-that-are-disallowed-in-bpel4ws"></a><span data-ttu-id="2fc50-149">Constructions XLANG/s non autorisées dans BPEL4WS</span><span class="sxs-lookup"><span data-stu-id="2fc50-149">XLANG/s constructs that are disallowed in BPEL4WS</span></span>  
  
-   <span data-ttu-id="2fc50-150">Référence de propriété de contexte de message</span><span class="sxs-lookup"><span data-stu-id="2fc50-150">Message context-property reference</span></span>  
  
-   <span data-ttu-id="2fc50-151">Référence de propriété de service</span><span class="sxs-lookup"><span data-stu-id="2fc50-151">Service-property reference</span></span>  
  
-   <span data-ttu-id="2fc50-152">Référence de propriété de port</span><span class="sxs-lookup"><span data-stu-id="2fc50-152">Port-property reference</span></span>  
  
-   <span data-ttu-id="2fc50-153">Référence de propriété de liaison de service</span><span class="sxs-lookup"><span data-stu-id="2fc50-153">Service link-property reference</span></span>  
  
-   <span data-ttu-id="2fc50-154">Unaire - de type non intégral</span><span class="sxs-lookup"><span data-stu-id="2fc50-154">Unary – with non-integral type</span></span>  
  
-   <span data-ttu-id="2fc50-155">Unaire ~</span><span class="sxs-lookup"><span data-stu-id="2fc50-155">Unary ~</span></span>  
  
-   <span data-ttu-id="2fc50-156">Opérateur de conversion</span><span class="sxs-lookup"><span data-stu-id="2fc50-156">Cast operator</span></span>  
  
-   <span data-ttu-id="2fc50-157">Binaire / avec opérandes de type intégral</span><span class="sxs-lookup"><span data-stu-id="2fc50-157">Binary / with integral operands</span></span>  
  
-   <span data-ttu-id="2fc50-158">Binaire +, -, *, %, / avec opérandes de type non intégral</span><span class="sxs-lookup"><span data-stu-id="2fc50-158">Binary +, -, *, %, / with non-integral operands</span></span>  
  
-   <span data-ttu-id="2fc50-159">Binaire <=, <, >=, > avec opérandes de type non chaîne</span><span class="sxs-lookup"><span data-stu-id="2fc50-159">Binary <=, <, >=, > with non-string operands</span></span>  
  
-   <span data-ttu-id="2fc50-160">Opérateurs de bits &, ^, &#124;</span><span class="sxs-lookup"><span data-stu-id="2fc50-160">Bitwise operators &, ^, &#124;</span></span>  
  
-   <span data-ttu-id="2fc50-161">Opérateurs de décalage <<, >></span><span class="sxs-lookup"><span data-stu-id="2fc50-161">Shift operators <<, >></span></span>  
  
-   <span data-ttu-id="2fc50-162">Expression vérifiée</span><span class="sxs-lookup"><span data-stu-id="2fc50-162">Checked expression</span></span>  
  
-   <span data-ttu-id="2fc50-163">Expression intrinsèque</span><span class="sxs-lookup"><span data-stu-id="2fc50-163">Intrinsic expression</span></span>  
  
-   <span data-ttu-id="2fc50-164">Antérieur et postérieur à l'incrémentation et la décrémentation ++, --</span><span class="sxs-lookup"><span data-stu-id="2fc50-164">Pre- and post- increment and decrement ++, --</span></span>  
  
-   <span data-ttu-id="2fc50-165">Appel d'objet (paramètres de référence avec ou sans ou et/ou)</span><span class="sxs-lookup"><span data-stu-id="2fc50-165">Object invocation (with our without out and/or ref params)</span></span>  
  
-   <span data-ttu-id="2fc50-166">Opérateur 'new'</span><span class="sxs-lookup"><span data-stu-id="2fc50-166">'new' operator</span></span>