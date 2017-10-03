---
title: "TRANSFORMS (nœud ReceivePort) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Transforms node [binding file]
ms.assetid: cd32f2fe-b70a-4153-86ec-bb1aa9bad0e4
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a7d039d95a1f28afa468078ff7547e9f298633bb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="transforms-receiveport-node"></a><span data-ttu-id="f1d4c-102">Transforms (nœud ReceivePort)</span><span class="sxs-lookup"><span data-stu-id="f1d4c-102">Transforms (ReceivePort Node)</span></span>
<span data-ttu-id="f1d4c-103">Le nœud Transforms du nœud ReceivePort d'un fichier de liaison contient le regroupement des transformations entrantes d'un port de réception unidirectionnel exporté avec ce fichier de liaison.</span><span class="sxs-lookup"><span data-stu-id="f1d4c-103">The Transforms node of the ReceivePort node of a binding file contains the collection of inbound transforms of a one way receive port that is exported with the binding file.</span></span>  
  
## <a name="nodes-in-the-transforms-node"></a><span data-ttu-id="f1d4c-104">Nœuds du nœud Transforms</span><span class="sxs-lookup"><span data-stu-id="f1d4c-104">Nodes in the Transforms node</span></span>  
 <span data-ttu-id="f1d4c-105">Le tableau suivant répertorie les propriétés que vous pouvez définir pour ce nœud d'un fichier de liaison :</span><span class="sxs-lookup"><span data-stu-id="f1d4c-105">The following table lists the properties that can be set for this node of a binding file:</span></span>  
  
|<span data-ttu-id="f1d4c-106">**Nom**</span><span class="sxs-lookup"><span data-stu-id="f1d4c-106">**Name**</span></span>|<span data-ttu-id="f1d4c-107">**Type de nœud**</span><span class="sxs-lookup"><span data-stu-id="f1d4c-107">**Node Type**</span></span>|<span data-ttu-id="f1d4c-108">**Type de données**</span><span class="sxs-lookup"><span data-stu-id="f1d4c-108">**Data Type**</span></span>|<span data-ttu-id="f1d4c-109">**Description**</span><span class="sxs-lookup"><span data-stu-id="f1d4c-109">**Description**</span></span>|<span data-ttu-id="f1d4c-110">**Restrictions**</span><span class="sxs-lookup"><span data-stu-id="f1d4c-110">**Restrictions**</span></span>|<span data-ttu-id="f1d4c-111">**Commentaires**</span><span class="sxs-lookup"><span data-stu-id="f1d4c-111">**Comments**</span></span>|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|[<span data-ttu-id="f1d4c-112">Transformation (nœud Transforms)</span><span class="sxs-lookup"><span data-stu-id="f1d4c-112">Transform (Transforms Node)</span></span>](../core/transform-transforms-node.md)|<span data-ttu-id="f1d4c-113">Record</span><span class="sxs-lookup"><span data-stu-id="f1d4c-113">Record</span></span>|<span data-ttu-id="f1d4c-114">Transform (ComplexType)</span><span class="sxs-lookup"><span data-stu-id="f1d4c-114">Transform (ComplexType)</span></span>|<span data-ttu-id="f1d4c-115">Spécifie un mappage BizTalk Server, ou transformation, qui est un élément représentant le mappage entre un schéma source et un schéma de destination.</span><span class="sxs-lookup"><span data-stu-id="f1d4c-115">Specifies a BizTalk Server map, or transform, which is an item that represents the mapping between a source schema and destination schema.</span></span>|<span data-ttu-id="f1d4c-116">Facultatif</span><span class="sxs-lookup"><span data-stu-id="f1d4c-116">Not required</span></span>|<span data-ttu-id="f1d4c-117">Valeur par défaut : Aucun</span><span class="sxs-lookup"><span data-stu-id="f1d4c-117">Default value: none</span></span>|