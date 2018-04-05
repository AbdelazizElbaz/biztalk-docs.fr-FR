---
title: Mappage (nœud mappages) | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Mapping node [binding file]
ms.assetid: bc54c476-505c-4020-b7df-1d19f86329aa
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b2c62d46e4d5c2b73eee5094ecda0e20c039798a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="mapping-mappings-node"></a><span data-ttu-id="3fae9-102">Mappage (nœud Mappages)</span><span class="sxs-lookup"><span data-stu-id="3fae9-102">Mapping (Mappings Node)</span></span>
<span data-ttu-id="3fae9-103">Le nœud Mappage d'un fichier de liaison décrit le mappage entre un port de tiers et une opération de type de ports de rôle du tiers inscrit.</span><span class="sxs-lookup"><span data-stu-id="3fae9-103">The Mapping node of a binding file describes the mapping between a party port and role port type operation for the enlisted party.</span></span>  
  
## <a name="nodes-in-the-mapping-node"></a><span data-ttu-id="3fae9-104">Nœuds du nœud Mappage</span><span class="sxs-lookup"><span data-stu-id="3fae9-104">Nodes in the Mapping node</span></span>  
 <span data-ttu-id="3fae9-105">Le tableau suivant répertorie les propriétés que vous pouvez définir pour ce nœud d'un fichier de liaison :</span><span class="sxs-lookup"><span data-stu-id="3fae9-105">The following table lists the properties that can be set for this node of a binding file:</span></span>  
  
|<span data-ttu-id="3fae9-106">**Nom**</span><span class="sxs-lookup"><span data-stu-id="3fae9-106">**Name**</span></span>|<span data-ttu-id="3fae9-107">**Type de nœud**</span><span class="sxs-lookup"><span data-stu-id="3fae9-107">**Node Type**</span></span>|<span data-ttu-id="3fae9-108">**Type de données**</span><span class="sxs-lookup"><span data-stu-id="3fae9-108">**Data Type**</span></span>|<span data-ttu-id="3fae9-109">**Description**</span><span class="sxs-lookup"><span data-stu-id="3fae9-109">**Description**</span></span>|<span data-ttu-id="3fae9-110">**Restrictions**</span><span class="sxs-lookup"><span data-stu-id="3fae9-110">**Restrictions**</span></span>|<span data-ttu-id="3fae9-111">**Commentaires**</span><span class="sxs-lookup"><span data-stu-id="3fae9-111">**Comments**</span></span>|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|<span data-ttu-id="3fae9-112">PortTypeName</span><span class="sxs-lookup"><span data-stu-id="3fae9-112">PortTypeName</span></span>|<span data-ttu-id="3fae9-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="3fae9-113">Attribute</span></span>|<span data-ttu-id="3fae9-114">xs:string</span><span class="sxs-lookup"><span data-stu-id="3fae9-114">xs:string</span></span>|<span data-ttu-id="3fae9-115">Spécifie le nom du type de port.</span><span class="sxs-lookup"><span data-stu-id="3fae9-115">Specifies the name of the port type.</span></span>|<span data-ttu-id="3fae9-116">Facultatif</span><span class="sxs-lookup"><span data-stu-id="3fae9-116">Not required</span></span>|<span data-ttu-id="3fae9-117">Valeur par défaut : vide</span><span class="sxs-lookup"><span data-stu-id="3fae9-117">Default value: empty</span></span>|  
|<span data-ttu-id="3fae9-118">NomOpération</span><span class="sxs-lookup"><span data-stu-id="3fae9-118">OperationName</span></span>|<span data-ttu-id="3fae9-119">Attribut</span><span class="sxs-lookup"><span data-stu-id="3fae9-119">Attribute</span></span>|<span data-ttu-id="3fae9-120">xs:string</span><span class="sxs-lookup"><span data-stu-id="3fae9-120">xs:string</span></span>|<span data-ttu-id="3fae9-121">Spécifie l'opération correspondant à ce type de port.</span><span class="sxs-lookup"><span data-stu-id="3fae9-121">Specifies the operation belonging to this port type.</span></span>|<span data-ttu-id="3fae9-122">Facultatif</span><span class="sxs-lookup"><span data-stu-id="3fae9-122">Not required</span></span>|<span data-ttu-id="3fae9-123">Valeur par défaut : vide</span><span class="sxs-lookup"><span data-stu-id="3fae9-123">Default value: empty</span></span>|  
|[<span data-ttu-id="3fae9-124">SendPortRef</span><span class="sxs-lookup"><span data-stu-id="3fae9-124">SendPortRef</span></span>](../core/sendportref-mapping-node.md)|<span data-ttu-id="3fae9-125">Record</span><span class="sxs-lookup"><span data-stu-id="3fae9-125">Record</span></span>|<span data-ttu-id="3fae9-126">SendPortRef (ComplexType)</span><span class="sxs-lookup"><span data-stu-id="3fae9-126">SendPortRef (ComplexType)</span></span>|<span data-ttu-id="3fae9-127">Nœud du conteneur de la liste des ports d'envoi associée à un mappage.</span><span class="sxs-lookup"><span data-stu-id="3fae9-127">Container node for the list of send ports associated with a mapping.</span></span>|<span data-ttu-id="3fae9-128">Facultatif</span><span class="sxs-lookup"><span data-stu-id="3fae9-128">Not required</span></span>|<span data-ttu-id="3fae9-129">Valeur par défaut : Aucun</span><span class="sxs-lookup"><span data-stu-id="3fae9-129">Default value: none</span></span>|