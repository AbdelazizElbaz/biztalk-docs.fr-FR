---
title: "Partie 3 : Créer de lot scénario | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- batching, creating
- creating, batching
ms.assetid: 02247186-5b21-4738-9110-f0ca0304f0fd
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0949d45fc70ead14338e30b554e0cb4b9694b5d5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="part-3-create-batch-scenario"></a>Partie 3 : Scénario de traitement par lots Créer
Dans cette partie du scénario, vous recevez deux messages entrants, les combinez en un message traité par lot et envoyez le lot vers une destination. BizTalk Accelerator pour HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) renvoie un lot d’accusé de réception contenant deux accusés de réception générés pour les messages à partir de la destination à la source. La figure suivante illustre le processus de cette partie du didacticiel.  
  
 ![](../../adapters-and-accelerators/accelerator-hl7/media/hl7-create-batch-scenario.gif "hl7_create_batch_scenario")  
  
 **Le flux des messages dans le scénario de traitement par lots de créer**  
  
 Ce scénario inclut le workflow suivant :  
  
-   [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]intercepte tous les messages conformes à la définition de lot dans la base de données MessageBox. Vous entrez cette définition dans le **définition de lot** onglet de [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] l’Explorateur de Configuration. Dans ce didacticiel, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] sera intercepter et traiter par lot de tous les messages à envoyer à Tutorial_BatchDest avec un schéma de ADT ^ A03 et tous les accusés de réception à envoyer au Tutorial_BatchSource à la suite ADT ^ A03 messages.  
  
-   Lorsque l’heure d’envoi de traitement par lots planifié se produit, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] envoie un message de contrôle de traitement par lots qui déclenche la transaction par lot sortant. Vous définissez la planification sur la **planification par lot** onglet de [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] l’Explorateur de Configuration. Vous pouvez également déclencher le processus en cliquant sur **envoyer maintenant** sur le même onglet.  
  
-   L’orchestration de traitement par lots constitue le lot de messages à partir des prise au piège dans la base de données MessageBox de messages. L’orchestration inclut également le lot dans un en-tête de fichier et le code de fin et un en-tête de lot et le code de fin. Cette orchestration est natif [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] orchestration ajoutée par [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] le programme d’installation à votre ensemble d’orchestrations BizTalk, afin qu’il est répertorié sous le nœud Orchestrations dans l’Explorateur BizTalk ou de la Console Administration de BizTalk Server.  
  
-   Si accusés de réception sont définis pour le tiers source (comme c’est dans ce cas pour Tutorial_BatchSource), BizTalk traite les accusés de réception et les renvoie dans un lot (vers le dossier \Tutorial_BatchACKDrop). Dans ce didacticiel, les accusés de réception par lot sont envoyées après un court délai.  
  
-   L’orchestration achemine le message vers le port d’envoi (Tutorial_BatchDest), qui envoie le message traité par lot à la destination (dans ce cas, le dossier \Tutorial_BatchMsgDrop sur votre disque dur). Dans ce didacticiel, les messages traités par lot sont envoyées après une heure.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Étape 1 : Configurer et activer le BatchControlPort Port de réception](../../adapters-and-accelerators/accelerator-hl7/step-1-configure-and-enable-the-batchcontrolport-receive-port.md)  
  
-   [Étape 2 : Activer l’Orchestration de traitement par lots](../../adapters-and-accelerators/accelerator-hl7/step-2-enable-the-batch-orchestration.md)  
  
-   [Étape 3 : Créer et configurer un tiers de Destination](../../adapters-and-accelerators/accelerator-hl7/step-3-create-and-configure-a-destination-party.md)  
  
-   [Étape 4 : Configurez la partie de la Source pour le scénario de traitement par lots Créer](../../adapters-and-accelerators/accelerator-hl7/step-4-configure-the-source-party-for-the-create-batch-scenario.md)  
  
-   [Étape 5 : Créer le Port d’envoi pour le lot de messages](../../adapters-and-accelerators/accelerator-hl7/step-5-create-the-send-port-for-the-message-batch.md)  
  
-   [Étape 6 : Créer le Port d’envoi pour le traitement de l’accusé de réception](../../adapters-and-accelerators/accelerator-hl7/step-6-create-the-send-port-for-the-acknowledgment-batch.md)  
  
-   [Étape 7 : Démarrer l’Orchestration et redémarrez le serveur BizTalk](../../adapters-and-accelerators/accelerator-hl7/step-7-start-the-orchestration-and-restart-biztalk-server.md)  
  
-   [Étape 8 : Tester le scénario de traitement par lots Créer](../../adapters-and-accelerators/accelerator-hl7/step-8-test-the-create-batch-scenario.md)