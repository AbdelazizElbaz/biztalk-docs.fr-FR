---
title: Base Types2 | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- JD Edwards EnterpriseOne adapters, data types
- adapters [JD Edwards EnterpriseOne adapters], data types
- data types, JD Edwards EnterpriseOne adapters
ms.assetid: 96a70f0d-f7f8-4e3b-9511-59b330910ead
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a7e5c47d8760e9743ec11a62598581d9d20b3e53
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="basic-types"></a><span data-ttu-id="c679f-102">Types de base</span><span class="sxs-lookup"><span data-stu-id="c679f-102">Basic Types</span></span>
<span data-ttu-id="c679f-103">L'adaptateur Microsoft BizTalk pour JD Edwards EnterpriseOne permet d'accéder uniquement aux fonctions commerciales de JD Edwards EnterpriseOne.</span><span class="sxs-lookup"><span data-stu-id="c679f-103">Microsoft BizTalk Adapter for JD Edwards EnterpriseOne provides access only to JD Edwards EnterpriseOne business functions.</span></span> <span data-ttu-id="c679f-104">Les métadonnées des fonctions commerciales sont lues à l'aide d'une interface de fonction commerciale et sont utilisées pour rechercher une liste des fonctions commerciales et des structures de données associées.</span><span class="sxs-lookup"><span data-stu-id="c679f-104">Business function metadata is read using a business function interface and used to find a list of business functions and associated data structures.</span></span> <span data-ttu-id="c679f-105">Dans tous les cas, les métadonnées sont fortement typées pour toutes les méthodes de fonctions commerciales.</span><span class="sxs-lookup"><span data-stu-id="c679f-105">Metadata is strongly typed in all cases for all business function methods.</span></span>  
  
 <span data-ttu-id="c679f-106">Toutes les méthodes de fonctions commerciales ont la même convention d’appel : trois paramètres dérivés du système et un pointeur vers une structure de données.</span><span class="sxs-lookup"><span data-stu-id="c679f-106">All business function methods have the same calling convention: three parameters that are system derived, and a pointer to a data structure.</span></span> <span data-ttu-id="c679f-107">Le tableau suivant présente la représentation des types de données d’entreprise (fonction).</span><span class="sxs-lookup"><span data-stu-id="c679f-107">The following table shows how business function data types are represented.</span></span>  
  
