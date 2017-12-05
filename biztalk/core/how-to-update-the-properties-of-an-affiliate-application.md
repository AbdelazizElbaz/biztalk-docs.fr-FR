---
title: "Comment mettre à jour les propriétés d’une Application associée | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing [SSO applications], updating properties
- applications [SSO], properties
ms.assetid: b06eefdd-a5ca-4a32-93d7-72246e31a2e4
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0ef4a2fb99d423f7c7ccb08cec58c3c49928e1ed
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-update-the-properties-of-an-affiliate-application"></a>Comment mettre à jour les propriétés d’une Application associée
Le composant logiciel enfichable MMC ou cette commande permet de mettre à jour une ou plusieurs propriétés d'application, comme spécifié dans le fichier XML. Pour exécuter cette tâche, vous devez être Administrateur d'applications associées. Voici un exemple de fichier XML qui répertorie les champs que vous pouvez mettre à jour.  
  
```  
<SSO>  
<application name="SSOApplication">  
<description>An SSO Application</description>  
<contact>someone@companyname.com</contact>  
<appUserAccount>DomainName\AppUserGroup</appUserAccount>  
<appAdminAccount>DomainName\AppAdminGroup</appAdminAccount>  
<flags allowTickets="no" validateTickets="yes"  timeoutTickets="yes" enableApp="no" />  
</application>  
</SSO>  
  
```  
  
 Après avoir créé une application associée, il est impossible de modifier les propriétés suivantes :  
  
-   Nom de l’application associée  
  
-   Champs liés à l'application associée  
  
-   Type de l'application associée (groupe d'hôtes, individuelle ou magasin de configuration)  
  
-   Compte d'administration identique au groupe des administrateurs d'applications associées (si vous spécifiez cet indicateur, le groupe Administrateurs associés sera toujours utilisé comme compte d'administrateurs pour cette application associée)  
  
> [!IMPORTANT]
>  Vous pouvez utiliser les comptes locaux pour le compte d'administration et le compte d'utilisateur en définissant l'indicateur allowLocalAccounts sur Oui. Vous pouvez toutefois sélectionner cet indicateur uniquement dans des scénarios impliquant un seul ordinateur.  
  
> [!IMPORTANT]
>  Pour effectuer cette tâche, vous devez être un administrateur SSO, un administrateur d'applications associées à SSO ou un administrateur d'applications.  
  
> [!IMPORTANT]
>  Pour modifier les indicateurs de tickets (validateTickets et timeoutTickets), vous devez être administrateur SSO.  
  
> [!IMPORTANT]
>  Pour modifier le compte d'administration relatif à l'application, vous devez être administrateur de l'authentification unique ou administrateur d'applications associées à SSO.  
  
### <a name="to-update-the-properties-of-an-affiliate-application-using-the-mmc-snap-in"></a>Pour mettre à jour les propriétés d'une application associée à l'aide du composant logiciel enfichable MMC  
  
1.  Sur le **Démarrer** menu, cliquez sur **programmes**, cliquez sur **Microsoft Enterprise Single Sign-On**, puis cliquez sur **Administration SSO**.  
  
2.  Dans le volet d'étendue du composant logiciel enfichable MMC ENTSSO, développez le nœud **Authentification unique de l'entreprise** .  
  
3.  Cliquez sur l’application associée, puis cliquez sur **mise à jour**.  
  
### <a name="to-update-the-properties-of-an-affiliate-application-using-the-command-line"></a>Pour mettre à jour les propriétés d'une application associée à l'aide de la ligne de commande  
  
1.  Sur le **Démarrer** menu, cliquez sur **exécuter**, puis tapez **cmd**.  
  
2.  Dans la ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise. Le répertoire d’installation par défaut est  **\<lecteur\>**: \Program Files\Enterprise Single Sign-On.  
  
3.  Type **ssomanage – updateapps \<nom de fichier d’application\>**, où le nom de fichier d’application est le fichier XML.  
  
    > [!NOTE]
    >  Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.  
  
## <a name="see-also"></a>Voir aussi  
 [Applications associées SSO](../core/sso-affiliate-applications.md)   
 [Comment activer une Application associée](../core/how-to-enable-an-affiliate-application.md)   
 [Gestion des mappages utilisateur](../core/managing-user-mappings.md)   
 [Gestion des applications associées](../core/managing-affiliate-applications.md)