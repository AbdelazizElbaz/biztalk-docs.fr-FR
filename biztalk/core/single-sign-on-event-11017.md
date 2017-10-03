---
title: "Single Sign-On : Événement 11017 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1a4f7264-18aa-4eca-97c9-d5fd7e90e2cc
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 25ef3f3be84e775fe522b508f7726f3e4e88870b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-11017"></a>Single Sign-On : Événement 11017
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|11017|  
|Source de l'événement|ENTSSO|  
|Composant|Néant|  
|Nom symbolique|SSO_PS_WARN_NOT_IN_GROUP_DELETE_OK|  
|Texte du message|Le mappage n'est pas valide car le compte Windows ne figure pas dans le compte Utilisateurs d'applications pour l'application. Le mappage a été supprimé.%r<br /><br /> ID de suivi : %1 %r<br /><br /> Compte Windows : %2 %r<br /><br /> Nom de l’application : %3 %r<br /><br /> Utilisateurs de l’application : %4|  
  
## <a name="explanation"></a>Explication  
 Le compte Windows spécifié n'a jamais fait partie du compte Utilisateurs d'applications, ou il en a fait partie avant d'être modifié ou supprimé. Le mappage a été supprimé.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Consultez les informations du compte de synchronisation de mot de passe pour votre système et assurez-vous qu'elles sont valides. Recréez ensuite le mappage. L'utilisation de l'Assistant Création d'un mappage réduit le risque d'informations de mappage non valides.