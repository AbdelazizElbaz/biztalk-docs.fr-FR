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
# <a name="step-4c-create-a-test-instance-for-the-fileact-real-time-scenario"></a>Étape 4c : créer une Instance de Test pour le scénario en temps réel FileAct
Avant de commencer cette étape, vous devez effectuer [étape 4 b : démarrez les Ports d’envoi et les Ports de réception pour le scénario en temps réel de FileAct](../../adapters-and-accelerators/fileact-interact/step-4b-start-the-send-and-receive-ports-for-the-fileact-real-time-scenario.md).  
  
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
  
2.  Enregistrez le fichier avec le nom « PutReqSimple.xml ».  
  
3.  Assurez-vous que le fichier (Sample_put.txt) est placé dans le dossier d’emplacement du Client.  
  
## <a name="see-also"></a>Voir aussi  
 [Étape 4 : Tester le scénario de bout en bout FileAct en temps réel](../../adapters-and-accelerators/fileact-interact/step-4-test-fileact-real-time-end-to-end-scenario.md)   
 [Étape 4 a : démarrer le Service SWIFTNet pour le scénario en temps réel FileAct](../../adapters-and-accelerators/fileact-interact/step-4a-start-the-swiftnet-service-for-the-fileact-real-time-scenario.md)   
 [Étape 4 b : démarrez les Ports d’envoi et Ports de réception pour le scénario en temps réel FileAct](../../adapters-and-accelerators/fileact-interact/step-4b-start-the-send-and-receive-ports-for-the-fileact-real-time-scenario.md)   
 [Étape 4d : tester une Instance valide pour le scénario en temps réel FileAct](../../adapters-and-accelerators/fileact-interact/step-4d-test-a-valid-instance-for-the-fileact-real-time-scenario.md)