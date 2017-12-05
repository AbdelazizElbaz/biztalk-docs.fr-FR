---
title: "Comment afficher les informations de base de données SSO | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing [SSO], viewing SSO database
- SSO database, viewing
- viewing, SSO database
ms.assetid: 0ebadd2e-6ea5-460c-b0a8-f48589e6bf1c
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e834874cb87da598db0bc92e516b58dfe2da9069
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-display-the-sso-database-information"></a>Comment afficher les informations de base de données SSO
Vous pouvez afficher les informations de la base de données SSO à l'aide du composant logiciel enfichable MMC ou de l'utilitaire de ligne de commande (ssomanage).  
  
### <a name="to-display-the-sso-database-information-using-the-mmc-snap-in"></a>Pour afficher les informations de la base de données SSO à l'aide du composant logiciel enfichable MMC  
  
1.  Dans le menu **Démarrer** , cliquez sur **Tous les programmes**, **Authentification unique de l'entreprise Microsoft**, puis sur **Administration SSO**.  
  
2.  Dans le volet d'étendue du composant logiciel enfichable MMC ENTSSO, développez le nœud **Authentification unique de l'entreprise** .  
  
3.  Cliquez avec le bouton droit sur **Système**, puis cliquez sur **Propriétés**.  
  
4.  Cliquez sur les onglets dans le **propriétés système** boîte de dialogue pour afficher les informations de base de données SSO.  
  
### <a name="to-display-the-sso-database-information-using-the-command-line"></a>Pour afficher les informations de la base de données SSO à l'aide de la ligne de commande  
  
1.  Sur le **Démarrer** menu, cliquez sur **exécuter**, puis tapez **cmd**.  
  
2.  Dans l'invite de ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise. Le répertoire d’installation par défaut est  **\<lecteur\>**: \Program Files\Enterprise Single Sign-On.  
  
3.  Type **ssomanage – displaydb**.  
  
    > [!NOTE]
    >  Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.  
  
### <a name="to-display-the-sso-database-the-sso-server-is-connected-to-using-the-command-line"></a>Pour afficher la base de données SSO à laquelle le serveur d'authentification unique est connecté à l'aide de la ligne de commande  
  
1.  Sur le **Démarrer** menu, cliquez sur **exécuter**, puis tapez **cmd**.  
  
2.  Dans l'invite de ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise. Le répertoire d’installation par défaut est  **\<lecteur\>**: \Program Files\Enterprise Single Sign-On.  
  
3.  Type **ssomanage – showdb**.  
  
    > [!NOTE]
    >  Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.  
  
 Le tableau suivant décrit les valeurs affichées grâce à ces procédures.  
  
|Propriété|Valeur|  
|--------------|-----------|  
|SQL Server|**\<Nom SQL Server\>**|  
|Base de données de l'authentification unique|**\<Nom de base de données SQL Server\>**|  
|Nom du serveur de secret de l'authentification unique|**\<Nom du serveur de l’authentification unique\>**|  
|Compte des administrateurs de l'authentification unique|Domaine\nom du compte|  
|Compte des administrateurs d'applications associées à authentification unique|Domaine\nom du compte|  
|Taille de la table d'audit pour les applications supprimées (nombre d'entrées d'audit)|1 000 (par défaut)|  
|Taille de la table d'audit pour les mappages d'utilisateurs supprimés (nombre d'entrées d'audit)|1 000 (par défaut)|  
|Taille de la table d'audit pour les recherches d'informations d'identification externes (nombre d'entrées d'audit)|1 000 (par défaut)|  
|Délai d'attente du ticket (en minutes)|2 (valeur par défaut)<br /><br /> Cette valeur doit être un nombre entier compris entre 1 et 525 600|  
|Délai d'attente du cache des informations d'identification (en minutes)|60 (par défaut)|  
|État de l'authentification unique|Activé/désactivé|  
|Tickets autorisés|Oui/non (par défaut)|  
|Valider les tickets|Oui (par défaut)/non|  
  
## <a name="see-also"></a>Voir aussi  
 [Comment configurer les Tickets d’authentification unique](../core/how-to-configure-the-sso-tickets.md)   
 [Utilisation de l’authentification unique](../core/using-sso.md)