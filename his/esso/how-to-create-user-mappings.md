---
title: Comment créer des mappages utilisateur | Documents Microsoft
ms.custom: ''
ms.date: 11/30/2017
ms.prod: host-integration-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eb91879c-73f4-4e9e-9e5b-534f48cd5584
caps.latest.revision: ''
author: gplarsen
ms.author: hisdocs; plarsen
manager: anneta
ms.openlocfilehash: 89fd7ab2ca83d23a37944447997becd2d3f008c2
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/28/2018
---
# <a name="how-to-create-user-mappings"></a>Comment créer des mappages utilisateur
Utilisez le **createmappings** commande pour créer un ou plusieurs mappages utilisateur, tel que spécifié dans le fichier XML. Voici un exemple de fichier XML.  
  
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
  
 Si un compte d'utilisateur est modifié, vous devez utiliser cette commande pour créer un mappage pour le nouveau compte d'utilisateur. Vous devez également supprimer l'ancien mappage utilisateur. Pour plus d’informations sur la suppression d’un mappage, consultez [comment supprimer des mappages utilisateur](../esso/how-to-delete-user-mappings.md).  
  
 Après avoir créé un mappage utilisateur, vous devez l’activer avant de pouvoir utiliser ce mappage dans le système Single Sign-On (SSO). Pour plus d’informations, consultez [comment activer un mappage utilisateur](../esso/how-to-enable-a-user-mapping.md).  
  
> [!IMPORTANT]
>  Seuls les groupes de domaine sont pris en charge avec les mappages utilisateur.  
  
### <a name="to-create-user-mappings-using-the-administration-utility"></a>Pour créer des mappages utilisateur à l'aide de l'utilitaire d'administration  
  
1.  Cliquez sur **Démarrer**, cliquez sur **exécuter**, type `cmd`, puis appuyez sur ENTRÉE.  
  
2.  À l’invite de commandes, accédez au répertoire d’installation Enterprise Single Sign-On.  
  
     Le répertoire d’installation par défaut est \< *lecteur*> : \Program Files\Enterprise Single Sign-On.  
  
3.  Type `ssomanage –createmappings <mappings file name>`, où  *\<nom de fichier de mappage >* est le nom du fichier qui contient les mappages utilisateur que vous souhaitez créer.  
  
### <a name="to-create-user-mappings-using-the-client-utility"></a>Pour créer des mappages utilisateur à l'aide de l'utilitaire client  
  
1.  Cliquez sur **Démarrer**, cliquez sur **exécuter**, type `cmd`, puis appuyez sur ENTRÉE.  
  
2.  À l’invite de commandes, accédez au répertoire d’installation Enterprise Single Sign-On.  
  
     Le répertoire d’installation par défaut est \< *lecteur*> : \Program Files\Enterprise Single Sign-On.  
  
3.  Type `ssoclient –setcredentials <application name >`, où  *\<nom de l’application >* est le nom de l’application associée que l’utilisateur souhaite créer un mappage pour.  
  
## <a name="see-also"></a>Voir aussi  
 [Mappages SSO](../esso/sso-mappings.md)   
 [Gestion des Applications associées](../esso/managing-affiliate-applications.md)   
 [Gestion des mappages utilisateur](../esso/managing-user-mappings.md)