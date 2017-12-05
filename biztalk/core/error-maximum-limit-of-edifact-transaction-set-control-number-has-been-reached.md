---
title: "Génération de l’accusé de réception a échoué car la limite maximale du numéro de contrôle de jeu de transactions Edifact a été atteinte pour les paramètres de tiers | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bcbb6374-0403-42b0-892b-b35157a2c74a
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 81b1095f4d8f3fa69e30e9e0af89b0010175d185
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="acknowledgement-generation-has-failed-as-maximum-limit-of-edifact-transaction-set-control-number-has-been-reached-for-party-settings"></a>Un accusé de réception n'a pas pu être généré car la limite maximale du numéro de contrôle d'un document informatisé EDIFACT a été atteinte pour les paramètres du tiers
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|ID d'événement|-|  
|Source de l'événement|EDI de BizTalk Server|  
|Composant|Moteur EDI|  
|Nom symbolique|-|  
|Texte du message|Un accusé de réception n'a pas pu être généré car la limite maximale du nombre de contrôle d'ensembles de transactions Edifact a été atteinte pour le tiers {0}. Pour réinitialiser le compteur, accédez au tiers dans l'écran du rôle d'émetteur, champ UNH 1 dans le gestionnaire d'accord partenaire.|  
  
## <a name="explanation"></a>Explication  
 Cet événement d'erreur/d'avertissement/d'informations indique que BizTalk Server n'a pas pu générer un accusé de réception pour l'échange EDIFACT, car le numéro de contrôle qu'il a entré dans le numéro de référence du document informatisé (UNH1) de l'accusé de réception est supérieur à la valeur maximale autorisée pour UNH1. Dans cette instance, BizTalk Server a créé l'accusé de réception à l'aide des propriétés de tiers EDI.  
  
 La valeur maximale du numéro de référence du document informatisé dépend du nombre de chiffres utilisés pour le numéro de référence. Le numéro de référence peut comporter jusqu'à 14 caractères, le préfixe et le suffixe 13. Les trois champs combinés peuvent contenir jusqu'à 14 caractères.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, dans la page Définition des segments UNG et UNH, rétablissez le champ du numéro de référence (UNH1.2) du numéro de référence du document informatisé (UNH1) sur une valeur inférieure à la limite maximale. Définissez cette propriété dans la boîte de dialogue Propriétés EDI dans la Console Administration de BizTalk Server.