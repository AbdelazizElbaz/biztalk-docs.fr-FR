---
title: "Comment configurer la forme Actions parallèles | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Parallel Actions shape [Orchestration Designer], Terminate shape [Orchestration Designer]
- Parallel Actions shape [Orchestration Designer], synchronizing data access
- Parallel Actions shape [Orchestration Designer]
- configuring [Orchestration Designer], Parallel Actions shapes
- Parallel Actions shape [Orchestration Designer], branching
- Parallel Actions shape [Orchestration Designer], about Parallel Actions shape
- Terminate shape [Orchestration Designer], Parallel Actions shape [Orchestration Designer]
- Parallel Actions shape [Orchestration Designer], configuring
ms.assetid: 396d6182-f5dd-4aab-9edc-92efe236fd3e
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 125d479a09eefb6771a884d2cddbfa98f34aeb36
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-the-parallel-actions-shape"></a><span data-ttu-id="2710c-102">Configuration de la forme Actions parallèles</span><span class="sxs-lookup"><span data-stu-id="2710c-102">How to Configure the Parallel Actions Shape</span></span>
![](../core/media/ebiz-orch-paralactions.gif "ebiz_orch_paralactions")  
<span data-ttu-id="2710c-103">Forme Actions parallèle</span><span class="sxs-lookup"><span data-stu-id="2710c-103">Parallel Actions shape</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="2710c-104">Si vous placez un **Terminate** mettre en forme à l’intérieur d’un **Actions parallèles** forme et la branche avec la **Terminate** son exécution, l’instance se termine immédiatement, indépendamment du Indique si des autres branches en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="2710c-104">If you place a **Terminate** shape inside a **Parallel Actions** shape, and the branch with the **Terminate** on it is run, the instance completes immediately, regardless of whether other branches have finished running.</span></span> <span data-ttu-id="2710c-105">En fonction de votre conception, les résultats peuvent être imprévisibles.</span><span class="sxs-lookup"><span data-stu-id="2710c-105">Depending on your design, results might be unpredictable in this case.</span></span>  
  
## <a name="synchronization-of-data-access"></a><span data-ttu-id="2710c-106">Synchronisation de l'accès aux données</span><span class="sxs-lookup"><span data-stu-id="2710c-106">Synchronization of data access</span></span>  
 <span data-ttu-id="2710c-107">Il est possible que plusieurs branches d’un **Actions parallèles** forme va tenter d’accéder aux mêmes données.</span><span class="sxs-lookup"><span data-stu-id="2710c-107">It is possible that more than one branch of a **Parallel Actions** shape will attempt to access the same data.</span></span> <span data-ttu-id="2710c-108">Pour éviter la génération d'erreurs, placez toutes les formes accédant aux données dans des étendues synchronisées.</span><span class="sxs-lookup"><span data-stu-id="2710c-108">To avoid errors, place any shapes that access the data inside synchronized scopes.</span></span> <span data-ttu-id="2710c-109">Vous pouvez spécifier dans les propriétés d’un **étendue** forme qu’elle est synchronisée ou pas.</span><span class="sxs-lookup"><span data-stu-id="2710c-109">You can specify in the properties of a **Scope** shape that it is synchronized or not synchronized.</span></span> <span data-ttu-id="2710c-110">Pour plus d’informations, consultez [étendues](../core/scopes.md).</span><span class="sxs-lookup"><span data-stu-id="2710c-110">For more information, see [Scopes](../core/scopes.md).</span></span>  
  
#### <a name="to-add-a-branch-to-a-parallel-actions-shape"></a><span data-ttu-id="2710c-111">Pour ajouter une branche à une forme Actions parallèles</span><span class="sxs-lookup"><span data-stu-id="2710c-111">To add a branch to a Parallel Actions shape</span></span>  
  
1.  <span data-ttu-id="2710c-112">Cliquez sur le **Actions parallèles** mettre en forme, puis cliquez sur **nouvelle branche parallèle**.</span><span class="sxs-lookup"><span data-stu-id="2710c-112">Right-click the **Parallel Actions** shape, and then click **New Parallel Branch**.</span></span>  
  
     <span data-ttu-id="2710c-113">— Ou :</span><span class="sxs-lookup"><span data-stu-id="2710c-113">—Or—</span></span>  
  
2.  <span data-ttu-id="2710c-114">Faites glisser une nouvelle forme entre deux branches existantes.</span><span class="sxs-lookup"><span data-stu-id="2710c-114">Drag a new shape between two existing branches.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2710c-115">Pour supprimer une branche d’un **Actions parallèles** mettre en forme, cliquez sur la branche que vous souhaitez supprimer, puis cliquez sur **supprimer**.</span><span class="sxs-lookup"><span data-stu-id="2710c-115">To remove a branch from a **Parallel Actions** shape, right-click the branch you want to remove, and then click **Delete**.</span></span>