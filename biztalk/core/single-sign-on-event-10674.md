---
title: "Single Sign-On : Événement 10674 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ad0c0d9e-1e6d-4c3e-86e0-9e336a18f3d6
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d239353276657e85c7fbdcfa634c3c1268723724
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10674"></a>Single Sign-On : Événement 10674
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|10674|  
|Source de l'événement|ENTSSO|  
|Composant|N\A|  
|Nom symbolique|SSO_WARN_WINDOWS_MAPPING_CONFLICT_NOT_ALLOWED|  
|Texte du message|Une modification de mot de passe externe aurait entraîné la modification de plusieurs comptes Windows.%r<br /><br /> Cela ne s'est pas produit, car la carte pour ce système externe est configurée de sorte à ne pas autoriser les conflits de mappage.%r<br /><br /> ID de suivi : %1 %r<br /><br /> Carte : %2 %r<br /><br /> Compte externe : %3 %r<br /><br /> Compte Windows 1 : %4 %r<br /><br /> Le compte Windows 2 : %5|  
  
## <a name="explanation"></a>Explication  
 Cet événement d'avertissement indique qu'une modification de mot de passe externe aurait entraîné la modification de plusieurs comptes Windows. Cette modification ne s'est pas produite car la configuration de l'adaptateur ne le permettait pas.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, procédez comme suit :  
  
-   Si les conflits de mappage sont attendus et autorisés, utilisez les outils d’administration de l’authentification unique pour configurer le **autoriser les conflits de mappage** propriété pour l’adaptateur de synchronisation de mot de passe.  
  
## <a name="more-info"></a>En savoir plus
  
-   **Propriétés de l’adaptateur de synchronisation de mot de passe : Options**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]
  
-   [Synchronisation de mot de passe](../core/password-synchronization2.md)