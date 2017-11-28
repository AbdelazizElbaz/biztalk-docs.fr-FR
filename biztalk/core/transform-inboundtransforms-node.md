---
title: "Transformation (nœud InboundTransforms) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Transform node [binding file]
ms.assetid: c1bad23e-78a4-4fd4-95ef-30601393d53c
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 705b1b04b8305330ab1d5ff705c5025f24b0685c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="transform-inboundtransforms-node"></a><span data-ttu-id="84eaa-102">Transformation (nœud InboundTransforms)</span><span class="sxs-lookup"><span data-stu-id="84eaa-102">Transform (InboundTransforms Node)</span></span>
<span data-ttu-id="84eaa-103">Le nœud Transformation du nœud InboundTransforms d'un fichier de liaison contient des informations spécifiques sur un mappage Biztalk Server exporté avec ce fichier de liaison.</span><span class="sxs-lookup"><span data-stu-id="84eaa-103">The Transform node of the InboundTransforms node of a binding file contains specific information about a BizTalk Server map that is exported with the binding file.</span></span>  
  
## <a name="nodes-in-the-transform-node"></a><span data-ttu-id="84eaa-104">Nœuds du nœud Transform</span><span class="sxs-lookup"><span data-stu-id="84eaa-104">Nodes in the Transform node</span></span>  
 <span data-ttu-id="84eaa-105">Le tableau suivant répertorie les propriétés que vous pouvez définir pour ce nœud d'un fichier de liaison :</span><span class="sxs-lookup"><span data-stu-id="84eaa-105">The following table lists the properties that can be set for this node of a binding file:</span></span>  
  
|<span data-ttu-id="84eaa-106">**Nom**</span><span class="sxs-lookup"><span data-stu-id="84eaa-106">**Name**</span></span>|<span data-ttu-id="84eaa-107">**Type de nœud**</span><span class="sxs-lookup"><span data-stu-id="84eaa-107">**Node Type**</span></span>|<span data-ttu-id="84eaa-108">**Type de données**</span><span class="sxs-lookup"><span data-stu-id="84eaa-108">**Data Type**</span></span>|<span data-ttu-id="84eaa-109">**Description**</span><span class="sxs-lookup"><span data-stu-id="84eaa-109">**Description**</span></span>|<span data-ttu-id="84eaa-110">**Restrictions**</span><span class="sxs-lookup"><span data-stu-id="84eaa-110">**Restrictions**</span></span>|<span data-ttu-id="84eaa-111">**Commentaires**</span><span class="sxs-lookup"><span data-stu-id="84eaa-111">**Comments**</span></span>|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|<span data-ttu-id="84eaa-112">FullName</span><span class="sxs-lookup"><span data-stu-id="84eaa-112">FullName</span></span>|<span data-ttu-id="84eaa-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="84eaa-113">Attribute</span></span>|<span data-ttu-id="84eaa-114">xs:string</span><span class="sxs-lookup"><span data-stu-id="84eaa-114">xs:string</span></span>|<span data-ttu-id="84eaa-115">Spécifie le nom complet du mappage.</span><span class="sxs-lookup"><span data-stu-id="84eaa-115">Specifies the full name of the map.</span></span>|<span data-ttu-id="84eaa-116">Facultatif</span><span class="sxs-lookup"><span data-stu-id="84eaa-116">Not required</span></span>|<span data-ttu-id="84eaa-117">Valeur par défaut : vide</span><span class="sxs-lookup"><span data-stu-id="84eaa-117">Default value: empty</span></span>|  
|<span data-ttu-id="84eaa-118">AssemblyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="84eaa-118">AssemblyQualifiedName</span></span>|<span data-ttu-id="84eaa-119">Attribut</span><span class="sxs-lookup"><span data-stu-id="84eaa-119">Attribute</span></span>|<span data-ttu-id="84eaa-120">xs:string</span><span class="sxs-lookup"><span data-stu-id="84eaa-120">xs:string</span></span>|<span data-ttu-id="84eaa-121">Spécifie le nom qualifié d'assembly du mappage.</span><span class="sxs-lookup"><span data-stu-id="84eaa-121">Specifies the assembly qualified name of the map.</span></span>|<span data-ttu-id="84eaa-122">Facultatif</span><span class="sxs-lookup"><span data-stu-id="84eaa-122">Not required</span></span>|<span data-ttu-id="84eaa-123">Valeur par défaut : vide</span><span class="sxs-lookup"><span data-stu-id="84eaa-123">Default value: empty</span></span>|