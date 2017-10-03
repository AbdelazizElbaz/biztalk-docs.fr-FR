---
title: "Single Sign-On : Événement 10731 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 605e77f0-61f2-4a97-9ea0-bdc56344e8d9
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 10960489638aa565a11ecc32c70fc3a8fc6d477b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10731"></a>Single Sign-On : Événement 10731
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|10731|  
|Source de l'événement|ENTSSO|  
|Composant|N\A|  
|Nom symbolique|SSO_WARN_INVALID_USER_NOT_IN_GROUP|  
|Texte du message|Impossible de créer un mappage car l'utilisateur spécifié n'est pas membre du compte Utilisateurs d'applications.%r<br /><br /> Nom de domaine : %1 %r<br /><br /> Nom d’utilisateur : %2 %r<br /><br /> Nom de l’application : %3 %r<br /><br /> Utilisateurs de l’application : %4 %r<br /><br /> Code d’erreur : %5|  
  
## <a name="explanation"></a>Explication  
 Cet événement d'avertissement indique qu'un mappage n'a pas pu être créé car l'utilisateur spécifié n'est pas membre du compte Utilisateurs d'applications.  
  
 Il y a un compte du groupe Utilisateurs d'applications pour chaque application associée. Les membres de ce compte peuvent vérifier leurs informations d'identification dans l'application associée et gérer leurs mappages d'informations d'identification dans l'application associée.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cet avertissement, procédez comme suit :  
  
-   Ajoutez l'utilisateur spécifié au groupe Utilisateurs d'applications de l'application associée spécifiée.  
  
 Pour plus d'informations, consultez les ressources ci-dessous.  
  
-   [Groupes d’utilisateurs de l’authentification unique](../core/sso-user-groups.md)  
  
-   [Applications associées SSO](../core/sso-affiliate-applications.md)