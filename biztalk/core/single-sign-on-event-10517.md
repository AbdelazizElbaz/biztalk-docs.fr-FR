---
title: "Single Sign-On : Événement 10517 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2b63e4b0-0ef6-45c2-b8b1-55ac20e79e26
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2716eb7d331ec5c15070555a028c00310188856c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10517"></a>Single Sign-On : Événement 10517
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|10517|  
|Source de l'événement|ENTSSO|  
|Composant|N\A|  
|Nom symbolique|SSO_ERROR_BAD_SSO_ADMIN|  
|Texte du message|Le compte Administrateurs de l'authentification unique n'est pas valide. S'il s'agit d'un compte local, assurez-vous que ce compte existe sur le serveur. S'il s'agit d'un compte de domaine, contactez votre administrateur système. Activez SSO lorsque le compte est valide.%r<br /><br /> Les administrateurs de l’authentification unique : %1 %r<br /><br /> Comptes non valides : %2 %r<br /><br /> Code d’erreur : %3|  
  
## <a name="explanation"></a>Explication  
 Cet événement d'erreur indique que le compte Administrateurs de l'authentification unique spécifié pour l'authentification unique de l'entreprise n'est pas un compte Windows valide. Le compte de service exécutant le service d'authentification unique de l'entreprise doit être membre de ce compte. Le compte Administrateurs de l'authentification unique peut être un compte de groupe Windows ou un compte individuel. Il peut également être un compte de groupe de domaine ou local. Lorsque vous utilisez un compte individuel, vous ne pouvez pas modifier ce compte en un autre compte individuel.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, procédez comme suit :  
  
-   Vérifiez que le compte Administrateurs de l'authentification unique existe.  
  
 Pour plus d'informations, consultez les ressources suivantes dans l'aide de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] :  
  
-   [Groupes d’utilisateurs de l’authentification unique](../core/sso-user-groups.md)