---
title: "Condition d’exclusion violée | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0e508da6-7edc-45c0-a7ab-f23337dc1b54
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f5a508c113daf628491837adee119649ac17b478
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="exclusion-condition-violated"></a>Condition d'exclusion non respectée
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|ID d'événement|-|  
|Source de l'événement|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI|  
|Composant|Moteur EDI|  
|Nom symbolique|X12DeExclusionConditionViolatedDescription|  
|Texte du message|Condition d'exclusion non respectée, pour plus de détails, consultez la valeur du champ dans l'instance|  
  
## <a name="explanation"></a>Explication  
 Cet événement de type erreur/avertissement/information indique que la validation d'un échange X12 a échoué, soit lors de la phase de conception (à l'aide de l'outil de validation XML) ou lors de l'exécution, côté réception ou envoi, car un segment dans l'instance n'a pas respecté une règle d'exclusion de validation de champ croisée.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, vérifiez que le segment qui n'a pas respecté la règle d'exclusion est modifié de sorte qu'il subisse avec succès la validation de champ croisée, puis réexécutez le processus de validation.