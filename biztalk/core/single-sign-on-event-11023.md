---
title: "Single Sign-On : Événement 11023 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: feeb4ede-6045-46bf-9f2b-65062c583faa
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cd65ac5cab5b49f43e0c3649cf205f7f6dc2ceaf
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-11023"></a>Single Sign-On : Événement 11023
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|11023|  
|Source de l'événement|ENTSSO|  
|Composant|Néant|  
|Nom symbolique|SSO_WARN_WINDOWS_PASSWORD_DELETED|  
|Texte du message|Un mot de passe Windows non valide dans la base de données SSO a été supprimé pour éviter le verrouillage de compte.%r<br /><br /> Utilisez les outils d'administration SSO afin de définir les informations d'identification externes pour ce compte Windows.%r<br /><br /> ID de suivi : %1 %r<br /><br /> Carte : %2 %r<br /><br /> Compte Windows : %3|  
  
## <a name="explanation"></a>Explication  
 Un mot de passe Windows non valide a été supprimé.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Utilisez les outils d'administration SSO afin de définir les informations d'identification externes pour ce compte Windows. Pour plus d’informations, consultez [à l’aide de l’authentification unique](../core/using-sso.md).