---
title: "Nœuds d’élément de données | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- definition files [BAM], data items
- Data Item nodes [Tracking Profile Editor]
- Tracking Profile Editor, node descriptions
- Tracking Profile Editor, definition files [BAM]
ms.assetid: 95856bfa-90e3-49d9-b55b-5f1b35a23f78
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a968bf7533697922938eeb8953f17813c77147c2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="data-item-nodes"></a>Nœuds d'élément de données
Les nœuds d'élément de données figurent dans le fichier de définition d'activité que le développeur importe à partir du modèle observation créé par l'analyste d'entreprise. L'Éditeur de modèle de suivi les nomme (Customer Name par exemple) pour les éléments de données dont ils assurent le suivi. Vous devez ensuite déplacer un ou plusieurs éléments de données de l'affichage de schéma de message vers le nœud qui correspond à Customer Name.  
  
## <a name="working-with-data-item-nodes"></a>Utilisation de nœuds d'élément de données  
 Lorsque vous mappez des nœuds d'élément de données, nous vous recommandons de n'effectuer le suivi des éléments de données qu'une seule fois par processus d'entreprise si le processus d'entreprise concerné englobe plusieurs modèles de suivi. Si votre orchestration comporte un chemin conditionnel, vous pouvez sélectionner l'élément de données dans les deux chemins car un seul sera exécuté. Cela étant, évitez de choisir une forme au sein d'une boucle à moins de savoir que les valeurs de l'élément de données varieront à chaque itération.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment mapper des données de l’élément](../core/how-to-map-item-data.md)   
 [Nœuds de l’activité TPE](../core/tpe-activity-view-nodes.md)