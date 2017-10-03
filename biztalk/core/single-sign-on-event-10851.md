---
title: "Single Sign-On : Événement 10851 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 582b92bf-2833-47cd-b685-1245e870d81d
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fdd719c77dc77fb626f97460ed92bd74ab6da812
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10851"></a>Single Sign-On : Événement 10851
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|10851|  
|Source de l'événement|ENTSSO|  
|Composant|Néant|  
|Nom symbolique|ENTSSO_E_PSADMIN_NO_DIRECT_PASSWORD_SYNC|  
|Texte du message|L'application ne peut pas être affectée à un adaptateur de synchronisation de mot de passe car l'indicateur « direct password sync » est défini pour elle.|  
  
## <a name="explanation"></a>Explication  
 Une application ne peut pas utiliser la synchronisation de mot de passe directe et un adaptateur de synchronisation de mot de passe.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Examinez votre application et décidez si la synchronisation de mot de passe directe doit être activée pour elle. Dans l'affirmative, conservez l'indicateur défini tel que et ne tentez pas d'affecter l'application à un adaptateur de synchronisation de mot de passe. Dans la négative, désactivez l'indicateur et affectez l'application à un adaptateur de synchronisation de mot de passe.