---
title: "Single Sign-On : Événement 10568 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 266fd09a-c7e6-4a69-ac1c-1834097fa393
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 84ca9c08d5eb6458fe3bb73ce912c577efe8937b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10568"></a>Single Sign-On : Événement 10568
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|10568|  
|Source de l'événement|ENTSSO|  
|Composant|Néant|  
|Nom symbolique|SSO_WARN_INVALID_APP_ADMIN_GROUP|  
|Texte du message|Le compte Administrateurs d'application n'est pas valide pour la mise à jour de l'application.%r<br /><br /> Nom de l’application : %1 %r<br /><br /> Administrateurs d’application : %2 %r<br /><br /> Comptes non valides : %3 %r<br /><br /> Code d’erreur : %4|  
  
## <a name="explanation"></a>Explication  
 Vous avez tenté de mettre à jour un compte Administrateurs d'application qui n'est pas valide ou n'existe pas.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Vérifiez que le nom du compte est correct.