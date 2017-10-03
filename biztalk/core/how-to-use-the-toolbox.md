---
title: "L’utilisation de la boîte à outils | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- creating, pipelines
- pipeline components, deleting from toolbox
- pipeline components, Pipeline Designer
- pipeline components, adding to toolbox
- Pipeline Designer, toolbox
- pipelines, creating
ms.assetid: 7a60c590-1a38-46fe-addf-0aa2c8b63cf9
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3965a063aebcc932f07937fd19c3998412591ea1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-use-the-toolbox"></a>Utilisation de la boîte à outils
Pour créer un pipeline, il faut glisser des composants (formes) de la boîte à outils jusqu'à la surface de conception. Le Concepteur de pipeline vous aide à assembler des pipelines valides en soumettant le processus de création à certaines restrictions. Vous ne pouvez sélectionner que des composants de boîte à outils qui s'appliquent au type de pipeline que vous êtes en train de créer. Ainsi, un pipeline de réception affichera les décodeurs, désassembleurs et valideurs comme des composants de boîte à outils valides, tandis que les encodeurs et les assembleurs seront désactivés (apparaissant de façon grisée).  
  
 De plus, les phases ne peuvent accepter que des composants valides. Il est par exemple impossible de glisser un composant d'encodeur sur une phase d'assemblage. Lorsque vous faites glisser un composant près d'un emplacement de dépôt valide, une flèche apparaît, indiquant l'endroit où le composant peut être inséré.  
  
 Si vous faites glisser un composant valide sur une phase réduite, laissez-y la souris quelques secondes pour la développer, puis déposez-y le composant.  
  
 L'ajout d'un composant personnalisé à la boîte à outils dans le Concepteur de pipeline est similaire à la procédure standard Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].  
  
 **Formes début et fin**  
  
 **Démarrer** et **fin** formes apparaissent sous forme de puces dans tous les pipelines. Elles sont représentées sur la surface de conception à des fins d'organisation visuelle uniquement. Il n'y a qu'un exemplaire de chacune et elles ne peuvent être ni ajoutées ni supprimées. Le **Démarrer** et **fin** formes n’apparaissent pas dans la boîte à outils.  
  
### <a name="to-add-a-pipeline-component-to-the-toolbox"></a>Pour ajouter un composant de pipeline à la boîte à outils  
  
1.  Dans le menu **Outils** , cliquez sur **Choisir des éléments de boîte à outils**.  
  
     — Ou :  
  
     Avec le bouton droit de la boîte à outils, puis cliquez sur **choisir des éléments de**.  
  
2.  Dans le **personnaliser la boîte à outils** boîte de dialogue, cliquez sur le **composants de Pipeline BizTalk** onglet.  
  
     Une boîte de dialogue affiche les composants de pipeline compatibles. Vous pouvez naviguer dans les différentes catégories en cliquant sur les onglets de la partie supérieure de cette boîte de dialogue.  
  
3.  Sélectionnez le composant que vous souhaitez ajouter à la boîte à outils.  
  
4.  Cliquez sur **OK**. Le composant s’affiche dans le **composants de Pipeline BizTalk** onglet de la boîte à outils.  
  
### <a name="to-remove-a-pipeline-component-from-the-toolbox"></a>Pour supprimer un composant de pipeline de la boîte à outils  
  
-   Ouvrez le **personnaliser la boîte à outils** boîte de dialogue (comme dans la procédure précédente) et désactivez le composant à supprimer.  
  
     Les composants restent inscrits même après leur suppression de la boîte à outils.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment créer un Pipeline](../core/how-to-create-a-new-pipeline.md)   
 [Comment ouvrir un Pipeline](../core/how-to-open-a-pipeline.md)   
 [Comment accéder à l’aide du clavier](../core/how-to-navigate-with-the-keyboard.md)   
 [Création de Pipelines avec le Concepteur de Pipeline](../core/creating-pipelines-with-pipeline-designer.md)