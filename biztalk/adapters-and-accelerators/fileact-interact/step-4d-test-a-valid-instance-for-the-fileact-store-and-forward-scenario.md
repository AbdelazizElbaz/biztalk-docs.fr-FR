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
# <a name="step-4d-test-a-valid-instance-for-the-fileact-store-and-forward-scenario"></a>Étape 4d : tester une Instance valide pour et le scénario de transfert de FileAct
Avant de commencer cette étape, vous devez effectuer [étape 4c : créer une Instance de Test pour et le scénario de transfert de FileAct](../../adapters-and-accelerators/fileact-interact/step-4c-create-a-test-instance-for-the-fileact-store-and-forward-scenario.md).  
  
### <a name="to-test-a-valid-instance"></a>Pour tester une instance valide  
  
1.  Faites glisser le fichier PutReqSimple.xml dans C:\SWIFTAdapterTutorial\Fileact\FileRequestDropSnF.  
  
2.  Vérifiez que le fichier PutReqSimple.xml disparaît après quelques instants, à partir du dossier.  
  
3.  Vérifiez que le fichier Sample_Put.txt est transféré de C:\SWIFTAdapterTurorial\Fileact\ClientLocation vers C:\SWIFTAdapterTutorial\Fileact\ServerLocation, et que les réponses apparaissent dans C:\SWIFTAdapterTutorial\ResponseServer.  
  
4.  Recherchez le dossier de l’événement (c:\SWIFTAdapterTutorial\Fileact\StatusEvents) état du trois messages HandleFileEventRequest. Ces messages doivent contenir le statut du transfert suivant :  
  
     Message de HandleFileEventRequest\<Sw-TransferStatus > accepté\</Sw-TransferStatus >  
  
     Message de HandleFileEventRequest \<Sw-TransferStatus > a été initiée\</Sw-TransferStatus >  
  
     Message de HandleFileEventRequest \<Sw-TransferStatus > terminé\</Sw-TransferStatus >  
  
## <a name="see-also"></a>Voir aussi  
 [Étape 4 : Tester et de scénario de bout en bout avant de FileAct](../../adapters-and-accelerators/fileact-interact/step-4-test-fileact-store-and-forward-end-to-end-scenario.md)   
 [Étape 4 a : démarrer le Service SWIFTNet pour et le scénario de transfert de FileAct](../../adapters-and-accelerators/fileact-interact/step-4a-start-the-swiftnet-service-for-the-fileact-store-and-forward-scenario.md)   
 [Étape 4 b : démarrez les Ports d’envoi et de réception pour et le scénario de transfert de FileAct](../../adapters-and-accelerators/fileact-interact/step-4b-start-the-send-ports-and-receive-ports-for-fileact-store-and-forward.md)   
 [Étape 4c : créer une Instance de Test pour et le scénario de transfert de FileAct](../../adapters-and-accelerators/fileact-interact/step-4c-create-a-test-instance-for-the-fileact-store-and-forward-scenario.md)