---
title: "Validation des propriétés de contrat | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9d565c26-37ef-4aee-aebb-3152880242a1
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 20c01ec281005cbeaffda6dcd2349c1153a531b1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="agreement-properties-validation"></a>Validation des propriétés de l'accord
Les propriétés de l'accord incluent la détection de doublons de numéros de contrôle d'échanges, de groupes ou de documents informatisés. Le pipeline de réception EDI effectue ces validations seulement si elles sont activées dans les propriétés de l'accord. Ces validations sont :  
  
-   Vérifier la présence de numéro de contrôle d'échange en double (ISA13 dans X12 ou UNB5 dans EDIFACT). Vous entrez une valeur de temps (en jours) pour définir une plage horaire valide pour cette vérification.  
  
-   Vérifier la présence de numéro de contrôle du groupe en double dans un échange (GS6 dans X12 ou UNG5 dans EDIFACT)  
  
-   Vérifier la présence de numéro de contrôle du document informatisé en double dans un groupe fonctionnel (ST2 dans X12 ou UNH1 dans EDIFACT)  
  
## <a name="see-also"></a>Voir aussi  
 [Validation des messages EDI](../core/edi-message-validation.md)