---
title: "Étape 4c : créer une Instance de Test pour le scénario en temps réel FileAct | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 80e0cb59-8b4f-4273-a7a4-db3446008061
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 04952616f1b49eb30b4eb00462e4e5295ade0cfc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-4c-create-a-test-instance-for-the-fileact-real-time-scenario"></a><span data-ttu-id="00b05-102">Étape 4c : créer une Instance de Test pour le scénario en temps réel FileAct</span><span class="sxs-lookup"><span data-stu-id="00b05-102">Step 4C: Create a Test Instance for the FileAct Real-Time Scenario</span></span>
<span data-ttu-id="00b05-103">Avant de commencer cette étape, vous devez effectuer [étape 4 b : démarrez les Ports d’envoi et les Ports de réception pour le scénario en temps réel de FileAct](../../adapters-and-accelerators/fileact-interact/step-4b-start-the-send-and-receive-ports-for-the-fileact-real-time-scenario.md).</span><span class="sxs-lookup"><span data-stu-id="00b05-103">Before you begin this step, you must complete [Step 4B: Start the Send Ports and Receive Ports for the FileAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-4b-start-the-send-and-receive-ports-for-the-fileact-real-time-scenario.md).</span></span>  
  
### <a name="to-create-a-test-instance"></a><span data-ttu-id="00b05-104">Pour créer une instance de test</span><span class="sxs-lookup"><span data-stu-id="00b05-104">To create a test instance</span></span>  
  
1.  <span data-ttu-id="00b05-105">Ouvrez un nouveau fichier dans un éditeur de texte, tel que le bloc-notes et collez le texte suivant :</span><span class="sxs-lookup"><span data-stu-id="00b05-105">Open a new file in a text editor, such as Notepad, and paste the following:</span></span>  
  
    ```  
    <?xml version="1.0" encoding="utf-8"?>  
    <Sw-ExchangeFileRequest>  
    <Sw-FileRequest>  
    <Sw-FileOpRequest>  
    <Sw-PutFileRequest>  
    <Sw-PhysicalName>%PhysicalFolderName%\sample_put.txt</Sw-PhysicalName>  
    </Sw-PutFileRequest>  
    </Sw-FileOpRequest>  
    </Sw-FileRequest>  
    </Sw-ExchangeFileRequest>  
    ```  
  
2.  <span data-ttu-id="00b05-106">Enregistrez le fichier avec le nom « PutReqSimple.xml ».</span><span class="sxs-lookup"><span data-stu-id="00b05-106">Save the file with the name “PutReqSimple.xml”.</span></span>  
  
3.  <span data-ttu-id="00b05-107">Assurez-vous que le fichier (Sample_put.txt) est placé dans le dossier d’emplacement du Client.</span><span class="sxs-lookup"><span data-stu-id="00b05-107">Make sure that the file (Sample_put.txt) is placed in the Client Location folder.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00b05-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="00b05-108">See Also</span></span>  
 <span data-ttu-id="00b05-109">[Étape 4 : Tester le scénario de bout en bout FileAct en temps réel](../../adapters-and-accelerators/fileact-interact/step-4-test-fileact-real-time-end-to-end-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="00b05-109">[Step 4: Test FileAct Real-Time End-to-End Scenario](../../adapters-and-accelerators/fileact-interact/step-4-test-fileact-real-time-end-to-end-scenario.md) </span></span>  
 <span data-ttu-id="00b05-110">[Étape 4 a : démarrer le Service SWIFTNet pour le scénario en temps réel FileAct](../../adapters-and-accelerators/fileact-interact/step-4a-start-the-swiftnet-service-for-the-fileact-real-time-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="00b05-110">[Step 4A: Start the SWIFTNet Service for the FileAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-4a-start-the-swiftnet-service-for-the-fileact-real-time-scenario.md) </span></span>  
 <span data-ttu-id="00b05-111">[Étape 4 b : démarrez les Ports d’envoi et Ports de réception pour le scénario en temps réel FileAct](../../adapters-and-accelerators/fileact-interact/step-4b-start-the-send-and-receive-ports-for-the-fileact-real-time-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="00b05-111">[Step 4B: Start the Send Ports and Receive Ports for the FileAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-4b-start-the-send-and-receive-ports-for-the-fileact-real-time-scenario.md) </span></span>  
 [<span data-ttu-id="00b05-112">Étape 4d : tester une Instance valide pour le scénario en temps réel FileAct</span><span class="sxs-lookup"><span data-stu-id="00b05-112">Step 4D: Test a Valid Instance for the FileAct Real-Time Scenario</span></span>](../../adapters-and-accelerators/fileact-interact/step-4d-test-a-valid-instance-for-the-fileact-real-time-scenario.md)