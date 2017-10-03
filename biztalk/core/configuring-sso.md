---
title: Configuration de SSO | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SSO, command line utilities
- configuring, SSO
- SSO, interfaces
- SSOConfig [SSO]
- SSO, configuring
- SSOClient [SSO]
- SSO, tools
- SSOManage [SSO]
ms.assetid: 6f755735-9b48-4771-beec-ced844f3d532
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d729633717d709a83c10e9b50c55791029902010
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-sso"></a>Configuration de l’authentification unique
Vous pouvez configurer l'authentification unique de l'entreprise à l'aide d'utilitaires de ligne de commande, d'outils utilisant l'interface utilisateur ou d'interfaces COM ou Microsoft .NET.  
  
## <a name="sso-command-line-utilities"></a>Utilitaires de ligne de commande SSO  
 Trois utilitaires de ligne de commande distincts permettent d'effectuer des tâches liées à l'authentification unique de l'entreprise :  
  
 **SSOConfig.** permet à un administrateur de l'authentification unique (SSO) de configurer la base de données SSO et de gérer le secret principal.  
  
> [!NOTE]
>  L'Assistant Configuration crée la base de données SSO et le serveur de secret principal.  
  
 **SSOManage.** Active les administrateurs SSO, administrateurs d’applications associées SSO et administrateurs de l’application mettre à jour la base de données SSO à ajouter, supprimer et gérer des applications, administrer des mappages d’utilisateur et pour définir les informations d’identification de la filiale utilisateurs de l’application. Certaines opérations peuvent être réalisées uniquement par les administrateurs SSO ou uniquement par les administrateurs SSO et les administrateurs d'applications associées à SSO. Toutes les opérations pouvant être réalisées par les administrateurs d'applications peuvent également l'être par les administrateurs SSO et les administrateurs d'applications associées à SSO.  
  
 **SSOClient.** permet aux utilisateurs de l'authentification unique de gérer leurs propres mappages et de définir leurs informations d'identification.  
  
 Pour plus d’informations sur les comptes de l’authentification unique, consultez [groupes utilisateur SSO](../core/sso-user-groups.md).  
  
## <a name="sso-ui-tools"></a>Outils utilisant l'interface utilisateur SSO  
 **Enterprise SSO enfichable MMC.** permet aux administrateurs SSO, aux administrateurs d'applications associées à SSO et aux administrateurs d'application de mettre à jour la base de données SSO afin d'ajouter, de supprimer et de gérer des applications, d'administrer des mappages d'utilisateurs et de définir des informations d'identification pour les utilisateurs d'applications associées. Certaines opérations peuvent être effectuées uniquement par les administrateurs de l’authentification unique, ou uniquement par l’authentification unique, les administrateurs et l’authentification unique associée aux administrateurs. Toutes les opérations qui peuvent être effectuées par les administrateurs d’applications peuvent également être effectuées par les administrateurs SSO et administrateurs d’applications associées à authentification unique.  
  
 **Utilitaire Client SSO :** permet aux utilisateurs finaux de gérer leurs propres mappages et de définir leurs informations d'identification à l'aide de l'outil utilisant l'interface utilisateur.  
  
## <a name="sso-com-and-net-interfaces"></a>Interfaces COM et .NET SSO  
 Dans l'optique de simplifier l'administration du système SSO, l'authentification unique de l'entreprise propose des interfaces de programmation COM et .NET qui vous permettent de créer des composants personnalisés ainsi que des scripts.  
  
## <a name="see-also"></a>Voir aussi  
 [Composants de l’authentification unique](../core/sso-components.md)