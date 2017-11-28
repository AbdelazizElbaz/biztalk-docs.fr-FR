---
title: Base Types1 | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- JD Edwards OneWorld adapters, data types
- JD Edwards OneWorld adapters, business functions
- .NET Framework, mapping [JD Edwards OneWorld adapters]
- adapters [JD Edwards OneWorld adapters], data types
- adapters [JD Edwards OneWorld adapters], .NET Framework
- JD Edwards OneWorld adapters, .NET Framework
- adapters [JD Edwards OneWorld adapters], business functions
ms.assetid: d306ea1b-fb74-4fa3-9681-405252928df1
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e90cda6259567adf5236d0c28e576900d8b25271
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="basic-types"></a><span data-ttu-id="52b85-102">Types de base</span><span class="sxs-lookup"><span data-stu-id="52b85-102">Basic Types</span></span>
<span data-ttu-id="52b85-103">L'adaptateur Microsoft BizTalk pour Edwards OneWorld permet d'accéder uniquement aux fonctions commerciales de JD Edwards OneWorld.</span><span class="sxs-lookup"><span data-stu-id="52b85-103">Microsoft BizTalk Adapter for JD Edwards OneWorld provides access only to JD Edwards OneWorld business functions.</span></span> <span data-ttu-id="52b85-104">Les métadonnées des fonctions commerciales sont lues à l'aide d'une interface de fonction commerciale et sont utilisées pour rechercher une liste des fonctions commerciales et des structures de données associées.</span><span class="sxs-lookup"><span data-stu-id="52b85-104">Business function metadata is read using a business function interface and used to find a list of business functions and associated data structures.</span></span> <span data-ttu-id="52b85-105">Dans tous les cas, les métadonnées sont fortement typées pour toutes les méthodes de fonctions commerciales.</span><span class="sxs-lookup"><span data-stu-id="52b85-105">Metadata is strongly typed in all cases for all business function methods.</span></span>  
  
 <span data-ttu-id="52b85-106">Toutes les méthodes de fonctions commerciales ont la même convention d’appel : trois paramètres dérivés du système et un pointeur vers une structure de données.</span><span class="sxs-lookup"><span data-stu-id="52b85-106">All business function methods have the same calling convention: three parameters that are system derived, and a pointer to a data structure.</span></span> <span data-ttu-id="52b85-107">Le tableau suivant illustre la représentation des types de données des fonctions commerciales.</span><span class="sxs-lookup"><span data-stu-id="52b85-107">The following table shows how the business function data types are represented.</span></span>  
  
 <span data-ttu-id="52b85-108">**Type de données métiers (fonction)**</span><span class="sxs-lookup"><span data-stu-id="52b85-108">**Business function data types**</span></span>  
  
