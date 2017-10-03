---
title: "Traitement de Message Repair et New Submission spécial | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- repairing messages, rekey verification
- repairing messages, process flow
- rekey verification
- repairing messages
- messages, templates
- messages, rekey verification
- BIC fields
- templates, messages
- BIC-12 data
- messages, process flow
- BIC-11 data
ms.assetid: 0ab729e3-4b67-47d3-84c9-f016318a4c41
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1d77d518b080fd84b874c9bb79dedd5173d0a78b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="special-processing-in-message-repair-and-new-submission"></a>Traitement spécial dans le Message Repair et New Submission
Le [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] Message Repair et New Submission permet aux clients de développer une implémentation de l’entreprise. La fonctionnalité prend en charge le traitement spécial suivant :  
  
-   Nouvelle clé de vérification  
  
-   Prise en charge des flux de travail de service spécifique (pour plus d’informations, consultez [la réparation des Messages et envoi de nouveaux Messages](../../adapters-and-accelerators/accelerator-swift/repairing-messages-and-submitting-new-messages.md).)  
  
-   Entrée de données BIC-12-11 BIC  
  
-   Entrée de champs BIC sous forme de chaîne  
  
-   Réparation et la nouvelle soumission d’analysent les échecs (pour plus d’informations, consultez [la réparation des Messages non analysée](../../adapters-and-accelerators/accelerator-swift/repairing-unparsed-messages.md).)  
  
-   Répare l’enregistrement en cours d’exécution à l’aide de la commande Enregistrer  
  
-   Création d’un modèle à l’aide de la commande Enregistrer sous  
  
## <a name="rekey-verification"></a>Recomposition de vérification  
 Pour de nombreuses institutions financières, le moyen principal de la vérification du travail est d’une deuxième personne à recomposition champs les plus importants d’une transaction. Cette opération vérifie que la deuxième personne a lu et compris, les données de ces champs. [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]offre cette possibilité pour les messages réparé ou créé dans [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].  
  
 Si une étape de changement de clé est requise, [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] vides les champs à être régénérée sous la forme présentée à l’utilisateur. [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]affiche toujours le contenu du message d’origine dans le volet de tâches, par conséquent, le vérificateur peut utiliser ce contenu lors de la saisie de données. Le vérificateur ne doit pas modifier d’autres champs dans le message, car cela peut permettre de modifications sans vérification. Au lieu de cela, le vérificateur doit rejeter la réparation de message si d’autres modifications doivent être apportées.  
  
 Après l’étape de changement de clé, [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] compare les résultats de la nouvelle clé avec les résultats de la réparation. Il effectue cette comparaison uniquement sur les champs qui ont été régénérées, chaque champ par champ. Si les deux versions ne les acceptez pas chaque caractère par caractère, le message doit être réparé à nouveau. [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]Indique qu’il y a une incompatibilité de vérification de la clé et ajoute l’erreur à la partie de la collection d’erreurs du message. Les données entrées par le vérificateur ne sont pas enregistrées.  
  
 Les champs à être régénérée sont spécifiés dans le fichier MrsrXpathConfig.xml dans le dossier MRSR sous le [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] dossier. Ce fichier contient les paires nom/valeur avec le champ à être régénérée et le xpath dans le champ de. Vous pouvez personnaliser ce fichier pour modifier les champs qui seront être régénérées pour chaque message. Les champs à être régénérée sont généralement ceux représentant la date de plus importante associée avec le contenu du message, la devise de la transaction et le montant de la transaction.  
  
 Toutes les étapes de vérification dans le Message Repair et New Submission impliquent la vérification de changement de clé. Vérification de la vue est effectuée par l’approbateur.  
  
## <a name="entry-of-bic-12-data-as-bic-11"></a>Entrée de données BIC-12-11 BIC  
 [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]prend en charge la nécessité d’un caractère supplémentaire dans l’adresse logique Terminal (LT) d’un message. L’adresse LT contient 11 caractères de données, mais l’accès de Alliance SWIFT (SAA) nécessite le champ LT d’avoir un « X » à la position 9. Ce caractère supplémentaire indique à SAA qu’il doit sélectionner le LT. correct  
  
 L’adresse LT est utilisé pour la transmission du message sur le réseau FIN. Il peut être inclu dans les deux champs d’un message SWIFTBound (champ LT adresse du bloc d’en-tête de base) ou le champ adresse de Destination dans le bloc d’en-tête de l’Application d’entrée et de deux champs d’un message à partir de SWIFT (le champ LT adresse du bloc d’en-tête de base ou le Adresse LT dans la référence du Message d’entrée dans le bloc d’en-tête d’Application de sortie).  
  
 Les utilisateurs doivent entrer uniquement de 11 caractères lorsqu’ils créent ou réparer un message ou recomposition le champ dans le cadre de la vérification. Même lorsque la réparation ou régénération un LT qui a 12 caractères, un utilisateur doit entrer de 11 caractères. [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]Insère le caractère douzième et valide le champ de 12 caractères. [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]valide l’adresse LT de 11 caractères par rapport à l’adresse dans la base de données BIC Plus.  
  
## <a name="entry-of-bic-fields-as-one-string"></a>Entrée de champs BIC sous forme de chaîne  
 Vous pouvez entrer le code BIC dans un champ unique [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] forms. Le code BIC contient quatre sous-champs, chacun d’eux a un sous-champ sur le [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] forms. Une fois que vous entrez la chaîne BIC complète dans le champ unique, [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] remplit chaque quatre sous-champ.  
  
## <a name="saving-repairs-in-progress"></a>L’enregistrement de la réparation en cours  
 Si vous avez besoin interrompre une réparation, vous pouvez enregistrer un message dans son état actuel dans la boîte de réception de réparation. Pour cela, à l’aide de la commande Enregistrer pour archiver le message. Vous pouvez fermer le [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] forme et examinez le message du délai d’attente plus tard, ou une autre personne peut le retirer pour continuer la réparation. Historique du message indique l’enregistrement opération et une deuxième réparateur peuvent voir les corrections que vous avez effectuées.  
  
 Vous pouvez exécuter une commande Enregistrer sous pour stocker un message dans son état actuel sur l’ordinateur local de l’utilisateur. Cela laisse le message extrait par l’utilisateur qui a exécuté la commande Enregistrer sous. L’utilisateur peut fermer le [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] formulaire et retour pour terminer la réparation, mais un autre utilisateur ne peut pas extraire le message et réparez-le.  
  
## <a name="creating-a-new-template"></a>Création d’un modèle  
 Lorsque vous créez un nouveau message, vous pouvez créer un nouveau modèle en exécutant une commande Enregistrer sous. Cela permet d’ouvrir un modèle existant, ajouter des données à des champs, puis créez un nouveau modèle basé sur le modèle existant qui contient les données supplémentaires. Vous enregistrez le modèle avec un nouveau nom, et toute personne ayant accès vers le nouveau dossier de message dans le site MRSR pouvez créer un nouveau message basé sur le modèle. Vous devez enregistrer le modèle sur le site MRSR pour envoyer un message basé sur le modèle à [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]. Sinon, des erreurs se produiront, ou vous ne serez pas en mesure d’ouvrir le formulaire.