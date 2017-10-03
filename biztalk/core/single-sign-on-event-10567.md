---
title: "Single Sign-On : Événement 10567 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3f29c8d9-3da2-4de7-b61f-8c586382b68f
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: eb6f57bed2f386363d3ae4d92b4e300061056826
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10567"></a>Single Sign-On : Événement 10567
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|10567|  
|Source de l'événement|ENTSSO|  
|Composant|Néant|  
|Nom symbolique|SSO_WARN_INVALID_APP_USER_GROUP|  
|Texte du message|Le compte Utilisateurs d'applications n'est pas valide pour la mise à jour de l'application.%r<br /><br /> Nom de l’application : %1 %r<br /><br /> Utilisateurs de l’application : %2 %r<br /><br /> Comptes non valides : %3 %r<br /><br /> Code d’erreur : %4|  
  
## <a name="explanation"></a>Explication  
 Vous avez tenté de mettre à jour un compte Utilisateurs d'applications qui n'est pas valide ou n'existe pas.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Vérifiez que le nom du compte est correct.