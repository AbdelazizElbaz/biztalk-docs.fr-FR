---
title: "Tiers (nœud tiers inscrits) inscrit | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Enlisted Parties node [binding file]
ms.assetid: 2ff7b563-17c5-48e9-b33e-62c821188448
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 624f74d3b49b80e8000723c3f7451c52b37c8d3d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="enlisted-party-enlisted-parties-node"></a><span data-ttu-id="ef1bd-102">Tiers inscrit (nœud Tiers inscrits)</span><span class="sxs-lookup"><span data-stu-id="ef1bd-102">Enlisted Party (Enlisted Parties Node)</span></span>
<span data-ttu-id="ef1bd-103">Le nœud Tiers inscrit d'un fichier de liaison contient des informations sur le tiers enregistré associé à un transport exporté avec le fichier de liaison.</span><span class="sxs-lookup"><span data-stu-id="ef1bd-103">The Enlisted Party node of a binding file contains specific information about an enlisted party associated with a role that is exported with the binding file.</span></span>  
  
## <a name="nodes-in-the-enlisted-party-node"></a><span data-ttu-id="ef1bd-104">Nœuds figurant dans le nœud Tiers inscrits</span><span class="sxs-lookup"><span data-stu-id="ef1bd-104">Nodes in the Enlisted Party node</span></span>  
 <span data-ttu-id="ef1bd-105">Le tableau suivant répertorie les propriétés que vous pouvez définir pour ce nœud d'un fichier de liaison :</span><span class="sxs-lookup"><span data-stu-id="ef1bd-105">The following table lists the properties that can be set for this node of a binding file:</span></span>  
  
|<span data-ttu-id="ef1bd-106">**Nom**</span><span class="sxs-lookup"><span data-stu-id="ef1bd-106">**Name**</span></span>|<span data-ttu-id="ef1bd-107">**Type de nœud**</span><span class="sxs-lookup"><span data-stu-id="ef1bd-107">**Node Type**</span></span>|<span data-ttu-id="ef1bd-108">**Type de données**</span><span class="sxs-lookup"><span data-stu-id="ef1bd-108">**Data Type**</span></span>|<span data-ttu-id="ef1bd-109">**Description**</span><span class="sxs-lookup"><span data-stu-id="ef1bd-109">**Description**</span></span>|<span data-ttu-id="ef1bd-110">**Restrictions**</span><span class="sxs-lookup"><span data-stu-id="ef1bd-110">**Restrictions**</span></span>|<span data-ttu-id="ef1bd-111">**Commentaires**</span><span class="sxs-lookup"><span data-stu-id="ef1bd-111">**Comments**</span></span>|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|<span data-ttu-id="ef1bd-112">Nom</span><span class="sxs-lookup"><span data-stu-id="ef1bd-112">Name</span></span>|<span data-ttu-id="ef1bd-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="ef1bd-113">Attribute</span></span>|<span data-ttu-id="ef1bd-114">xs:string</span><span class="sxs-lookup"><span data-stu-id="ef1bd-114">xs:string</span></span>|<span data-ttu-id="ef1bd-115">Indique le nom du tiers inscrit.</span><span class="sxs-lookup"><span data-stu-id="ef1bd-115">Specifies the name of the enlisted party</span></span>|<span data-ttu-id="ef1bd-116">Facultatif</span><span class="sxs-lookup"><span data-stu-id="ef1bd-116">Not required</span></span>|<span data-ttu-id="ef1bd-117">Valeur par défaut : vide</span><span class="sxs-lookup"><span data-stu-id="ef1bd-117">Default value: empty</span></span>|  
|[<span data-ttu-id="ef1bd-118">Mappages</span><span class="sxs-lookup"><span data-stu-id="ef1bd-118">Mappings</span></span>](../core/mappings-enlisted-party-node.md)|<span data-ttu-id="ef1bd-119">Record</span><span class="sxs-lookup"><span data-stu-id="ef1bd-119">Record</span></span>|<span data-ttu-id="ef1bd-120">ArrayOfEnlistedPartyMapping (ComplexType)</span><span class="sxs-lookup"><span data-stu-id="ef1bd-120">ArrayOfEnlistedPartyMapping (ComplexType)</span></span>|<span data-ttu-id="ef1bd-121">Le nœud du conteneur des mappages entre les ports de tiers et les opérations de type de ports de rôle.</span><span class="sxs-lookup"><span data-stu-id="ef1bd-121">Container node for the mappings between party ports and role port type operations.</span></span>|<span data-ttu-id="ef1bd-122">Facultatif</span><span class="sxs-lookup"><span data-stu-id="ef1bd-122">Not required</span></span>|<span data-ttu-id="ef1bd-123">Valeur par défaut : Aucun</span><span class="sxs-lookup"><span data-stu-id="ef1bd-123">Default value: none</span></span>|