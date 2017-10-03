---
title: "À l’aide des fonctoids pour créer des mappages plus complexes | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7d53e3a3-5ccd-4733-8c2f-3101e41fca61
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 736b6fa99844182c59db582182056faea1d3f322
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="using-functoids-to-create-more-complex-mappings"></a>Utilisation de fonctoids pour créer des mappages plus complexes

## <a name="overview"></a>Vue d'ensemble
Les fonctoids jouent un rôle essentiel dans de nombreux scénarios de mappage. Sans les fonctoids, vous pouvez copier des données d'éléments et d'attributs, mais vous ne pouvez pas vraiment manipuler les valeurs elles-mêmes. Les fonctoids autorisent presque toutes les transformations. Par exemple, à l'aide d'un fonctoid, vous pouvez prendre deux valeurs issues de deux emplacements complètement différents, les ajouter et placer le résultat dans le schéma de destination.  
  
 Les fonctoids apparaissent dans la boîte à outils [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], un onglet de boîte à outils par catégorie, lorsque vous modifiez un mappage BizTalk. Une fois que vous avez ouvert la boîte à outils et choisi une catégorie de fonctoids en cliquant sur l'onglet correspondant, faites glisser votre fonctoid sur une page de grille. Créez ensuite des liens d'entrée et de sortie entre le fonctoid et l'un ou l'autre des nœuds de schéma ou un autre fonctoid. Les liens d'entrée correspondent aux paramètres d'entrée et conduisent à un fonctoid à partir de la gauche. Quant au lien de sortie, il correspond au paramètre de sortie et abandonne le fonctoid par la droite.  
  
 Tout comme d'autres éléments de mappage, les fonctoids ont des propriétés. L'une des propriétés les plus importantes des fonctoids est leur ensemble de paramètres d'entrée. Pour plus d’informations, consultez [comment ajouter des fonctoids à un mappage](../core/how-to-add-basic-functoids-to-a-map.md).  
  
 Cette section contient des instructions détaillées concernant l'utilisation de fonctoids dans les mappages BizTalk. Pour plus d’informations de référence sur les fonctoids, consultez le **référence du fonctoid** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].
  
## <a name="next-steps"></a>Étapes suivantes 
  
-   [Comment ouvrir la boîte à outils des fonctoids](../core/how-to-open-the-functoid-toolbox.md)  
  
-   [Ajout de fonctoids de base à une carte](../core/how-to-add-basic-functoids-to-a-map.md)  
  
-   [Ajout de fonctoids avancés à une carte](../core/adding-advanced-functoids-to-a-map.md)  
  
-   [Modification des propriétés des fonctoids et des paramètres d’entrée](../core/editing-functoid-properties-and-input-parameters.md)  
  
-   [Comment sélectionner plusieurs fonctoids](../core/how-to-select-multiple-functoids.md)  
  
-   [Comment supprimer des fonctoids](../core/how-to-delete-functoids.md)  
  
-   [Comment copier, couper et coller un fonctoid](../core/how-to-copy-cut-and-paste-a-functoid.md)