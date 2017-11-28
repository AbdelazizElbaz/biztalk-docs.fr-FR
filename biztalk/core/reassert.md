---
title: "Redéclarer | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Assert function [Business Rules Engine]
ms.assetid: 9cd640a2-bfeb-4c7a-b737-1c92cc122a9c
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 22fcc8be7760d85a12cb05c53137177703c0fa73
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="reassert"></a><span data-ttu-id="46f39-102">Reassert</span><span class="sxs-lookup"><span data-stu-id="46f39-102">Reassert</span></span>
<span data-ttu-id="46f39-103">Pour *redéclarer* signifie appeler le **Assert** fonction sur un objet qui existe déjà dans le moteur de mémoire de travail.</span><span class="sxs-lookup"><span data-stu-id="46f39-103">To *reassert* means to call the **Assert** function on an object that is already in the engine's working memory.</span></span> <span data-ttu-id="46f39-104">Une commande de redéclaration équivaut à émettre une commande Rétracter pour l'objet, suivie d'une commande Déclarer.</span><span class="sxs-lookup"><span data-stu-id="46f39-104">A reassert command is equivalent to issuing a retract command for the object, followed by an assert command.</span></span>  
  
## <a name="net-objects"></a><span data-ttu-id="46f39-105">Objets .NET</span><span class="sxs-lookup"><span data-stu-id="46f39-105">.NET Objects</span></span>  
 <span data-ttu-id="46f39-106">L'objet est d'abord rétracté et toutes les actions sur l'agenda pour les règles qui utilisent cet objet (dans un prédicat ou une action) sont supprimées.</span><span class="sxs-lookup"><span data-stu-id="46f39-106">The object is first retracted and any actions on the agenda for rules that use the object (in a predicate or action) are removed.</span></span> <span data-ttu-id="46f39-107">L'objet est ensuite redéclaré dans la mémoire de travail et évalué comme tout objet nouvellement déclaré.</span><span class="sxs-lookup"><span data-stu-id="46f39-107">The object is then asserted back into working memory and evaluated as any object that is newly asserted.</span></span> <span data-ttu-id="46f39-108">Cela signifie que toutes les règles qui utilisent l'objet dans un prédicat sont réévaluées et que leurs actions sont ajoutées à l'agenda selon les nécessités.</span><span class="sxs-lookup"><span data-stu-id="46f39-108">This means that any rules that use the object in a predicate are re-evaluated and their actions are added to the agenda as appropriate.</span></span> <span data-ttu-id="46f39-109">Toutes les règles qui auparavant **true** et utilisez uniquement l’objet dans leurs actions verront ces actions rajoutées à l’agenda.</span><span class="sxs-lookup"><span data-stu-id="46f39-109">Any rules that previously evaluated to **true** and only use the object in their actions will have their actions re-added to the agenda.</span></span>  
  
