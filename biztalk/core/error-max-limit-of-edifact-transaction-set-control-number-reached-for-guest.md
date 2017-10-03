---
title: "La limite maximale de Edifact acceptable document informatisé a été atteinte pour les paramètres invité | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3924a18c-87bc-4727-b7cd-598d3e5ade2a
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 709d6069d143cea2271e6311fad571a0290133db
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="max-limit-of-acceptable-edifact-transaction-set-control-number-has-reached-for-guest-settings"></a>La limite maximale du nombre de contrôle d'ensembles de transactions Edifact a été atteinte pour les paramètres Invité.
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|ID d'événement|-|  
|Source de l'événement|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI|  
|Composant|Moteur EDI|  
|Nom symbolique|GlobalEdifactUnhNumberError|  
|Texte du message|La limite maximale du numéro de contrôle jeu de transactions Edifact acceptable a atteint pour les paramètres invité. Pour réinitialiser le compteur, accédez à la Configuration globale dans l'écran sur le rôle de récepteur, champ UNH 1 dans le gestionnaire d'accord partenaire|  
  
## <a name="explanation"></a>Explication  
 Cet événement de type erreur/avertissement/information indique que le pipeline d'envoi n'a pas pu traiter l'échange sortant, car le nombre de contrôle d'ensembles de transactions du champ UNH1 défini dans les paramètres globaux, notamment le numéro de référence du champ UNH1.2, était supérieur à la valeur maximum autorisée. La valeur maximum autorisée pour le numéro de contrôle du groupe dépend des valeurs des trois champs dans UNH1. Le numéro de référence (champ UNH1.2) peut comporter jusqu'à 14 caractères, le préfixe et le suffixe 13 (respectivement, champs UNH1.1 et UNH1.3). Les trois champs combinés peuvent contenir jusqu'à 14 caractères.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, rétablissez le champ du numéro de référence (UNH1.2) du numéro de contrôle du document informatisé en procédant comme suit :  
  
1.  Dans la boîte de dialogue Propriétés globales EDI, ouvrez la page Définition des segments UNH.  
  
2.  Cliquez sur le champ d'édition associé au champ UNH1.  
  
3.  Définissez le champ du milieu associé au numéro de contrôle du groupe (le numéro de référence dans UNH1.2) sur une nouvelle valeur, en faisant en sorte que le champ présente un nombre acceptable de chiffres.