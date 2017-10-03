---
title: "Conditions d’erreur d’accusé de réception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- acknowledgements, errors
- errors, acknowledgements
ms.assetid: 605c7fa0-2365-4cb6-92fb-6df570905ca8
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 15b481f4cdb60822841021f7f708a6caea021b8b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="acknowledgment-error-conditions"></a>Conditions d’erreur d’accusé de réception
Les conditions suivantes provoque une erreur irrécupérable quand la condition [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator pour HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) est accusé de réception de traitement des messages (ACK) :  
  
-   Les champs requis dans MSH9 manquants  
  
-   Les champs requis dans MSH12 manquants  
  
 Les conditions suivantes génèrent dans une condition d’erreur non fatale. Dans ce cas, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] génère l’accusé de réception, mais également suspend l’accusé de réception :  
  
-   Un champ obligatoire dans MSH11 manquant  
  
-   Valeur MSH10 manquante  
  
-   Erreurs de type énumération pour les champs facultatifs dans l’en-tête.  
  
> [!NOTE]
>  Pour les erreurs de type énumération trouvés dans l’en-tête lorsque MSH 15 est définie sur AL ou ER, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] génère une validation de l’accusé de réception avec l’état **MSA_1 = CR**.  
  
## <a name="see-also"></a>Voir aussi  
 [Création et le traitement des accusés de réception](../../adapters-and-accelerators/accelerator-hl7/creating-and-processing-acknowledgments.md)   
 [Types de schémas de Message de l’accusé de réception](../../adapters-and-accelerators/accelerator-hl7/ack-message-schema-types.md)   
 [Segment de message d’accusé de réception](../../adapters-and-accelerators/accelerator-hl7/message-acknowledgment-segment.md)   
 [Configuration d’un Port d’envoi pour recevoir des accusés de réception](../../adapters-and-accelerators/accelerator-hl7/setting-up-a-send-port-for-receiving-acks.md)