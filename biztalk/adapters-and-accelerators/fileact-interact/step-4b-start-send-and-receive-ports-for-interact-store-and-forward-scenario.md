---
title: "Étape 4 b : démarrez les Ports d’envoi et Ports de réception pour le magasin d’interagir et le scénario de transfert (Pull) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 00ab119d-ed44-4f4a-84ea-20f2c41e5a92
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b747c76b30b9f7d04bef379be9eaccaaeca063ca
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-4b-start-the-send-ports-and-receive-ports-for-the-interact-store-and-forward-pull-scenario"></a><span data-ttu-id="a9d46-102">Étape 4 b : démarrez les Ports d’envoi et Ports de réception pour le magasin d’interagir et le scénario de transfert (Pull)</span><span class="sxs-lookup"><span data-stu-id="a9d46-102">Step 4B: Start the Send Ports and Receive Ports for the InterAct Store and Forward (Pull) Scenario</span></span>
<span data-ttu-id="a9d46-103">Avant de commencer cette étape, vous devez effectuer[étape 4 : tester le magasin d’interagir et le scénario de transfert de bout en bout](../../adapters-and-accelerators/fileact-interact/step-4-test-the-interact-store-and-forward-end-to-end-scenario.md).</span><span class="sxs-lookup"><span data-stu-id="a9d46-103">Before you begin this step, you must complete[Step 4: Test the InterAct Store and Forward End-to-End Scenario](../../adapters-and-accelerators/fileact-interact/step-4-test-the-interact-store-and-forward-end-to-end-scenario.md).</span></span>  
  
### <a name="to-start-the-send-ports-and-receive-ports"></a><span data-ttu-id="a9d46-104">Pour démarrer les ports d’envoi et de ports de réception</span><span class="sxs-lookup"><span data-stu-id="a9d46-104">To start the send ports and receive ports</span></span>  
  
1.  <span data-ttu-id="a9d46-105">Démarrer **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="a9d46-105">Start **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="a9d46-106">Dans l’arborescence de la console, développez le groupe BizTalk, puis développez l’application BizTalk où vous avez créé les ports d’envoi.</span><span class="sxs-lookup"><span data-stu-id="a9d46-106">In the console tree, expand the BizTalk group, and then expand the BizTalk application where you created the send ports.</span></span>  
  
3.  <span data-ttu-id="a9d46-107">Pour chacun de ces ports d’envoi, cliquez sur le port d’envoi, puis cliquez sur **Démarrer**:</span><span class="sxs-lookup"><span data-stu-id="a9d46-107">For each of the following send ports, right-click the send port, and then click **Start**:</span></span>  
  
    -   <span data-ttu-id="a9d46-108">**Tutorial_ IA_SendPullResponseToReceiver**</span><span class="sxs-lookup"><span data-stu-id="a9d46-108">**Tutorial_ IA_SendPullResponseToReceiver**</span></span>  
  
    -   <span data-ttu-id="a9d46-109">**Tutorial_IA_SendRequest_SnF**</span><span class="sxs-lookup"><span data-stu-id="a9d46-109">**Tutorial_IA_SendRequest_SnF**</span></span>  
  
    -   <span data-ttu-id="a9d46-110">**Tutorial_IA_DynamicSendPort**</span><span class="sxs-lookup"><span data-stu-id="a9d46-110">**Tutorial_IA_DynamicSendPort**</span></span>  
  
4.  <span data-ttu-id="a9d46-111">Dans l’arborescence de la console, développez le groupe BizTalk, puis développez l’application BizTalk où vous avez créé les emplacements de réception.</span><span class="sxs-lookup"><span data-stu-id="a9d46-111">In the console tree, expand the BizTalk group, and then expand the BizTalk application where you created the receive locations.</span></span>  
  
5.  <span data-ttu-id="a9d46-112">Pour chacun des emplacements de réception suivants, avec le bouton droit à l’emplacement de réception, puis cliquez sur **activer**:</span><span class="sxs-lookup"><span data-stu-id="a9d46-112">For each of the following receive locations, right-click the receive location, and then click **Enable**:</span></span>  
  
    -   <span data-ttu-id="a9d46-113">**Tutorial_IA_InputRequest_SnF**</span><span class="sxs-lookup"><span data-stu-id="a9d46-113">**Tutorial_IA_InputRequest_SnF**</span></span>  
  
    -   <span data-ttu-id="a9d46-114">**Tutorial_ IA_InputRequest_PullMode**</span><span class="sxs-lookup"><span data-stu-id="a9d46-114">**Tutorial_ IA_InputRequest_PullMode**</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9d46-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a9d46-115">See Also</span></span>  
 <span data-ttu-id="a9d46-116">[Étape 4 a : démarrer le Service de SWIFTNet pour le magasin d’interagir et le scénario de transfert (Pull)](../../adapters-and-accelerators/fileact-interact/step-4a-start-swiftnet-service-for-the-interact-store-and-forward-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="a9d46-116">[Step 4A: Start the SWIFTNet Service for the InterAct Store and Forward (Pull) Scenario](../../adapters-and-accelerators/fileact-interact/step-4a-start-swiftnet-service-for-the-interact-store-and-forward-scenario.md) </span></span>  
 <span data-ttu-id="a9d46-117">[Étape 4c : créer une Instance de Test pour le magasin d’interagir et le scénario de transfert (Pull)](../../adapters-and-accelerators/fileact-interact/step-4c-create-a-test-instance-for-interact-store-and-forward-pull-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="a9d46-117">[Step 4C: Create a Test Instance for the InterAct Store and Forward (Pull) Scenario](../../adapters-and-accelerators/fileact-interact/step-4c-create-a-test-instance-for-interact-store-and-forward-pull-scenario.md) </span></span>  
 [<span data-ttu-id="a9d46-118">Étape 4d : tester une Instance valide pour le magasin d’interagir et le scénario de transfert (Pull)</span><span class="sxs-lookup"><span data-stu-id="a9d46-118">Step 4D: Test a Valid Instance for the InterAct Store and Forward (Pull) Scenario</span></span>](../../adapters-and-accelerators/fileact-interact/step-4d-test-a-valid-instance-for-interact-store-and-forward-pull-scenario.md)