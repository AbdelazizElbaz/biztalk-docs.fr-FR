---
title: "Transaction jeu numérique séquence de contrôle pour le partenaire et TPA | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 67f194ca-3e0f-4ad4-8bc8-88aa7e5193a7
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 40d87b1f2681bb07816721971cfbd17d2c3a0b91
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="transaction-set-control-number-sequence-exhausted-for-partner-and-tpa"></a>La séquence du numéro de contrôle du document informatisé pour le partenaire et l'accord de partenariat commercial est épuisée
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|ID d'événement|-|  
|Source de l'événement|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI|  
|Composant|Moteur EDI|  
|Nom symbolique|EdiControlNumberExhaustedForParty|  
|Texte du message|Transaction jeu numéro séquence de contrôle pour le partenaire « {{1}' pour la « {{2} » est Épuisée. Rétablissez la séquence dans {{2} - propriétés EDI à l’aide de la console Administration de BizTalk Server.|  
  
## <a name="explanation"></a>Explication  
 Cet événement d’erreur/avertissement/Information indique que BizTalk Server n’a pas réussi à traiter que le document car la plage de contrôle de document informatisé est épuisé pour l’accord dans {{2}.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, cochez la case à cocher pour rétablir le numéro de contrôle de l’accord {2} ou augmentez la plage de numéros de contrôle ou le bouton Réinitialiser par rapport à la spécification de plage numéro de contrôle d’accès dans l’accord.