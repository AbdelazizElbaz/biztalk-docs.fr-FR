---
title: "Single Sign-On : Événement 10680 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 88ea12ff-d181-423f-9054-b0c656cc4558
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bd7b1804578e1b0880eaa564f68a24f0841280fa
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10680"></a>Single Sign-On : Événement 10680
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|10680|  
|Source de l'événement|ENTSSO|  
|Composant|N\A|  
|Nom symbolique|SSO_WARN_PS_GET_CREDS_FAILED|  
|Texte du message|Le mot de passe n'a pas été modifié pour le compte externe car les informations d'identification externes existantes n'ont pas pu être obtenues auprès de la base de données SSO.%r<br /><br /> ID de suivi : %1 %r<br /><br /> Carte : %2 %r<br /><br /> Nom de l’application : %3 %r<br /><br /> Compte externe : %4 %r<br /><br /> Code d’erreur : %5|  
  
## <a name="explanation"></a>Explication  
 Cet événement d'avertissement indique que le mot de passe n'a pas été modifié pour le compte externe car les informations d'identification externes existantes n'ont pas pu être obtenues auprès de la base de données SSO.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cet avertissement, procédez comme suit :  
  
-   Vérifiez les informations d'identification externes.  
  
-   Les informations d'identification externes ne sont pas valides. Utilisez les outils d'administration de l'authentification unique pour définir les informations d'identification externes pour ce compte externe. Vous devez définir le mot de passe externe (pour le compte donné) dans toutes les applications associées.  
  
## <a name="more-info"></a>En savoir plus
  
-   [Synchronisation de mot de passe](../core/password-synchronization2.md)  
  
-   **Propriétés de l’adaptateur de synchronisation de mot de passe : Options**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]