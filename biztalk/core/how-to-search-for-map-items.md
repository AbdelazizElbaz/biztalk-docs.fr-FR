---
title: Comment rechercher des éléments de la carte | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- bts10.mapper.search
ms.assetid: 3dbb089a-6aa8-4921-a82d-81d3a193e933
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ee61bccfae53a79d8fba6bd0aa5af2c537d98270
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-search-for-map-items"></a>Recherche d'éléments de mappage
Le Mappeur BizTalk permet de rechercher des éléments dans le schéma source, le schéma de destination et la surface de la grille. Cette rubrique fournit les informations vous permettant d'effectuer cette opération.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Les instructions suivantes requièrent que le Mappeur BizTalk est en cours d’exécution.  
  
## <a name="to-search-for-items"></a>Pour rechercher des éléments  
 Sélectionnez le schéma dans lequel effectuer une recherche. Si vous sélectionnez le schéma source, le Mappeur BizTalk effectue la recherche dans le seul schéma source. Vous pouvez toutefois sélectionner le schéma source et le schéma de destination.  
  
> [!NOTE]
>  Pour confirmer la sélection, recherchez la marque en regard du schéma ou de l'élément de schéma.  
  
 ![Recherche d’éléments de la carte](../core/media/searching-map-items.gif "Searching_map_items")  
  
 Dans le **recherche** sur le ruban de l’utilitaire mappeur, tapez le nom de l’élément que vous souhaitez rechercher. Vous pouvez rechercher une chaîne dans le nom d'un nœud du schéma source ou du schéma de destination, ainsi que dans le nom, l'étiquette, le commentaire, les entrées ou les scripts d'un fonctoid.  
  
 Lorsque vous entrez la chaîne de recherche, les objets qui correspondent aux critères de recherche sont mis en surbrillance. Vous pouvez ensuite parcourir les résultats de recherche soit à l’aide de la flèche de touches du clavier ou ![déplacer vers le haut dans la liste](../core/media/move-up-button.gif "Move_up_button") et ![déplacement vers le bas dans une liste] (../core/media/move-down-button.gif " Move_down_button") les icônes sur le ruban de l’utilitaire. Si les résultats de la recherche sont répartis entre les trois vues, ils sont parcourus dans l'ordre suivant : schéma source, vue de relation et schéma de destination. Après avoir examiné les résultats de recherche, vous pouvez fermer la recherche en supprimant la chaîne de recherche ou en cliquant sur le (![dans le Mappeur clair](../core/media/mapper-search-cancel.gif "Mapper_Search_Cancel")) icône en regard de la chaîne de recherche.  
  
> [!NOTE]
>  Vous pouvez également utiliser les combinaisons de touches CTRL+M, CTRL+J ou CTRL+M, CTRL+K pour faire défiler les résultats de la rcherche vers le haut ou le bas, respectivement. Pour obtenir la liste des raccourcis du mappeur, consultez [raccourcis clavier de Mappeur BizTalk](../core/biztalk-mapper-keyboard-shortcuts.md).  
  
> [!IMPORTANT]
>  Si les résultats de la recherche pour la vue de relation ne sont pas visibles dans une seule vue de mappage, le Mappeur BizTalk affiche des flèches clignotantes pointant vers les autres résultats. Par exemple, l’icône de flèche vers le haut (![Direction pour les résultats de recherche supplémentaires](../core/media/mapper-search-direction.gif "Mapper_Search_Direction")) indique qu’il existe des résultats de recherche supplémentaires qui peuvent être affichées par défilement vers le haut. De même, si les résultats de la recherche sont situés dans d'autres pages de mappage, les onglets de ces pages sont mis en surbrillance, en jaune. Lors du déplacement de la souris sur la page en surbrillance, l'info-bulle indique le nombre de correspondances de la recherche dans cette page. La barre d'état affiche les résultats de la recherche.  
  
 ![Afficher les résultats de recherche de la barre d’état](../core/media/searching-map-items-statusbar.jpg "Searching_map_items_statusbar")  
  
## <a name="see-also"></a>Voir aussi  
 [À l’aide du Mappeur BizTalk](../core/using-biztalk-mapper.md)