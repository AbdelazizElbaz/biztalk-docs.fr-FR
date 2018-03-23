---
title: L’optimisation de l’arborescence du schéma | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ab4ad6b5-5bbd-443b-9041-6cddf9d64735
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: aeeddd0893b80c1c7b37b2d0ee5f9f6cd68849d6
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/23/2018
---
# <a name="how-to-optimize-the-schema-tree-view"></a>Optimisation de la vue de l'arborescence de schéma
Vous pouvez utiliser la **vue pertinence** dans le Mappeur BizTalk pour optimiser la source et/ou cible des arborescences de schéma. Cette rubrique fournit des instructions sur l'exécution de l'opération.  
  
 La vue Pertinence utilise un principe de fusion pour réduire les éléments de schéma non pertinents afin d'obtenir une vue plus compacte du schéma. Cela réduit la nécessité de défilement et vous aide à vous concentrer sur l'exigence d'utiliser des schémas et des mappages.  
  
 La figure suivante présente un schéma illustrant la vue Pertinence DÉSACTIVÉE. Le volet Schéma affiche tous les nœuds, qu'ils fassent partie d'une relation ou non.  
  
 ![Schéma de la vue pertinence est mises hors tension](../core/media/off-schema-relevance-view.gif "Off_Schema_Relevance_View")  
  
 Cliquez sur le ![basculer vers la vue pertinence](../core/media/mapper-intellitree.gif "Mapper_IntelliTree") icône sur le ruban de l’utilitaire mappeur pour activer la vue pertinence. Vous pouvez basculer vers la vue Pertinence pour le schéma source et le schéma cible ; cliquez sur les icônes correspondant aux schémas source et cible.  
  
 Lorsque vous basculez vers la vue Pertinence pour un schéma :  
  
-   Tous les éléments d'enregistrement n'ayant pas de liens entre eux ou avec leurs éléments de champ enfants sont réduits.  
  
-   Tous les nœuds suivants qui n’ont pas tous les liens sont fusionnés et sont remplacés par le ![fusionnés nœuds masqués](../core/media/mapper-coalescence-on.gif "Mapper_Coalescence_On") icône. Le Mappeur BizTalk recherche au moins deux nœuds non pertinents successifs pouvant être fusionnés. Vous pouvez déplacer la souris sur l'icône pour afficher la liste des nœuds fusionnés. Notez que l'info-bulle affiche uniquement les noms des trois premiers nœuds fusionnés, même s'il y en a davantage. Vous pouvez afficher tous les nœuds en cliquant sur le ![fusionnés nœuds masqués](../core/media/mapper-coalescence-on.gif "Mapper_Coalescence_On") icône.  
  
    > [!NOTE]
    >  Pour plus d’informations sur l’info-bulle, consultez [l’info-bulle de l’affichage et l’info-bulle](../core/how-to-view-infotip-and-tooltip.md).  
  
## <a name="prerequisites"></a>Configuration requise  
 Cette opération nécessite l'exécution du Mappeur BizTalk.  
  
## <a name="to-optimize-the-schema-tree-view"></a>Pour optimiser l'affichage de l'arborescence du schéma  
 Sur le ruban de l’utilitaire mappeur, activez la vue pertinence pour les schémas source et/ou cible en cliquant sur la ![basculer vers la vue pertinence](../core/media/mapper-intellitree.gif "Mapper_IntelliTree") icônes. La figure suivante illustre le même schéma lorsque la vue Pertinence est activée. Tous les nœuds non pertinents sont remplacés par le ![fusionnés nœuds masqués](../core/media/mapper-coalescence-on.gif "Mapper_Coalescence_On") icône pour fournir une vue plus compacte du schéma.  
  
 ![Schéma lorsque la vue pertinence est défini sur](../core/media/on-schema.gif "On_schema")  
  
 Lorsque vous développez les nœuds fusionnés dans les schémas sources et/ou de destination, le ![fusionnés nœuds masqués](../core/media/mapper-coalescence-on.gif "Mapper_Coalescence_On") devient ![fusionné les nœuds affichés] (../core/media/switchoff-mapper-coalesence.jpg "SwitchOff_Mapper_Coalesence") icône.  
  
> [!NOTE]
>  Vous pouvez appuyer sur CTRL+M, CTRL+E ou CTRL+M, CTRL+C pour développer ou réduire les nœuds d'arborescence du schéma source. De même, vous pouvez appuyer sur CTRL+M, CTRL+E ou CTRL+M, CTRL+C pour développer ou réduire les nœuds d'arborescence du schéma de destination. Pour fusionner la source ou la cible, vous pouvez utiliser les combinaisons de touches Ctrl+M, Ctrl+H ou Ctrl+M, Ctrl+D. Pour obtenir la liste des raccourcis du mappeur, consultez [raccourcis clavier de Mappeur BizTalk](../core/biztalk-mapper-keyboard-shortcuts.md).  
  
## <a name="see-also"></a>Voir aussi  
 [À l’aide des fonctionnalités améliorées dans le Mappeur BizTalk](../core/using-enhanced-features-in-biztalk-mapper.md)