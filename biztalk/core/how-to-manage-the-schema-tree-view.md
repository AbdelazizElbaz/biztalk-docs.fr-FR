---
title: "Comment gérer l’arborescence du schéma | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 97fb7a88-e38a-4abb-93bc-a5be1bd091e6
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f84ba68cd515c673daaac2e2ca96bb0e2346ecbb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-manage-the-schema-tree-view"></a>Gestion de l'arborescence de schéma
Tâches de gestion en ce qui concerne l’arborescence de schéma peuvent être divisés en quatre catégories : modifier sa taille, de modifier sa couleur d’arrière-plan et la police, de modifier son utilisation des messages d’avertissement et de développer et de réduire sa structure arborescente. Cette rubrique fournit des instructions pas à pas pour ces différentes tâches.  
  
### <a name="to-make-the-schema-tree-view-taller-or-shorter"></a>Pour agrandir ou réduire verticalement l'arborescence des schémas  
  
1.  Placez le pointeur de la souris sur le bord inférieur de la fenêtre d'édition principale de Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], qui affiche les vues XSD et de l'arborescence des schémas côte à côte, jusqu'à ce que le curseur se transforme en icône de redimensionnement vertical de fenêtre standard.  
  
2.  Cliquez avec le bouton gauche, maintenez-le enfoncé et déplacez le bord de la fenêtre vers le haut ou vers le bas.  
  
     Vous avez redimensionné verticalement la vue de l'arborescence des schémas en redimensionnant verticalement la fenêtre d'édition principale dans son intégralité.  
  
### <a name="to-make-the-schema-tree-view-wider-or-more-narrow"></a>Pour agrandir ou réduire horizontalement l'arborescence des schémas  
  
1.  Placez le pointeur de la souris sur le trait séparant les volets de la fenêtre d'édition principale de [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], qui sépare les vues XSD et de l'arborescence des schémas, jusqu'à ce que le curseur se transforme en icône de redimensionnement horizontal de fenêtre standard.  
  
2.  Cliquez avec le bouton gauche, maintenez-le enfoncé et déplacez le bord du volet vers la gauche (pour rétrécir) ou vers la droite (pour élargir).  
  
     Vous avez redimensionné horizontalement l'arborescence des schémas en modifiant l'espace de la fenêtre d'édition principale dédié à l'arborescence des schémas par rapport à la vue XSD.  
  
     Vous pouvez aussi élargir ou rétrécir l'arborescence des schémas en redimensionnant horizontalement l'intégralité de la fenêtre d'édition principale.  
  
### <a name="to-change-the-background-color-andor-font-used-by-the-schema-tree-view"></a>Pour modifier la couleur d'arrière-plan et/ou la police utilisée par la vue de l'arborescence des schémas  
  
1.  Dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], dans le menu **Outils** , cliquez sur **Options**.  
  
2.  Dans le **Options** boîte de dialogue, cliquez sur le dossier de l’Éditeur BizTalk et si nécessaire, développez le **affichage du schéma** catégorie en cliquant sur le signe plus (+) icône.  
  
3.  Modifier la couleur d’arrière-plan et/ou la police en utilisant le sélecteur de couleur déroulant et/ou **police** boîte de dialogue associé à la **couleur d’arrière-plan de l’arborescence schéma** et **policedel’arborescencedeschéma**propriétés, respectivement.  
  
     Accès le **police** boîte de dialogue en utilisant les points de suspension (**...** ) situé à l’extrémité droite de la **police de l’arborescence de schéma** zone de valeur de propriété.  
  
### <a name="to-change-the-warning-dialogs-used-when-working-in-the-schema-tree-view"></a>Pour modifier les messages d'avertissement utilisés lors du travail dans la vue de l'arborescence de schéma  
  
1.  Dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], dans le menu **Outils** , cliquez sur **Options**.  
  
2.  Dans le **Options** boîte de dialogue, cliquez sur le **l’Éditeur BizTalk** dossier et, si nécessaire, développez le **Options d’édition** section en cliquant sur le signe plus (+) icône.  
  
