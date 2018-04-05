---
title: 'Erreur : fonctoid Index avec trop d’index | Documents Microsoft'
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- bts10.map.error.indexFunctoidHasTooManyIndices
ms.assetid: 5dd2d5b4-3f7a-45be-b6f4-708b0a76805a
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3a22b49a921b957c0fb36f9e6b6925c991cc3cf6
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="error---index-functoid-has-too-many-indexes"></a><span data-ttu-id="69d37-102">Erreur : fonctoid Index avec trop d’index</span><span class="sxs-lookup"><span data-stu-id="69d37-102">Error - Index Functoid Has Too Many Indexes</span></span>
<span data-ttu-id="69d37-103">**Code d’erreur**</span><span class="sxs-lookup"><span data-stu-id="69d37-103">**Error Code**</span></span>  
  
 <span data-ttu-id="69d37-104">btm1016</span><span class="sxs-lookup"><span data-stu-id="69d37-104">btm1016</span></span>  
  
 <span data-ttu-id="69d37-105">**Explication**</span><span class="sxs-lookup"><span data-stu-id="69d37-105">**Explanation**</span></span>  
  
 <span data-ttu-id="69d37-106">Le fonctoid **Index** le fonctoid ne comporte trop de paramètres d’entrée d’index spécifiées.</span><span class="sxs-lookup"><span data-stu-id="69d37-106">The indicated **Index** functoid has too many index input parameters specified.</span></span> <span data-ttu-id="69d37-107">Le nombre de paramètres d’entrée d’index ne doit pas dépasser le nombre de boucle **enregistrement** nœuds au sein de laquelle le **champ** le nœud spécifié comme le premier paramètre d’entrée est imbriqué.</span><span class="sxs-lookup"><span data-stu-id="69d37-107">The number of index input parameters must not exceed the number of ancestor looping **Record** nodes within which the **Field** node specified as the first input parameter is nested.</span></span>  
  
 <span data-ttu-id="69d37-108">**Action de l’utilisateur**</span><span class="sxs-lookup"><span data-stu-id="69d37-108">**User Action**</span></span>  
  
 <span data-ttu-id="69d37-109">Sélectionnez le **Index** fonctoid, cliquez sur le bouton de sélection (**...** ) associés à la **paramètres d’entrée** propriété de Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] fenêtre Propriétés, puis, dans le **configurer \<fonctoid\> Fonctoid** boîte de dialogue, supprimez l’index en trop de paramètres d’entrée en sélectionnant et en cliquant sur le ![ ] (../core/media/bts-tls-paramdelete.gif "bts_tls_paramdelete") bouton pour chacun d’eux.</span><span class="sxs-lookup"><span data-stu-id="69d37-109">Select the indicated **Index** functoid, click the ellipsis (**...**) button associated with the **Input Parameters** property in the Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window, and then in the **Configure \<Functoid\> Functoid** dialog box, delete the excess index input parameters by selecting and clicking the  ![](../core/media/bts-tls-paramdelete.gif "bts_tls_paramdelete") button for each of them.</span></span>