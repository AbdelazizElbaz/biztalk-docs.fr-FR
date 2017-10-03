---
title: "Étape 4d : tester une Instance valide pour le magasin d’interagir et le scénario avant | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6aa49df8-ccf6-455a-99ff-38879d2b7bf9
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a5d27b23195adffc5915d8cb2170dca9e975ec94
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-4d-test-a-valid-instance-for-the-interact-store-and-forward-scenario"></a>Étape 4d : tester une Instance valide pour le magasin d’interagir et le scénario avant
Avant de commencer cette étape, vous devez effectuer [étape 4c : créer une Instance de Test pour le magasin d’interagir et le scénario par progression](../../adapters-and-accelerators/fileact-interact/step-4c-create-a-test-instance-for-the-interact-store-and-forward-scenario.md).  
  
### <a name="to-test-a-valid-instance"></a>Pour tester une instance valide  
  
1.  Supprimer le fichier ExchangeReqSimple.xml dans c:\SWIFTAdapterTutorial\Interact\InputRequest_SnF  
  
2.  Vérifiez que le fichier ExchangeReqSimple.xml disparaît après quelques instants, à partir du dossier.  
  
3.  Accédez à C:\SWIFTAdapterTutorial\Interact\HandleRequest. Vérifiez que Sw:HandleRequest se trouve dans le dossier.  
  
4.  Ouvrez le message de Sw:HandleRequest dans un éditeur de texte, tel que le bloc-notes et vérifiez que la section de charge utile est le même que celui du fichier ExchangeReqSimple.xml.  
  
## <a name="see-also"></a>Voir aussi  
 [Étape 4 : Tester le magasin d’interagir et le scénario de bout en bout avant](../../adapters-and-accelerators/fileact-interact/step-4-test-the-interact-store-and-forward-end-to-end-scenario.md)   
 [Étape 4 a : démarrer le Service de SWIFTNet pour le magasin d’interagir et d’un scénario avant](../../adapters-and-accelerators/fileact-interact/step-4a-start-the-swiftnet-service-for-the-interact-store-and-forward-scenario.md)   
 [Étape 4 b : démarrez les Ports d’envoi et Ports de réception pour le magasin d’interagir et d’un scénario avant](../../adapters-and-accelerators/fileact-interact/step-4b-start-the-send-and-receive-ports-for-interact-store-and-forward.md)   
 [Étape 4c : créer une Instance de Test pour le magasin d’interagir et le scénario avant](../../adapters-and-accelerators/fileact-interact/step-4c-create-a-test-instance-for-the-interact-store-and-forward-scenario.md)