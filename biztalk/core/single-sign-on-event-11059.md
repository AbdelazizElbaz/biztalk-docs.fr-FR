---
title: "Single Sign-On : Événement 11059 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ac5b6ce7-8819-4b9d-85f7-f5dfaf940487
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3dfab1d020211565df452b6cfaf0bca14e724f0b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-11059"></a>Single Sign-On : Événement 11059
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|11059|  
|Source de l'événement|ENTSSO|  
|Composant|Néant|  
|Nom symbolique|SSO_INFO_INVALID_USER_NOT_IN_GROUP|  
|Texte du message|Impossible de créer un mappage car l'utilisateur spécifié n'est pas membre du compte Utilisateurs d'applications.%r<br /><br /> Compte Windows : %1\\%2 %r<br /><br /> Nom de l’application : %3 %r<br /><br /> Utilisateurs de l’application : %4 %r<br /><br /> Code d’erreur : %5|  
  
## <a name="explanation"></a>Explication  
 Le mappage n’a pas pu être créé car l’utilisateur spécifié n’est pas un membre du compte utilisateurs d’applications.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Contactez votre administrateur de l'authentification unique de l'entreprise pour devenir membre du compte Utilisateurs d'applications.