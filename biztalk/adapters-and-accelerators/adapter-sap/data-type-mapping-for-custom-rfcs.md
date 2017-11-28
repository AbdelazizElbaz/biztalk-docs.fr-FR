---
title: "Mappage pour les RFC personnalisés du Type de données | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: custom RFCs, data type mapping
ms.assetid: 33539a5a-bdfc-423f-8026-436f69a20c70
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cac254734a35658e3aa635b086f765e8f06494a7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="data-type-mapping-for-custom-rfcs"></a><span data-ttu-id="cb276-102">Mappage de Type de données pour les RFC personnalisés</span><span class="sxs-lookup"><span data-stu-id="cb276-102">Data Type Mapping for Custom RFCs</span></span>
<span data-ttu-id="cb276-103">Le tableau suivant fournit des informations sur les types de données SAP et comment ils sont mappés aux types de données .NET pour le document RFC Z_EXTRACT_DATA_OO.</span><span class="sxs-lookup"><span data-stu-id="cb276-103">The following table provides information about SAP data types and how they are mapped to .NET data types for the Z_EXTRACT_DATA_OO RFC.</span></span> <span data-ttu-id="cb276-104">Ce document RFC personnalisée est utilisée par le [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cb276-104">This custom RFC is used by the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)].</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cb276-105">Pour le Z_EXECUTE_SAP_QUERY, qui est utilisé par le [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] pour exécuter la commande EXECQUERY, tous les types de données SAP sont convertis en types de chaîne .NET.</span><span class="sxs-lookup"><span data-stu-id="cb276-105">For the Z_EXECUTE_SAP_QUERY, which is used by the [!INCLUDE[adoprovidersapshort](../../includes/adoprovidersapshort-md.md)] to execute the EXECQUERY command, all SAP data types are converted to .NET string types.</span></span>  
  
|<span data-ttu-id="cb276-106">Type de données SAP</span><span class="sxs-lookup"><span data-stu-id="cb276-106">SAP Data Type</span></span>|<span data-ttu-id="cb276-107">Type de données .NET</span><span class="sxs-lookup"><span data-stu-id="cb276-107">.NET Data Type</span></span>|  
|-------------------|--------------------|  
|<span data-ttu-id="cb276-108">ACCP</span><span class="sxs-lookup"><span data-stu-id="cb276-108">ACCP</span></span>|<span data-ttu-id="cb276-109">-Int32</span><span class="sxs-lookup"><span data-stu-id="cb276-109">-   Int32</span></span><br /><span data-ttu-id="cb276-110">-Chaîne, si **disabledatavalidation** option est définie dans l’instruction SELECT ou EXEC.</span><span class="sxs-lookup"><span data-stu-id="cb276-110">-   String, if **disabledatavalidation** option is set in the SELECT or EXEC statement.</span></span>|  
|<span data-ttu-id="cb276-111">CHAR</span><span class="sxs-lookup"><span data-stu-id="cb276-111">CHAR</span></span>|<span data-ttu-id="cb276-112">Chaîne</span><span class="sxs-lookup"><span data-stu-id="cb276-112">String</span></span>|  
|<span data-ttu-id="cb276-113">CLNT</span><span class="sxs-lookup"><span data-stu-id="cb276-113">CLNT</span></span>|<span data-ttu-id="cb276-114">Chaîne</span><span class="sxs-lookup"><span data-stu-id="cb276-114">String</span></span>|  
|<span data-ttu-id="cb276-115">CUKY</span><span class="sxs-lookup"><span data-stu-id="cb276-115">CUKY</span></span>|<span data-ttu-id="cb276-116">Chaîne</span><span class="sxs-lookup"><span data-stu-id="cb276-116">String</span></span>|  
|<span data-ttu-id="cb276-117">DR</span><span class="sxs-lookup"><span data-stu-id="cb276-117">CURR</span></span>|<span data-ttu-id="cb276-118">Decimal, si la précision inférieure ou égale à 28</span><span class="sxs-lookup"><span data-stu-id="cb276-118">Decimal, if precision less than or equal to 28</span></span><br /><br /> <span data-ttu-id="cb276-119">Chaîne, si la précision supérieure à 28</span><span class="sxs-lookup"><span data-stu-id="cb276-119">String, if precision greater than 28</span></span>|  
|<span data-ttu-id="cb276-120">FICHIERS DAT</span><span class="sxs-lookup"><span data-stu-id="cb276-120">DATS</span></span>|<span data-ttu-id="cb276-121">-DateTime</span><span class="sxs-lookup"><span data-stu-id="cb276-121">-   DateTime</span></span><br /><span data-ttu-id="cb276-122">-Chaîne, si **disabledatavalidation** option est définie dans l’instruction SELECT ou EXEC.</span><span class="sxs-lookup"><span data-stu-id="cb276-122">-   String, if **disabledatavalidation** option is set in the SELECT or EXEC statement.</span></span>|  
|<span data-ttu-id="cb276-123">DEC</span><span class="sxs-lookup"><span data-stu-id="cb276-123">DEC</span></span>|<span data-ttu-id="cb276-124">Décimal</span><span class="sxs-lookup"><span data-stu-id="cb276-124">Decimal</span></span>|  
|<span data-ttu-id="cb276-125">FLTP</span><span class="sxs-lookup"><span data-stu-id="cb276-125">FLTP</span></span>|<span data-ttu-id="cb276-126">Double</span><span class="sxs-lookup"><span data-stu-id="cb276-126">Double</span></span>|  
|<span data-ttu-id="cb276-127">INT1</span><span class="sxs-lookup"><span data-stu-id="cb276-127">INT1</span></span>|<span data-ttu-id="cb276-128">Byte</span><span class="sxs-lookup"><span data-stu-id="cb276-128">Byte</span></span>|  
|<span data-ttu-id="cb276-129">INT2</span><span class="sxs-lookup"><span data-stu-id="cb276-129">INT2</span></span>|<span data-ttu-id="cb276-130">Int16</span><span class="sxs-lookup"><span data-stu-id="cb276-130">Int16</span></span>|  
|<span data-ttu-id="cb276-131">INT4</span><span class="sxs-lookup"><span data-stu-id="cb276-131">INT4</span></span>|<span data-ttu-id="cb276-132">Int32</span><span class="sxs-lookup"><span data-stu-id="cb276-132">Int32</span></span>|  
|<span data-ttu-id="cb276-133">LANG</span><span class="sxs-lookup"><span data-stu-id="cb276-133">LANG</span></span>|<span data-ttu-id="cb276-134">Chaîne</span><span class="sxs-lookup"><span data-stu-id="cb276-134">String</span></span>|  
|<span data-ttu-id="cb276-135">NUMC</span><span class="sxs-lookup"><span data-stu-id="cb276-135">NUMC</span></span>|<span data-ttu-id="cb276-136">-Int32, si le champ longueur est inférieure ou égale à 9</span><span class="sxs-lookup"><span data-stu-id="cb276-136">-   Int32, if field length less than or equal to 9</span></span><br /><span data-ttu-id="cb276-137">-Int64, si le champ longueur supérieure à 9 et inférieur ou égal à 19</span><span class="sxs-lookup"><span data-stu-id="cb276-137">-   Int64, if field length greater than 9 and less than or equal to 19</span></span><br /><span data-ttu-id="cb276-138">-Chaîne, si elle est supérieure à 19</span><span class="sxs-lookup"><span data-stu-id="cb276-138">-   String, if greater than 19</span></span><br /><span data-ttu-id="cb276-139">-Chaîne, si **disabledatavalidation** option est définie dans l’instruction SELECT ou EXEC.</span><span class="sxs-lookup"><span data-stu-id="cb276-139">-   String, if **disabledatavalidation** option is set in the SELECT or EXEC statement.</span></span>|  
|<span data-ttu-id="cb276-140">PREC</span><span class="sxs-lookup"><span data-stu-id="cb276-140">PREC</span></span>|<span data-ttu-id="cb276-141">Int16</span><span class="sxs-lookup"><span data-stu-id="cb276-141">Int16</span></span>|  
|<span data-ttu-id="cb276-142">QUAN</span><span class="sxs-lookup"><span data-stu-id="cb276-142">QUAN</span></span>|<span data-ttu-id="cb276-143">Décimal</span><span class="sxs-lookup"><span data-stu-id="cb276-143">Decimal</span></span>|  
|<span data-ttu-id="cb276-144">RAW</span><span class="sxs-lookup"><span data-stu-id="cb276-144">RAW</span></span>|<span data-ttu-id="cb276-145">Byte]</span><span class="sxs-lookup"><span data-stu-id="cb276-145">Byte []</span></span>|  
|<span data-ttu-id="cb276-146">RSTR</span><span class="sxs-lookup"><span data-stu-id="cb276-146">RSTR</span></span>|<span data-ttu-id="cb276-147">Byte]</span><span class="sxs-lookup"><span data-stu-id="cb276-147">Byte []</span></span>|  
|<span data-ttu-id="cb276-148">SSTR</span><span class="sxs-lookup"><span data-stu-id="cb276-148">SSTR</span></span>|<span data-ttu-id="cb276-149">Chaîne</span><span class="sxs-lookup"><span data-stu-id="cb276-149">String</span></span>|  
|<span data-ttu-id="cb276-150">STRG</span><span class="sxs-lookup"><span data-stu-id="cb276-150">STRG</span></span>|<span data-ttu-id="cb276-151">Chaîne</span><span class="sxs-lookup"><span data-stu-id="cb276-151">String</span></span>|  
|<span data-ttu-id="cb276-152">TIM</span><span class="sxs-lookup"><span data-stu-id="cb276-152">TIMS</span></span>|<span data-ttu-id="cb276-153">-TimeSpan</span><span class="sxs-lookup"><span data-stu-id="cb276-153">-   TimeSpan</span></span><br /><span data-ttu-id="cb276-154">-Chaîne, si **disabledatavalidation** option est définie dans l’instruction SELECT ou EXEC.</span><span class="sxs-lookup"><span data-stu-id="cb276-154">-   String, if **disabledatavalidation** option is set in the SELECT or EXEC statement.</span></span>|  
|<span data-ttu-id="cb276-155">UNITÉ</span><span class="sxs-lookup"><span data-stu-id="cb276-155">UNIT</span></span>|<span data-ttu-id="cb276-156">Chaîne</span><span class="sxs-lookup"><span data-stu-id="cb276-156">String</span></span>|  
|<span data-ttu-id="cb276-157">LCHR</span><span class="sxs-lookup"><span data-stu-id="cb276-157">LCHR</span></span>|<span data-ttu-id="cb276-158">Chaîne</span><span class="sxs-lookup"><span data-stu-id="cb276-158">String</span></span>|  
|<span data-ttu-id="cb276-159">LRAW</span><span class="sxs-lookup"><span data-stu-id="cb276-159">LRAW</span></span>|<span data-ttu-id="cb276-160">Byte]</span><span class="sxs-lookup"><span data-stu-id="cb276-160">Byte []</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cb276-161">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cb276-161">See Also</span></span>  
 [<span data-ttu-id="cb276-162">Messages et des schémas de Message pour l’adaptateur BizTalk pour mySAP Business Suite</span><span class="sxs-lookup"><span data-stu-id="cb276-162">Messages and Message Schemas for BizTalk Adapter for mySAP Business Suite</span></span>](../../adapters-and-accelerators/adapter-sap/messages-and-message-schemas-for-biztalk-adapter-for-mysap-business-suite.md)