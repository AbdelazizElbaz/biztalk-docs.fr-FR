---
title: "Nœuds Activity et ActivityID | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ActivityID nodes [Tracking Profile Editor]
- Activity nodes [Tracking Profile Editor]
- Tracking Profile Editor, node descriptions
- activities [BAM], definitions
ms.assetid: 94d4130a-53c5-4cd5-916a-4a6bd9acbf23
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d100c88eec5f5a05db2bb651968aa987e3ec4e33
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="activity-and-activityid-nodes"></a>Nœuds Activity et ActivityID
Les nœuds Activity et ActivityID sont utilisés pour contenir et identifier une définition d'activité. Le nœud Activity est le dossier parent destiné aux éléments de la définition d'activité. L'ensemble des éléments de donnée et des nœuds d'événements commerciaux figurent dans le nœud d'activité associé et lui sont subordonnés. Le nom du nœud Activity doit refléter le nom de l'activité elle-même.  
  
 Le nœud ActivityID est un élément généré automatiquement dans la définition d'activité et sert à contenir un identificateur unique pour l'activité. Il peut être utilisé pour effectuer le suivi des identificateurs fournis par l'utilisateur ou générés par le système. À titre d'exemple, dans un scénario dans lequel un numéro de bon de commande est l'identificateur unique de tous les bons de commande dans l'ensemble du système, vous pouvez utiliser ce numéro en tant qu'ActivityID et donc mapper la valeur de l'ActivityID à partir de n'importe quelle source d'événement, par exemple le champ de numéro de bon de commande figurant dans le schéma de bon de commande. Si la valeur de bon de commande n'est pas unique, vous n'êtes pas obligé de mapper le nœud et l'analyse BAM génèrera automatiquement des identificateurs uniques lors de l'exécution.  
  
 Les activités peuvent être associées à d'autres activités. Dans certains scénarios, ces relations font explicitement partie du modèle observation.  Plus particulièrement, lorsqu'une vue utilisateur comprend au moins deux activités, il existe une relation automatique entre ces activités.  Quand une telle relation existe, un nœud de relation est automatiquement créé dans l'arborescence d'activité sous le nœud Activity, pour chaque activité homologue connue. Dans les scénarios où l'on trouve une relation de données mais pas de vue d'ensemble, vous pouvez ajouter manuellement un nœud de relation à l'arborescence d'activité.  
  
 Dans les deux cas, le rôle du nœud de relation est de fournir un identificateur à l'activité associée. Par exemple, une relation plusieurs à plusieurs peut exister entre les bons de commandes et les livraisons (un seul bon de commande est honoré par plusieurs livraisons ; une livraison peut comporter un produit correspondant à plusieurs bons de commande).  L'enregistrement d'activité de chaque bon de commande peut contenir plusieurs pointeurs liés aux livraisons associées tandis que chaque enregistrement d'activité de livraison peut être pointé sur un ou plusieurs bons de commandes.  En termes de base de données, la valeur du nœud de relation est la clé étrangère de la table pour l'autre activité.  
  
## <a name="working-with-activity-id-nodes"></a>Utilisation des nœuds ActivityID  
 Par exemple, considérez le scénario suivant : l’orchestration EquityLoan contient le dossier d’activité LoanProcess. Elle fait référence à des événements commerciaux dont :  
  
-   LoanApplicationReceived                     
  
-   CHRequest  
  
-   CHResponse  
  
-   AppraisalRequest  
  
-   AppraisalResponse  
  
-   Approved  
  
-   Refusées  
  
 Le nœud ActivityID permet au développeur de solutions d'extraire les données qui identifient de manière unique l'activité, un numéro de bon de commande par exemple ou, dans le cas du scénario proposé, le champ SSN (social security number, numéro de sécurité sociale) du message. Si vous ne faites glisser aucune donnée vers le nœud ActivityID, un GUID généré automatiquement identifie les activités d'entreprise.  
  
 Pour définir la relation entre des événements commerciaux ou des étapes majeures dans diverses orchestrations, l'orchestration cible doit faire référence au nœud ActivityID. Pour plus d’informations sur l’implémentation des relations à l’aide de l’éditeur, consultez [nœuds de relation](../core/relationship-nodes.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Nœuds de l’activité TPE](../core/tpe-activity-view-nodes.md)