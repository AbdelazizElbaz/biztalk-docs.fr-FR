---
title: "OutboundTransforms (nœud ReceivePort) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: OutboundTransforms node [binding file]
ms.assetid: 6deea062-4eb0-47ed-869c-ed6ec9290ea7
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fc6fa0bc804fad0d0ddea79614c392769452f1c7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="outboundtransforms-receiveport-node"></a><span data-ttu-id="ea678-102">OutboundTransforms (nœud ReceivePort)</span><span class="sxs-lookup"><span data-stu-id="ea678-102">OutboundTransforms (ReceivePort Node)</span></span>
<span data-ttu-id="ea678-103">Le nœud OutboundTransforms du nœud ReceivePort d'un fichier de liaison contient le regroupement des transformations sortantes d'un port de réception bidirectionnel exporté avec le fichier de liaison.</span><span class="sxs-lookup"><span data-stu-id="ea678-103">The OutboundTransforms node of the ReceivePort node of a binding file contains the collection of outbound transforms of a two-way receive port that is exported with the binding file.</span></span>  
  
## <a name="nodes-in-the-outboundtransforms-node"></a><span data-ttu-id="ea678-104">Nœuds du nœud OutboundTransforms</span><span class="sxs-lookup"><span data-stu-id="ea678-104">Nodes in the OutboundTransforms node</span></span>  
 <span data-ttu-id="ea678-105">Le tableau suivant répertorie les propriétés que vous pouvez définir pour ce nœud d'un fichier de liaison :</span><span class="sxs-lookup"><span data-stu-id="ea678-105">The following table lists the properties that can be set for this node of a binding file:</span></span>  
  
|<span data-ttu-id="ea678-106">**Nom**</span><span class="sxs-lookup"><span data-stu-id="ea678-106">**Name**</span></span>|<span data-ttu-id="ea678-107">**Type de nœud**</span><span class="sxs-lookup"><span data-stu-id="ea678-107">**Node Type**</span></span>|<span data-ttu-id="ea678-108">**Type de données**</span><span class="sxs-lookup"><span data-stu-id="ea678-108">**Data Type**</span></span>|<span data-ttu-id="ea678-109">**Description**</span><span class="sxs-lookup"><span data-stu-id="ea678-109">**Description**</span></span>|<span data-ttu-id="ea678-110">**Restrictions**</span><span class="sxs-lookup"><span data-stu-id="ea678-110">**Restrictions**</span></span>|<span data-ttu-id="ea678-111">**Commentaires**</span><span class="sxs-lookup"><span data-stu-id="ea678-111">**Comments**</span></span>|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|[<span data-ttu-id="ea678-112">Transformation (nœud OutboundTransforms)</span><span class="sxs-lookup"><span data-stu-id="ea678-112">Transform (OutboundTransforms Node)</span></span>](../core/transform-outboundtransforms-node.md)|<span data-ttu-id="ea678-113">Record</span><span class="sxs-lookup"><span data-stu-id="ea678-113">Record</span></span>|<span data-ttu-id="ea678-114">Transform (ComplexType)</span><span class="sxs-lookup"><span data-stu-id="ea678-114">Transform (ComplexType)</span></span>|<span data-ttu-id="ea678-115">Spécifie un mappage BizTalk Server, ou transformation, qui est un élément représentant le mappage entre un schéma source et un schéma de destination.</span><span class="sxs-lookup"><span data-stu-id="ea678-115">Specifies a BizTalk Server map, or transform, which is an item that represents the mapping between a source schema and destination schema.</span></span>|<span data-ttu-id="ea678-116">Facultatif</span><span class="sxs-lookup"><span data-stu-id="ea678-116">Not required</span></span>|<span data-ttu-id="ea678-117">Valeur par défaut : Aucun</span><span class="sxs-lookup"><span data-stu-id="ea678-117">Default value: none</span></span>|