---
title: Exemple de PrivateInitiator | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4f176566-2a71-487d-84c1-5e7767701e8b
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 853b77e24359d6a833d526fc07166384ea946887
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="privateinitiator-sample"></a>Exemple de PrivateInitiator
L’exemple PrivateInitiator.odx contient le code pour le processus privé initiateur installé par [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® BizTalk Server. Il s’agit d’un processus de privée générique qui envoie et reçoit des messages de contenu de service RNIF à partir de la valeur par défaut SQL basé sur un adaptateur d’envoi et ports de réception.  
  
 Par défaut, le [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] programme d’installation installe l’exemple dans \< *lecteur*\>: \Program Files\\ [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk \<version\> Accelerator for RosettaNet\SDK\PrivateInitiator.  
  
## <a name="sample-contents"></a>Exemple de contenu  
 Le processus privé initiateur est le processus d’entreprise interne à l’initiateur. Le processus privé fournit l’intégration de back-end entre le processus public initiateur et le programme line-of-business back-end. Le processus privé initiateur communique avec le processus public pour initier des messages.  
  
 Le processus privé initiateur est unique pour chaque implémentation. Vous pouvez personnaliser l’exemple PrivateInitiator.odx à vos besoins. Vous devez être prudent que vous n’affectez pas porter le fonctionnement du processus publics initiateur.  
  
 Pour plus d’informations, y compris une description du flux de messages, consultez [les processus privés de l’initiateur](../../adapters-and-accelerators/accelerator-rosettanet/initiator-private-process.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Exemples d’orchestration](../../adapters-and-accelerators/accelerator-rosettanet/orchestration-samples.md)   
 [Processus privés](../../adapters-and-accelerators/accelerator-rosettanet/private-processes.md)