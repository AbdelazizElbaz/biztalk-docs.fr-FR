---
title: "Single Sign-On : Événement 10665 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8d0de9d0-9b46-4f3a-b796-1ce3de01cf4c
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8a7d4d5c4140448914ff77b09a692cc3a2136dfc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10665"></a>Single Sign-On : Événement 10665
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|10665|  
|Source de l'événement|ENTSSO|  
|Composant|N\A|  
|Nom symbolique|SSO_WARN_NO_PROPERTIES|  
|Texte du message|Erreur lors de la lecture des propriétés de l'adaptateur de synchronisation de mot de passe. Utilisation des valeurs par défaut.%r<br /><br /> Carte : %1 %r<br /><br /> Code d’erreur : %2|  
  
## <a name="explanation"></a>Explication  
 Cet événement d'avertissement indique la survenue d'une erreur lors de la lecture des propriétés de l'adaptateur de synchronisation de mot de passe par défaut. Chaque adaptateur de synchronisation de mot de passe est associé à des propriétés. Celles-ci peuvent être stockées dans la banque de configuration SSO et sont créées par les outils de ligne de commande SSO ou la console MMC d'administration de l'authentification unique lorsque l'adaptateur de synchronisation de mot de passe est créé.  Des propriétés peuvent être manquantes si l'adaptateur de synchronisation de mot de passe a été créé autrement, et cette erreur peut être générée.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cet avertissement, effectuez l'une ou plusieurs des opérations suivantes :  
  
-   Vérifiez les propriétés de l'adaptateur de synchronisation de mot de passe.  
  
-   Recréez l'adaptateur de synchronisation de mot de passe.  
  
## <a name="more-info"></a>En savoir plus
  
-   **Propriétés de l’adaptateur de synchronisation de mot de passe : Options**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]
  
-   [Synchronisation de mot de passe](../core/password-synchronization2.md)