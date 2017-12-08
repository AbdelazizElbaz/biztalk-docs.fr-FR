---
title: "Classe SiebelParameter dans l’adaptateur Siebel | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SiebelParameter
- Data Provider for Siebel, SiebelParameter
- SiebelParameter, supported properties and methods
ms.assetid: 1dcb72c7-a470-4609-8aba-a5c8ad5f3ac9
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 27df4b207b23cd04f7d29a2a18ec4ab032836e5b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="siebelparameter-class-in-the-siebel-adapter"></a><span data-ttu-id="abe5c-102">Classe SiebelParameter dans l’adaptateur Siebel</span><span class="sxs-lookup"><span data-stu-id="abe5c-102">SiebelParameter class in the Siebel adapter</span></span>
<span data-ttu-id="abe5c-103">Le [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] fournit un `DbParameter` mise en œuvre pour permettre à un client ADO.NET spécifier des paramètres pour une commande particulière.</span><span class="sxs-lookup"><span data-stu-id="abe5c-103">The [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] provides a `DbParameter` implementation to enable an ADO.NET client to specify parameters for a particular command.</span></span> <span data-ttu-id="abe5c-104">À l’aide d’une instance de la `System.Data.Common.DbCommand` classe de la [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)], un programme client peut obtenir une instance de la `System.Data.Common.DbParameter` classe.</span><span class="sxs-lookup"><span data-stu-id="abe5c-104">Using an instance of the `System.Data.Common.DbCommand` class of the [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)], a client program can obtain an instance of the `System.Data.Common.DbParameter` class.</span></span>  
  
```  
//In this example, command is an instance of DbCommand  
DbParameter param = command.CreateParameter();  
```  
  
 <span data-ttu-id="abe5c-105">L’approche suivante peut également être utilisée :</span><span class="sxs-lookup"><span data-stu-id="abe5c-105">Alternatively, the following approach can be used:</span></span>  
  
```  
  
//Here command is an instance of SiebelCommand  
SiebelParameter param = (SiebelParameter) command.CreateParameter();                  
param.ParameterName = "@Time";  
```  
  
 <span data-ttu-id="abe5c-106">Le `SiebelParameter` hérite de la classe `DbParameter`.</span><span class="sxs-lookup"><span data-stu-id="abe5c-106">The `SiebelParameter` class inherits from `DbParameter`.</span></span>  <span data-ttu-id="abe5c-107">Il existe dans l’espace de noms `Microsoft.Data.SiebelClient`.</span><span class="sxs-lookup"><span data-stu-id="abe5c-107">It exists in the namespace `Microsoft.Data.SiebelClient`.</span></span>  
  
## <a name="supported-properties"></a><span data-ttu-id="abe5c-108">Propriétés prises en charge</span><span class="sxs-lookup"><span data-stu-id="abe5c-108">Supported Properties</span></span>  
 <span data-ttu-id="abe5c-109">Le `SiebelParameter` classe prend en charge les éléments suivants `DbParameter` *public* propriétés :</span><span class="sxs-lookup"><span data-stu-id="abe5c-109">The `SiebelParameter` class supports the following `DbParameter`*public* properties:</span></span>  
  
