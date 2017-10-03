---
title: "Single Sign-On : Événement 10807 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 882c01c6-70db-4986-9f4b-f08335424250
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4e269b22bc8ea2fec013123d515ac04bd3f60d46
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10807"></a>Single Sign-On : Événement 10807
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|10807|  
|Source de l'événement|ENTSSO|  
|Composant|Néant|  
|Nom symbolique|ENTSSO_E_TOO_MANY_UNCONFIRMED_NOTIFICATIONS|  
|Texte du message|Notifications non confirmées trop nombreuses.|  
  
## <a name="explanation"></a>Explication  
 Chaque fois qu'une notification de modification de mot de passe est envoyée, un message de confirmation est reçu. Dans ce cas, la limite des notifications sans confirmation a été dépassée.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Vérifiez l'adaptateur de synchronisation de mot de passe.