---
title: Comment spécifier les administrateurs de l’authentification unique et les applications associées à des administrateurs de comptes | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- administrator accounts, SSO
- enabling, SSO
- SSO, enabling
- disabling, SSO
- SSO, disabling
- managing [SSO], configuring administrator accounts
- managing [SSO], enabling
- managing [SSO], disabling
- SSO, administrator accounts
ms.assetid: 6c300e09-b781-45de-b2da-b1083164a1c0
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6c96e2d99bd6071098a65b3635bb466de44a455d
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/28/2018
---
# <a name="how-to-specify-sso-administrators-and-affiliate-administrators-accounts"></a>Comment spécifier les administrateurs de l’authentification unique et les applications associées à des administrateurs de comptes
Les comptes Administrateurs SSO de l'entreprise et Administrateurs d'applications associées à SSO peuvent être des comptes de groupe d'hôtes ou individuels. Vous devez créer ces comptes avant de configurer le système SSO.  
  
 Si vous utilisez des comptes de domaine, vous devez créer ces deux comptes en tant que groupes de sécurité globale de domaine au sein du contrôleur de domaine. La création de ces comptes incombe à l'administrateur de domaine.  
  
 Vous devez spécifier les comptes Administrateurs SSO et Administrateurs d'applications associées à SSO dans la base de données SSO. Vous devez désactiver le système SSO avant de mettre à jour la base de données SSO avec le groupe Administrateurs SSO.  
  
 Voici un exemple de code XML permettant de mettre à jour la base de données SSO :  
  
```  
<sso>  
<globalInfo>  
<ssoAdminAccount>Domain\Accountname</ssoAdminAccount>  
<ssoAffiliateAdminAccount>Domain\Accountname</ssoAffiliateAdminAccount>  
</globalInfo>  
</sso>  
```  
  
> [!NOTE]
>  L'Assistant Configuration spécifie automatiquement les groupes Administrateurs SSO et Administrateurs d'applications associées à SSO dans la base de données SSO.  
  
> [!NOTE]
>  S'il est impossible de configurer l'authentification unique, il est recommandé de vérifier l'utilisation des comptes de domaine locaux dans un domaine en mode mixte.  
  
### <a name="to-disable-the-enterprise-single-sign-on-system-using-the-mmc-snap-in"></a>Pour désactiver le système d'authentification unique de l'entreprise à l'aide du composant logiciel enfichable MMC  
  
1.  Dans le menu **Démarrer** , cliquez sur **Tous les programmes**, **Authentification unique de l'entreprise Microsoft**, puis sur **Administration SSO**.  
  
2.  Dans le volet d'étendue du composant logiciel enfichable MMC ENTSSO, développez le nœud **Authentification unique de l'entreprise** .  
  
3.  Avec le bouton droit **système**, puis cliquez sur **désactiver**.  
  
### <a name="to-disable-the-enterprise-single-sign-on-system-using-the-command-line"></a>Pour désactiver le système d'authentification unique de l'entreprise à l'aide de la ligne de commande  
  
1.  Sur le **Démarrer** menu, cliquez sur **exécuter**, puis tapez **cmd**.  
  
2.  Dans la ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise. Le répertoire d’installation par défaut est \< *lecteur*\>: \Program Files\Enterprise Single Sign-On.  
  
3.  Type **ssomanage** –**disablesso**.  
  
    > [!NOTE]
    >  Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.  
  
### <a name="to-update-the-sso-database-using-the-mmc-snap-in"></a>Pour mettre à jour la base de données SSO à l'aide du composant logiciel enfichable MMC  
  
1.  Sur le **Démarrer** menu, cliquez sur **tous les programmes**, **Microsoft Enterprise Single Sign-On**, puis **Administration SSO**.  
  
2.  Dans le volet d'étendue du composant logiciel enfichable MMC ENTSSO, développez le nœud **Authentification unique de l'entreprise** .  
  
3.  Avec le bouton droit **système**, puis cliquez sur **mise à jour**.  
  
### <a name="to-update-the-sso-database-using-the-command-line"></a>Pour mettre à jour la base de données SSO à l'aide de la ligne de commande  
  
1.  Sur le **Démarrer** menu, cliquez sur **exécuter**, puis tapez **cmd**.  
  
2.  Dans la ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise. Le répertoire d’installation par défaut est  *\<lecteur\>*: \Program Files\Enterprise Single Sign-On.  
  
3.  Type ** ssomanage-updatedb *\<fichier de mise à jour\>***, où *\<fichier de mise à jour\>* est le chemin d’accès et le nom du fichier XML.  
  
    > [!NOTE]
    >  Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.  
  
### <a name="to-enable-the-enterprise-single-sign-on-system-using-the-mmc-snap-in"></a>Pour activer le système d'authentification unique de l'entreprise à l'aide du composant logiciel enfichable MMC  
  
1.  Sur le **Démarrer** menu, cliquez sur **tous les programmes**, **Microsoft Enterprise Single Sign-On**, puis **Administration SSO**.  
  
2.  Dans le volet d'étendue du composant logiciel enfichable MMC ENTSSO, développez le nœud **Authentification unique de l'entreprise** .  
  
3.  Avec le bouton droit **système**, puis cliquez sur **activer**.  
  
### <a name="to-enable-the-enterprise-single-sign-on-system-using-the-command-line"></a>Pour activer le système d'authentification unique de l'entreprise à l'aide de la ligne de commande  
  
1.  Sur le **Démarrer** menu, cliquez sur **exécuter**, puis tapez **cmd**.  
  
2.  Dans la ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise. Le répertoire d’installation par défaut est  *\<lecteur\>*: \Program Files\Enterprise Single Sign-On.  
  
3.  Type **ssomanage – enablesso**.  
  
    > [!NOTE]
    >  Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.  
  
## <a name="see-also"></a>Voir aussi  
 [Groupes d’utilisateurs de l’authentification unique](../core/sso-user-groups.md)