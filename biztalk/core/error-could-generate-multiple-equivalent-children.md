---
title: "Erreur : génération de plusieurs enfants équivalent possible | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: bts10.map.error.couldGenMultipleEquivChildren
ms.assetid: ef3ea6db-6759-4f38-804c-e32a1f24d758
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 686899c2871ded25f6901e919e9283694b9bacf0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="error---could-generate-multiple-equivalent-children"></a><span data-ttu-id="b4632-102">Erreur : génération de plusieurs enfants équivalent possible</span><span class="sxs-lookup"><span data-stu-id="b4632-102">Error - Could Generate Multiple Equivalent Children</span></span>
<span data-ttu-id="b4632-103">**Code d’erreur**</span><span class="sxs-lookup"><span data-stu-id="b4632-103">**Error Code**</span></span>  
  
 <span data-ttu-id="b4632-104">btm1026</span><span class="sxs-lookup"><span data-stu-id="b4632-104">btm1026</span></span>  
  
 <span data-ttu-id="b4632-105">**Explication**</span><span class="sxs-lookup"><span data-stu-id="b4632-105">**Explanation**</span></span>  
  
 <span data-ttu-id="b4632-106">Des liens vers le schéma de destination inappropriée permettent à plusieurs nœuds au sein d’un **équivalent** nœud de groupe.</span><span class="sxs-lookup"><span data-stu-id="b4632-106">Links to the destination schema inappropriately enable multiple nodes within an **Equivalent** group node to be generated.</span></span>  
  
 <span data-ttu-id="b4632-107">**Action de l’utilisateur**</span><span class="sxs-lookup"><span data-stu-id="b4632-107">**User Action**</span></span>  
  
 <span data-ttu-id="b4632-108">Corrigez les liens vers le schéma de destination, à l’aide des fonctoids logiques, ainsi qu’un seul nœud dans le **équivalent** nœud de groupe peut être généré lors du mappage.</span><span class="sxs-lookup"><span data-stu-id="b4632-108">Rework the links into the destination schema, potentially using logical functoids, so that only a single node within the **Equivalent** group node can be generated during mapping.</span></span>