---
title: "Classe SAPParameterCollection dans l’adaptateur SAP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: SAPParameterCollection, supported methods and classes
ms.assetid: fd09355b-95f4-4d49-a643-b13058e63d74
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 924cb884c64f337cec0e628c804b5c5a8c6cf37b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="sapparametercollection-class-in-the-sap-adapter"></a><span data-ttu-id="a8e74-102">Classe SAPParameterCollection dans l’adaptateur SAP</span><span class="sxs-lookup"><span data-stu-id="a8e74-102">SAPParameterCollection class in the SAP adapter</span></span>
<span data-ttu-id="a8e74-103">La section suivante répertorie les méthodes et propriétés pour le **SAPParameterCollection** classe.</span><span class="sxs-lookup"><span data-stu-id="a8e74-103">The following section lists the methods and properties for the **SAPParameterCollection** class.</span></span> <span data-ttu-id="a8e74-104">Elle est dérivée de **System.Data.Common.DbParameterCollection**.</span><span class="sxs-lookup"><span data-stu-id="a8e74-104">This is derived from **System.Data.Common.DbParameterCollection**.</span></span>  
  
## <a name="supported-properties"></a><span data-ttu-id="a8e74-105">Propriétés prises en charge</span><span class="sxs-lookup"><span data-stu-id="a8e74-105">Supported Properties</span></span>  
  
|<span data-ttu-id="a8e74-106">Nom</span><span class="sxs-lookup"><span data-stu-id="a8e74-106">Name</span></span>|<span data-ttu-id="a8e74-107">Get/Set.</span><span class="sxs-lookup"><span data-stu-id="a8e74-107">Get/Set</span></span>|<span data-ttu-id="a8e74-108"> Description</span><span class="sxs-lookup"><span data-stu-id="a8e74-108">Description</span></span>|  
|----------|--------------|-----------------|  
|<span data-ttu-id="a8e74-109">**Count**</span><span class="sxs-lookup"><span data-stu-id="a8e74-109">**Count**</span></span>|<span data-ttu-id="a8e74-110">Obtenir</span><span class="sxs-lookup"><span data-stu-id="a8e74-110">Get</span></span>|<span data-ttu-id="a8e74-111">Nombre de paramètres dans la collection.</span><span class="sxs-lookup"><span data-stu-id="a8e74-111">Number of parameters in the collection.</span></span>|  
|<span data-ttu-id="a8e74-112">**IsFixedSize**</span><span class="sxs-lookup"><span data-stu-id="a8e74-112">**IsFixedSize**</span></span>|<span data-ttu-id="a8e74-113">Obtenir</span><span class="sxs-lookup"><span data-stu-id="a8e74-113">Get</span></span>|<span data-ttu-id="a8e74-114">Non pris en charge.</span><span class="sxs-lookup"><span data-stu-id="a8e74-114">Not supported.</span></span> <span data-ttu-id="a8e74-115">Retourne la valeur false.</span><span class="sxs-lookup"><span data-stu-id="a8e74-115">Returns false.</span></span>|  
|<span data-ttu-id="a8e74-116">**IsReadOnly**</span><span class="sxs-lookup"><span data-stu-id="a8e74-116">**IsReadOnly**</span></span>|<span data-ttu-id="a8e74-117">Obtenir</span><span class="sxs-lookup"><span data-stu-id="a8e74-117">Get</span></span>|<span data-ttu-id="a8e74-118">Non pris en charge.</span><span class="sxs-lookup"><span data-stu-id="a8e74-118">Not supported.</span></span> <span data-ttu-id="a8e74-119">Retourne la valeur false.</span><span class="sxs-lookup"><span data-stu-id="a8e74-119">Returns false.</span></span>|  
|<span data-ttu-id="a8e74-120">**IsSynchronized**</span><span class="sxs-lookup"><span data-stu-id="a8e74-120">**IsSynchronized**</span></span>|<span data-ttu-id="a8e74-121">Obtenir</span><span class="sxs-lookup"><span data-stu-id="a8e74-121">Get</span></span>|<span data-ttu-id="a8e74-122">Non pris en charge.</span><span class="sxs-lookup"><span data-stu-id="a8e74-122">Not supported.</span></span> <span data-ttu-id="a8e74-123">Retourne la valeur false.</span><span class="sxs-lookup"><span data-stu-id="a8e74-123">Returns false.</span></span>|  
|<span data-ttu-id="a8e74-124">**SyncRoot**</span><span class="sxs-lookup"><span data-stu-id="a8e74-124">**SyncRoot**</span></span>|<span data-ttu-id="a8e74-125">Obtenir</span><span class="sxs-lookup"><span data-stu-id="a8e74-125">Get</span></span>|<span data-ttu-id="a8e74-126">Retourne l’objet de verrouillage.</span><span class="sxs-lookup"><span data-stu-id="a8e74-126">Returns the lock object.</span></span>|  
  
