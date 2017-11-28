---
title: "À l’aide de la Type2 MATH_NUMERIC | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- exponents, JD Edwards OneWorld adapters
- currency, JD Edwards OneWorld adapters
- MATH_NUMERIC type
- adapters [JD Edwards OneWorld adapters], currency
ms.assetid: 14d04576-0028-4af4-84bd-92c4ca492126
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ac6c96c32244acdcfaf81e8747e381bebd455598
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="using-the-mathnumeric-type"></a><span data-ttu-id="eca5c-102">À l’aide du Type MATH_NUMERIC</span><span class="sxs-lookup"><span data-stu-id="eca5c-102">Using the MATH_NUMERIC Type</span></span>
<span data-ttu-id="eca5c-103">Cette rubrique décrit le type MATH_NUMERIC et détaille la gestion des exposants, le nombre maximal de chiffres et le nombre maximal de chiffres décimaux.</span><span class="sxs-lookup"><span data-stu-id="eca5c-103">This topic describes the MATH_NUMERIC type and details how exponents are handled, the maximum number of digits, and the maximum number of decimal digits.</span></span> <span data-ttu-id="eca5c-104">Il inclut également une discussion sur les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="eca5c-104">It also includes a discussion on the following:</span></span>  
  
-   <span data-ttu-id="eca5c-105">exposants ;</span><span class="sxs-lookup"><span data-stu-id="eca5c-105">Exponents</span></span>  
  
-   <span data-ttu-id="eca5c-106">valeurs non valides ;</span><span class="sxs-lookup"><span data-stu-id="eca5c-106">Invalid Values</span></span>  
  
-   <span data-ttu-id="eca5c-107">précision des opérations ;</span><span class="sxs-lookup"><span data-stu-id="eca5c-107">Precision for Operations</span></span>  
  
-   <span data-ttu-id="eca5c-108">Monétaire (Currency)</span><span class="sxs-lookup"><span data-stu-id="eca5c-108">Currency</span></span>  
  
 <span data-ttu-id="eca5c-109">Le type MATH_NUMERIC est un type de chaîne numérique.</span><span class="sxs-lookup"><span data-stu-id="eca5c-109">The MATH_NUMERIC type is a numeric string type.</span></span> <span data-ttu-id="eca5c-110">Pour l'utiliser, vous devez entrer les valeurs des paramètres au format suivant :</span><span class="sxs-lookup"><span data-stu-id="eca5c-110">To use it, enter parameter values of the following format:</span></span>  
  
```  
<OptionalSign><IntegerAndFractionalPart><OptionalExponentPart>  
```  
  
 <span data-ttu-id="eca5c-111">Où</span><span class="sxs-lookup"><span data-stu-id="eca5c-111">Where</span></span>  
  
-   <span data-ttu-id="eca5c-112">`<OptionalSign>`peut être `+` ou `-`.</span><span class="sxs-lookup"><span data-stu-id="eca5c-112">`<OptionalSign>` can be `+` or `-`.</span></span> <span data-ttu-id="eca5c-113">`+`est la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="eca5c-113">`+` is the default.</span></span>  
  
-   <span data-ttu-id="eca5c-114">`<IntegerAndFractionalPart>` inclut jusqu'à 32 chiffres significatifs, sans compter le symbole décimal.</span><span class="sxs-lookup"><span data-stu-id="eca5c-114">`<IntegerAndFractionalPart>` is a maximum of 32 significant digits, not counting the decimal symbol.</span></span> <span data-ttu-id="eca5c-115">Le symbole décimal est spécifique aux paramètres régionaux de l'installation JD Edwards OneWorld, généralement un point (.) ou une virgule (,).</span><span class="sxs-lookup"><span data-stu-id="eca5c-115">The decimal symbol is locale-specific to the JD Edwards OneWorld installation—typically a period (.) or a comma (,).</span></span> <span data-ttu-id="eca5c-116">Les chiffres peuvent être des nombres entiers et/ou des fractions, et sont 32 au maximum.</span><span class="sxs-lookup"><span data-stu-id="eca5c-116">The digits may be all integer, all fraction, or part integer and part fraction, but they cannot exceed 32.</span></span>  
  
-   <span data-ttu-id="eca5c-117">`<OptionalExponentPart>` est équivalent à :</span><span class="sxs-lookup"><span data-stu-id="eca5c-117">`<OptionalExponentPart>` is equivalent to:</span></span>  
  
    ```  
    'e' <OptionalSign><ExponentDigits>  
    ```  
  
 <span data-ttu-id="eca5c-118">Où</span><span class="sxs-lookup"><span data-stu-id="eca5c-118">Where</span></span>  
  
-   <span data-ttu-id="eca5c-119">`<OptionalSign>`peut être `+` ou -.</span><span class="sxs-lookup"><span data-stu-id="eca5c-119">`<OptionalSign>` can be `+` or -.</span></span> <span data-ttu-id="eca5c-120">`+`est la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="eca5c-120">`+` is the default.</span></span>  
  
