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
# <a name="step-4c-create-a-test-instance-for-the-fileact-store-and-forward-scenario"></a>Étape 4c : créer une Instance de Test pour et le scénario de transfert de FileAct
Avant de commencer cette étape, vous devez effectuer [étape 4 b : démarrez les Ports d’envoi et les Ports de réception pour et le scénario de transfert de FileAct](../../adapters-and-accelerators/fileact-interact/step-4b-start-the-send-ports-and-receive-ports-for-fileact-store-and-forward.md).  
  
### <a name="to-create-a-test-instance"></a>Pour créer une instance de test  
  
1.  Ouvrez un nouveau fichier dans un éditeur de texte, tel que le bloc-notes et collez le texte suivant :  
  
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
    >  Vous devez remplacer PhysicalFolderName % par le nom du dossier réel vous avez configuré dans le FILEACT emplacement de réception.  
  
2.  Enregistrez le fichier avec le nom « PutReqSimple.xml ».  
  
3.  Assurez-vous que le fichier (Sample_put.txt) est placé dans le dossier d’emplacement du Client.  
  
## <a name="see-also"></a>Voir aussi  
 [Étape 4 : Tester et de scénario de bout en bout avant de FileAct](../../adapters-and-accelerators/fileact-interact/step-4-test-fileact-store-and-forward-end-to-end-scenario.md)   
 [Étape 4 a : démarrer le Service SWIFTNet pour et le scénario de transfert de FileAct](../../adapters-and-accelerators/fileact-interact/step-4a-start-the-swiftnet-service-for-the-fileact-store-and-forward-scenario.md)   
 [Étape 4 b : démarrez les Ports d’envoi et de réception pour et le scénario de transfert de FileAct](../../adapters-and-accelerators/fileact-interact/step-4b-start-the-send-ports-and-receive-ports-for-fileact-store-and-forward.md)   
 [Étape 4d : tester une Instance valide pour et le scénario de transfert de FileAct](../../adapters-and-accelerators/fileact-interact/step-4d-test-a-valid-instance-for-the-fileact-store-and-forward-scenario.md)