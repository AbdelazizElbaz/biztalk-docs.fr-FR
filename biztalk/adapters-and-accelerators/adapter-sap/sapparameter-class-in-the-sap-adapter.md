---
title: "Classe d’objet SAPParameter dans l’adaptateur SAP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: SAPParameter, supported methods, classes, and constructors
ms.assetid: 60053393-ad22-4c99-abae-e538d43c8e18
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9ff43c344cc14adb3deef226c270adc3ca94f2a5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="sapparameter-class-in-the-sap-adapter"></a><span data-ttu-id="5603c-102">Classe d’objet SAPParameter dans l’adaptateur SAP</span><span class="sxs-lookup"><span data-stu-id="5603c-102">SAPParameter class in the SAP adapter</span></span>
<span data-ttu-id="5603c-103">La section suivante répertorie les méthodes et propriétés pour le **objet SAPParameter** classe.</span><span class="sxs-lookup"><span data-stu-id="5603c-103">The following section lists the methods and properties for the **SAPParameter** class.</span></span> <span data-ttu-id="5603c-104">Elle est dérivée de **System.Data.Common.DbParameter**.</span><span class="sxs-lookup"><span data-stu-id="5603c-104">This is derived from **System.Data.Common.DbParameter**.</span></span>  
  
## <a name="supported-properties"></a><span data-ttu-id="5603c-105">Propriétés prises en charge</span><span class="sxs-lookup"><span data-stu-id="5603c-105">Supported Properties</span></span>  
  
|<span data-ttu-id="5603c-106">Nom</span><span class="sxs-lookup"><span data-stu-id="5603c-106">Name</span></span>|<span data-ttu-id="5603c-107">Get/Set.</span><span class="sxs-lookup"><span data-stu-id="5603c-107">Get/Set</span></span>|<span data-ttu-id="5603c-108"> Description</span><span class="sxs-lookup"><span data-stu-id="5603c-108">Description</span></span>|  
|----------|--------------|-----------------|  
|<span data-ttu-id="5603c-109">**DbType**</span><span class="sxs-lookup"><span data-stu-id="5603c-109">**DbType**</span></span>|<span data-ttu-id="5603c-110">Obtenir</span><span class="sxs-lookup"><span data-stu-id="5603c-110">Get</span></span>|<span data-ttu-id="5603c-111">DbType si le paramètre est retourné.</span><span class="sxs-lookup"><span data-stu-id="5603c-111">DbType if the parameter returned.</span></span> <span data-ttu-id="5603c-112">Ne peut pas être définie.</span><span class="sxs-lookup"><span data-stu-id="5603c-112">Cannot be set.</span></span>|  
|<span data-ttu-id="5603c-113">**Direction**</span><span class="sxs-lookup"><span data-stu-id="5603c-113">**Direction**</span></span>|<span data-ttu-id="5603c-114">Get et Set</span><span class="sxs-lookup"><span data-stu-id="5603c-114">Get and Set</span></span>|<span data-ttu-id="5603c-115">ParameterDirection.ReturnValue ne pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="5603c-115">ParameterDirection.ReturnValue not supported.</span></span>|  
|<span data-ttu-id="5603c-116">**IsNullable**</span><span class="sxs-lookup"><span data-stu-id="5603c-116">**IsNullable**</span></span>|-|<span data-ttu-id="5603c-117">Non pris en charge.</span><span class="sxs-lookup"><span data-stu-id="5603c-117">Not supported.</span></span>|  
|<span data-ttu-id="5603c-118">**ParameterName**</span><span class="sxs-lookup"><span data-stu-id="5603c-118">**ParameterName**</span></span>|<span data-ttu-id="5603c-119">Get et Set</span><span class="sxs-lookup"><span data-stu-id="5603c-119">Get and Set</span></span>|<span data-ttu-id="5603c-120">Nom du paramètre.</span><span class="sxs-lookup"><span data-stu-id="5603c-120">Name of the parameter.</span></span>|  
|<span data-ttu-id="5603c-121">**Taille**</span><span class="sxs-lookup"><span data-stu-id="5603c-121">**Size**</span></span>|-|<span data-ttu-id="5603c-122">Non pris en charge.</span><span class="sxs-lookup"><span data-stu-id="5603c-122">Not supported.</span></span>|  
|<span data-ttu-id="5603c-123">**SourceColumn**</span><span class="sxs-lookup"><span data-stu-id="5603c-123">**SourceColumn**</span></span>|-|<span data-ttu-id="5603c-124">Non pris en charge.</span><span class="sxs-lookup"><span data-stu-id="5603c-124">Not supported.</span></span>|  
|<span data-ttu-id="5603c-125">**SourceColumnNullMapping**</span><span class="sxs-lookup"><span data-stu-id="5603c-125">**SourceColumnNullMapping**</span></span>|-|<span data-ttu-id="5603c-126">Non pris en charge.</span><span class="sxs-lookup"><span data-stu-id="5603c-126">Not supported.</span></span>|  
|<span data-ttu-id="5603c-127">**SourceVersion**</span><span class="sxs-lookup"><span data-stu-id="5603c-127">**SourceVersion**</span></span>|-|<span data-ttu-id="5603c-128">Non pris en charge.</span><span class="sxs-lookup"><span data-stu-id="5603c-128">Not supported.</span></span>|  
|<span data-ttu-id="5603c-129">**Valeur**</span><span class="sxs-lookup"><span data-stu-id="5603c-129">**Value**</span></span>|<span data-ttu-id="5603c-130">Get et Set</span><span class="sxs-lookup"><span data-stu-id="5603c-130">Get and Set</span></span>|<span data-ttu-id="5603c-131">Valeur du paramètre</span><span class="sxs-lookup"><span data-stu-id="5603c-131">Value of the parameter</span></span>|  
  
