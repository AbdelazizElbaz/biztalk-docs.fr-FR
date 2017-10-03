---
title: "Single Sign-On : Événement 11069 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1accfe68-000c-4b5e-909c-244e18eba110
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 66f89a1d273b0ed621cd3b59526714d9cb167bfb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-11069"></a>Single Sign-On : Événement 11069
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|11069|  
|Source de l'événement|ENTSSO|  
|Composant|Néant|  
|Nom symbolique|SSO_WARN_PS_PCNS_NOT_ALLOWED|  
|Texte du message|La configuration actuelle de ce serveur d'authentification unique n'autorise pas les modifications de mot de passe Windows à partir de PCNS. Utilisez « ssoconfig -allowPS PCNS yes » ou la console MMC d'administration de l'authentification unique.%r<br /><br /> ID de suivi : %1 %r<br /><br /> Utilisateur client : %2|  
  
## <a name="explanation"></a>Explication  
 La configuration actuelle de ce serveur d'authentification unique n'autorise pas les modifications de mot de passe Windows à partir de PCNS.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour autoriser les modifications de mot de passe Windows à partir de PCNS, dans le **le composant logiciel enfichable serveurs**, **propriétés de synchronisation de mot de passe** onglet, sélectionnez **autoriser la synchronisation de mot de passe à partir de PCNS.**  
  
 Pour plus d’informations, consultez [comment utiliser le composant logiciel enfichable serveurs](../core/how-to-use-the-servers-snap-in.md).