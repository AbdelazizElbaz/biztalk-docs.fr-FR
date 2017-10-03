---
title: Message Repair et New Submission | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- repairing messages
- resubmitting messages
- errors, messages
- messages, errors
- messages, resubmitting
ms.assetid: 5bc6bfa2-8210-4dd3-89bb-5455e294ca92
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5bc15351848fe68d6ef54c31fc6d58c075bb1c58
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="message-repair-and-new-submission"></a>Message Repair et New Submission
La fonctionnalité réparer du Message et de la nouvelle soumission de [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] fournit un moyen de vous permet de réparer les messages de ce dernier et MX dont la validation échouent. Le site SharePoint de MRSR (déployé par l’utilisateur), vous pouvez voir comment le message d’échec de la validation. À partir du site MRSR, vous pouvez ouvrir le message dans un formulaire InfoPath qui vous permet d’identifier l’erreur, réparez le message et les soumettre de retraitement.  
  
 Message Repair et New Submission prend en charge la réparation de message basée sur le rôle. Un flux de travail de réparation complète inclut la réparation, la vérification et approbation. Réparation d’un flux de travail est associé à un service qui définit les rôles (ou les étapes) du flux de travail et configure un utilisateur A4SWIFT pour chaque rôle. Chaque rôle de réparation dispose d’une vue de site MRSR distincte adaptée au rôle. [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]effectue une validation et chaque utilisateur qui A4SWIFT effectue un signe de rôle du message, à l’aide d’un certificat, pour garantir un processus sécurisé.  
  
 En plus de la réparation de message, A4SWIFT vous permet d’envoyer un message à l’aide d’une version améliorée [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] formulaire. Un quatrième utilisateur A4SWIFT, un créateur exécute cette fonction. Le processus effectue la validation et peut impliquer la réparation, la vérification et approbation rôles afin d’envoi réussi. A4SWIFT gère la nouvelle soumission de message via un [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] forment la même manière qu’elle gère un message réparé.  
  
 Contenu de cette section :  
  
-   [Processus de réparation de message](../../adapters-and-accelerators/accelerator-swift/message-repair-process.md)  
  
-   [Création de services et les rôles pour Message Repair et New Submission](../../adapters-and-accelerators/accelerator-swift/creating-departments-and-roles-for-message-repair-and-new-submission.md)  
  
-   [À l’aide d’un formulaire InfoPath à réparer un Message ou envoyez un nouveau Message](../../adapters-and-accelerators/accelerator-swift/using-an-infopath-form-to-repair-a-message-or-submit-a-new-message.md)  
  
-   [Traitement spécial dans le Message Repair et New Submission](../../adapters-and-accelerators/accelerator-swift/special-processing-in-message-repair-and-new-submission.md)  
  
-   [Réparer les Messages non analysées](../../adapters-and-accelerators/accelerator-swift/repairing-unparsed-messages.md)  
  
-   [Nouveau traitement de Service d’envoi et de la réparation de message](../../adapters-and-accelerators/accelerator-swift/message-repair-and-new-submission-service-processing.md)