---
title: "Étape 4d : tester une Instance valide pour le scénario en temps réel d’interagir | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e163c3ac-a00d-40cf-b1b8-4a38f74ab0e8
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 94bdb2acd8147ec5041df7d6a1c4324ca833d9e4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-4d-test-a-valid-instance-for-the-interact-real-time-scenario"></a>Étape 4d : tester une Instance valide pour l’interaction du scénario en temps réel
Avant de commencer cette étape, vous devez effectuer [étape 4c : créer une Instance de Test pour le scénario en temps réel interagir](../../adapters-and-accelerators/fileact-interact/step-4c-create-a-test-instance-for-the-interact-real-time-scenario.md).  
  
### <a name="to-test-a-valid-instance"></a>Pour tester une instance valide  
  
1.  Faites glisser le fichier ExchangeReqSimple.xml dans C:\SWIFTAdapterTutorial\Interact\InputRequest_RealTime.  
  
2.  Vérifiez que le fichier ExchangeReqSimple.xml disparaît après quelques instants, à partir du dossier.  
  
3.  Accédez à C:\SWIFTAdapterTutorial\Interact\HandleRequest pour afficher le message de demande de handle Sw:HandleRequest.  
  
4.  Accédez à C:\SWIFTAdapterTutorial\Interact\Response pour afficher le message de réponse de handle Sw:HandleResponse.  
  
5.  Ouvrez le message de Sw:HandleRequest dans un éditeur de texte, tel que le bloc-notes et vérifiez que la section de charge utile est le même que celui du fichier ExchangeReqSimple.xml.  
  
## <a name="see-also"></a>Voir aussi  
 [Étape 4 : Tester l’interaction du scénario de bout en bout en temps réel](../../adapters-and-accelerators/fileact-interact/step-4-test-the-interact-real-time-end-to-end-scenario.md)   
 [Étape 4 a : démarrer le Service SWIFTNet](../../adapters-and-accelerators/fileact-interact/step-4a-start-the-swiftnet-service.md)   
 [Étape 4 b : démarrer les Ports d’envoi et de réception pour l’interaction scénario en temps réel](../../adapters-and-accelerators/fileact-interact/step-4b-start-the-send-and-receive-ports-for-interact-real-time-scenario.md)   
 [Étape 4c : créer une Instance de Test pour l’interaction du scénario en temps réel](../../adapters-and-accelerators/fileact-interact/step-4c-create-a-test-instance-for-the-interact-real-time-scenario.md)