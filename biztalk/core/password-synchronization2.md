---
title: La synchronisation2 de mot de passe | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SSO, passwords
- passwords, synchronizing [SSO]
- managing [SSO], synchronizing passwords
- Password Synchronization [SSO]
- Password Synchronization [SSO], about Password Synchronization
- SSO database, passwords
ms.assetid: 6d4970e0-ac73-4fca-ab8f-6c8a6f3a6ec0
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b9c12bc9ff5190fe0a76c92b1cfee2233b9d206a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="password-synchronization"></a>Synchronisation d’un mot de passe
La fonction de la synchronisation de mots de passe consiste à simplifier l'administration de la base de données SSO et à synchroniser les mots de passe au sein des annuaires d'utilisateurs.  
  
 Ces deux tâches sont effectuées par l'intermédiaire d'adaptateurs de synchronisation de mots de passe ; les rubriques de cette section présentent l'utilitaire de ligne de commande permettant de créer et de gérer ces adaptateurs.  
  
 Il existe trois types de sous-fonctionnalités de synchronisation de mots de passe.  
  
 Le premier type est **Windows vers externe** (par exemple, Active Directory vers RACF). Dans ce scénario, une modification apportée à un mot de passe utilisateur Windows est capturée puis envoyée au serveur de l'authentification unique de l'entreprise assigné à la réception des modifications des mots de passe des contrôleurs de domaine. Ce serveur transfère ensuite la modification du mot de passe à un système externe et le mappage dans la base de données SSO est synchronisé avec la modification apportée au système externe.  
  
 Le deuxième type est **externe vers Windows - synchronisation complète**. Au cours de ce scénario, un mot de passe est capturé sur le système externe puis envoyé au serveur de l'authentification unique de l'entreprise assigné à la synchronisation des mots de passe. Celui-ci met à jour le mot de passe dans la base de données SSO ainsi que le mot de passe utilisateur Windows dans Active Directory.  
  
 Le troisième type **externe vers Windows - synchronisation partielle**. Lors de ce scénario, un mot de passe est capturé sur le système externe puis envoyé au serveur de l'authentification unique de l'entreprise assigné à la synchronisation des mots de passe. Celui-ci met à jour le mot de passe dans la base de données SSO.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Comment installer la synchronisation de mot de passe](../core/how-to-install-password-synchronization.md)  
  
-   [Comment administrer la synchronisation de mot de passe](../core/how-to-administer-password-synchronization.md)  
  
-   [Comment configurer la synchronisation de mot de passe](../core/how-to-configure-password-synchronization.md)  
  
-   [Comment gérer la synchronisation de mot de passe](../core/how-to-manage-password-synchronization.md)