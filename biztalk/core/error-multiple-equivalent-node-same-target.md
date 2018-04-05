---
title: 'Erreur : plusieurs nœuds équivalents même cible | Documents Microsoft'
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- bts10.map.error.multipleEquivNodeSameTarget
ms.assetid: d8ca9f94-1d87-41bb-9479-6a01a5b6702d
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 12df4f7a68bb1eceaa3211c6aad6e9a581f17a4a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="error---multiple-equivalent-node-same-target"></a><span data-ttu-id="c65ec-102">Erreur : plusieurs nœuds équivalents même cible</span><span class="sxs-lookup"><span data-stu-id="c65ec-102">Error - Multiple Equivalent Node Same Target</span></span>
<span data-ttu-id="c65ec-103">**Code d’erreur**</span><span class="sxs-lookup"><span data-stu-id="c65ec-103">**Error Code**</span></span>  
  
 <span data-ttu-id="c65ec-104">btm1025</span><span class="sxs-lookup"><span data-stu-id="c65ec-104">btm1025</span></span>  
  
 <span data-ttu-id="c65ec-105">**Explication**</span><span class="sxs-lookup"><span data-stu-id="c65ec-105">**Explanation**</span></span>  
  
 <span data-ttu-id="c65ec-106">Les nœuds indiqués dans le schéma source, qui sont des nœuds enfants en conflit d’un **équivalent** nœud de groupe, sont liés au nœud indiqué dans le schéma de destination.</span><span class="sxs-lookup"><span data-stu-id="c65ec-106">The indicated nodes in the source schema, which are conflicting child nodes of an **Equivalent** group node, are both linked to the indicated node in the destination schema.</span></span> <span data-ttu-id="c65ec-107">Un seul de ces nœuds peut apparaître dans un message d'instance donné.</span><span class="sxs-lookup"><span data-stu-id="c65ec-107">Only one of these nodes in the source schema can occur in a given instance message.</span></span>  
  
 <span data-ttu-id="c65ec-108">**Action de l’utilisateur**</span><span class="sxs-lookup"><span data-stu-id="c65ec-108">**User Action**</span></span>  
  
 <span data-ttu-id="c65ec-109">Assurez-vous qu’un seul des enfants nœuds de la **équivalent** nœud de groupe est connecté à un nœud donné dans le schéma de destination.</span><span class="sxs-lookup"><span data-stu-id="c65ec-109">Ensure that only one of the child nodes of the **Equivalent** group node is connected to a given node in the destination schema.</span></span>