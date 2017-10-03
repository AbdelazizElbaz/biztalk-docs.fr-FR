---
title: Validation des Messages | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- validating, acknowledgements
- messages, acknowledgements
- acknowledgements, validating
- validating, messages
- acknowledgements, messages
- messages, validating
ms.assetid: 7dba0f40-5e19-4598-82cb-22c71e9536c6
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1edaffcab50d6a8af508cb16c9eede39c5ddb952
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="validating-messages"></a>Validation des Messages
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]BizTalk Accelerator pour HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) prend en charge l’envoi des accusés de réception (ACK) pour les messages entrants à partir d’une application ou partenaire sous la forme d’un accusé de réception HL7 XML nécessitant une conversion vers un HL7 encodé le message d’accusé de réception. [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]en général, génère un accusé de réception après avoir vérifié le message entrant par rapport à la spécification de document entrant (format de partenariat commercial) appropriés. Lorsque tous les segments validées, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] renvoie un accusé de réception qui indique à l’application. Dans le cas contraire, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] génère un accusé de réception indiquant une erreur ou échec/refuser.  
  
 Le [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] transmission de l’accusé de réception signale des erreurs syntaxiques et schémas par rapport à la norme HL7. Si la validation échoue, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] place le document dans la file d’attente de messages suspendus et renvoie un accusé de réception détaillant le rejet. Le [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] analyseur effectue la validation qui implique la vérification des types de données, la syntaxe et la validation du schéma. [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]enregistre toutes les erreurs de schémas qui se produisent lors de l’analyse de la réception, ainsi que les détails de l’emplacement.  
  
 Au moment de configurer, vous devez créer le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] artefacts requis pour répondre avec un accusé de réception. Le [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] analyseur crée l’instance de ACK XML canonique HL7. BizTalk convertit au format de version requis dans un mappage BizTalk approprié et valide le format de destination. Le [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] sérialiseur convertit ensuite le message dans une instance HL7 encodé.  
  
> [!NOTE]
>  S’il existe un conflit entre les délimiteurs d’un message entrant et de celles spécifiées dans le [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] configuration, puis [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] génère un message d’accusé de réception qui utilise les délimiteurs mêmes du message entrant et remplace la configuration Paramètres.  
  
## <a name="see-also"></a>Voir aussi  
 [Création et le traitement des accusés de réception](../../adapters-and-accelerators/accelerator-hl7/creating-and-processing-acknowledgments.md)   
 [Guide de programmation](../../adapters-and-accelerators/accelerator-hl7/programming-guide1.md)   
 [Modes d’accusé de réception du Message](../../adapters-and-accelerators/accelerator-hl7/ack-message-modes.md)