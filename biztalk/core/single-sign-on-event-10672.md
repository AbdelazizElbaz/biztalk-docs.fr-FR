---
title: "Single Sign-On : Événement 10672 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f2422c7d-51bc-4f12-8830-193d71d2bce9
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 03eb6a72be53f928c8c173ac84556f709df0723c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10672"></a>Single Sign-On : Événement 10672
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|10672|  
|Source de l'événement|ENTSSO|  
|Composant|N\A|  
|Nom symbolique|SSO_WARN_EXTERNAL_MAPPING_CONFLICT_NOT_ALLOWED|  
|Texte du message|Un changement de mot de passe Windows a endommagé plusieurs comptes figurant sur le même système externe.%r<br /><br /> Cela ne s'est pas produit, car la carte pour ce système externe est configurée de sorte à ne pas autoriser les conflits de mappage.%r<br /><br /> ID de suivi : %1 %r<br /><br /> Carte : %2 %r<br /><br /> Compte Windows : %3 %r<br /><br /> Compte externe 1 : %4 %r<br /><br /> Compte externe 2 : %5|  
  
## <a name="explanation"></a>Explication  
 Cet avertissement indique qu'un changement de mot de passe Windows a endommagé plusieurs comptes figurant sur le même système externe. Cette modification ne s'est pas produite car la configuration de l'adaptateur ne le permettait pas.  
  
## <a name="user-action"></a>Action de l'utilisateur  
  
-   Utilisez les outils d’administration de l’authentification unique pour configurer le **autoriser les conflits de mappage** propriété pour l’adaptateur de synchronisation de mot de passe.  
  
## <a name="more-info"></a>En savoir plus
  
-   **Propriétés de l’adaptateur de synchronisation de mot de passe : Options**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]
  
-   [Synchronisation de mot de passe](../core/password-synchronization2.md)