---
title: "Single Sign-On : Événement 11042 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c1927bb5-a400-4e3a-8f80-95ef5693216c
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: da20346fbf2f73ac2ab64db3c9137394aa5bd366
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-11042"></a>Single Sign-On : Événement 11042
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|11042|  
|Source de l'événement|ENTSSO|  
|Composant|Néant|  
|Nom symbolique|SSO_WARN_ACCESS_DENIED_ACCOUNTS|  
|Texte du message|Accès refusé.<br /><br /> L'utilisateur client doit être membre de l'un des comptes suivants pour exécuter cette fonction.%r<br /><br /> Les administrateurs de l’authentification unique : %1 %r<br /><br /> Administrateurs d’applications associées SSO : %2 %r<br /><br /> Administrateurs d’application : %3 %r<br /><br /> Utilisateurs de l’application : %4 %r<br /><br /> Données supplémentaires : %5|  
  
## <a name="explanation"></a>Explication  
 L'utilisateur client doit être membre de l'un des comptes répertoriés dans l'avertissement pour exécuter cette fonction.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Vous devez souscrire à l'un de ces comptes pour exécuter cette fonction.