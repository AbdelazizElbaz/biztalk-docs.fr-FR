---
title: Comment supprimer des mappages utilisateur | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- maps [SSO], deleting
- managing [SSO maps], deleting user maps
ms.assetid: de511113-b0b0-4920-91dc-4c9e380fda58
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0a4c8cb8766080a715ba309f2aa2736957b6ff54
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-delete-user-mappings"></a>Comment supprimer des mappages utilisateur
Ces commandes permettent de supprimer un ou plusieurs mappages utilisateur, comme décrit dans le fichier XML. Voici un exemple de fichier XML.  
  
```  
<sso>  
<mapping>  
<windowsDomain>domain</windowsDomain>   
<windowsUserId>WindowsUserName</windowsUserId>   
<externalApplication>Application name1</externalApplication>   
<externalUserId>App1UserName</externalUserId>   
</mapping>  
<mapping>  
<windowsDomain>domain</windowsDomain>   
<windowsUserId>WindowsUserName</windowsUserId>   
<externalApplication>Application name2</externalApplication>   
<externalUserId>App2UserName</externalUserId>   
</mapping>  
</sso>  
```  
  
 Si un utilisateur n'est pas membre du compte Utilisateurs d'applications ou n'existe pas dans Active Directory, vous devez utiliser cette commande pour supprimer le mappage utilisateur de la base de données SSO.  
  
 Si un compte d'utilisateur est modifié, vous devez utiliser cette commande pour supprimer les anciens mappages utilisateur, puis créer un mappage utilisateur pour le nouveau compte d'utilisateur. Pour plus d’informations sur la création d’un mappage, consultez [comment créer des mappages utilisateur](../core/how-to-create-user-mappings.md).  
  
### <a name="to-delete-user-mappings-using-the-administration-utility"></a>Pour supprimer des mappages utilisateur à l'aide de l'utilitaire d'administration  
  
1.  Sur le **Démarrer** menu, cliquez sur **exécuter**, puis tapez **cmd**.  
  
2.  Dans la ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise. Le répertoire d’installation par défaut est \< *lecteur*> : \Program Files\Enterprise Single Sign-On.  
  
3.  Type **ssomanage – deletemappings  *\<nom de fichier de mappage >***, où \< *nom de fichier de mappage*> est le nom du fichier qui contienne l’utilisateur ou les mappages que vous souhaitez supprimer.  
  
    > [!NOTE]
    >  Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.  
  
### <a name="to-delete-a-specific-user-mapping-using-the-administration-utility"></a>Pour supprimer un mappage utilisateur spécifique à l'aide de l'utilitaire d'administration  
  
1.  Sur le **Démarrer** menu, cliquez sur **exécuter**, puis tapez **cmd**.  
  
2.  Dans la ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise. Le répertoire d’installation par défaut est  *\<lecteur*> : \Program Files\Enterprise Single Sign-On.  
  
3.  Type  **ssomanage-deletemapping  *\<domaine >*\\*\<nom d’utilisateur >*  *\< nom de l’application >***, où  *\<domaine >* correspond au domaine Windows pour le compte d’utilisateur,  *\<nom d’utilisateur >* est le nom d’utilisateur Windows et \<* nom de l’application*> est l’application spécifique pour lequel vous souhaitez supprimer le mappage utilisateur.  
  
    > [!NOTE]
    >  Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.  
  
### <a name="to-delete-a-user-mapping-using-the-client-utility"></a>Pour supprimer un mappage utilisateur à l'aide de l'utilitaire client  
  
1.  Sur le **Démarrer** menu, cliquez sur **exécuter**, puis tapez **cmd**.  
  
2.  Dans la ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise. Le répertoire d’installation par défaut est  *\<lecteur*> : \Program Files\Enterprise Single Sign-On.  
  
3.  Type **ssoclient – deletemapping  *\<nom de l’application >***, où  *\<nom de l’application >* est le nom de la filiale vous souhaitez supprimer le mappage de l’application.  
  
    > [!NOTE]
    >  Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.  
  
## <a name="see-also"></a>Voir aussi  
 [Mappages SSO](../core/sso-mappings.md)   
 [Gestion des Applications associées](../core/managing-affiliate-applications.md)   
 [Gestion des mappages utilisateur](../core/managing-user-mappings.md)