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
# <a name="validating-passwords-for-host-initiated-sso"></a><span data-ttu-id="411d0-102">Authentification unique initiée par la validation des mots de passe pour l’hôte</span><span class="sxs-lookup"><span data-stu-id="411d0-102">Validating Passwords for Host Initiated SSO</span></span>
<span data-ttu-id="411d0-103">Lorsqu'une application associée pour l'authentification unique initiée par l'hôte est créée, la validation de mot de passe pour l'utilisateur non-Windows est activée par défaut.</span><span class="sxs-lookup"><span data-stu-id="411d0-103">When an affiliate application for host initiated SSO is created, password validation for the non-Windows user is enabled by default.</span></span> <span data-ttu-id="411d0-104">Cela signifie que lorsque les applications font appel à l'authentification unique pour obtenir le jeton d'utilisateur Windows pour accéder aux ressources, elles doivent fournir les compte d'utilisateur et mot de passe non-Windows.</span><span class="sxs-lookup"><span data-stu-id="411d0-104">This means when applications call SSO to obtain the Windows user token to access resources, they must provide the non-Windows user account and the non-Windows password.</span></span> <span data-ttu-id="411d0-105">Si le mot de passe ne correspond pas à celui dans la base de données SSO pour cet utilisateur non-Windows, l'accès est refusé.</span><span class="sxs-lookup"><span data-stu-id="411d0-105">If the password does not match the password in the SSO database for that non-Windows user, access is denied.</span></span> <span data-ttu-id="411d0-106">Le cas échéant, la fonctionnalité de validation de mot de passe peut être désactivée pour l'application associée.</span><span class="sxs-lookup"><span data-stu-id="411d0-106">If necessary, the password validation feature can be disabled for the affiliate application.</span></span> <span data-ttu-id="411d0-107">La fonctionnalité de validation de mot de passe s'applique aux applications associées de type individuel et groupe d'hôtes pour l'authentification unique initiée par un hôte.</span><span class="sxs-lookup"><span data-stu-id="411d0-107">The password validation feature applies to both individual and host group type affiliate applications for host initiated SSO.</span></span>  
  
 <span data-ttu-id="411d0-108">Voici un exemple de fichier XML pour une application associé à authentification unique initiée par un hôte de type individuel :</span><span class="sxs-lookup"><span data-stu-id="411d0-108">An example XML file for Individual type host initiated SSO affiliate application is:</span></span>  
  
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
  
 <span data-ttu-id="411d0-109">Dans le cas des applications individuelles pour l'authentification unique initiée par un hôte, le compte d'utilisateur de l'application (appUserAccount) est un compte de groupe contenant la liste des utilisateurs de compte de domaine Windows associés à un mappage 1 à 1 avec leurs comptes non-Windows correspondants.</span><span class="sxs-lookup"><span data-stu-id="411d0-109">In the case of individual applications for host initiated SSO, the appUserAccount is a group account that contains the list of Windows domain account users that have a 1 to 1 mapping with their corresponding non-Windows accounts.</span></span>  
  
 <span data-ttu-id="411d0-110">Voici un exemple de fichier XML pour l'application associée à authentification unique initiée par un hôte de type groupe d'hôtes :</span><span class="sxs-lookup"><span data-stu-id="411d0-110">An example XML file for host group type host initiated SSO affiliate application is:</span></span>  
  
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
  
 <span data-ttu-id="411d0-111">Dans les applications de groupe pour l'authentification unique initiée par un hôte, le compte d'utilisateur de l'application (appUserAccount) doit être un compte d'utilisateur individuel.</span><span class="sxs-lookup"><span data-stu-id="411d0-111">In group applications for host initiated SSO, the appUserAccount must be an individual user account.</span></span> <span data-ttu-id="411d0-112">Il s'agit du compte auquel tous les comptes non-Windows sont mappés.</span><span class="sxs-lookup"><span data-stu-id="411d0-112">It is this account that all non-Windows accounts are mapped to.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="411d0-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="411d0-113">See Also</span></span>  
 [<span data-ttu-id="411d0-114">L’authentification unique initiée par l’hôte</span><span class="sxs-lookup"><span data-stu-id="411d0-114">Host Initiated SSO</span></span>](../core/host-initiated-sso.md)