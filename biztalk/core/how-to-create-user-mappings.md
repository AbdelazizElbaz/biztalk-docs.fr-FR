---
title: "Comment créer des mappages utilisateur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- maps [SSO], creating
- managing [SSO maps], creating user maps
ms.assetid: c2e9f0db-920b-4d89-8e1e-5dc92805fd23
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5ffbcc0cb5ca00eb0b461f77c36397179f5c91f7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-create-user-mappings"></a>Comment créer des mappages utilisateur
Cette commande permet de créer un ou plusieurs mappages utilisateur, comme décrit dans le fichier XML. Voici un exemple de fichier XML.  
  
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
  
 Si un compte d'utilisateur est modifié, vous devez utiliser cette commande pour créer un mappage pour le nouveau compte d'utilisateur. Vous devez également supprimer l'ancien mappage utilisateur. Pour plus d’informations sur la suppression d’un mappage, consultez [comment supprimer des mappages utilisateur](../core/how-to-delete-user-mappings.md).  
  
 Après avoir créé un mappage utilisateur, vous devez l'activer avant de pouvoir l'utiliser dans le système d'authentification unique. Pour plus d’informations, consultez [comment activer un mappage utilisateur](../core/how-to-enable-a-user-mapping.md).  
  
> [!IMPORTANT]
>  Seuls les groupes de domaine sont pris en charge avec les mappages utilisateur.  
  
### <a name="to-create-user-mappings-using-the-administration-utility"></a>Pour créer des mappages utilisateur à l'aide de l'utilitaire d'administration  
  
1.  Sur le **Démarrer** menu, cliquez sur **exécuter**, puis tapez **cmd**.  
  
2.  Dans la ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise. Le répertoire d’installation par défaut est \< *lecteur*> : \Program Files\Enterprise Single Sign-On.  
  
3.  Type **ssomanage – createmappings  *\<nom de fichier de mappage >***, où  *\<nom de fichier de mappage >* est le nom du fichier qui contient le ou les utilisateurs mappages que vous souhaitez créer.  
  
    > [!NOTE]
    >  Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.  
  
### <a name="to-create-user-mappings-using-the-client-utility"></a>Pour créer des mappages utilisateur à l'aide de l'utilitaire client  
  
1.  Sur le **Démarrer** menu, cliquez sur **exécuter**, puis tapez **cmd**.  
  
2.  Dans la ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise. Le répertoire d’installation par défaut est \< *lecteur*> : \Program Files\Enterprise Single Sign-On.  
  
3.  Type **ssoclient – setcredentials  *\<nom de l’application >***, où  *\<nom de l’application >* est le nom de l’application associée que l’utilisateur souhaite créer un mappage pour.  
  
    > [!NOTE]
    >  Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.  
  
## <a name="see-also"></a>Voir aussi  
 [Mappages SSO](../core/sso-mappings.md)   
 [Gestion des Applications associées](../core/managing-affiliate-applications.md)   
 [Gestion des mappages utilisateur](../core/managing-user-mappings.md)