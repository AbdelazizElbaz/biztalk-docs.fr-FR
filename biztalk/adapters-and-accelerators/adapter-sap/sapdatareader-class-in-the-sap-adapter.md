---
title: "Classe SAPDataReader dans l’adaptateur SAP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: SAPDataReader, supported methods and classes
ms.assetid: bd0e55ea-7413-498f-851f-ed97bd8bacab
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 70fe658058b6d00b4a22b333ef5683a285b9cab3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="sapdatareader-class-in-the-sap-adapter"></a><span data-ttu-id="9196f-102">Classe SAPDataReader dans l’adaptateur SAP</span><span class="sxs-lookup"><span data-stu-id="9196f-102">SAPDataReader class in the SAP adapter</span></span>
<span data-ttu-id="9196f-103">La section suivante répertorie les méthodes et propriétés pour le **SAPDataReader** classe.</span><span class="sxs-lookup"><span data-stu-id="9196f-103">The following section lists the methods and properties for the **SAPDataReader** class.</span></span> <span data-ttu-id="9196f-104">Elle est dérivée de **System.Data.Common.DbDataReader**.</span><span class="sxs-lookup"><span data-stu-id="9196f-104">This is derived from **System.Data.Common.DbDataReader**.</span></span>  
  
## <a name="supported-properties"></a><span data-ttu-id="9196f-105">Propriétés prises en charge</span><span class="sxs-lookup"><span data-stu-id="9196f-105">Supported Properties</span></span>  
  
|<span data-ttu-id="9196f-106">Nom</span><span class="sxs-lookup"><span data-stu-id="9196f-106">Name</span></span>|<span data-ttu-id="9196f-107">Get/Set.</span><span class="sxs-lookup"><span data-stu-id="9196f-107">Get/Set</span></span>|<span data-ttu-id="9196f-108"> Description</span><span class="sxs-lookup"><span data-stu-id="9196f-108">Description</span></span>|  
|----------|--------------|-----------------|  
|<span data-ttu-id="9196f-109">**Profondeur**</span><span class="sxs-lookup"><span data-stu-id="9196f-109">**Depth**</span></span>|<span data-ttu-id="9196f-110">Obtenir</span><span class="sxs-lookup"><span data-stu-id="9196f-110">Get</span></span>|<span data-ttu-id="9196f-111">Non pris en charge.</span><span class="sxs-lookup"><span data-stu-id="9196f-111">Not supported.</span></span> <span data-ttu-id="9196f-112">Retourne 0.</span><span class="sxs-lookup"><span data-stu-id="9196f-112">Returns 0.</span></span>|  
|<span data-ttu-id="9196f-113">**FieldCount**</span><span class="sxs-lookup"><span data-stu-id="9196f-113">**FieldCount**</span></span>|<span data-ttu-id="9196f-114">Obtenir</span><span class="sxs-lookup"><span data-stu-id="9196f-114">Get</span></span>|<span data-ttu-id="9196f-115">Nombre de champs dans le jeu d’enregistrements actuel</span><span class="sxs-lookup"><span data-stu-id="9196f-115">Number of fields in the current record set</span></span>|  
|<span data-ttu-id="9196f-116">**IsClosed**</span><span class="sxs-lookup"><span data-stu-id="9196f-116">**IsClosed**</span></span>|<span data-ttu-id="9196f-117">Obtenir</span><span class="sxs-lookup"><span data-stu-id="9196f-117">Get</span></span>|<span data-ttu-id="9196f-118">Retourne l’état du lecteur de données</span><span class="sxs-lookup"><span data-stu-id="9196f-118">Returns status of data reader</span></span>|  
|<span data-ttu-id="9196f-119">**RecordsAffected**</span><span class="sxs-lookup"><span data-stu-id="9196f-119">**RecordsAffected**</span></span>|<span data-ttu-id="9196f-120">Obtenir</span><span class="sxs-lookup"><span data-stu-id="9196f-120">Get</span></span>|<span data-ttu-id="9196f-121">Non pris en charge.</span><span class="sxs-lookup"><span data-stu-id="9196f-121">Not supported.</span></span> <span data-ttu-id="9196f-122">Retourne -1</span><span class="sxs-lookup"><span data-stu-id="9196f-122">Returns -1</span></span>|  
  
## <a name="supported-methods"></a><span data-ttu-id="9196f-123">Méthodes prises en charge</span><span class="sxs-lookup"><span data-stu-id="9196f-123">Supported Methods</span></span>  
  
|<span data-ttu-id="9196f-124">Nom</span><span class="sxs-lookup"><span data-stu-id="9196f-124">Name</span></span>|<span data-ttu-id="9196f-125"> Description</span><span class="sxs-lookup"><span data-stu-id="9196f-125">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="9196f-126">**Close()**</span><span class="sxs-lookup"><span data-stu-id="9196f-126">**Close()**</span></span>|<span data-ttu-id="9196f-127">Ferme le DataReader</span><span class="sxs-lookup"><span data-stu-id="9196f-127">Closes the DataReader</span></span>|  
|<span data-ttu-id="9196f-128">**Obtenir le [méthodes]**<sup>*</sup></span><span class="sxs-lookup"><span data-stu-id="9196f-128">**Get [methods]** <sup>*</sup></span></span><br /><br /> <span data-ttu-id="9196f-129">où [méthodes] est le type de données attendu.</span><span class="sxs-lookup"><span data-stu-id="9196f-129">where [methods] is the expected data type.</span></span> <span data-ttu-id="9196f-130">Par ex.</span><span class="sxs-lookup"><span data-stu-id="9196f-130">E.g.</span></span> <span data-ttu-id="9196f-131">GetInt32(int)</span><span class="sxs-lookup"><span data-stu-id="9196f-131">GetInt32(int)</span></span>|<span data-ttu-id="9196f-132">Obtient la valeur de la colonne en fonction du type de données attendu</span><span class="sxs-lookup"><span data-stu-id="9196f-132">Gets column value based on the data type expected</span></span>|  
|<span data-ttu-id="9196f-133">**IsDBNull(int)**</span><span class="sxs-lookup"><span data-stu-id="9196f-133">**IsDBNull(int)**</span></span>|<span data-ttu-id="9196f-134">Non pris en charge.</span><span class="sxs-lookup"><span data-stu-id="9196f-134">Not supported.</span></span> <span data-ttu-id="9196f-135">Retourne la valeur false.</span><span class="sxs-lookup"><span data-stu-id="9196f-135">Returns false.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9196f-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9196f-136">See Also</span></span>  
 [<span data-ttu-id="9196f-137">Étendre des Interfaces ADO.NET avec l’adaptateur SAP</span><span class="sxs-lookup"><span data-stu-id="9196f-137">Extend ADO.NET Interfaces with the SAP adapter</span></span>](../../adapters-and-accelerators/adapter-sap/extend-ado-net-interfaces-with-the-sap-adapter.md)