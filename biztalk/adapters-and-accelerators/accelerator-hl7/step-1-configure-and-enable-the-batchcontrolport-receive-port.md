---
title: "Étape 1 : Configurer et activer le BatchControlPort Port de réception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: be248a05-e740-497a-b112-8ba3a57b020b
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d50289924062268db078844f2b3d2eaaccda23a2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-1-configure-and-enable-the-batchcontrolport-receive-port"></a>Étape 1 : Configurer et activer le BatchControlPort Port de réception
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]BizTalk Accelerator pour HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) le programme d’installation crée un port de réception, le contrôle du lot le port, pour gérer les messages que l’orchestration de traitement par lots utilise pour démarrer, arrêter et le temps de lots. Ces messages incluent l’activation du lot, arrêt du lot et des messages du minuteur de lot. Dans cette étape, vous configurez le pipeline de réception pour le port de contrôle de traitement par lots, activez le port.  
  
### <a name="to-configure-and-enable-batchcontrolport"></a>Pour configurer et activer BatchControlPort  
  
1.  Démarrer **Administration de BizTalk Server**.  
  
2.  Dans la Console Administration de BizTalk Server, développez **Administration de BizTalk Server**, **groupe BizTalk**, **Applications**, et **Application BizTalk 1**. Cliquez sur **les emplacements de réception**.  
  
3.  Avec le bouton droit **BatchControlLocation**, puis cliquez sur **désactiver**.  
  
4.  Avec le bouton droit **BatchControlLocation**, puis cliquez sur **propriétés**.  
  
5.  Dans la boîte de dialogue Propriétés de l’emplacement de réception pour **Pipeline de réception**, sélectionnez **BTAHL72XPipelines.BTAHL72XReceivePipeline**. Cliquez sur **OK**.  
  
6.  Dans la Console Administration de BizTalk, cliquez sur **BatchControlLocation**, puis cliquez sur **activer**.  
  
 Passez à [étape 2 : activer l’Orchestration de traitement par lots](../../adapters-and-accelerators/accelerator-hl7/step-2-enable-the-batch-orchestration.md).