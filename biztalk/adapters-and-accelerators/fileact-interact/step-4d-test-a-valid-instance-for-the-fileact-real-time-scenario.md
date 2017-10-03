---
title: "Étape 4d : tester une Instance valide pour le scénario en temps réel FileAct | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a8975c90-462b-4c9b-8766-1272ab7ceaba
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 77a9b887bc509ddf3dd67ea941e72cbbeb04a5ea
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-4d-test-a-valid-instance-for-the-fileact-real-time-scenario"></a>Étape 4d : tester une Instance valide pour le scénario en temps réel FileAct
Avant de commencer cette étape, vous devez effectuer [étape 4c : créer une Instance de Test pour le scénario en temps réel de FileAct](../../adapters-and-accelerators/fileact-interact/step-4c-create-a-test-instance-for-the-fileact-real-time-scenario.md).  
  
### <a name="to-test-a-valid-instance"></a>Pour tester une instance valide  
  
1.  Faites glisser le fichier PutReqSimple.xml dans C:\SWIFTAdapterTutorial\Fileact\FileRequestDropRealTime.  
  
2.  Vérifiez que le fichier PutReqSimple.xml disparaît après quelques instants, à partir du dossier.  
  
3.  Vérifiez que le fichier Sample_Put.txt est transféré à partir de : C:\SWIFTAdapterTutorial\Fileact\ClientLocation à C:\SWIFTAdapterTutorial\Fileact\ServerLocation, et que les réponses apparaissent dans C:\SWIFTAdapterTutorial\Fileact\ResponseClient et C:\ SWIFTAdapterTutorial\Fileact\ResponseServer.  
  
4.  Recherchez le dossier de l’événement (c:\SWIFTAdapterTutorial\Fileact\StatusEvents) état du trois messages HandleFileEventRequest. Ces messages doivent contenir le statut du transfert suivant :  
  
     Message de HandleFileEventRequest\<Sw-TransferStatus > accepté\</Sw-TransferStatus >  
  
     Message de HandleFileEventRequest \<Sw-TransferStatus > a été initiée\</Sw-TransferStatus >  
  
     Message de HandleFileEventRequest \<Sw-TransferStatus > terminé\</Sw-TransferStatus >  
  
## <a name="see-also"></a>Voir aussi  
 [Étape 4 : Tester le scénario de bout en bout FileAct en temps réel](../../adapters-and-accelerators/fileact-interact/step-4-test-fileact-real-time-end-to-end-scenario.md)   
 [Étape 4 a : démarrer le Service SWIFTNet pour le scénario en temps réel FileAct](../../adapters-and-accelerators/fileact-interact/step-4a-start-the-swiftnet-service-for-the-fileact-real-time-scenario.md)   
 [Étape 4 b : démarrez les Ports d’envoi et Ports de réception pour le scénario en temps réel FileAct](../../adapters-and-accelerators/fileact-interact/step-4b-start-the-send-and-receive-ports-for-the-fileact-real-time-scenario.md)   
 [Étape 4c : créer une Instance de Test pour le scénario en temps réel FileAct](../../adapters-and-accelerators/fileact-interact/step-4c-create-a-test-instance-for-the-fileact-real-time-scenario.md)