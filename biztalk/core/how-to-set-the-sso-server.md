---
title: "Comment définir le serveur SSO | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- servers, selecting [SSO]
- SSO, selecting servers
- managing [SSO], selecting servers
- SSOManage [SSO]
ms.assetid: a0b0176d-b426-4ab1-8a7e-1f96f4214683
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 96631531cc28ac1bed4ea2b2b56b4b8f9b80c281
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-set-the-sso-server"></a>Comment configurer le serveur d’authentification unique
Chaque fois que vous utilisez ssomanage, vous devez commencer par pointer l'utilisateur sur le serveur d'authentification unique auquel vous voulez vous connecter.  
  
 Vous pouvez le faire de deux façons :  
  
-   Les utilisateurs individuels peuvent se pointer eux-mêmes sur le serveur d'authentification unique approprié.  
  
-   Un administrateur d'ordinateur local pour le serveur d'authentification unique peut pointer tous les membres du compte Utilisateurs d'authentification unique sur ce serveur.  
  
### <a name="to-set-the-enterprise-single-sign-on-server-using-the-mmc-snap-in"></a>Pour définir le serveur d'authentification unique de l'entreprise à l'aide du composant logiciel enfichable MMC  
  
1.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur **Microsoft Enterprise Single Sign-On**, puis cliquez sur **Administration SSO**.  
  
2.  Dans la console MMC enfichable sous le **racine de la Console**, avec le bouton droit **Enterprise Single Sign-On**, puis cliquez sur **sélectionnez**.  
  
3.  Accédez au serveur de votre choix.  
  
4.  Le cas échéant, sélectionnez le **définir le serveur d’authentification unique pour tous les utilisateurs** case à cocher.  
  
5.  Cliquez sur **OK**.  
  
### <a name="to-set-the-enterprise-single-sign-on-server-for-a-single-user-using-the-command-line"></a>Pour définir le serveur d'authentification unique de l'entreprise pour un seul utilisateur à l'aide de la ligne de commande  
  
1.  Sur le **Démarrer** menu, cliquez sur **exécuter**, puis tapez **cmd**.  
  
2.  Dans l'invite de ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise. Le répertoire d’installation par défaut est  **\<lecteur >**: \Program Files\Enterprise Single Sign-On.  
  
3.  Type **ssomanage – server \<nom du serveur SSO >**, où  **\<nom du serveur SSO >** est le nom d’ordinateur unique l’authentification du serveur de l’utilisateur souhaite se connecter à.  
  
    > [!NOTE]
    >  Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.  
  
### <a name="to-set-the-enterprise-single-sign-on-server-for-all-users-using-the-command-line"></a>Pour définir le serveur d'authentification unique de l'entreprise pour tous les utilisateurs à l'aide de la ligne de commande  
  
1.  Sur le **Démarrer** menu, cliquez sur **exécuter**, puis tapez **cmd**.  
  
2.  Dans l'invite de ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise. Le répertoire d’installation par défaut est  **\<lecteur >**: \Program Files\Enterprise Single Sign-On.  
  
3.  Type **ssomanage – serverall \<nom du serveur SSO >**, où  **\<nom du serveur SSO >** est le nom d’ordinateur du serveur d’authentification unique de tous les membres, les utilisateurs de l’authentification unique compte est pointé.  
  
    > [!NOTE]
    >  Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.  
  
### <a name="to-determine-the-enterprise-single-sign-on-server-to-which-a-user-is-connected-using-the-command-line"></a>Pour déterminer le serveur d'authentification unique de l'entreprise auquel un utilisateur est connecté à l'aide de la ligne de commande  
  
1.  Sur le **Démarrer** menu, cliquez sur **exécuter**, puis tapez **cmd**.  
  
2.  Dans l'invite de ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise. Le répertoire d’installation par défaut est  **\<lecteur >**: \Program Files\Enterprise Single Sign-On.  
  
3.  Type **ssomanage – showserver**.  
  
    > [!NOTE]
    >  Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.  
  
> [!NOTE]
>  Cette commande affiche les paramètres pour l'utilisateur actuel ainsi que pour d'autres utilisateurs éventuels.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment activer l’authentification unique](../core/how-to-enable-sso.md)   
 [Comment désactiver l’authentification unique](../core/how-to-disable-sso.md)   
 [Comment afficher les informations de base de données SSO](../core/how-to-display-the-sso-database-information.md)   
 [À l’aide de l’authentification unique](../core/using-sso.md)