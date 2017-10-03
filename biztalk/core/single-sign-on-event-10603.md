---
title: "Single Sign-On : Événement 10603 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 139d1eb5-af88-4216-9604-c052f3db13c9
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 738d2939f4178fdfaa115b8dfcc2273935c37b85
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10603"></a>Single Sign-On : Événement 10603
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|10603|  
|Source de l'événement|ENTSSO|  
|Composant|Néant|  
|Nom symbolique|SSO_WARN_DB_ACCESS|  
|Texte du message|Impossible d'accéder à la base de données SSO. Si cette situation persiste, le service d'authentification unique se déconnecte.%r<br /><br /> %1.%r<br /><br /> Code d’erreur SQL : %2|  
  
## <a name="explanation"></a>Explication  
 La base de données SSO n'est pas disponible.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Consultez le code d'erreur SQL contenu dans l'avertissement. Il peut vous donner des informations utiles. Sinon, contactez les services de support technique Microsoft.