## <a name="typedxmldocument"></a><span data-ttu-id="46f39-110">TypedXmlDocument</span><span class="sxs-lookup"><span data-stu-id="46f39-110">TypedXmlDocument</span></span>  
 <span data-ttu-id="46f39-111">Lorsqu’un niveau supérieur **TypedXmlDocument** (**TXD**) est redéclaré, l’enfant **TXD**s qui sont créés lorsque le niveau supérieur **TXD** est initialement assertion ont des comportements différents selon l’état de l’enfant **TXD**s.</span><span class="sxs-lookup"><span data-stu-id="46f39-111">When a top level **TypedXmlDocument** (**TXD**) is reasserted, the child **TXD**s that are created when the top level **TXD** is initially asserted have different behaviors depending on the state of the child **TXD**s.</span></span> <span data-ttu-id="46f39-112">Dans le cas d’un nouvel enfant nœud ou un nœud enfant qui n’est pas intègre, ce qui signifie qu’au moins un de ses champs a été modifié dans la stratégie à l’aide d’une action de règle, une assertion, ou redéclarez action est effectué sur le nœud enfant.</span><span class="sxs-lookup"><span data-stu-id="46f39-112">In the case of a new child node or a child node that is dirty, meaning that at least one of its fields has been changed in the policy by using a rule action, an assert, or reassert action is performed on the child node.</span></span> <span data-ttu-id="46f39-113">Tout nœud enfant existant dont les champs n'ont pas été modifiés reste dans la mémoire de travail.</span><span class="sxs-lookup"><span data-stu-id="46f39-113">Any existing child node that is not dirty remains in the working memory.</span></span> <span data-ttu-id="46f39-114">L'exemple suivant est un scénario simplifié qui décrit le comportement des nœuds enfants quand leur nœud parent est redéclaré.</span><span class="sxs-lookup"><span data-stu-id="46f39-114">The following example is a simplified scenario that describes the behaviors of the child nodes when their parent node is reasserted.</span></span>  
  
 <span data-ttu-id="46f39-115">Supposons que trois **TXD**s actuellement dans la mémoire de travail : **P**, **C**1, **C**2, et **C**3.</span><span class="sxs-lookup"><span data-stu-id="46f39-115">Assume there are three **TXD**s currently in the working memory: **P**, **C**1, **C**2, and **C**3.</span></span> <span data-ttu-id="46f39-116">**P** est le niveau supérieur **TXD**, le nœud parent ; chaque enfant nœud contient un champ **x**.</span><span class="sxs-lookup"><span data-stu-id="46f39-116">**P** is the top level **TXD**, the parent node; each child node contains a field **x**.</span></span>  
  
 <span data-ttu-id="46f39-117">**P**</span><span class="sxs-lookup"><span data-stu-id="46f39-117">**P**</span></span>  
  
 <span data-ttu-id="46f39-118">**C**1 (**C**1. **x** = 1)</span><span class="sxs-lookup"><span data-stu-id="46f39-118">**C**1 (**C**1.**x** = 1)</span></span>  
  
 <span data-ttu-id="46f39-119">**C**2 (**C**2. **x** = 1)</span><span class="sxs-lookup"><span data-stu-id="46f39-119">**C**2 (**C**2.**x** = 1)</span></span>  
  
 <span data-ttu-id="46f39-120">**C**3 (**C**3. **x** = 1)</span><span class="sxs-lookup"><span data-stu-id="46f39-120">**C**3 (**C**3.**x** = 1)</span></span>  
  
 <span data-ttu-id="46f39-121">Supposez ensuite que les opérations suivantes ont été effectuées suite à une action de règle :</span><span class="sxs-lookup"><span data-stu-id="46f39-121">Next, assume the following operations have been performed as a result of rule action:</span></span>  
  
-   <span data-ttu-id="46f39-122">Le champ (**x**) pour la valeur **C**2 est mis à jour.</span><span class="sxs-lookup"><span data-stu-id="46f39-122">The field (**x**) value for **C**2 is updated.</span></span>  
  
-   <span data-ttu-id="46f39-123">**C**3 est supprimé à l’aide de code utilisateur.</span><span class="sxs-lookup"><span data-stu-id="46f39-123">**C**3 is deleted by using user code.</span></span>  
  
-   <span data-ttu-id="46f39-124">Un nœud enfant supplémentaire, **D**, est ajouté à **P** à l’aide de code utilisateur.</span><span class="sxs-lookup"><span data-stu-id="46f39-124">An additional child node, **D**, is added to **P** by using user code.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="46f39-125">Le moteur des règles d'entreprise ne pourra pas identifier un nœud ayant perdu son intégrité à cause d'opérations que le moteur ne reconnaît pas,</span><span class="sxs-lookup"><span data-stu-id="46f39-125">A node will not be marked dirty by the Business Rule Engine from operations, of which the engine is not aware.</span></span> <span data-ttu-id="46f39-126">comme l'ajout, la suppression ou la modification d'un nœud, par programme, dans une application externe.</span><span class="sxs-lookup"><span data-stu-id="46f39-126">For example, adding, deleting, or modifying a node programmatically in an external application.</span></span>  
  
 <span data-ttu-id="46f39-127">Dans la mémoire de travail, les objets adoptent la nouvelle représentation suivante.</span><span class="sxs-lookup"><span data-stu-id="46f39-127">The new representation of the objects in working memory is as follows.</span></span>  
  
 <span data-ttu-id="46f39-128">**P**</span><span class="sxs-lookup"><span data-stu-id="46f39-128">**P**</span></span>  
  
 <span data-ttu-id="46f39-129">**C**1 (**C**1. **x** = 1)</span><span class="sxs-lookup"><span data-stu-id="46f39-129">**C**1 (**C**1.**x** = 1)</span></span>  
  
 <span data-ttu-id="46f39-130">**C**2 (**C**2. **x** = *0*)</span><span class="sxs-lookup"><span data-stu-id="46f39-130">**C**2 (**C**2.**x** = *0*)</span></span>  
  
 <span data-ttu-id="46f39-131">**D**</span><span class="sxs-lookup"><span data-stu-id="46f39-131">**D**</span></span>  
  
 <span data-ttu-id="46f39-132">Maintenant, Redéclarez **P**. Les points suivants résument le comportement des nœuds enfants :</span><span class="sxs-lookup"><span data-stu-id="46f39-132">Now, reassert **P**. The following points summarize the behaviors of the child nodes:</span></span>  
  
