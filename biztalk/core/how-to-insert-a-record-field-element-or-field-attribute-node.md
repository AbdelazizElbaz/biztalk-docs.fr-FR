---
title: "Comment insérer un enregistrement, un élément de champ ou un nœud d’attribut de champ | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c26f2281-f1b8-4788-8593-8d6ad29a53f0
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1341a0f2d89070d42620396a8c86d497b5d646ef
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-insert-a-record-field-element-or-field-attribute-node"></a>Comment insérer un enregistrement, un élément de champ ou un nœud d’attribut de champ
**Enregistrement** nœuds (y compris le **racine** nœud), **attribut de champ** nœuds, et **élément de champ** nœuds sont uniques dans la mesure où ils peuvent être renommés afin que leurs les noms représentent les noms des éléments réels, nom personnalisé dans un message d’instance correspondant. Par exemple, si vous le nommez un **enregistrement** nœud FullName, à l’emplacement correspondant dans un message d’instance un élément XML nommé FullName est attendu. Si ce **enregistrement** nœud nommé FullName possède un enfant **attribut de champ** nœud nommé RequireFullMiddleName (avec ses **Min Occurs** et **Max Occurs** propriétés **1**), la **FullName** élément dans un message d’instance correspondant doivent avoir un attribut nommé **RequireFullMiddleName** associé.  
  
 Tous les **enregistrement** , lors de leur insertion sont représentés dans l’affichage XSD avec un **complexType** élément, mais pas avec une ultérieure **séquence**, **choix** , ou **tous les** élément. Pour cette raison, le **Group Order Type**, **Group Max Occurs**, et **Group Min Occurs** propriétés de la **enregistrement** nœud ne sont pas disponibles pour la modification.  
  
 Dès que vous ajoutez un enfant **enregistrement** ou **élément de champ** nœud à la **enregistrement** nœud, un **séquence** élément est ajouté pour le schéma XSD représentation dans le **complexType** élément doit contenir ce premier nœud enfant et le **Group Order Type** propriété de la **enregistrement** nœud affiche une valeur de **séquence**. Dans la plupart des cas, vous pouvez modifier le **Group Order Type** propriété à partir de **séquence** à **choix**et dans des circonstances plus limitées, à partir de **séquence**  à **tous les**, ce qui permet la modification de la paire d’élément qui contient les nœuds enfants correspondant soit **complexType/choix** ou **complexType/tous**, respectivement.  
  
 **Attribut de champ** nœuds ne peuvent pas avoir les mêmes noms de nœud dans la même portée.  
  
 **Enregistrement** et **élément de champ** nœuds peuvent avoir les mêmes noms de nœud dans la même portée uniquement si les conditions suivantes sont remplies :  
  
-   Ils doivent avoir le même type de données.  
  
-   Ils ne sont pas dans un **groupe tous** nœud.  
  
### <a name="to-insert-a-new-child-record-node-field-element-node-or-field-attribute-node-within-the-schema-node-or-an-existing-record-node"></a>Pour insérer un nouveau nœud enfant Enregistrement, Élément de champ ou Attribut de champ dans le nœud Schéma ou un nœud Enregistrement existant  
  
1.  Sélectionnez le **schéma** nœud ou un **enregistrement** nœud.  
  
2.  Sur le **BizTalk** menu, pointez sur **insérer un nœud de schéma**, puis cliquez sur **enregistrement enfant**, **élément de champ enfant**, ou  **Attribut de champ enfant**, le cas échéant.  
  
    > [!NOTE]
    >  Un nœud enfant du type choisi est ajouté après le dernier nœud dans l’arborescence de schéma (lors de l’insertion dans la **schéma** nœud) ou après le dernier nœud enfant existant du **enregistrement** nœud (lorsque insertion dans un existant **enregistrement** nœud).  
  
3.  Tapez un nom pour le nouvellement inséré **enregistrement**, **Fieldelement**, ou **attribut de champ** nœud, puis appuyez sur ENTRÉE.  
  
### <a name="to-insert-a-sibling-record-node-field-attribute-node-or-field-element-node-within-an-existing-record-node"></a>Pour insérer un nœud « frère » Enregistrement, Élément de champ ou Attribut de champ dans un nœud Enregistrement existant  
  
1.  Sélectionnez n’importe quel nœud enfant de la **enregistrement** dans lequel vous souhaitez insérer le frère de nœud **enregistrement**, **attribut de champ**, ou **élément de champ** nœud.  
  
2.  Sur le **BizTalk** menu, pointez sur **insérer un nœud de schéma**, puis cliquez sur **enregistrement frère**, **attribut de champ frère**, ou **Élément de champ frère**, le cas échéant.  
  
     Un nœud frère du type choisi est alors inséré à l'extrémité des frères du nœud sélectionné.  
  
3.  Tapez un nom pour le nouvellement inséré **enregistrement**, **attribut de champ**, ou **élément de champ** nœud, puis appuyez sur ENTRÉE.  
  
## <a name="see-also"></a>Voir aussi  
 [Insertion de nœuds dans un schéma](../core/inserting-nodes-into-a-schema.md)