---
title: "La limite maximale du numéro de contrôle de groupe fonctionnel a été atteinte pour le tiers de X12 acceptable | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a920a66c-1e38-4f4a-8113-cbad01940839
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 91d9fd8cba9ca86627c1381917a107e3ade754e3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="max-limit-of-acceptable-x12-functional-group-control-number-has-reached-for-party"></a>La limite maximale du numéro de contrôle du groupe fonctionnel X12 acceptable a été atteinte pour le tiers
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|ID d'événement|-|  
|Source de l'événement|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI|  
|Composant|Moteur EDI|  
|Nom symbolique|PartyX12GsNumberError|  
|Texte du message|La limite maximale du numéro de contrôle du groupe fonctionnel X12 acceptable a été atteinte pour le tiers {0}. Réinitialisez le compteur en naviguant jusqu'au tiers dans l'écran du rôle de destinataire, champ GS 6 dans le gestionnaire d'accords partenaires|  
  
## <a name="explanation"></a>Explication  
 Cet événement d'erreur/d'avertissement/d'informations indique que le pipeline d'envoi n'a pas pu traiter l'échange sortant car le numéro de contrôle du groupe (champ GS06) spécifié dans les paramètres du tiers est supérieur à la valeur maximale autorisée. Le nombre maximal de caractères du numéro de contrôle du groupe est 9.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, rétablissez le numéro de contrôle du groupe en procédant comme suit :  
  
1.  Dans la boîte de dialogue Propriétés EDI associée au tiers auquel l'échange correspond, ouvrez la page Définition des segments GS et ST pour le tiers en tant que récepteur d'échanges.  
  
2.  Cliquez sur le champ d'édition associé au champ GS06.  
  
3.  Définissez le numéro de contrôle du groupe sur une nouvelle valeur de manière à ce que le nombre de chiffres pour ce champ soit inférieur ou égal à neuf.