---
title: Comment copier, couper et coller un fonctoid | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 825847e4-87db-4b40-8e5d-5b5b1c79c6de
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9af3662fb866eb09c1dcb2516279ca097cc998f6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-copy-cut-and-paste-a-functoid"></a>Coupage, copie et collage d'un fonctoid
La fonctionnalité copier/couper/coller du Mappeur BizTalk permet la réutilisation des fonctoids. Dans un mappage, vous pouvez copier, couper et coller un ou plusieurs fonctoids à partir d'une page de grille sur une autre. Cette rubrique contient des instructions détaillées pour effectuer ces opérations.  
  
 Vous pouvez faire appel à la fonctionnalité copier/coller lorsque vous souhaitez réutiliser des fonctoids. Lorsque vous souhaitez supprimer un fonctoid de son emplacement actuel pour le déplacer vers un nouvel emplacement, vous pouvez utiliser la fonctionnalité couper/coller.  
  
> [!IMPORTANT]
>  Lorsque vous choisissez de copier un fonctoid, le fonctoid en lui-même, son étiquette, ses commentaires, ses entrées constantes ainsi que les index d'espaces réservés sont copiés. De même, lorsque vous choisissez de couper un fonctoid, le fonctoid en lui-même, son étiquette, ses commentaires, ses entrées constantes ainsi que les index d'espaces réservés sont coupés. Toutefois, lorsque vous collez votre sélection (après l'avoir coupée), les liens orphelins sont supprimés et seul le fonctoid est conservé ; l'étiquette, les commentaires, les entrées constantes et les index d'espaces réservés ne sont pas conservés.  
  
 Si vous sélectionnez simplement un fonctoid, qu'il soit lié à un autre fonctoid ou à un nœud de schéma, lui seul est coupé ou copié, sans les liens. Si vous coupez un fonctoid qui est lié soit à d'autres fonctoids du mappage soit aux nœuds de schéma, les liens pointant vers ce fonctoid sont supprimés.  
  
 Vous pouvez copier/couper des fonctoids :  
  
-   Au sein de la même page de grille d'un mappage  
  
-   D'une page de grille à l'autre dans le même mappage  
  
-   entre instances de Visual Studio.  
  
 Vous pouvez annuler ou rétablir les opérations Couper et Coller. Pour plus d’informations, consultez [comment annuler ou rétablir les opérations de l’utilisateur](../core/how-to-undo-or-redo-user-operations.md).  
  
## <a name="prerequisites"></a>Conditions préalables  
 Les instructions suivantes requièrent que le Mappeur BizTalk est en cours d’exécution.  
  
### <a name="to-copy-and-paste-a-functoid"></a>Pour copier et coller un fonctoid  
  
1.  Dans l'Explorateur de solutions, ouvrez le projet BizTalk, puis double-cliquez sur le mappage pour ouvrir ce dernier dans le Mappeur BizTalk.  
  
2.  Sélectionnez le fonctoid à copier. Pour sélectionnez plusieurs fonctoids, cliquez sur un fonctoid, maintenez la touche CTRL enfoncée, puis cliquez sur les autres fonctoids.  
  
    > [!NOTE]
    >  Vous pouvez utiliser la fonction de « sélection dans le Ruban » pour sélectionner plusieurs liens et/ou fonctoids. Pour plus d’informations, consultez [comment sélectionner plusieurs liens et fonctoids](../core/how-to-select-multiple-links-and-functoids.md).  
  
3.  Avec le bouton droit de la sélection, puis cliquez sur **copie**. Vous pouvez également cliquer sur **copie** à partir de Visual Studio **modifier** menu ou appuyez sur CTRL + C du clavier.  
  
    > [!NOTE]
    >  Pour obtenir la liste des raccourcis clavier, consultez [raccourcis clavier de Mappeur BizTalk](../core/biztalk-mapper-keyboard-shortcuts.md).  
  
4.  Positionnez le pointeur à l'emplacement où vous voulez coller le fonctoid.  
  
5.  Avec le bouton droit sur la page de grille, puis cliquez sur **coller**. Vous pouvez également cliquer sur **coller** à partir de Visual Studio **modifier** menu ou appuyez sur CTRL + V du clavier. Une copie du fonctoid ou du groupe de fonctoids sélectionné s'affiche dans le nouvel emplacement.  
  
### <a name="to-cut-and-paste-a-functoid"></a>Pour couper et coller un fonctoid  
  
1.  Dans l'Explorateur de solutions, ouvrez le projet BizTalk, puis double-cliquez sur le mappage pour ouvrir ce dernier dans le Mappeur BizTalk.  
  
2.  Sélectionnez le fonctoid à couper. Pour sélectionnez plusieurs fonctoids, cliquez sur un fonctoid, maintenez la touche CTRL enfoncée, puis cliquez sur les autres fonctoids.  
  
3.  Avec le bouton droit de la sélection, puis cliquez sur **couper**. Vous pouvez également cliquer sur **couper** à partir de Visual Studio **modifier** menu ou appuyez sur CTRL + X sur le clavier.  
  
    > [!NOTE]
    >  Pour obtenir la liste des raccourcis clavier, consultez [raccourcis clavier de Mappeur BizTalk](../core/biztalk-mapper-keyboard-shortcuts.md).  
  
4.  Positionnez le pointeur à l'emplacement où vous voulez coller le fonctoid.  
  
5.  Avec le bouton droit sur la page de grille, puis cliquez sur **coller**. Vous pouvez également cliquer sur **coller** à partir de Visual Studio **modifier** menu ou appuyez sur CTRL + V du clavier. Le fonctoid ou groupe de fonctoids sélectionné est supprimé de son emplacement actuel et s'affiche dans son nouvel emplacement.  
  
## <a name="see-also"></a>Voir aussi  
 [À l’aide des fonctoids pour créer des mappages plus complexes](../core/using-functoids-to-create-more-complex-mappings.md)