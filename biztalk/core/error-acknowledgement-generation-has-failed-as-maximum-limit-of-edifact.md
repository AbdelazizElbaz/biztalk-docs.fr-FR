---
title: "Génération de l’accusé de réception a échoué car la limite maximale du numéro de contrôle de jeu de transactions Edifact a été atteinte pour les paramètres globaux | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6adc02d7-ebc4-4da0-a19a-3a423d63499d
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 252f0fd6dbe77eb83018e2bb34d4a6cd07cdbdf2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="acknowledgement-generation-has-failed-as-maximum-limit-of-edifact-transaction-set-control-number-has-been-reached-for-global-settings"></a>Un accusé de réception n'a pas pu être généré car la limite maximale du numéro de contrôle d'un document informatisé EDIFACT a été atteinte pour les paramètres globaux.
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|ID d'événement|-|  
|Source de l'événement|[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] EDI|  
|Composant|Moteur EDI|  
|Nom symbolique|-|  
|Texte du message|Un accusé de réception n'a pas pu être généré car la limite maximale du numéro de contrôle du document informatisé EDIFACT acceptable a été atteinte pour les paramètres Invité. Réinitialisez le compteur en naviguant jusqu'au champ UNH 1 de l'écran du rôle de l'expéditeur de la configuration globale dans le gestionnaire d'accords partenaires.|  
  
## <a name="explanation"></a>Explication  
 Cet événement d'erreur/d'avertissement/d'informations indique que BizTalk Server n'a pas pu générer un accusé de réception pour l'échange EDIFACT, car le numéro de contrôle qu'il a entré dans le numéro de référence du document informatisé (UNH1) de l'accusé de réception est supérieur à la valeur maximale autorisée pour UNH1. Dans cette instance, BizTalk Server a créé l'accusé de réception à l'aide des propriétés globales EDI.  
  
 La valeur maximale du numéro de référence du document informatisé dépend du nombre de chiffres utilisés pour le numéro de référence. Le numéro de référence peut comporter jusqu'à 14 caractères, le préfixe et le suffixe 13. Les trois champs combinés peuvent contenir jusqu'à 14 caractères.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, dans la page Définition des segments UNG et UNH, rétablissez le champ du numéro de référence (UNH1.2) du numéro de référence du document informatisé (UNH1) sur une valeur inférieure à la limite maximale. Définissez cette propriété dans la boîte de dialogue Propriétés globales EDI de la console Administration de [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)].