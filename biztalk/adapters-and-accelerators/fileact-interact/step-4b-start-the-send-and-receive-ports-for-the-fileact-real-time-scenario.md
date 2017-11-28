---
title: "Étape 4 b : démarrez les Ports d’envoi et Ports de réception pour le scénario en temps réel FileAct | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c56b5f7b-551a-4bd2-97c7-0996f5d1b1a2
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9a9933f347d2da08dc2b8665dfd01530871a8cdf
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-4b-start-the-send-ports-and-receive-ports-for-the-fileact-real-time-scenario"></a><span data-ttu-id="a5fb5-102">Étape 4 b : démarrez les Ports d’envoi et Ports de réception pour le scénario en temps réel FileAct</span><span class="sxs-lookup"><span data-stu-id="a5fb5-102">Step 4B: Start the Send Ports and Receive Ports for the FileAct Real-Time Scenario</span></span>
<span data-ttu-id="a5fb5-103">Avant de commencer cette étape, vous devez effectuer [étape 4 a : démarrer le SWIFTNet Service pour le scénario en temps réel de FileAct](../../adapters-and-accelerators/fileact-interact/step-4a-start-the-swiftnet-service-for-the-fileact-real-time-scenario.md).</span><span class="sxs-lookup"><span data-stu-id="a5fb5-103">Before you begin this step, you must complete [Step 4A: Start the SWIFTNet Service for the FileAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-4a-start-the-swiftnet-service-for-the-fileact-real-time-scenario.md).</span></span>  
  
### <a name="to-start-the-send-ports-and-receive-ports"></a><span data-ttu-id="a5fb5-104">Pour démarrer les ports d’envoi et de ports de réception</span><span class="sxs-lookup"><span data-stu-id="a5fb5-104">To start the send ports and receive ports</span></span>  
  
1.  <span data-ttu-id="a5fb5-105">Démarrer **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="a5fb5-105">Start **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="a5fb5-106">Dans l’arborescence de la console, développez le groupe BizTalk, puis développez l’application BizTalk où vous avez créé les ports d’envoi.</span><span class="sxs-lookup"><span data-stu-id="a5fb5-106">In the console tree, expand the BizTalk group, and then expand the BizTalk application where you created the send ports.</span></span>  
  
3.  <span data-ttu-id="a5fb5-107">Pour chacun de ces ports d’envoi, cliquez sur le port d’envoi, puis cliquez sur **Démarrer**:</span><span class="sxs-lookup"><span data-stu-id="a5fb5-107">For each of the following send ports, right-click the send port, and then click **Start**:</span></span>  
  
    -   <span data-ttu-id="a5fb5-108">**Tutorial_FA_SendResponseToReceiver**</span><span class="sxs-lookup"><span data-stu-id="a5fb5-108">**Tutorial_FA_SendResponseToReceiver**</span></span>  
  
    -   <span data-ttu-id="a5fb5-109">**Tutorial_FA_SendResponseToSender**</span><span class="sxs-lookup"><span data-stu-id="a5fb5-109">**Tutorial_FA_SendResponseToSender**</span></span>  
  
    -   <span data-ttu-id="a5fb5-110">**Tutorial_FA_SendRequest_RealTime**</span><span class="sxs-lookup"><span data-stu-id="a5fb5-110">**Tutorial_FA_SendRequest_RealTime**</span></span>  
  
    -   <span data-ttu-id="a5fb5-111">**Tutorial_ GetStatusReports**</span><span class="sxs-lookup"><span data-stu-id="a5fb5-111">**Tutorial_ GetStatusReports**</span></span>  
  
4.  <span data-ttu-id="a5fb5-112">Dans l’arborescence de la console, développez le groupe BizTalk, puis développez l’application BizTalk où vous avez créé les emplacements de réception.</span><span class="sxs-lookup"><span data-stu-id="a5fb5-112">In the console tree, expand the BizTalk group, and then expand the BizTalk application where you created the receive locations.</span></span>  
  
5.  <span data-ttu-id="a5fb5-113">Pour chacun des emplacements de réception suivants, avec le bouton droit à l’emplacement de réception, puis cliquez sur **activer**:</span><span class="sxs-lookup"><span data-stu-id="a5fb5-113">For each of the following receive locations, right-click the receive location, and then click **Enable**:</span></span>  
  
    -   <span data-ttu-id="a5fb5-114">**Tutorial_FA_InputRequest_RealTime**</span><span class="sxs-lookup"><span data-stu-id="a5fb5-114">**Tutorial_FA_InputRequest_RealTime**</span></span>  
  
    -   <span data-ttu-id="a5fb5-115">**Tutorial_FA_HandleRequestOneWay_RealTime**</span><span class="sxs-lookup"><span data-stu-id="a5fb5-115">**Tutorial_FA_HandleRequestOneWay_RealTime**</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5fb5-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a5fb5-116">See Also</span></span>  
 <span data-ttu-id="a5fb5-117">[Étape 4 : Tester le scénario de bout en bout FileAct en temps réel](../../adapters-and-accelerators/fileact-interact/step-4-test-fileact-real-time-end-to-end-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="a5fb5-117">[Step 4: Test FileAct Real-Time End-to-End Scenario](../../adapters-and-accelerators/fileact-interact/step-4-test-fileact-real-time-end-to-end-scenario.md) </span></span>  
 <span data-ttu-id="a5fb5-118">[Étape 4 a : démarrer le Service SWIFTNet pour le scénario en temps réel FileAct](../../adapters-and-accelerators/fileact-interact/step-4a-start-the-swiftnet-service-for-the-fileact-real-time-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="a5fb5-118">[Step 4A: Start the SWIFTNet Service for the FileAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-4a-start-the-swiftnet-service-for-the-fileact-real-time-scenario.md) </span></span>  
 <span data-ttu-id="a5fb5-119">[Étape 4c : créer une Instance de Test pour le scénario en temps réel FileAct](../../adapters-and-accelerators/fileact-interact/step-4c-create-a-test-instance-for-the-fileact-real-time-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="a5fb5-119">[Step 4C: Create a Test Instance for the FileAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-4c-create-a-test-instance-for-the-fileact-real-time-scenario.md) </span></span>  
 [<span data-ttu-id="a5fb5-120">Étape 4d : tester une Instance valide pour le scénario en temps réel FileAct</span><span class="sxs-lookup"><span data-stu-id="a5fb5-120">Step 4D: Test a Valid Instance for the FileAct Real-Time Scenario</span></span>](../../adapters-and-accelerators/fileact-interact/step-4d-test-a-valid-instance-for-the-fileact-real-time-scenario.md)