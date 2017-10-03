---
title: "Single Sign-On : Événement 11019 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5ec07b00-d567-4518-89eb-340e4f92429b
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: eb4b2d2494a404566c7350a9e9988d429a3e335c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-11019"></a>Single Sign-On : Événement 11019
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|11019|  
|Source de l'événement|ENTSSO|  
|Composant|Néant|  
|Nom symbolique|SSO_PS_WARN_NOT_IN_GROUP_DELETE_FAILED|  
|Texte du message|Le mappage n'est pas valide car le compte Windows ne figure pas dans le compte Utilisateurs d'applications pour l'application. Échec lors de la suppression du mappage. Le mappage sera ignoré.%r<br /><br /> ID de suivi : %1 %r<br /><br /> Compte Windows : %2 %r<br /><br /> Nom de l’application : %3 %r<br /><br /> Utilisateurs de l’application : %4 %r<br /><br /> Code d’erreur : %5|  
  
## <a name="explanation"></a>Explication  
 Le compte Windows spécifié n'a jamais fait partie du compte Utilisateurs d'applications, ou il en a fait partie avant d'être modifié ou supprimé. Le mappage n'a pas été supprimé.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Consultez les informations du compte de synchronisation de mot de passe pour votre système et assurez-vous qu'elles sont valides. Recréez ensuite le mappage. L'utilisation de l'Assistant Création d'un mappage réduit le risque d'informations de mappage non valides. Vous pouvez supprimer le mappage avec échec. Si vous ne le supprimez pas, il sera ignoré.