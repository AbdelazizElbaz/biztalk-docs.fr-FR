---
title: "Comment faire pour optimiser l’affichage de liens | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2a9e16ff-01d3-4b7d-91c4-59d17266ee6d
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 689ab4c67bfe8cabc8109c373e899d391fdd56a5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-optimize-the-display-of-links"></a>Optimisation de l'affichage des liens
Lorsque la taille des schémas est importante, vos mappages peuvent inclure un grand nombre de liens entre le schéma source et le schéma de destination. La présence d'un aussi grand nombre de liens sur la surface de mappage complique le suivi d'un lien ou d'un objet sur lequel vous devez travailler. De même, cette visibilité rend difficile le suivi d'une relation de bout en bout entre un schéma source, les liens, les fonctoids et le schéma de destination. Le Mappeur BizTalk permet de mieux gérer les schémas complexes et volumineux et d'optimiser l'affichage des liens du mappage. Cette rubrique fournit des détails sur l'affichage des liens.  
  
 Vous pouvez classer les liens selon la typologie suivante :  
  
-   Partiellement dans l'étendue  
  
-   Entièrement dans l'étendue  
  
-   Entièrement hors de l'étendue  
  
## <a name="prerequisites"></a>Conditions préalables  
 Les instructions suivantes requièrent que le Mappeur BizTalk est en cours d’exécution.  
  
## <a name="to-view-the-links-partially-in-scope"></a>Affichage des liens partiellement dans l'étendue  
 Les liens possédant au moins une extrémité visible sur la surface de la grille sont considérés comme « partiellement dans l'étendue ».  
  
 La figure ci-dessous illustre un lien « partiellement dans l'étendue ». Ces liens sont affichés en tant que lignes en pointillé dans la page de la grille.  
  
 Cliquez sur le lien partiellement visible sur la surface de la grille : la page se déplace automatiquement vers le haut ou vers le bas de manière à placer la relation dans la vue active.  
  
 ![Liaisons du Mappeur partiellement dans l’étendue](../core/media/mapper-partiallyinscope.gif "Mapper_PartiallyInScope")  
  
## <a name="to-view-the-links-completely-in-scope"></a>Affichage des liens entièrement dans l'étendue  
 Un lien dont les deux extrémités (nœud à nœud, nœud à fonctoid, fonctoid à fonctoid ou fonctoid à nœud) sont visibles sur la surface de la grille est considéré comme « entièrement dans l'étendue ».  
  
 La figure ci-dessous illustre un lien reliant « DataCollection1 » et « ST01 » entièrement dans l'étendue.  
  
 Cliquez sur le lien : la relation entre le nœud source et le nœud cible est sélectionnée.  
  
 ![Liaisons du Mappeur entièrement dans l’étendue](../core/media/mapper-completelyinscope.gif "Mapper_CompletelyInScope")  
  
## <a name="to-view-the-links-completely-out-of-scope"></a>Affichage des liens entièrement hors de l'étendue  
 Un lien dont aucune de ses extrémités n'est visible dans la vue active du mappage est considéré comme « entièrement hors de l'étendue ».  
  
 La figure ci-dessous illustre un lien « entièrement hors de l'étendue ».  
  
 Si vous ne souhaitez pas afficher ces liens sur la carte de surface (car aucun des liens sont visibles), vous pouvez choisir de les mettre hors tension en cliquant sur ![afficher tous les liens](../core/media/mapper-showhideoutscopelinks.gif "Mapper_ShowHideOutScopeLinks") sur le Mappeur ruban de l’utilitaire. Cela permet de réduire le nombre de liens affichés sur la vue Grille.  
  
 ![Liaisons du Mappeur entièrement hors de portée](../core/media/mapper-completelyoutscope.gif "Mapper_CompletelyOutScope")  
  
## <a name="see-also"></a>Voir aussi  
 [À l’aide des fonctionnalités améliorées dans le Mappeur BizTalk](../core/using-enhanced-features-in-biztalk-mapper.md)