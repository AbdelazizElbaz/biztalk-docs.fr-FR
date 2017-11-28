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
ms.openlocfilehash: 2a9451d1f156bf98b3e8fd7da177937cd4492b0b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="xlang-s-to-bpel4ws-type-conversions"></a><span data-ttu-id="f728e-102">XLANG-s pour les Conversions de Type BPEL4WS</span><span class="sxs-lookup"><span data-stu-id="f728e-102">XLANG-s to BPEL4WS Type Conversions</span></span>
<span data-ttu-id="f728e-103">Les tableaux suivants présentent les conversions entre diverses constructions XLANG/s et BPEL4WS.</span><span class="sxs-lookup"><span data-stu-id="f728e-103">The following tables detail the conversions between various XLANG/s constructs and BPEL4WS constructs.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="f728e-104">XPath 1.1 ne prend pas en charge les nombres au format exponentiel ou double.</span><span class="sxs-lookup"><span data-stu-id="f728e-104">XPath 1.1 does not support numbers in exponential or double formats.</span></span> <span data-ttu-id="f728e-105">Les valeurs littérales de ces formats dans les orchestrations XLANG/s sont exportées vers BPEL4WS à l'aide du format %f, et une perte de précision peut en résulter.</span><span class="sxs-lookup"><span data-stu-id="f728e-105">Literal values in these formats in XLANG/s orchestrations are exported to BPEL4WS using the %f format, and a loss of precision might result.</span></span>  
  
## <a name="literals-if-the-literal-is-part-of-an-expression"></a><span data-ttu-id="f728e-106">Littéraux (si le littéral fait partie d'une expression)</span><span class="sxs-lookup"><span data-stu-id="f728e-106">Literals (if the literal is part of an expression)</span></span>  
  
|<span data-ttu-id="f728e-107">XLANG/s</span><span class="sxs-lookup"><span data-stu-id="f728e-107">XLANG/s</span></span>|<span data-ttu-id="f728e-108">BPEL4WS</span><span class="sxs-lookup"><span data-stu-id="f728e-108">BPEL4WS</span></span>|  
|--------------|-------------|  
|<span data-ttu-id="f728e-109">Chaîne, caractère</span><span class="sxs-lookup"><span data-stu-id="f728e-109">String, character</span></span>|<span data-ttu-id="f728e-110">Chaîne XPath</span><span class="sxs-lookup"><span data-stu-id="f728e-110">XPath string</span></span>|  
|<span data-ttu-id="f728e-111">Entier, réel</span><span class="sxs-lookup"><span data-stu-id="f728e-111">Integer, real</span></span>|<span data-ttu-id="f728e-112">Nombre XPath</span><span class="sxs-lookup"><span data-stu-id="f728e-112">XPath number</span></span>|  
|<span data-ttu-id="f728e-113">Booléen "true", "false"</span><span class="sxs-lookup"><span data-stu-id="f728e-113">Boolean "true", "false"</span></span>|<span data-ttu-id="f728e-114">Fonctions XPath true(), false()</span><span class="sxs-lookup"><span data-stu-id="f728e-114">XPath true(), false() functions</span></span>|  
  
## <a name="literals-standalone-assignment"></a><span data-ttu-id="f728e-115">Littéraux (assignation autonome)</span><span class="sxs-lookup"><span data-stu-id="f728e-115">Literals (standalone assignment)</span></span>  
  
|<span data-ttu-id="f728e-116">XLANG/s</span><span class="sxs-lookup"><span data-stu-id="f728e-116">XLANG/s</span></span>|<span data-ttu-id="f728e-117">BPEL4WS</span><span class="sxs-lookup"><span data-stu-id="f728e-117">BPEL4WS</span></span>|  
|--------------|-------------|  
|<span data-ttu-id="f728e-118">Constante littérale</span><span class="sxs-lookup"><span data-stu-id="f728e-118">Literal constant</span></span>|<span data-ttu-id="f728e-119">Équivalent XSD</span><span class="sxs-lookup"><span data-stu-id="f728e-119">XSD equivalent</span></span>|  
  
## <a name="variables"></a><span data-ttu-id="f728e-120">Variables</span><span class="sxs-lookup"><span data-stu-id="f728e-120">Variables</span></span>  
  
