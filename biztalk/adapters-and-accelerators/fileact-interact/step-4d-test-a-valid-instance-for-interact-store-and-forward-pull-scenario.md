---
title: "Étape 4d : tester une Instance valide pour le magasin d’interagir et le scénario de transfert (Pull) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7c2933d0-bbe3-4486-832e-5009b2d760ac
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9c9c8ea24eeb5541cf84448363ca91fcb8171f19
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-4d-test-a-valid-instance-for-the-interact-store-and-forward-pull-scenario"></a>Étape 4d : tester une Instance valide pour le magasin d’interagir et le scénario de transfert (Pull)
Avant de commencer cette étape, vous devez effectuer [étape 4c : créer une Instance de Test pour le magasin d’interagir et le scénario de (Pull) vers l’avant](../../adapters-and-accelerators/fileact-interact/step-4c-create-a-test-instance-for-interact-store-and-forward-pull-scenario.md).  
  
### <a name="to-test-a-valid-instance"></a>Pour tester une instance valide  
  
1.  Faites glisser le fichier ExchangeReqSimple.xml dans c:\SWIFTAdapterTutorial\Interact\InputRequest_SnF.  
  
2.  Vérifiez que le fichier ExchangeReqSimple.xml disparaît après quelques instants, à partir du dossier.  
  
3.  Faites glisser le fichier acquirequeue.xml dans c:\SWIFTAdapterTutorial\Interact\PullRequest.  
  
4.  Accédez à C:\SWIFTAdapterTutorial\Interact\PullResponse Vérifiez que Sw:HandleRequest se trouve dans le dossier.  
  
5.  Ouvrez le message de Sw:HandleRequest dans un éditeur de texte, tel que le bloc-notes et vérifiez que la section de charge utile est le même que celui du fichier ExchangeReqSimple.xml.  
  
## <a name="see-also"></a>Voir aussi  
 [Étape 4 a : démarrer le Service de SWIFTNet pour le magasin d’interagir et le scénario de transfert (Pull)](../../adapters-and-accelerators/fileact-interact/step-4a-start-swiftnet-service-for-the-interact-store-and-forward-scenario.md)   
 [Étape 4 b : démarrez les Ports d’envoi et Ports de réception pour le magasin d’interagir et le scénario de transfert (Pull)](../../adapters-and-accelerators/fileact-interact/step-4b-start-send-and-receive-ports-for-interact-store-and-forward-scenario.md)   
 [Étape 4c : créer une Instance de Test pour le magasin d’interagir et le scénario de transfert (Pull)](../../adapters-and-accelerators/fileact-interact/step-4c-create-a-test-instance-for-interact-store-and-forward-pull-scenario.md)