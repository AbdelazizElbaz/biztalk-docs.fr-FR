---
title: "Schéma (nœud TrackedSchemas) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Schema node
ms.assetid: a503aad6-07f8-4650-a214-4d2f6650cb80
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5376c505332ed05507169c1db2dc54ec4e7bdfe6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="schema-trackedschemas-node"></a><span data-ttu-id="78d29-102">Schéma (nœud TrackedSchemas)</span><span class="sxs-lookup"><span data-stu-id="78d29-102">Schema (TrackedSchemas Node)</span></span>
<span data-ttu-id="78d29-103">Le nœud Schéma du nœud TrackedSchemas d'un fichier de liaison décrit un schéma lié à un service exporté avec le fichier de liaison.</span><span class="sxs-lookup"><span data-stu-id="78d29-103">The Schema node of the TrackedSchemas node of a binding file describes a schema bound to a service that is exported with the binding file.</span></span>  
  
## <a name="nodes-in-the-schema-node"></a><span data-ttu-id="78d29-104">Nœuds du nœud Schéma</span><span class="sxs-lookup"><span data-stu-id="78d29-104">Nodes in the Schema node</span></span>  
 <span data-ttu-id="78d29-105">Le tableau suivant répertorie les propriétés que vous pouvez définir pour ce nœud d'un fichier de liaison :</span><span class="sxs-lookup"><span data-stu-id="78d29-105">The following table lists the properties that can be set for this node of a binding file:</span></span>  
  
