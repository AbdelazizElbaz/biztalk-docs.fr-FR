---
title: "Nœuds événement commercial | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- events, Tracking Profile Editor
- events, date specific
- events, time specific
- Tracking Profile Editor, node descriptions
- Business Event nodes [Tracking Profile Editor]
- Tracking Profile Editor, events
ms.assetid: 177bc3c4-e762-42fe-80bc-edede5cd4fcd
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 44c3d06e553f129abb36eb53c4dde9c5ab9c25f7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="business-event-nodes"></a>Nœuds Événement commercial
Les nœuds Événement commercial ou nœuds d'étape majeure définissent des événements correspondant à des dates ou des heures spécifiques. Les dossiers prédéfinis pour un événement commercial ou pour une étape majeure se trouvent dans la définition d'activité importée de l'utilisateur final. Il vous est impossible de les supprimer sans réimporter le fichier de définition d'activité.  
  
## <a name="working-with-business-event-nodes"></a>Utilisation des nœuds d'événements commerciaux  
 Vous pouvez faire glisser des formes de l'orchestration dans le dossier des événements commerciaux afin d'effectuer le suivi de ces événements une fois l'exécution des formes terminée.  
  
 L'Éditeur de modèle de suivi utilise le nom de la forme pour nommer le dossier d'événements, auquel est attribuée une icône unique. Dans l'exemple du processus de prêt, l'Éditeur de modèle de suivi nomme les dossiers d'événements en fonction de l'événement concerné : Approuvé, Refusé, etc. Nous vous recommandons de n'effectuer le suivi des événements commerciaux qu'une seule fois par processus d'entreprise si le processus d'entreprise concerné englobe plusieurs modèles de suivi. Si votre orchestration comporte un chemin conditionnel, vous pouvez sélectionner l'événement commercial en utilisant les deux chemins. En effet, un seul est effectivement exécuté. Vous ne devez pas sélectionner une forme à l'intérieur d'une boucle.  
  
> [!NOTE]
>  Il est impossible de supprimer des dossiers sans réimporter la définition d'activité. En revanche, vous pouvez parfaitement supprimer des formes (événements).  
  
## <a name="see-also"></a>Voir aussi  
 [Nœuds de l’activité TPE](../core/tpe-activity-view-nodes.md)