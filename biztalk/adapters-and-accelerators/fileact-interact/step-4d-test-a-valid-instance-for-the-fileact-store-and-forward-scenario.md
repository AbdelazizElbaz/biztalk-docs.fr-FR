---
title: "Étape 4d : tester une Instance valide pour et le scénario de transfert de FileAct | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7f47b1fd-a4ef-4b1d-812a-8c2fa946f98c
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 21ee5e3fb8c44825bab039e1066184881a62d998
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-4d-test-a-valid-instance-for-the-fileact-store-and-forward-scenario"></a><span data-ttu-id="cdb22-102">Étape 4d : tester une Instance valide pour et le scénario de transfert de FileAct</span><span class="sxs-lookup"><span data-stu-id="cdb22-102">Step 4D: Test a Valid Instance for the FileAct Store and Forward Scenario</span></span>
<span data-ttu-id="cdb22-103">Avant de commencer cette étape, vous devez effectuer [étape 4c : créer une Instance de Test pour et le scénario de transfert de FileAct](../../adapters-and-accelerators/fileact-interact/step-4c-create-a-test-instance-for-the-fileact-store-and-forward-scenario.md).</span><span class="sxs-lookup"><span data-stu-id="cdb22-103">Before you begin this step, you must complete [Step 4C: Create a Test Instance for the FileAct Store and Forward Scenario](../../adapters-and-accelerators/fileact-interact/step-4c-create-a-test-instance-for-the-fileact-store-and-forward-scenario.md).</span></span>  
  
### <a name="to-test-a-valid-instance"></a><span data-ttu-id="cdb22-104">Pour tester une instance valide</span><span class="sxs-lookup"><span data-stu-id="cdb22-104">To test a valid instance</span></span>  
  
1.  <span data-ttu-id="cdb22-105">Faites glisser le fichier PutReqSimple.xml dans C:\SWIFTAdapterTutorial\Fileact\FileRequestDropSnF.</span><span class="sxs-lookup"><span data-stu-id="cdb22-105">Drop the file PutReqSimple.xml into C:\SWIFTAdapterTutorial\Fileact\FileRequestDropSnF.</span></span>  
  
2.  <span data-ttu-id="cdb22-106">Vérifiez que le fichier PutReqSimple.xml disparaît après quelques instants, à partir du dossier.</span><span class="sxs-lookup"><span data-stu-id="cdb22-106">Verify that after a moment, the PutReqSimple.xml file disappears from the folder.</span></span>  
  
3.  <span data-ttu-id="cdb22-107">Vérifiez que le fichier Sample_Put.txt est transféré de C:\SWIFTAdapterTurorial\Fileact\ClientLocation vers C:\SWIFTAdapterTutorial\Fileact\ServerLocation, et que les réponses apparaissent dans C:\SWIFTAdapterTutorial\ResponseServer.</span><span class="sxs-lookup"><span data-stu-id="cdb22-107">Verify that the Sample_Put.txt file is transferred from C:\SWIFTAdapterTurorial\Fileact\ClientLocation to C:\SWIFTAdapterTutorial\Fileact\ServerLocation, and that responses appear in C:\SWIFTAdapterTutorial\ResponseServer.</span></span>  
  
4.  <span data-ttu-id="cdb22-108">Recherchez le dossier de l’événement (c:\SWIFTAdapterTutorial\Fileact\StatusEvents) état du trois messages HandleFileEventRequest.</span><span class="sxs-lookup"><span data-stu-id="cdb22-108">Check status event (c:\SWIFTAdapterTutorial\Fileact\StatusEvents) folder for three HandleFileEventRequest messages.</span></span> <span data-ttu-id="cdb22-109">Ces messages doivent contenir le statut du transfert suivant :</span><span class="sxs-lookup"><span data-stu-id="cdb22-109">These messages should contain the following Transfer status:</span></span>  
  
     <span data-ttu-id="cdb22-110">Message de HandleFileEventRequest\<Sw-TransferStatus > accepté\</Sw-TransferStatus ></span><span class="sxs-lookup"><span data-stu-id="cdb22-110">HandleFileEventRequest message\<Sw-TransferStatus>Accepted\</Sw-TransferStatus></span></span>  
  
     <span data-ttu-id="cdb22-111">Message de HandleFileEventRequest \<Sw-TransferStatus > a été initiée\</Sw-TransferStatus ></span><span class="sxs-lookup"><span data-stu-id="cdb22-111">HandleFileEventRequest message \<Sw-TransferStatus>Initiated\</Sw-TransferStatus></span></span>  
  
     <span data-ttu-id="cdb22-112">Message de HandleFileEventRequest \<Sw-TransferStatus > terminé\</Sw-TransferStatus ></span><span class="sxs-lookup"><span data-stu-id="cdb22-112">HandleFileEventRequest message \<Sw-TransferStatus>Completed\</Sw-TransferStatus></span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cdb22-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cdb22-113">See Also</span></span>  
 <span data-ttu-id="cdb22-114">[Étape 4 : Tester et de scénario de bout en bout avant de FileAct](../../adapters-and-accelerators/fileact-interact/step-4-test-fileact-store-and-forward-end-to-end-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="cdb22-114">[Step 4: Test FileAct Store and Forward End-to-End Scenario](../../adapters-and-accelerators/fileact-interact/step-4-test-fileact-store-and-forward-end-to-end-scenario.md) </span></span>  
 <span data-ttu-id="cdb22-115">[Étape 4 a : démarrer le Service SWIFTNet pour et le scénario de transfert de FileAct](../../adapters-and-accelerators/fileact-interact/step-4a-start-the-swiftnet-service-for-the-fileact-store-and-forward-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="cdb22-115">[Step 4A: Start the SWIFTNet Service for the FileAct Store and Forward Scenario](../../adapters-and-accelerators/fileact-interact/step-4a-start-the-swiftnet-service-for-the-fileact-store-and-forward-scenario.md) </span></span>  
 <span data-ttu-id="cdb22-116">[Étape 4 b : démarrez les Ports d’envoi et de réception pour et le scénario de transfert de FileAct](../../adapters-and-accelerators/fileact-interact/step-4b-start-the-send-ports-and-receive-ports-for-fileact-store-and-forward.md) </span><span class="sxs-lookup"><span data-stu-id="cdb22-116">[Step 4B: Start the Send Ports and Receive Ports for the FileAct Store and Forward Scenario](../../adapters-and-accelerators/fileact-interact/step-4b-start-the-send-ports-and-receive-ports-for-fileact-store-and-forward.md) </span></span>  
 [<span data-ttu-id="cdb22-117">Étape 4c : créer une Instance de Test pour et le scénario de transfert de FileAct</span><span class="sxs-lookup"><span data-stu-id="cdb22-117">Step 4C: Create a Test Instance for the FileAct Store and Forward Scenario</span></span>](../../adapters-and-accelerators/fileact-interact/step-4c-create-a-test-instance-for-the-fileact-store-and-forward-scenario.md)