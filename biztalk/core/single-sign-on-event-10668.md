---
title: "Single Sign-On : Événement 10668 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0eb3dd4d-04b5-4713-93c1-76af012d6920
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 006855842ea2d789290200d5c5a9692b6e046e8a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10668"></a>Single Sign-On : Événement 10668
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|10668|  
|Source de l'événement|ENTSSO|  
|Composant|N\A|  
|Nom symbolique|SSO_WARN_NO_OLD_WINDOWS_PASSWORD|  
|Texte du message|Impossible de modifier le mot de passe Windows car l'ancien mot de passe Windows pour ce compte n'est pas disponible dans la base de données SSO.%r<br /><br /> Utilisez les outils d'administration SSO afin de définir les informations d'identification externes pour ce compte Windows.%r<br /><br /> ID de suivi : %1 %r<br /><br /> Carte : %2 %r<br /><br /> Compte Windows : %3|  
  
## <a name="explanation"></a>Explication  
 Cet événement d'avertissement indique que la synchronisation des mots de passe ne peut pas modifier le mot de passe Windows car l'ancien mot de passe Windows pour ce compte n'est pas disponible dans la base de données SSO.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cet avertissement, procédez comme suit :  
  
-   Identifiez les applications affectées à cet adaptateur (nom dans le message du journal des événements), puis définissez les informations d'identification externes pour ce compte Windows à l'aide des outils d'administration de l'authentification unique. Vous devez définir le mot de passe externe (pour le compte Windows donné) dans toutes ces applications.  
  
## <a name="more-info"></a>En savoir plus
  
-   [Synchronisation de mot de passe](../core/password-synchronization2.md)  
  
-   **Propriétés de l’adaptateur de synchronisation de mot de passe : Options**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]