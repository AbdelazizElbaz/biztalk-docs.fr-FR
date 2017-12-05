---
title: "À l’aide d’un formulaire InfoPath à réparer un Message ou envoyez un nouveau Message | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- creating, messages
- InfoPath forms, verifying messages
- submitting, messages
- InfoPath forms, repairing messages
- Bank Identifier Code (BIC)
- messages, submitting
- messages, repairing
- unparsed messages
- repairing messages, unparsed messages
- messages, unparsed messages
- messages, modifying
- messages, InfoPath forms
- modifying, messages
- messages, approving
- repairing messages, InfoPath forms
- messages, creating
- approving messages
- messages, verifying
- verifying, messages
ms.assetid: fb1a885f-fb01-42be-88bc-f68715f689f7
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a78dabdaefc430fe88e0a5e39d533ee34f0d3db1
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="using-an-infopath-form-to-repair-a-message-or-submit-a-new-message"></a>À l’aide d’un formulaire InfoPath à réparer un Message ou envoyez un nouveau Message
Pour réparer, vérifier, approuver ou créer un message, vous travaillez dans un [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] formulaire que vous ouvrez depuis le [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] site Web de MRSR. Le site MRSR contient un [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] formulaire pour chaque type de message et un [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] formulaire pour les messages non analysées. Message Repair et New Submission envoie des messages ayant besoin de réparation, la vérification ou une approbation à la bibliothèque de documents MRSR appropriée, où vous pouvez l’ouvrir.  
  
 Lorsque vous ouvrez un message dans une bibliothèque de documents MRSR [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] affiche un [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] formulaire rempli avec les données du message. Effectuer l’opération à l’intérieur de la [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] formulaire, ce qui vous permet de manipuler les données dans les champs étiquetés, pour sélectionner des valeurs dans les listes déroulantes (le cas échéant) et pour voir si un champ est obligatoire ou facultatif. [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]garantit que le Message Repair et New Submission processus est sécurisé en demandant à un compte de domaine et de la signature avec un certificat pour la présentation.  
  
 Pour effectuer une opération sur un message dans le [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] site MRSR, vous devez déployer le [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] formulaire pour ce type de message. Cette opération charge le [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] requis pour le message dans la bibliothèque de documents modèles de formulaire.  
  
## <a name="repairing-a-message"></a>La réparation d’un Message  
 Pour réparer, vérifier, approuver ou créer un message, vous travaillez dans un formulaire InfoPath que vous ouvrez à partir du site SharePoint de MRSR. Le message à réparer est publié sur le site MRSR. Message Repair et New Submission envoie des messages ayant besoin de réparation, la vérification ou une approbation à la bibliothèque document du site MRSR appropriée, où vous pouvez l’ouvrir.  
  
 Lorsque vous ouvrez un message dans une bibliothèque de documents du site MRSR, A4SWIFT affiche un formulaire InfoPath rempli avec les données du message. Vous effectuez l’opération dans le formulaire InfoPath, ce qui vous permet de manipuler les données dans les champs étiquetés, pour sélectionner des valeurs dans les listes déroulantes (le cas échéant) et pour voir si un champ est obligatoire ou facultatif. A4SWIFT garantit que le Message Repair et New Submission processus est sécurisé en demandant à un compte de domaine et de la signature avec un certificat pour la présentation.  
  
 Pour effectuer une opération sur un message dans le site MRSR, vous devez déployer le formulaire InfoPath pour ce type de message. Cette opération charge le formulaire InfoPath requis pour le message dans la bibliothèque de documents modèles.  
  
## <a name="verifying-a-message"></a>Vérification d’un Message  
 Un flux de travail de réparation peut inclure une étape de vérification. Dans cette étape, après qu’un réparateur a réparé un message, un vérificateur vérifie que les réparations dans le message sont correctes. Pour ce faire, vous ouvrez le message dans une [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] écran à partir de la \<nom du service informatique\>_RekeyVerify et bibliothèque de documents de votre site MRSR, vérifiez que les réparations effectuées dans le message sont correctes. Vous devez également recomposition des données dans certains champs nécessitant une nouvelle clé. Toutes les étapes de vérification nécessitent la régénération des clés, vous pouvez personnaliser les champs (le cas échéant) ont besoin d’être régénérée. Pour plus d’informations sur la vérification de changement de clé, consultez [un traitement spécial dans le Message Repair et New Submission](../../adapters-and-accelerators/accelerator-swift/special-processing-in-message-repair-and-new-submission.md).  
  
 Un workflow composé de toutes les phases possibles inclut une ou plusieurs étapes de vérification. Toutefois, un flux de travail n’a pas besoin d’inclure une étape de vérification.  
  
