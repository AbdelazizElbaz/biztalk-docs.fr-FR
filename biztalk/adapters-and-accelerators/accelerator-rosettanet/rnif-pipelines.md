---
title: Les Pipelines RNIF | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- RNIF, pipelines
- pipelines, RNIF
ms.assetid: 6cf480fe-6b54-4b13-8318-617f3bba71d0
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2cfdc50906f356a7eceeea50dd716c903720f785
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="rnif-pipelines"></a>Pipelines RNIF
Le [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] recevoir et envoyer les pipelines effectuent le traitement nécessaire pour recevoir ou envoyer des messages de Framework RNIF (RosettaNet Implementation). Ce traitement inclut le prétraitement, codage/décodage, déchiffrement et le cryptage, montage/démontage et l’authentification de tiers.  
  
## <a name="pipeline-files"></a>Fichiers de pipeline  
 Standard [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] recevoir et envoyer des pipelines ne traitent pas les messages RNIF en mode natif. [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]a ajouté personnalisée de réception et pipelines d’envoi à cet effet. Ces pipelines sont construits sur la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] pipelines, mais ajouter [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]-les capacités de traitement spécifique. Le [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] pipelines (RNIFReceive.btp et RNIFSend.btp) sont disponibles dans le [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] SDK à l’adresse \< *lecteur*\>: \Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK\RNPipelines. Cela vous permet de les personnaliser selon vos besoins.  
  
## <a name="see-also"></a>Voir aussi  
 [Pipeline de réception BTARN](../../adapters-and-accelerators/accelerator-rosettanet/btarn-receive-pipeline.md)   
 [Pipeline d’envoi BTARN](../../adapters-and-accelerators/accelerator-rosettanet/btarn-send-pipeline.md)