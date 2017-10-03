---
title: "Pour gérer les mappages utilisateur pour l’hôte authentification unique initiée par | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- maps, host initiated SSO
- host initiated SSO, user maps
ms.assetid: 6b05249e-da35-475b-9c23-5eb556013d57
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4dc65f584bdd474314cd976edc586d0ed60f0505
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-manage-user-mappings-for-host-initiated-sso"></a>Authentification unique initiée par le comment gérer des mappages utilisateur pour l’hôte
Les procédures suivantes permettent de créer des mappages, de définir les informations d'identification et d'activer ou de désactiver le mappage.  
  
### <a name="to-manage-user-mappings-for-host-initiated-sso-using-the-mmc-snap-in"></a>Pour gérer les mappages utilisateur pour l'authentification unique initiée par l'hôte à l'aide du composant logiciel enfichable MMC  
  
1.  Dans le menu **Démarrer** , cliquez sur **Tous les programmes**, **Authentification unique de l'entreprise Microsoft**, puis sur **Administration SSO**.  
  
2.  Dans le volet d'étendue du composant logiciel enfichable MMC ENTSSO, développez le nœud **Authentification unique de l'entreprise** .  
  
3.  Dans le volet d’étendue, cliquez sur **Applications associées**.  
  
4.  Dans le volet Détails, cliquez avec le bouton droit sur l'application associée, puis choisissez l'élément de menu approprié pour votre action.  
  
### <a name="to-create-mappings-in-host-initiated-sso-using-the-command-line"></a>Pour créer des mappages pour l'authentification unique initiée par l'hôte à l'aide de la ligne de commande  
  
1.  Dans le menu **Démarrer** , cliquez sur **Exécuter**.  
  
2.  Dans le **exécuter** boîte de dialogue, tapez **cmd**, puis cliquez sur **OK**.  
  
3.  Dans la ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise. La valeur par défaut est \<lecteur > : \Program Files\Enterprise Single Sign-On.  
  
4.  Type **ssomanage – createmappings \<fichier de mappage >**, où **fichier de mappage >** est le nom du fichier xml.  
  
    > [!NOTE]
    >  Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.  
  
     Voici un exemple de fichier de mappage :  
  
    ```  
    <SSO>  
      <mapping>  
        <windowsDomain>DomainName</windowsDomain>  
        <windowsUserId>UserA</windowsUserId>  
        <externalApplication>SSOApplication</externalApplication>  
    <externalUserId>ExternalUserID that corresponds to UserA</externalUserId>  
      </mapping>  
    </SSO>  
  
    ```  
  
 Lorsque la fonctionnalité de validation du mot de passe est activée pour l'application associée, il est nécessaire de définir les informations d'identification comme suit :  
  
#### <a name="to-set-credentials-for-individual-type-affiliate-applications-using-the-command-line"></a>Pour définir les informations d'identification des applications associées de type individuel à l'aide de la ligne de commande  
  
1.  Dans le menu **Démarrer** , cliquez sur **Exécuter**.  
  
2.  Dans le **exécuter** boîte de dialogue, tapez **cmd**, puis cliquez sur **OK**.  
  
3.  Dans la ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise. La valeur par défaut est \<lecteur > : \Program Files\Enterprise Single Sign-On.  
  
4.  Type **ssomanage - setcredentials \<nom de compte Windows > \<nom de l’application >**.  
  
    > [!NOTE]
    >  Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.  
  
#### <a name="to-set-credentials-for-host-group-type-affiliate-applications-using-the-command-line"></a>Pour définir les informations d'identification des applications associées de type groupe d'hôtes à l'aide de la ligne de commande  
  
1.  Dans le menu **Démarrer** , cliquez sur **Exécuter**.  
  
2.  Dans le **exécuter** boîte de dialogue, tapez **cmd**, puis cliquez sur **OK**.  
  
3.  Dans la ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise. La valeur par défaut est \<lecteur > : \Program Files\Enterprise Single Sign-On.  
  
4.  Type **ssomanage - setcredentials \<nom du compte externe > \<nom de l’application >**.  
  
    > [!NOTE]
    >  Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.  
  
#### <a name="to-enable-mappings-for-individual-type-affiliate-applications-using-the-command-line"></a>Pour activer les mappages des applications associées de type individuel à l'aide de la ligne de commande  
  
1.  Dans le menu **Démarrer** , cliquez sur **Exécuter**.  
  
2.  Dans le **exécuter** boîte de dialogue, tapez **cmd**, puis cliquez sur **OK**.  
  
3.  Dans la ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise. La valeur par défaut est \<lecteur > : \Program Files\Enterprise Single Sign-On.  
  
4.  Type **ssomanage - enablemapping \<nom de compte Windows > \<nom de l’application >**.  
  
    > [!NOTE]
    >  Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.  
  
#### <a name="to-disable-mappings-for-individual-type-affiliate-applications-using-the-command-line"></a>Pour désactiver les mappages des applications associées de type individuel à l'aide de la ligne de commande  
  
1.  Dans le menu **Démarrer** , cliquez sur **Exécuter**.  
  
2.  Dans le **exécuter** boîte de dialogue, tapez **cmd**, puis cliquez sur **OK**.  
  
3.  Dans la ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise. La valeur par défaut est \<lecteur > : \Program Files\Enterprise Single Sign-On.  
  
4.  Type **ssomanage - disablemapping \<nom de compte Windows > \<nom de l’application >**.  
  
    > [!NOTE]
    >  Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.  
  
#### <a name="to-enable-mappings-for-host-group-type-affiliate-applications-using-the-command-line"></a>Pour activer les mappages des applications associées de type groupe d'hôtes à l'aide de la ligne de commande  
  
1.  Dans le menu **Démarrer** , cliquez sur **Exécuter**.  
  
2.  Dans le **exécuter** boîte de dialogue, tapez **cmd**, puis cliquez sur **OK**.  
  
3.  Dans la ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise. La valeur par défaut est \<lecteur > : \Program Files\Enterprise Single Sign-On.  
  
4.  Type **ssomanage - enablemapping \<nom du compte externe > \<nom de l’application >**.  
  
    > [!NOTE]
    >  Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.  
  
#### <a name="to-disable-mappings-for-individual-type-affiliate-applications-using-the-command-line"></a>Pour désactiver les mappages des applications associées de type individuel à l'aide de la ligne de commande  
  
1.  Dans le menu **Démarrer** , cliquez sur **Exécuter**.  
  
2.  Dans le **exécuter** boîte de dialogue, tapez **cmd**, puis cliquez sur **OK**.  
  
3.  Dans la ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise. La valeur par défaut est \<lecteur > : \Program Files\Enterprise Single Sign-On.  
  
4.  Type **ssomanage - disablemapping \<nom du compte externe > \<nom de l’application >**.  
  
    > [!NOTE]
    >  Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.  
  
## <a name="see-also"></a>Voir aussi  
 [L’authentification unique initiée par l’hôte](../core/host-initiated-sso.md)