|<span data-ttu-id="f728e-121">XLANG/s</span><span class="sxs-lookup"><span data-stu-id="f728e-121">XLANG/s</span></span>|<span data-ttu-id="f728e-122">BPEL4WS</span><span class="sxs-lookup"><span data-stu-id="f728e-122">BPEL4WS</span></span>|  
|--------------|-------------|  
|<span data-ttu-id="f728e-123">Référence de variable</span><span class="sxs-lookup"><span data-stu-id="f728e-123">Variable reference</span></span>|<span data-ttu-id="f728e-124">bpws:getContainerData(%varName%,  part, %locationPath%)</span><span class="sxs-lookup"><span data-stu-id="f728e-124">bpws:getContainerData(%varName%,  part, %locationPath%)</span></span>|  
|<span data-ttu-id="f728e-125">Référence de message (type .NET)</span><span class="sxs-lookup"><span data-stu-id="f728e-125">Message reference (.NET type)</span></span>|<span data-ttu-id="f728e-126">getContainerData(%msgName%, part, %locationPath%)</span><span class="sxs-lookup"><span data-stu-id="f728e-126">bpws:getContainerData(%msgName%, part, %locationPath%)</span></span>|  
|<span data-ttu-id="f728e-127">Référence de partie de message</span><span class="sxs-lookup"><span data-stu-id="f728e-127">Message-part reference</span></span>|<span data-ttu-id="f728e-128">bpws:getContainerData(%msgName%, %locationPath%)</span><span class="sxs-lookup"><span data-stu-id="f728e-128">bpws:getContainerData(%msgName%, %locationPath%)</span></span>|  
|<span data-ttu-id="f728e-129">Référence de champ distinctif</span><span class="sxs-lookup"><span data-stu-id="f728e-129">Distinguished-field reference</span></span>|<span data-ttu-id="f728e-130">bpws:getContainerData(%msgName%, %partName%, %locationPath%)</span><span class="sxs-lookup"><span data-stu-id="f728e-130">bpws:getContainerData(%msgName%, %partName%, %locationPath%)</span></span>|  
|<span data-ttu-id="f728e-131">Référence de propriété de données de message</span><span class="sxs-lookup"><span data-stu-id="f728e-131">Message data-property reference</span></span>|<span data-ttu-id="f728e-132">bpws:getContainerProperty(%msgName%, %propertyQName%)</span><span class="sxs-lookup"><span data-stu-id="f728e-132">bpws:getContainerProperty(%msgName%, %propertyQName%)</span></span>|  
  
## <a name="operators"></a><span data-ttu-id="f728e-133">Opérateurs</span><span class="sxs-lookup"><span data-stu-id="f728e-133">Operators</span></span>  
  
|<span data-ttu-id="f728e-134">XLANG/s</span><span class="sxs-lookup"><span data-stu-id="f728e-134">XLANG/s</span></span>|<span data-ttu-id="f728e-135">BPEL4WS</span><span class="sxs-lookup"><span data-stu-id="f728e-135">BPEL4WS</span></span>|  
|--------------|-------------|  
|<span data-ttu-id="f728e-136">Unaire +</span><span class="sxs-lookup"><span data-stu-id="f728e-136">Unary +</span></span>|<span data-ttu-id="f728e-137">Ignoré</span><span class="sxs-lookup"><span data-stu-id="f728e-137">Ignored</span></span>|  
|<span data-ttu-id="f728e-138">Opérateur unaire -</span><span class="sxs-lookup"><span data-stu-id="f728e-138">Unary -</span></span>|<span data-ttu-id="f728e-139">Moins unaire XPath</span><span class="sxs-lookup"><span data-stu-id="f728e-139">XPath unary -</span></span>|  
|<span data-ttu-id="f728e-140">Unaire !</span><span class="sxs-lookup"><span data-stu-id="f728e-140">Unary !</span></span>|<span data-ttu-id="f728e-141">Fonction XPath not()</span><span class="sxs-lookup"><span data-stu-id="f728e-141">XPath not() function</span></span>|  
|<span data-ttu-id="f728e-142">Binaire & &, &#124; &#124;</span><span class="sxs-lookup"><span data-stu-id="f728e-142">Binary &&, &#124;&#124;</span></span>|<span data-ttu-id="f728e-143">Opérateurs XPath 'and', 'or'</span><span class="sxs-lookup"><span data-stu-id="f728e-143">XPath 'and', 'or' operators</span></span>|  
|<span data-ttu-id="f728e-144">Binaire ==, ! =, < =, \<, > =, ></span><span class="sxs-lookup"><span data-stu-id="f728e-144">Binary ==, !=, <=, \<, >=, ></span></span>|<span data-ttu-id="f728e-145">XPath '=', '!</span><span class="sxs-lookup"><span data-stu-id="f728e-145">XPath '=', '!</span></span> <span data-ttu-id="f728e-146">=', ' < = ','\<', ' > =', ' >' opérateurs</span><span class="sxs-lookup"><span data-stu-id="f728e-146">=', '<=', '\<', '>=', '>' operators</span></span>|  
|<span data-ttu-id="f728e-147">Binaire +, -, *, % avec les deux opérandes de type intégral</span><span class="sxs-lookup"><span data-stu-id="f728e-147">Binary +, -, *, % with both integral operands</span></span>|<span data-ttu-id="f728e-148">Opérateurs XPath '+', '-', '*', 'mod'</span><span class="sxs-lookup"><span data-stu-id="f728e-148">XPath '+', '-', '*', 'mod' operators</span></span>|  
  
