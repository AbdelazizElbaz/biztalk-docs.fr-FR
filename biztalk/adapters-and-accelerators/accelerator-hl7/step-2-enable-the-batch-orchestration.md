---
title: "Étape 2 : Activer l’Orchestration de traitement par lots | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4badf807-f461-4d0a-a3b6-9f671e580d91
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0f8b18e41aacf61ac4e55e1c8047e9685179656a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-2-enable-the-batch-orchestration"></a><span data-ttu-id="f4080-102">Étape 2 : Activer l’Orchestration de traitement par lots</span><span class="sxs-lookup"><span data-stu-id="f4080-102">Step 2: Enable the Batch Orchestration</span></span>
<span data-ttu-id="f4080-103">L’orchestration de traitement par lots contrôle le traitement par lots de créer.</span><span class="sxs-lookup"><span data-stu-id="f4080-103">The batch orchestration controls the create batch process.</span></span> <span data-ttu-id="f4080-104">Conserve les références pour tous les messages à inclure dans le lot, contrôle de la transaction par lot sortant, génère le message du lot, achemine le lot sortant et traite les lots d’accusé de réception entrant.</span><span class="sxs-lookup"><span data-stu-id="f4080-104">It maintains references for all messages to be included in the batch, controls the outbound batch transaction, generates the batch message, routes the outgoing batch, and processes incoming acknowledgment batches.</span></span> <span data-ttu-id="f4080-105">Vous devez inscrire l’orchestration de traitement par lots pour le traitement par lots de créer fonctionner.</span><span class="sxs-lookup"><span data-stu-id="f4080-105">You need to enlist the batch orchestration for the create batch process to work.</span></span>  
  
### <a name="to-enable-the-batch-orchestration"></a><span data-ttu-id="f4080-106">Pour activer l’orchestration de traitement par lots</span><span class="sxs-lookup"><span data-stu-id="f4080-106">To enable the batch orchestration</span></span>  
  
1.  <span data-ttu-id="f4080-107">Dans la Console Administration de BizTalk, cliquez sur **Orchestrations**, avec le bouton droit **BatchOrchestration.Orchestration_1**, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="f4080-107">In the BizTalk Administration Console, click **Orchestrations**, right-click **BatchOrchestration.Orchestration_1**, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="f4080-108">Dans la boîte de dialogue Propriétés d’Orchestration dans l’arborescence de la console, cliquez sur **liaisons**.</span><span class="sxs-lookup"><span data-stu-id="f4080-108">In the Orchestration Properties dialog box, in the console tree, click **Bindings**.</span></span>  
  
3.  <span data-ttu-id="f4080-109">Dans le **liaisons** volet, pour **hôte**, sélectionnez **BizTalkServerApplication**.</span><span class="sxs-lookup"><span data-stu-id="f4080-109">In the **Bindings** pane, for **Host**, select **BizTalkServerApplication**.</span></span> <span data-ttu-id="f4080-110">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="f4080-110">Click **OK**.</span></span>  
  
4.  <span data-ttu-id="f4080-111">Dans la Console Administration de BizTalk, cliquez sur **BatchOrchestration.Orchestration_1**, puis cliquez sur **Enlist**.</span><span class="sxs-lookup"><span data-stu-id="f4080-111">In the BizTalk Administration Console, right-click **BatchOrchestration.Orchestration_1**, and then click **Enlist**.</span></span>  
  
 <span data-ttu-id="f4080-112">Passez à [étape 3 : créer et configurer un tiers de Destination](../../adapters-and-accelerators/accelerator-hl7/step-3-create-and-configure-a-destination-party.md).</span><span class="sxs-lookup"><span data-stu-id="f4080-112">Proceed to [Step 3: Create and Configure a Destination Party](../../adapters-and-accelerators/accelerator-hl7/step-3-create-and-configure-a-destination-party.md).</span></span>