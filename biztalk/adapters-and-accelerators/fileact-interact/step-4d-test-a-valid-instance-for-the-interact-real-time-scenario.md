---
title: "Étape 4d : tester une Instance valide pour le scénario en temps réel d’interagir | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e163c3ac-a00d-40cf-b1b8-4a38f74ab0e8
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 94bdb2acd8147ec5041df7d6a1c4324ca833d9e4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-4d-test-a-valid-instance-for-the-interact-real-time-scenario"></a><span data-ttu-id="95e14-102">Étape 4d : tester une Instance valide pour l’interaction du scénario en temps réel</span><span class="sxs-lookup"><span data-stu-id="95e14-102">Step 4D: Test a Valid Instance for the InterAct Real-Time Scenario</span></span>
<span data-ttu-id="95e14-103">Avant de commencer cette étape, vous devez effectuer [étape 4c : créer une Instance de Test pour le scénario en temps réel interagir](../../adapters-and-accelerators/fileact-interact/step-4c-create-a-test-instance-for-the-interact-real-time-scenario.md).</span><span class="sxs-lookup"><span data-stu-id="95e14-103">Before you begin this step, you must complete [Step 4C: Create a Test Instance for the InterAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-4c-create-a-test-instance-for-the-interact-real-time-scenario.md).</span></span>  
  
### <a name="to-test-a-valid-instance"></a><span data-ttu-id="95e14-104">Pour tester une instance valide</span><span class="sxs-lookup"><span data-stu-id="95e14-104">To test a valid instance</span></span>  
  
1.  <span data-ttu-id="95e14-105">Faites glisser le fichier ExchangeReqSimple.xml dans C:\SWIFTAdapterTutorial\Interact\InputRequest_RealTime.</span><span class="sxs-lookup"><span data-stu-id="95e14-105">Drop the file ExchangeReqSimple.xml into C:\SWIFTAdapterTutorial\Interact\InputRequest_RealTime.</span></span>  
  
2.  <span data-ttu-id="95e14-106">Vérifiez que le fichier ExchangeReqSimple.xml disparaît après quelques instants, à partir du dossier.</span><span class="sxs-lookup"><span data-stu-id="95e14-106">Verify that after a moment, the ExchangeReqSimple.xml file disappears from the folder.</span></span>  
  
3.  <span data-ttu-id="95e14-107">Accédez à C:\SWIFTAdapterTutorial\Interact\HandleRequest pour afficher le message de demande de handle Sw:HandleRequest.</span><span class="sxs-lookup"><span data-stu-id="95e14-107">Browse to C:\SWIFTAdapterTutorial\Interact\HandleRequest to view the handle request message, Sw:HandleRequest.</span></span>  
  
4.  <span data-ttu-id="95e14-108">Accédez à C:\SWIFTAdapterTutorial\Interact\Response pour afficher le message de réponse de handle Sw:HandleResponse.</span><span class="sxs-lookup"><span data-stu-id="95e14-108">Browse to C:\SWIFTAdapterTutorial\Interact\Response to view the handle response message, Sw:HandleResponse.</span></span>  
  
5.  <span data-ttu-id="95e14-109">Ouvrez le message de Sw:HandleRequest dans un éditeur de texte, tel que le bloc-notes et vérifiez que la section de charge utile est le même que celui du fichier ExchangeReqSimple.xml.</span><span class="sxs-lookup"><span data-stu-id="95e14-109">Open the Sw:HandleRequest message in a text editor, such as Notepad, and verify that the payload section is the same as in the file ExchangeReqSimple.xml.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95e14-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="95e14-110">See Also</span></span>  
 <span data-ttu-id="95e14-111">[Étape 4 : Tester l’interaction du scénario de bout en bout en temps réel](../../adapters-and-accelerators/fileact-interact/step-4-test-the-interact-real-time-end-to-end-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="95e14-111">[Step 4: Test the InterAct Real-Time End-to-End Scenario](../../adapters-and-accelerators/fileact-interact/step-4-test-the-interact-real-time-end-to-end-scenario.md) </span></span>  
 <span data-ttu-id="95e14-112">[Étape 4 a : démarrer le Service SWIFTNet](../../adapters-and-accelerators/fileact-interact/step-4a-start-the-swiftnet-service.md) </span><span class="sxs-lookup"><span data-stu-id="95e14-112">[Step 4A: Start the SWIFTNet Service](../../adapters-and-accelerators/fileact-interact/step-4a-start-the-swiftnet-service.md) </span></span>  
 <span data-ttu-id="95e14-113">[Étape 4 b : démarrer les Ports d’envoi et de réception pour l’interaction scénario en temps réel](../../adapters-and-accelerators/fileact-interact/step-4b-start-the-send-and-receive-ports-for-interact-real-time-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="95e14-113">[Step 4B: Start the Send Ports and Receive Ports for the InterAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-4b-start-the-send-and-receive-ports-for-interact-real-time-scenario.md) </span></span>  
 [<span data-ttu-id="95e14-114">Étape 4c : créer une Instance de Test pour l’interaction du scénario en temps réel</span><span class="sxs-lookup"><span data-stu-id="95e14-114">Step 4C: Create a Test Instance for the InterAct Real-Time Scenario</span></span>](../../adapters-and-accelerators/fileact-interact/step-4c-create-a-test-instance-for-the-interact-real-time-scenario.md)