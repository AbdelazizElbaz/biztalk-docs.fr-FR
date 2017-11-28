---
title: "Étape 4c : créer une Instance de Test pour et le scénario de transfert de FileAct | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 477abefa-63d0-4cf2-9e4f-67467195efa8
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f0149d93501473e039dca7f4f8c4dbe50e904098
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-4c-create-a-test-instance-for-the-fileact-store-and-forward-scenario"></a><span data-ttu-id="ef1f2-102">Étape 4c : créer une Instance de Test pour et le scénario de transfert de FileAct</span><span class="sxs-lookup"><span data-stu-id="ef1f2-102">Step 4C: Create a Test Instance for the FileAct Store and Forward Scenario</span></span>
<span data-ttu-id="ef1f2-103">Avant de commencer cette étape, vous devez effectuer [étape 4 b : démarrez les Ports d’envoi et les Ports de réception pour et le scénario de transfert de FileAct](../../adapters-and-accelerators/fileact-interact/step-4b-start-the-send-ports-and-receive-ports-for-fileact-store-and-forward.md).</span><span class="sxs-lookup"><span data-stu-id="ef1f2-103">Before you begin this step, you must complete [Step 4B: Start the Send Ports and Receive Ports for the FileAct Store and Forward Scenario](../../adapters-and-accelerators/fileact-interact/step-4b-start-the-send-ports-and-receive-ports-for-fileact-store-and-forward.md).</span></span>  
  
### <a name="to-create-a-test-instance"></a><span data-ttu-id="ef1f2-104">Pour créer une instance de test</span><span class="sxs-lookup"><span data-stu-id="ef1f2-104">To create a test instance</span></span>  
  
1.  <span data-ttu-id="ef1f2-105">Ouvrez un nouveau fichier dans un éditeur de texte, tel que le bloc-notes et collez le texte suivant :</span><span class="sxs-lookup"><span data-stu-id="ef1f2-105">Open a new file in a text editor, such as Notepad, and paste the following:</span></span>  
  
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
  
    > [!NOTE]
    >  <span data-ttu-id="ef1f2-106">Vous devez remplacer PhysicalFolderName % par le nom du dossier réel vous avez configuré dans le FILEACT emplacement de réception.</span><span class="sxs-lookup"><span data-stu-id="ef1f2-106">You must replace %PhysicalFolderName% with the actual folder name you configured in the FILEACT receive location.</span></span>  
  
2.  <span data-ttu-id="ef1f2-107">Enregistrez le fichier avec le nom « PutReqSimple.xml ».</span><span class="sxs-lookup"><span data-stu-id="ef1f2-107">Save the file with the name “PutReqSimple.xml”.</span></span>  
  
3.  <span data-ttu-id="ef1f2-108">Assurez-vous que le fichier (Sample_put.txt) est placé dans le dossier d’emplacement du Client.</span><span class="sxs-lookup"><span data-stu-id="ef1f2-108">Make sure that the file (Sample_put.txt) is placed in the Client Location folder.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef1f2-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ef1f2-109">See Also</span></span>  
 <span data-ttu-id="ef1f2-110">[Étape 4 : Tester et de scénario de bout en bout avant de FileAct](../../adapters-and-accelerators/fileact-interact/step-4-test-fileact-store-and-forward-end-to-end-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="ef1f2-110">[Step 4: Test FileAct Store and Forward End-to-End Scenario](../../adapters-and-accelerators/fileact-interact/step-4-test-fileact-store-and-forward-end-to-end-scenario.md) </span></span>  
 <span data-ttu-id="ef1f2-111">[Étape 4 a : démarrer le Service SWIFTNet pour et le scénario de transfert de FileAct](../../adapters-and-accelerators/fileact-interact/step-4a-start-the-swiftnet-service-for-the-fileact-store-and-forward-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="ef1f2-111">[Step 4A: Start the SWIFTNet Service for the FileAct Store and Forward Scenario](../../adapters-and-accelerators/fileact-interact/step-4a-start-the-swiftnet-service-for-the-fileact-store-and-forward-scenario.md) </span></span>  
 <span data-ttu-id="ef1f2-112">[Étape 4 b : démarrez les Ports d’envoi et de réception pour et le scénario de transfert de FileAct](../../adapters-and-accelerators/fileact-interact/step-4b-start-the-send-ports-and-receive-ports-for-fileact-store-and-forward.md) </span><span class="sxs-lookup"><span data-stu-id="ef1f2-112">[Step 4B: Start the Send Ports and Receive Ports for the FileAct Store and Forward Scenario](../../adapters-and-accelerators/fileact-interact/step-4b-start-the-send-ports-and-receive-ports-for-fileact-store-and-forward.md) </span></span>  
 [<span data-ttu-id="ef1f2-113">Étape 4d : tester une Instance valide pour et le scénario de transfert de FileAct</span><span class="sxs-lookup"><span data-stu-id="ef1f2-113">Step 4D: Test a Valid Instance for the FileAct Store and Forward Scenario</span></span>](../../adapters-and-accelerators/fileact-interact/step-4d-test-a-valid-instance-for-the-fileact-store-and-forward-scenario.md)