## <a name="supported-methods"></a><span data-ttu-id="5603c-132">Méthodes prises en charge</span><span class="sxs-lookup"><span data-stu-id="5603c-132">Supported Methods</span></span>  
  
|<span data-ttu-id="5603c-133">Nom</span><span class="sxs-lookup"><span data-stu-id="5603c-133">Name</span></span>|<span data-ttu-id="5603c-134"> Description</span><span class="sxs-lookup"><span data-stu-id="5603c-134">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="5603c-135">**ResetDbType()**</span><span class="sxs-lookup"><span data-stu-id="5603c-135">**ResetDbType()**</span></span>|<span data-ttu-id="5603c-136">Non pris en charge.</span><span class="sxs-lookup"><span data-stu-id="5603c-136">Not supported.</span></span>|  
  
## <a name="supported-constructors"></a><span data-ttu-id="5603c-137">Constructeur pris en charge</span><span class="sxs-lookup"><span data-stu-id="5603c-137">Supported Constructors</span></span>  
  
|<span data-ttu-id="5603c-138">Nom</span><span class="sxs-lookup"><span data-stu-id="5603c-138">Name</span></span>|<span data-ttu-id="5603c-139"> Description</span><span class="sxs-lookup"><span data-stu-id="5603c-139">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="5603c-140">**SAPParameter()**</span><span class="sxs-lookup"><span data-stu-id="5603c-140">**SAPParameter()**</span></span>|<span data-ttu-id="5603c-141">Instance de paramètre SAP.</span><span class="sxs-lookup"><span data-stu-id="5603c-141">SAP parameter instance.</span></span>|  
|<span data-ttu-id="5603c-142">**SAPParameter(string)**</span><span class="sxs-lookup"><span data-stu-id="5603c-142">**SAPParameter(string)**</span></span>|<span data-ttu-id="5603c-143">Paramètre SAP avec le nom de paramètre SAP.</span><span class="sxs-lookup"><span data-stu-id="5603c-143">SAP parameter with SAP parameter name.</span></span>|  
|<span data-ttu-id="5603c-144">**Objet SAPParameter (string, DbType)**</span><span class="sxs-lookup"><span data-stu-id="5603c-144">**SAPParameter(string, DbType)**</span></span>|<span data-ttu-id="5603c-145">Paramètre SAP avec le nom du paramètre SAP et DbType.</span><span class="sxs-lookup"><span data-stu-id="5603c-145">SAP parameter with SAP parameter name and DbType.</span></span>|  
|<span data-ttu-id="5603c-146">**Objet SAPParameter (string, object)**</span><span class="sxs-lookup"><span data-stu-id="5603c-146">**SAPParameter(string, object)**</span></span>|<span data-ttu-id="5603c-147">Paramètre SAP avec le nom de paramètre SAP et la valeur.</span><span class="sxs-lookup"><span data-stu-id="5603c-147">SAP parameter with SAP parameter name and value.</span></span> <span data-ttu-id="5603c-148">Les types complexes ont la valeur de type de table de données et de la chaîne XML.</span><span class="sxs-lookup"><span data-stu-id="5603c-148">Complex types have value of type DataTable and XML string.</span></span>|  
|<span data-ttu-id="5603c-149">**Objet SAPParameter (string, ParameterDirection)**</span><span class="sxs-lookup"><span data-stu-id="5603c-149">**SAPParameter(string, ParameterDirection)**</span></span>|<span data-ttu-id="5603c-150">Paramètre SAP avec la direction de paramètres et de nom de paramètre SAP.</span><span class="sxs-lookup"><span data-stu-id="5603c-150">SAP parameter with SAP parameter name and parameter direction.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5603c-151">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5603c-151">See Also</span></span>  
 [<span data-ttu-id="5603c-152">Étendre des Interfaces ADO.NET avec l’adaptateur SAP</span><span class="sxs-lookup"><span data-stu-id="5603c-152">Extend ADO.NET Interfaces with the SAP adapter</span></span>](../../adapters-and-accelerators/adapter-sap/extend-ado-net-interfaces-with-the-sap-adapter.md)