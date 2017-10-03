---
title: Mappages SSO | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- maps [SSO]
- maps [SSO], creating
- SSO, maps
ms.assetid: b44f7a0c-595c-49dc-9d75-2e76f29dca88
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 98b44a1a9e8be3b275a4dd328c70323d79eb8a54
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="sso-mappings"></a>Mappages SSO
Lorsqu'un administrateur de l'authentification unique de l'entreprise ou un administrateur d'applications associées à SSO définit une application associée, il peut la définir soit comme une application utilisant des mappages individuels, soit comme une application utilisant un mappage de groupe.  
  
## <a name="individual-mappings"></a>Mappages individuels  
 Les mappages individuels SSO permettent aux administrateurs et aux utilisateurs de créer un mappage un-à-un entre les utilisateurs Windows et leurs informations d'identification non-Windows correspondantes. Lors de l'utilisation de mappages individuels, les utilisateurs peuvent gérer leurs propres mappages. Le système SSO entretient la relation un-à-un pour le compte Windows et le compte non-Windows d'un utilisateur.  
  
 Les utilisateurs finaux Windows peuvent créer et gérer leurs propres mappages pour les applications de type individuel. La même application associée peut jouer le rôle d'une application SSO initiée par Windows et celui d'une application SSO initiée par l'hôte.  
  
> [!IMPORTANT]
>  Des mappages ne peuvent être créés que pour des comptes de domaine Windows. Les comptes locaux ne peuvent pas être mappés.  
  
> [!NOTE]
>  Lors de l'utilisation de mappages individuels, seuls les utilisateurs individuels peuvent obtenir les informations d'identification de leur compte individuel.  
  
## <a name="group-mapping"></a>Mappage de groupe  
 Le mappage de groupe SSO consiste à associer un groupe Windows qui contient plusieurs utilisateurs à un compte unique dans l'application associée.  
  
 Vous pouvez aussi spécifier plusieurs comptes pour le rôle des utilisateurs d'applications à authentification unique. Chaque compte que vous spécifiez peut être associé à un compte externe. Par exemple, vous pouvez mapper successivement un compte de groupe de domaine vers EXTERNALUSER1 et un compte de domaine individuel vers EXTERNALUSER2. Si un même utilisateur dispose de plusieurs mappages, le premier apparaissant dans l'ordre des utilisateurs d'applications associées à SSO est utilisé.  
  
 Seul un administrateur d'applications, un administrateur d'applications associées à SSO ou un administrateur de l'authentification unique peut créer ou gérer un mappage de groupe.  
  
 Vous ne pouvez pas indiquer la même application de groupe pour l'authentification unique initiée par Windows et pour l'authentification unique initiée par l'hôte.  
  
> [!IMPORTANT]
>  Des mappages ne peuvent être créés que pour des comptes de domaine Windows. Les comptes locaux ne peuvent pas être mappés.  
  
> [!IMPORTANT]
>  Lorsque vous utilisez des mappages de groupe, les membres du groupe peuvent obtenir les informations d'identification pour le mappage de groupe.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des mappages utilisateur](../core/managing-user-mappings.md)   
 [Applications associées SSO](../core/sso-affiliate-applications.md)