3.  Définissez les propriétés suivantes sur **True** ou **False** à l’aide de la liste déroulante accédée sur le bord droit de la zone de valeur de propriété respective.  
  
    > [!NOTE]
    >  La valeur **True** correspond à la valeur par défaut pour tous les trois options de boîte de dialogue Avertissement.  
  
    |Propriété| Description|  
    |--------------|-----------------|  
    |**Afficher Structure boîte de dialogue Avertissement de destruction**|Lorsque la valeur **True**, affiche une boîte de dialogue d’avertissement avant que la structure de schéma est détruite et vous permet d’annuler l’opération de destruction.|  
    |**Afficher avertissement de codage**|Lorsque la valeur **True**, affiche une boîte de dialogue lorsque le nom de nœud que vous avez tapé ne sera pas valides en XML, sauf si encodé, ce qui vous permet d’annuler l’opération d’affectation de noms, ou continuer avec le nom de l’encodage.|  
    |**Afficher la boîte de dialogue Insérer non valide**|Lorsque la valeur **True**, affiche une boîte de dialogue d’avertissement pour certaines erreurs d’insertion de nœud et offre des options sur la marche à suivre. Les erreurs d'insertion de nœud possibles incluent :<br /><br /> -Vous avez créé en double **attribut de champ** nœuds avec le même nom et le même nœud parent.<br />-Vous avez créé en double **enregistrement** nœuds avec le même nom et le même nœud parent, mais avec des types sous-jacents différents.|  
  
### <a name="to-completely-expand-all-or-part-of-the-schema-tree"></a>Pour développer complètement tout ou partie de l'arborescence de schéma  
  
-   Sélectionnez le nœud sous lequel vous souhaitez développer complètement l'arborescence du schéma.  
  
     Le nœud sélectionné doit être un nœud en regard duquel une icône plus (+) ou moins (-) est affichée.  
  
     Sur le **BizTalk** menu, ou dans le menu contextuel du nœud, cliquez sur **développer le nœud de schéma**. Tous les nœuds se trouvant sous le nœud sélectionné sont complètement développés. Si l’arborescence du schéma située sous le nœud sélectionné est déjà entièrement développée, le **développer le nœud de schéma** menu sera grisée.  
  
    > [!NOTE]
    >  Dans un schéma volumineux et complexe, lorsque vous cliquez sur **développer le nœud de schéma** sur un nœud qui contient les types complexes, certains nœuds du schéma peuvent rester dans l’état réduit. Cela est dû au fait que le processus récurrent ne développe que la première occurrence d'un type complexe donné. Vous devrez développer les autres occurrences manuellement. Ce comportement permet d'optimiser les performances lors du développement de nœuds de grands schémas complexes.  
  
### <a name="to-completely-collapse-all-or-part-of-the-schema-tree"></a>Pour réduire complètement tout ou partie de l'arborescence de schéma  
  
1.  Sélectionnez le nœud sous lequel vous souhaitez réduire complètement l'arborescence du schéma.  
  
     Le nœud sélectionné doit être un nœud en regard duquel une icône plus (+) ou moins (-) est affichée.  
  
2.  Sur le **BizTalk** menu, ou dans le menu contextuel du nœud, cliquez sur **réduire le nœud de schéma**.  
  
     Tous les nœuds se trouvant sous le nœud sélectionné sont réduits.  
  
    > [!NOTE]
    >  Si l’arborescence du schéma située sous le nœud sélectionné est déjà complètement réduite, le **réduire le nœud de schéma** menu sera grisée.  
  
    > [!NOTE]
    >  Cette opération ne conserve pas les paramètres individuels de développement et de réduction des nœuds situés sous le nœud sélectionné. Autrement dit, lorsque vous développerez à nouveau le nœud réduit, les différents paramètres précédents seront perdus et vous devrez développer l'arborescence de schéma se trouvant en dessous de ce point nœud par nœud, ou la développer entièrement.  
  
### <a name="to-expand-a-node-of-the-schema-tree"></a>Pour développer un nœud de l'arborescence de schéma  
  
-   Cliquez sur l’icône plus (+) située à côté du nœud que vous voulez développer.  
  
    > [!NOTE]
    >  Le nœud choisi est développé. Que ses nœuds descendants soient développés ou réduits dépend de leurs paramètres de développement et de réduction précédents et de la façon dont le nœud choisi a été réduit.  
  
### <a name="to-collapse-a-node-of-the-schema-tree"></a>Pour réduire un nœud de l'arborescence de schéma  
  
-   Cliquez sur l’icône moins (-) située à côté du nœud que vous voulez réduire.  
  
    > [!NOTE]
    >  Le nœud choisi est réduit.  
  
    > [!NOTE]
    >  Cette opération conserve les paramètres individuels de développement et de réduction des nœuds situés sous le nœud choisi. Autrement dit, lorsque vous développerez à nouveau le nœud réduit à l'aide de l'icône plus (+), les paramètres individuels précédents ne seront pas perdus, et l'arborescence de schéma se trouvant sous ce point reprendra son état développer/réduire précédent.  
  
## <a name="see-also"></a>Voir aussi  
 [À l’aide de l’Éditeur BizTalk](../core/using-biztalk-editor.md)