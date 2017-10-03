---
title: "La limite maximale acceptable X12 numéro de contrôle de groupe fonctionnel a été atteinte pour les paramètres invité | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 05cba774-fa35-4694-aa34-d7151f8cd75c
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3210fb773b7093c2e28f98e0cf1aa223e1a63936
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="max-limit-of-acceptable-x12-functional-group-control-number-has-reached-for-guest-settings"></a>La limite maximale acceptable pour le numéro de contrôle du groupe fonctionnel X12 a été atteinte pour les paramètres Invité.
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|ID d'événement|-|  
|Source de l'événement|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI|  
|Composant|Moteur EDI|  
|Nom symbolique|GlobalEdifactUnhNumberError|  
|Texte du message|La limite maximale du numéro de contrôle du groupe fonctionnel X12 acceptable pour les paramètres Invité. Réinitialisez le compteur en naviguant jusqu'au champ GS 6 de l'écran du rôle de destinataire de la configuration globale dans le gestionnaire d'accords partenaires.|  
  
## <a name="explanation"></a>Explication  
 Cet événement de type erreur/avertissement/information indique que le pipeline d'envoi n'a pas pu traiter l'échange X12 sortant, car le numéro de contrôle du groupe du champ GS06 défini dans les paramètres globaux était supérieur à la valeur maximum autorisée. Le nombre maximal de caractères du numéro de contrôle du groupe est 9.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, rétablissez le numéro de contrôle du groupe en procédant comme suit :  
  
1.  Dans la boîte de dialogue Propriétés globales EDI, ouvrez la page de définition des segments GS et ST.  
  
2.  Cliquez sur le champ d'édition associé au champ GS06.  
  
3.  Définissez le numéro de contrôle du groupe sur une nouvelle valeur de manière à ce que le nombre de chiffres pour ce champ soit inférieur ou égal à neuf.