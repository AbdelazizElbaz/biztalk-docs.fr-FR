---
title: "Partie 1 : Par lot entrant fragmentés scénario | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- batching, fragmenting messages
- batching tutorial, fragmenting messages
- fragmenting messages
ms.assetid: 8adf2c17-5f66-408d-b30b-51b22d8e71fa
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d8891bd09c803c77e1878b304f5db5b71a26ab9d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="part-1-fragmented-inbound-batch-scenario"></a>Partie 1 : Scénario de lot entrant fragmenté
Dans cette partie du didacticiel, recevoir un lot HL7 encodé, il fragment en messages individuels et envoyer les messages individuels vers une destination. La figure suivante illustre le flux de ce processus.  
  
 ![](../../adapters-and-accelerators/accelerator-hl7/media/hl7-fragmented-inbound-batching-scenario.gif "hl7_fragmented_inbound_batching_scenario")  
  
 Ce scénario inclut le workflow suivant :  
  
1.  Le flux de travail commence quand une application métier-envoie un lot de messages à la [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)] moteur d’intégration à l’aide du protocole de protocole de couche inférieure minimale (MLLP). Le lot contient deux versions d’un ADT ^ A03 message. L’application source appartient au tiers Tutorial_BatchSource.  
  
2.  Le moteur de l’Interface reçoit le lot sur un MLLP port de réception et valide le lot de messages. (Le niveau de validation dépend des paramètres sélectionnés pour la partie de la source dans l’Explorateur de Configuration BTAHL7.)  
  
3.  Basé sur un paramètre dans l’Explorateur de Configuration BTAHL7 qui permet la fragmentation du lot, le moteur d’Interface analyse le lot dans deux ADT individuels ^ A03 messages. Il valide les messages individuels, en fonction de paramètres sélectionnés pour le tiers source dans l’Explorateur de Configuration BTAHL7.  
  
4.  Le moteur de l’Interface génère un accusé de réception pour chaque message, selon les paramètres de la définition d’accusé de réception dans l’Explorateur de Configuration BTAHL7. Dans ce didacticiel, vous allez sélectionner le mode d’accusé de réception d’origine, afin du moteur de l’Interface génère une seule Application accepte d’accusé de réception pour chaque message après la validation de l’en-tête de message et le corps. Le moteur génère l’accusé de réception en fonction du schéma ACK_024_GLO_DEF, passe à « AA » dans le champ MSA2 de l’accusé de réception, passe à des tiers de destination dans MSH3 et passe à la partie source dans MSH5.  
  
5.  Le moteur d’Interface place wrappers MLLP autour de chaque accusé de réception, et les itinéraires les accusés de réception à la source de tiers via un adaptateur d’envoi MLLP configurée pour traiter les accusés de réception.  
  
6.  Le moteur de l’Interface place des wrappers autour de chaque message et les itinéraires configurée pour traiter les messages d’accusé de réception non de port d’envoi de chaque message individuellement pour un MLLP MLLP.  
  
7.  BTAHL7 envoie chaque message via un autre port d’envoi MLLP à la destination spécifiée dans son champ MSH5.  
  
8.  Le tiers de destination envoie à BTAHL7 une acceptation d’accusé de réception pour chaque message qu’il a reçu d’application.  
  
9. Le moteur de l’Interface reçoit chaque accusé de réception.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Étape 1 : Ajouter des schémas d’en-tête et d’accusé de réception](../../adapters-and-accelerators/accelerator-hl7/step-1-add-header-and-acknowledgment-schemas.md)  
  
-   [Étape 2 : Ajouter des schémas courants pour v2.3.1](../../adapters-and-accelerators/accelerator-hl7/step-2-add-common-schemas-for-v2-3-1.md)  
  
-   [Étape 3 : Ajouter un schéma d’événement (Message) de déclencheur](../../adapters-and-accelerators/accelerator-hl7/step-3-add-a-trigger-event-message-schema.md)  
  
-   [Étape 4 : Créer un Port de réception pour accepter le Message du lot](../../adapters-and-accelerators/accelerator-hl7/step-4-create-a-receive-port-for-accepting-the-batch-message.md)  
  
-   [Étape 5 : Créer un Port d’envoi pour remettre des Messages](../../adapters-and-accelerators/accelerator-hl7/step-5-create-a-send-port-to-deliver-messages.md)  
  
-   [Étape 6 : Créer un Port d’envoi pour remettre les accusés de réception](../../adapters-and-accelerators/accelerator-hl7/step-6-create-a-send-port-to-deliver-acknowledgments.md)  
  
-   [Étape 7 : Créer et configurer une partie de la Source](../../adapters-and-accelerators/accelerator-hl7/step-7-create-and-configure-a-source-party.md)  
  
-   [Étape 8 : Redémarrer BizTalk Server](../../adapters-and-accelerators/accelerator-hl7/step-8-restart-biztalk-server.md)  
  
-   [Étape 9 : Vérifier que le scénario par lot entrant fragmentés](../../adapters-and-accelerators/accelerator-hl7/step-9-verify-the-fragmented-inbound-batch-scenario.md)