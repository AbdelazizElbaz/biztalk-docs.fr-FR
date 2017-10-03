---
title: "Étape 4c : créer une Instance de Test pour le magasin de FileAct et d’un scénario de transfert (par extraction) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 50fc72f0-ec00-46f9-b24b-fe8d5e5079ee
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c991dd980df9e19f036b3872289f9d0d8aa82d6e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-4c-create-a-test-instance-for-the-fileact-store-and-forward-pull-scenario"></a><span data-ttu-id="eea40-102">Étape 4c : créer une Instance de Test pour le magasin de FileAct et d’un scénario de transfert (extraction de données)</span><span class="sxs-lookup"><span data-stu-id="eea40-102">Step 4C: Create a Test Instance for the FileAct Store and Forward (Pull) Scenario</span></span>
<span data-ttu-id="eea40-103">Avant de commencer cette étape, vous devez effectuer [étape 4 b : démarrez les Ports d’envoi et les Ports de réception pour et le scénario de (extraits) avant de FileAct](../../adapters-and-accelerators/fileact-interact/step-4b-start-send-and-receive-ports-for-fileact-store-and-forward-scenario.md).</span><span class="sxs-lookup"><span data-stu-id="eea40-103">Before you begin this step, you must complete [Step 4B: Start the Send Ports and Receive Ports for the FileAct Store and Forward (Pull) Scenario](../../adapters-and-accelerators/fileact-interact/step-4b-start-send-and-receive-ports-for-fileact-store-and-forward-scenario.md).</span></span>  
  
### <a name="to-create-a-test-instance"></a><span data-ttu-id="eea40-104">Pour créer une instance de test</span><span class="sxs-lookup"><span data-stu-id="eea40-104">To create a test instance</span></span>  
  
1.  <span data-ttu-id="eea40-105">Ouvrez un nouveau fichier dans un éditeur de texte, tel que le bloc-notes et collez le texte suivant :</span><span class="sxs-lookup"><span data-stu-id="eea40-105">Open a new file in a text editor, such as Notepad, and paste the following:</span></span>  
  
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
    >  <span data-ttu-id="eea40-106">Vous devez remplacer *PhysicalFolderName %* avec le nom du dossier réel que vous avez configurées dans le FILEACT emplacement de réception.</span><span class="sxs-lookup"><span data-stu-id="eea40-106">You must replace *%PhysicalFolderName%* with the actual folder name which you configured in the FILEACT receive location.</span></span>  
  
2.  <span data-ttu-id="eea40-107">Enregistrez le fichier avec le nom ExchangeReqSimple.xml.</span><span class="sxs-lookup"><span data-stu-id="eea40-107">Save the File with the name ExchangeReqSimple.xml.</span></span>  
  
3.  <span data-ttu-id="eea40-108">Ouvrez un nouveau fichier dans un éditeur de texte, tel que le bloc-notes et collez le texte suivant :</span><span class="sxs-lookup"><span data-stu-id="eea40-108">Open a new file in a text editor, such as Notepad, and paste the following:</span></span>  
  
    ```  
    <?xml version="1.0" encoding="utf-8" ?>  
    <Sw-ExchangeSnFRequest>  
    <Sw-SnFRequest>  
    <Sw-SnFOpRequest>  
    <Sw-AcquireSnFRequest>  
    <SwInt-Queue Type the queue name, based on your provisioning with SWIFT </SwInt-Queue>  
    <Sw-SessionMode>Pull</Sw-SessionMode>  
    <Sw-ForceAcquire>TRUE</Sw-ForceAcquire>  
    <Sw-OrderBy>InterAct</Sw-OrderBy>  
    <Sw-RecoveryMode>TRUE</Sw-RecoveryMode>  
    </Sw-AcquireSnFRequest>  
    </Sw-SnFOpRequest>  
    </Sw-SnFRequest>  
    </Sw-ExchangeSnFRequest>  
  
    ```  
  
4.  <span data-ttu-id="eea40-109">Enregistrez le fichier avec le nom acquirequeue.xml.</span><span class="sxs-lookup"><span data-stu-id="eea40-109">Save the File with the name acquirequeue.xml.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eea40-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="eea40-110">See Also</span></span>  
 <span data-ttu-id="eea40-111">[Étape 4 a : démarrer le Service SWIFTNet pour et le scénario de transfert (Pull) de FileAct](../../adapters-and-accelerators/fileact-interact/step-4a-start-swiftnet-service-for-fileact-store-and-forward-pull-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="eea40-111">[Step 4A: Start the SWIFTNet Service for the FileAct Store and Forward (Pull) Scenario](../../adapters-and-accelerators/fileact-interact/step-4a-start-swiftnet-service-for-fileact-store-and-forward-pull-scenario.md) </span></span>  
 <span data-ttu-id="eea40-112">[Étape 4 b : démarrez les Ports d’envoi et de réception pour le magasin de FileAct et d’un scénario de transfert (extraction de données)](../../adapters-and-accelerators/fileact-interact/step-4b-start-send-and-receive-ports-for-fileact-store-and-forward-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="eea40-112">[Step 4B: Start the Send Ports and Receive Ports for the FileAct Store and Forward (Pull) Scenario](../../adapters-and-accelerators/fileact-interact/step-4b-start-send-and-receive-ports-for-fileact-store-and-forward-scenario.md) </span></span>  
 [<span data-ttu-id="eea40-113">Étape 4d : tester une Instance valide pour le magasin de FileAct et d’un scénario de transfert (extraction de données)</span><span class="sxs-lookup"><span data-stu-id="eea40-113">Step 4D: Test a Valid Instance for the FileAct Store and Forward (Pull) Scenario</span></span>](../../adapters-and-accelerators/fileact-interact/step-4d-test-a-valid-instance-for-fileact-store-and-forward-pull-scenario.md)