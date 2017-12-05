---
title: "Pour créer des Applications associées pour hôte authentification unique initiée par | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- applications [SSO], host initiated SSO
- creating, applications [SSO]
- host initiated SSO, creating affiliate applications
ms.assetid: 06202d21-055a-46bc-acff-da461f5673f1
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ce8a5cf43cd1d6e455492a74985edb91f2cb0a94
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-create-affiliate-applications-for-host-initiated-sso"></a>Comment créer des Applications associées pour l’authentification unique initiée par l’hôte
Vous pouvez définir deux types d'applications :  
  
-   **Individuels** il existe une relation 1 à 1 entre les utilisateurs Windows et non-Windows.  
  
-   **Groupe hôte** plusieurs utilisateurs non-Windows peuvent être mappés sur le même compte Windows.  
  
### <a name="to-create-an-affiliate-application-using-the-mmc-snap-in"></a>Pour créer une application associée à l'aide du composant logiciel enfichable MMC  
  
1.  Dans le menu **Démarrer** , cliquez sur **Tous les programmes**, **Authentification unique de l'entreprise Microsoft**, puis sur **Administration SSO**.  
  
2.  Dans le volet d'étendue du composant logiciel enfichable MMC ENTSSO, développez le nœud **Authentification unique de l'entreprise** .  
  
3.  Avec le bouton droit **Applications associées**, puis cliquez sur **créer une Application** pour ouvrir le **unique Sign-On Assistant Application d’entreprise**.  
  
4.  Utilisez l'Assistant pour sélectionner les propriétés de votre application associée.  
  
### <a name="to-create-an-individual-type-affiliate-application-using-the-command-line"></a>Pour créer une application associée de type individuel à l'aide d'une ligne de commande  
  
1.  Dans le menu **Démarrer** , cliquez sur **Exécuter**.  
  
2.  Dans le **exécuter** boîte de dialogue, tapez **cmd**, puis cliquez sur **OK**.  
  
3.  Dans la ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise. La valeur par défaut est \<lecteur\>: \Program Files\Enterprise Single Sign-On.  
  
4.  Type **ssomanage – createapps \<AffApp.xml\>**, où AffApp.xml est le nom du fichier xml.  
  
    > [!NOTE]
    >  Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.  
  
     Vous trouverez ci-dessous un exemple de fichier :  
  
    ```  
    <?xml version="1.0"?>  
    <SSO>  
      <application name="SSOApp_Host1">  
        <description>An Individual Type Affiliate Application for Host Initiated SSO</description>  
        <contact>someone@companyname.com</contact>  
        <appUserAccount>DomainName\AppUserGroup_HISSO</appUserAccount>  
        <appAdminAccount>DomainName\AppAdminGroup_HISSO</appAdminAccount>  
        <field ordinal="0" label="User ID" masked="no" />  
        <field ordinal="1" label="Password" masked="yes" />  
        <flags windowsInitiatedSSO="no" enableApp="yes" />  
      </application>  
    </SSO>  
  
    ```  
  
### <a name="to-create-a-host-group-type-affiliate-application-using-the-command-line"></a>Pour créer une application associée de type groupe d'hôtes à l'aide d'une ligne de commande  
  
1.  Dans le menu **Démarrer** , cliquez sur **Exécuter**.  
  
2.  Dans le **exécuter** boîte de dialogue, tapez **cmd**, puis cliquez sur **OK**.  
  
3.  Dans la ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise. La valeur par défaut est \<lecteur\>: \Program Files\Enterprise Single Sign-On.  
  
4.  Type **ssomanage – createapps \<AffApp.xml\>**, où AffApp.xml est le nom du fichier xml.  
  
    > [!NOTE]
    >  Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.  
  
     Vous trouverez ci-dessous un exemple de fichier :  
  
    ```  
    <?xml version="1.0"?>  
    <SSO>  
      <application name="SSOApp_HostGroupApp1">  
        <description>A Group Type Affiliate Application for Host Initiated SSO associating multiple non-Windows user to a single Windows user account(DomainName\WindowsUserAccount1)</description>  
        <contact>someone@companyname.com</contact>  
        <windowsAccount>DomainName\WindowsUserAccount1</windowsAccount>  
        <appAdminAccount>DomainName\AppAdminGroup_HISSO</appAdminAccount>  
        <field ordinal="0" label="User ID" masked="no" />  
        <field ordinal="1" label="Password" masked="yes" />  
        <flags  enableApp="yes" />  
      </application>  
    </SSO>  
  
    ```  
  
### <a name="to-create-an-affiliate-application-supporting-both-windows-initiated-sso-and-host-initiated-sso-using-the-command-line"></a>Pour créer une application associée prenant en charge l'authentification unique initiée par Windows et l'authentification unique initiée par l'hôte à l'aide d'une ligne de commande  
  
1.  Dans le menu **Démarrer** , cliquez sur **Exécuter**.  
  
2.  Dans le **exécuter** boîte de dialogue, tapez **cmd**, puis cliquez sur **OK**.  
  
3.  Dans la ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise. La valeur par défaut est \<lecteur\>: \Program Files\Enterprise Single Sign-On.  
  
4.  Type **ssomanage – createapps \<AffApp.xml\>**, où AffApp.xml est le nom du fichier xml.  
  
    > [!NOTE]
    >  Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.  
  
     Vous trouverez ci-dessous un exemple de fichier :  
  
    ```  
    <?xml version="1.0" ?>   
    - <SSO>  
    - <application name="SSOApp1">  
      <description>An Individual Type Affiliate Application for both Host Initiated SSO and Windows Initiated SSO</description>   
      <contact>someone@companyname.com</contact>   
      <appUserAccount>DomainName\AppUserGroup</appUserAccount>   
      <appAdminAccount>DomainName\AppAdminGroup</appAdminAccount>   
      <field ordinal="0" label="User ID" masked="no" />   
      <field ordinal="1" label="Password" masked="yes" />   
      <flags  enableApp="yes" />   
      </application>  
      </SSO>  
  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [Authentification unique initiée par l’hôte](../core/host-initiated-sso.md)