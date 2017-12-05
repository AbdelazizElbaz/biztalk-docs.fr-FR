---
title: "Comment créer une Application associée | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing [SSO applications], creating
- applications [SSO], creating
- creating, applications [SSO]
ms.assetid: d0967c4b-6201-416a-9d3a-23b5de5b83d6
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d2f621faef7694a3dba7885bab5641e0baa58e8f
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-create-an-affiliate-application"></a>Comment créer une Application associée
Le composant logiciel enfichable MMC ou cette commande permet de créer une ou plusieurs applications, comme spécifié dans le fichier XML. Voici un exemple de fichier XML pour l'authentification unique initiée par Windows :  
  
```  
<sso>  
<application name="SAP">  
<description>The SAP application</description>   
<contact>someone@example.com</contact>   
<appuserAccount>domain\AppUserAccount</appuserAccount>   
<appAdminAccount>domain\AppAdminAccount</appAdminAccount>   
<field ordinal="0" label="User Id" masked="no" />   
<field ordinal="1" label="Password" masked="yes" />   
<flags groupApp="no" configStoreApp="no" allowTickets="no" validateTickets="yes" allowLocalAccounts="no" timeoutTickets="yes" adminAccountSame="no" enableApp="no" />  
</application>  
</sso>  
  
```  
  
 Après avoir créé une application associée, il est impossible de modifier les propriétés suivantes :  
  
-   Nom de l’application associée  
  
-   Champs liés à l'application associée  
  
-   Type de l'application associée (groupe d'hôtes, individuelle ou magasin de configuration)  
  
-   Compte d'administration identique au groupe des administrateurs d'applications associées (si vous spécifiez cet indicateur, le groupe Administrateurs associés sera toujours utilisé comme compte d'administrateurs pour cette application associée)  
  
> [!IMPORTANT]
>  Vous pouvez utiliser les comptes locaux pour le compte d'administration et le compte d'utilisateur en définissant l'indicateur allowLocalAccounts sur Oui. Vous devez toutefois sélectionner cet indicateur uniquement dans des scénarios impliquant un seul ordinateur.  
  
> [!IMPORTANT]
>  Pour effectuer cette tâche, vous devez être un administrateur SSO ou un administrateur d'applications associées à SSO.  
  
 Après avoir créé l'application associée, vous devez l'activer. Pour plus d’informations, consultez [comment activer une Application associée](../core/how-to-enable-an-affiliate-application.md).  
  
### <a name="to-create-an-affiliate-application-using-the-mmc-snap-in"></a>Pour créer une application associée à l'aide du composant logiciel enfichable MMC  
  
1.  Sur le **Démarrer** menu, cliquez sur **programmes**, cliquez sur **Microsoft Enterprise Single Sign-On**, puis cliquez sur **Administration SSO**.  
  
2.  Dans le volet d'étendue du composant logiciel enfichable MMC ENTSSO, développez le nœud **Authentification unique de l'entreprise** .  
  
3.  Avec le bouton droit **Applications associées**, puis cliquez sur **créer une Application**.  
  
4.  Suivez les instructions de la **unique Sign-On Assistant Application d’entreprise**.  
  
### <a name="to-create-an-affiliate-application-using-the-command-line"></a>Pour créer une application associée à l'aide de la ligne de commande  
  
1.  Sur le **Démarrer** menu, cliquez sur **exécuter**, puis tapez **cmd**.  
  
2.  Dans la ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise. Le répertoire d’installation par défaut est  *\<lecteur\>*: \Program Files\Enterprise Single Sign-On.  
  
3.  Type **ssomanage – createapps  *\<nom de fichier d’application\>***, où  *\<nom de fichier d’application\>*  est le fichier XML.  
  
    > [!NOTE]
    >  Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.  
  
## <a name="see-also"></a>Voir aussi  
 [Applications associées SSO](../core/sso-affiliate-applications.md)   
 [Comment activer une Application associée](../core/how-to-enable-an-affiliate-application.md)   
 [Comment supprimer une Application associée](../core/how-to-delete-an-affiliate-application.md)   
 [Gestion des mappages utilisateur](../core/managing-user-mappings.md)   
 [Gestion des applications associées](../core/managing-affiliate-applications.md)