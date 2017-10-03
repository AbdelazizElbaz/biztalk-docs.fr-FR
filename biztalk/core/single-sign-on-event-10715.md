---
title: "Single Sign-On : Événement 10715 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f63c98d2-988e-466f-be40-171b13a34732
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 24bf65f00d9ef915d585c91aa06900b96d4b44d0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10715"></a>Single Sign-On : Événement 10715
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|10715|  
|Source de l'événement|ENTSSO|  
|Composant|N\A|  
|Nom symbolique|SSO_WARN_NO_CREATE_ADAPTER|  
|Texte du message|L'utilisateur client doit être membre du compte Administrateurs SSO pour pouvoir créer des adaptateurs.%r<br /><br /> L’utilisateur client : %1 %r<br /><br /> Les administrateurs SSO : %2 %r<br /><br /> Carte : %3 %r<br /><br /> Code d’erreur : %4|  
  
## <a name="explanation"></a>Explication  
 Cet avertissement indique que l'utilisateur client doit être membre du compte Administrateurs SSO pour pouvoir créer des adaptateurs.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cet avertissement, procédez comme suit :  
  
-   Connectez-vous à l'aide d'un compte appartenant au groupe Administrateurs SSO.  
  
 Pour plus d'informations, consultez les ressources ci-dessous.  
  
-   [Groupes d’utilisateurs de l’authentification unique](../core/sso-user-groups.md)