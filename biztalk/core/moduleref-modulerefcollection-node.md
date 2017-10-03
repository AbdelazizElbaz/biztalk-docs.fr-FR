---
title: "ModuleRef (nœud ModuleRefCollection) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: ModuleRef node [binding file]
ms.assetid: 61787779-33bd-499a-a5c1-c1e0bd306b48
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8ed580b022e9896ade824c8cf8eccc2458c7ddce
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="moduleref-modulerefcollection-node"></a><span data-ttu-id="f4614-102">ModuleRef (nœud ModuleRefCollection)</span><span class="sxs-lookup"><span data-stu-id="f4614-102">ModuleRef (ModuleRefCollection Node)</span></span>
<span data-ttu-id="f4614-103">Le nœud ModuleRef d'un fichier de liaison contient des informations spécifiques sur un assembly .NET exporté avec ce fichier.</span><span class="sxs-lookup"><span data-stu-id="f4614-103">The ModuleRef node of a binding file contains specific information about a .NET assembly that was exported with the binding file.</span></span> <span data-ttu-id="f4614-104">Un nœud ModuleRef peut comporter, entre autres, des descriptions d'assemblys qui contiennent un code personnalisé, des schémas et des orchestrations.</span><span class="sxs-lookup"><span data-stu-id="f4614-104">A ModuleRef node can include but is not limited to descriptions of assemblies that contain custom code, schemas, and orchestrations.</span></span>  
  
## <a name="nodes-in-the-moduleref-node"></a><span data-ttu-id="f4614-105">Nœuds du nœud ModuleRef</span><span class="sxs-lookup"><span data-stu-id="f4614-105">Nodes in the ModuleRef node</span></span>  
 <span data-ttu-id="f4614-106">Le tableau suivant répertorie les propriétés que vous pouvez définir pour ce nœud d'un fichier de liaison :</span><span class="sxs-lookup"><span data-stu-id="f4614-106">The following table lists the properties that can be set for this node of a binding file:</span></span>  
  
|<span data-ttu-id="f4614-107">**Nom**</span><span class="sxs-lookup"><span data-stu-id="f4614-107">**Name**</span></span>|<span data-ttu-id="f4614-108">**Type de nœud**</span><span class="sxs-lookup"><span data-stu-id="f4614-108">**Node Type**</span></span>|<span data-ttu-id="f4614-109">**Type de données**</span><span class="sxs-lookup"><span data-stu-id="f4614-109">**Data Type**</span></span>|<span data-ttu-id="f4614-110">**Description**</span><span class="sxs-lookup"><span data-stu-id="f4614-110">**Description**</span></span>|<span data-ttu-id="f4614-111">**Restrictions**</span><span class="sxs-lookup"><span data-stu-id="f4614-111">**Restrictions**</span></span>|<span data-ttu-id="f4614-112">**Commentaires**</span><span class="sxs-lookup"><span data-stu-id="f4614-112">**Comments**</span></span>|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|[<span data-ttu-id="f4614-113">Services</span><span class="sxs-lookup"><span data-stu-id="f4614-113">Services</span></span>](../core/services-moduleref-node.md)|<span data-ttu-id="f4614-114">Record</span><span class="sxs-lookup"><span data-stu-id="f4614-114">Record</span></span>|<span data-ttu-id="f4614-115">ArrayOfServiceRef (ComplexType)</span><span class="sxs-lookup"><span data-stu-id="f4614-115">ArrayOfServiceRef (ComplexType)</span></span>|<span data-ttu-id="f4614-116">Nœud conteneur pour les services associés à cet assembly .NET.</span><span class="sxs-lookup"><span data-stu-id="f4614-116">Container node for services associated with this .NET assembly.</span></span>|<span data-ttu-id="f4614-117">Facultatif</span><span class="sxs-lookup"><span data-stu-id="f4614-117">Not required</span></span>|<span data-ttu-id="f4614-118">Valeur par défaut : Aucun</span><span class="sxs-lookup"><span data-stu-id="f4614-118">Default value: none</span></span>|  
|[<span data-ttu-id="f4614-119">TrackedSchemas (nœud ModuleRef)</span><span class="sxs-lookup"><span data-stu-id="f4614-119">TrackedSchemas (ModuleRef Node)</span></span>](../core/trackedschemas-moduleref-node.md)|<span data-ttu-id="f4614-120">Record</span><span class="sxs-lookup"><span data-stu-id="f4614-120">Record</span></span>|<span data-ttu-id="f4614-121">ArrayOfSchema (ComplexType)</span><span class="sxs-lookup"><span data-stu-id="f4614-121">ArrayOfSchema (ComplexType)</span></span>|<span data-ttu-id="f4614-122">Nœud conteneur pour les schémas associés à cet assembly .NET.</span><span class="sxs-lookup"><span data-stu-id="f4614-122">Container node for schemas associated with this .NET assembly</span></span>|<span data-ttu-id="f4614-123">Facultatif</span><span class="sxs-lookup"><span data-stu-id="f4614-123">Not required</span></span>|<span data-ttu-id="f4614-124">Valeur par défaut : Aucun</span><span class="sxs-lookup"><span data-stu-id="f4614-124">Default value: none</span></span>|