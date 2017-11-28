---
title: "Étape 1 : Configurer et activer le BatchControlPort Port de réception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: be248a05-e740-497a-b112-8ba3a57b020b
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d50289924062268db078844f2b3d2eaaccda23a2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-1-configure-and-enable-the-batchcontrolport-receive-port"></a><span data-ttu-id="82052-102">Étape 1 : Configurer et activer le BatchControlPort Port de réception</span><span class="sxs-lookup"><span data-stu-id="82052-102">Step 1: Configure and Enable the BatchControlPort Receive Port</span></span>
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]<span data-ttu-id="82052-103">BizTalk Accelerator pour HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) le programme d’installation crée un port de réception, le contrôle du lot le port, pour gérer les messages que l’orchestration de traitement par lots utilise pour démarrer, arrêter et le temps de lots.</span><span class="sxs-lookup"><span data-stu-id="82052-103"> BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) setup creates a receive port, the batch control port, to handle the messages that the batch orchestration uses to start, stop, and time batches.</span></span> <span data-ttu-id="82052-104">Ces messages incluent l’activation du lot, arrêt du lot et des messages du minuteur de lot.</span><span class="sxs-lookup"><span data-stu-id="82052-104">These messages include the batch activation, batch termination, and batch timer messages.</span></span> <span data-ttu-id="82052-105">Dans cette étape, vous configurez le pipeline de réception pour le port de contrôle de traitement par lots, activez le port.</span><span class="sxs-lookup"><span data-stu-id="82052-105">In this step, you configure the receive pipeline for the batch control port, and enable the port.</span></span>  
  
### <a name="to-configure-and-enable-batchcontrolport"></a><span data-ttu-id="82052-106">Pour configurer et activer BatchControlPort</span><span class="sxs-lookup"><span data-stu-id="82052-106">To configure and enable BatchControlPort</span></span>  
  
1.  <span data-ttu-id="82052-107">Démarrer **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="82052-107">Start **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="82052-108">Dans la Console Administration de BizTalk Server, développez **Administration de BizTalk Server**, **groupe BizTalk**, **Applications**, et **Application BizTalk 1**.</span><span class="sxs-lookup"><span data-stu-id="82052-108">In the BizTalk Server Administration Console, expand **BizTalk Server Administration**, **BizTalk Group**, **Applications**, and **BizTalk Application 1**.</span></span> <span data-ttu-id="82052-109">Cliquez sur **les emplacements de réception**.</span><span class="sxs-lookup"><span data-stu-id="82052-109">Click **Receive Locations**.</span></span>  
  
3.  <span data-ttu-id="82052-110">Avec le bouton droit **BatchControlLocation**, puis cliquez sur **désactiver**.</span><span class="sxs-lookup"><span data-stu-id="82052-110">Right-click **BatchControlLocation**, and then click **Disable**.</span></span>  
  
4.  <span data-ttu-id="82052-111">Avec le bouton droit **BatchControlLocation**, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="82052-111">Right-click **BatchControlLocation**, and then click **Properties**.</span></span>  
  
5.  <span data-ttu-id="82052-112">Dans la boîte de dialogue Propriétés de l’emplacement de réception pour **Pipeline de réception**, sélectionnez **BTAHL72XPipelines.BTAHL72XReceivePipeline**. Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="82052-112">In the Receive Location Properties dialog box, for **Receive Pipeline**, select **BTAHL72XPipelines.BTAHL72XReceivePipeline**.Click **OK**.</span></span>  
  
6.  <span data-ttu-id="82052-113">Dans la Console Administration de BizTalk, cliquez sur **BatchControlLocation**, puis cliquez sur **activer**.</span><span class="sxs-lookup"><span data-stu-id="82052-113">In the BizTalk Administration Console, right-click **BatchControlLocation**, and then click **Enable**.</span></span>  
  
 <span data-ttu-id="82052-114">Passez à [étape 2 : activer l’Orchestration de traitement par lots](../../adapters-and-accelerators/accelerator-hl7/step-2-enable-the-batch-orchestration.md).</span><span class="sxs-lookup"><span data-stu-id="82052-114">Proceed to [Step 2: Enable the Batch Orchestration](../../adapters-and-accelerators/accelerator-hl7/step-2-enable-the-batch-orchestration.md).</span></span>