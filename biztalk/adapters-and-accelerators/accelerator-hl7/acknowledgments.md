---
title: "Accusés de réception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- messages, acknowledgements
- parties, acknowledgements
- acknowledgements, about acknowledgements
- acknowledgements, messages
- acknowledgements, parties
ms.assetid: d25352a4-bae9-4de9-a504-2339bea25c4a
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c519ec4649ee1fbcfbc51edb7e3e8fe6ba6b5871
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="acknowledgments"></a>Accusés de réception
Configurer des accusés de réception HL7 sur le niveau de tiers à l’aide [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator pour HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) l’Explorateur de Configuration. Accusés de réception s’appliquent aux parties qui envoient des messages via un emplacement de réception (et éventuellement l’adaptateur MLLP) et le HL7 HL7 pipeline de réception 2.X. Quand un message termine, l’analyse et la validation, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] peut créer un message d’accusé de réception qui contient le résultat (succès ou erreur) du processus de validation. [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]peut retourner des messages d’accusé de réception de l’une des deux façons. Si le tiers expéditeur d’origine envoyé le message d’origine via bidirectionnel recevoir la configuration du port, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] renvoie le message d’accusé de réception via cet emplacement de port d’origine. Si le port d’envoi d’origine envoyé le message d’origine via unidirectionnel port de réception, puis [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] envoie le message d’accusé de réception dans la base de données MessageBox et l’achemine à l’aide du modèle d’abonnement.[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] effectue l’association de partie pour le traitement du message de réception automatiquement en fonction de la valeur dans le champ d’application émettrice du message HL7 (MSH 3.1).  
  
## <a name="see-also"></a>Voir aussi  
 [Flux de messages](../../adapters-and-accelerators/accelerator-hl7/message-flow.md)