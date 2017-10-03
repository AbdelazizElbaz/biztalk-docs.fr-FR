---
title: "Étape 4c : créer une Instance de Test pour le magasin d’interagir et le scénario avant | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 64a69dcc-d307-47c0-87e8-b0cb2a4d655b
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 44addc30191dd9541d7f5964a3de0eec244c9993
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-4c-create-a-test-instance-for-the-interact-store-and-forward-scenario"></a><span data-ttu-id="2f62d-102">Étape 4c : créer une Instance de Test pour le magasin d’interagir et le scénario avant</span><span class="sxs-lookup"><span data-stu-id="2f62d-102">Step 4C: Create a Test Instance for the InterAct Store and Forward Scenario</span></span>
<span data-ttu-id="2f62d-103">Avant de commencer cette étape, vous devez effectuer [étape 4 b : démarrez les Ports d’envoi et les Ports de réception pour le magasin d’interagir et le scénario par progression](../../adapters-and-accelerators/fileact-interact/step-4b-start-the-send-and-receive-ports-for-interact-store-and-forward.md).</span><span class="sxs-lookup"><span data-stu-id="2f62d-103">Before you begin this step, you must complete [Step 4B: Start the Send Ports and Receive Ports for the InterAct Store and Forward Scenario](../../adapters-and-accelerators/fileact-interact/step-4b-start-the-send-and-receive-ports-for-interact-store-and-forward.md).</span></span>  
  
### <a name="to-create-a-test-instance"></a><span data-ttu-id="2f62d-104">Pour créer une instance de test</span><span class="sxs-lookup"><span data-stu-id="2f62d-104">To create a test instance</span></span>  
  
1.  <span data-ttu-id="2f62d-105">Ouvrez un nouveau fichier dans un éditeur de texte, tel que le bloc-notes et collez le texte suivant :</span><span class="sxs-lookup"><span data-stu-id="2f62d-105">Open a new file in a text editor, such as Notepad, and paste the following:</span></span>  
  
    ```  
    <SwInt-ExchangeRequest>  
    <SwInt-Request>  
    <SwInt-RequestPayload>  
    Get Well soon  
    </SwInt-RequestPayload>  
    </SwInt-Request>  
    </SwInt-ExchangeRequest>  
    ```  
  
2.  <span data-ttu-id="2f62d-106">Enregistrez le fichier avec le nom ExchangeReqSimple.xml.</span><span class="sxs-lookup"><span data-stu-id="2f62d-106">Save the File with the name ExchangeReqSimple.xml.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f62d-107">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2f62d-107">See Also</span></span>  
 <span data-ttu-id="2f62d-108">[Étape 4 : Tester le magasin d’interagir et le scénario de bout en bout avant](../../adapters-and-accelerators/fileact-interact/step-4-test-the-interact-store-and-forward-end-to-end-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="2f62d-108">[Step 4: Test the InterAct Store and Forward End-to-End Scenario](../../adapters-and-accelerators/fileact-interact/step-4-test-the-interact-store-and-forward-end-to-end-scenario.md) </span></span>  
 <span data-ttu-id="2f62d-109">[Étape 4 a : démarrer le Service de SWIFTNet pour le magasin d’interagir et d’un scénario avant](../../adapters-and-accelerators/fileact-interact/step-4a-start-the-swiftnet-service-for-the-interact-store-and-forward-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="2f62d-109">[Step 4A: Start the SWIFTNet Service for the InterAct Store and Forward Scenario](../../adapters-and-accelerators/fileact-interact/step-4a-start-the-swiftnet-service-for-the-interact-store-and-forward-scenario.md) </span></span>  
 <span data-ttu-id="2f62d-110">[Étape 4 b : démarrez les Ports d’envoi et Ports de réception pour le magasin d’interagir et d’un scénario avant](../../adapters-and-accelerators/fileact-interact/step-4b-start-the-send-and-receive-ports-for-interact-store-and-forward.md) </span><span class="sxs-lookup"><span data-stu-id="2f62d-110">[Step 4B: Start the Send Ports and Receive Ports for the InterAct Store and Forward Scenario](../../adapters-and-accelerators/fileact-interact/step-4b-start-the-send-and-receive-ports-for-interact-store-and-forward.md) </span></span>  
 [<span data-ttu-id="2f62d-111">Étape 4d : tester une Instance valide pour le magasin d’interagir et le scénario avant</span><span class="sxs-lookup"><span data-stu-id="2f62d-111">Step 4D: Test a Valid Instance for the InterAct Store and Forward Scenario</span></span>](../../adapters-and-accelerators/fileact-interact/step-4d-test-a-valid-instance-for-the-interact-store-and-forward-scenario.md)