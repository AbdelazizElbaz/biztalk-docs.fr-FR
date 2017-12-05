---
title: "Comment désactiver l’authentification unique | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- disabling, SSO
- SSO, disabling
- managing [SSO], disabling
ms.assetid: 0fe4f87a-d7c2-4af6-afee-1065bc4a5285
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d7096a9c77dda72bbf0aea3ec76423c759fa90df
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-disable-sso"></a>Comment désactiver l’authentification unique
Vous pouvez désactiver le système d'authentification unique à l'aide du composant logiciel enfichable MMC ou de la ligne de commande.  
  
 Il y a un court délai avant que tous les serveurs d'authentification unique ne soient désactivés, le temps d'interroger la base de données SSO pour obtenir les dernières informations globales.  
  
### <a name="to-disable-enterprise-single-sign-on-using-the-mmc-snap-in"></a>Pour désactiver l'authentification unique de l'entreprise à l'aide du composant logiciel enfichable MMC  
  
1.  Dans le menu **Démarrer** , cliquez sur **Tous les programmes**, **Authentification unique de l'entreprise Microsoft**, puis sur **Administration SSO**.  
  
2.  Dans le volet d'étendue du composant logiciel enfichable MMC ENTSSO, développez le nœud **Authentification unique de l'entreprise** .  
  
3.  Avec le bouton droit **système**, puis cliquez sur **désactiver**.  
  
### <a name="to-disable-enterprise-single-sign-on-using-the-command-line"></a>Pour désactiver l'authentification unique de l'entreprise à l'aide de la ligne de commande  
  
1.  Sur le **Démarrer** menu, cliquez sur **exécuter**, puis tapez **cmd**.  
  
2.  Dans l'invite de ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise. Le répertoire d’installation par défaut est  *\<lecteur\>*: \Program Files\Enterprise Single Sign-On.  
  
3.  Type **ssomanage – disablesso**.  
  
    > [!NOTE]
    >  Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment activer l’authentification unique](../core/how-to-enable-sso.md)   
 [Utilisation de l’authentification unique](../core/using-sso.md)