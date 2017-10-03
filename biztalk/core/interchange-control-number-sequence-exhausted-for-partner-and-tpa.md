---
title: "Contrôle séquence du numéro de l’échange pour le partenaire et TPA | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e77c0574-bc51-4690-a7f6-5702f6486f05
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b4744a8db00985db3e85c1cb8843f07b3488544b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="interchange-control-number-sequence-exhausted-for-partner-and-tpa"></a>La séquence du numéro de contrôle de l'échange pour le partenaire et l'accord de partenariat commercial est épuisée
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|ID d'événement|-|  
|Source de l'événement|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI|  
|Composant|Moteur EDI|  
|Nom symbolique|EdiControlNumberExhaustedForParty|  
|Texte du message|Séquence du numéro de contrôle échange atteint pour le partenaire « {{1} » pour la « {{2} » est Épuisée. Rétablissez la séquence dans {{2} - propriétés EDI à l’aide de la console Administration de BizTalk Server.|  
  
## <a name="explanation"></a>Explication  
 Cet événement d’erreur/avertissement/Information indique que BizTalk Server n’a pas pu traiter le document, car la plage de contrôle d’échange est épuisée pour l’accord dans {{2}.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, cochez la case à cocher pour rétablir le numéro de contrôle de l’accord {2} ou augmentez la plage de numéros de contrôle ou le bouton Réinitialiser par rapport à la spécification de plage numéro de contrôle d’accès dans l’accord.