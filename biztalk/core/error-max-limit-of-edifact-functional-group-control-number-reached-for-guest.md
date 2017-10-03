---
title: "La limite maximale du numéro de contrôle de groupe fonctionnel Edifact acceptable a été atteinte pour les paramètres invité | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 93ea1bd6-8c39-4d11-81a5-75d4a861e041
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 736b191628807bf7ed0af647e83fb3665d4f2d65
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="max-limit-of-acceptable-edifact-functional-group-control-number-has-reached-for-guest-settings"></a>La limite maximale du numéro de contrôle d'un groupe fonctionnel EDIFACT a été atteinte pour les paramètres Invité
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|ID d'événement|-|  
|Source de l'événement|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI|  
|Composant|Moteur EDI|  
|Nom symbolique|GlobalEdifactUngNumberError|  
|Texte du message|La limite maximale du numéro de contrôle du groupe fonctionnel EDIFACT acceptable a été atteinte pour les paramètres Invité. Réinitialisez le compteur en naviguant jusqu'au champ UNG 5 de l'écran du rôle de destinataire de la configuration globale dans le gestionnaire d'accords partenaires|  
  
## <a name="explanation"></a>Explication  
 Cet événement d'erreur/d'avertissement/d'informations indique que le pipeline d'envoi n'a pas pu traiter l'échange sortant car le numéro de contrôle du groupe (champ UNG5) spécifié dans les paramètres globaux, notamment le numéro de référence (champ UNG5.2), est supérieur à la valeur maximale autorisée. La valeur maximale autorisée pour le numéro de contrôle du groupe dépend des valeurs des trois champs dans UNG5. Le numéro de référence (champ UNG5.2) peut comporter jusqu'à 14 caractères, le préfixe et le suffixe 13 (respectivement, champs UNG5.1 et UNG5.3). Les trois champs combinés peuvent contenir jusqu'à 14 caractères.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, rétablissez le champ du numéro de référence (UNG5.2) du numéro de contrôle du groupe en procédant comme suit :  
  
1.  Dans la boîte de dialogue Propriétés globales EDI, ouvrez la page Définition des segments UNG et UNH.  
  
2.  Cliquez sur le champ d'édition associé au champ UNG5.  
  
3.  Définissez le champ du milieu du numéro de contrôle du groupe (le numéro de référence dans UNG5.2) sur une nouvelle valeur de manière à ce que le nombre de chiffres pour ce champ soit acceptable.