|<span data-ttu-id="78d29-106">**Nom**</span><span class="sxs-lookup"><span data-stu-id="78d29-106">**Name**</span></span>|<span data-ttu-id="78d29-107">**Type de nœud**</span><span class="sxs-lookup"><span data-stu-id="78d29-107">**Node Type**</span></span>|<span data-ttu-id="78d29-108">**Type de données**</span><span class="sxs-lookup"><span data-stu-id="78d29-108">**Data Type**</span></span>|<span data-ttu-id="78d29-109">**Description**</span><span class="sxs-lookup"><span data-stu-id="78d29-109">**Description**</span></span>|<span data-ttu-id="78d29-110">**Restrictions**</span><span class="sxs-lookup"><span data-stu-id="78d29-110">**Restrictions**</span></span>|<span data-ttu-id="78d29-111">**Commentaires**</span><span class="sxs-lookup"><span data-stu-id="78d29-111">**Comments**</span></span>|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|<span data-ttu-id="78d29-112">FullName</span><span class="sxs-lookup"><span data-stu-id="78d29-112">FullName</span></span>|<span data-ttu-id="78d29-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="78d29-113">Attribute</span></span>|<span data-ttu-id="78d29-114">xs:string</span><span class="sxs-lookup"><span data-stu-id="78d29-114">xs:string</span></span>|<span data-ttu-id="78d29-115">Spécifie le nom complet du schéma.</span><span class="sxs-lookup"><span data-stu-id="78d29-115">Specifies the full name for the schema.</span></span>|<span data-ttu-id="78d29-116">Facultatif</span><span class="sxs-lookup"><span data-stu-id="78d29-116">Not required</span></span>|<span data-ttu-id="78d29-117">Valeur par défaut : vide</span><span class="sxs-lookup"><span data-stu-id="78d29-117">Default value: empty</span></span>|  
|<span data-ttu-id="78d29-118">AssemblyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="78d29-118">AssemblyQualifiedName</span></span>|<span data-ttu-id="78d29-119">Attribut</span><span class="sxs-lookup"><span data-stu-id="78d29-119">Attribute</span></span>|<span data-ttu-id="78d29-120">xs:string</span><span class="sxs-lookup"><span data-stu-id="78d29-120">xs:string</span></span>|<span data-ttu-id="78d29-121">Spécifie le nom complet de l'assembly contenant le schéma.</span><span class="sxs-lookup"><span data-stu-id="78d29-121">Specifies the qualified name for the assembly containing this schema.</span></span>|<span data-ttu-id="78d29-122">Facultatif</span><span class="sxs-lookup"><span data-stu-id="78d29-122">Not required</span></span>|<span data-ttu-id="78d29-123">Valeur par défaut : vide</span><span class="sxs-lookup"><span data-stu-id="78d29-123">Default value: empty</span></span>|  
|<span data-ttu-id="78d29-124">AlwaysTrackAllProperties</span><span class="sxs-lookup"><span data-stu-id="78d29-124">AlwaysTrackAllProperties</span></span>|<span data-ttu-id="78d29-125">Attribut</span><span class="sxs-lookup"><span data-stu-id="78d29-125">Attribute</span></span>|<span data-ttu-id="78d29-126">xs:boolean</span><span class="sxs-lookup"><span data-stu-id="78d29-126">xs:boolean</span></span>|<span data-ttu-id="78d29-127">Indique s'il faut ou non suivre toutes les propriétés pour l'assembly spécifié.</span><span class="sxs-lookup"><span data-stu-id="78d29-127">Specifies whether to track all properties for the specified assembly.</span></span>|<span data-ttu-id="78d29-128">Requis</span><span class="sxs-lookup"><span data-stu-id="78d29-128">Required</span></span>|<span data-ttu-id="78d29-129">Valeur par défaut : Aucun</span><span class="sxs-lookup"><span data-stu-id="78d29-129">Default value: none</span></span><br /><br /> <span data-ttu-id="78d29-130">La valeur **true** pour effectuer le suivi de toutes les propriétés, sinon la valeur **false**.</span><span class="sxs-lookup"><span data-stu-id="78d29-130">Set to **true** to track all properties, otherwise set to **false**.</span></span>|  
|<span data-ttu-id="78d29-131"> Description</span><span class="sxs-lookup"><span data-stu-id="78d29-131">Description</span></span>|<span data-ttu-id="78d29-132">Attribut</span><span class="sxs-lookup"><span data-stu-id="78d29-132">Attribute</span></span>|<span data-ttu-id="78d29-133">xs:string</span><span class="sxs-lookup"><span data-stu-id="78d29-133">xs:string</span></span>|<span data-ttu-id="78d29-134">Spécifie une description pour le schéma.</span><span class="sxs-lookup"><span data-stu-id="78d29-134">Specifies a description for the schema.</span></span>|<span data-ttu-id="78d29-135">Facultatif</span><span class="sxs-lookup"><span data-stu-id="78d29-135">Not required</span></span>|<span data-ttu-id="78d29-136">Valeur par défaut : vide</span><span class="sxs-lookup"><span data-stu-id="78d29-136">Default value: empty</span></span>|  
|[<span data-ttu-id="78d29-137">TrackedPropertyNames (nœud de schéma)</span><span class="sxs-lookup"><span data-stu-id="78d29-137">TrackedPropertyNames (Schema Node)</span></span>](../core/trackedpropertynames-schema-node.md)|<span data-ttu-id="78d29-138">Record</span><span class="sxs-lookup"><span data-stu-id="78d29-138">Record</span></span>|<span data-ttu-id="78d29-139">ArrayOfString (ComplexType)</span><span class="sxs-lookup"><span data-stu-id="78d29-139">ArrayOfString (ComplexType)</span></span>|<span data-ttu-id="78d29-140">Conteneur pour les éléments qui spécifient les propriétés à suivre.</span><span class="sxs-lookup"><span data-stu-id="78d29-140">Container for the elements that specify the properties to be tracked.</span></span>|<span data-ttu-id="78d29-141">Facultatif</span><span class="sxs-lookup"><span data-stu-id="78d29-141">Not required</span></span>|<span data-ttu-id="78d29-142">Valeur par défaut : Aucun</span><span class="sxs-lookup"><span data-stu-id="78d29-142">Default value: none</span></span>|