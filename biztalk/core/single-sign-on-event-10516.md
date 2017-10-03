---
title: "Single Sign-On : Événement 10516 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d20df92f-c995-4cbc-a8f9-21cea30b82c9
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7d0b74ca4a47bc62d28b25564bd5843729c56362
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10516"></a>Single Sign-On : Événement 10516
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|10516|  
|Source de l'événement|ENTSSO|  
|Composant|N\A|  
|Nom symbolique|SSO_ERROR_BAD_SSO_APP_ADMIN|  
|Texte du message|Le compte Administrateurs d'applications associées à SSO n'est pas valide. S'il s'agit d'un compte local, assurez-vous que ce compte existe sur le serveur. S'il s'agit d'un compte de domaine, contactez votre administrateur système. Activez SSO lorsque le compte est valide.%r<br /><br /> Administrateurs d’applications associées SSO : %1 %r<br /><br /> Comptes non valides : %2 %r<br /><br /> Code d’erreur : %3|  
  
## <a name="explanation"></a>Explication  
 Cette erreur indique que le groupe ou le compte Administrateurs d'applications associées à SSO créé par l'authentification unique de l'entreprise ne correspond pas à un compte Windows valide. Le compte Administrateurs d'applications associées à SSO peut correspondre à un compte individuel ou de groupe Windows. Le compte Administrateurs d'applications associées à SSO peut également correspondre à un compte de groupe local ou de domaine.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, procédez comme suit :  
  
-   Assurez-vous que le compte Administrateurs d'applications associées à SSO existe.  
  
 Pour plus d'informations, consultez les ressources suivantes dans l'aide de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] :  
  
-   [Groupes d’utilisateurs de l’authentification unique](../core/sso-user-groups.md)  
  
-   [Comment mettre à jour la base de données SSO](../core/how-to-update-the-sso-database.md)