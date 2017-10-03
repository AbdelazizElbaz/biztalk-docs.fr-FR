---
title: "Étape 4 b : démarrez les Ports d’envoi et de réception pour le magasin de FileAct et d’un scénario de transfert (par extraction) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ea2215c5-fb43-4c7e-a42d-5d131a6dee38
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ad4c6b9d17ab1ea55c1f8378f1cb481a07b09e34
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-4b-start-the-send-ports-and-receive-ports-for-the-fileact-store-and-forward-pull-scenario"></a><span data-ttu-id="5f975-102">Étape 4 b : démarrez les Ports d’envoi et de réception pour le magasin de FileAct et d’un scénario de transfert (extraction de données)</span><span class="sxs-lookup"><span data-stu-id="5f975-102">Step 4B: Start the Send Ports and Receive Ports for the FileAct Store and Forward (Pull) Scenario</span></span>
<span data-ttu-id="5f975-103">Avant de commencer cette étape, vous devez effectuer [étape 4 a : démarrer le SWIFTNet Service pour et le scénario de (extraits) avant de FileAct](../../adapters-and-accelerators/fileact-interact/step-4a-start-swiftnet-service-for-fileact-store-and-forward-pull-scenario.md).</span><span class="sxs-lookup"><span data-stu-id="5f975-103">Before you begin this step, you must complete [Step 4A: Start the SWIFTNet Service for the FileAct Store and Forward (Pull) Scenario](../../adapters-and-accelerators/fileact-interact/step-4a-start-swiftnet-service-for-fileact-store-and-forward-pull-scenario.md).</span></span>  
  
### <a name="to-start-the-send-ports-and-receive-ports"></a><span data-ttu-id="5f975-104">Pour démarrer les ports d’envoi et de ports de réception</span><span class="sxs-lookup"><span data-stu-id="5f975-104">To start the send ports and receive ports</span></span>  
  
1.  <span data-ttu-id="5f975-105">Démarrer **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="5f975-105">Start **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="5f975-106">Dans l’arborescence de la console, développez le groupe BizTalk, puis développez l’application BizTalk où vous avez créé les ports d’envoi.</span><span class="sxs-lookup"><span data-stu-id="5f975-106">In the console tree, expand the BizTalk group, and then expand the BizTalk application where you created the send ports.</span></span>  
  
3.  <span data-ttu-id="5f975-107">Pour chacun de ces ports d’envoi, cliquez sur le port d’envoi, puis cliquez sur **Démarrer**:</span><span class="sxs-lookup"><span data-stu-id="5f975-107">For each of the following send ports, right-click the send port, and then click **Start**:</span></span>  
  
    -   <span data-ttu-id="5f975-108">**Tutorial_ FA_SendPullResponseToReceiver**</span><span class="sxs-lookup"><span data-stu-id="5f975-108">**Tutorial_ FA_SendPullResponseToReceiver**</span></span>  
  
    -   <span data-ttu-id="5f975-109">**Tutorial_ FA_SendRequest_SnF**</span><span class="sxs-lookup"><span data-stu-id="5f975-109">**Tutorial_ FA_SendRequest_SnF**</span></span>  
  
    -   <span data-ttu-id="5f975-110">**Tutorial_ FA_DynamicSendPort**</span><span class="sxs-lookup"><span data-stu-id="5f975-110">**Tutorial_ FA_DynamicSendPort**</span></span>  
  
4.  <span data-ttu-id="5f975-111">Dans l’arborescence de la console, développez le groupe BizTalk, puis développez l’application BizTalk où vous avez créé les emplacements de réception.</span><span class="sxs-lookup"><span data-stu-id="5f975-111">In the console tree, expand the BizTalk group, and then expand the BizTalk application where you created the receive locations.</span></span>  
  
5.  <span data-ttu-id="5f975-112">Pour chacun des emplacements de réception suivants, avec le bouton droit à l’emplacement de réception, puis cliquez sur **activer**:</span><span class="sxs-lookup"><span data-stu-id="5f975-112">For each of the following receive locations, right-click the receive location, and then click **Enable**:</span></span>  
  
    -   <span data-ttu-id="5f975-113">**Tutorial_ FA_InputRequest_SnF**</span><span class="sxs-lookup"><span data-stu-id="5f975-113">**Tutorial_ FA_InputRequest_SnF**</span></span>  
  
    -   <span data-ttu-id="5f975-114">**Tutorial_ FA_InputRequest_PullMode**</span><span class="sxs-lookup"><span data-stu-id="5f975-114">**Tutorial_ FA_InputRequest_PullMode**</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f975-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5f975-115">See Also</span></span>  
 <span data-ttu-id="5f975-116">[Étape 4 a : démarrer le Service SWIFTNet pour et le scénario de transfert (Pull) de FileAct](../../adapters-and-accelerators/fileact-interact/step-4a-start-swiftnet-service-for-fileact-store-and-forward-pull-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="5f975-116">[Step 4A: Start the SWIFTNet Service for the FileAct Store and Forward (Pull) Scenario](../../adapters-and-accelerators/fileact-interact/step-4a-start-swiftnet-service-for-fileact-store-and-forward-pull-scenario.md) </span></span>  
 <span data-ttu-id="5f975-117">[Étape 4c : créer une Instance de Test pour le magasin de FileAct et d’un scénario de transfert (extraction de données)](../../adapters-and-accelerators/fileact-interact/step-4c-create-a-test-instance-for-fileact-store-and-forward-pull-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="5f975-117">[Step 4C: Create a Test Instance for the FileAct Store and Forward (Pull) Scenario](../../adapters-and-accelerators/fileact-interact/step-4c-create-a-test-instance-for-fileact-store-and-forward-pull-scenario.md) </span></span>  
 [<span data-ttu-id="5f975-118">Étape 4d : tester une Instance valide pour le magasin de FileAct et d’un scénario de transfert (extraction de données)</span><span class="sxs-lookup"><span data-stu-id="5f975-118">Step 4D: Test a Valid Instance for the FileAct Store and Forward (Pull) Scenario</span></span>](../../adapters-and-accelerators/fileact-interact/step-4d-test-a-valid-instance-for-fileact-store-and-forward-pull-scenario.md)