---
title: "Comment déplacer et copier des nœuds | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e4f1ec14-c607-4da3-9139-73a61963b819
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a55901e9ba6b27d05dccce0e547df618123ab466
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-move-and-copy-nodes"></a>Comment déplacer et copier des nœuds
Il vous arrivera probablement de vouloir déplacer un nœud existant vers un autre emplacement dans l'arborescence de schéma. Vous pourrez gagner du temps si vous effectuez une copie du nœud existant et que vous le collez à un autre endroit de l'arborescence de schéma. Cette rubrique contient des instructions détaillées pour exécuter ces tâches.  
  
> [!NOTE]
>  L'Éditeur BizTalk ne prend en charge la copie et le collage de nœuds qu'à l'intérieur des schémas et non pas d'un schéma à l'autre.  
  
### <a name="to-move-a-node-within-a-schema"></a>Pour déplacer un nœud dans un schéma  
  
1.  Si nécessaire, développez l'arborescence de schéma afin d'afficher le nœud que vous comptez déplacer et l'emplacement dans lequel vous souhaitez le placer. Pour plus d’informations sur le développement et réduction de l’arborescence du schéma, consultez [la gestion de l’arborescence du schéma](../core/how-to-manage-the-schema-tree-view.md).  
  
2.  Cliquez sur le nœud que vous voulez déplacer et maintenez le bouton de la souris enfoncé pour faire glisser le nœud vers un autre emplacement de l'arborescence.  
  
> [!NOTE]
>  Quand vous commencez à déplacer le nœud vers le haut ou le bas de l'arborescence de schéma, le pointeur de la souris se transforme en une flèche vers le haut ou vers le bas, ou en une flèche enfant. Cette flèche indique où le nœud sera placé lorsque vous relâcherez le bouton de la souris : avant le nœud, après le nœud ou en tant qu'enfant du nœud.  
  
#### <a name="to-copy-a-node-within-a-schema"></a>Pour copier un nœud dans un schéma  
  
1.  Cliquez sur le nœud que vous souhaitez copier, puis cliquez sur **copie**.  
  
2.  Cliquez sur le **enregistrement** nœud ou nœud de groupe dans lequel vous souhaitez insérer le nœud copié, puis cliquez sur **coller**.  
  
     La copie du nœud copié est placée à la fin des nœuds enfants de la **enregistrement** nœud ou nœud de groupe que vous avez sélectionné à l’étape 2.  
  
> [!NOTE]
>  Vous ne pouvez utiliser la fonctionnalité couper/copier/coller que dans un seul schéma. En d'autres termes, il est impossible de copier des nœuds d'un schéma à l'autre.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation des nœuds existants](../core/working-with-existing-nodes.md)