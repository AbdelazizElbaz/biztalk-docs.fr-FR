---
title: "À l’aide de la Type1 MATH_NUMERIC | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- adapters [JD Edwards EnterpriseOne adapters], currency
- JD Edwards EnterpriseOne adapters, exponents
- adapters [JD Edwards EnterpriseOne adapters], exponents
- MATH_NUMERIC type
- currency, values [JD Edwards EnterpriseOne adapters]
- JD Edwards EnterpriseOne adapters, currency
- exponents, values [JD Edwards EnterpriseOne adapters]
ms.assetid: 2a302216-f0a6-4afb-8f7d-bb1475ea1c57
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ec4a5df2d15f489d52c8e3d6dfc575f9e644c646
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="using-the-mathnumeric-type"></a><span data-ttu-id="09e9a-102">À l’aide du Type MATH_NUMERIC</span><span class="sxs-lookup"><span data-stu-id="09e9a-102">Using the MATH_NUMERIC Type</span></span>
<span data-ttu-id="09e9a-103">Cette rubrique décrit le type MATH_NUMERIC et détaille la gestion des exposants, le nombre maximal de chiffres et le nombre maximal de chiffres décimaux.</span><span class="sxs-lookup"><span data-stu-id="09e9a-103">This topic describes the MATH_NUMERIC type and details how exponents are handled, the maximum number of digits, and the maximum number of decimal digits.</span></span> <span data-ttu-id="09e9a-104">Elle décrit également les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="09e9a-104">It also includes a discussion on:</span></span>  
  
-   <span data-ttu-id="09e9a-105">exposants ;</span><span class="sxs-lookup"><span data-stu-id="09e9a-105">Exponents</span></span>  
  
-   <span data-ttu-id="09e9a-106">valeurs non valides ;</span><span class="sxs-lookup"><span data-stu-id="09e9a-106">Invalid Values</span></span>  
  
-   <span data-ttu-id="09e9a-107">précision des opérations ;</span><span class="sxs-lookup"><span data-stu-id="09e9a-107">Precision for Operations</span></span>  
  
-   <span data-ttu-id="09e9a-108">Monétaire (Currency)</span><span class="sxs-lookup"><span data-stu-id="09e9a-108">Currency</span></span>  
  
 <span data-ttu-id="09e9a-109">Le type MATH_NUMERIC est un type de chaîne numérique.</span><span class="sxs-lookup"><span data-stu-id="09e9a-109">The MATH_NUMERIC type is a numeric string type.</span></span> <span data-ttu-id="09e9a-110">Pour l'utiliser, vous devez entrer les valeurs des paramètres au format suivant :</span><span class="sxs-lookup"><span data-stu-id="09e9a-110">To use it, enter parameter values of the following format:</span></span>  
  
```  
<OptionalSign><IntegerAndFractionalPart><OptionalExponentPart>  
  
```  
  
 <span data-ttu-id="09e9a-111">Où</span><span class="sxs-lookup"><span data-stu-id="09e9a-111">Where</span></span>  
  
 <span data-ttu-id="09e9a-112">`<OptionalSign>`peut être `+` ou `-`.</span><span class="sxs-lookup"><span data-stu-id="09e9a-112">`<OptionalSign>` can be `+` or `-`.</span></span> <span data-ttu-id="09e9a-113">`+`est la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="09e9a-113">`+` is the default.</span></span>  
  
 <span data-ttu-id="09e9a-114">`<IntegerAndFractionalPart>` inclut jusqu'à 32 chiffres significatifs, sans compter le symbole décimal.</span><span class="sxs-lookup"><span data-stu-id="09e9a-114">`<IntegerAndFractionalPart>` is a maximum of 32 significant digits, not counting the decimal symbol.</span></span> <span data-ttu-id="09e9a-115">Le symbole décimal est spécifique aux paramètres régionaux de l'installation EnterpriseOne, généralement un point (.) ou une virgule (,).</span><span class="sxs-lookup"><span data-stu-id="09e9a-115">The decimal symbol is locale-specific to the JD Edwards EnterpriseOne installation—typically a period (.) or a comma (,).</span></span> <span data-ttu-id="09e9a-116">Les chiffres peuvent être des nombres entiers et/ou des fractions, et sont 32 au maximum.</span><span class="sxs-lookup"><span data-stu-id="09e9a-116">The digits may be all integer, all fraction, or part integer and part fraction, but they cannot exceed 32.</span></span>  
  
 <span data-ttu-id="09e9a-117">`<OptionalExponentPart>` est équivalent à :</span><span class="sxs-lookup"><span data-stu-id="09e9a-117">`<OptionalExponentPart>` is equivalent to:</span></span>  
  
