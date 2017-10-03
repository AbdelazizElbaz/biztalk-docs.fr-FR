---
title: "Liaison et démarrage de l’Orchestration FRR | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- FRR, binding orchestrations
- FRR, starting orchestrations
- bindings, orchestrations
- orchestrations, bindings
ms.assetid: b74a0116-e98b-4fec-b386-710ce421a1e2
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 81cf116fc03a8f2d898752a077e8347fd395a4a5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="binding-and-starting-the-frr-orchestration"></a><span data-ttu-id="bf630-102">Liaison et démarrage de l’Orchestration FRR</span><span class="sxs-lookup"><span data-stu-id="bf630-102">Binding and Starting the FRR Orchestration</span></span>
[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]<span data-ttu-id="bf630-103">inclut l’orchestration FRR comme un assembly déployé ([!INCLUDE[btsCoName](../../includes/btsconame-md.md)]. Solutions.FinancialServices.SWIFT.FrrOrchestration).</span><span class="sxs-lookup"><span data-stu-id="bf630-103"> includes the FRR orchestration as a deployed assembly ([!INCLUDE[btsCoName](../../includes/btsconame-md.md)].Solutions.FinancialServices.SWIFT.FrrOrchestration).</span></span> <span data-ttu-id="bf630-104">Vous devez démarrer cette orchestration.</span><span class="sxs-lookup"><span data-stu-id="bf630-104">You need to start this orchestration.</span></span>  
  
 <span data-ttu-id="bf630-105">**Résumé**</span><span class="sxs-lookup"><span data-stu-id="bf630-105">**Summary**</span></span>  
  
 <span data-ttu-id="bf630-106">Pour démarrer l’orchestration FRR, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="bf630-106">To start the FRR orchestration, do the following:</span></span>  
  
-   <span data-ttu-id="bf630-107">Lier l’orchestration FrrOrchestration.FrrMain en définissant l’hôte BizTalkServerApplication.</span><span class="sxs-lookup"><span data-stu-id="bf630-107">Bind the FrrOrchestration.FrrMain orchestration by setting the host to BizTalkServerApplication.</span></span>  
  
-   <span data-ttu-id="bf630-108">Démarrer l’orchestration FrrOrchestration.FrrMain.</span><span class="sxs-lookup"><span data-stu-id="bf630-108">Start the FrrOrchestration.FrrMain orchestration.</span></span>  
  
### <a name="to-bind-and-start-the-frr-orchestration"></a><span data-ttu-id="bf630-109">Pour lier et démarrer l’orchestration FRR</span><span class="sxs-lookup"><span data-stu-id="bf630-109">To bind and start the FRR orchestration</span></span>  
  
1.  <span data-ttu-id="bf630-110">Dans la Console Administration de BizTalk Server, développez **Administration de BizTalk Server**, **groupe BizTalk**, **Applications**, puis **BizTalk Application 1**.</span><span class="sxs-lookup"><span data-stu-id="bf630-110">In the BizTalk Server Administration Console, expand **BizTalk Server Administration**, **BizTalk Group**, **Applications**, and then **BizTalk Application 1**.</span></span> <span data-ttu-id="bf630-111">Cliquez sur **Orchestrations**.</span><span class="sxs-lookup"><span data-stu-id="bf630-111">Click **Orchestrations**.</span></span>  
  
2.  <span data-ttu-id="bf630-112">Dans le volet Orchestrations, cliquez sur le **FrrOrchestration.FrrMain** orchestration, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="bf630-112">In the Orchestrations pane, right-click the **FrrOrchestration.FrrMain** orchestration, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="bf630-113">Dans la boîte de dialogue Propriétés de l’Orchestration, cliquez sur **liaisons** dans le volet gauche.</span><span class="sxs-lookup"><span data-stu-id="bf630-113">In the Orchestration Properties dialog box, click **Bindings** in the left pane.</span></span> <span data-ttu-id="bf630-114">Pour **hôte**, sélectionnez **BizTalkServerApplication**.</span><span class="sxs-lookup"><span data-stu-id="bf630-114">For **Host**, select **BizTalkServerApplication**.</span></span> <span data-ttu-id="bf630-115">Cliquez sur **appliquer**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="bf630-115">Click **Apply**, and then click **OK**.</span></span>  
  
4.  <span data-ttu-id="bf630-116">Dans le volet Orchestrations, cliquez sur le **FrrMain** orchestration, puis cliquez sur **Démarrer**.</span><span class="sxs-lookup"><span data-stu-id="bf630-116">In the Orchestrations pane, right-click the **FrrMain** orchestration, and then click **Start**.</span></span>