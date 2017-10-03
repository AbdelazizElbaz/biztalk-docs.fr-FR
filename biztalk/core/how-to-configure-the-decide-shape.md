---
title: "Comment configurer la forme décider | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Decide shape [Orchestration Designer]
- Decide shape [Orchestration Designer], configuring
- Decide shape [Orchestration Designer], branching
- configuring [Orchestration Designer], Decide shapes
ms.assetid: 70910861-3834-49e7-ab1e-d62730ea2a95
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a22368134e2c1a0d8deb277e186792158a7c2dd0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-the-decide-shape"></a><span data-ttu-id="baae1-102">Configuration de la forme Décider</span><span class="sxs-lookup"><span data-stu-id="baae1-102">How to Configure the Decide Shape</span></span>
![](../core/media/ebiz-orch-decide.gif "ebiz_orch_decide")  
<span data-ttu-id="baae1-103">Forme Décider</span><span class="sxs-lookup"><span data-stu-id="baae1-103">Decide shape</span></span>  
  
 <span data-ttu-id="baae1-104">Chaque branche d’un **décider** forme, à l’exception de la **else** créer une branche, est associé à une règle.</span><span class="sxs-lookup"><span data-stu-id="baae1-104">Each branch of a **Decide** shape, except the **else** branch, has a rule associated with it.</span></span> <span data-ttu-id="baae1-105">Vous pouvez utiliser l'Éditeur d'expression BizTalk pour créer une expression booléenne dans la règle évaluée pour l'exécution de cette branche.</span><span class="sxs-lookup"><span data-stu-id="baae1-105">You can use BizTalk Expression Editor to create a Boolean expression in the rule that is evaluated for the execution of that branch.</span></span> <span data-ttu-id="baae1-106">Étant donné que la **else** branche implique la négation de l’expression booléenne dans la branche précédente, il n’a pas une expression associée.</span><span class="sxs-lookup"><span data-stu-id="baae1-106">Because the **else** branch implies the negation of the Boolean expression in the previous branch, it does not have an expression associated with it.</span></span>  
  
 <span data-ttu-id="baae1-107">Sous la règle ou **else** clause, une branche d’un **décider** forme peut contenir des formes supplémentaires, comme toute autre partie de l’orchestration.</span><span class="sxs-lookup"><span data-stu-id="baae1-107">Below the rule or **else** clause, a branch of a **Decide** shape can contain additional shapes, just like any other part of the orchestration.</span></span>  
  
### <a name="to-configure-a-decide-shape"></a><span data-ttu-id="baae1-108">Pour configurer une forme Décider</span><span class="sxs-lookup"><span data-stu-id="baae1-108">To configure a Decide shape</span></span>  
  
1.  <span data-ttu-id="baae1-109">Si l’éditeur d’Expression BizTalk n’est pas visible, cliquez sur la règle, puis cliquez sur **modifier l’Expression booléenne**, ou dans la fenêtre Propriétés, cliquez sur le **points de suspension** (**...** ) bouton pour le **Expression** propriété.</span><span class="sxs-lookup"><span data-stu-id="baae1-109">If BizTalk Expression Editor is not visible, right-click the rule and click **Edit Boolean Expression**, or in the Properties window, click the **Ellipsis** (**...**) button for the **Expression** property.</span></span>  
  
2.  <span data-ttu-id="baae1-110">Dans Éditeur d’Expression BizTalk, créez une expression booléenne pour chaque branche sauf la **Else** branche.</span><span class="sxs-lookup"><span data-stu-id="baae1-110">In BizTalk Expression Editor, create a Boolean expression for each branch except the **Else** branch.</span></span> <span data-ttu-id="baae1-111">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="baae1-111">For example,</span></span>  
  
    ```  
    myMessage.Total > 1000  
    myObject.IsValid()  
    myMessage.VIP == true  
    ```  
  
### <a name="to-add-a-branch-to-a-decide-shape"></a><span data-ttu-id="baae1-112">Pour ajouter une branche à une forme Décider</span><span class="sxs-lookup"><span data-stu-id="baae1-112">To add a branch to a Decide shape</span></span>  
  
1.  <span data-ttu-id="baae1-113">Avec le bouton droit le **décider** mettre en forme, puis cliquez sur **nouvelle branche règles**.</span><span class="sxs-lookup"><span data-stu-id="baae1-113">Right-click the **Decide** shape, and then click **New Rule Branch**.</span></span>  
  
     <span data-ttu-id="baae1-114">— Ou :</span><span class="sxs-lookup"><span data-stu-id="baae1-114">—Or—</span></span>  
  
2.  <span data-ttu-id="baae1-115">Faites glisser une nouvelle forme entre deux branches existantes.</span><span class="sxs-lookup"><span data-stu-id="baae1-115">Drag a new shape between two existing branches.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="baae1-116">Pour supprimer une branche d’un **décider** mettre en forme, cliquez sur la branche que vous souhaitez supprimer, puis cliquez sur **supprimer**, ou sélectionnez la branche de règle et appuyez sur la **supprimer** clé.</span><span class="sxs-lookup"><span data-stu-id="baae1-116">To remove a branch from a **Decide** shape, right-click the branch you want to remove, and then click **Delete**, or select the rule branch and press the **DELETE** key.</span></span>