---
title: "Étape 6 : Démarrer les Orchestrations | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- orchestrations, starting
- loopback tutorial, starting orchestratrations
ms.assetid: f16a4a77-04fe-4e73-8517-556668174eb9
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7ef08b7c0db08d527df4943aa25650d81231e703
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-6-start-orchestrations"></a>Étape 6 : Démarrer des Orchestrations
Dans cette étape, vous utilisez [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] pour démarrer les orchestrations pour [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)].  
  
### <a name="to-start-the-btarn-orchestrations-using-visual-studio"></a>Pour démarrer les orchestrations BTARN à l'aide de Visual Studio  
  
1.  Dans la console de gestion **BTARN** , développez successivement **Administration de BizTalk Server**, **Groupe BizTalk**, **Applications**, puis **BizTalk Application 1**.  
  
2.  Cliquez sur **Ports d'envoi**, puis démarrez les ports d'envoi **PrivateInitiator_To_LOB** et **PrivateResponder_To_LOB** .  
  
3.  Cliquez sur **Emplacements de réception**, puis activez les emplacements de réception **LOB_To_PrivateInitiator**, **LOB_To_PrivateResponder**, **Async_Http_Receive**et **Sync_Http_Receive** .  
  
4.  Cliquez sur **Orchestrations**et démarrez toutes les **orchestrations BTARN**.  
  
## <a name="see-also"></a>Voir aussi  
 [Étape 7 : Créer un exemple de Message LOB](../../adapters-and-accelerators/accelerator-rosettanet/step-7-create-a-sample-lob-message.md)   
 [L’arrêt et démarrage des Orchestrations, Ports d’envoi et emplacements de réception par programmation](../../adapters-and-accelerators/accelerator-rosettanet/code-to-stop-and-start-orchestrations-send-ports-and-receive-locations.md)