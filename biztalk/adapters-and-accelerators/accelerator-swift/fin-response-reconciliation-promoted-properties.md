---
title: "Rapprochement de réponse FIN des propriétés promues | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- promoted properties, FIN Response Reconciliation
- FIN Response Reconciliation, promoted properties
ms.assetid: 1a638e9e-61eb-482c-8856-b1aea36c449c
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 14a3e3a004dcb9e58abde08345352c02f0914801
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="fin-response-reconciliation-promoted-properties"></a>Propriétés promues de rapprochement de réponse FIN
Le [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] fonction rapprochement de réponse de FIN inclut les propriétés promues suivantes.  
  
|Nom de promotion| Description|Type de données|Plage de valeurs|Exemple d’utilisation|  
|-------------------|-----------------|---------------|-----------------|-------------------|  
|**A4SWIFT_FRRFailed**|Cette propriété est promue dans un scénario négatif lors de l’envoi du message principal.|Booléen|True<br /><br /> False|Utilisé dans l’expression de filtre d’un port d’envoi FRR pour envoyer un message ayant échoué vers un gestionnaire personnalisé.|  
|**A4SWIFT_FrrFailedReason**|Indique que le message d’origine n’a pas été correctement traité par SAA/SWIFT.|Chaîne|-   \<NAKErrorCode ><br />-Délai d’attente<br />-TransportError<br />-Delayed_NAK<br />-AbortReceived|Utilisé dans l’expression de filtre d’un port d’envoi FRR pour envoyer un message ayant échoué vers un gestionnaire personnalisé.|  
|**A4SWIFT_FRRCorrelationToken**|Indique le jeton de corrélation unique de la sortie MT*xxx* message.|Chaîne|-|FRR compare cette propriété sur le **MQMD_CorrelID** propriété de contexte de la réponse FIN.|  
|**A4SWIFT_SendingServiceType**|Indique le service FRR qui envoie le message.|Chaîne|A4SWIFT_FrrService|Promue lorsque **A4SWIFT_FRRFailed** est définie sur True.|  
  
## <a name="see-also"></a>Voir aussi  
 [A4SWIFT_ * propriétés promues](../../adapters-and-accelerators/accelerator-swift/a4swift-promoted-properties.md)   
 [Propriétés promues du message Repair et New Submission](../../adapters-and-accelerators/accelerator-swift/message-repair-and-new-submission-promoted-properties.md)