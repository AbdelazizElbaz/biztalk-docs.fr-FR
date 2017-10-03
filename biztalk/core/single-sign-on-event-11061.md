---
title: "Single Sign-On : Événement 11061 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 52fb18e2-4482-4cdb-b8ed-d579a95acd7c
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e86ad25248952697e27fc732ddead6732065acf7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-11061"></a>Single Sign-On : Événement 11061
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|11061|  
|Source de l'événement|ENTSSO|  
|Composant|Néant|  
|Nom symbolique|SSO_WARN_BAD_PASSWORD_FILTER|  
|Texte du message|La chaîne du filtre de mot de passe n'est pas valide. Aucun filtre de mot de passe ne sera utilisé.%r<br /><br /> Nom de l’application : %1 %r<br /><br /> Chaîne de filtre de mot de passe : %2 %r<br /><br /> Nombre de jetons traités : %3 %r<br /><br /> Données supplémentaires : %4 %r<br /><br /> Code d’erreur : %5|  
  
## <a name="explanation"></a>Explication  
 Un filtre de mot de passe non valide a été créé manuellement. Une erreur est survenue au cours de ce processus (consultez la chaîne du filtre de mot de passe dans l'avertissement pour déterminer l'emplacement de l'erreur).  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour créer le filtre de mot de passe à l’aide de l’Assistant Création d’un filtre de mot de passe, consultez [comment utiliser des filtres de mot de passe](../core/how-to-use-password-filters.md).