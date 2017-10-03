---
title: Comment copier, couper et coller des liens et fonctoids | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 80b4792a-5ff6-4603-96cd-b3d3d530c12f
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5eec0ddc164af936e1c3739e4da167753a6e58c8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-copy-cut-and-paste-links-and-functoids"></a>Coupage, copie et collage de liens et fonctoid
La fonction copier/couper/coller dans le Mappeur BizTalk permet de réutiliser une relation. Cette rubrique fournit des instructions pas à pas pour copier, couper et coller des fonctoids et/or des liens dans un mappage.  
  
 Vous pouvez utiliser la fonction copier/coller pour réutiliser un ensemble de fonctoids et/ou de liens. Lorsque vous voulez supprimer la sélection de l'emplacement existant et la déplacer vers un nouvel emplacement, vous pouvez utiliser la fonction couper/coller.  
  
> [!IMPORTANT]
>  Vous trouvez que la fonction couper/coller et la fonction de déplacement sont similaires ? Il existe une différence. Lorsque vous sélectionnez couper, seuls les fonctoids et/ou les liens de votre sélection sont supprimés de la page de grille source. Mais, lorsque vous sélectionnez déplacer, tous les fonctoids et liens de la relation (indépendamment de la sélection) sont supprimés de manière récursive de la page de grille source. Pour plus d’informations sur le déplacement d’une relation, consultez [comment déplacer une relation entre les Pages de grille](../core/how-to-move-a-relationship-between-grid-pages.md).  
  
 Lorsque vous copiez/coupez un ensemble de fonctoids et/ou liens, fonctoids, étiquettes, commentaires et valeurs constantes (ainsi que les espaces réservés appropriés) associés qu’ensemble sont conservés.  
  
 Vous pouvez copier/couper uniquement ces éléments de mappage :  
  
-   Lien du schéma source au schéma de destination.  
  
-   Lien du fonctoid au nœud de schéma, si et seulement si le fonctoid est également sélectionné avec le lien.  
  
-   Lien du fonctoid au fonctoid, si et seulement si les fonctoids sont sélectionnés avec le lien.  
  
 Vous pouvez copier/couper des fonctoids et/ou des liens à partir de :  
  
-   Au sein de la même page de grille d'un mappage  
  
-   D'une page de grille à l'autre dans le même mappage  
  
-   D'un mappage à l'autre dans la même instance de Visual Studio  
  
-   Entre différentes instances de Visual Studio  
  
 Vous pouvez annuler ou rétablir les opérations Couper et Coller. Pour plus d’informations, consultez [comment annuler ou rétablir les opérations de l’utilisateur](../core/how-to-undo-or-redo-user-operations.md).  
  
 En outre, vous devez prendre en compte les points suivants lors du collage de liens :  
  
-   Un lien entre les schémas source et cible peut être collé si et seulement si le mappage actuel, où le lien est collé, contient un nœud source ainsi qu'un nœud cible dont le XPath est identique au XPath des nœuds source et cible pour le lien collé.  
  
-   Un lien entre les schémas source et cible peut être collé si et seulement s'il n'existe aucun lien entre les nœuds source et cible susmentionnés.  
  
-   Un lien entre un fonctoid et le schéma de destination peut être collé si et seulement s'il existe un nœud cible dont le XPath est identique au XPath du nœud cible du lien collé.  
  
-   Un lien entre un schéma source et un fonctoid peut être collé si et seulement s'il existe un nœud source dont le XPath est identique au XPath du nœud source du lien collé.  
  
> [!NOTE]
>  Si vous sélectionnez plusieurs éléments (liens et/ou fonctoids) dont certaines ne peuvent pas être coupés/copiés, puis que vous exécutez une commande de coupe/copie, le message d'avertissement « Impossible de couper/copier certains des éléments sélectionnés » s'affiche dans la barre d'état de Visual Studio. Le message fournit également tous les détails utiles.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Les instructions suivantes requièrent que le Mappeur BizTalk est en cours d’exécution.  
  
### <a name="to-copy-and-paste-a-relationship"></a>Pour copier et coller une relation  
  
1.  Dans l'Explorateur de solutions, ouvrez le projet BizTalk, puis double-cliquez sur le mappage pour ouvrir ce dernier dans le Mappeur BizTalk.  
  
2.  Sélectionnez les fonctoids et/ou les liens à copier.  
  
    > [!TIP]
    >  Vous pouvez les sélectionner en maintenant appuyée la touche CTRL et en sélectionnant les fonctoids et/ou liens souhaités ou en faisant un glisser-déplacer entre les liens pour former un rectangle de sélection.  
  
    > [!NOTE]
    >  Vous pouvez utiliser la fonction de « sélection dans le Ruban » pour sélectionner plusieurs liens et/ou fonctoids. Pour plus d’informations, consultez [comment sélectionner plusieurs liens et fonctoids](../core/how-to-select-multiple-links-and-functoids.md).  
  
3.  Cliquez sur la sélection. puis cliquez sur **copie**. Vous pouvez également appuyer sur CTRL+C sur le clavier.  
  
    > [!NOTE]
    >  Pour obtenir la liste des raccourcis clavier, consultez [raccourcis clavier de Mappeur BizTalk](../core/biztalk-mapper-keyboard-shortcuts.md).  
  
4.  Placez le curseur là où vous voulez coller la sélection.  
  
5.  Avec le bouton droit sur la page de grille, puis cliquez sur **coller**. Vous pouvez également appuyer sur CTRL+V sur le clavier. Une copie de la sélection apparaît au nouvel emplacement.  
  
### <a name="to-cut-and-paste-a-relationship"></a>Pour couper et coller une relation  
  
1.  Dans l'Explorateur de solutions, ouvrez le projet BizTalk, puis double-cliquez sur le mappage pour ouvrir ce dernier dans le Mappeur BizTalk.  
  
2.  Sélectionnez les fonctoids et/ou les liens à couper.  
  
    > [!TIP]
    >  Vous pouvez les sélectionner en maintenant appuyée la touche CTRL et en sélectionnant les fonctoids et/ou liens souhaités ou en faisant un glisser-déplacer entre les liens pour former un rectangle de sélection.  
  
    > [!NOTE]
    >  Vous pouvez utiliser la fonction de « sélection dans le Ruban » pour sélectionner plusieurs liens et/ou fonctoids. Pour plus d’informations, consultez [comment sélectionner plusieurs liens et fonctoids](../core/how-to-select-multiple-links-and-functoids.md).  
  
3.  Avec le bouton droit de la sélection, puis cliquez sur **couper**. Vous pouvez également appuyer sur CTRL+X sur le clavier.  
  
    > [!NOTE]
    >  Pour obtenir la liste des raccourcis clavier, consultez [raccourcis clavier de Mappeur BizTalk](../core/biztalk-mapper-keyboard-shortcuts.md).  
  
4.  Placez le curseur là où vous voulez coller la sélection.  
  
5.  Avec le bouton droit sur la page de grille, puis cliquez sur **coller**. Vous pouvez également appuyer sur CTRL+V sur le clavier. La sélection est supprimée de l'emplacement existant et apparaît au nouvel emplacement.