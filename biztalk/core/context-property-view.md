---
title: "Vue propriété de contexte | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Tracking Profile Editor, message schemas
- Context Property view [Tracking Profile Editor]
- Tracking Profile Editor, Context Property view
- message schemas, XML messages
ms.assetid: 17a21b86-995c-4dc2-9a3c-1309837d0b9b
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 84a0f3a1d507e1440f67cd5f9e4afa18bff0b52a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="context-property-view"></a>Vue Propriété de contexte
La vue Propriété de contexte affiche le schéma du message XML associé à la propriété. Cette vue peut s'afficher à partir du menu contextuel de certaines des formes de la vue de planification d'orchestration.  
  
## <a name="working-with-the-context-property-view"></a>Utilisation de la vue Propriété de contexte  
 Vous sélectionnez votre affichage de la propriété de contexte en cliquant sur le **Source d’événement sélectionnez** bouton et en cliquant sur le **sélectionner la propriété de contexte** élément de menu. Sélectionnez ensuite une propriété de contexte dans la liste des propriétés de contexte connues pour charger le schéma correspondant à cette propriété. Une fois la propriété sélectionnée, vous pouvez faire glisser des éléments du schéma associé vers les dossiers des éléments de données de l'activité, indiquant ainsi que vous souhaitez extraire ces données de l'expression XPath contenue dans le message associé à l'action.  
  
 Vous pouvez ouvrir les vues de propriété de contexte à partir de la vue de la planification d'orchestration en cliquant avec le bouton droit sur une forme contenant une propriété de contexte. S’ouvre un menu contextuel à partir de laquelle vous pouvez cliquer sur le **schéma de propriété de contexte** élément de menu à récupérer la liste des propriétés de contexte associé à la forme.  
  
 La liste des propriétés de contexte disponibles peut être longue. Si vous connaissez une partie du nom de la propriété que vous recherchez, vous pouvez la taper dans le **dans la chaîne** zone de texte et cliquez sur le **recherche** bouton. Ainsi, seules les propriétés contenant la partie de la chaîne que vous avez entrée seront sélectionnées.  
  
> [!NOTE]
>  Lorsque vous choisissez d'effectuer des mappages de la vue Propriétés de contexte, la liste des schémas de propriété potentiels est une liste complète de tous les schémas de propriété qui ont été configurés dans votre installation BizTalk Server.  Vous devez savoir que les schémas présentés ne tiennent pas compte des fonctionnalités BizTalk Server utilisées par le processus en cours d'exécution sur lequel vous travaillez. Vous pouvez par exemple sélectionner un schéma pour des propriétés SOAP dans la liste de schémas proposée lors d'un mappage à partir des propriétés de contexte, mais, de son côté, le processus en cours d'exécution ne pourra pas utiliser SOAP. Tout élément d'activité BAM mappé à partir d'une propriété inutilisée entraîne la capture de données nulles ou vides par l'analyse BAM.  
  
## <a name="see-also"></a>Voir aussi  
 [Nouveautés de la vue ?](../core/what-is-the-source-event-view.md)   
 [Éditeur de modèle de suivi](../core/tracking-profile-editor.md)