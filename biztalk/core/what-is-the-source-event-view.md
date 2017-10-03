---
title: "Qu'est-ce que la vue de la source d'événements ? | Microsoft Docs"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Tracking Profile Editor, Source Event view
- Source Event view [Tracking Profile Editor]
- message schemas, Tracking Profile Editor
- orchestrations, Tracking Profile Editor
- Tracking Profile Editor, message schemas
- Tracking Profile Editor, orchestrations
ms.assetid: 72e74780-8590-484b-899d-cdc3d2a908be
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e2437d2effe2fa03078e7f92fdb06f378c9e7cac
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="what-is-the-source-event-view"></a>Qu'est-ce que la vue de la source d'événements ?
La vue de la source d'événements est l'emplacement où l'Éditeur de modèle de suivi (TPE) présente les orchestrations ou les schémas de messages sélectionnés à partir des assemblys ou des propriétés de contexte que vous mappez à la définition d'activité.  
  
 Cette vue se trouve dans le volet droit de l'interface utilisateur. Le contenu de ce volet varie en fonction de la source de données sélectionnée.  
  
## <a name="event-source-options"></a>Options liées aux sources d'événements  
 Vous disposez de quatre options pour les sources d’événements : les planifications d’orchestration, les charges de messagerie, les propriétés de contexte et les propriétés de messagerie.  
  
 Les orchestrations et les charges de messagerie nécessitent la sélection d'un assembly à partir duquel vous effectuez le mappage des éléments de données. Vous sélectionnez ensuite les orchestrations ou schémas de charges de message spécifiques qui vous intéressent à partir de l'assembly. Pour les planifications d'orchestration, vous obtenez la liste des orchestrations de l'assembly. Les charges de messagerie vous permettent de faire votre choix dans une liste de schémas tandis que les propriétés de contexte présentent une liste de schémas dans l'assembly et dans les schémas système publics.  
  
 Lorsque vous sélectionnez des propriétés de contexte, vous obtenez tout d'abord une liste de noms de propriétés de contexte. Lorsque vous sélectionnez une propriété de contexte, le schéma qui lui est associé s'affiche dans le volet droit. Vous pouvez alors mapper la propriété de contexte à votre activité, en la faisant glisser vers le nœud d'activité souhaité.  
  
 Lorsque vous sélectionnez des propriétés de messagerie, vous obtenez la liste des propriétés de messagerie connues, que vous pouvez ensuite mapper à l'activité souhaitée.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Vue de planification d’orchestration](../core/orchestration-schedule-view.md)  
  
-   [Affichage de la charge de messagerie](../core/messaging-payload-view.md)  
  
-   [Vue propriété de contexte](../core/context-property-view.md)  
  
-   [Vue propriété de messagerie](../core/messaging-property-view.md)