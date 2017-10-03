---
title: MLLP recevoir et envoyer des composants | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- send components
- Minimal Lower Layer Protocol (MLLP)
- MLLP adapters
- MLLP adapters, wrappers
- wrappers [MLLP adapters]
- receive components
ms.assetid: 2f1c4099-8f52-437a-bdc1-efe707fbf347
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ab82aa317b205d62b8bd05aff513e80d406b658b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="mllp-receive-and-send-components"></a>MLLP recevoir et envoyer des composants
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]BizTalk Accelerator pour HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) prend en charge tous les [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] types d’adaptateur natif, y compris le fichier, HTTP, SQL et FTP. Pour HL7-message réception et l’envoi, toutefois, vous utilisez généralement l’adaptateur MLLP. Cet adaptateur est un adaptateur de socket TCP/IP qui utilise le protocole minimale de couche inférieure (MLLP). Ce protocole permet à des messages bidirectionnels prise en charge et bout en bout de soins de santé intégration d’application.  
  
 Vous pouvez configurer le MLLP comme une carte bidirectionnelle ou une carte à sens unique : adaptateur de réception. Vous pouvez configurer l’adaptateur d’envoi MLLP que l’adaptateur d’envoi une bidirectionnelle avec sollicitation-réponse, unidirectionnel l’adaptateur d’envoi configuré pour recevoir des accusés de réception (ACK) sur la même connexion de socket ou adaptateur qui ne retourne pas les messages d’envoi unidirectionnel. Lorsque vous utilisez bidirectionnel adaptateur MLLP d’envoi de sollicitation-réponse, vous pouvez configurer le port de réception pour renvoyer des accusés de réception ou de messages de réponse. Pour obtenir des exemples de MLLP envoyer et recevoir des adaptateurs, consultez [Interrogative didacticiel](../../adapters-and-accelerators/accelerator-hl7/interrogative-tutorial.md).  
  
 Les messages [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] reçoit ou envoie sur un adaptateur MLLP requièrent les wrappers suivantes :  
  
-   \<SB > caractère de début de bloc  
  
-   \<EB > caractère du bloc de fin  
  
-   \<CR > chariot retourner octets (facultatif)  
  
 Les adaptateurs MLLP fournissent manquantes de gestion des erreurs \<SB > ou \<EB > wrappers, les pertes de connexion ou les délais. Avec un adaptateur MLLP, vous pouvez configurer une limitation du nombre de connexions. Vous pouvez utiliser un vaste choix d’accusés de réception avec un adaptateur MLLP.  
  
## <a name="see-also"></a>Voir aussi  
 [Le traitement des Messages encodés en MLLP](../../adapters-and-accelerators/accelerator-hl7/processing-mllp-encoded-messages.md)   
 [BizTalk Accelerator pour HL7 composants](../../adapters-and-accelerators/accelerator-hl7/biztalk-accelerator-for-hl7-components.md)