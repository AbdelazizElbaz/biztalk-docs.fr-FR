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
# <a name="how-to-log-a-local-user-on-to-a-non-windows-application"></a>Procédure : se connecter un utilisateur Local à une Application non-Windows
Après avoir configuré votre utilisateur avec une application associée, vous pouvez utiliser l'authentification unique (SSO) pour accéder au nom et aux informations d'identification d'utilisateur externe de l'utilisateur actuel. À l'aide de ces informations d'identification, vous pouvez ouvrir une session pour votre utilisateur sur l'application associée qui s'exécute sur un serveur hôte.  
  
> [!NOTE]
>  Outre la définition des protocoles de sécurité appropriés pour SSO, il peut également s'avérer nécessaire de définir des mesures de sécurité supplémentaires afin de permettre à votre application d'appeler SSO dans le contexte de sécurité correct. Si votre application ne parvient pas à appeler SSO dans le contexte de sécurité correct, SSO lui refusera l'accès.  
  
### <a name="to-set-the-security-context-for-an-sso-application"></a>Pour définir le contexte de sécurité pour une application SSO  
  
1.  Identifiez les informations d'identification nécessaires pour que votre application s'exécute correctement.  
  
     Par exemple, une application utilisant des services Web ou .NET Framework hébergé à distance dans IIS doit emprunter l'identité du client pour transmettre les informations d'identification appropriées à SSO.  
  
2.  Confirmez que les paramètres de sécurité appropriés, tels que ceux des répertoires virtuels, pools d'applications et fichiers web.config, sont définis pour fournir ces informations d'identification à votre application.  
  
     Pour plus d’informations sur la façon de définir les informations d’identification de sécurité, consultez [création d’Applications ASP.NET sécurisées : authentification, autorisation et Communication sécurisée](http://go.microsoft.com/fwlink/?LinkId=193906).  
  
     Pour plus d’informations sur les informations d’identification de passage d’un service Web ASP.NET, consultez [Comment : passer des informations actuelles d’identification à un Service Web ASP.NET](http://go.microsoft.com/fwlink/?LinkId=193907).  
  
### <a name="to-log-a-local-user-on-to-a-host-application"></a>Pour ouvrir une session pour un utilisateur local sur une application hôte  
  
1.  Recevez la requête d'ouverture de session pour l'utilisateur actuel sur une application exécutée sur le serveur hôte.  
  
     Il vous incombe de déterminer comment l'utilisateur actuel requiert d'être connecté à une application hôte.  
  
2.  Récupérez les informations d'identification de l'utilisateur actuel à l'aide de `ISSOLookup1.GetCredentials` ou `ISSOLookup2.GetCredentials`.  
  
     Vous devez fournir le nom de l’application hôte ainsi que tous les indicateurs nécessaires. `GetCredentials`Retourne le nom d’utilisateur associé et les informations d’identification pour l’application hôte.  
  
     Notez que vous pouvez aussi bien utiliser `ISSOLookup1` que `ISSOLookup2`. La seule différence est que `ISSOLookup2` dispose également d'une méthode d'ouverture de session pour un utilisateur distant sur une application Windows locale.  
  
3.  Utilisez les nom et informations d'identification d'utilisateur externe pour l'ouverture de session sur l'application hôte.  
  
     Il vous incombe de déterminer comment utiliser les informations d'identification pour l'ouverture de session sur l'application hôte.  
  
## <a name="see-also"></a>Voir aussi  
 [Procédure : se connecter un utilisateur distant sur une Application locale](../core/how-to-log-a-remote-user-on-to-a-local-application.md)