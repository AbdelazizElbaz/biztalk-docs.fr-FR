---
title: "Comment connecter un utilisateur Local à une Application non-Windows | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b55957f4-22c4-48b5-827a-ab41d8f846ac
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c3c2e9ffaede20e29987938a436ad2a091920fce
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-log-a-local-user-on-to-a-non-windows-application"></a><span data-ttu-id="305a0-102">Procédure : se connecter un utilisateur Local à une Application non-Windows</span><span class="sxs-lookup"><span data-stu-id="305a0-102">How to Log a Local User on to a Non-Windows Application</span></span>
<span data-ttu-id="305a0-103">Après avoir configuré votre utilisateur avec une application associée, vous pouvez utiliser l'authentification unique (SSO) pour accéder au nom et aux informations d'identification d'utilisateur externe de l'utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="305a0-103">After you set up your user with an affiliate application, you can use Single Sign-On (SSO) to access the external user name and credentials of the current user.</span></span> <span data-ttu-id="305a0-104">À l'aide de ces informations d'identification, vous pouvez ouvrir une session pour votre utilisateur sur l'application associée qui s'exécute sur un serveur hôte.</span><span class="sxs-lookup"><span data-stu-id="305a0-104">Using these credentials, you can then log your user on to the affiliate application that is running on a host server.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="305a0-105">Outre la définition des protocoles de sécurité appropriés pour SSO, il peut également s'avérer nécessaire de définir des mesures de sécurité supplémentaires afin de permettre à votre application d'appeler SSO dans le contexte de sécurité correct.</span><span class="sxs-lookup"><span data-stu-id="305a0-105">In addition to setting the appropriate security protocols for SSO, you might also need to set additional security to allow your application to call SSO in the correct security context.</span></span> <span data-ttu-id="305a0-106">Si votre application ne parvient pas à appeler SSO dans le contexte de sécurité correct, SSO lui refusera l'accès.</span><span class="sxs-lookup"><span data-stu-id="305a0-106">If your application cannot call SSO in the correct security context, SSO will deny access to your application.</span></span>  
  
### <a name="to-set-the-security-context-for-an-sso-application"></a><span data-ttu-id="305a0-107">Pour définir le contexte de sécurité pour une application SSO</span><span class="sxs-lookup"><span data-stu-id="305a0-107">To set the security context for an SSO application</span></span>  
  
1.  <span data-ttu-id="305a0-108">Identifiez les informations d'identification nécessaires pour que votre application s'exécute correctement.</span><span class="sxs-lookup"><span data-stu-id="305a0-108">Identify what credentials your application needs to run successfully.</span></span>  
  
     <span data-ttu-id="305a0-109">Par exemple, une application utilisant des services Web ou .NET Framework hébergé à distance dans IIS doit emprunter l'identité du client pour transmettre les informations d'identification appropriées à SSO.</span><span class="sxs-lookup"><span data-stu-id="305a0-109">For example, an application that uses Web services or .NET Framework remoting hosted in IIS needs to impersonate the client in order to pass the appropriate credentials on to SSO.</span></span>  
  