```  
'e' <OptionalSign><ExponentDigits>  
```  
  
 <span data-ttu-id="09e9a-118">Où</span><span class="sxs-lookup"><span data-stu-id="09e9a-118">Where</span></span>  
  
 <span data-ttu-id="09e9a-119">`<OptionalSign>`peut être `+` ou `-`.</span><span class="sxs-lookup"><span data-stu-id="09e9a-119">`<OptionalSign>` can be `+` or `-`.</span></span> <span data-ttu-id="09e9a-120">`+`est la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="09e9a-120">`+` is the default.</span></span>  
  
 <span data-ttu-id="09e9a-121">`<ExponentDigits>` inclut jusqu'à deux chiffres.</span><span class="sxs-lookup"><span data-stu-id="09e9a-121">`<ExponentDigits>` are at most two digits.</span></span> <span data-ttu-id="09e9a-122">Les valeurs comprises entre 63 et -63 sont autorisées (à l'exception de zéro).</span><span class="sxs-lookup"><span data-stu-id="09e9a-122">You are permitted values between 63 and -63 excluding zero.</span></span>  
  
## <a name="valid-values"></a><span data-ttu-id="09e9a-123">Valeurs valides</span><span class="sxs-lookup"><span data-stu-id="09e9a-123">Valid Values</span></span>  
 <span data-ttu-id="09e9a-124">Exemples de **valide** valeurs MATH_NUMERIC :</span><span class="sxs-lookup"><span data-stu-id="09e9a-124">Examples of **valid** MATH_NUMERIC values:</span></span>  
  
-   <span data-ttu-id="09e9a-125">123.045</span><span class="sxs-lookup"><span data-stu-id="09e9a-125">123.045</span></span>  
  
-   <span data-ttu-id="09e9a-126">4089 (notez qu'il n'y a pas de virgule pour les milliers)</span><span class="sxs-lookup"><span data-stu-id="09e9a-126">4089 (note there is no comma for thousands)</span></span>  
  
-   <span data-ttu-id="09e9a-127">-9084</span><span class="sxs-lookup"><span data-stu-id="09e9a-127">-9084</span></span>  
  
-   <span data-ttu-id="09e9a-128">-230.75</span><span class="sxs-lookup"><span data-stu-id="09e9a-128">-230.75</span></span>  
  
-   <span data-ttu-id="09e9a-129">0.010503</span><span class="sxs-lookup"><span data-stu-id="09e9a-129">0.010503</span></span>  
  
-   <span data-ttu-id="09e9a-130">1.023e-10, qui est équivalent à 0.0000000001023</span><span class="sxs-lookup"><span data-stu-id="09e9a-130">1.023e-10, which is equivalent to 0.0000000001023</span></span>  
  
-   <span data-ttu-id="09e9a-131">0.097e5 ou 0.097e+5, qui est équivalent à 9700</span><span class="sxs-lookup"><span data-stu-id="09e9a-131">0.097e5 or 0.097e+5, which is equivalent to 9700</span></span>  
  
