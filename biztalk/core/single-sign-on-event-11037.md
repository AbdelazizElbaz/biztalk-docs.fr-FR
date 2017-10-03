---
title: "Single Sign-On : Événement 11037 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b523ff56-112e-4798-97d2-b1b19e130ec7
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 245b4af07a88c4015048db0ea20fe04b714d0ed4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-11037"></a>Single Sign-On : Événement 11037
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|11037|  
|Source de l'événement|ENTSSO|  
|Composant|Néant|  
|Nom symbolique|SSO_INFO_PS_MAPPING_INVALID|  
|Texte du message|Changement du mot de passe externe. Le mot de passe n'a pas été modifié pour le compte externe, car le mappage n'est plus valide.%r<br /><br /> ID de suivi : %1 %r<br /><br /> Carte : %2 %r<br /><br /> Nom de l’application : %3 %r<br /><br /> Compte externe : %4|  
  
## <a name="explanation"></a>Explication  
 Le mappage ne fait plus partie du groupe Utilisateurs d'applications.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Ce message indique le nom du compte externe et de l'application. Vous pouvez vous en servir pour déterminer la raison pour  laquelle le mappage n'est plus valide.