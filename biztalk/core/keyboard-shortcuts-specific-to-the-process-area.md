---
title: "Clavier raccourcis propres à la zone de processus | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- keyboard shortcuts, Orchestration Designer
- Orchestration Designer, keyboard shortcuts
ms.assetid: d993d341-99f2-4788-b1f3-6a8b911e5278
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ba60b23c6c8719789e8de6903dbb538fa5088b08
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="keyboard-shortcuts-specific-to-the-process-area"></a>Raccourcis clavier propres à la zone de processus
Le tableau suivant décrit les raccourcis clavier disponibles dans la zone de processus, à savoir la partie centrale de la surface de conception utilisée pour définir le flux des processus de l'orchestration.  
  
|Clé|Effet|  
|---------|------------|  
|Bas|Déplace la sélection vers la ligne de connexion ou forme suivante vers le bas. Si la forme est connectée à plusieurs branches situées en dessous (comme dans le cas d'une forme Décider), la sélection se déplace sur la première forme de la branche la plus à gauche.<br /><br /> Si la sélection se trouve sur la forme Fin de l'orchestration, ce raccourci est sans effet, car la forme Fin n'est suivie d'aucune autre forme.|  
|Flèche haut|Déplace la sélection vers la ligne de connexion ou forme suivante vers le haut. Si la forme est connectée à plusieurs branches situées au-dessus, la sélection se déplace sur la dernière forme de la branche la plus à gauche.<br /><br /> Ce raccourci n’a aucun effet lorsque les **Démarrer** forme est sélectionnée.|  
|Gauche|Si la sélection porte sur une forme Envoi ou Réception et que la forme soit connectée à un port :<br /><br /> -Si la forme comporte un connecteur de port pointant vers un port de la Surface du Port gauche, la sélection est déplacée vers le connecteur de port de la forme.<br />-Si la forme comporte un connecteur de port pointant vers un port de la Surface de Port de droite, ce raccourci n’a aucun effet.<br />-Si la forme ne comporte aucun connecteur de port, la navigation est identique à toute autre forme.<br /><br /> Pour toute autre forme (ou des formes Envoi ou Réception non connectées à un port) :<br /><br /> -Si la sélection se trouve dans une branche, et une branche existe avec les formes sur celui-ci vers la gauche de la branche active, la sélection se déplace vers la forme la plus proche de la branche vers la gauche.<br />-La clé est sans effet ailleurs dans l’orchestration.|  
|Flèche droite|Identique à la touche GAUCHE, mais dans la direction opposée.|  
|Origine|La sélection passe au connecteur sortant de la forme Début de l'orchestration.|  
|END|La sélection passe au connecteur entrant de la forme Fin de l'orchestration.|  
|VERR. NUM + -|Réduit la forme complexe sélectionnée.|  
|VERR. NUM + +|Développe la forme complexe sélectionnée.|  
|VERR. NUM + *|Développe la forme complexe sélectionnée, ainsi que les formes complexes enfants qu'elle pourrait contenir.|  
  
## <a name="see-also"></a>Voir aussi  
 [Raccourcis de clavier du Concepteur d’orchestration](../core/orchestration-designer-keyboard-shortcuts.md)