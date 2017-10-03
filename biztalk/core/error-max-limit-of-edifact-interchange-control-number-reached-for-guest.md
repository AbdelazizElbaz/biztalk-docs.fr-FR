---
title: "La limite maximale du numéro de contrôle l’échange Edifact acceptable a été atteinte pour les paramètres invité | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a5d2dcc0-61fd-47c9-9339-8a85319c5398
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6dc8110f9aa9a48e098f970383b65266cc544c19
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="max-limit-of-acceptable-edifact-interchange-control-number-has-reached-for-guest-settings"></a>La limite maximale du numéro de contrôle d'échange Edifact acceptable a été atteinte pour les paramètres Invité
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|ID d'événement|-|  
|Source de l'événement|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI|  
|Composant|Moteur EDI|  
|Nom symbolique|GlobalEdifactUnbNumberError|  
|Texte du message|La limite maximale du numéro de contrôle d'échange Edifact acceptable a été atteinte pour les paramètres Invité. Réinitialisez le compteur en naviguant jusqu'au champ UNB 5 de l'écran du rôle de destinataire de la configuration globale dans le gestionnaire d'accords partenaires|  
  
## <a name="explanation"></a>Explication  
 Cet événement d'erreur/d'avertissement/d'informations indique que le pipeline d'envoi n'a pas pu traiter l'échange sortant, car son numéro de contrôle (champ ISA13) spécifié dans les paramètres globaux, notamment le numéro de référence (champ UNB5.2), est supérieur à la valeur maximale autorisée. La valeur maximale autorisée pour le numéro de contrôle d'un échange dépend des valeurs des trois champs dans UNB5. Le numéro de référence (champ UNB5.2) peut comporter jusqu'à 14 caractères, le préfixe et le suffixe 13 (respectivement, champs UNB5.1 et UNB5.3). Les trois champs combinés peuvent contenir jusqu'à 14 caractères.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, rétablissez le champ du numéro de référence (UNB5.2) du numéro de contrôle de l'échange en procédant comme suit :  
  
1.  Dans la boîte de dialogue Propriétés globales EDI, ouvrez la page Définition du segment UNB.  
  
2.  Cliquez sur le champ d'édition associé au champ UNB5.  
  
3.  Définissez le champ du milieu du numéro de contrôle de l'échange (le numéro de référence dans UNB5.2) sur une nouvelle valeur de manière à ce que le nombre de chiffres pour ce champ soit acceptable.