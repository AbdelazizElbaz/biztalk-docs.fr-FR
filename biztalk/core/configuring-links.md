---
title: Configuration des liens | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 10050c28-0944-4073-afd2-54cd6c8d79a2
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e3da50b626eeb65a137deb8a1a7ef4f2ee3e0609
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-links"></a>Configuration des liens

## <a name="overview"></a>Vue d'ensemble
Les liens sont associés à des propriétés qui apparaissent dans la fenêtre de propriétés de [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] lorsqu'un lien est sélectionné dans la pages de grille affichée. Pour plus d’informations de référence sur les propriétés associées à des liens, consultez **propriétés des liaisons** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]. 

## <a name="source-target-and-label"></a>Source, cible et étiquette  
 Les propriétés suivantes correspondent à la configuration de liens d'un mappage :  
  
-   **Liaisons sources**. Vous utilisez la **liaisons sources** propriété pour configurer la nature des données à partir d’un message d’instance d’entrée qui servira à construire le message d’instance de sortie. Le choix par défaut, également le plus courant, consiste à utiliser la valeur d'élément ou d'attribut provenant du message d'instance d'entrée. D'autres solutions sont possibles, par exemple l'utilisation du nom de l'élément ou de l'attribut provenant du message d'instance d'entrée. Pour plus d’informations sur cette propriété et de son choix disponibles, consultez **propriétés des liaisons** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].
  
-   **Liaisons cibles**. Vous utilisez la **liaisons cibles** propriété pour configurer la façon dont le Mappeur BizTalk correspond à des niveaux de hiérarchie de nœuds. Par défaut, les hiérarchies de schéma source sont mises à plat lors de la création du message d’instance de sortie. Vous pouvez également choisir de conserver les hiérarchies, en établissant une correspondance des liens, du haut vers le bas ou du bas vers le haut. Pour plus d’informations sur cette propriété et de son choix disponibles, consultez **propriétés des liaisons** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].
  
-   **Étiquette**. Vous utilisez la **étiquette** propriété pour créer un nom plus lisible pour le lien à la valeur XPath qui est utilisé par défaut. Il est particulièrement utile de configurer cette propriété lorsque le lien est utilisé comme entrée de bouclage piloté par la table. Pour plus d’informations sur cette propriété et de son choix disponibles, ainsi que sur le bouclage piloté par table, consultez **propriétés des liaisons** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]. Consultez également [bouclage de Table et de fonctoids Extracteur de Table](../core/table-looping-and-table-extractor-functoids.md), respectivement.  
  
## <a name="see-also"></a>Voir aussi  
  [Procédure : modifier les propriétés de lien](../core/how-to-edit-link-properties.md)