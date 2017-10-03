---
title: "La limite maximale du numéro de contrôle d’échange a été atteinte pour le tiers de X12 acceptable | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: adc49089-3c7b-4ce2-9fbc-68e582c3a822
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fba803260af4879e4e2a286c0f7864af7ccf2747
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="max-limit-of-acceptable-x12-interchange-control-number-has-reached-for-party"></a>La limite maximale du numéro de contrôle d'échange X12 acceptable a été atteinte pour le tiers
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|ID d'événement|-|  
|Source de l'événement|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI|  
|Composant|Moteur EDI|  
|Nom symbolique|PartyX12IsaNumberError|  
|Texte du message|La limite maximale du numéro de contrôle d'échange X12 acceptable a été atteinte pour le tiers {0}. Réinitialisez le compteur en naviguant jusqu'au tiers dans l'écran du rôle du destinataire, champ ISA 13 dans le gestionnaire d'accords partenaires|  
  
## <a name="explanation"></a>Explication  
 Cet événement d'erreur/d'avertissement/d'informations indique que le pipeline d'envoi n'a pas pu traiter l'échange x12 sortant car le numéro de contrôle (champ ISA13) spécifié dans les paramètres de tiers est supérieur à la valeur maximale autorisée. Le nombre maximal de caractères d'un numéro de contrôle de l'échange est neuf.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, rétablissez le numéro de contrôle de l'échange en procédant comme suit :  
  
1.  Dans la boîte de dialogue Propriétés EDI associée au tiers auquel l'échange correspond, ouvrez la page Définition du segment ISA pour le tiers en tant que récepteur d'échanges.  
  
2.  Cliquez sur le champ d'édition associé au champ ISA13.  
  
3.  Définissez le numéro de contrôle de l'échange sur une nouvelle valeur de manière à ce que le nombre de chiffres pour ce champ soit acceptable.