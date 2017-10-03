---
title: "Problèmes connus de traitement par lots | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- batching, known issues
- known issues, batching
ms.assetid: 25c645eb-845d-483a-8f77-398e7dfe0c8f
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b47246662c5945f8ef09040ec7a8aa49326f59db
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="batching-known-issues"></a>Problèmes connus de traitement par lot
Cette section contient des informations utiles qui peuvent vous aider à éviter les erreurs de traitement par lot.  
  
## <a name="batch-trailer-segment-fts-and-bts-fields-are-accepted-even-if-they-are-strings"></a>Champs (recherche en texte intégral et BTS) sont acceptés, même si elles sont des chaînes de segment de code de fin du lot  
 HL7 spécifie les champs dans les segments de recherche en texte intégral et BTS différemment dans les différentes versions de HL7. [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]définit tous les champs en tant que type de données String pour éviter toute incohérence.  
  
## <a name="data-type-of-an-ack-to-a-batch-message"></a>Type de données d’un accusé de réception pour un lot de messages  
 Dans un message d’accusé de réception (ACK) généré en réponse à un lot de messages, si la fragmentation de tiers source est mises hors tension, puis le MSH10 champ (ID de contrôle de message) correspond à un GUID, plutôt que de tout autre type de données du champ MSH10 dans le message du lot.  
  
## <a name="btahl7-configuration-explorer-and-create-batch-orchestrations-are-not-two-way-synchronized"></a>Orchestrations BTAHL7 Configuration Explorer et créer un lot ne sont pas bidirectionnelles synchronisé  
 Vous ne pouvez pas en mesure de consulter l’état actuel de la planification de contrôle de traitement par lots, même si vous appuyez sur F5 dans [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] l’Explorateur de Configuration et vous devrez peut-être activer les deux [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] outil Explorateur de Configuration et l’intégrité et l’activité de suivi du fonctionnement (HAT) en cours état de la planification de contrôle de traitement par lots.  
  
## <a name="two-parsing-errors-logged-when-messages-in-batch-inbatch-out-scenario-contain-validation-errors"></a>Deux erreurs d’analyse enregistré lorsque des messages dans les lots dans / scénario hors lot contiennent des erreurs de validation  
 Lorsque le premier message dans le lot dans / scénario de lot Out (plusieurs messages traités par lot sans en-têtes de lot) contient des erreurs de validation, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] ouvre deux erreurs dans le journal des événements. La première erreur concernant le premier message dans le lot, et la deuxième erreur relative au reste des messages.  
  
## <a name="subscription-using-the-btsmessagetype-property-for-the-batch-inbatch-out-scenario-with-fragmentation-disabled-is-not-supported"></a>Abonnement à l’aide de l’envoi. Propriété MessageType pour le lot dans / scénario de lot sortant avec fragmentation désactivée n’est pas pris en charge.  
 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]ne prend pas en charge l’abonnement à l’aide du **BTS. MessageType** propriété pour le lot dans / lots scénario avec la fragmentation désactivée, car un échange peut se composer de plusieurs types de messages.  
  
## <a name="entire-batch-suspended-after-erroneous-message-in-the-batch-inbatch-out-scenario"></a>Intégralité du lot suspendu après le message erroné dans le lot dans / lots scénario  
 Si un message avec des erreurs d’analyse irrécupérable (par exemple, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] n’analyse pas MSH 9 ou schéma MSH 12 ou le corps du message n’a pas pu charger) est rencontré dans un lot fragmenté dans / même de scénario de lot sortant, toutes les données après la suspension du message erroné if le prise en charge des échanges récupérables a été activée.  
  
## <a name="batch-of-acks-get-routed-to-the-source-party-of-the-first-message-in-batch-inbatch-out-scenario"></a>Traitement des accusés de réception seront acheminés vers la partie de la source du premier message dans un lot dans / lots scénario  
 Dans du lot dans / lot hors lot de scénario d’accusés de réception obtenir basée sur les informations du tiers source du premier message, car cette fonctionnalité supposent que pour tous les messages du trafic entrant par lot de la source et de tiers de destination sont identiques.  
  
## <a name="batch-of-acks-does-not-get-routed-to-the-source-party-when-two-way-receive-port-is-used-in-batch-in-batch-out-scenario"></a>Traitement des accusés de réception ne sont pas acheminé au tiers source lorsque bidirectionnelle recevoir le port est utilisé dans le lot dans / lots scénario  
 En cas de demande-réponse port de réception de que lot ACK/NACK ne sont pas acheminé au tiers source pour le scénario BIBO.  
  
## <a name="see-also"></a>Voir aussi  
 [Problèmes connus](../../adapters-and-accelerators/accelerator-hl7/known-issues1.md)