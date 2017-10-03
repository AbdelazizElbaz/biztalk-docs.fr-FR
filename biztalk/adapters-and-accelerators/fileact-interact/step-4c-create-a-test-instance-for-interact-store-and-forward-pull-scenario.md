---
title: "Étape 4c : créer une Instance de Test pour le magasin d’interagir et le scénario de transfert (Pull) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3c937edd-9524-4f8f-9bd1-68e24f2eebdc
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bf5d0908593110b04f6e5cd0f5912b66264dc7a2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-4c-create-a-test-instance-for-the-interact-store-and-forward-pull-scenario"></a><span data-ttu-id="1cc5a-102">Étape 4c : créer une Instance de Test pour le magasin d’interagir et le scénario de transfert (Pull)</span><span class="sxs-lookup"><span data-stu-id="1cc5a-102">Step 4C: Create a Test Instance for the InterAct Store and Forward (Pull) Scenario</span></span>
<span data-ttu-id="1cc5a-103">Avant de commencer cette étape, vous devez effectuer [étape 3 b : lier l’orchestration avec un port d’envoi dynamique pour interagir magasin et scénario (Pull) avant](../../adapters-and-accelerators/fileact-interact/step-3b-bind-orchestration-with-dynamic-send-port-for-interact-scenario.md).</span><span class="sxs-lookup"><span data-stu-id="1cc5a-103">Before you begin this step, you must complete [Step 3B: Bind the orchestration with dynamic send port for InterAct Store and Forward (Pull) Scenario](../../adapters-and-accelerators/fileact-interact/step-3b-bind-orchestration-with-dynamic-send-port-for-interact-scenario.md).</span></span>  
  
### <a name="to-create-a-test-instance"></a><span data-ttu-id="1cc5a-104">Pour créer une instance de test</span><span class="sxs-lookup"><span data-stu-id="1cc5a-104">To create a test instance</span></span>  
  
1.  <span data-ttu-id="1cc5a-105">Ouvrez un nouveau fichier dans un éditeur de texte, tel que le bloc-notes et collez le texte suivant :</span><span class="sxs-lookup"><span data-stu-id="1cc5a-105">Open a new file in a text editor, such as Notepad, and paste the following:</span></span>  
  
    ```  
    SwInt-ExchangeRequest>  
    <SwInt-Request>  
    <SwInt-RequestPayload>  
    Get Well soon  
    </SwInt-RequestPayload>  
    </SwInt-Request>  
    </SwInt-ExchangeRequest>  
  
    ```  
  
2.  <span data-ttu-id="1cc5a-106">Enregistrez le fichier avec le nom ExchangeReqSimple.xml.</span><span class="sxs-lookup"><span data-stu-id="1cc5a-106">Save the File with the name ExchangeReqSimple.xml.</span></span>  
  
3.  <span data-ttu-id="1cc5a-107">Ouvrez un nouveau fichier dans un éditeur de texte, tel que le bloc-notes et collez le texte suivant :</span><span class="sxs-lookup"><span data-stu-id="1cc5a-107">Open a new file in a text editor, such as Notepad, and paste the following:</span></span>  
  
    ```  
    <?xml version="1.0" encoding="utf-8" ?>  
    <Sw-ExchangeSnFRequest>  
    <Sw-SnFRequest>  
    <Sw-SnFOpRequest>  
    <Sw-AcquireSnFRequest>  
    <SwInt-Queue>ptsguspp_genericfa!x</SwInt-Queue>  
    <Sw-SessionMode>Pull</Sw-SessionMode>  
    <Sw-ForceAcquire>TRUE</Sw-ForceAcquire>  
    <Sw-OrderBy>FileAct</Sw-OrderBy>  
    <Sw-RecoveryMode>TRUE</Sw-RecoveryMode>  
    </Sw-AcquireSnFRequest>  
    </Sw-SnFOpRequest>  
    </Sw-SnFRequest>  
    </Sw-ExchangeSnFRequest>  
  
    ```  
  
4.  <span data-ttu-id="1cc5a-108">Enregistrez le fichier avec le nom acquirequeue.xml.</span><span class="sxs-lookup"><span data-stu-id="1cc5a-108">Save the File with the name acquirequeue.xml.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1cc5a-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1cc5a-109">See Also</span></span>  
 <span data-ttu-id="1cc5a-110">[Étape 4 a : démarrer le Service de SWIFTNet pour le magasin d’interagir et le scénario de transfert (Pull)](../../adapters-and-accelerators/fileact-interact/step-4a-start-swiftnet-service-for-the-interact-store-and-forward-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="1cc5a-110">[Step 4A: Start the SWIFTNet Service for the InterAct Store and Forward (Pull) Scenario](../../adapters-and-accelerators/fileact-interact/step-4a-start-swiftnet-service-for-the-interact-store-and-forward-scenario.md) </span></span>  
 <span data-ttu-id="1cc5a-111">[Étape 4 b : démarrez les Ports d’envoi et Ports de réception pour le magasin d’interagir et le scénario de transfert (Pull)](../../adapters-and-accelerators/fileact-interact/step-4b-start-send-and-receive-ports-for-interact-store-and-forward-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="1cc5a-111">[Step 4B: Start the Send Ports and Receive Ports for the InterAct Store and Forward (Pull) Scenario](../../adapters-and-accelerators/fileact-interact/step-4b-start-send-and-receive-ports-for-interact-store-and-forward-scenario.md) </span></span>  
 [<span data-ttu-id="1cc5a-112">Étape 4d : tester une Instance valide pour le magasin d’interagir et le scénario de transfert (Pull)</span><span class="sxs-lookup"><span data-stu-id="1cc5a-112">Step 4D: Test a Valid Instance for the InterAct Store and Forward (Pull) Scenario</span></span>](../../adapters-and-accelerators/fileact-interact/step-4d-test-a-valid-instance-for-interact-store-and-forward-pull-scenario.md)