-   <span data-ttu-id="09e9a-132">1.0e-32, qui est équivalent à 0.00000000000000000000000000000001 (Cette valeur est valide car, dans ce cas, l'intégrale « 0 » est ignorée, 32 chiffres fractionnels significatifs.)</span><span class="sxs-lookup"><span data-stu-id="09e9a-132">1.0e-32, which is equivalent to 0.00000000000000000000000000000001 (This is valid because in this case, the integral '0' is ignored, 32 significant fractional digits.)</span></span>  
  
## <a name="invalid-values"></a><span data-ttu-id="09e9a-133">valeurs non valides ;</span><span class="sxs-lookup"><span data-stu-id="09e9a-133">Invalid Values</span></span>  
 <span data-ttu-id="09e9a-134">Les valeurs non valides dépendent du type de valeur.</span><span class="sxs-lookup"><span data-stu-id="09e9a-134">Invalid values depend on the kind of value.</span></span> <span data-ttu-id="09e9a-135">Une fraction décimale trop petite est interprétée comme un zéro (tous les chiffres significatifs sont perdus).</span><span class="sxs-lookup"><span data-stu-id="09e9a-135">A decimal fraction that is too small is interpreted as zero (all significant digits are lost).</span></span> <span data-ttu-id="09e9a-136">Un nombre entier ayant trop de chiffres significatifs génère des résultats inattendus.</span><span class="sxs-lookup"><span data-stu-id="09e9a-136">An integer that has too many significant digits causes unexpected results.</span></span> <span data-ttu-id="09e9a-137">JD Edwards EnterpriseOne ne génère pas toujours une condition d'erreur dans ce cas.</span><span class="sxs-lookup"><span data-stu-id="09e9a-137">JD Edwards EnterpriseOne does not always raise an error condition in this case.</span></span> <span data-ttu-id="09e9a-138">Un exposant trop grand ou trop petit est renvoyé comme valeur non valide.</span><span class="sxs-lookup"><span data-stu-id="09e9a-138">An exponent that is too large or too small also returns as an invalid value.</span></span>  
  
 <span data-ttu-id="09e9a-139">Exemples de **non valide** valeurs MATH_NUMERIC :</span><span class="sxs-lookup"><span data-stu-id="09e9a-139">Examples of **invalid** MATH_NUMERIC values:</span></span>  
  
-   <span data-ttu-id="09e9a-140">1034.00000000000000000000000000001023 (trop de chiffres significatifs)</span><span class="sxs-lookup"><span data-stu-id="09e9a-140">1034.00000000000000000000000000001023 - too many significant digits</span></span>  
  
-   <span data-ttu-id="09e9a-141">1.023e-64 (exposant trop petit)</span><span class="sxs-lookup"><span data-stu-id="09e9a-141">1.023e-64 - exponent too small</span></span>  
  
-   <span data-ttu-id="09e9a-142">0.00317e64 (exposant trop grand)</span><span class="sxs-lookup"><span data-stu-id="09e9a-142">0.00317e64 - exponent too large</span></span>  
  
 <span data-ttu-id="09e9a-143">Les caractères non numériques autres que ceux appropriés pour les signes et symboles décimaux génèrent une valeur non valide.</span><span class="sxs-lookup"><span data-stu-id="09e9a-143">Any non-numeric characters other than those appropriate for signs and decimal symbols result in an invalid value.</span></span>  
  
## <a name="exponents"></a><span data-ttu-id="09e9a-144">exposants ;</span><span class="sxs-lookup"><span data-stu-id="09e9a-144">Exponents</span></span>  
 <span data-ttu-id="09e9a-145">Les exposants fournis par le type MATH_NUMERIC de JD Edwards EnterpriseOne facilitent la saisie des valeurs.</span><span class="sxs-lookup"><span data-stu-id="09e9a-145">Exponents are provided by the JD Edwards EnterpriseOne MATH_NUMERIC as a convenience for entering values.</span></span> <span data-ttu-id="09e9a-146">Toutefois, la plupart des valeurs sont renvoyées sans exposant (avec les 32 chiffres significatifs visibles).</span><span class="sxs-lookup"><span data-stu-id="09e9a-146">However, most values return without exponents (with all 32 significant digits visible).</span></span>  
  
## <a name="precision-for-operations"></a><span data-ttu-id="09e9a-147">précision des opérations ;</span><span class="sxs-lookup"><span data-stu-id="09e9a-147">Precision for Operations</span></span>  
 <span data-ttu-id="09e9a-148">Si une opération entraîne une perte de précision, un arrondi est effectué.</span><span class="sxs-lookup"><span data-stu-id="09e9a-148">If an operation results in loss of precision, rounding occurs.</span></span> <span data-ttu-id="09e9a-149">Exemple :</span><span class="sxs-lookup"><span data-stu-id="09e9a-149">For example:</span></span>  
  
 <span data-ttu-id="09e9a-150">1.9e-31 / 10.0 = 0.00000000000000000000000000000002.</span><span class="sxs-lookup"><span data-stu-id="09e9a-150">1.9e-31 / 10.0 = 0.00000000000000000000000000000002.</span></span>  
  
 <span data-ttu-id="09e9a-151">1.9e-31 / 100.0 = 0.00000000000000000000000000000000</span><span class="sxs-lookup"><span data-stu-id="09e9a-151">1.9e-31 / 100.0 = 0.00000000000000000000000000000000</span></span>  
  
 <span data-ttu-id="09e9a-152">Dans d'autres cas, des résultats imprévisibles sont générés, comme lorsqu'une valeur positive très grande est multipliée par une autre.</span><span class="sxs-lookup"><span data-stu-id="09e9a-152">In other cases, unpredictable results occur, as when a very large positive value is multiplied by another.</span></span> <span data-ttu-id="09e9a-153">1.01e32 * 2.053e32 ne génère pas de résultats fiables et ne génère pas d’erreur.</span><span class="sxs-lookup"><span data-stu-id="09e9a-153">1.01e32 * 2.053e32 does not yield reliable results and does not raise an error.</span></span> <span data-ttu-id="09e9a-154">Pour la plupart des scénarios d'entreprise, ces plages ne sont pas dépassées.</span><span class="sxs-lookup"><span data-stu-id="09e9a-154">For most business scenarios, these ranges are not exceeded.</span></span>  
  
## <a name="currency"></a><span data-ttu-id="09e9a-155">Monétaire (Currency)</span><span class="sxs-lookup"><span data-stu-id="09e9a-155">Currency</span></span>  
 <span data-ttu-id="09e9a-156">Lorsqu'une fonction d'entreprise JD Edwards EnterpriseOne attend une valeur de devise, la fonction d'entreprise inclut toujours un paramètre distinct pour un code de devise à quatre caractères.</span><span class="sxs-lookup"><span data-stu-id="09e9a-156">When a JD Edwards EnterpriseOne business function expects a currency value, the business function always has a separate parameter for a four-character currency code.</span></span> <span data-ttu-id="09e9a-157">Il n'est pas nécessaire de transmettre ce code, sauf si vous utilisez une devise autre que celle par défaut configurée pour le système JD Edwards EnterpriseOne.</span><span class="sxs-lookup"><span data-stu-id="09e9a-157">It is not necessary to pass in this code unless you are using a currency other than the default configured for the JD Edwards EnterpriseOne system.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09e9a-158">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="09e9a-158">See Also</span></span>  
 [<span data-ttu-id="09e9a-159">Annexe b : les Types de données</span><span class="sxs-lookup"><span data-stu-id="09e9a-159">Appendix B: Data Types</span></span>](../core/appendix-b-data-types.md)