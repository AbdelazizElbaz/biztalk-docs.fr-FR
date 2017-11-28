---
title: "Étape 4d : tester une Instance valide pour le magasin d’interagir et le scénario avant | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6aa49df8-ccf6-455a-99ff-38879d2b7bf9
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a5d27b23195adffc5915d8cb2170dca9e975ec94
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-4d-test-a-valid-instance-for-the-interact-store-and-forward-scenario"></a><span data-ttu-id="e6ed4-102">Étape 4d : tester une Instance valide pour le magasin d’interagir et le scénario avant</span><span class="sxs-lookup"><span data-stu-id="e6ed4-102">Step 4D: Test a Valid Instance for the InterAct Store and Forward Scenario</span></span>
<span data-ttu-id="e6ed4-103">Avant de commencer cette étape, vous devez effectuer [étape 4c : créer une Instance de Test pour le magasin d’interagir et le scénario par progression](../../adapters-and-accelerators/fileact-interact/step-4c-create-a-test-instance-for-the-interact-store-and-forward-scenario.md).</span><span class="sxs-lookup"><span data-stu-id="e6ed4-103">Before you begin this step, you must complete [Step 4C: Create a Test Instance for the InterAct Store and Forward Scenario](../../adapters-and-accelerators/fileact-interact/step-4c-create-a-test-instance-for-the-interact-store-and-forward-scenario.md).</span></span>  
  
### <a name="to-test-a-valid-instance"></a><span data-ttu-id="e6ed4-104">Pour tester une instance valide</span><span class="sxs-lookup"><span data-stu-id="e6ed4-104">To test a valid instance</span></span>  
  
1.  <span data-ttu-id="e6ed4-105">Supprimer le fichier ExchangeReqSimple.xml dans c:\SWIFTAdapterTutorial\Interact\InputRequest_SnF</span><span class="sxs-lookup"><span data-stu-id="e6ed4-105">Drop the file ExchangeReqSimple.xml into c:\SWIFTAdapterTutorial\Interact\InputRequest_SnF</span></span>  
  
2.  <span data-ttu-id="e6ed4-106">Vérifiez que le fichier ExchangeReqSimple.xml disparaît après quelques instants, à partir du dossier.</span><span class="sxs-lookup"><span data-stu-id="e6ed4-106">Verify that after a moment, the ExchangeReqSimple.xml file disappears from the folder.</span></span>  
  
3.  <span data-ttu-id="e6ed4-107">Accédez à C:\SWIFTAdapterTutorial\Interact\HandleRequest.</span><span class="sxs-lookup"><span data-stu-id="e6ed4-107">Browse to C:\SWIFTAdapterTutorial\Interact\HandleRequest.</span></span> <span data-ttu-id="e6ed4-108">Vérifiez que Sw:HandleRequest se trouve dans le dossier.</span><span class="sxs-lookup"><span data-stu-id="e6ed4-108">Verify that Sw:HandleRequest is in the folder.</span></span>  
  
4.  <span data-ttu-id="e6ed4-109">Ouvrez le message de Sw:HandleRequest dans un éditeur de texte, tel que le bloc-notes et vérifiez que la section de charge utile est le même que celui du fichier ExchangeReqSimple.xml.</span><span class="sxs-lookup"><span data-stu-id="e6ed4-109">Open the Sw:HandleRequest message in a text editor, such as Notepad, and verify that the payload section is the same as in the file ExchangeReqSimple.xml.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6ed4-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e6ed4-110">See Also</span></span>  
 <span data-ttu-id="e6ed4-111">[Étape 4 : Tester le magasin d’interagir et le scénario de bout en bout avant](../../adapters-and-accelerators/fileact-interact/step-4-test-the-interact-store-and-forward-end-to-end-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="e6ed4-111">[Step 4: Test the InterAct Store and Forward End-to-End Scenario](../../adapters-and-accelerators/fileact-interact/step-4-test-the-interact-store-and-forward-end-to-end-scenario.md) </span></span>  
 <span data-ttu-id="e6ed4-112">[Étape 4 a : démarrer le Service de SWIFTNet pour le magasin d’interagir et d’un scénario avant](../../adapters-and-accelerators/fileact-interact/step-4a-start-the-swiftnet-service-for-the-interact-store-and-forward-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="e6ed4-112">[Step 4A: Start the SWIFTNet Service for the InterAct Store and Forward Scenario](../../adapters-and-accelerators/fileact-interact/step-4a-start-the-swiftnet-service-for-the-interact-store-and-forward-scenario.md) </span></span>  
 <span data-ttu-id="e6ed4-113">[Étape 4 b : démarrez les Ports d’envoi et Ports de réception pour le magasin d’interagir et d’un scénario avant](../../adapters-and-accelerators/fileact-interact/step-4b-start-the-send-and-receive-ports-for-interact-store-and-forward.md) </span><span class="sxs-lookup"><span data-stu-id="e6ed4-113">[Step 4B: Start the Send Ports and Receive Ports for the InterAct Store and Forward Scenario](../../adapters-and-accelerators/fileact-interact/step-4b-start-the-send-and-receive-ports-for-interact-store-and-forward.md) </span></span>  
 [<span data-ttu-id="e6ed4-114">Étape 4c : créer une Instance de Test pour le magasin d’interagir et le scénario avant</span><span class="sxs-lookup"><span data-stu-id="e6ed4-114">Step 4C: Create a Test Instance for the InterAct Store and Forward Scenario</span></span>](../../adapters-and-accelerators/fileact-interact/step-4c-create-a-test-instance-for-the-interact-store-and-forward-scenario.md)