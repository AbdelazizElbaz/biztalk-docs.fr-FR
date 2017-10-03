---
title: "Single Sign-On : Événement 11043 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 128d68fb-1905-49b3-9b67-30a9442569cc
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fc211e4726c68a16f860dd0431a234765e80b76a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-11043"></a>Single Sign-On : Événement 11043
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|11043|  
|Source de l'événement|ENTSSO|  
|Composant|Néant|  
|Nom symbolique|SSO_WARN_PS_ADAPTER_REPORTED_FAILURE|  
|Texte du message|L'adaptateur de synchronisation de mot de passe a signalé un échec lors de la modification du mot de passe externe. Le mot de passe externe n'a pas été mis à jour dans la base de données SSO.%r<br /><br /> ID de suivi : %1 %r<br /><br /> Carte : %2 %r<br /><br /> Compte externe : %3 %r<br /><br /> Message d’erreur : %4 %r<br /><br /> Code d’erreur : %5|  
  
## <a name="explanation"></a>Explication  
 Lorsque l'authentification unique envoie une modification de mot de passe à un adaptateur de synchronisation de mot de passe, le mot de passe externe doit être modifié avant que l'authentification unique de l'entreprise le fasse dans la base de données SSO. Ce n'est pas ce qui s'est passé dans ce cas.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Notez les informations dans le message d'avertissement et consultez votre administrateur système.