|<span data-ttu-id="52b85-109">Type de données JD Edwards OneWorld</span><span class="sxs-lookup"><span data-stu-id="52b85-109">JD Edwards OneWorld Data Type</span></span>|<span data-ttu-id="52b85-110"> Description</span><span class="sxs-lookup"><span data-stu-id="52b85-110">Description</span></span>|<span data-ttu-id="52b85-111">Conversion WDSL</span><span class="sxs-lookup"><span data-stu-id="52b85-111">WDSL Conversion</span></span>|  
|-----------------------------------|-----------------|---------------------|  
|<span data-ttu-id="52b85-112">char</span><span class="sxs-lookup"><span data-stu-id="52b85-112">char</span></span>|<span data-ttu-id="52b85-113">Chaîne de caractères.</span><span class="sxs-lookup"><span data-stu-id="52b85-113">Character string.</span></span>|<span data-ttu-id="52b85-114">xsd:string de 1</span><span class="sxs-lookup"><span data-stu-id="52b85-114">xsd:string of 1</span></span>|  
|<span data-ttu-id="52b85-115">int</span><span class="sxs-lookup"><span data-stu-id="52b85-115">int</span></span>|<span data-ttu-id="52b85-116">Entier court.</span><span class="sxs-lookup"><span data-stu-id="52b85-116">Short integer.</span></span>|<span data-ttu-id="52b85-117">xsd:short</span><span class="sxs-lookup"><span data-stu-id="52b85-117">xsd:short</span></span>|  
|<span data-ttu-id="52b85-118">long</span><span class="sxs-lookup"><span data-stu-id="52b85-118">long</span></span>|<span data-ttu-id="52b85-119">Entier long.</span><span class="sxs-lookup"><span data-stu-id="52b85-119">Long integer.</span></span>|<span data-ttu-id="52b85-120">xsd:short</span><span class="sxs-lookup"><span data-stu-id="52b85-120">xsd:short</span></span>|  
|<span data-ttu-id="52b85-121">Chaîne</span><span class="sxs-lookup"><span data-stu-id="52b85-121">String</span></span>|<span data-ttu-id="52b85-122">Consultez [la gestion des valeurs de chaîne](../core/handling-string-values1.md).</span><span class="sxs-lookup"><span data-stu-id="52b85-122">See [Handling String Values](../core/handling-string-values1.md).</span></span>|<span data-ttu-id="52b85-123">xsd:string</span><span class="sxs-lookup"><span data-stu-id="52b85-123">xsd:string</span></span>|  
|<span data-ttu-id="52b85-124">JDEDATE</span><span class="sxs-lookup"><span data-stu-id="52b85-124">JDEDATE</span></span>|<span data-ttu-id="52b85-125">Implémentation spéciale de dates.</span><span class="sxs-lookup"><span data-stu-id="52b85-125">Special implementation of dates.</span></span>|<span data-ttu-id="52b85-126">xsd:date</span><span class="sxs-lookup"><span data-stu-id="52b85-126">xsd:date</span></span>|  
|<span data-ttu-id="52b85-127">MATH_NUMERIC</span><span class="sxs-lookup"><span data-stu-id="52b85-127">MATH_NUMERIC</span></span>|<span data-ttu-id="52b85-128">Implémentation spéciale de nombres à virgule flottante, y compris les valeurs de devises.</span><span class="sxs-lookup"><span data-stu-id="52b85-128">Special implementation of floating point numbers, including currency values.</span></span>|<span data-ttu-id="52b85-129">XSD : String de 32</span><span class="sxs-lookup"><span data-stu-id="52b85-129">xsd:string of 32</span></span>|  
|<span data-ttu-id="52b85-130">Byte</span><span class="sxs-lookup"><span data-stu-id="52b85-130">Byte</span></span>|<span data-ttu-id="52b85-131">Caractère non signé unique.</span><span class="sxs-lookup"><span data-stu-id="52b85-131">Single unsigned character.</span></span>|<span data-ttu-id="52b85-132">xsd:string de 1</span><span class="sxs-lookup"><span data-stu-id="52b85-132">xsd:string of 1</span></span>|  
  
 <span data-ttu-id="52b85-133">Le tableau suivant présente la liste des types de base présents dans JD Edwards OneWorld et la manière dont ceux-ci sont mappés à Microsoft .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="52b85-133">The following table contains the list of basic types in JD Edwards OneWorld and how they map to the Microsoft .NET Framework.</span></span>  
  
 <span data-ttu-id="52b85-134">**Types de base et comment ils sont mappés avec Microsoft .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="52b85-134">**Basic types and how they map to the Microsoft .NET Framework**</span></span>  
  