## <a name="xlangs-constructs-that-are-disallowed-in-bpel4ws"></a><span data-ttu-id="f728e-149">Constructions XLANG/s non autorisées dans BPEL4WS</span><span class="sxs-lookup"><span data-stu-id="f728e-149">XLANG/s constructs that are disallowed in BPEL4WS</span></span>  
  
-   <span data-ttu-id="f728e-150">Référence de propriété de contexte de message</span><span class="sxs-lookup"><span data-stu-id="f728e-150">Message context-property reference</span></span>  
  
-   <span data-ttu-id="f728e-151">Référence de propriété de service</span><span class="sxs-lookup"><span data-stu-id="f728e-151">Service-property reference</span></span>  
  
-   <span data-ttu-id="f728e-152">Référence de propriété de port</span><span class="sxs-lookup"><span data-stu-id="f728e-152">Port-property reference</span></span>  
  
-   <span data-ttu-id="f728e-153">Référence de propriété de liaison de service</span><span class="sxs-lookup"><span data-stu-id="f728e-153">Service link-property reference</span></span>  
  
-   <span data-ttu-id="f728e-154">Unaire - de type non intégral</span><span class="sxs-lookup"><span data-stu-id="f728e-154">Unary – with non-integral type</span></span>  
  
-   <span data-ttu-id="f728e-155">Unaire ~</span><span class="sxs-lookup"><span data-stu-id="f728e-155">Unary ~</span></span>  
  
-   <span data-ttu-id="f728e-156">Opérateur de conversion</span><span class="sxs-lookup"><span data-stu-id="f728e-156">Cast operator</span></span>  
  
-   <span data-ttu-id="f728e-157">Binaire / avec opérandes de type intégral</span><span class="sxs-lookup"><span data-stu-id="f728e-157">Binary / with integral operands</span></span>  
  
-   <span data-ttu-id="f728e-158">Binaire +, -, *, %, / avec opérandes de type non intégral</span><span class="sxs-lookup"><span data-stu-id="f728e-158">Binary +, -, *, %, / with non-integral operands</span></span>  
  
-   <span data-ttu-id="f728e-159">Binaire < =, \<, > =, > avec opérandes de chaîne non</span><span class="sxs-lookup"><span data-stu-id="f728e-159">Binary <=, \<, >=, > with non-string operands</span></span>  
  
-   <span data-ttu-id="f728e-160">Opérateurs de bits &, ^, &#124;</span><span class="sxs-lookup"><span data-stu-id="f728e-160">Bitwise operators &, ^, &#124;</span></span>  
  
-   <span data-ttu-id="f728e-161">Opérateurs de décalage <\<, >></span><span class="sxs-lookup"><span data-stu-id="f728e-161">Shift operators <\<, >></span></span>  
  
-   <span data-ttu-id="f728e-162">Expression vérifiée</span><span class="sxs-lookup"><span data-stu-id="f728e-162">Checked expression</span></span>  
  
-   <span data-ttu-id="f728e-163">Expression intrinsèque</span><span class="sxs-lookup"><span data-stu-id="f728e-163">Intrinsic expression</span></span>  
  
-   <span data-ttu-id="f728e-164">Antérieur et postérieur à l'incrémentation et la décrémentation ++, --</span><span class="sxs-lookup"><span data-stu-id="f728e-164">Pre- and post- increment and decrement ++, --</span></span>  
  
-   <span data-ttu-id="f728e-165">Appel d'objet (paramètres de référence avec ou sans ou et/ou)</span><span class="sxs-lookup"><span data-stu-id="f728e-165">Object invocation (with our without out and/or ref params)</span></span>  
  
-   <span data-ttu-id="f728e-166">Opérateur 'new'</span><span class="sxs-lookup"><span data-stu-id="f728e-166">'new' operator</span></span>