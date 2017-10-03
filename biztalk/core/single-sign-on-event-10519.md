---
title: "Single Sign-On : Événement 10519 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e709957e-a690-4a44-a863-07b2a55dae7b
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 928892ff1d0ee461a26095ddc7a72fd3accecf10
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10519"></a>Single Sign-On : Événement 10519
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|10519|  
|Source de l'événement|ENTSSO|  
|Composant|N\A|  
|Nom symbolique|SSO_WARN_BAD_APP_ADMIN_GROUP|  
|Texte du message|Le compte Administrateurs d'applications associé à cette application n'est pas valide. S'il s'agit d'un compte local, assurez-vous que ce compte existe sur le serveur. S'il s'agit d'un compte de domaine, contactez votre administrateur système. Activez l'application une fois le compte valide. Vous pouvez ignorer ce message si vous n'envisagez pas d'utiliser cette application sur cet ordinateur.%r<br /><br /> Nom de l’application : %1 %r<br /><br /> Administrateurs d’application : %2 %r<br /><br /> Comptes non valides : %3 %r<br /><br /> Code d’erreur : %4|  
  
## <a name="explanation"></a>Explication  
 Cet avertissement indique que le compte du groupe Administrateurs d'applications ne correspond pas à un compte Windows valide. Il existe un groupe de compte Administrateurs d'applications pour chaque application associée.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cet avertissement, effectuez l'une ou plusieurs des opérations suivantes :  
  
-   Assurez-vous que le compte Administrateurs d'applications spécifié existe.  
  
-   À l'aide de l'utilitaire d'administration SSO, vérifiez que l'application associée spécifiée est configurée de façon à utiliser le compte Administrateurs d'applications correct.  
  
 Pour plus d'informations, consultez les ressources suivantes dans l'aide de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] :  
  
-   [Groupes d’utilisateurs de l’authentification unique](../core/sso-user-groups.md)  
  
-   [Applications associées SSO](../core/sso-affiliate-applications.md)  
  
-   [Comment mettre à jour les propriétés d’une Application associée](../core/how-to-update-the-properties-of-an-affiliate-application.md)