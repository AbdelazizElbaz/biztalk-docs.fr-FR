---
title: "Étape 4 b : démarrez les Ports d’envoi et de réception pour et le scénario de transfert de FileAct | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0f8c34b1-24a5-4ac7-bb96-27834bc3c711
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: eb40a366a3c4952eaac9557ea04f5a84c846c81e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-4b-start-the-send-ports-and-receive-ports-for-the-fileact-store-and-forward-scenario"></a><span data-ttu-id="6c8ec-102">Étape 4 b : démarrez les Ports d’envoi et de réception pour et le scénario de transfert de FileAct</span><span class="sxs-lookup"><span data-stu-id="6c8ec-102">Step 4B: Start the Send Ports and Receive Ports for the FileAct Store and Forward Scenario</span></span>
<span data-ttu-id="6c8ec-103">Avant de commencer cette étape, vous devez effectuer [étape 4 a : démarrer le SWIFTNet Service pour et le scénario de transfert de FileAct](../../adapters-and-accelerators/fileact-interact/step-4a-start-the-swiftnet-service-for-the-fileact-store-and-forward-scenario.md).</span><span class="sxs-lookup"><span data-stu-id="6c8ec-103">Before you begin this step, you must complete [Step 4A: Start the SWIFTNet Service for the FileAct Store and Forward Scenario](../../adapters-and-accelerators/fileact-interact/step-4a-start-the-swiftnet-service-for-the-fileact-store-and-forward-scenario.md).</span></span>  
  
### <a name="to-start-the-send-ports-and-receive-ports"></a><span data-ttu-id="6c8ec-104">Pour démarrer les ports d’envoi et de ports de réception</span><span class="sxs-lookup"><span data-stu-id="6c8ec-104">To start the send ports and receive ports</span></span>  
  
1.  <span data-ttu-id="6c8ec-105">Démarrer **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="6c8ec-105">Start **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="6c8ec-106">Dans l’arborescence de la console, développez le groupe BizTalk, puis développez l’application BizTalk où vous avez créé les ports d’envoi.</span><span class="sxs-lookup"><span data-stu-id="6c8ec-106">In the console tree, expand the BizTalk group, and then expand the BizTalk application where you created the send ports.</span></span>  
  
3.  <span data-ttu-id="6c8ec-107">Pour chacun de ces ports d’envoi, cliquez sur le port d’envoi, puis cliquez sur **Démarrer**:</span><span class="sxs-lookup"><span data-stu-id="6c8ec-107">For each of the following send ports, right-click the send port, and then click **Start**:</span></span>  
  
    -   <span data-ttu-id="6c8ec-108">**Tutorial_FA_SendResponseToReceiver**</span><span class="sxs-lookup"><span data-stu-id="6c8ec-108">**Tutorial_FA_SendResponseToReceiver**</span></span>  
  
    -   <span data-ttu-id="6c8ec-109">**Tutorial_FA_SendRequest_SnF**</span><span class="sxs-lookup"><span data-stu-id="6c8ec-109">**Tutorial_FA_SendRequest_SnF**</span></span>  
  
    -   <span data-ttu-id="6c8ec-110">**Tutorial_ GetStatusReports**</span><span class="sxs-lookup"><span data-stu-id="6c8ec-110">**Tutorial_ GetStatusReports**</span></span>  
  
4.  <span data-ttu-id="6c8ec-111">Dans l’arborescence de la console, développez le groupe BizTalk, puis développez l’application BizTalk où vous avez créé les emplacements de réception.</span><span class="sxs-lookup"><span data-stu-id="6c8ec-111">In the console tree, expand the BizTalk group, and then expand the BizTalk application where you created the receive locations.</span></span>  
  
5.  <span data-ttu-id="6c8ec-112">Pour chacun des emplacements de réception suivants, avec le bouton droit à l’emplacement de réception, puis cliquez sur **activer**:</span><span class="sxs-lookup"><span data-stu-id="6c8ec-112">For each of the following receive locations, right-click the receive location, and then click **Enable**:</span></span>  
  
    -   <span data-ttu-id="6c8ec-113">**Tutorial_FA_InputRequest_SnF**</span><span class="sxs-lookup"><span data-stu-id="6c8ec-113">**Tutorial_FA_InputRequest_SnF**</span></span>  
  
    -   <span data-ttu-id="6c8ec-114">**Tutorial_FA_HandleRequestOneWay_SnF**</span><span class="sxs-lookup"><span data-stu-id="6c8ec-114">**Tutorial_FA_HandleRequestOneWay_SnF**</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c8ec-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6c8ec-115">See Also</span></span>  
 <span data-ttu-id="6c8ec-116">[Étape 4 : Tester et de scénario de bout en bout avant de FileAct](../../adapters-and-accelerators/fileact-interact/step-4-test-fileact-store-and-forward-end-to-end-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="6c8ec-116">[Step 4: Test FileAct Store and Forward End-to-End Scenario](../../adapters-and-accelerators/fileact-interact/step-4-test-fileact-store-and-forward-end-to-end-scenario.md) </span></span>  
 <span data-ttu-id="6c8ec-117">[Étape 4 a : démarrer le Service SWIFTNet pour et le scénario de transfert de FileAct](../../adapters-and-accelerators/fileact-interact/step-4a-start-the-swiftnet-service-for-the-fileact-store-and-forward-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="6c8ec-117">[Step 4A: Start the SWIFTNet Service for the FileAct Store and Forward Scenario](../../adapters-and-accelerators/fileact-interact/step-4a-start-the-swiftnet-service-for-the-fileact-store-and-forward-scenario.md) </span></span>  
 <span data-ttu-id="6c8ec-118">[Étape 4c : créer une Instance de Test pour et le scénario de transfert de FileAct](../../adapters-and-accelerators/fileact-interact/step-4c-create-a-test-instance-for-the-fileact-store-and-forward-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="6c8ec-118">[Step 4C: Create a Test Instance for the FileAct Store and Forward Scenario](../../adapters-and-accelerators/fileact-interact/step-4c-create-a-test-instance-for-the-fileact-store-and-forward-scenario.md) </span></span>  
 [<span data-ttu-id="6c8ec-119">Étape 4d : tester une Instance valide pour et le scénario de transfert de FileAct</span><span class="sxs-lookup"><span data-stu-id="6c8ec-119">Step 4D: Test a Valid Instance for the FileAct Store and Forward Scenario</span></span>](../../adapters-and-accelerators/fileact-interact/step-4d-test-a-valid-instance-for-the-fileact-store-and-forward-scenario.md)