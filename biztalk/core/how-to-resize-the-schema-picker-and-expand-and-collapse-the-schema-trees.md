---
title: "Redimensionner le sélecteur de schéma et développer ou réduire les arborescences de schéma | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 267ea17d-54fe-4031-a044-719606489f24
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 972be8ca5f412c39e1eb6fa2c81ccd9a21e65a34
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-resize-the-schema-picker-and-expand-and-collapse-the-schema-trees"></a>Redimensionner le sélecteur de schéma et développer ou réduire les arborescences de schéma
Lorsque vous développez des mappages BizTalk, vous avez souvent besoin de développer et de réduire les arborescences des schémas source et de destination pour afficher ou masquer les différents nœuds des schémas. Cette rubrique fournit des instructions détaillées pour redimensionner le sélecteur de schéma et pour développer et réduire l’arborescence du schéma.  

## <a name="resize-the-schema-picker"></a>Redimensionner le sélecteur de schéma

Lorsque vous créez un mappage, vous ajoutez un schéma source et un schéma de destination. Lorsque vous ajoutez ou remplacez un schéma, la fenêtre de sélecteur de Type BizTalk s’ouvre et vous sélectionnez votre schéma. 

**En commençant par [!INCLUDE[bts2016_md](../includes/bts2016-md.md)]** , vous pouvez redimensionner la fenêtre Sélecteur de Type. Cette fonctionnalité vous permet de voir le nom complet de votre schéma.

1. Dans votre mappage, sélectionnez **ouvrir le schéma de Destination**, ou **ouvrir le schéma Source**.
2. Dans le **sélecteur de Type BizTalk** fenêtre, coin glisser l’angle inférieur droit pour augmenter ou diminuer la taille de fenêtre.
  
## <a name="expand-all-or-part-of-a-schema-tree"></a>Développer tout ou partie d’une arborescence de schéma  
  
1.  Sélectionnez le nœud sous lequel vous souhaitez développer complètement l'arborescence du schéma.  
  
     Le nœud sélectionné doit être un nœud en regard duquel une icône plus (+) ou moins (-) est affichée.  
  
2.  Sur le **BizTalk** menu, ou dans le menu contextuel du nœud, cliquez sur **développer le nœud d’arborescence**. Tous les nœuds se trouvant sous le nœud sélectionné sont complètement développés.  
  
     Si l’arborescence du schéma située sous le nœud sélectionné est déjà entièrement développée, le **développer le nœud d’arborescence** élément de menu est désactivé.  
  
    > [!NOTE]
    >  Vous pouvez également appuyer sur CTRL+M, E pour développer les nœuds d'arborescence de schéma. Pour obtenir la liste des raccourcis clavier, consultez [raccourcis clavier de Mappeur BizTalk](../core/biztalk-mapper-keyboard-shortcuts.md).  
  
    > [!NOTE]
    >  Dans un schéma volumineux et complexe, lorsque vous cliquez sur **développer le nœud d’arborescence** sur un nœud qui contient les types complexes, certains nœuds du schéma peuvent rester dans l’état réduit. Cela est dû au fait que le processus récurrent ne développe que la première occurrence d'un type complexe donné. Vous devrez développer les autres occurrences manuellement. Ce comportement permet d'optimiser les performances lors du développement de nœuds de grands schémas complexes.  
  
## <a name="collapse-all-or-part-of-a-schema-tree"></a>Réduire tout ou partie d’une arborescence de schéma  
  
1.  Sélectionnez le nœud sous lequel vous souhaitez réduire complètement l'arborescence du schéma.  
  
     Le nœud sélectionné doit être un nœud en regard duquel une icône plus (+) ou moins (-) est affichée.  
  
2.  Sur le **BizTalk** menu, ou dans le menu contextuel du nœud, cliquez sur **réduire le nœud d’arborescence**.  
  
     Tous les nœuds se trouvant sous le nœud sélectionné sont réduits.  
  
    > [!NOTE]
    >  Vous pouvez également appuyer sur CTRL+M, C pour réduire les nœuds d'arborescence de schéma. Pour obtenir la liste des raccourcis clavier, consultez [raccourcis clavier de Mappeur BizTalk](../core/biztalk-mapper-keyboard-shortcuts.md).  
  
     Si l’arborescence du schéma située sous le nœud sélectionné est déjà complètement réduite, le **réduire le nœud d’arborescence** élément de menu est désactivé.  
  
 Cette opération ne conserve pas les paramètres individuels de développement et de réduction des nœuds situés sous le nœud sélectionné. Lorsque vous développez à nouveau le nœud réduit, les paramètres précédents sont perdus, et vous devez développer l’arborescence de schéma se trouvant en dessous de ce point nœud par nœud, ou la développer entièrement.  
  
### <a name="expand-a-node"></a>Développez un nœud
  
-   Cliquez sur l’icône plus (+) située à côté du nœud que vous voulez développer.  
  
 Le nœud sélectionné est développé. Le fait que ses nœuds descendants soient développés ou réduits dépend de la façon dont le nœud sélectionné a été réduit et des paramètres de développement et de réduction précédents.  
  
### <a name="collapse-a-node"></a>Réduire un nœud
  
-   Cliquez sur l’icône moins (-) située à côté du nœud que vous voulez réduire.  
  
 Le nœud sélectionné est réduit.  
  
 Cette opération conserve les paramètres individuels de développement et de réduction des nœuds situés sous le nœud sélectionné. Lorsque vous développez à nouveau le nœud réduit à l’aide de l’icône plus (+), les paramètres individuels précédents ne sont pas perdus, et l’arborescence de schéma se trouvant sous ce point est rétablie dans son état précédent.  
  
## <a name="see-also"></a>Voir aussi  
 [À l’aide du Mappeur BizTalk](../core/using-biztalk-mapper.md)