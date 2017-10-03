---
title: "Partie 2 : Dans lot scénario | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- batching, outbound batches
- batching, inbound batches
ms.assetid: 36b9d927-f5b7-4c1a-9163-9e79d17c3e9e
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 56ffac38676fe6b163a39ff06be5fe0538800d2c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="part-2-batch-inbatch-out-scenario"></a>Partie 2 : Traitement par lots de dans / lots scénario
Dans cette partie du didacticiel, vous recevez un fichier de commandes de HL7 encodé, transmettre [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] sans fragmentation et envoyez le fichier de commandes intactes à la destination. La figure suivante illustre le flux de ce processus, et la sous-section ci-dessous décrit le flux de travail.  
  
> [!NOTE]
>  Avant de commencer cette partie du didacticiel, désactivez les outils MllpReceive et MllpSend que vous avez utilisé dans la partie 1, en fermant les invites de commandes.  
  
 ![](../../adapters-and-accelerators/accelerator-hl7/media/hl7-batch-in-batch-out-scenario.gif "hl7_batch_in_batch_out_scenario")  
  
 **Le flux des messages dans le lot dans / lots scénario**  
  
 Ce scénario inclut le workflow suivant :  
  
1.  Le flux de travail commence quand une application métier-envoie un lot de messages à la [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator pour HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) en utilisant le protocole de fichier moteur d’intégration. Le lot contient deux versions d’un ADT ^ A03 message. L’application source appartient au tiers Tutorial_BatchSource.  
  
2.  Le moteur d’intégration reçoit le lot sur un fichier de port de réception et valide le lot de messages. (Le niveau de validation dépend des paramètres sélectionnés pour la partie de la source de [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] l’Explorateur de Configuration.)  
  
3.  Basé sur un paramètre dans [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Explorer de Configuration qui désactive la fragmentation de lot pour le tiers, le moteur d’Interface n’analyse pas le lot en messages individuels, mais laisse le lot en tant que lot. Il valide les messages individuels, en fonction de paramètres sélectionnés pour le tiers source dans [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] l’Explorateur de Configuration.  
  
4.  Le moteur de l’Interface génère un accusé de réception pour le message de lot, selon les paramètres de la définition d’accusé de réception dans le [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] éditeur de Configuration pour le tiers. Dans ce cas, vous sélectionnez le mode d’accusé de réception d’origine, afin du moteur de l’Interface génère un accusé de réception de Application accepter unique pour le lot de messages après la validation de l’en-tête de message et le corps. Le moteur génère l’accusé de réception en fonction du schéma ACK_024_GLO_DEF, passe à « AA » dans le champ MSA2 de l’accusé de réception, passe à des tiers de destination dans MSH3 et passe à la partie source dans MSH5.  
  
5.  Les itinéraires de moteur d’Interface que le traitement de l’accusé de réception à la source de tiers via un fichier de l’adaptateur configuré pour traiter les accusés de réception d’envoi. Dans ce cas, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] achemine le lot dans le dossier \Tutorial_BatchACKDrop.  
  
6.  [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]envoie que le lot de messages à la destination spécifiée pour le tiers de destination, dans ce cas, le dossier \Tutorial_BTAHL7Drop.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Étape 1 : Configurer des informations sur le tiers pour le traitement par lots dans / hors du lot](../../adapters-and-accelerators/accelerator-hl7/step-1-configure-party-information-for-batch-in-batch-out.md)  
  
-   [Étape 2 : Modifier ou créer l’envoi et Ports de réception](../../adapters-and-accelerators/accelerator-hl7/step-2-modify-or-create-the-send-and-receive-ports.md)  
  
-   [Étape 3 : Tester le lot dans / lots scénario](../../adapters-and-accelerators/accelerator-hl7/step-3-test-the-batch-in-batch-out-scenario.md)