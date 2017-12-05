---
title: "Activer et de désactivation de l’authentification unique initiée par | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- host initiated SSO, disabling
- disabling, host initiated SSO
- enabling, host initiated SSO
- host initiated SSO, enabling
ms.assetid: a11d314a-6ff9-4d0a-89c3-c412541c2cec
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c1e5783893bbc9091d0a5f1fb3f116b17413bc5d
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-enable-and-disable-host-initiated-sso"></a>Activer et de désactivation de l’authentification unique initiée par
Par défaut, l'authentification unique initiée par l'hôte n'est pas activée dans le système d'authentification unique et doit l'être par l'administrateur de cette authentification.  
  
### <a name="to-enable-host-initiated-sso-using-the-mmc-snap-in"></a>Pour activer l'authentification initiée par l'hôte à l'aide du composant logiciel enfichable MMC  
  
1.  Sur le **Démarrer** menu, cliquez sur **programmes**, cliquez sur **Microsoft Enterprise Single Sign-On**, puis cliquez sur **Administration SSO**.  
  
2.  Dans le volet d'étendue du composant logiciel enfichable MMC ENTSSO, développez le nœud **Authentification unique de l'entreprise** .  
  
3.  Cliquez avec le bouton droit sur **Système**, puis cliquez sur **Propriétés**.  
  
4.  Cliquez sur le **Options** onglet.  
  
5.  Sélectionnez le **l’authentification unique initiée par l’hôte de l’activer** , puis cliquez sur **OK**.  
  
### <a name="to-enable-host-initiated-sso-using-the-command-line"></a>Pour activer l'authentification unique initiée par l'hôte à l'aide de la ligne de commande  
  
1.  Dans le menu **Démarrer** , cliquez sur **Exécuter**.  
  
2.  Dans le **exécuter** boîte de dialogue, tapez **cmd**, puis cliquez sur **OK**.  
  
3.  Dans la ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise. La valeur par défaut est \<lecteur\>: \Program Files\Enterprise Single Sign-On.  
  
4.  Type **ssomanage-activer hisso**.  
  
    > [!NOTE]
    >  Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.  
  
 La désactivation de l'authentification unique s'applique à tout le système d'authentification unique, et toutes les opérations en rapport avec l'hôte l'ayant initiée sont désactivées.  
  
#### <a name="to-disable-host-initiated-sso-using-the-mmc-snap-in"></a>Pour désactiver l'authentification initiée par l'hôte à l'aide du composant logiciel enfichable MMC  
  
1.  Sur le **Démarrer** menu, cliquez sur **programmes**, cliquez sur **Microsoft Enterprise Single Sign-On**, puis cliquez sur **Administration SSO**.  
  
2.  Dans le volet d'étendue du composant logiciel enfichable MMC ENTSSO, développez le nœud **Authentification unique de l'entreprise** .  
  
3.  Cliquez avec le bouton droit sur **Système**, puis cliquez sur **Propriétés**.  
  
4.  Cliquez sur le **Options** onglet.  
  
5.  Désactivez le **l’authentification unique initiée par l’hôte de l’activer** , puis cliquez sur **OK**.  
  
#### <a name="to-disable-host-initiated-sso-using-the-command-line"></a>Pour désactiver l'authentification unique initiée par l'hôte à l'aide de la ligne de commande  
  
1.  Dans le menu **Démarrer** , cliquez sur **Exécuter**.  
  
2.  Dans le **exécuter** boîte de dialogue, tapez **cmd**, puis cliquez sur **OK**.  
  
3.  Dans la ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise. La valeur par défaut est \<lecteur\>: \Program Files\Enterprise Single Sign-On.  
  
4.  Type **ssomanage-désactiver hisso** selon le cas.  
  
    > [!NOTE]
    >  Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.  
  
## <a name="see-also"></a>Voir aussi  
 [Authentification unique initiée par l’hôte](../core/host-initiated-sso.md)