-   <span data-ttu-id="eca5c-121">`<ExponentDigits>` inclut jusqu'à deux chiffres.</span><span class="sxs-lookup"><span data-stu-id="eca5c-121">`<ExponentDigits>` are at most two digits.</span></span> <span data-ttu-id="eca5c-122">Les valeurs comprises entre 63 et -63 sont autorisées (à l'exception de zéro).</span><span class="sxs-lookup"><span data-stu-id="eca5c-122">You are permitted values between 63 and -63 excluding zero.</span></span>  
  
## <a name="valid-values"></a><span data-ttu-id="eca5c-123">Valeurs valides</span><span class="sxs-lookup"><span data-stu-id="eca5c-123">Valid Values</span></span>  
 <span data-ttu-id="eca5c-124">Voici des exemples de valeurs MATH_NUMERIC valides :</span><span class="sxs-lookup"><span data-stu-id="eca5c-124">Examples of valid MATH_NUMERIC values:</span></span>  
  
-   <span data-ttu-id="eca5c-125">123.045</span><span class="sxs-lookup"><span data-stu-id="eca5c-125">123.045</span></span>  
  
-   <span data-ttu-id="eca5c-126">4089 (notez qu'il n'y a pas de virgule pour les milliers)</span><span class="sxs-lookup"><span data-stu-id="eca5c-126">4089 (note there is no comma for thousands)</span></span>  
  
-   <span data-ttu-id="eca5c-127">-9084</span><span class="sxs-lookup"><span data-stu-id="eca5c-127">-9084</span></span>  
  
-   <span data-ttu-id="eca5c-128">-230.75</span><span class="sxs-lookup"><span data-stu-id="eca5c-128">-230.75</span></span>  
  
-   <span data-ttu-id="eca5c-129">0.010503</span><span class="sxs-lookup"><span data-stu-id="eca5c-129">0.010503</span></span>  
  
-   <span data-ttu-id="eca5c-130">1.023e-10, qui est équivalent à 0.0000000001023</span><span class="sxs-lookup"><span data-stu-id="eca5c-130">1.023e-10, which is equivalent to 0.0000000001023</span></span>  
  
-   <span data-ttu-id="eca5c-131">0.097e5 ou 0.097e+5, qui est équivalent à 9700</span><span class="sxs-lookup"><span data-stu-id="eca5c-131">0.097e5 or 0.097e+5, which is equivalent to 9700</span></span>  
  
