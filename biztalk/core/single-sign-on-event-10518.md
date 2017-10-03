---
title: "Single Sign-On : Événement 10518 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 274e29f9-1933-4e40-83c0-2e84c6708315
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a27b82d7f0a6bbaf02400679add53851867d728c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10518"></a>Single Sign-On : Événement 10518
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|10518|  
|Source de l'événement|ENTSSO|  
|Composant|N\A|  
|Nom symbolique|SSO_WARN_BAD_USER_GROUP|  
|Texte du message|Le compte Utilisateurs d'applications pour cette application n'est pas valide. S'il s'agit d'un compte local, assurez-vous que ce compte existe sur le serveur. S'il s'agit d'un compte de domaine, contactez votre administrateur système. Activez l'application une fois le compte valide. Vous pouvez ignorer ce message si vous n'envisagez pas d'utiliser cette application sur cet ordinateur.%r<br /><br /> Nom de l’application : %1 %r<br /><br /> Utilisateurs de l’application : %2 %r<br /><br /> Comptes non valides : %3 %r<br /><br /> Code d’erreur : %4|  
  
## <a name="explanation"></a>Explication  
 Cet événement d'avertissement indique qu'un compte de groupe Utilisateurs d'applications n'est pas un compte Windows valide. Il existe un compte du groupe Utilisateurs d'applications pour chaque application associée.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cet avertissement, effectuez l'une ou plusieurs des opérations suivantes :  
  
-   Vérifiez que le compte Utilisateurs d'applications spécifié existe.  
  
-   Utilisez l'utilitaire d'administration de l'authentification unique pour vérifier que l'application associée spécifiée est configurée pour utiliser le compte Utilisateurs d'applications correct.  
  
 Pour plus d'informations, consultez les ressources suivantes dans l'aide de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] :  
  
-   [Groupes d’utilisateurs de l’authentification unique](../core/sso-user-groups.md)  
  
-   [Applications associées SSO](../core/sso-affiliate-applications.md)  
  
-   [Comment mettre à jour les propriétés d’une Application associée](../core/how-to-update-the-properties-of-an-affiliate-application.md)