|<span data-ttu-id="abe5c-110">Nom</span><span class="sxs-lookup"><span data-stu-id="abe5c-110">Name</span></span>|<span data-ttu-id="abe5c-111">Get/Set.</span><span class="sxs-lookup"><span data-stu-id="abe5c-111">Get/Set</span></span>|<span data-ttu-id="abe5c-112"> Description</span><span class="sxs-lookup"><span data-stu-id="abe5c-112">Description</span></span>|  
|----------|--------------|-----------------|  
|<span data-ttu-id="abe5c-113">**DbType**</span><span class="sxs-lookup"><span data-stu-id="abe5c-113">**DbType**</span></span>|<span data-ttu-id="abe5c-114">Get et Set</span><span class="sxs-lookup"><span data-stu-id="abe5c-114">Get and Set</span></span>|<span data-ttu-id="abe5c-115">Type de données du paramètre.</span><span class="sxs-lookup"><span data-stu-id="abe5c-115">Data type of the parameter.</span></span> <span data-ttu-id="abe5c-116">Consultez [base données Siebel Types](../../adapters-and-accelerators/adapter-siebel/basic-siebel-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="abe5c-116">See [Basic Siebel Data Types](../../adapters-and-accelerators/adapter-siebel/basic-siebel-data-types.md).</span></span>|  
|<span data-ttu-id="abe5c-117">**Direction**</span><span class="sxs-lookup"><span data-stu-id="abe5c-117">**Direction**</span></span>|<span data-ttu-id="abe5c-118">Get et Set</span><span class="sxs-lookup"><span data-stu-id="abe5c-118">Get and Set</span></span>|<span data-ttu-id="abe5c-119">Les valeurs suivantes sont prises en charge :</span><span class="sxs-lookup"><span data-stu-id="abe5c-119">The following values are supported:</span></span><br /><br /> -                     `ParameterDirection.Input`<br /><br /> -                     `ParameterDirection.Output`<br /><br /> -                     `ParameterDirection.InputOutput`|  
|<span data-ttu-id="abe5c-120">**IsNullable**</span><span class="sxs-lookup"><span data-stu-id="abe5c-120">**IsNullable**</span></span>|<span data-ttu-id="abe5c-121">Get et Set</span><span class="sxs-lookup"><span data-stu-id="abe5c-121">Get and Set</span></span>|<span data-ttu-id="abe5c-122">La propriété n’est pas prise en charge et lève une exception si elle est appelée.</span><span class="sxs-lookup"><span data-stu-id="abe5c-122">The property is not supported, and will throw an exception if called.</span></span>|  
|<span data-ttu-id="abe5c-123">**ParameterName**</span><span class="sxs-lookup"><span data-stu-id="abe5c-123">**ParameterName**</span></span>|<span data-ttu-id="abe5c-124">Get et Set</span><span class="sxs-lookup"><span data-stu-id="abe5c-124">Get and Set</span></span>|<span data-ttu-id="abe5c-125">Le [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] prend en charge cette propriété pour un client ADO.NET spécifier le nom du paramètre.</span><span class="sxs-lookup"><span data-stu-id="abe5c-125">The [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] supports this property for an ADO.NET client to specify the parameter name.</span></span>|  
|<span data-ttu-id="abe5c-126">**Valeur**</span><span class="sxs-lookup"><span data-stu-id="abe5c-126">**Value**</span></span>|<span data-ttu-id="abe5c-127">Get et Set</span><span class="sxs-lookup"><span data-stu-id="abe5c-127">Get and Set</span></span>|<span data-ttu-id="abe5c-128">La [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] représente des valeurs de paramètre en tant que chaînes.</span><span class="sxs-lookup"><span data-stu-id="abe5c-128">The [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] represents parameter values as strings.</span></span>|  
  
###  <a name="BKMK_Datatypes"></a><span data-ttu-id="abe5c-129">Types de données pris en charge</span><span class="sxs-lookup"><span data-stu-id="abe5c-129">Supported Data Types</span></span>  
 <span data-ttu-id="abe5c-130">Le tableau suivant récapitule la simple Siebel champ types [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] prend en charge.</span><span class="sxs-lookup"><span data-stu-id="abe5c-130">The following table summarizes the simple Siebel field types that [!INCLUDE[adoprovidersiebelshort](../../includes/adoprovidersiebelshort-md.md)] supports.</span></span> <span data-ttu-id="abe5c-131">Des explications plus détaillées, consultez [des Types de données Siebel base](../../adapters-and-accelerators/adapter-siebel/basic-siebel-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="abe5c-131">For more detailed coverage, see [Basic Siebel Data Types](../../adapters-and-accelerators/adapter-siebel/basic-siebel-data-types.md).</span></span>  
  
|<span data-ttu-id="abe5c-132">Type de champ de Siebel</span><span class="sxs-lookup"><span data-stu-id="abe5c-132">Siebel Field Type</span></span>|<span data-ttu-id="abe5c-133">Type .NET</span><span class="sxs-lookup"><span data-stu-id="abe5c-133">.NET Type</span></span>|<span data-ttu-id="abe5c-134">Type de schéma XML</span><span class="sxs-lookup"><span data-stu-id="abe5c-134">XML Schema Type</span></span>|  
|-----------------------|---------------|---------------------|  
|<span data-ttu-id="abe5c-135">DTYPE_BOOL</span><span class="sxs-lookup"><span data-stu-id="abe5c-135">DTYPE_BOOL</span></span>|<span data-ttu-id="abe5c-136">Booléen</span><span class="sxs-lookup"><span data-stu-id="abe5c-136">Boolean</span></span>|<span data-ttu-id="abe5c-137">xsd:boolean</span><span class="sxs-lookup"><span data-stu-id="abe5c-137">xsd:boolean</span></span>|  
|<span data-ttu-id="abe5c-138">DTYPE_CURRENCY</span><span class="sxs-lookup"><span data-stu-id="abe5c-138">DTYPE_CURRENCY</span></span>|<span data-ttu-id="abe5c-139">Décimal</span><span class="sxs-lookup"><span data-stu-id="abe5c-139">Decimal</span></span>|<span data-ttu-id="abe5c-140">xsd:decimal</span><span class="sxs-lookup"><span data-stu-id="abe5c-140">xsd:decimal</span></span>|  
|<span data-ttu-id="abe5c-141">DTYPE_DATE</span><span class="sxs-lookup"><span data-stu-id="abe5c-141">DTYPE_DATE</span></span>|<span data-ttu-id="abe5c-142">DateTime</span><span class="sxs-lookup"><span data-stu-id="abe5c-142">DateTime</span></span>|<span data-ttu-id="abe5c-143">xsd:dateTime</span><span class="sxs-lookup"><span data-stu-id="abe5c-143">xsd:dateTime</span></span>|  
|<span data-ttu-id="abe5c-144">DTYPE_DATETIME</span><span class="sxs-lookup"><span data-stu-id="abe5c-144">DTYPE_DATETIME</span></span>|<span data-ttu-id="abe5c-145">DateTime</span><span class="sxs-lookup"><span data-stu-id="abe5c-145">DateTime</span></span>|<span data-ttu-id="abe5c-146">xsd:dateTime</span><span class="sxs-lookup"><span data-stu-id="abe5c-146">xsd:dateTime</span></span>|  
|<span data-ttu-id="abe5c-147">DTYPE_ UTCDATETIME</span><span class="sxs-lookup"><span data-stu-id="abe5c-147">DTYPE_ UTCDATETIME</span></span>|<span data-ttu-id="abe5c-148">DateTime</span><span class="sxs-lookup"><span data-stu-id="abe5c-148">DateTime</span></span>|<span data-ttu-id="abe5c-149">xsd:dateTime</span><span class="sxs-lookup"><span data-stu-id="abe5c-149">xsd:dateTime</span></span>|  
|<span data-ttu-id="abe5c-150">DTYPE_ID</span><span class="sxs-lookup"><span data-stu-id="abe5c-150">DTYPE_ID</span></span>|<span data-ttu-id="abe5c-151">Chaîne</span><span class="sxs-lookup"><span data-stu-id="abe5c-151">String</span></span>|<span data-ttu-id="abe5c-152">xsd:string</span><span class="sxs-lookup"><span data-stu-id="abe5c-152">xsd:string</span></span>|  
|<span data-ttu-id="abe5c-153">DTYPE_INTEGER</span><span class="sxs-lookup"><span data-stu-id="abe5c-153">DTYPE_INTEGER</span></span>|<span data-ttu-id="abe5c-154">Entier</span><span class="sxs-lookup"><span data-stu-id="abe5c-154">Integer</span></span>|<span data-ttu-id="abe5c-155">xsd:int</span><span class="sxs-lookup"><span data-stu-id="abe5c-155">xsd:int</span></span>|  
|<span data-ttu-id="abe5c-156">DTYPE_NOTE</span><span class="sxs-lookup"><span data-stu-id="abe5c-156">DTYPE_NOTE</span></span>|<span data-ttu-id="abe5c-157">Chaîne</span><span class="sxs-lookup"><span data-stu-id="abe5c-157">String</span></span>|<span data-ttu-id="abe5c-158">xsd:string</span><span class="sxs-lookup"><span data-stu-id="abe5c-158">xsd:string</span></span>|  
|<span data-ttu-id="abe5c-159">DTYPE_NUMBER</span><span class="sxs-lookup"><span data-stu-id="abe5c-159">DTYPE_NUMBER</span></span>|<span data-ttu-id="abe5c-160">Décimal</span><span class="sxs-lookup"><span data-stu-id="abe5c-160">Decimal</span></span>|<span data-ttu-id="abe5c-161">xsd:decimal</span><span class="sxs-lookup"><span data-stu-id="abe5c-161">xsd:decimal</span></span>|  
|<span data-ttu-id="abe5c-162">DTYPE_PHONE</span><span class="sxs-lookup"><span data-stu-id="abe5c-162">DTYPE_PHONE</span></span>|<span data-ttu-id="abe5c-163">Chaîne</span><span class="sxs-lookup"><span data-stu-id="abe5c-163">String</span></span>|<span data-ttu-id="abe5c-164">xsd:string</span><span class="sxs-lookup"><span data-stu-id="abe5c-164">xsd:string</span></span>|  
|<span data-ttu-id="abe5c-165">DTYPE_TEXT</span><span class="sxs-lookup"><span data-stu-id="abe5c-165">DTYPE_TEXT</span></span>|<span data-ttu-id="abe5c-166">Chaîne</span><span class="sxs-lookup"><span data-stu-id="abe5c-166">String</span></span>|<span data-ttu-id="abe5c-167">xsd:string</span><span class="sxs-lookup"><span data-stu-id="abe5c-167">xsd:string</span></span>|  
|<span data-ttu-id="abe5c-168">DTYPE_TIME</span><span class="sxs-lookup"><span data-stu-id="abe5c-168">DTYPE_TIME</span></span>|<span data-ttu-id="abe5c-169">DateTime</span><span class="sxs-lookup"><span data-stu-id="abe5c-169">DateTime</span></span>|<span data-ttu-id="abe5c-170">xsd:dateTime</span><span class="sxs-lookup"><span data-stu-id="abe5c-170">xsd:dateTime</span></span>|  
  
## <a name="supported-methods"></a><span data-ttu-id="abe5c-171">Méthodes prises en charge</span><span class="sxs-lookup"><span data-stu-id="abe5c-171">Supported Methods</span></span>  
 <span data-ttu-id="abe5c-172">Le `SiebelParameter` classe ne remplace pas les méthodes spéciales dans `DbParameter`.</span><span class="sxs-lookup"><span data-stu-id="abe5c-172">The `SiebelParameter` class does not override any special methods in `DbParameter`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="abe5c-173">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="abe5c-173">See Also</span></span>  
 [<span data-ttu-id="abe5c-174">Étendre des Interfaces ADO.NET avec l’adaptateur Siebel</span><span class="sxs-lookup"><span data-stu-id="abe5c-174">Extend ADO.NET Interfaces with the Siebel adapter</span></span>](../../adapters-and-accelerators/adapter-siebel/extend-ado-net-interfaces-with-the-siebel-adapter.md)