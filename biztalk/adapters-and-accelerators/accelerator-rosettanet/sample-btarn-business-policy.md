---
title: "Exemple de stratégie d’entreprise BTARN | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: db932c17-8e8f-4f7a-b165-d1d7d749cdb6
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c85cbb7894f0d8bd1b61b7e7856865b49fd33859
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="sample-btarn-business-policy"></a>Exemple de stratégie d'entreprise BTARN
Cet exemple est le code XML associé à un [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] stratégie de règles d’entreprise.  
  
 L’exemple de fichier est samplebtarnpolicy.xml dans \< *lecteur*\>: \Program Files\\ [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk \<version\> Accelerator for RosettaNet\SDK\ PIPAutomation\3A4.  
  
## <a name="demonstrates"></a>Montre  
 Ce code illustre une stratégie de règles d'entreprise avec la règle suivante :  
  
 IF (AccountNumber dans le message de bon de commande entrant 3A4 = « 111111111 ») et (MonetaryAmount de la commande < 500) THEN envoyer automatiquement un message de réponse  
  
## <a name="see-also"></a>Voir aussi  
 [Orchestration de répondeur privé 3A4 avec une règle d’entreprise](../../adapters-and-accelerators/accelerator-rosettanet/3a4-private-responder-orchestration-using-a-business-rule.md)