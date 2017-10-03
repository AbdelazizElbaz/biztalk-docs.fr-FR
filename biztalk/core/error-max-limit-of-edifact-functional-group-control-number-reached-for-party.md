---
title: "La limite maximale du numéro de contrôle de groupe fonctionnel Edifact acceptable a été atteinte pour le tiers | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2fde516b-59f1-49a1-8456-127469df0e02
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4d4a47e0866c78e692f8c992afbd6b24cde95632
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="max-limit-of-acceptable-edifact-functional-group-control-number-has-reached-for-party"></a>La limite maximale du numéro de contrôle du groupe fonctionnel EDIFACT acceptable a été atteinte pour le tiers.
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|ID d'événement|-|  
|Source de l'événement|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI|  
|Composant|Moteur EDI|  
|Nom symbolique|PartyEdifactUngNumberError|  
|Texte du message|La limite maximale du numéro de contrôle du groupe fonctionnel EDIFACT acceptable a été atteinte pour le tiers {0}. Réinitialisez le compteur en naviguant jusqu'au tiers dans l'écran du rôle du destinataire, champ UNG 5 dans le gestionnaire d'accords partenaires|  
  
## <a name="explanation"></a>Explication  
 Cet événement de type erreur/avertissement/information indique que le pipeline d'envoi n'a pas pu traiter l'échange EDIFACT sortant, car le numéro de contrôle du groupe du champ UNG5 défini dans les paramètres du tiers, notamment le numéro de référence du champ UNG5.2, était supérieur à la valeur maximum autorisée. La valeur maximale autorisée pour le numéro de contrôle du groupe dépend des valeurs des trois champs dans UNG5. Le numéro de référence (champ UNG5.2) peut comporter jusqu'à 14 caractères, le préfixe et le suffixe 13 (respectivement, champs UNG5.1 et UNG5.3). Les trois champs combinés peuvent contenir jusqu'à 14 caractères.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, rétablissez le champ du numéro de référence (UNG5.2) du numéro de contrôle du groupe en procédant comme suit :  
  
1.  Dans la boîte de dialogue Propriétés EDI correspondant au tiers résolu pour l'échange, ouvrez la page Définition des segments UNG et UNH pour le tiers jouant le rôle de récepteur des échanges.  
  
2.  Cliquez sur le champ d'édition associé au champ UNG5.  
  
3.  Définissez le champ du milieu du numéro de contrôle du groupe (le numéro de référence dans UNG5.2) sur une nouvelle valeur de manière à ce que le nombre de chiffres pour ce champ soit acceptable.