|<span data-ttu-id="c679f-108">Type de données JD Edwards EnterpriseOne</span><span class="sxs-lookup"><span data-stu-id="c679f-108">JD Edwards EnterpriseOne Data Type</span></span>|<span data-ttu-id="c679f-109"> Description</span><span class="sxs-lookup"><span data-stu-id="c679f-109">Description</span></span>|<span data-ttu-id="c679f-110">Conversion WDSL</span><span class="sxs-lookup"><span data-stu-id="c679f-110">WDSL Conversion</span></span>|  
|----------------------------------------|-----------------|---------------------|  
|<span data-ttu-id="c679f-111">char</span><span class="sxs-lookup"><span data-stu-id="c679f-111">char</span></span>|<span data-ttu-id="c679f-112">Chaîne de caractères.</span><span class="sxs-lookup"><span data-stu-id="c679f-112">Character string.</span></span>|<span data-ttu-id="c679f-113">xsd:string de 1</span><span class="sxs-lookup"><span data-stu-id="c679f-113">xsd:string of 1</span></span>|  
|<span data-ttu-id="c679f-114">int</span><span class="sxs-lookup"><span data-stu-id="c679f-114">int</span></span>|<span data-ttu-id="c679f-115">Entier court.</span><span class="sxs-lookup"><span data-stu-id="c679f-115">Short integer.</span></span>|<span data-ttu-id="c679f-116">xsd:short</span><span class="sxs-lookup"><span data-stu-id="c679f-116">xsd:short</span></span>|  
|<span data-ttu-id="c679f-117">long</span><span class="sxs-lookup"><span data-stu-id="c679f-117">long</span></span>|<span data-ttu-id="c679f-118">Entier long.</span><span class="sxs-lookup"><span data-stu-id="c679f-118">Long integer.</span></span>|<span data-ttu-id="c679f-119">xsd:short</span><span class="sxs-lookup"><span data-stu-id="c679f-119">xsd:short</span></span>|  
|<span data-ttu-id="c679f-120">Chaîne</span><span class="sxs-lookup"><span data-stu-id="c679f-120">String</span></span>|<span data-ttu-id="c679f-121">Consultez [la gestion des valeurs de chaîne](../core/handling-string-values2.md).</span><span class="sxs-lookup"><span data-stu-id="c679f-121">See [Handling String Values](../core/handling-string-values2.md).</span></span>|<span data-ttu-id="c679f-122">xsd:string</span><span class="sxs-lookup"><span data-stu-id="c679f-122">xsd:string</span></span>|  
|<span data-ttu-id="c679f-123">JDEDATE</span><span class="sxs-lookup"><span data-stu-id="c679f-123">JDEDATE</span></span>|<span data-ttu-id="c679f-124">Implémentation spéciale de dates.</span><span class="sxs-lookup"><span data-stu-id="c679f-124">Special implementation of dates.</span></span>|<span data-ttu-id="c679f-125">xsd:date</span><span class="sxs-lookup"><span data-stu-id="c679f-125">xsd:date</span></span>|  
|<span data-ttu-id="c679f-126">MATH_NUMERIC</span><span class="sxs-lookup"><span data-stu-id="c679f-126">MATH_NUMERIC</span></span>|<span data-ttu-id="c679f-127">Implémentation spéciale de nombres à virgule flottante, y compris les valeurs de devises.</span><span class="sxs-lookup"><span data-stu-id="c679f-127">Special implementation of floating point numbers, including currency values.</span></span>|<span data-ttu-id="c679f-128">XSD : String de 32</span><span class="sxs-lookup"><span data-stu-id="c679f-128">xsd:string of 32</span></span>|  
|<span data-ttu-id="c679f-129">Byte</span><span class="sxs-lookup"><span data-stu-id="c679f-129">Byte</span></span>|<span data-ttu-id="c679f-130">Caractère non signé unique.</span><span class="sxs-lookup"><span data-stu-id="c679f-130">Single unsigned character.</span></span>|<span data-ttu-id="c679f-131">xsd:string de 1</span><span class="sxs-lookup"><span data-stu-id="c679f-131">xsd:string of 1</span></span>|  
|<span data-ttu-id="c679f-132">JDEUTIME</span><span class="sxs-lookup"><span data-stu-id="c679f-132">JDEUTIME</span></span>|<span data-ttu-id="c679f-133">Inclut les composants de date et heure.</span><span class="sxs-lookup"><span data-stu-id="c679f-133">Includes both date and time components.</span></span><br /><br /> <span data-ttu-id="c679f-134">Le type de données enregistre toutes les dates/heures et effectue tous les calculs de date/heure en temps universel coordonné (UTC).</span><span class="sxs-lookup"><span data-stu-id="c679f-134">The data type stores all dates/times and performs all date/time calculations in Coordinated Universal Time (UTC).</span></span>|<span data-ttu-id="c679f-135">xsd:dateTime</span><span class="sxs-lookup"><span data-stu-id="c679f-135">xsd:dateTime</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c679f-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c679f-136">See Also</span></span>  
 <span data-ttu-id="c679f-137">[À l’aide du Type MATH_NUMERIC](../core/using-the-math-numeric-type1.md) </span><span class="sxs-lookup"><span data-stu-id="c679f-137">[Using the MATH_NUMERIC Type](../core/using-the-math-numeric-type1.md) </span></span>  
 <span data-ttu-id="c679f-138">[Gestion des valeurs de chaîne](../core/handling-string-values2.md) </span><span class="sxs-lookup"><span data-stu-id="c679f-138">[Handling String Values](../core/handling-string-values2.md) </span></span>  
 [<span data-ttu-id="c679f-139">Annexe b : les Types de données</span><span class="sxs-lookup"><span data-stu-id="c679f-139">Appendix B: Data Types</span></span>](../core/appendix-b-data-types.md)