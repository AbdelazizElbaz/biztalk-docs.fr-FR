---
title: Comment installer la synchronisation de mot de passe | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- installing, Password Synchronization [SSO]
- Password Synchronization [SSO], installing
ms.assetid: 8ace0401-b759-4ea3-91a0-be2aa8b5a5a4
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a3a6a3f93e600a8e68581f09af8fcdbc77ed57af
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-install-password-synchronization"></a>Comment installer la synchronisation de mot de passe
À l'instar des autres fonctionnalités d'authentification unique, la synchronisation de mot de passe n'est pas installée par défaut avec [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et doit être sélectionnée lors de l'installation.  
  
### <a name="to-install-password-synchronization"></a>Pour installer la synchronisation de mot de passe  
  
1.  Sur le CD-ROM de BizTalk Server, accédez à la  **\<CDRoot\>\Platforms\SSO** dossier.  
  
2.  Exécutez **setup.exe** et suivez les instructions de l’Assistant.  
  
3.  Sélectionnez le **synchronisation de mot de passe** de fonctionnalité et de poursuivre l’installation.  
  
 Les adaptateurs de synchronisation de mot de passe sont également nécessaires pour envoyer et recevoir les modifications de mot de passe via le système externe. Les rubriques de cette section décrivent la configuration de vos propres adaptateurs.  
  
 Vous pouvez également contacter les alias de support pour obtenir des informations sur les adaptateurs de synchronisation de mot de passe disponibles.  
  
 Enfin, outre la fonctionnalité de synchronisation de mot de passe du service d'authentification unique de l'entreprise (ENTSSO), des composants doivent être installés sur les contrôleurs de domaine pour capturer les modifications de mot de passe effectuées dans Active Directory.  
  
 Le composant de capture de mot de passe Windows et le service de notification de modification de mot de passe (PCNS, Password Change Notification Service) doivent être installés sur tous les contrôleurs de domaine pour lesquels les mots de passe seront capturés. Vous pouvez télécharger ces composants à l'adresse suivante :  
  
 [http://go.Microsoft.com/fwlink/?LinkId=68145](http://go.microsoft.com/fwlink/?LinkId=68145)  
  
 Consultez la documentation associée (également située dans ce dossier) avant de procéder à l'installation sur le contrôleur de domaine.  
  
## <a name="see-also"></a>Voir aussi  
 [Synchronisation de mot de passe](../core/password-synchronization2.md)