2.  <span data-ttu-id="305a0-110">Confirmez que les paramètres de sécurité appropriés, tels que ceux des répertoires virtuels, pools d'applications et fichiers web.config, sont définis pour fournir ces informations d'identification à votre application.</span><span class="sxs-lookup"><span data-stu-id="305a0-110">Confirm that the relevant security settings, such as those on virtual directories, application pools, and web.config files, are set to provide your application with those credentials.</span></span>  
  
     <span data-ttu-id="305a0-111">Pour plus d’informations sur la façon de définir les informations d’identification de sécurité, consultez [création d’Applications ASP.NET sécurisées : authentification, autorisation et Communication sécurisée](http://go.microsoft.com/fwlink/?LinkId=193906).</span><span class="sxs-lookup"><span data-stu-id="305a0-111">For more information about how to set security credentials, see [Building Secure ASP.NET Applications: Authentication, Authorization, and Secure Communication](http://go.microsoft.com/fwlink/?LinkId=193906).</span></span>  
  
     <span data-ttu-id="305a0-112">Pour plus d’informations sur les informations d’identification de passage d’un service Web ASP.NET, consultez [Comment : passer des informations actuelles d’identification à un Service Web ASP.NET](http://go.microsoft.com/fwlink/?LinkId=193907).</span><span class="sxs-lookup"><span data-stu-id="305a0-112">For more information about passing credentials for an ASP.NET Web service, see [HOW TO: Pass Current Credentials to an ASP.NET Web Service](http://go.microsoft.com/fwlink/?LinkId=193907).</span></span>  
  
### <a name="to-log-a-local-user-on-to-a-host-application"></a><span data-ttu-id="305a0-113">Pour ouvrir une session pour un utilisateur local sur une application hôte</span><span class="sxs-lookup"><span data-stu-id="305a0-113">To log a local user on to a host application</span></span>  
  
1.  <span data-ttu-id="305a0-114">Recevez la requête d'ouverture de session pour l'utilisateur actuel sur une application exécutée sur le serveur hôte.</span><span class="sxs-lookup"><span data-stu-id="305a0-114">Receive the request to log the current user on to an application running on the host server.</span></span>  
  
     <span data-ttu-id="305a0-115">Il vous incombe de déterminer comment l'utilisateur actuel requiert d'être connecté à une application hôte.</span><span class="sxs-lookup"><span data-stu-id="305a0-115">It is your responsibility to determine how the current user requests to be logged on to a host application.</span></span>  
  
2.  <span data-ttu-id="305a0-116">Récupérez les informations d'identification de l'utilisateur actuel à l'aide de `ISSOLookup1.GetCredentials` ou `ISSOLookup2.GetCredentials`.</span><span class="sxs-lookup"><span data-stu-id="305a0-116">Retrieve the credentials for the current user who is using `ISSOLookup1.GetCredentials` or `ISSOLookup2.GetCredentials`.</span></span>  
  
     <span data-ttu-id="305a0-117">Vous devez fournir le nom de l’application hôte ainsi que tous les indicateurs nécessaires.</span><span class="sxs-lookup"><span data-stu-id="305a0-117">You must supply the name of the host application together with any relevant flags.</span></span> <span data-ttu-id="305a0-118">`GetCredentials`Retourne le nom d’utilisateur associé et les informations d’identification pour l’application hôte.</span><span class="sxs-lookup"><span data-stu-id="305a0-118">`GetCredentials` returns the associated user name and credentials for the host application.</span></span>  
  
     <span data-ttu-id="305a0-119">Notez que vous pouvez aussi bien utiliser `ISSOLookup1` que `ISSOLookup2`.</span><span class="sxs-lookup"><span data-stu-id="305a0-119">Note that you can use either `ISSOLookup1` or `ISSOLookup2`.</span></span> <span data-ttu-id="305a0-120">La seule différence est que `ISSOLookup2` dispose également d'une méthode d'ouverture de session pour un utilisateur distant sur une application Windows locale.</span><span class="sxs-lookup"><span data-stu-id="305a0-120">The only difference is that `ISSOLookup2` also has a method for logging a remote user on to a local windows application.</span></span>  
  
3.  <span data-ttu-id="305a0-121">Utilisez les nom et informations d'identification d'utilisateur externe pour l'ouverture de session sur l'application hôte.</span><span class="sxs-lookup"><span data-stu-id="305a0-121">Use the external user name and credentials to log on to the host application.</span></span>  
  
     <span data-ttu-id="305a0-122">Il vous incombe de déterminer comment utiliser les informations d'identification pour l'ouverture de session sur l'application hôte.</span><span class="sxs-lookup"><span data-stu-id="305a0-122">It is your responsibility to determine how to use the credentials to log on to the host application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="305a0-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="305a0-123">See Also</span></span>  
 [<span data-ttu-id="305a0-124">Procédure : se connecter un utilisateur distant sur une Application locale</span><span class="sxs-lookup"><span data-stu-id="305a0-124">How to Log a Remote User on to a Local Application</span></span>](../core/how-to-log-a-remote-user-on-to-a-local-application.md)