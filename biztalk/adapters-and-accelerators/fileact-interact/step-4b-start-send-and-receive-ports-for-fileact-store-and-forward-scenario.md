---
title: "Étape 4 b : démarrez les Ports d’envoi et de réception pour le magasin de FileAct et d’un scénario de transfert (par extraction) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ea2215c5-fb43-4c7e-a42d-5d131a6dee38
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ad4c6b9d17ab1ea55c1f8378f1cb481a07b09e34
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-4b-start-the-send-ports-and-receive-ports-for-the-fileact-store-and-forward-pull-scenario"></a>Étape 4 b : démarrez les Ports d’envoi et de réception pour le magasin de FileAct et d’un scénario de transfert (extraction de données)
Avant de commencer cette étape, vous devez effectuer [étape 4 a : démarrer le SWIFTNet Service pour et le scénario de (extraits) avant de FileAct](../../adapters-and-accelerators/fileact-interact/step-4a-start-swiftnet-service-for-fileact-store-and-forward-pull-scenario.md).  
  
### <a name="to-start-the-send-ports-and-receive-ports"></a>Pour démarrer les ports d’envoi et de ports de réception  
  
1.  Démarrer **Administration de BizTalk Server**.  
  
2.  Dans l’arborescence de la console, développez le groupe BizTalk, puis développez l’application BizTalk où vous avez créé les ports d’envoi.  
  
3.  Pour chacun de ces ports d’envoi, cliquez sur le port d’envoi, puis cliquez sur **Démarrer**:  
  
    -   **Tutorial_ FA_SendPullResponseToReceiver**  
  
    -   **Tutorial_ FA_SendRequest_SnF**  
  
    -   **Tutorial_ FA_DynamicSendPort**  
  
4.  Dans l’arborescence de la console, développez le groupe BizTalk, puis développez l’application BizTalk où vous avez créé les emplacements de réception.  
  
5.  Pour chacun des emplacements de réception suivants, avec le bouton droit à l’emplacement de réception, puis cliquez sur **activer**:  
  
    -   **Tutorial_ FA_InputRequest_SnF**  
  
    -   **Tutorial_ FA_InputRequest_PullMode**  
  
## <a name="see-also"></a>Voir aussi  
 [Étape 4 a : démarrer le Service SWIFTNet pour et le scénario de transfert (Pull) de FileAct](../../adapters-and-accelerators/fileact-interact/step-4a-start-swiftnet-service-for-fileact-store-and-forward-pull-scenario.md)   
 [Étape 4c : créer une Instance de Test pour le magasin de FileAct et d’un scénario de transfert (extraction de données)](../../adapters-and-accelerators/fileact-interact/step-4c-create-a-test-instance-for-fileact-store-and-forward-pull-scenario.md)   
 [Étape 4d : tester une Instance valide pour le magasin de FileAct et d’un scénario de transfert (extraction de données)](../../adapters-and-accelerators/fileact-interact/step-4d-test-a-valid-instance-for-fileact-store-and-forward-pull-scenario.md)