---
title: Groupes utilisateur SSO | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- administrator accounts, SSO
- groups, SSO
- user accounts, administrators
- service accounts, SSO
- SSO, user groups
- SSO, service accounts
- SSO, administrator accounts
ms.assetid: e279001e-c724-4a2d-8939-0ba9dd08a19c
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 949f3aa72771982321abf6904c43352b8821fc0c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="sso-user-groups"></a>Groupes d’utilisateurs de l’authentification unique
Pour configurer et gérer le système d'authentification unique de l'entreprise, vous devez créer certains groupes et comptes Windows pour chacun de ces rôles. Lors de la configuration de ces comptes d'accès dans l'authentification unique de l'entreprise, vous pouvez spécifier plusieurs comptes pour chaque rôle. Cette section décrit ces rôles.  
  
> [!IMPORTANT]
>  Il est fortement recommandé d'utiliser les groupes de domaine lors de la configuration de l'authentification unique.  
  
> [!NOTE]
>  Pour des raisons de sécurité, le système d'authentification unique n'autorise pas les comptes intégrés.  
  
## <a name="single-sign-on-administrators"></a>Administrateurs de l’authentification unique  
 Les administrateurs SSO disposent des droits d'utilisateur les plus élevés dans le système d'authentification unique. Ils peuvent :  
  
-   Créer et gérer la base de données SSO  
  
-   Créer et gérer le secret principal  
  
-   Activer et désactiver le système d'authentification unique  
  
-   Créer des adaptateurs de synchronisation de mot de passe  
  
-   Activer et désactiver la synchronisation de mot de passe dans le système d'authentification unique  
  
-   Activer et désactiver l'authentification unique initiée par l'hôte  
  
-   Effectuer toutes les tâches d'administration  
  
 Le compte d'administrateur SSO peut être un compte de groupe Windows ou un compte individuel. Le compte d'administrateur SSO peut également être un compte individuel ou de groupe de domaine ou local. Lorsque vous utilisez un compte individuel, vous ne pouvez pas modifier ce compte en un autre compte individuel. Par conséquent, il est recommandé de ne pas utiliser un compte individuel. Vous pouvez changer ce compte en un compte de groupe tant que le compte d'origine est membre du nouveau compte.  
  
> [!IMPORTANT]
>  Le compte de service exécutant le service d'authentification unique de l'entreprise doit être membre de ce compte. Pour sécuriser votre environnement, vérifiez qu'aucun autre service n'utilise le même compte de service.  
  
## <a name="single-sign-on-affiliate-administrators"></a>Administrateurs d'applications associées à SSO  
 L'administrateur d'applications associées à SSO définit les applications associées contenues dans le système d'authentification unique. Les applications associées sont une entité logique qui représente le système principal auquel vous êtes connecté à l'aide de l'authentification unique. Les administrateurs d'applications associées à SSO peuvent :  
  
-   Créer, gérer et supprimer des applications associées  
  
-   Spécifier le compte d'administrateur d'application pour chaque application associée  
  
-   Effectuer toutes les tâches d'administration que les administrateurs et utilisateurs d'application peuvent réaliser  
  
 Le compte d'administrateur d'applications associées à SSO peut être un compte de groupe Windows ou un compte individuel. Le compte d'administrateur d'applications associées à SSO peut également être un compte ou groupe de domaine ou local.  
  
## <a name="application-administrators"></a>Administrateurs d'application  
 Il existe un groupe d'administrateurs d'application par application associée.  
  
 Les membres de ce groupe peuvent :  
  
-   Modifier le compte du groupe d'utilisateurs d'application  
  
-   Créer, supprimer et gérer les mappages d'informations d'identification pour tous les utilisateurs de l'application associée spécifique  
  
-   Définir des informations d'identification pour tout utilisateur dans ce compte du groupe d'utilisateurs d'application associée spécifique  
  
-   Effectuer toutes les tâches d'administration que les utilisateurs d'application peuvent réaliser  
  
## <a name="application-users"></a>Utilisateurs d'application  
 Il existe un compte du groupe d'utilisateurs d'application pour chaque application associée. Ce compte contient la liste des utilisateurs finaux dans un environnement d'authentification unique de l'entreprise. Les membres de ce compte peuvent :  
  
-   Rechercher leurs informations d'identification dans l'application associée  
  
-   Gérer leurs mappages d'informations d'identification dans l'application associée  
  
> [!NOTE]
>  N'oubliez pas d'être vigilant lors de l'affectation des groupes. Par exemple, vous pouvez utiliser un groupe d'utilisateurs de sécurité BizTalk Server pour un groupe d'utilisateurs d'application SSO. Avant de procéder, assurez-vous que tous les utilisateurs ont besoin de tout l'accès dont ils disposeront alors.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment mettre à jour les propriétés d’une Application associée](../core/how-to-update-the-properties-of-an-affiliate-application.md)   
 [Comment mettre à jour la base de données SSO](../core/how-to-update-the-sso-database.md)   
 [Gestion des mappages utilisateur](../core/managing-user-mappings.md)   
 [Présentation de l’authentification unique](../core/understanding-sso.md)