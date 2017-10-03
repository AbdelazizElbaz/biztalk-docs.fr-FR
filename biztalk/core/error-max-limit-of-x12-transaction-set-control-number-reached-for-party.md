---
title: "La limite maximale acceptable X12 document informatisé a été atteinte pour le tiers | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a402f6d0-4399-47c9-a39a-56d7fa1efa86
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3c46a221e0e69d159ee1f5d8cdeee0e0c31389e5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="max-limit-of-acceptable-x12-transaction-set-control-number-has-reached-for-party"></a>La limite maximale du numéro de contrôle du document informatisé X12 acceptable a été atteinte pour le tiers
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|ID d'événement|-|  
|Source de l'événement|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI|  
|Composant|Moteur EDI|  
|Nom symbolique|PartyX12TsNumberError|  
|Texte du message|La limite maximale du numéro de contrôle de document informatisé X12 acceptable a été atteinte pour le tiers {0}. Pour réinitialiser le compteur, naviguez jusqu'au tiers dans l'écran du rôle de destinataire, champ ST 2 dans le gestionnaire d'accords partenaires|  
  
## <a name="explanation"></a>Explication  
 Cet événement d'erreur/d'avertissement/d'informations indique que le pipeline d'envoi n'a pas pu traiter l'échange X12 sortant car le numéro de contrôle du document informatisé (champ ST02) spécifié dans les paramètres du tiers, notamment le numéro de référence (champ ST02.2), est supérieur à la valeur maximale autorisée. La valeur maximale autorisée pour le numéro de contrôle d'un document informatisé dépend des valeurs des trois champs dans ST02. Le numéro de référence (champ ST02.2) peut comporter jusqu'à 9 caractères, le préfixe et le suffixe 8 (respectivement, champs ST02.1 et ST02.3). Les trois champs combinés peuvent contenir jusqu'à 9 caractères.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, rétablissez le champ du numéro de référence (UNH1.2) du numéro de contrôle du document informatisé en procédant comme suit :  
  
1.  Dans la boîte de dialogue Propriétés EDI associée au tiers auquel l'échange correspond, ouvrez la page Définition des segments UNG et UNH.  
  
2.  Cliquez sur le champ d'édition associé au champ UNH1.  
  
3.  Définissez le champ du milieu du numéro de contrôle du document informatisé (le numéro de référence dans UNH1.2) sur une nouvelle valeur de manière à ce que le nombre de chiffres pour ce champ soit acceptable.