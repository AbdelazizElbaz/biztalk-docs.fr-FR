---
title: "Modes de Message d’accusé de réception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- message modes, ACK messages
- messages, acknowledgements
- acknowledgements, message modes
- ACK message modes
ms.assetid: ab4a9470-dab2-46d4-8d0a-54dc12f2fa90
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 122f0851005c7d8abba6c1739ae86a1d65d89625
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="ack-message-modes"></a>Modes d’accusé de réception du Message
Pour les messages d’accusé de réception (ACK), [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator pour HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) détermine le mode d’accusé de réception et les valeurs à utiliser pour remplir les champs MSH15 et MSH16 de l’accusé de réception que vous souhaitez générer. Ces valeurs sont présentes dans la configuration de la gestion des partenaires commerciaux (GPC). Les valeurs suivantes sont possibles pour le mode de l’accusé de réception :  
  
> [!NOTE]
>  Dans la liste suivante, la spécification de HL7 mandate éléments 1 à 3 et qu’ils contiennent des valeurs MSH15 et MSH16. [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]définit l’élément 4 pour indiquer qu’un accusé de réception ne doit pas être généré.  
  
1.  Original - il s’agit d’un accusé de réception après la validation de l’en-tête et corps. Ce mode implique la validation du schéma.  
  
2.  Étendu - deux messages d’accusé de réception envoyés :  
  
    -   Accepter l’accusé de réception – le système de réception envoie ce type d’accusé de réception après la validation de l’en-tête. Cet accusé de réception signale à l’application d’origine que le message est validé dans la base de données.  
  
    -   Système de réception de l’accusé de réception-l’application envoie ce type d’accusé de réception après la validation de message complet, y compris l’en-tête et le corps.  
  
3.  -Deux accusés de réception des messages différés envoyés.  
  
    -   Mode d’origine : Le système de réception envoie ce type d’accusé de réception après la validation de l’en-tête et corps. Ce mode implique la validation du schéma.  
  
    -   Mode différé : L’application métier-accuse réception du message après son traitement. L’application transmet le message différé à [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], qui la traite comme un message autonome, puis les remet à la destination.  
  
4.  Static - un en cas de réussite ou d’échec de l’accusé de réception envoyé.  
  
## <a name="see-also"></a>Voir aussi  
 [Création et le traitement des accusés de réception](../../adapters-and-accelerators/accelerator-hl7/creating-and-processing-acknowledgments.md)   
 [Guide de programmation](../../adapters-and-accelerators/accelerator-hl7/programming-guide1.md)   
 [Modèle de processus de l’accusé de réception](../../adapters-and-accelerators/accelerator-hl7/ack-process-model.md)   
 [Accusés de réception statiques](../../adapters-and-accelerators/accelerator-hl7/static-acknowledgments.md)