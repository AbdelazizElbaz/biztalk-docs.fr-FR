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
# <a name="step-4d-test-a-valid-instance-for-the-fileact-store-and-forward-pull-scenario"></a>Étape 4d : tester une Instance valide pour le magasin de FileAct et d’un scénario de transfert (extraction de données)
Avant de commencer cette étape, vous devez effectuer [étape 4c : créer une Instance de Test pour et le scénario de (extraits) avant de FileAct](../../adapters-and-accelerators/fileact-interact/step-4c-create-a-test-instance-for-fileact-store-and-forward-pull-scenario.md).  
  
### <a name="to-test-a-valid-instance"></a>Pour tester une instance valide  
  
1.  Faites glisser le fichier PutReqSimple.xml dans **C:\SWIFTAdapterTutorial\Fileact\FileRequestDropSnF**.  
  
2.  Vérifiez que le fichier PutReqSimple.xml disparaît après quelques instants, à partir du dossier.  
  
3.  Supprimer le fichier fileactcquirequeue.xml dans **C:\SWIFTAdapterTutorial\FileAct\PullRequest**.  
  
4.  Vérifiez que le fichier Sample_Put.txt est transféré à partir de **C:\SWIFTAdapterTutorial\Fileact\ClientLocation** à **C:\SWIFTAdapterTutorial\Fileact\ServerLocation**, et que les réponses apparaissent dans **C:\SWIFTAdapterTutorial\PullResponse**.  
  
## <a name="see-also"></a>Voir aussi  
 [Étape 4 a : démarrer le Service SWIFTNet pour et le scénario de transfert (Pull) de FileAct](../../adapters-and-accelerators/fileact-interact/step-4a-start-swiftnet-service-for-fileact-store-and-forward-pull-scenario.md)   
 [Étape 4 b : démarrez les Ports d’envoi et de réception pour le magasin de FileAct et d’un scénario de transfert (extraction de données)](../../adapters-and-accelerators/fileact-interact/step-4b-start-send-and-receive-ports-for-fileact-store-and-forward-scenario.md)   
 [Étape 4c : créer une Instance de Test pour le magasin de FileAct et d’un scénario de transfert (extraction de données)](../../adapters-and-accelerators/fileact-interact/step-4c-create-a-test-instance-for-fileact-store-and-forward-pull-scenario.md)