-   <span data-ttu-id="46f39-133">Nœud **C**2 est redéclaré, car il a modifié après son champ mis à jour.</span><span class="sxs-lookup"><span data-stu-id="46f39-133">Node **C**2 is reasserted, because it has become dirty after its field being updated.</span></span>  
  
-   <span data-ttu-id="46f39-134">Nœud **C**3 est rétracté de la mémoire de travail.</span><span class="sxs-lookup"><span data-stu-id="46f39-134">Node **C**3 is retracted from the working memory.</span></span>  
  
-   <span data-ttu-id="46f39-135">Nœud **D** est déclaré dans la mémoire de travail.</span><span class="sxs-lookup"><span data-stu-id="46f39-135">Node **D** is asserted into the working memory.</span></span>  
  
-   <span data-ttu-id="46f39-136">Nœud **C**1 reste dans la mémoire de travail, car il n’a pas mis à jour avant **P** soit redéclaré.</span><span class="sxs-lookup"><span data-stu-id="46f39-136">Node **C**1 remains unchanged in the working memory, because it was not updated before **P** was reasserted.</span></span>  
  
## <a name="typeddatatable"></a><span data-ttu-id="46f39-137">TypedDataTable</span><span class="sxs-lookup"><span data-stu-id="46f39-137">TypedDataTable</span></span>  
 <span data-ttu-id="46f39-138">Si **redéclarer** est émise sur un **TypedDataRow**, cette ligne est rétractée et puis déclarée dans la mémoire de travail.</span><span class="sxs-lookup"><span data-stu-id="46f39-138">If **Reassert** is issued on a **TypedDataRow**, that row is retracted and then asserted into working memory.</span></span> <span data-ttu-id="46f39-139">Si **redéclarer** est émise sur le **TypedDataTable**, toutes les **TypedDataRow**sont rétractées, puis déclarées.</span><span class="sxs-lookup"><span data-stu-id="46f39-139">If **Reassert** is issued on the **TypedDataTable**, all associated **TypedDataRow**s are retracted and then asserted.</span></span>  
  
## <a name="dataconnection"></a><span data-ttu-id="46f39-140">DataConnection</span><span class="sxs-lookup"><span data-stu-id="46f39-140">DataConnection</span></span>  
 <span data-ttu-id="46f39-141">Tous les **TypedDataRow**récupérées via les **DataConnection** sont retirées.</span><span class="sxs-lookup"><span data-stu-id="46f39-141">All **TypedDataRow**s retrieved through the **DataConnection** are retracted.</span></span> <span data-ttu-id="46f39-142">Tous les prédicats qui utilisent la **DataConnection** sont ensuite réévalués, à l’origine de la **DataConnection** pour être actualisé pour créer les **TypedDataRow**s.</span><span class="sxs-lookup"><span data-stu-id="46f39-142">All predicates that use the **DataConnection** are then re-evaluated, causing the **DataConnection** to be requeried to create the relevant **TypedDataRow**s.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46f39-143">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="46f39-143">See Also</span></span>  
 [<span data-ttu-id="46f39-144">Fonctions de contrôle du moteur</span><span class="sxs-lookup"><span data-stu-id="46f39-144">Engine Control Functions</span></span>](../core/engine-control-functions.md)