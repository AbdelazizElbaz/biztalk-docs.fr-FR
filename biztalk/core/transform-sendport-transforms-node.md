---
title: "Transformation (nœud SendPort-transformations) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Transform node [binding file]
ms.assetid: db9a82b2-9bc1-4bd8-8d98-a708a8d25b35
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0a54ed1f25b762d12f598bca84da9b9c3ddd26a9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="transform-sendport-transforms-node"></a><span data-ttu-id="b9c51-102">Transformation (nœud SendPort-transformations)</span><span class="sxs-lookup"><span data-stu-id="b9c51-102">Transform (SendPort-Transforms Node)</span></span>
<span data-ttu-id="b9c51-103">Le nœud de transformation du nœud Transforms d'un fichier de liaison contient des informations sur un mappage Biztalk server  associé à un transport exporté avec le fichier de liaison.</span><span class="sxs-lookup"><span data-stu-id="b9c51-103">The Transform node of the Transforms node of a binding file contains specific information about a BizTalk Server map that is exported with the binding file.</span></span>  
  
## <a name="nodes-in-the-transform-node"></a><span data-ttu-id="b9c51-104">Nœuds du nœud Transform</span><span class="sxs-lookup"><span data-stu-id="b9c51-104">Nodes in the Transform node</span></span>  
 <span data-ttu-id="b9c51-105">Le tableau suivant répertorie les propriétés que vous pouvez définir pour ce nœud d'un fichier de liaison :</span><span class="sxs-lookup"><span data-stu-id="b9c51-105">The following table lists the properties that can be set for this node of a binding file:</span></span>  
  
|<span data-ttu-id="b9c51-106">**Nom**</span><span class="sxs-lookup"><span data-stu-id="b9c51-106">**Name**</span></span>|<span data-ttu-id="b9c51-107">**Type de nœud**</span><span class="sxs-lookup"><span data-stu-id="b9c51-107">**Node Type**</span></span>|<span data-ttu-id="b9c51-108">**Type de données**</span><span class="sxs-lookup"><span data-stu-id="b9c51-108">**Data Type**</span></span>|<span data-ttu-id="b9c51-109">**Description**</span><span class="sxs-lookup"><span data-stu-id="b9c51-109">**Description**</span></span>|<span data-ttu-id="b9c51-110">**Restrictions**</span><span class="sxs-lookup"><span data-stu-id="b9c51-110">**Restrictions**</span></span>|<span data-ttu-id="b9c51-111">**Commentaires**</span><span class="sxs-lookup"><span data-stu-id="b9c51-111">**Comments**</span></span>|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|<span data-ttu-id="b9c51-112">FullName</span><span class="sxs-lookup"><span data-stu-id="b9c51-112">FullName</span></span>|<span data-ttu-id="b9c51-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="b9c51-113">Attribute</span></span>|<span data-ttu-id="b9c51-114">xs:string</span><span class="sxs-lookup"><span data-stu-id="b9c51-114">xs:string</span></span>|<span data-ttu-id="b9c51-115">Spécifie le nom complet du mappage.</span><span class="sxs-lookup"><span data-stu-id="b9c51-115">Specifies the full name of the map.</span></span>|<span data-ttu-id="b9c51-116">Facultatif</span><span class="sxs-lookup"><span data-stu-id="b9c51-116">Not required</span></span>|<span data-ttu-id="b9c51-117">Valeur par défaut : vide</span><span class="sxs-lookup"><span data-stu-id="b9c51-117">Default value: empty</span></span>|  
|<span data-ttu-id="b9c51-118">AssemblyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="b9c51-118">AssemblyQualifiedName</span></span>|<span data-ttu-id="b9c51-119">Attribut</span><span class="sxs-lookup"><span data-stu-id="b9c51-119">Attribute</span></span>|<span data-ttu-id="b9c51-120">xs:string</span><span class="sxs-lookup"><span data-stu-id="b9c51-120">xs:string</span></span>|<span data-ttu-id="b9c51-121">Spécifie le nom qualifié d'assembly du mappage.</span><span class="sxs-lookup"><span data-stu-id="b9c51-121">Specifies the assembly qualified name of the map.</span></span>|<span data-ttu-id="b9c51-122">Facultatif</span><span class="sxs-lookup"><span data-stu-id="b9c51-122">Not required</span></span>|<span data-ttu-id="b9c51-123">Valeur par défaut : vide</span><span class="sxs-lookup"><span data-stu-id="b9c51-123">Default value: empty</span></span>|