---
title: "Étape 4d : tester une Instance valide pour le magasin de FileAct et d’un scénario de transfert (par extraction) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 33c7aabe-206f-4b89-b739-ac1e63675451
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cf6f53257ff2a9194cf85597d0806780f15c8e52
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-4d-test-a-valid-instance-for-the-fileact-store-and-forward-pull-scenario"></a><span data-ttu-id="95661-102">Étape 4d : tester une Instance valide pour le magasin de FileAct et d’un scénario de transfert (extraction de données)</span><span class="sxs-lookup"><span data-stu-id="95661-102">Step 4D: Test a Valid Instance for the FileAct Store and Forward (Pull) Scenario</span></span>
<span data-ttu-id="95661-103">Avant de commencer cette étape, vous devez effectuer [étape 4c : créer une Instance de Test pour et le scénario de (extraits) avant de FileAct](../../adapters-and-accelerators/fileact-interact/step-4c-create-a-test-instance-for-fileact-store-and-forward-pull-scenario.md).</span><span class="sxs-lookup"><span data-stu-id="95661-103">Before you begin this step, you must complete [Step 4C: Create a Test Instance for the FileAct Store and Forward (Pull) Scenario](../../adapters-and-accelerators/fileact-interact/step-4c-create-a-test-instance-for-fileact-store-and-forward-pull-scenario.md).</span></span>  
  
### <a name="to-test-a-valid-instance"></a><span data-ttu-id="95661-104">Pour tester une instance valide</span><span class="sxs-lookup"><span data-stu-id="95661-104">To test a valid instance</span></span>  
  
1.  <span data-ttu-id="95661-105">Faites glisser le fichier PutReqSimple.xml dans **C:\SWIFTAdapterTutorial\Fileact\FileRequestDropSnF**.</span><span class="sxs-lookup"><span data-stu-id="95661-105">Drop the file PutReqSimple.xml into **C:\SWIFTAdapterTutorial\Fileact\FileRequestDropSnF**.</span></span>  
  
2.  <span data-ttu-id="95661-106">Vérifiez que le fichier PutReqSimple.xml disparaît après quelques instants, à partir du dossier.</span><span class="sxs-lookup"><span data-stu-id="95661-106">Verify that after a moment, the PutReqSimple.xml file disappears from the folder.</span></span>  
  
3.  <span data-ttu-id="95661-107">Supprimer le fichier fileactcquirequeue.xml dans **C:\SWIFTAdapterTutorial\FileAct\PullRequest**.</span><span class="sxs-lookup"><span data-stu-id="95661-107">Drop the file fileactcquirequeue.xml into **C:\SWIFTAdapterTutorial\FileAct\PullRequest**.</span></span>  
  
4.  <span data-ttu-id="95661-108">Vérifiez que le fichier Sample_Put.txt est transféré à partir de **C:\SWIFTAdapterTutorial\Fileact\ClientLocation** à **C:\SWIFTAdapterTutorial\Fileact\ServerLocation**, et que les réponses apparaissent dans **C:\SWIFTAdapterTutorial\PullResponse**.</span><span class="sxs-lookup"><span data-stu-id="95661-108">Verify that the Sample_Put.txt file is transferred from **C:\SWIFTAdapterTutorial\Fileact\ClientLocation** to **C:\SWIFTAdapterTutorial\Fileact\ServerLocation**, and that responses appear in **C:\SWIFTAdapterTutorial\PullResponse**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95661-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="95661-109">See Also</span></span>  
 <span data-ttu-id="95661-110">[Étape 4 a : démarrer le Service SWIFTNet pour et le scénario de transfert (Pull) de FileAct](../../adapters-and-accelerators/fileact-interact/step-4a-start-swiftnet-service-for-fileact-store-and-forward-pull-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="95661-110">[Step 4A: Start the SWIFTNet Service for the FileAct Store and Forward (Pull) Scenario](../../adapters-and-accelerators/fileact-interact/step-4a-start-swiftnet-service-for-fileact-store-and-forward-pull-scenario.md) </span></span>  
 <span data-ttu-id="95661-111">[Étape 4 b : démarrez les Ports d’envoi et de réception pour le magasin de FileAct et d’un scénario de transfert (extraction de données)](../../adapters-and-accelerators/fileact-interact/step-4b-start-send-and-receive-ports-for-fileact-store-and-forward-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="95661-111">[Step 4B: Start the Send Ports and Receive Ports for the FileAct Store and Forward (Pull) Scenario](../../adapters-and-accelerators/fileact-interact/step-4b-start-send-and-receive-ports-for-fileact-store-and-forward-scenario.md) </span></span>  
 [<span data-ttu-id="95661-112">Étape 4c : créer une Instance de Test pour le magasin de FileAct et d’un scénario de transfert (extraction de données)</span><span class="sxs-lookup"><span data-stu-id="95661-112">Step 4C: Create a Test Instance for the FileAct Store and Forward (Pull) Scenario</span></span>](../../adapters-and-accelerators/fileact-interact/step-4c-create-a-test-instance-for-fileact-store-and-forward-pull-scenario.md)