---
title: "Rapprochement de réponse FIN | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ACKs
- FRR
- FIN Response Reconciliation
- SAA
- NAKs
- FRR, about FRR
- acknowledgements
- FIN Response Reconciliation, about FIN Response Reconciliation
- FIN Response Reconciliation, acknowledgements
ms.assetid: 987b932b-e487-4ca8-acd0-410d71df8e6d
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5452dbacb8a9a20c8d2e62d62f6043aaea2d18da
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="fin-response-reconciliation"></a>Rapprochement de réponse FIN
La fonctionnalité de rapprochement de réponse de FIN (FRR) de [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] rapproche d’une réponse FIN avec le message d’origine correspondant envoyé par [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]. Cela établit l’état du message d’origine et permet [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] prendre des mesures en fonction de cet état. Sans le rapprochement, cela ne serait pas possible. [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]sait qu’il (avec ou sans succès) envoyé le message d’origine à l’autorité d’homologation et il aurait la réponse reçue à partir de l’autorité d’homologation indiquant l’état de la transmission, mais il ne serait pas en mesure d’établir la connexion entre les deux. FRR établit la connexion.  
  
 Réponses FIN sont des accusés de réception (ACK) ou négatifs (NAKs) d’accusés de réception envoyés par SAA à [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)], ou envoyé par le réseau SWIFT à SAA et ensuite transmis par SAA à [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]. La présence ou l’absence de ces accusés de réception définit l’état de l’entreprise du message. Vous pouvez surveiller cet état au moyen de rapports d’analyse BAM (Business Activity).  
  
 Vous pouvez également implémenter le comportement de l’application personnalisée autour de FRR. Un gestionnaire personnalisé peut implémenter votre propre logique pour la gestion de jeux rapprochée des réponses FIN. Pour obtenir un exemple d’un gestionnaire personnalisé qui traite les messages FRR a mis en corrélation avec un message MTS21_FIN_ACKNAK NAK, consultez [FRR NAK Gestionnaire exemple](../../adapters-and-accelerators/accelerator-swift/frr-nak-handler-sample.md).  
  
 L’orchestration FRR est installée par défaut par le [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] programme d’installation. Vous devez configurer le système FRR en créant un pipeline de réception, emplacements de réception et ports d’envoi. Vous devez également configurer FRR pour spécifier la durée pendant laquelle il doit attendre pour NAKs retardées et pour les réponses en général. Pour plus d’informations sur la configuration de FRR et d’administration, consultez [rapprochement de réponse de FIN configuration](../../adapters-and-accelerators/accelerator-swift/configuring-fin-response-reconciliation.md) et [rapprochement de réponse de FIN administration](../../adapters-and-accelerators/accelerator-swift/administering-fin-response-reconciliation.md).  
  
 Contenu de cette section :  
  
-   [Types de réponse FIN](../../adapters-and-accelerators/accelerator-swift/fin-response-types.md)  
  
-   [Traitement de FRR](../../adapters-and-accelerators/accelerator-swift/frr-processing.md)  
  
-   [Orchestration de FRR](../../adapters-and-accelerators/accelerator-swift/frr-orchestration.md)  
  
-   [FRR emplacement de réception pour les Messages à partir de l’Application Back-End.](../../adapters-and-accelerators/accelerator-swift/frr-receive-location-for-messages-from-the-back-end-application.md)  
  
-   [FRR Port d’envoi de Messages SWIFT](../../adapters-and-accelerators/accelerator-swift/frr-send-port-for-messages-to-swift.md)  
  
-   [FRR emplacement de réception pour les Messages à partir de SWIFT](../../adapters-and-accelerators/accelerator-swift/frr-receive-location-for-messages-from-swift.md)  
  
-   [FRR des Ports d’envoi des Messages aux gestionnaires personnalisés](../../adapters-and-accelerators/accelerator-swift/frr-send-ports-for-messages-to-the-custom-handlers.md)  
  
-   [Gestion des ensembles de messages de rapprochement](../../adapters-and-accelerators/accelerator-swift/handling-reconciled-message-sets.md)