## <a name="supported-methods"></a><span data-ttu-id="a8e74-127">Méthodes prises en charge</span><span class="sxs-lookup"><span data-stu-id="a8e74-127">Supported Methods</span></span>  
  
|<span data-ttu-id="a8e74-128">Nom</span><span class="sxs-lookup"><span data-stu-id="a8e74-128">Name</span></span>|<span data-ttu-id="a8e74-129"> Description</span><span class="sxs-lookup"><span data-stu-id="a8e74-129">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="a8e74-130">**Add(SAPParameter)**</span><span class="sxs-lookup"><span data-stu-id="a8e74-130">**Add(SAPParameter)**</span></span>|<span data-ttu-id="a8e74-131">Paramètre ne peut pas appartenir à plusieurs ParameterCollection.</span><span class="sxs-lookup"><span data-stu-id="a8e74-131">Parameter cannot belong to more than one ParameterCollection.</span></span>|  
|<span data-ttu-id="a8e74-132">**Utiliser**</span><span class="sxs-lookup"><span data-stu-id="a8e74-132">**Add(object)**</span></span>|<span data-ttu-id="a8e74-133">Objet doit être de type de l’objet SAPParameter.</span><span class="sxs-lookup"><span data-stu-id="a8e74-133">Object should be of SAPParameter type.</span></span>|  
|<span data-ttu-id="a8e74-134">**AddRange(System.Array)**</span><span class="sxs-lookup"><span data-stu-id="a8e74-134">**AddRange(System.Array)**</span></span>|<span data-ttu-id="a8e74-135">Ajoute un tableau d’instances de l’objet SAPParameter.</span><span class="sxs-lookup"><span data-stu-id="a8e74-135">Adds an array of SAPParameter instances.</span></span>|  
|<span data-ttu-id="a8e74-136">**Clear()**</span><span class="sxs-lookup"><span data-stu-id="a8e74-136">**Clear()**</span></span>|<span data-ttu-id="a8e74-137">Efface les paramètres de la collection.</span><span class="sxs-lookup"><span data-stu-id="a8e74-137">Clears the parameters in the collection.</span></span>|  
|<span data-ttu-id="a8e74-138">**Contains(Object)**</span><span class="sxs-lookup"><span data-stu-id="a8e74-138">**Contains(object)**</span></span>|<span data-ttu-id="a8e74-139">Contrôles basés sur l’instance de paramètre.</span><span class="sxs-lookup"><span data-stu-id="a8e74-139">Checks based on parameter instance.</span></span>|  
|<span data-ttu-id="a8e74-140">**Contains(String)**</span><span class="sxs-lookup"><span data-stu-id="a8e74-140">**Contains(string)**</span></span>|<span data-ttu-id="a8e74-141">Contrôles basés sur le nom du paramètre.</span><span class="sxs-lookup"><span data-stu-id="a8e74-141">Checks based on parameter name.</span></span>|  
|<span data-ttu-id="a8e74-142">**CopyTo ([] d’objet SAPParameter, int)**</span><span class="sxs-lookup"><span data-stu-id="a8e74-142">**CopyTo(SAPParameter[], int)**</span></span>|<span data-ttu-id="a8e74-143">Liste de paramètres de copies à un tableau de types d’objet SAPParameter.</span><span class="sxs-lookup"><span data-stu-id="a8e74-143">Copies parameter list to an array of SAPParameter types.</span></span>|  
|<span data-ttu-id="a8e74-144">**CopyTo (System.Array, int)**</span><span class="sxs-lookup"><span data-stu-id="a8e74-144">**CopyTo(System.Array, int)**</span></span>|<span data-ttu-id="a8e74-145">Copie la liste des paramètres dans un tableau.</span><span class="sxs-lookup"><span data-stu-id="a8e74-145">Copies parameter list to an array.</span></span>|  
|<span data-ttu-id="a8e74-146">**GetEnumerator()**</span><span class="sxs-lookup"><span data-stu-id="a8e74-146">**GetEnumerator()**</span></span>|<span data-ttu-id="a8e74-147">Obtient un énumérateur pour les paramètres dans la collection.</span><span class="sxs-lookup"><span data-stu-id="a8e74-147">Gets an enumerator for the parameters in the collection.</span></span>|  
|<span data-ttu-id="a8e74-148">**IndexOf (Object)**</span><span class="sxs-lookup"><span data-stu-id="a8e74-148">**IndexOf(object)**</span></span>|<span data-ttu-id="a8e74-149">Index de paramètre en fonction de l’instance de l’objet SAPParameter.</span><span class="sxs-lookup"><span data-stu-id="a8e74-149">Index of parameter based on SAPParameter instance.</span></span>|  
|<span data-ttu-id="a8e74-150">**IndexOf (String)**</span><span class="sxs-lookup"><span data-stu-id="a8e74-150">**IndexOf(string)**</span></span>|<span data-ttu-id="a8e74-151">Index de paramètre en fonction du nom de l’objet SAPParameter.</span><span class="sxs-lookup"><span data-stu-id="a8e74-151">Index of parameter based on SAPParameter name.</span></span>|  
|<span data-ttu-id="a8e74-152">**Insert (int, object)**</span><span class="sxs-lookup"><span data-stu-id="a8e74-152">**Insert(int, object)**</span></span>|<span data-ttu-id="a8e74-153">Insère un objet SAPParameter dans la collection.</span><span class="sxs-lookup"><span data-stu-id="a8e74-153">Inserts an SAPParameter into the collection.</span></span>|  
|<span data-ttu-id="a8e74-154">**Remove(Object)**</span><span class="sxs-lookup"><span data-stu-id="a8e74-154">**Remove(object)**</span></span>|<span data-ttu-id="a8e74-155">Supprime un objet SAPParameter dans la collection en fonction de l’instance.</span><span class="sxs-lookup"><span data-stu-id="a8e74-155">Removes an SAPParameter into the collection based on instance.</span></span>|  
|<span data-ttu-id="a8e74-156">**RemoveAt(int)**</span><span class="sxs-lookup"><span data-stu-id="a8e74-156">**RemoveAt(int)**</span></span>|<span data-ttu-id="a8e74-157">Supprime un objet SAPParameter dans la collection à un index donné.</span><span class="sxs-lookup"><span data-stu-id="a8e74-157">Removes an SAPParameter into the collection at a given index.</span></span>|  
|<span data-ttu-id="a8e74-158">**RemoveAt (String)**</span><span class="sxs-lookup"><span data-stu-id="a8e74-158">**RemoveAt(string)**</span></span>|<span data-ttu-id="a8e74-159">Supprime un objet SAPParameter dans la collection en fonction de nom.</span><span class="sxs-lookup"><span data-stu-id="a8e74-159">Removes an SAPParameter into the collection based on name.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a8e74-160">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a8e74-160">See Also</span></span>  
 [<span data-ttu-id="a8e74-161">Étendre des Interfaces ADO.NET avec l’adaptateur SAP</span><span class="sxs-lookup"><span data-stu-id="a8e74-161">Extend ADO.NET Interfaces with the SAP adapter</span></span>](../../adapters-and-accelerators/adapter-sap/extend-ado-net-interfaces-with-the-sap-adapter.md)