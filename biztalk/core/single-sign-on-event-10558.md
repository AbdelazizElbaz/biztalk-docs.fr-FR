---
title: "Single Sign-On : Événement 10558 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 84637b67-09df-4c1e-b9f2-85a738ba0d7a
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2c2ee5c21bdf90e6aedcdbe2ac83e0e51a7f48f6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10558"></a>Single Sign-On : Événement 10558
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|10558|  
|Source de l'événement|ENTSSO|  
|Composant|Néant|  
|Nom symbolique|SSO_WARN_USER_OWN_MAPPINGS|  
|Texte du message|Les utilisateurs d'applications sont uniquement autorisés à contrôler leurs propres mappages.%r<br /><br /> Nom de domaine : %1 %r<br /><br /> Nom d’utilisateur : %2 %r<br /><br /> Nom de l’application : %3 %r<br /><br /> Utilisateur client : %4|  
  
## <a name="explanation"></a>Explication  
 Un utilisateur d'applications a tenté de contrôler les mappages d'un autre utilisateur. Cela n'est pas autorisé.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Les mappages peuvent uniquement être contrôlés par les utilisateurs d'applications associés à ces mappages spécifiques.