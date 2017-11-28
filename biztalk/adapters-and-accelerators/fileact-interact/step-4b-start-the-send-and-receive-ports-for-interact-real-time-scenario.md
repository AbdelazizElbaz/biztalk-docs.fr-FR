---
title: "Étape 4 b : démarrer les Ports d’envoi et de réception pour le scénario en temps réel d’interagir | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dffee9a6-5877-4744-9b46-12ca4f8fa959
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3391f966fb1033ec1886f44b62158f910179d72f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-4b-start-the-send-ports-and-receive-ports-for-the-interact-real-time-scenario"></a><span data-ttu-id="3958c-102">Étape 4 b : démarrer les Ports d’envoi et de réception pour l’interaction scénario en temps réel</span><span class="sxs-lookup"><span data-stu-id="3958c-102">Step 4B: Start the Send Ports and Receive Ports for the InterAct Real-Time Scenario</span></span>
<span data-ttu-id="3958c-103">Avant de commencer cette étape, vous devez effectuer [étape 4 a : démarrer le SWIFTNet Service](../../adapters-and-accelerators/fileact-interact/step-4a-start-the-swiftnet-service.md).</span><span class="sxs-lookup"><span data-stu-id="3958c-103">Before you begin this step, you must complete [Step 4A: Start the SWIFTNet Service](../../adapters-and-accelerators/fileact-interact/step-4a-start-the-swiftnet-service.md).</span></span>  
  
### <a name="to-start-the-send-ports-and-receive-ports"></a><span data-ttu-id="3958c-104">Pour démarrer les ports d’envoi et de ports de réception</span><span class="sxs-lookup"><span data-stu-id="3958c-104">To start the send ports and receive ports</span></span>  
  
1.  <span data-ttu-id="3958c-105">Démarrer **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="3958c-105">Start **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="3958c-106">Dans l’arborescence de la console, développez le groupe BizTalk, puis développez l’application BizTalk où vous avez créé les ports d’envoi.</span><span class="sxs-lookup"><span data-stu-id="3958c-106">In the console tree, expand the BizTalk group, and then expand the BizTalk application where you created the send ports.</span></span>  
  
3.  <span data-ttu-id="3958c-107">Pour chacun de ces ports d’envoi, cliquez sur le port d’envoi, puis cliquez sur **Démarrer**:</span><span class="sxs-lookup"><span data-stu-id="3958c-107">For each of the following send ports, right-click the send port, and then click **Start**:</span></span>  
  
    -   <span data-ttu-id="3958c-108">**Tutorial_IA_SendResponseToReceiver**</span><span class="sxs-lookup"><span data-stu-id="3958c-108">**Tutorial_IA_SendResponseToReceiver**</span></span>  
  
    -   <span data-ttu-id="3958c-109">**Tutorial_IA_SendResponseToSender**</span><span class="sxs-lookup"><span data-stu-id="3958c-109">**Tutorial_IA_SendResponseToSender**</span></span>  
  
    -   <span data-ttu-id="3958c-110">**Tutorial_IA_SendRequest_RealTime**</span><span class="sxs-lookup"><span data-stu-id="3958c-110">**Tutorial_IA_SendRequest_RealTime**</span></span>  
  
4.  <span data-ttu-id="3958c-111">Dans l’arborescence de la console, développez le groupe BizTalk, puis développez l’application BizTalk où vous avez créé les emplacements de réception.</span><span class="sxs-lookup"><span data-stu-id="3958c-111">In the console tree, expand the BizTalk group, and then expand the BizTalk application where you created the receive locations.</span></span>  
  
5.  <span data-ttu-id="3958c-112">Pour chacun des emplacements de réception suivants, avec le bouton droit à l’emplacement de réception, puis cliquez sur **activer**:</span><span class="sxs-lookup"><span data-stu-id="3958c-112">For each of the following receive locations, right-click the receive location, and then click **Enable**:</span></span>  
  
    -   <span data-ttu-id="3958c-113">**Tutorial_IA_InputRequest_RealTime**</span><span class="sxs-lookup"><span data-stu-id="3958c-113">**Tutorial_IA_InputRequest_RealTime**</span></span>  
  
    -   <span data-ttu-id="3958c-114">**Tutorial_IA_HandleRequestOneWay_RealTime**</span><span class="sxs-lookup"><span data-stu-id="3958c-114">**Tutorial_IA_HandleRequestOneWay_RealTime**</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3958c-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3958c-115">See Also</span></span>  
 <span data-ttu-id="3958c-116">[Étape 4 : Tester l’interaction du scénario de bout en bout en temps réel](../../adapters-and-accelerators/fileact-interact/step-4-test-the-interact-real-time-end-to-end-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="3958c-116">[Step 4: Test the InterAct Real-Time End-to-End Scenario](../../adapters-and-accelerators/fileact-interact/step-4-test-the-interact-real-time-end-to-end-scenario.md) </span></span>  
 <span data-ttu-id="3958c-117">[Étape 4 a : démarrer le Service SWIFTNet](../../adapters-and-accelerators/fileact-interact/step-4a-start-the-swiftnet-service.md) </span><span class="sxs-lookup"><span data-stu-id="3958c-117">[Step 4A: Start the SWIFTNet Service](../../adapters-and-accelerators/fileact-interact/step-4a-start-the-swiftnet-service.md) </span></span>  
 <span data-ttu-id="3958c-118">[Étape 4c : créer une Instance de Test pour l’interaction du scénario en temps réel](../../adapters-and-accelerators/fileact-interact/step-4c-create-a-test-instance-for-the-interact-real-time-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="3958c-118">[Step 4C: Create a Test Instance for the InterAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-4c-create-a-test-instance-for-the-interact-real-time-scenario.md) </span></span>  
 [<span data-ttu-id="3958c-119">Étape 4d : tester une Instance valide pour l’interaction du scénario en temps réel</span><span class="sxs-lookup"><span data-stu-id="3958c-119">Step 4D: Test a Valid Instance for the InterAct Real-Time Scenario</span></span>](../../adapters-and-accelerators/fileact-interact/step-4d-test-a-valid-instance-for-the-interact-real-time-scenario.md)