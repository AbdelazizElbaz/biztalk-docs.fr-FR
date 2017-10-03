---
title: "Étape 4 b : démarrez les Ports d’envoi et Ports de réception pour le magasin d’interagir et le scénario avant | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c7b0ecd4-ea08-4567-80bd-14f465ba4867
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f5d92b70a1c98a2ff21443980be57d969281fbd3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-4b-start-the-send-ports-and-receive-ports-for-the-interact-store-and-forward-scenario"></a>Étape 4 b : démarrez les Ports d’envoi et Ports de réception pour le magasin d’interagir et d’un scénario avant
Avant de commencer cette étape, vous devez effectuer [étape 4 a : démarrer le SWIFTNet Service pour le magasin d’interagir et le scénario par progression](../../adapters-and-accelerators/fileact-interact/step-4a-start-the-swiftnet-service-for-the-interact-store-and-forward-scenario.md).  
  
### <a name="to-start-the-send-ports-and-receive-ports"></a>Pour démarrer les ports d’envoi et de ports de réception  
  
1.  Démarrer **Administration de BizTalk Server**.  
  
2.  Dans l’arborescence de la console, développez le groupe BizTalk, puis développez l’application BizTalk où vous avez créé les ports d’envoi.  
  
3.  Pour chacun de ces ports d’envoi, cliquez sur le port d’envoi, puis cliquez sur **Démarrer**:  
  
    -   **Tutorial_IA_SendResponseToReceiver**  
  
    -   **Tutorial_IA_SendResponseToSender**  
  
    -   **Tutorial_IA_SendRequest_SnF**  
  
4.  Dans l’arborescence de la console, développez le groupe BizTalk, puis développez l’application BizTalk où vous avez créé les emplacements de réception.  
  
5.  Pour chacun des emplacements de réception suivants, avec le bouton droit à l’emplacement de réception, puis cliquez sur **activer**:  
  
    -   **Tutorial_IA_InputRequest_SnF**  
  
    -   **Tutorial_IA_HandleRequestOneWay_SnF**  
  
## <a name="see-also"></a>Voir aussi  
 [Étape 4 : Tester le magasin d’interagir et le scénario de bout en bout avant](../../adapters-and-accelerators/fileact-interact/step-4-test-the-interact-store-and-forward-end-to-end-scenario.md)   
 [Étape 4 a : démarrer le Service de SWIFTNet pour le magasin d’interagir et d’un scénario avant](../../adapters-and-accelerators/fileact-interact/step-4a-start-the-swiftnet-service-for-the-interact-store-and-forward-scenario.md)   
 [Étape 4c : créer une Instance de Test pour le magasin d’interagir et le scénario avant](../../adapters-and-accelerators/fileact-interact/step-4c-create-a-test-instance-for-the-interact-store-and-forward-scenario.md)   
 [Étape 4d : tester une Instance valide pour le magasin d’interagir et le scénario avant](../../adapters-and-accelerators/fileact-interact/step-4d-test-a-valid-instance-for-the-interact-store-and-forward-scenario.md)