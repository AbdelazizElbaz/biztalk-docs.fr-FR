---
title: "Comment gérer la synchronisation de mot de passe | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Password Synchronization [SSO], managing
- managing [SSO], disabling features
- managing [SSO], enabling features
- Password Synchronization [SSO], SSOMANAGE command line utility
- SSO database, SSOMANAGE command line utility
- managing, Password Synchronization [SSO]
- SSO database, database settings
- SSOMANAGE command line utility
ms.assetid: 033e63f2-e5b0-4400-99c3-145679d9b84e
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8ce76f2ca16cca44af1658983c49d11f6931e931
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-manage-password-synchronization"></a>Comment gérer la synchronisation de mot de passe
Le composant logiciel enfichable MMC et l'utilitaire de ligne de commande SSOMANAGE permettent d'activer ou de désactiver les fonctionnalités d'authentification unique, ainsi que d'afficher les paramètres de la base de données SSO.  
  
### <a name="to-manage-features-or-display-settings-using-the-mmc-snap-in"></a>Pour gérer les fonctionnalités ou afficher les paramètres à l'aide du composant logiciel enfichable MMC  
  
1.  Cliquez avec le bouton droit sur la fonctionnalité ou la base de données appropriée.  
  
2.  Cliquez sur l'élément de menu approprié.  
  
### <a name="to-enable-sso-features-using-the-command-line"></a>Pour activer les fonctionnalités d'authentification unique à l'aide de l'utilitaire de ligne de commande  
  
1.  Dans le menu **Démarrer** , cliquez sur **Exécuter**.  
  
2.  Dans le **exécuter** boîte de dialogue, tapez **cmd**, puis cliquez sur **OK**.  
  
3.  Dans la ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise. La valeur par défaut est \<lecteur\>: \Program Files\Enterprise Single Sign-On.  
  
4.  Type **ssomanage-activer** et appuyez sur ENTRÉE.  
  
### <a name="to-disable-sso-features-using-the-command-line"></a>Pour désactiver les fonctionnalités d'authentification unique à l'aide de l'utilitaire de ligne de commande  
  
1.  Dans le menu **Démarrer** , cliquez sur **Exécuter**.  
  
2.  Dans le **exécuter** boîte de dialogue, tapez **cmd**, puis cliquez sur **OK**.  
  
3.  Dans la ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise. La valeur par défaut est \<lecteur\>: \Program Files\Enterprise Single Sign-On.  
  
4.  Type **ssomanage-désactiver** et appuyez sur ENTRÉE.  
  
### <a name="to-display-current-database-settings-using-the-command-line"></a>Pour afficher les paramètres de base de données actuels à l'aide de l'utilitaire de ligne de commande  
  
1.  Dans le menu **Démarrer** , cliquez sur **Exécuter**.  
  
2.  Dans le **exécuter** boîte de dialogue, tapez **cmd**, puis cliquez sur **OK**.  
  
3.  Dans la ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise. La valeur par défaut est \<lecteur\>: \Program Files\Enterprise Single Sign-On.  
  
4.  Type **ssomanage - displaydb** et appuyez sur ENTRÉE.  
  
## <a name="see-also"></a>Voir aussi  
 [Synchronisation de mot de passe](../core/password-synchronization2.md)