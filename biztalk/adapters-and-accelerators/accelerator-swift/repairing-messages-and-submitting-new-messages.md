---
title: "Messages de réparation et de soumission des nouveaux Messages | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- repairing messages
- Message Repair and New Submission
- submitting, messages
- submitting, Message Repair and New Submission
- messages, Message Repair and New Submission
- messages, submitting
- Message Repair and New Submission. about Message Repair and New Submission
ms.assetid: 6abcce90-f611-422a-b3c8-e25f1e75b039
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 59ece524ce06430492a3927c0cd1437eef4b216d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="repairing-messages-and-submitting-new-messages"></a>Messages de réparation et de soumission des nouveaux Messages
[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]Message Repair et New Submission vous permet de réparer un message d’échec de la validation XML ou le moteur des règles d’entreprise. Le processus de réparation inclut des étapes de vérification et approbation qui garantissent la précision et la pertinence de la réparation de message. Ce processus est exécuté à l’aide de [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[btsOfficeNoVersion](../../includes/btsofficenoversion-md.md)] [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] formulaires au sein du site MRSR.  
  
 [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]vous permet également à envoyer un message à l’aide de ce processus. Un créateur d’envoie le message et le flux de travail peut inclure un réparateur, un vérificateur et un approbateur effectuer les mêmes tâches que dans réparation de message.  
  
 [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]permet de garantir la sécurité de ce processus en attribuant différents utilisateurs pour effectuer chaque tâche. Vous affectez la réparation appropriée, vérifiez ou approuvez le rôle de chacun de ces utilisateurs, et chaque utilisateur doit utiliser un certificat spécifique pour effectuer la tâche. [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]Il prend également en charge l’utilisation des services dans le traitement des messages réparés et soumis. Chaque service implique un workflow spécifique des tâches effectuées sur un ensemble spécifique de messages. Dans toute la créer, réparer, vérifiez ou approuver des étapes, lorsque vous envoyez le message, [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] appelle la validation BRE et vérifie que l’utilisateur est un membre du service approprié. Pour plus d’informations sur message repair et new submission, consultez [Message réparer et New Submission](../../adapters-and-accelerators/accelerator-swift/message-repair-and-new-submission.md).  
  
 Si vous recevez un message non analysé, Message Repair et New Submission affiche le message et une description de l’échec dans un [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] écran et vous permet d’afficher le message ou l’enregistrer dans un fichier. Vous pouvez réparer et renvoyez le message. Toutefois, [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] ne pas appeler la validation de BRE ou vérifier l’appartenance à un service quand vous envoyez un message non analysé que vous avez réparé. En outre, un message non analysé soumise à nouveau n'est pas vérifié ou approuvé. Pour plus d’informations sur les messages non analysées, consultez [la réparation des Messages non analysée](../../adapters-and-accelerators/accelerator-swift/repairing-unparsed-messages.md).  
  
 Contenu de cette section :  
  
-   [La réparation d’un Message](../../adapters-and-accelerators/accelerator-swift/repairing-a-message.md)  
  
-   [Vérification d’un Message](../../adapters-and-accelerators/accelerator-swift/verifying-a-message.md)  
  
-   [L’approbation d’un Message](../../adapters-and-accelerators/accelerator-swift/approving-a-message.md)  
  
-   [Gestion d’un Message non analysé](../../adapters-and-accelerators/accelerator-swift/handling-an-unparsed-message.md)  
  
-   [Création et envoi d’un nouveau Message](../../adapters-and-accelerators/accelerator-swift/creating-and-submitting-a-new-message.md)  
  
-   [Création d’un modèle de Message](../../adapters-and-accelerators/accelerator-swift/creating-a-new-message-template.md)