-   <span data-ttu-id="eca5c-132">1.0e-32, qui est équivalent à 0.00000000000000000000000000000001</span><span class="sxs-lookup"><span data-stu-id="eca5c-132">1.0e-32, which is equivalent to 0.00000000000000000000000000000001</span></span>  
  
     <span data-ttu-id="eca5c-133">(Cette valeur est valide car, dans ce cas, l'intégrale « 0 » est ignorée, 32 chiffres fractionnels significatifs.)</span><span class="sxs-lookup"><span data-stu-id="eca5c-133">(This is valid because in this case the integral '0' is ignored, 32 significant fractional digits.)</span></span>  
  
## <a name="invalid-values"></a><span data-ttu-id="eca5c-134">valeurs non valides ;</span><span class="sxs-lookup"><span data-stu-id="eca5c-134">Invalid Values</span></span>  
 <span data-ttu-id="eca5c-135">Les valeurs non valides dépendent du type de valeur.</span><span class="sxs-lookup"><span data-stu-id="eca5c-135">Invalid values depend on the kind of value.</span></span> <span data-ttu-id="eca5c-136">Une fraction décimale trop petite est interprétée comme un zéro (tous les chiffres significatifs sont perdus).</span><span class="sxs-lookup"><span data-stu-id="eca5c-136">A decimal fraction that is too small is interpreted as zero (all significant digits are lost).</span></span> <span data-ttu-id="eca5c-137">Un nombre entier ayant trop de chiffres significatifs génère des résultats inattendus.</span><span class="sxs-lookup"><span data-stu-id="eca5c-137">An integer that has too many significant digits causes unexpected results.</span></span> <span data-ttu-id="eca5c-138">JD Edwards OneWorld ne génère pas toujours une condition d'erreur dans ce cas.</span><span class="sxs-lookup"><span data-stu-id="eca5c-138">JD Edwards OneWorld does not always raise an error condition in this case.</span></span>  
  
 <span data-ttu-id="eca5c-139">Un exposant est trop grande ou petite retourne sous la forme d’une valeur non valide.</span><span class="sxs-lookup"><span data-stu-id="eca5c-139">An exponent that is too large or small returns as an invalid value.</span></span>  
  
 <span data-ttu-id="eca5c-140">Voici des exemples de valeurs MATH_NUMERIC non valides :</span><span class="sxs-lookup"><span data-stu-id="eca5c-140">Examples of invalid MATH_NUMERIC values:</span></span>  
  
-   <span data-ttu-id="eca5c-141">1034.00000000000000000000000000001023 (trop de chiffres significatifs)</span><span class="sxs-lookup"><span data-stu-id="eca5c-141">1034.00000000000000000000000000001023 - too many significant digits</span></span>  
  
-   <span data-ttu-id="eca5c-142">1.023e-64 (exposant trop petit)</span><span class="sxs-lookup"><span data-stu-id="eca5c-142">1.023e-64 - exponent too small</span></span>  
  
-   <span data-ttu-id="eca5c-143">0.00317e64 (exposant trop grand)</span><span class="sxs-lookup"><span data-stu-id="eca5c-143">0.00317e64 - exponent too large</span></span>  
  
 <span data-ttu-id="eca5c-144">Les caractères non numériques autres que ceux appropriés pour les signes et symboles décimaux génèrent une valeur non valide.</span><span class="sxs-lookup"><span data-stu-id="eca5c-144">Any non-numeric characters other than those appropriate for signs and decimal symbols result in an invalid value.</span></span>  
  
## <a name="exponents"></a><span data-ttu-id="eca5c-145">exposants ;</span><span class="sxs-lookup"><span data-stu-id="eca5c-145">Exponents</span></span>  
 <span data-ttu-id="eca5c-146">Les exposants fournis par le type MATH_NUMERIC de JD Edwards OneWorld facilitent la saisie des valeurs.</span><span class="sxs-lookup"><span data-stu-id="eca5c-146">Exponents are provided by the JD Edwards OneWorld MATH_NUMERIC as a convenience for entering values.</span></span> <span data-ttu-id="eca5c-147">Toutefois, la plupart des valeurs sont renvoyées sans exposant (avec les 32 chiffres significatifs visibles).</span><span class="sxs-lookup"><span data-stu-id="eca5c-147">However, most values return without exponents (with all 32 significant digits visible).</span></span>  
  
## <a name="precision-for-operations"></a><span data-ttu-id="eca5c-148">précision des opérations ;</span><span class="sxs-lookup"><span data-stu-id="eca5c-148">Precision for Operations</span></span>  
 <span data-ttu-id="eca5c-149">Si une opération entraîne une perte de précision, un arrondi est effectué.</span><span class="sxs-lookup"><span data-stu-id="eca5c-149">If an operation results in loss of precision, rounding occurs.</span></span> <span data-ttu-id="eca5c-150">Exemple :</span><span class="sxs-lookup"><span data-stu-id="eca5c-150">For example:</span></span>  
  
 <span data-ttu-id="eca5c-151">1.9e-31 / 10.0 = 0.00000000000000000000000000000002</span><span class="sxs-lookup"><span data-stu-id="eca5c-151">1.9e-31 / 10.0 = 0.00000000000000000000000000000002</span></span>  
  
 <span data-ttu-id="eca5c-152">1.9e-31 / 100.0 = 0.00000000000000000000000000000000</span><span class="sxs-lookup"><span data-stu-id="eca5c-152">1.9e-31 / 100.0 = 0.00000000000000000000000000000000</span></span>  
  
 <span data-ttu-id="eca5c-153">Dans d'autres cas, des résultats imprévisibles sont générés, comme lorsqu'une valeur positive très grande est multipliée par une autre.</span><span class="sxs-lookup"><span data-stu-id="eca5c-153">In other cases, unpredictable results occur, as when a very large positive value is multiplied by another.</span></span>  
  
 <span data-ttu-id="eca5c-154">1.01e32 * 2.053e32 ne génère pas de résultats fiables et ne génère pas d’erreur.</span><span class="sxs-lookup"><span data-stu-id="eca5c-154">1.01e32 * 2.053e32 does not yield reliable results and does not raise an error.</span></span>  
  
 <span data-ttu-id="eca5c-155">Pour la plupart des scénarios d'entreprise, ces plages ne sont pas dépassées.</span><span class="sxs-lookup"><span data-stu-id="eca5c-155">For most business scenarios, these ranges are not exceeded.</span></span>  
  
## <a name="currency"></a><span data-ttu-id="eca5c-156">Monétaire (Currency)</span><span class="sxs-lookup"><span data-stu-id="eca5c-156">Currency</span></span>  
 <span data-ttu-id="eca5c-157">Lorsqu'une fonction d'entreprise JD Edwards OneWorld attend une valeur de devise, la fonction d'entreprise inclut toujours un paramètre distinct pour un code de devise à quatre caractères.</span><span class="sxs-lookup"><span data-stu-id="eca5c-157">When a JD Edwards OneWorld business function expects a currency value, the business function always has a separate parameter for a four-character currency code.</span></span> <span data-ttu-id="eca5c-158">Il n'est pas nécessaire de transmettre ce code, sauf si vous utilisez une devise autre que celle par défaut configurée pour le système JD Edwards OneWorld.</span><span class="sxs-lookup"><span data-stu-id="eca5c-158">It is not necessary to pass in this code unless you are using a currency other than the default configured for the JD Edwards OneWorld system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eca5c-159">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="eca5c-159">See Also</span></span>  
 [<span data-ttu-id="eca5c-160">Annexe a : les Types de données</span><span class="sxs-lookup"><span data-stu-id="eca5c-160">Appendix A: Data Types</span></span>](../core/appendix-a-data-types.md)