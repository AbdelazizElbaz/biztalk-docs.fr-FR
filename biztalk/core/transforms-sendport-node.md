---
title: TRANSFORMS (nœud SendPort) | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Transforms node [binding file]
ms.assetid: b405397b-e394-44fa-b507-93896f800f66
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c1571a38841f6567279a27c58770f4198ba3eb56
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="transforms-sendport-node"></a><span data-ttu-id="6d960-102">Transforms (nœud SendPort)</span><span class="sxs-lookup"><span data-stu-id="6d960-102">Transforms (SendPort Node)</span></span>
<span data-ttu-id="6d960-103">Le nœud Transforms du nœud SendPort d'un fichier de liaison contient le regroupement des transformations sortantes d'un port d'envoi unidirectionnel exporté avec le fichier de liaison.</span><span class="sxs-lookup"><span data-stu-id="6d960-103">The Transforms node of the SendPort node of a binding file contains the collection of outbound transforms of a one way send port that is exported with the binding file.</span></span>  
  
## <a name="nodes-in-the-transforms-node"></a><span data-ttu-id="6d960-104">Nœuds du nœud Transforms</span><span class="sxs-lookup"><span data-stu-id="6d960-104">Nodes in the Transforms node</span></span>  
 <span data-ttu-id="6d960-105">Le tableau suivant répertorie les propriétés que vous pouvez définir pour ce nœud d'un fichier de liaison :</span><span class="sxs-lookup"><span data-stu-id="6d960-105">The following table lists the properties that can be set for this node of a binding file:</span></span>  
  
|<span data-ttu-id="6d960-106">**Nom**</span><span class="sxs-lookup"><span data-stu-id="6d960-106">**Name**</span></span>|<span data-ttu-id="6d960-107">**Type de nœud**</span><span class="sxs-lookup"><span data-stu-id="6d960-107">**Node Type**</span></span>|<span data-ttu-id="6d960-108">**Type de données**</span><span class="sxs-lookup"><span data-stu-id="6d960-108">**Data Type**</span></span>|<span data-ttu-id="6d960-109">**Description**</span><span class="sxs-lookup"><span data-stu-id="6d960-109">**Description**</span></span>|<span data-ttu-id="6d960-110">**Restrictions**</span><span class="sxs-lookup"><span data-stu-id="6d960-110">**Restrictions**</span></span>|<span data-ttu-id="6d960-111">**Commentaires**</span><span class="sxs-lookup"><span data-stu-id="6d960-111">**Comments**</span></span>|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|[<span data-ttu-id="6d960-112">Transformation (nœud SendPort-transformations)</span><span class="sxs-lookup"><span data-stu-id="6d960-112">Transform (SendPort-Transforms Node)</span></span>](../core/transform-sendport-transforms-node.md)|<span data-ttu-id="6d960-113">Record</span><span class="sxs-lookup"><span data-stu-id="6d960-113">Record</span></span>|<span data-ttu-id="6d960-114">Transform (ComplexType)</span><span class="sxs-lookup"><span data-stu-id="6d960-114">Transform (ComplexType)</span></span>|<span data-ttu-id="6d960-115">Spécifie un mappage BizTalk Server, ou transformation, qui est un élément représentant le mappage entre un schéma source et un schéma de destination.</span><span class="sxs-lookup"><span data-stu-id="6d960-115">Specifies a BizTalk Server map, or transform, which is an item that represents the mapping between a source schema and destination schema.</span></span>|<span data-ttu-id="6d960-116">Facultatif</span><span class="sxs-lookup"><span data-stu-id="6d960-116">Not required</span></span>|<span data-ttu-id="6d960-117">Valeur par défaut : Aucun</span><span class="sxs-lookup"><span data-stu-id="6d960-117">Default value: none</span></span>|