---
title: "Single Sign-On : Événement 10820 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2da93a2c-d00d-4ca0-a0cf-453cee4bf3c3
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 46a3ae1be84ca0b936fe38463e51e6385071f7a9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10820"></a>Single Sign-On : Événement 10820
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|10820|  
|Source de l'événement|ENTSSO|  
|Composant|Néant|  
|Nom symbolique|ENTSSO_E_REQUIRE_OLD_PASSWORD|  
|Texte du message|Lors de la modification du mot de passe d'un compte externe, l'adaptateur doit fournir l'ancien mot de passe.|  
  
## <a name="explanation"></a>Explication  
 La configuration de cette application requiert l'adaptateur de synchronisation de mot de passe pour fournir l'ancien mot de passe.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Vérifiez la configuration de votre adaptateur de synchronisation de mot de passe.