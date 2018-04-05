---
title: Transformation (nœud OutboundTransforms) | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Transform node [binding file]
ms.assetid: 928a93cd-7a26-4148-b1af-dc0bc316f8c1
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b44dc5ffd444ebaee8f1f3007f27343c389c5e5f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="transform-outboundtransforms-node"></a><span data-ttu-id="87029-102">Transformation (nœud OutboundTransforms)</span><span class="sxs-lookup"><span data-stu-id="87029-102">Transform (OutboundTransforms Node)</span></span>
<span data-ttu-id="87029-103">Le nœud Transformation du nœud OutboundTransforms d'un fichier de liaison contient des informations spécifiques sur un mappage Biztalk Server exporté avec le fichier de liaison.</span><span class="sxs-lookup"><span data-stu-id="87029-103">The Transform node of the OutboundTransforms node of a binding file contains specific information about a BizTalk Server map that is exported with the binding file.</span></span>  
  
## <a name="nodes-in-the-transform-node"></a><span data-ttu-id="87029-104">Nœuds du nœud Transform</span><span class="sxs-lookup"><span data-stu-id="87029-104">Nodes in the Transform node</span></span>  
 <span data-ttu-id="87029-105">Le tableau suivant répertorie les propriétés que vous pouvez définir pour ce nœud d'un fichier de liaison :</span><span class="sxs-lookup"><span data-stu-id="87029-105">The following table lists the properties that can be set for this node of a binding file:</span></span>  
  
|<span data-ttu-id="87029-106">**Nom**</span><span class="sxs-lookup"><span data-stu-id="87029-106">**Name**</span></span>|<span data-ttu-id="87029-107">**Type de nœud**</span><span class="sxs-lookup"><span data-stu-id="87029-107">**Node Type**</span></span>|<span data-ttu-id="87029-108">**Type de données**</span><span class="sxs-lookup"><span data-stu-id="87029-108">**Data Type**</span></span>|<span data-ttu-id="87029-109">**Description**</span><span class="sxs-lookup"><span data-stu-id="87029-109">**Description**</span></span>|<span data-ttu-id="87029-110">**Restrictions**</span><span class="sxs-lookup"><span data-stu-id="87029-110">**Restrictions**</span></span>|<span data-ttu-id="87029-111">**Commentaires**</span><span class="sxs-lookup"><span data-stu-id="87029-111">**Comments**</span></span>|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|<span data-ttu-id="87029-112">FullName</span><span class="sxs-lookup"><span data-stu-id="87029-112">FullName</span></span>|<span data-ttu-id="87029-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="87029-113">Attribute</span></span>|<span data-ttu-id="87029-114">xs:string</span><span class="sxs-lookup"><span data-stu-id="87029-114">xs:string</span></span>|<span data-ttu-id="87029-115">Spécifie le nom complet du mappage.</span><span class="sxs-lookup"><span data-stu-id="87029-115">Specifies the full name of the map.</span></span>|<span data-ttu-id="87029-116">Facultatif</span><span class="sxs-lookup"><span data-stu-id="87029-116">Not required</span></span>|<span data-ttu-id="87029-117">Valeur par défaut : vide</span><span class="sxs-lookup"><span data-stu-id="87029-117">Default value: empty</span></span>|  
|<span data-ttu-id="87029-118">AssemblyQualifiedName</span><span class="sxs-lookup"><span data-stu-id="87029-118">AssemblyQualifiedName</span></span>|<span data-ttu-id="87029-119">Attribut</span><span class="sxs-lookup"><span data-stu-id="87029-119">Attribute</span></span>|<span data-ttu-id="87029-120">xs:string</span><span class="sxs-lookup"><span data-stu-id="87029-120">xs:string</span></span>|<span data-ttu-id="87029-121">Spécifie le nom qualifié d'assembly du mappage.</span><span class="sxs-lookup"><span data-stu-id="87029-121">Specifies the assembly qualified name of the map.</span></span>|<span data-ttu-id="87029-122">Facultatif</span><span class="sxs-lookup"><span data-stu-id="87029-122">Not required</span></span>|<span data-ttu-id="87029-123">Valeur par défaut : vide</span><span class="sxs-lookup"><span data-stu-id="87029-123">Default value: empty</span></span>|