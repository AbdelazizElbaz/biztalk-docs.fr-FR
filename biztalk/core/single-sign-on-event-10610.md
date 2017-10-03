---
title: "Single Sign-On : Événement 10610 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f6a400eb-7cf2-49df-befb-caf76e845fdf
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d3e4edc579c18147ad34234fbf268ec8d867c60f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10610"></a>Single Sign-On : Événement 10610
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|10610|  
|Source de l'événement|ENTSSO|  
|Composant|Néant|  
|Nom symbolique|SSO_WARN_CRED_CACHE_FAILED|  
|Texte du message|Le cache des informations d'identification a rencontré une erreur inattendue et s'est arrêté. Cela peut avoir une incidence sur les performances.%r<br /><br /> Code d’erreur : %1|  
  
## <a name="explanation"></a>Explication  
 Le cache des informations d'identification a rencontré une erreur inattendue et s'est arrêté. Bien que cette situation puisse affecter les performances, cela n'aura aucune incidence sur les fonctionnalités.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Redémarrez le service SSO au moment opportun.