---
title: "Single Sign-On : Événement 11071 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9c0f61b9-cd86-482b-a8fe-0093a928c89b
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e744e4f477ee45e6f634e8e4b2ca976754cbecf1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-11071"></a>Single Sign-On : Événement 11071
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|11071|  
|Source de l'événement|ENTSSO|  
|Composant|Néant|  
|Nom symbolique|SSO_WARN_PS_WIN_CHANGE_DISCARDED_ZERO_LENGTH|  
|Texte du message|Une modification de mot de passe Windows a été ignorée car le mot de passe Windows ne comporte aucun caractère.%r<br /><br /> ID de suivi : %1 %r<br /><br /> Compte Windows : %2 %r<br /><br /> Utilisateur client : %3|  
  
## <a name="explanation"></a>Explication  
 Une modification de mot de passe Windows a été ignorée car le mot de passe Windows ne comporte aucun caractère. Le compte Windows et le nom d'utilisateur du client sont fournis.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Modifiez à nouveau le mot de passe en utilisant les nombre et type de caractères requis par votre système SSO.