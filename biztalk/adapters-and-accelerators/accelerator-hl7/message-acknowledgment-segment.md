---
title: "Segment d’accusé de réception de message | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- segments, acknowledgements
- acknowledgements, segments
ms.assetid: 6f2b9f6f-a328-4a0f-9e7d-edba32cc045a
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9547b6d8ddf3013facd94930b5d91ec42db0e5d0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="message-acknowledgment-segment"></a>Segment de message d’accusé de réception
Le segment de Message d’accusé de réception (MSA) d’un message d’accusé de réception (ACK) identifie le type d’accusé de réception envoie le système et indique quel message confirmation de l’accusé de réception. Il se compose de deux segments requis : un code d’accusé de réception et un message d’ID de contrôle.  
  
## <a name="acknowledgment-code-msa1"></a>Code de l’accusé de réception : MSA1  
 Le tableau suivant répertorie les valeurs de champ disponibles MSA1 indiquant le résultat de la réception du message.  
  
|Valeur|Signification| Description|  
|-----------|-------------|-----------------|  
|AA|Accusé de réception application|Le système a reçu le message et le traitement sans problème.|  
|AE|Erreur d’application|Un problème de traitement lié au message ou à sa structure s’est produite au niveau de l’application de réception. Le système d’envoi doit-elle diagnostiquer et corriger le problème avant de tenter de renvoyer le message.|  
|AR|Rejet d’application|Un problème s’est produite à l’emplacement de réception lié à la valeur de MSH9 (type de message), MSH11 (traitement ID), ou MSH12 (ID de version), auquel cas le système d’envoi doit-elle diagnostiquer et corriger le problème avant de renvoyer le message ; ou un problème s’est produite au niveau du système de réception qui correspondait au message ou à sa structure, dans lequel cas le système d’envoi doit renvoyer le message après une période appropriée, sans modification sur le message.|  
  
## <a name="message-control-id-msa2"></a>ID de contrôle de message (MSA2)  
 Le champ MSA2 identifie le message qui accuse réception de l’accusé de réception. [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]BizTalk Accelerator pour HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) génère la valeur dans MSA2 selon le mode d’accusé de réception. Cette valeur permet aux applications émettrices et réceptrices conserver le message et l’accusé de réception est synchronisé. Le tableau suivant répertorie les valeurs disponibles pour le champ MSA2.  
  
|Mode d’accusé de réception|Valeur de MSA2|  
|-------------------------|-------------------|  
|Mode d’origine|Une valeur transposée de la valeur dans la MSH10 (ID de contrôle du message) champ du message d’origine|  
|Mode étendu : Valider l’accusé de réception|Une valeur transposée de la valeur dans la MSH10 (ID de contrôle du message) champ du message d’origine|  
|Mode étendu : Accusé de réception Application|Un GUID généré par [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] pour l’accusé de réception|  
  
## <a name="see-also"></a>Voir aussi  
 [Création et le traitement des accusés de réception](../../adapters-and-accelerators/accelerator-hl7/creating-and-processing-acknowledgments.md)   
 [Types de schémas de Message de l’accusé de réception](../../adapters-and-accelerators/accelerator-hl7/ack-message-schema-types.md)   
 [Configuration d’un Port d’envoi pour recevoir des accusés de réception](../../adapters-and-accelerators/accelerator-hl7/setting-up-a-send-port-for-receiving-acks.md)   
 [Conditions d’erreur d’accusé de réception](../../adapters-and-accelerators/accelerator-hl7/acknowledgment-error-conditions.md)