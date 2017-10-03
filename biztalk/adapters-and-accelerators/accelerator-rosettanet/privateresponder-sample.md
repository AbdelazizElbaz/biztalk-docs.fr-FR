---
title: Exemple de PrivateResponder | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3137fadd-9582-4cc6-acfb-c44aca636950
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3de3428aa9971ba62b682494cd94c6bb74bcab53
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="privateresponder-sample"></a>Exemple de PrivateResponder
L’exemple PrivateResponder.odx contient le code pour le processus privé répondeur installé par [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)]. Ce processus privé générique envoie et reçoit des messages de contenu de service RNIF à partir de la valeur par défaut SQL basé sur un adaptateur d’envoi et ports de réception.  
  
 Par défaut, le [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] programme d’installation installe l’exemple dans \< *lecteur*> : \Program Files\\ [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk \<version > Accelerator for RosettaNet\SDK\ PrivateResponder.  
  
## <a name="sample-contents"></a>Exemple de contenu  
 Le processus privé du répondeur est le processus d’entreprise qui est interne au répondeur. Le processus privé fournit l’intégration de back-end entre le processus public répondeur et que le programme de line-of-business back-end. Le processus privé répondeur communique avec le processus public pour répondre aux messages.  
  
 Le processus privé du répondeur est unique pour chaque implémentation. Vous pouvez personnaliser l’exemple PrivateResponder.odx à vos besoins. Vous devez être prudent que vous n’affectez pas porter le fonctionnement du processus publics répondeur.  
  
 Pour plus d’informations, y compris une description du flux de messages, consultez [répondeur privé processus](../../adapters-and-accelerators/accelerator-rosettanet/responder-private-process.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Exemples d’orchestration](../../adapters-and-accelerators/accelerator-rosettanet/orchestration-samples.md)   
 [Processus privés](../../adapters-and-accelerators/accelerator-rosettanet/private-processes.md)