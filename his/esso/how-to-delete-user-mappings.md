---
title: Comment supprimer des mappages utilisateur | Documents Microsoft
ms.custom: ''
ms.date: 11/30/2017
ms.prod: host-integration-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 82c4cdff-b82d-4cfd-8e20-220a2fe78656
caps.latest.revision: ''
author: gplarsen
ms.author: hisdocs; plarsen
manager: anneta
ms.openlocfilehash: a9d0a31c3dbc9d5980f59d9f30d20ec15f603a38
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/28/2018
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
  
 Si un utilisateur n’est pas membre du compte utilisateurs d’applications, ou il n’existe pas dans Active Directory, vous devez utiliser cette commande pour supprimer le mappage utilisateur à partir de la base de données d’informations d’identification.  
  
 Si un compte d'utilisateur est modifié, vous devez utiliser cette commande pour supprimer les anciens mappages utilisateur, puis créer un mappage utilisateur pour le nouveau compte d'utilisateur. Pour plus d’informations sur la création d’un mappage, consultez [comment créer des mappages utilisateur](../esso/how-to-create-user-mappings.md).  
  
### <a name="to-delete-user-mappings-using-the-administration-utility"></a>Pour supprimer des mappages utilisateur à l'aide de l'utilitaire d'administration  
  
1.  Cliquez sur **Démarrer**, cliquez sur **exécuter**, type `cmd`, puis appuyez sur ENTRÉE.  
  
2.  À l’invite de commandes, accédez au répertoire d’installation Enterprise Single Sign-On.  
  
     Le répertoire d’installation par défaut est \< *lecteur*> : \Program Files\Enterprise Single Sign-On.  
  
3.  Type `ssomanage –deletemappings <mappings file name>`, où \< *nom de fichier de mappage*> est le nom du fichier qui contient les mappages utilisateur que vous souhaitez supprimer.  
  
### <a name="to-delete-a-specific-user-mapping-using-the-administration-utility"></a>Pour supprimer un mappage utilisateur spécifique à l'aide de l'utilitaire d'administration  
  
1.  Cliquez sur **Démarrer**, cliquez sur **exécuter**, type `cmd`, puis appuyez sur ENTRÉE.  
  
2.  À l’invite de commandes, accédez au répertoire d’installation Enterprise Single Sign-On.  
  
     Le répertoire d’installation par défaut est  *\<lecteur >*: \Program Files\Enterprise Single Sign-On.  
  
3.  Type `ssomanage –deletemapping <domain>\<username> <application name>`, où  *\<domaine >* correspond au domaine Windows pour le compte d’utilisateur,  *\<nom d’utilisateur >* est le nom d’utilisateur Windows et \< *nom de l’application*> est l’application spécifique pour lequel vous souhaitez supprimer le mappage utilisateur.  
  
### <a name="to-delete-a-user-mapping-using-the-client-utility"></a>Pour supprimer un mappage utilisateur à l'aide de l'utilitaire client  
  
1.  Cliquez sur **Démarrer**, cliquez sur **exécuter**, type `cmd`, puis appuyez sur ENTRÉE.  
  
2.  À l’invite de commandes, accédez au répertoire d’installation Enterprise Single Sign-On.  
  
     Le répertoire d’installation par défaut est  *\<lecteur >*: \Program Files\Enterprise Single Sign-On.  
  
3.  Type `ssoclient –deletemapping <application name>`, où  *\<nom de l’application >* est le nom de l’application associée pour laquelle vous souhaitez supprimer le mappage utilisateur.  
  
## <a name="see-also"></a>Voir aussi  
 [Mappages SSO](../esso/sso-mappings.md)   
 [Gestion des Applications associées](../esso/managing-affiliate-applications.md)   
 [Gestion des mappages utilisateur](../esso/managing-user-mappings.md)