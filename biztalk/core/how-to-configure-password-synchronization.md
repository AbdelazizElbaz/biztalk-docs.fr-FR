---
title: Comment configurer la synchronisation de mot de passe | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Password Synchronization [SSO], replay files
- Password Synchronization [SSO], maximum age
- SSOCONFIG command line utility
- Password Synchronization [SSO], SSOCONFIG command line utility
- Password Synchronization [SSO], configuring
- configuring, Password Synchronization [SSO]
ms.assetid: 04000dfc-02b9-4d50-babe-8bc8a07a33b7
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fb913c1719f4833ef36cf9f73f6a96432217f2af
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-password-synchronization"></a>Comment configurer la synchronisation de mot de passe
L'utilitaire de ligne de commande SSOCONFIG permet de configurer les paramètres de synchronisation de mot de passe.  
  
### <a name="to-specify-the-directory-for-replay-files"></a>Pour spécifier le répertoire des fichiers de relecture  
  
1.  Dans le menu **Démarrer** , cliquez sur **Exécuter**.  
  
2.  Dans le **exécuter** boîte de dialogue, tapez **cmd**, puis cliquez sur **OK**.  
  
3.  Dans la ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise. La valeur par défaut est \<lecteur > : \Program Files\Enterprise Single Sign-On.  
  
4.  Type **ssoconfig - replayfiles \<répertoire des fichiers de relecture > &#124; - par défaut** et appuyez sur ENTRÉE.  
  
> [!NOTE]
>  Les fichiers de relecture ne sont pas supprimés quand vous modifiez le compte de service. Si vous modifiez celui-ci, vous devrez supprimer les fichiers de relecture manuellement.  
  
#### <a name="to-display-or-change-maximum-password-synchronization-age"></a>Pour afficher ou modifier l'ancienneté maximale de la synchronisation de mot de passe  
  
1.  Dans le menu **Démarrer** , cliquez sur **Exécuter**.  
  
2.  Dans le **exécuter** boîte de dialogue, tapez **cmd**, puis cliquez sur **OK**.  
  
3.  Dans la ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise. La valeur par défaut est \<lecteur > : \Program Files\Enterprise Single Sign-On.  
  
4.  Type **ssoconfig - syncage \<durée de vie maximale en heures >** et appuyez sur ENTRÉE.  
  
> [!NOTE]
>  L'utilitaire SSOCONFIG utilise l'heure de l'ordinateur SQL Server comme heure système. Prenez cet élément en compte lorsque vous utilisez une commande en relation avec l'heure.  
  
## <a name="see-also"></a>Voir aussi  
 [Synchronisation de mot de passe](../core/password-synchronization2.md)