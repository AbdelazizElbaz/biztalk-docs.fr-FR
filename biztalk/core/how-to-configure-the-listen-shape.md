---
title: "Comment configurer la forme écouter | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Listen shape [Orchestration Designer], about Listen shape
- Listen shape [Orchestration Designer], configuring
- Listen shape [Orchestration Designer]
- Listen shape [Orchestration Designer], branching
- configuring [Orchestration Designer], Listen shapes
ms.assetid: 4765dc0a-a30e-4515-83bc-72b4f37268cf
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5bd8f8bbcc08d41430b95a9d177aeb06a5288be4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-the-listen-shape"></a><span data-ttu-id="147ab-102">Configuration de la forme Écouter</span><span class="sxs-lookup"><span data-stu-id="147ab-102">How to Configure the Listen Shape</span></span>
<span data-ttu-id="147ab-103">Les tâches d'écoute permettent aux applications d'attendre un ou plusieurs messages sur un ou plusieurs ports, ou de mettre un terme à l'écoute après un délai donné, et de créer une branche en fonction des résultats.</span><span class="sxs-lookup"><span data-stu-id="147ab-103">Listen actions enable applications to wait for one of several messages on one or more ports, or to stop waiting after a specified time-out interval, and branch based upon the results.</span></span>  
  
 ![](../core/media/ebiz-orch-listen.gif "ebiz_orch_listen")  
<span data-ttu-id="147ab-104">Forme Écouter</span><span class="sxs-lookup"><span data-stu-id="147ab-104">Listen shape</span></span>  
  
 <span data-ttu-id="147ab-105">Vous pouvez ajouter autant de branches que vous le souhaitez,</span><span class="sxs-lookup"><span data-stu-id="147ab-105">You can add as many branches as you like.</span></span> <span data-ttu-id="147ab-106">Vous pouvez placer n’importe quel autre forme sous initial **réception** ou **délai** forme.</span><span class="sxs-lookup"><span data-stu-id="147ab-106">You can place any other shape below the initial **Receive** or **Delay** shape.</span></span>  
  
 <span data-ttu-id="147ab-107">Il est possible d’utiliser une activation de réception dans un **écouter** forme.</span><span class="sxs-lookup"><span data-stu-id="147ab-107">It is possible to use an activation receive in a **Listen** shape.</span></span> <span data-ttu-id="147ab-108">Si une branche de la **écouter** forme contient une activation de réception, toutes les autres branches doivent également contenir l’activation reçoit et aucun délai d’expiration ne peut être utilisé.</span><span class="sxs-lookup"><span data-stu-id="147ab-108">If one branch of the **Listen** shape contains an activation receive, then all branches must contain activation receives, and no timeout can be used.</span></span> <span data-ttu-id="147ab-109">La réception avec activation doit être la première action de chaque branche.</span><span class="sxs-lookup"><span data-stu-id="147ab-109">The activation receive must be the first action in each branch.</span></span>  
  
 <span data-ttu-id="147ab-110">Vous pouvez utiliser la **écouter** forme au flux d’orchestration de branche en fonction de l’occurrence d’un ou plusieurs événements.</span><span class="sxs-lookup"><span data-stu-id="147ab-110">You can use the **Listen** shape to branch orchestration flow based on the occurrence of one or more events.</span></span> <span data-ttu-id="147ab-111">La première forme dans chaque branche doit être un **délai** ou un **réception** forme.</span><span class="sxs-lookup"><span data-stu-id="147ab-111">The first shape in each branch must be either a **Delay** or a **Receive** shape.</span></span> <span data-ttu-id="147ab-112">La première branche remplissant la condition, l’occurrence d’un délai d’attente pour un **délai** forme ou la réception d’un message pour un **réception** forme — s’exécute.</span><span class="sxs-lookup"><span data-stu-id="147ab-112">The first branch that meets its condition—the occurrence of a time-out for a **Delay** shape or the receipt of a message for a **Receive** shape—will execute.</span></span> <span data-ttu-id="147ab-113">Vous avez la possibilité d'ajouter de nouvelles branches, si besoin est.</span><span class="sxs-lookup"><span data-stu-id="147ab-113">You can add additional branches if needed.</span></span>  
  
### <a name="to-configure-a-listen-shape"></a><span data-ttu-id="147ab-114">Pour configurer une forme Écouter</span><span class="sxs-lookup"><span data-stu-id="147ab-114">To configure a Listen shape</span></span>  
  
1.  <span data-ttu-id="147ab-115">Sélectionnez une branche.</span><span class="sxs-lookup"><span data-stu-id="147ab-115">Select a branch.</span></span>  
  
2.  <span data-ttu-id="147ab-116">Dans la fenêtre Propriétés, définissez la **Type de branche** propriété.</span><span class="sxs-lookup"><span data-stu-id="147ab-116">In the Properties window, specify the **Branch Type** property.</span></span>  
  
     <span data-ttu-id="147ab-117">— Ou :</span><span class="sxs-lookup"><span data-stu-id="147ab-117">—Or—</span></span>  
  
     <span data-ttu-id="147ab-118">Faites glisser un **délai** ou **réception** forme sur la branche.</span><span class="sxs-lookup"><span data-stu-id="147ab-118">Drag a **Delay** or **Receive** shape onto the branch.</span></span>  
  
### <a name="to-add-a-branch-to-a-listen-shape"></a><span data-ttu-id="147ab-119">Pour ajouter une branche à une forme Écouter</span><span class="sxs-lookup"><span data-stu-id="147ab-119">To add a branch to a Listen shape</span></span>  
  
-   <span data-ttu-id="147ab-120">Cliquez sur le **écouter** mettre en forme, puis cliquez sur **nouvelle branche écouter**.</span><span class="sxs-lookup"><span data-stu-id="147ab-120">Right-click the **Listen** shape and then click **New Listen Branch**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="147ab-121">Pour supprimer une branche d’un **écouter** mettre en forme, cliquez sur la branche que vous souhaitez supprimer, puis cliquez sur **supprimer**.</span><span class="sxs-lookup"><span data-stu-id="147ab-121">To remove a branch from a **Listen** shape, right-click the branch you want to remove, and then click **Delete**.</span></span>