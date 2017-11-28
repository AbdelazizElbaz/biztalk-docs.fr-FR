---
title: "InboundTransforms (nœud SendPort) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: InboundTransforms node [binding file]
ms.assetid: 5ed239b9-13d8-4099-b779-08f589a722e9
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 03567b5ea6095e38370260e1f17055ab40da4d6f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="inboundtransforms-sendport-node"></a><span data-ttu-id="acc16-102">InboundTransforms (Nœud SendPort)</span><span class="sxs-lookup"><span data-stu-id="acc16-102">InboundTransforms (SendPort Node)</span></span>
<span data-ttu-id="acc16-103">Le nœud InboundTransforms du nœud SendPort d'un fichier de liaison contient le regroupement des transformations entrantes d'un port d'envoi bidirectionnel exporté avec le fichier de liaison.</span><span class="sxs-lookup"><span data-stu-id="acc16-103">The InboundTransforms node of the SendPort node of a binding file contains the collection of inbound transforms of a two-way send port that is exported with the binding file.</span></span>  
  
## <a name="nodes-in-the-inboundtransforms-node"></a><span data-ttu-id="acc16-104">Nœuds du nœud InboundTransforms</span><span class="sxs-lookup"><span data-stu-id="acc16-104">Nodes in the InboundTransforms node</span></span>  
 <span data-ttu-id="acc16-105">Le tableau suivant répertorie les propriétés que vous pouvez définir pour ce nœud d'un fichier de liaison :</span><span class="sxs-lookup"><span data-stu-id="acc16-105">The following table lists the properties that can be set for this node of a binding file:</span></span>  
  
|<span data-ttu-id="acc16-106">**Nom**</span><span class="sxs-lookup"><span data-stu-id="acc16-106">**Name**</span></span>|<span data-ttu-id="acc16-107">**Type de nœud**</span><span class="sxs-lookup"><span data-stu-id="acc16-107">**Node Type**</span></span>|<span data-ttu-id="acc16-108">**Type de données**</span><span class="sxs-lookup"><span data-stu-id="acc16-108">**Data Type**</span></span>|<span data-ttu-id="acc16-109">**Description**</span><span class="sxs-lookup"><span data-stu-id="acc16-109">**Description**</span></span>|<span data-ttu-id="acc16-110">**Restrictions**</span><span class="sxs-lookup"><span data-stu-id="acc16-110">**Restrictions**</span></span>|<span data-ttu-id="acc16-111">**Commentaires**</span><span class="sxs-lookup"><span data-stu-id="acc16-111">**Comments**</span></span>|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|[<span data-ttu-id="acc16-112">Transformation (nœud InboundTransforms)</span><span class="sxs-lookup"><span data-stu-id="acc16-112">Transform (InboundTransforms Node)</span></span>](../core/transform-inboundtransforms-node.md)|<span data-ttu-id="acc16-113">Record</span><span class="sxs-lookup"><span data-stu-id="acc16-113">Record</span></span>|<span data-ttu-id="acc16-114">Transform (ComplexType)</span><span class="sxs-lookup"><span data-stu-id="acc16-114">Transform (ComplexType)</span></span>|<span data-ttu-id="acc16-115">Spécifie un mappage BizTalk Server, ou transformation, qui est un élément représentant le mappage entre un schéma source et un schéma de destination.</span><span class="sxs-lookup"><span data-stu-id="acc16-115">Specifies a BizTalk Server map, or transform, which is an item that represents the mapping between a source schema and destination schema.</span></span>|<span data-ttu-id="acc16-116">Facultatif</span><span class="sxs-lookup"><span data-stu-id="acc16-116">Not required</span></span>|<span data-ttu-id="acc16-117">Valeur par défaut : Aucun</span><span class="sxs-lookup"><span data-stu-id="acc16-117">Default value: none</span></span>|