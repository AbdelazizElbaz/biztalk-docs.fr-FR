---
title: "Étape 4c : créer une Instance de Test pour le scénario en temps réel d’interagir | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3557acdc-eb3f-4c70-b64a-3f523a1ba650
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 21c0035074eba0eec6994aa7ab024afbcec10984
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-4c-create-a-test-instance-for-the-interact-real-time-scenario"></a><span data-ttu-id="3d680-102">Étape 4c : créer une Instance de Test pour l’interaction du scénario en temps réel</span><span class="sxs-lookup"><span data-stu-id="3d680-102">Step 4C: Create a Test Instance for the InterAct Real-Time Scenario</span></span>
<span data-ttu-id="3d680-103">Avant de commencer cette étape, vous devez effectuer [étape 4 b : démarrez les Ports d’envoi et les Ports de réception pour le scénario en temps réel interagir](../../adapters-and-accelerators/fileact-interact/step-4b-start-the-send-and-receive-ports-for-interact-real-time-scenario.md).</span><span class="sxs-lookup"><span data-stu-id="3d680-103">Before you begin this step, you must complete [Step 4B: Start the Send Ports and Receive Ports for the InterAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-4b-start-the-send-and-receive-ports-for-interact-real-time-scenario.md).</span></span>  
  
### <a name="to-create-a-test-instance"></a><span data-ttu-id="3d680-104">Pour créer une instance de test</span><span class="sxs-lookup"><span data-stu-id="3d680-104">To create a test instance</span></span>  
  
1.  <span data-ttu-id="3d680-105">Ouvrez un nouveau fichier dans un éditeur de texte, tel que le bloc-notes et collez le texte suivant :</span><span class="sxs-lookup"><span data-stu-id="3d680-105">Open a new file in a text editor, such as Notepad, and paste the following:</span></span>  
  
    ```  
    <SwInt-ExchangeRequest>  
    <SwInt-Request>  
    <SwInt-RequestPayload>  
    Get Well soon  
    </SwInt-RequestPayload>  
    </SwInt-Request>  
    </SwInt-ExchangeRequest>  
    ```  
  
2.  <span data-ttu-id="3d680-106">Enregistrez le fichier sous le nom **ExchangeReqSimple.xml**.</span><span class="sxs-lookup"><span data-stu-id="3d680-106">Save the file with the name **ExchangeReqSimple.xml**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d680-107">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3d680-107">See Also</span></span>  
 <span data-ttu-id="3d680-108">[Étape 4 : Tester l’interaction du scénario de bout en bout en temps réel](../../adapters-and-accelerators/fileact-interact/step-4-test-the-interact-real-time-end-to-end-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="3d680-108">[Step 4: Test the InterAct Real-Time End-to-End Scenario](../../adapters-and-accelerators/fileact-interact/step-4-test-the-interact-real-time-end-to-end-scenario.md) </span></span>  
 <span data-ttu-id="3d680-109">[Étape 4 a : démarrer le Service SWIFTNet](../../adapters-and-accelerators/fileact-interact/step-4a-start-the-swiftnet-service.md) </span><span class="sxs-lookup"><span data-stu-id="3d680-109">[Step 4A: Start the SWIFTNet Service](../../adapters-and-accelerators/fileact-interact/step-4a-start-the-swiftnet-service.md) </span></span>  
 <span data-ttu-id="3d680-110">[Étape 4 b : démarrer les Ports d’envoi et de réception pour l’interaction scénario en temps réel](../../adapters-and-accelerators/fileact-interact/step-4b-start-the-send-and-receive-ports-for-interact-real-time-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="3d680-110">[Step 4B: Start the Send Ports and Receive Ports for the InterAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-4b-start-the-send-and-receive-ports-for-interact-real-time-scenario.md) </span></span>  
 [<span data-ttu-id="3d680-111">Étape 4d : tester une Instance valide pour l’interaction du scénario en temps réel</span><span class="sxs-lookup"><span data-stu-id="3d680-111">Step 4D: Test a Valid Instance for the InterAct Real-Time Scenario</span></span>](../../adapters-and-accelerators/fileact-interact/step-4d-test-a-valid-instance-for-the-interact-real-time-scenario.md)