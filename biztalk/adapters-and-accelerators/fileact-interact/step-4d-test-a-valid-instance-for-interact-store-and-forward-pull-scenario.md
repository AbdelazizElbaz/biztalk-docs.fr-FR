---
title: "Étape 4d : tester une Instance valide pour le magasin d’interagir et le scénario de transfert (Pull) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7c2933d0-bbe3-4486-832e-5009b2d760ac
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9c9c8ea24eeb5541cf84448363ca91fcb8171f19
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-4d-test-a-valid-instance-for-the-interact-store-and-forward-pull-scenario"></a><span data-ttu-id="0cdac-102">Étape 4d : tester une Instance valide pour le magasin d’interagir et le scénario de transfert (Pull)</span><span class="sxs-lookup"><span data-stu-id="0cdac-102">Step 4D: Test a Valid Instance for the InterAct Store and Forward (Pull) Scenario</span></span>
<span data-ttu-id="0cdac-103">Avant de commencer cette étape, vous devez effectuer [étape 4c : créer une Instance de Test pour le magasin d’interagir et le scénario de (Pull) vers l’avant](../../adapters-and-accelerators/fileact-interact/step-4c-create-a-test-instance-for-interact-store-and-forward-pull-scenario.md).</span><span class="sxs-lookup"><span data-stu-id="0cdac-103">Before you begin this step, you must complete [Step 4C: Create a Test Instance for the InterAct Store and Forward (Pull) Scenario](../../adapters-and-accelerators/fileact-interact/step-4c-create-a-test-instance-for-interact-store-and-forward-pull-scenario.md).</span></span>  
  
### <a name="to-test-a-valid-instance"></a><span data-ttu-id="0cdac-104">Pour tester une instance valide</span><span class="sxs-lookup"><span data-stu-id="0cdac-104">To test a valid instance</span></span>  
  
1.  <span data-ttu-id="0cdac-105">Faites glisser le fichier ExchangeReqSimple.xml dans c:\SWIFTAdapterTutorial\Interact\InputRequest_SnF.</span><span class="sxs-lookup"><span data-stu-id="0cdac-105">Drop the file ExchangeReqSimple.xml into c:\SWIFTAdapterTutorial\Interact\InputRequest_SnF.</span></span>  
  
2.  <span data-ttu-id="0cdac-106">Vérifiez que le fichier ExchangeReqSimple.xml disparaît après quelques instants, à partir du dossier.</span><span class="sxs-lookup"><span data-stu-id="0cdac-106">Verify that after a moment, the ExchangeReqSimple.xml file disappears from the folder.</span></span>  
  
3.  <span data-ttu-id="0cdac-107">Faites glisser le fichier acquirequeue.xml dans c:\SWIFTAdapterTutorial\Interact\PullRequest.</span><span class="sxs-lookup"><span data-stu-id="0cdac-107">Drop the file acquirequeue.xml into c:\SWIFTAdapterTutorial\Interact\PullRequest.</span></span>  
  
4.  <span data-ttu-id="0cdac-108">Accédez à C:\SWIFTAdapterTutorial\Interact\PullResponse Vérifiez que Sw:HandleRequest se trouve dans le dossier.</span><span class="sxs-lookup"><span data-stu-id="0cdac-108">Browse to C:\SWIFTAdapterTutorial\Interact\PullResponse Verify that Sw:HandleRequest is in the folder.</span></span>  
  
5.  <span data-ttu-id="0cdac-109">Ouvrez le message de Sw:HandleRequest dans un éditeur de texte, tel que le bloc-notes et vérifiez que la section de charge utile est le même que celui du fichier ExchangeReqSimple.xml.</span><span class="sxs-lookup"><span data-stu-id="0cdac-109">Open the Sw:HandleRequest message in a text editor, such as Notepad, and verify that the payload section is the same as in the file ExchangeReqSimple.xml.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0cdac-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0cdac-110">See Also</span></span>  
 <span data-ttu-id="0cdac-111">[Étape 4 a : démarrer le Service de SWIFTNet pour le magasin d’interagir et le scénario de transfert (Pull)](../../adapters-and-accelerators/fileact-interact/step-4a-start-swiftnet-service-for-the-interact-store-and-forward-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="0cdac-111">[Step 4A: Start the SWIFTNet Service for the InterAct Store and Forward (Pull) Scenario](../../adapters-and-accelerators/fileact-interact/step-4a-start-swiftnet-service-for-the-interact-store-and-forward-scenario.md) </span></span>  
 <span data-ttu-id="0cdac-112">[Étape 4 b : démarrez les Ports d’envoi et Ports de réception pour le magasin d’interagir et le scénario de transfert (Pull)](../../adapters-and-accelerators/fileact-interact/step-4b-start-send-and-receive-ports-for-interact-store-and-forward-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="0cdac-112">[Step 4B: Start the Send Ports and Receive Ports for the InterAct Store and Forward (Pull) Scenario](../../adapters-and-accelerators/fileact-interact/step-4b-start-send-and-receive-ports-for-interact-store-and-forward-scenario.md) </span></span>  
 [<span data-ttu-id="0cdac-113">Étape 4c : créer une Instance de Test pour le magasin d’interagir et le scénario de transfert (Pull)</span><span class="sxs-lookup"><span data-stu-id="0cdac-113">Step 4C: Create a Test Instance for the InterAct Store and Forward (Pull) Scenario</span></span>](../../adapters-and-accelerators/fileact-interact/step-4c-create-a-test-instance-for-interact-store-and-forward-pull-scenario.md)