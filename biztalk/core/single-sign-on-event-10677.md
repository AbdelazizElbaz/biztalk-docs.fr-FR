---
title: "Single Sign-On : Événement 10677 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2894792b-e1c9-4c24-875d-9193cbb5cd35
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 876048e9c86cf908be9eda121340ec60354803c1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10677"></a>Single Sign-On : Événement 10677
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|10677|  
|Source de l'événement|ENTSSO|  
|Composant|N\A|  
|Nom symbolique|SSO_WARN_NO_EXISTING_PASSWORD|  
|Texte du message|Changement du mot de passe externe. L'ancien mot de passe ne peut pas être vérifié car il n'y a pas d'informations d'identification pour ce compte externe.%r<br /><br /> ID de suivi : %1 %r<br /><br /> Carte : %2 %r<br /><br /> Nom de l’application : %3 %r<br /><br /> Compte externe : %4|  
  
## <a name="explanation"></a>Explication  
 Cet événement d'avertissement indique qu'un mot de passe externe a été modifié car l'ancien mot de passe n'a pas d'informations d'identification existantes.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cet avertissement, effectuez l'une ou plusieurs des opérations suivantes :  
  
-   Identifiez les applications affectées à cet adaptateur (nom dans le message du journal des événements), puis définissez les informations d'identification externes pour ce compte externe à l'aide des outils d'administration de l'authentification unique. Vous devez définir le mot de passe externe (pour le compte donné) dans toutes ces applications.  
  
## <a name="more-info"></a>En savoir plus
  
-   [Synchronisation de mot de passe](../core/password-synchronization2.md)  
  
-   **Propriétés de l’adaptateur de synchronisation de mot de passe : Options**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]