---
title: Mise en évidence des éléments de la carte | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a2732b36-ca57-4566-ba26-da27a3082f32
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d6bb03969a044c6a474f5d2d1c1e5e1a5067cf81
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/23/2018
---
# <a name="how-to-emphasize-map-items"></a>Mise en évidence des éléments de mappage
Dans le Mappeur BizTalk, lorsque vous sélectionnez un élément de mappage, tous les liens et fonctoids associés sont mis en évidence. Cela est utile dans les mappages comprenant de nombreux liens, où il est difficile d'identifier une relation et les éléments de schéma associés.  
  
 Lorsque vous sélectionnez un lien, un fonctoid ou un élément de schéma, le Mappeur BizTalk met en évidence la relation et les éléments de schéma. Pour l'élément de mappage sélectionné, l'ensemble des liens entrants et sortants sont mis en gras (de manière récursive) et tous les autres éléments de mappage sont grisés. La capture d'écran suivante montre l'élément de mappage sélectionné en gras et en couleur, et les autres éléments de façon moins distincte.  
  
> [!NOTE]
>  Dans ce contexte, une relation associée signifie que l'ensemble des liens, fonctoids ou éléments de schéma sont directement ou indirectement liés à l'élément de mappage sélectionné.  
  
 ![Mettre en évidence un élément cartographique](../core/media/mapper-intelliselect.gif "Mapper_IntelliSelect")  
  
## <a name="prerequisites"></a>Configuration requise  
 Cette opération nécessite l'exécution du Mappeur BizTalk.  
  
## <a name="to-emphasize-a-map-item"></a>Pour mettre en évidence un élément de mappage  
  
-   Cliquez sur un élément de mappage (lien, fonctoid ou élément de schéma). Vous pouvez voir que tous les autres liens et fonctoids (y compris les nœuds de schéma) associés à l'élément de mappage sélectionné dans la page de grille active sont en évidence.  
  
     Parfois, pour le nœud sélectionné, il peut y avoir des relations existantes dans d'autres pages de grille. Dans ce cas, le Mappeur BizTalk met en évidence l'instance dans la page de grille active, ainsi que l'onglet de la page où existe l'autre relation associée au nœud sélectionné.  
  
## <a name="see-also"></a>Voir aussi  
 [À l’aide des fonctionnalités améliorées dans le Mappeur BizTalk](../core/using-enhanced-features-in-biztalk-mapper.md)