## <a name="approving-a-message"></a>L’approbation d’un Message  
 Un flux de travail de réparation peut inclure une étape d’approbation. Dans cette étape, une fois un vérificateur a vérifié les réparations à un message, ou les données dans un nouveau message, un approbateur vérifie visuellement que les réparations dans le message sont correctes. Notez que la phase de vérification se compose d’une vérification de changement de clé, pendant une phase d’approbation se compose d’une vérification de visual.  
  
## <a name="accepting-or-rejecting-the-changes-to-a-message"></a>Accepter ou rejeter les modifications apportées à un Message  
 Après avoir effectué une étape, un créateur réparateur, vérificateur ou approbateur pouvez accepter les modifications, annuler les modifications ou rejeter les modifications. Si la soumission a réussi, acceptation déplace le message à l’étape suivante. Rejet envoie le message avec les modifications rejetées. L’annulation annule le processus de soumission, et le message reste dans sa phase en cours.  
  
 Si vous rejette un message dans la vérifier ou approuver la scène, [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] renvoie le message à la première étape définie pour ce flux de travail (créer ou réparer). Le flux de travail est réinitialisée, afin de n’importe quel réparateur peut réparer le message. Si la première étape du flux de travail rejette le message, l’orchestration de réparation publie le message dans la MessageBox avec les propriétés promues appropriées. Vous pouvez écrire un gestionnaire personnalisé pour traiter ces messages. Pour plus d’informations, consultez [création d’un gestionnaire personnalisé pour les Messages rejetés](../../adapters-and-accelerators/accelerator-swift/creating-a-custom-handler-for-rejected-messages.md).  
  
 Si vous le rejetez un message à l’étape de création ou de la réparation [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] interrompt le message, et vous recevez le message d’erreur : « Impossible de réinitialiser à la première étape dans le flux de travail. »  
  
## <a name="repairing-an-unparsed-message"></a>La réparation d’un Message non analysé  
 Si un message échoue en raison d’une erreur d’analyse, [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] achemine le message vers la bibliothèque de documents non analysée dans le site MRSR. Comme avec les messages que la validation échouent, lorsque vous double-cliquez sur le message, [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] affiche un [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] formulaire rempli avec les données du message. Vous réparez le message dans le formulaire. Lorsque vous envoyez le message, [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] envoie le message directement à la boîte d’envoi sans vérification ou de l’approbation. Pour plus d’informations, consultez [la réparation des Messages non analysée](../../adapters-and-accelerators/accelerator-swift/repairing-unparsed-messages.md).  
  
## <a name="creating-and-submitting-a-new-message"></a>Création et envoi d’un nouveau Message  
 Vous pouvez créer un nouveau message dans le [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] site MRSR en affichant un nouveau formulaire de message, de saisie de données et de sa soumission. Pour plus d’informations, consultez [création et envoi d’un nouveau Message](../../adapters-and-accelerators/accelerator-swift/creating-and-submitting-a-new-message.md).  
  
 Pour créer un nouveau message, vous devez déployer un nouveau formulaire de message pour ce type de message. Cette opération charge le format XML requis pour le message dans une bibliothèque de documents que vous créez pour contenir les formulaires de nouveau message.  
  
 Lorsque vous créez un message à partir du formulaire de nouveau message par défaut, aucun des champs sont remplis, que vous ayez besoin d’entrer des données dans tous les champs. Vous pouvez préremplir les champs dans un formulaire à l’ouverture d’un message, la saisie de données et l’exécution de l’enregistrement-en tant que commande dans le menu fichier dans le site MRSR. Vous pouvez donner le [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] forment un autre nom et l’enregistrer dans une bibliothèque de documents.  
  
## <a name="looking-up-a-bic"></a>Recherche un BIC  
 Lorsque vous travaillez dans un [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] forment dans le [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] site MRSR, vous devrez peut-être entrer un Code identificateur de banque (BIC). [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]fournit un utilitaire que vous pouvez utiliser pour rechercher un BIC. Dans le [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] , cliquez sur la recherche BIC dans le volet droit du formulaire. Cela affiche un écran pour rechercher le code BIC basé sur le nom de la banque, ou vice versa. La table Bicplus de recherche est effectuée dans le [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] base de données. Pour plus d’informations sur la table Bicplus, consultez [l’activation de Validation d’identificateur de Codes de la banque](../../adapters-and-accelerators/accelerator-swift/enabling-validation-of-bank-identifier-codes.md) et [la gestion de la Table dans la base de données A4SWIFT Bicplus](../../adapters-and-accelerators/accelerator-swift/managing-the-bicplus-table-in-the-a4swift-database.md).