---
title: "Processus de réparation de message | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- repairing messages
- errors, messages
- messages, errors
- validating, messages
- messages, validating
ms.assetid: 87b97cec-5796-4684-bcf0-53285aca7ee2
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 442e49c347b4adf84dd7e6ee86c3b3595452cb34
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="message-repair-process"></a>Processus de réparation de message
Par défaut, [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] suspend les messages ayant échoué dans la file d’attente suspendue de la base de données MessageBox. Ce processus gère les messages ayant échoué séparément à partir des messages de réussite. À l’aide de ce mécanisme par défaut, toutefois, vous devez pouvoir récupérer les messages ayant échoué et les réparer. La fonctionnalité réparer du Message et de la nouvelle soumission de [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] permet une [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] utilisateur pour réparer un message et le renvoyer. Un autre [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] utilisateur peut vérifier puis les réparations, et une troisième peut approuver les réparations.  
  
> [!NOTE]
>  Dans ce contexte, un [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] utilisateur est un utilisateur qui exécute un rôle dans un flux de travail de réparation de service. Cet utilisateur A4SWIFT est défini et associé à un certificat, dans le lien utilisateurs du profil Web Client. Cela [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] utilisateur n’est pas identique à un [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] compte d’utilisateur, tel que défini dans le [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] groupe d’utilisateurs dans le [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] utilitaire de gestion de l’ordinateur. La personne qui fonctionne comme un [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] utilisateur doit avoir un [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] compte d’utilisateur afin qu’ils peuvent utiliser des certificats de ce compte lors de l’envoi d’un message. Toutefois, cette personne peut également servir autres [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] utilisateurs : réparateur, le vérificateur, Approbateur ou créateur. Pour plus d’informations, consultez [des services de création et de rôles pour Message Repair et New Submission](../../adapters-and-accelerators/accelerator-swift/creating-departments-and-roles-for-message-repair-and-new-submission.md).  
  
 Ce flux de travail de réparation [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] ne suspend pas un message ayant échoué. Il effectue un traitement supplémentaire sur le message ayant échoué et supprime le message dans la MessageBox, comme il le ferait un message de réussite. L’orchestration de réparation supprime le message dans le [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] site MRSR, où les utilisateurs peuvent effectuer leurs fonctions dans [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] forms.  
  
## <a name="message-validation"></a>Validation de message  
 Message Repair et New Submission envoie un message d’échec de la validation suivante à un site MRSR pour réparation :  
  
-   Validation structurelle effectuée par l’Analyseur de fichier plat (messages non analysées)  
  
-   Validation des données effectuée par le lecteur de validation de XML  
  
-   Réseau rapide et l’utilisation de règle de validation effectués par le moteur de règles d’entreprise (BRE)  
  
 [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]collecte toutes les erreurs rencontrées lors de la validation dans un objet de collection d’erreurs qui accompagne le message SWIFT. Le processus de réparation inclut des informations sur l’erreur sérialisation en XML et en l’attachant à un message sous la forme d’une partie de l’erreur. Ce traitement inclut également de marquer le message avec une propriété promue qui indique que le message d’échec de la validation ([!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_Failed == True), et le nombre d’une autre propriété promue qui signale l’erreur pour chaque étape de validation. Le message à parties multiples qui en résulte se compose des éléments suivants :  
  
-   Une partie du corps qui contient le message ayant échoué  
  
-   Une partie de l’erreur contenant le XML de la collection d’erreurs  
  
-   Qui indique l’état d’échec des propriétés promues  
  
## <a name="message-repair"></a>Réparation de messages  
 La règle d’entreprise au sein de la MRSRDepartmentPolicy MRSRDepartmentRule détermine le service gère le message ayant échoué. L’orchestration de réparation message démarre le flux de travail de réparation par le routage du message vers une boîte de réception associé au rôle de réparation du service. Le [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] utilisateur joue le rôle de réparation ouvre le message dans la [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] formulaire, répare le message, puis se connecte et l’envoie. L’orchestration achemine le message réparé à chacun des rôles de l’approbation, vérification de changement de clé ou la réparation et une fois que le flux de travail terminé, il achemine le message au port d’envoi.  
  
 En plus de la validation, [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] vérifie les signatures sur le message pour déterminer les éléments suivants :  
  
-   Les utilisateurs dans le flux de travail de réparation appartiennent au même service  
  
-   Chaque utilisateur s’est connecté à une seule fois  
  
-   La séquence de rôles correspondant aux utilisateurs correspond à la séquence dans le flux de travail défini pour ce service  
  
 Pour plus d’informations sur les services, consultez [des services de création et de rôles pour Message Repair et New Submission](../../adapters-and-accelerators/accelerator-swift/creating-departments-and-roles-for-message-repair-and-new-submission.md).  
  
 [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]vous permet également de réparer les messages non analysées. Toutefois, [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] effectue un traitement différent sur un message non analysé réparé. Pour plus d’informations, consultez [la réparation des Messages non analysée](../../adapters-and-accelerators/accelerator-swift/repairing-unparsed-messages.md).