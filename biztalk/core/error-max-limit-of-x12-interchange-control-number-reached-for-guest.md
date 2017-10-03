---
title: "La limite maximale du numéro de contrôle d’échange a été atteinte pour les paramètres invité de X12 acceptable | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9737053d-6065-4c88-8dfa-5f69b48e0e82
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c72fc565367477d9dbd09f3c0d4c4f9d6ab686a8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="max-limit-of-acceptable-x12-interchange-control-number-has-reached-for-guest-settings"></a>Limite maximale du numéro de contrôle d’échange a été atteinte pour les paramètres invité de X12 acceptable
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|ID d'événement|-|  
|Source de l'événement|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI|  
|Composant|Moteur EDI|  
|Nom symbolique|GlobalX12IsaNumberError|  
|Texte du message|La limite maximale du numéro de contrôle acceptable de l'échange X12 a été atteinte pour les paramètres Invité Réinitialisez le compteur en naviguant jusqu'au champ ISA 13 de l'écran du rôle de destinataire de la configuration globale dans le gestionnaire d'accords partenaires|  
  
## <a name="explanation"></a>Explication  
 Cet événement d'erreur/d'avertissement/d'informations indique que le pipeline d'envoi n'a pas pu traiter l'échange x12 sortant car le numéro de contrôle (champ ISA13) spécifié dans les paramètres globaux est supérieur à la valeur maximale autorisée. Le nombre maximal de caractères d'un numéro de contrôle de l'échange est neuf.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, rétablissez le numéro de contrôle de l'échange en procédant comme suit :  
  
1.  Dans la boîte de dialogue Propriétés globales EDI, ouvrez la page Définition des segments ISA.  
  
2.  Cliquez sur le champ d'édition associé au champ ISA13.  
  
3.  Définissez le numéro de contrôle de l'échange sur une nouvelle valeur de manière à ce que le nombre de chiffres pour ce champ soit acceptable.