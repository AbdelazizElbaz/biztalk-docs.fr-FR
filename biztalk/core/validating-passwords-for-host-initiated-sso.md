---
title: "Validation des mots de passe pour l’hôte, authentification unique initiée par | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- passwords, host initiated [SSO]
- host initiated SSO, passwords
ms.assetid: 3cc1d68a-27ac-46ce-ba1e-21139a9df55e
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 03a33eb83630831863f231ff9594e3082f0faa98
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="validating-passwords-for-host-initiated-sso"></a>Authentification unique initiée par la validation des mots de passe pour l’hôte
Lorsqu'une application associée pour l'authentification unique initiée par l'hôte est créée, la validation de mot de passe pour l'utilisateur non-Windows est activée par défaut. Cela signifie que lorsque les applications font appel à l'authentification unique pour obtenir le jeton d'utilisateur Windows pour accéder aux ressources, elles doivent fournir les compte d'utilisateur et mot de passe non-Windows. Si le mot de passe ne correspond pas à celui dans la base de données SSO pour cet utilisateur non-Windows, l'accès est refusé. Le cas échéant, la fonctionnalité de validation de mot de passe peut être désactivée pour l'application associée. La fonctionnalité de validation de mot de passe s'applique aux applications associées de type individuel et groupe d'hôtes pour l'authentification unique initiée par un hôte.  
  
 Voici un exemple de fichier XML pour une application associé à authentification unique initiée par un hôte de type individuel :  
  
```  
<sso>  
<application name="SAP">  
<description>The SAP application</description>   
<contact>someone@example.com</contact>   
<appuserAccount>domain\AppUserGroupAccount</appuserAccount>   
<appAdminAccount>domain\AppAdminGroupAccount</appAdminAccount>   
<field ordinal="0" label="User Id" masked="no" />   
<field ordinal="1" label="Password" masked="yes" />   
<flags groupApp="no"  configStoreApp="no" allowTickets="no" validateTickets="yes" allowLocalAccounts="no" timeoutTickets="yes" adminAccountSame="no" enableApp="no" />  
</application>  
</sso>  
  
```  
  
 Dans le cas des applications individuelles pour l'authentification unique initiée par un hôte, le compte d'utilisateur de l'application (appUserAccount) est un compte de groupe contenant la liste des utilisateurs de compte de domaine Windows associés à un mappage 1 à 1 avec leurs comptes non-Windows correspondants.  
  
 Voici un exemple de fichier XML pour l'application associée à authentification unique initiée par un hôte de type groupe d'hôtes :  
  
```  
<sso>  
<application name="SAP">  
<description>The SAP application</description>   
<contact>someone@example.com</contact>   
<appuserAccount>domain\AppUserAccount</appuserAccount>   
<appAdminAccount>domain\AppAdminGroupAccount</appAdminAccount>   
<field ordinal="0" label="User Id" masked="no" />   
<field ordinal="1" label="Password" masked="yes" />   
<flags  configStoreApp="no" allowTickets="no" validateTickets="yes" allowLocalAccounts="no" timeoutTickets="yes" adminAccountSame="no" enableApp="no" />  
</application>  
</sso>  
  
```  
  
 Dans les applications de groupe pour l'authentification unique initiée par un hôte, le compte d'utilisateur de l'application (appUserAccount) doit être un compte d'utilisateur individuel. Il s'agit du compte auquel tous les comptes non-Windows sont mappés.  
  
## <a name="see-also"></a>Voir aussi  
 [L’authentification unique initiée par l’hôte](../core/host-initiated-sso.md)