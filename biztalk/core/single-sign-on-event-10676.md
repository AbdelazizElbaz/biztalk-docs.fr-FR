---
title: "Single Sign-On : Événement 10676 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ec0e86fb-921d-4505-b458-51b565123ea7
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3805e59e5e8984652ec40af9f93db793d5d3b5fc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10676"></a>Single Sign-On : Événement 10676
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|10676|  
|Source de l'événement|ENTSSO|  
|Composant|N\A|  
|Nom symbolique|SSO_ERROR_REQUIRE_OLD_PASSWORD|  
|Texte du message|Changement du mot de passe externe. Lors de la modification du mot de passe relatif à un compte externe, l'adaptateur doit fournir l'ancien mot de passe.%r<br /><br /> ID de suivi : %1 %r<br /><br /> Carte : %2 %r<br /><br /> Compte externe : %3|  
  
## <a name="explanation"></a>Explication  
 Cette erreur indique que l'adaptateur de synchronisation de mot de passe a été configuré de manière à ce qu'un ancien mot de passe du système externe soit indiqué, ce qui n'a pas été le cas dans la situation présente. Cela signifie que le système externe (l'adaptateur de synchronisation de mot de passe externe) n'est pas configuré ou ne fonctionne pas comme prévu ou que l'adaptateur de synchronisation de mot de passe est configuré de manière incorrecte. Cette erreur peut également renvoyer le nom symbolique de code d'erreur ENTSSO_E_REQUIRE_OLD_PASSWORD.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, procédez comme suit :  
  
-   Utilisez les outils d’administration SSO pour définir la propriété configurable par l’utilisateur **vérifier un ancien mot de passe** sous l’onglet de propriétés Options de l’adaptateur de synchronisation de mot de passe. Cette propriété peut également être définie lors de la création d'adaptateurs par le biais des outils de ligne de commande (ssops.exe), avec le nom d'indicateur `verifyOldPassword`, ainsi que lors de la création d'un adaptateur de synchronisation de mot de passe à l'aide de l'Assistant de l'adaptateur de synchronisation de mot de passe.  
  
## <a name="more-info"></a>En savoir plus
  
-   [Synchronisation de mot de passe](../core/password-synchronization2.md)  
  
-   **Propriétés de l’adaptateur de synchronisation de mot de passe : Options**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]