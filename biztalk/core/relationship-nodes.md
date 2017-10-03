---
title: "Nœuds de relation | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- definition files [BAM], relationships
- definition files [BAM], Tracking Profile Editor
- Relationship nodes [Tracking Profile Editor]
- activities [BAM], relationships
- activities [BAM], Tracking Profile Editor
- Tracking Profile Editor, node descriptions
- Tracking Profile Editor, definition files [BAM]
ms.assetid: 74090133-24d1-4aba-a4fc-f12d19c881fb
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f670c62b4e883b124d849ab61396f6f5216e7182
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="relationship-nodes"></a>Nœuds de relation
Des dossiers de relations sont utilisés chaque fois qu'un fichier de définition d'activité contient plus d'une activité. Le nom des dossiers correspond au nom de l'activité associée. Vous établissez le lien en faisant correspondre le nom du dossier de relation à l'ID de l'activité correspondante, ainsi que les valeurs des éléments de données. Chaque relation doit être définie à l'aide d'un nœud spécifique.  
  
## <a name="working-with-relationship-nodes"></a>Utilisation des nœuds de relation  
 Pour spécifier l'identificateur d'instance unique qui relie les éléments de données entre plusieurs activités :  
  
-   Mappez un élément de données au nœud ActivityId de l'orchestration principale.  
  
-   Faites glisser un élément de données portant le même nom et déposez-le sur le nœud de relation de l'activité correspondante. Le nœud de relation porte le même nom que le nœud de l'activité principale.  
  
 Ainsi, dans le scénario proposé, il peut exister un processus d'entreprise lié mais distinct représenté dans une orchestration intitulée RefinanceOrchestration. Cette orchestration peut contenir un nœud d'activité LoanRefinance, un ID d'activité Refinance et des formes d'orchestration telles que Recevoir une requête d'évaluation. Le nœud et l'ID de relation, cependant, peuvent être intitulés LoanID, ce qui indique un lien vers l'activité d'origine LoanProcess.  
  
## <a name="see-also"></a>Voir aussi  
 [Nœuds de l’activité TPE](../core/tpe-activity-view-nodes.md)