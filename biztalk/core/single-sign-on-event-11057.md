---
title: "Single Sign-On : Événement 11057 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1e165e24-fe43-4899-ab6e-1437f639f534
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6ca69661d1421433c44472e0572c5d4d4bf76a13
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-11057"></a>Single Sign-On : Événement 11057
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|Enterprise Single Sign-On|  
|Version du produit|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|ID d'événement|11057|  
|Source de l'événement|ENTSSO|  
|Composant|Néant|  
|Nom symbolique|SSO_WARN_PS_DIRECT_MISSING_INITIAL_CREDS|  
|Texte du message|Modification directe du mot de passe. Certains champs d'informations d'identification externes manquants pour ce mappage ont été définis sur des valeurs par défaut.%r<br /><br /> ID de suivi : %1 %r<br /><br /> Nom de l’application : %2 %r<br /><br /> Compte Windows : %3 %r<br /><br /> Compte externe : %4|  
  
## <a name="explanation"></a>Explication  
 S'il est possible de modifier les mots de passe à l'aide de la synchronisation directe de mot de passe, cette fonctionnalité prend uniquement en charge un champ d'informations d'identification externes. Dans ce cas, le système d'authentification unique de l'entreprise a rencontré plusieurs champs d'informations d'identification externes et a défini ces champs sur des valeurs par défaut (vides).  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Aucune action utilisateur n’est nécessaire.