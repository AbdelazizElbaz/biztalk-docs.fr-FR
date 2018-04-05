---
title: Transformation (nœud Transforms) | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Transform node [binding file]
ms.assetid: 2d1387f1-1668-4982-a717-52478e2a91f9
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 33e70e5a2bcba2925941e727034b90c9fe4b1418
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="transform-transforms-node"></a><span data-ttu-id="531da-102">Transformation (Nœud Transforms)</span><span class="sxs-lookup"><span data-stu-id="531da-102">Transform (Transforms Node)</span></span>
<span data-ttu-id="531da-103">Le nœud de transformation du nœud Transforms d'un fichier de liaison contient des informations sur un mappage Biztalk server  associé à un transport exporté avec le fichier de liaison.</span><span class="sxs-lookup"><span data-stu-id="531da-103">The Transform node of the Transforms node of a binding file contains specific information about a BizTalk Server map that is exported with the binding file.</span></span>  
  
## <a name="nodes-in-the-transform-node"></a><span data-ttu-id="531da-104">Nœuds du nœud Transform</span><span class="sxs-lookup"><span data-stu-id="531da-104">Nodes in the Transform node</span></span>  
 <span data-ttu-id="531da-105">Le tableau suivant répertorie les propriétés que vous pouvez définir pour ce nœud d'un fichier de liaison :</span><span class="sxs-lookup"><span data-stu-id="531da-105">The following table lists the properties that can be set for this node of a binding file:</span></span>  
  
|<span data-ttu-id="531da-106">**Nom**</span><span class="sxs-lookup"><span data-stu-id="531da-106">**Name**</span></span>|<span data-ttu-id="531da-107">**Type de nœud**</span><span class="sxs-lookup"><span data-stu-id="531da-107">**Node Type**</span></span>|<span data-ttu-id="531da-108">**Type de données**</span><span class="sxs-lookup"><span data-stu-id="531da-108">**Data Type**</span></span>|<span data-ttu-id="531da-109">**Description**</span><span class="sxs-lookup"><span data-stu-id="531da-109">**Description**</span></span>|<span data-ttu-id="531da-110">**Restrictions**</span><span class="sxs-lookup"><span data-stu-id="531da-110">**Restrictions**</span></span>|<span data-ttu-id="531da-111">**Commentaires**</span><span class="sxs-lookup"><span data-stu-id="531da-111">**Comments**</span></span>|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|<span data-ttu-id="531da-112">FullName</span><span class="sxs-lookup"><span data-stu-id="531da-112">FullName</span></span>|<span data-ttu-id="531da-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="531da-113">Attribute</span></span>|<span data-ttu-id="531da-114">xs:string</span><span class="sxs-lookup"><span data-stu-id="531da-114">xs:string</span></span>|<span data-ttu-id="531da-115">Spécifie le nom complet du mappage.</span><span class="sxs-lookup"><span data-stu-id="531da-115">Specifies the full name of the map.</span></span>|<span data-ttu-id="531da-116">Facultatif</span><span class="sxs-lookup"><span data-stu-id="531da-116">Not required</span></span>|<span data-ttu-id="531da-117">Valeur par défaut : vide</span><span class="sxs-lookup"><span data-stu-id="531da-117">Default value: empty</span></span>|  
|<span data-ttu-id="531da-118">AssemblyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="531da-118">AssemblyQualifiedName</span></span>|<span data-ttu-id="531da-119">Attribut</span><span class="sxs-lookup"><span data-stu-id="531da-119">Attribute</span></span>|<span data-ttu-id="531da-120">xs:string</span><span class="sxs-lookup"><span data-stu-id="531da-120">xs:string</span></span>|<span data-ttu-id="531da-121">Spécifie le nom qualifié d'assembly du mappage.</span><span class="sxs-lookup"><span data-stu-id="531da-121">Specifies the assembly qualified name of the map.</span></span>|<span data-ttu-id="531da-122">Facultatif</span><span class="sxs-lookup"><span data-stu-id="531da-122">Not required</span></span>|<span data-ttu-id="531da-123">Valeur par défaut : vide</span><span class="sxs-lookup"><span data-stu-id="531da-123">Default value: empty</span></span>|