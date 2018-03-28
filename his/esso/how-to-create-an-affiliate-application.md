---
title: Comment créer une Application associée | Documents Microsoft
ms.custom: ''
ms.date: 11/30/2017
ms.prod: host-integration-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3be483f8-2617-459e-9081-aab886c75d93
caps.latest.revision: ''
author: gplarsen
ms.author: hisdocs; plarsen
manager: anneta
ms.openlocfilehash: 5145111b2c585edab92cc10c3e3614e8bb91a85d
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/28/2018
---
# <a name="how-to-create-an-affiliate-application"></a>Comment créer une Application associée
Vous pouvez utiliser le composant logiciel enfichable MMC ou la **createapps** commande pour créer une ou plusieurs applications, comme spécifié par le fichier XML. Voici un exemple de fichier XML pour Windows-Initiated Single Sign-On (SSO) :  
  
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
  
-   Nom de l'application associée.  
  
-   Champs associés à l’application associée.  
  
-   Applications associées à type d’application (magasin individuel, groupe ou la configuration d’hôte).  
  
-   Compte d'administration identique au groupe des administrateurs d'applications associées (Définition de cet indicateur utilisent toujours le groupe Administrateurs associés en tant que le compte d’administrateur pour cette application associée.)  
  
> [!IMPORTANT]
>  Vous pouvez utiliser les comptes locaux pour le compte d'administration et le compte d'utilisateur en définissant l'indicateur allowLocalAccounts sur Oui. Vous devez toutefois sélectionner cet indicateur uniquement dans des scénarios impliquant un seul ordinateur.  
  
> [!IMPORTANT]
>  Pour effectuer cette tâche, vous devez être un administrateur SSO ou un administrateur d'applications associées à SSO.  
  
> [!NOTE]
>  Si vous effectuez la configuration sur un contrôleur de domaine et les groupes locaux de domaine de la portée sont spécifiées pour les administrateurs d’applications ou utilisateurs de l’Application lors de la création d’Applications associées, il est recommandé d’activer l’indicateur de compte local. Pour effectuer cette opération :  
  
-   Dans le composant logiciel enfichable MMC, sélectionnez Autoriser les comptes locaux pour les comptes d’accès pendant le processus de création.  
  
-   À partir de la ligne de commande, spécifiez allowLocalAccounts = yes dans le fichier XML pour la création d’applications associées à l’Application.  
  
 Après avoir créé l'application associée, vous devez l'activer. Pour plus d’informations, consultez [comment activer une Application associée](../esso/how-to-enable-an-affiliate-application.md).  
  
### <a name="to-create-an-affiliate-application-using-the-microsoft-management-console-mmc-snap-in"></a>Pour créer une application associée à l’aide du composant logiciel enfichable Microsoft Management Console (MMC)  
  
1.  Cliquez sur **Démarrer**, pointez sur **programmes**, cliquez sur **Microsoft Enterprise Single Sign-On**, puis cliquez sur **Administration SSO**.  
  
2.  Dans le volet d'étendue du composant logiciel enfichable MMC ENTSSO, développez le nœud **Authentification unique de l'entreprise** .  
  
3.  Avec le bouton droit **Applications associées**, puis cliquez sur **nouveau**.  
  
4.  Suivez les instructions de la **créer une nouvelle Application associée** Assistant.  
  
### <a name="to-create-an-affiliate-application-using-the-command-line"></a>Pour créer une application associée à l'aide de la ligne de commande  
  
1.  Cliquez sur **Démarrer**, cliquez sur **exécuter**, type `cmd`, puis appuyez sur ENTRÉE.  
  
2.  À l’invite de commandes, accédez au répertoire d’installation Enterprise Single Sign-On.  
  
     Le répertoire d’installation par défaut est  *\<lecteur >*: \Program Files\Enterprise Single Sign-On.  
  
3.  Type `ssomanage –createapps <application file name>`, où  *\<nom de fichier d’application >* est le fichier XML.  
  
## <a name="see-also"></a>Voir aussi  
 [Applications associées SSO](../esso/sso-affiliate-applications.md)   
 [Comment activer une Application associée](../esso/how-to-enable-an-affiliate-application.md)   
 [Comment supprimer une Application associée](../esso/how-to-delete-an-affiliate-application.md)   
 [Gestion des mappages utilisateur](../esso/managing-user-mappings.md)   
 [Gestion des applications associées](../esso/managing-affiliate-applications.md)