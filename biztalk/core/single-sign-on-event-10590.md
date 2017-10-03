---
title: "Single Sign-On : Événement 10590 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fd8c3804-5c84-403f-881b-e4b101c2323a
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 542e597c56f1049133670c91f233d82f5f431b78
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10590"></a>Single Sign-On : Événement 10590
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|10590|  
|Source de l'événement|ENTSSO|  
|Composant|Néant|  
|Nom symbolique|SSO_ERROR_OUT_OF_SERVICE|  
|Texte du message|Déconnexion en cours de l'authentification unique de l'entreprise.|  
  
## <a name="explanation"></a>Explication  
 Le système ENTSSO recherche généralement des mises à jour au niveau de la base de données ENTSSO toutes les 30 secondes. Si la base de données n'est pas disponible pendant une durée spécifiée (en général, cinq minutes), le système se déconnecte. Cela fait, le système ne répond plus aux demandes d'informations d'identification. Il est toutefois toujours possible d'effectuer certaines activités d'administration et hors ligne.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Cette erreur indique que la base de données ENTSSO est hors ligne. Vous devez en rechercher la cause immédiatement.