|<span data-ttu-id="52b85-135">JD Edwards OneWorld XE</span><span class="sxs-lookup"><span data-stu-id="52b85-135">JD Edwards OneWorld XE</span></span>|<span data-ttu-id="52b85-136">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="52b85-136">.NET Framework</span></span>|  
|----------------------------|--------------------|  
|<span data-ttu-id="52b85-137">char</span><span class="sxs-lookup"><span data-stu-id="52b85-137">char</span></span>|<span data-ttu-id="52b85-138">Chaîne</span><span class="sxs-lookup"><span data-stu-id="52b85-138">String</span></span>|  
|<span data-ttu-id="52b85-139">int</span><span class="sxs-lookup"><span data-stu-id="52b85-139">int</span></span>|<span data-ttu-id="52b85-140">Short</span><span class="sxs-lookup"><span data-stu-id="52b85-140">Short</span></span>|  
|<span data-ttu-id="52b85-141">long</span><span class="sxs-lookup"><span data-stu-id="52b85-141">long</span></span>|<span data-ttu-id="52b85-142">Short</span><span class="sxs-lookup"><span data-stu-id="52b85-142">Short</span></span>|  
|<span data-ttu-id="52b85-143">Chaîne</span><span class="sxs-lookup"><span data-stu-id="52b85-143">String</span></span>|<span data-ttu-id="52b85-144">Chaîne</span><span class="sxs-lookup"><span data-stu-id="52b85-144">String</span></span>|  
|<span data-ttu-id="52b85-145">JDEDATE</span><span class="sxs-lookup"><span data-stu-id="52b85-145">JDEDATE</span></span>|<span data-ttu-id="52b85-146">System.DateTime</span><span class="sxs-lookup"><span data-stu-id="52b85-146">System.DateTime</span></span>|  
|<span data-ttu-id="52b85-147">MATH_NUMERIC</span><span class="sxs-lookup"><span data-stu-id="52b85-147">MATH_NUMERIC</span></span>|<span data-ttu-id="52b85-148">Chaîne</span><span class="sxs-lookup"><span data-stu-id="52b85-148">String</span></span>|  
|<span data-ttu-id="52b85-149">Byte</span><span class="sxs-lookup"><span data-stu-id="52b85-149">Byte</span></span>|<span data-ttu-id="52b85-150">Chaîne</span><span class="sxs-lookup"><span data-stu-id="52b85-150">String</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="52b85-151">S'il n'existe qu'un argument et que l'argument de retour est void, l'espace réservé est remplacé par la classe, et la partie sortante devient la valeur de retour.</span><span class="sxs-lookup"><span data-stu-id="52b85-151">If there is only one argument, and the return argument is void, the holder is replaced by the class, and the out portion becomes the return value.</span></span> <span data-ttu-id="52b85-152">Exemple :</span><span class="sxs-lookup"><span data-stu-id="52b85-152">For example:</span></span>  
  
```  
org.apache.axis.holders.DateHolder becomes a java.util.Date.   
```  
  
 <span data-ttu-id="52b85-153">Voici un exemple de signatures de méthode :</span><span class="sxs-lookup"><span data-stu-id="52b85-153">The following is an example of method signatures:</span></span>  
  
```  
void testDate1(org.apache.axis.holders.DateHolder date1  
        org.apache.axis.holders.DateHolder date2);  
  
java.util.Date testDate2(java.util.Date date);  
```  
  
## <a name="character-limited-strings"></a><span data-ttu-id="52b85-154">Nombre de caractères limité dans les chaînes</span><span class="sxs-lookup"><span data-stu-id="52b85-154">Character-Limited Strings</span></span>  
 <span data-ttu-id="52b85-155">Dans JD Edwards OneWorld, le nombre de caractères de certaines chaînes est limité.</span><span class="sxs-lookup"><span data-stu-id="52b85-155">In JD Edwards OneWorld, some strings are character-limited.</span></span> <span data-ttu-id="52b85-156">Tout caractère supplémentaire engendre une erreur.</span><span class="sxs-lookup"><span data-stu-id="52b85-156">Any extra character causes an error.</span></span> <span data-ttu-id="52b85-157">Pour voir la limite de caractères des chaînes, vous devez utiliser l'assistant Adaptateur Microsoft.</span><span class="sxs-lookup"><span data-stu-id="52b85-157">To see the limit of characters in the strings, you can use the Microsoft Adapter Wizard.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52b85-158">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="52b85-158">See Also</span></span>  
 <span data-ttu-id="52b85-159">[À l’aide du Type MATH_NUMERIC](../core/using-the-math-numeric-type2.md) </span><span class="sxs-lookup"><span data-stu-id="52b85-159">[Using the MATH_NUMERIC Type](../core/using-the-math-numeric-type2.md) </span></span>  
 <span data-ttu-id="52b85-160">[Gestion des valeurs de chaîne](../core/handling-string-values1.md) </span><span class="sxs-lookup"><span data-stu-id="52b85-160">[Handling String Values](../core/handling-string-values1.md) </span></span>  
 [<span data-ttu-id="52b85-161">Annexe a : les Types de données</span><span class="sxs-lookup"><span data-stu-id="52b85-161">Appendix A: Data Types</span></span>](../core/appendix-a-data-types.md)