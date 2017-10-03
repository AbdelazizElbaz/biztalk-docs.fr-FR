---
title: "Sécurité du Runtime serveur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security, server runtime
- servers, security
- servers, runtime
ms.assetid: 40f5ca3e-d9d3-4543-bd38-82283c343b76
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9a5979162a521185b87977191c9d709fb754b1ed
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="server-runtime-security"></a>Sécurité du Runtime serveur
[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]Message Repair et New Submission régit le flux de messages SWIFT entre les utilisateurs professionnels, les systèmes back-end et les points de terminaison de réseau rapide de manière sécurisée et déterministe. Il authentifie les messages envoyés par les utilisateurs professionnels, valide les messages pour les données et l’exactitude de la règle d’entreprise et achemine les messages pour les systèmes back-end ou pour une livraison finale au réseau rapide. Pour plus d’informations sur les certificats numériques, consultez « Chiffrement et signature de certificats » sur le site Web MSDN Library à l’adresse [http://go.microsoft.com/fwlink/?linkid=50285](http://go.microsoft.com/fwlink/?linkid=50285).  
  
 Message Repair et New Submission est un [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] application d’orchestration, hébergés et exécutés dans le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] contexte de sécurité. Il est sécurisé dans un [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] application par le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] des fonctionnalités de sécurité décrites précédemment. Message Repair et New Submission également définit et applique les stratégies de sécurité au niveau de l’utilisateur spécifiques à la création de messages SWIFT, de réparation, de l’approbation et de soumission, comme suit :  
  
-   Tous les messages, nouveau ou réparés, soumis à [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] via Message Repair et New Submission doivent provenir d’un utilisateur approuvé.  
  
-   Les utilisateurs approuvés qui créent ou réparer des messages doivent avoir l’autorisation correcte et droits. Les utilisateurs approuvés qui approuvent ou rejettent les messages doivent avoir l’autorisation correcte et droits.  
  
-   Tous les messages doivent être approuvés par un nombre connu des utilisateurs approuvés. Chaque utilisateur approuvé dans la chaîne du créateur de message, réparateur et les approbateurs doit être unique, le même utilisateur ne peut pas créer ou réparer et approuver ou rejeter un message. Le même utilisateur ne peut pas entrer plusieurs approuver ou rejeter les décisions pour un message unique dans un processus d’approbation en plusieurs étapes. Vous ne pouvez pas approuver vos propres messages créés ou réparés, ni vous pouvez approuver le même message que plusieurs approbateurs.  
  
-   Vous ne pouvez pas modifier un message pendant le processus d’approbation (autrement dit, un message ne peut pas être modifié après l’envoi d’origine pour Message Repair et New Submission, en tant que nouvelle ou réparé message).  
  
-   Messages modifiés au cours d’une étape de vérification de changement de clé doivent correspondre exactement le message d’origine (création ou réparées).  
  
 Pour appliquer ces sémantiques de sécurité, le Message réparer et New Submission valide la signature numérique est incorporée dans tous les messages XML qu’il reçoit, à chaque étape du processus de demande d’approbation de la création ou de la réparation. La validation des signatures numériques Message Repair et New Submission effectue les vérifications suivantes. Si un ou plusieurs de ces vérifications échouent, le Message Repair et New Submission s’arrête et sont conservée via la boîte de message et une erreur de sécurité sont enregistrés dans le journal des événements :  
  
-   Le message XML doit être signé numériquement et doit donc contenir une signature numérique correspondante.  
  
-   Chaque signature numérique utilisée dans le flux de travail doit être effectuée à l’aide d’un certificat numérique approuvé. Cela garantit que le créateur de message, réparateur, vérificateur et les approbateurs sont approuvés.  
  
-   Chaque certificat approuvé doit appartenir à un [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] utilisateur de domaine qui est membre du groupe de domaine ayant autorité logique ou des droits pour effectuer des actions dans [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]. Cela garantit que chaque participant dans le processus de création ou de réparation de demande d’approbation a l’ou les droits pour effectuer l’action spécifique qu’il a effectués correct.  
  
     Les règles précédentes sont appliquées via les listes sur le site SharePoint via des groupes d’utilisateurs de site et le code d’envoi de formulaire. Si l’utilisateur agissant sur le message n’est pas dans le [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] groupe d’utilisateurs (domaine ou local), Message Repair et New Submission rejette le message.  
  
     Par exemple, une organisation qui applique un processus d’approbation de trois étapes peut définir ces trois rôles logiques : réparateurs, les vérificateurs (phase de changement de clé) et les approbateurs. En conséquence, les utilisateurs appartenant aux rôles doivent appartenir à la [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] groupe de domaine aux utilisateurs. Pour mieux verrouiller le site SharePoint, les utilisateurs doivent être organisés en groupes de domaine logique (par exemple, réparateurs, vérificateurs, approbateurs).  
  
     Pour plus d’informations sur les groupes d’utilisateurs de site, consultez [sécurité de Windows SharePoint Services](../../adapters-and-accelerators/accelerator-swift/windows-sharepoint-services-security.md).  
  
-   Chaque signature numérique dans la pile doit être unique. Autrement dit, chaque signature numérique doit intervenir à l’aide d’un certificat numérique unique (par rapport à d’autres signatures dans la même pile). Cela garantit que le message n’a pas été approuvé par la personne qui a créé/réparé de message, et qu’aucune personne n’approuvée le même message que plusieurs approbateurs.  
  
 Message Repair et New Submission impose des stratégies de sécurité stricte en ayant des points de contrôle à chaque point d’entrée dans l’infrastructure de création, de réparation, réception et envoi de messages. Ces points de contrôle sont étroitement liés à la fonctionnalité principale de Message Repair et New Submission et ne peut pas être contournées. Pendant que le Message Repair et New Submission est conçu pour s’intégrer sans problème avec le [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] fonctionnalités de signature de formulaire, il est également conçu pour être sécurisé et suffisamment robuste pour appliquer l’authenticité et la protection de systèmes de messages SWIFT même [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] est pas utilisé et les messages sont envoyés directement par les utilisateurs finaux pour Message Repair et New Submission recevoir des points de terminaison (les dossiers SharePoint Web).