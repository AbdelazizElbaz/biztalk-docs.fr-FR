---
title: "Utilisation des points d’arrêt | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Orchestration Debugger, breakpoints
- Orchestration Debugger, suspended orchestrations
- Orchestration Debugger, Message Flow view
- Orchestration Debugger, service options
- Message Flow view [Orchestration Debugger]
ms.assetid: aad1a2b0-d705-49cd-85f7-b0ab2e473bcc
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 60e9cee77f105b132438e621651ee90c0090c1be
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="working-with-breakpoints"></a><span data-ttu-id="729ed-102">Utilisation de points d'arrêt</span><span class="sxs-lookup"><span data-stu-id="729ed-102">Working with Breakpoints</span></span>
<span data-ttu-id="729ed-103">Vous pouvez définir des points d'arrêt en joignant une orchestration suspendue ou en définissant un point d'arrêt sur une classe.</span><span class="sxs-lookup"><span data-stu-id="729ed-103">You can set breakpoints by attaching to a suspended orchestration, or by setting a breakpoint on a class.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="729ed-104">Lorsque vous annulez le déploiement d’un assembly, la base de données conserve les options de suivi et les informations de point d’arrêt pour cet assembly.</span><span class="sxs-lookup"><span data-stu-id="729ed-104">When you undeploy an assembly, the database maintains the tracking options and breakpoint information for that assembly.</span></span> <span data-ttu-id="729ed-105">Si, par la suite, vous redéployez le même assembly, ces informations sont restaurées.</span><span class="sxs-lookup"><span data-stu-id="729ed-105">If you subsequently deploy the same assembly again, the options and breakpoint information for that assembly are restored.</span></span>  
  
### <a name="to-attach-to-a-suspended-orchestration"></a><span data-ttu-id="729ed-106">Pour joindre une orchestration suspendue</span><span class="sxs-lookup"><span data-stu-id="729ed-106">To attach to a suspended orchestration</span></span>  
  
1.  <span data-ttu-id="729ed-107">Sélectionnez une orchestration suspendue automatiquement à l'aide d'une forme de suspension, puis passez à l'étape 3.</span><span class="sxs-lookup"><span data-stu-id="729ed-107">Select an automatically suspended orchestration using a suspend shape, and then go to Step 3.</span></span>  
  
2.  <span data-ttu-id="729ed-108">Actualisez la vue pour vérifier que l'instance apparaît maintenant avec l'état Suspendu.</span><span class="sxs-lookup"><span data-stu-id="729ed-108">Refresh the view to check that the instance now appears in a Suspended state.</span></span>  
  
3.  <span data-ttu-id="729ed-109">Cliquez sur **reprendre en mode de débogage**.</span><span class="sxs-lookup"><span data-stu-id="729ed-109">Click **Resume in Debug**.</span></span>  
  
     <span data-ttu-id="729ed-110">L'orchestration reprend à un état Point d'arrêt.</span><span class="sxs-lookup"><span data-stu-id="729ed-110">The orchestration resumes in an In Breakpoint state.</span></span> <span data-ttu-id="729ed-111">Vous pouvez procéder au débogage de façon interactive.</span><span class="sxs-lookup"><span data-stu-id="729ed-111">You can now debug interactively.</span></span>  
  
### <a name="to-switch-to-the-message-flow-view"></a><span data-ttu-id="729ed-112">Pour basculer vers l'affichage Flux message</span><span class="sxs-lookup"><span data-stu-id="729ed-112">To switch to the Message Flow view</span></span>  
  
-   <span data-ttu-id="729ed-113">Cliquez sur une cellule dans la liste des résultats et sélectionnez **flux Message** dans le menu contextuel.</span><span class="sxs-lookup"><span data-stu-id="729ed-113">Right-click a cell in the Results list and select **Message Flow** from the shortcut menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="729ed-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="729ed-114">See Also</span></span>  
 [<span data-ttu-id="729ed-115">Utilisation de la vue débogueur Orchestration</span><span class="sxs-lookup"><span data-stu-id="729ed-115">Working with the Orchestration Debugger View</span></span>](../core/working-with-the-orchestration-debugger-view.md)