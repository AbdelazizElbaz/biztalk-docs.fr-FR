---
title: Erreur - Max de la propriété promue | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- bts10.edit.error.promoPropMaxOccurs
ms.assetid: fc07367e-40f2-46e9-aeeb-bfa2498b1b37
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a9c8395757d19eff5241d47c31b15409a00b6faf
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="error---promoted-property-max-occurs"></a><span data-ttu-id="30a0f-102">Erreur - Max de la propriété promue</span><span class="sxs-lookup"><span data-stu-id="30a0f-102">Error - Promoted Property Max Occurs</span></span>
<span data-ttu-id="30a0f-103">**Code d’erreur**</span><span class="sxs-lookup"><span data-stu-id="30a0f-103">**Error Code**</span></span>  
  
 <span data-ttu-id="30a0f-104">BEC2002</span><span class="sxs-lookup"><span data-stu-id="30a0f-104">BEC2002</span></span>  
  
 <span data-ttu-id="30a0f-105">**Explication**</span><span class="sxs-lookup"><span data-stu-id="30a0f-105">**Explanation**</span></span>  
  
 <span data-ttu-id="30a0f-106">Le paramètre de la **Max Occurs** propriété du nœud en cours de promotion, ou de l’un de ses nœuds ancêtres, n’est pas compatible avec la promotion de propriété.</span><span class="sxs-lookup"><span data-stu-id="30a0f-106">The setting of the **Max Occurs** property of the node being promoted, or of one of its ancestor nodes, is incompatible with property promotion.</span></span> <span data-ttu-id="30a0f-107">La promotion de propriétés n'est pas possible pour les nœuds pouvant apparaître plusieurs fois dans un message d'instance.</span><span class="sxs-lookup"><span data-stu-id="30a0f-107">Property promotion is disallowed for nodes that can occur more than once in an instance message.</span></span> <span data-ttu-id="30a0f-108">Par conséquent, le **Max Occurs** propriétés de tous les nœuds à partir du nœud en cours de promotion et le nœud racine doivent être définies sur 1.</span><span class="sxs-lookup"><span data-stu-id="30a0f-108">Therefore, the **Max Occurs** properties of all nodes from the node being promoted back to the root node must be set to 1.</span></span>  
  
 <span data-ttu-id="30a0f-109">**Action de l’utilisateur**</span><span class="sxs-lookup"><span data-stu-id="30a0f-109">**User Action**</span></span>  
  
 <span data-ttu-id="30a0f-110">Vérifiez que le **Max Occurs** du nœud en cours de promotion et tous ses nœuds de niveau supérieur est définie sur un (1).</span><span class="sxs-lookup"><span data-stu-id="30a0f-110">Ensure that the **Max Occurs** property of the node being promoted and all of its ancestor nodes is set to one (1).</span></span>