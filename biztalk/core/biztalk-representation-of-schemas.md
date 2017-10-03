---
title: "Représentation BizTalk de schémas | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f0460a37-1f4f-4c0b-91db-bb457f434fe9
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c8f22abea29cf848c85bf97e2b3531965566f145
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="biztalk-representation-of-schemas"></a>Représentation BizTalk de schémas

## <a name="overview"></a>Vue d'ensemble
Bien que les schémas BizTalk soient finalement représentés et conservés dans le langage XSD (XML Schema Definition), ils sont représentés sous la forme d'une hiérarchie graphique de nœuds lorsque l'on travaille dans l'Éditeur BizTalk. En haut de la hiérarchie est toujours le  **\<schéma >** nœud et les autres types de nœuds sont utilisés pour générer le schéma de sorte qu’il représente un message particulier qui est échangé à l’aide de BizTalk.  

## <a name="insert-schema-node-options"></a>Options de nœud de schéma d’insertion  
 L'Éditeur BizTalk offre un moyen de construire des schémas XSD sans passer par l'apprentissage de toutes les subtilités de la syntaxe XSD. Lorsque vous utilisez la **insérer un nœud de schéma** commande sur le **BizTalk** menu ou le menu contextuel, les choix suivants pour les nœuds à insérer sont disponibles dans le menu en cascade.  
  
|Option de menu Insérer un nœud de schéma| Description|  
|------------------------------------|-----------------|  
|**Enregistrement enfant**|Insère un **enregistrement** nœud à la fin de la séquence dans le nœud sélectionné. Pour plus d’informations sur **enregistrement** nœuds, voir [nœuds enregistrement](../core/record-nodes.md).|  
|**Attribut de champ enfant**|Insère un **attribut de champ** nœud à la fin de l’élément **enregistrement** ou **groupe d’attributs** nœud. Pour plus d’informations sur **attribut de champ** nœuds, voir [nœuds attribut de champ](../core/field-attribute-nodes.md).|  
|**Élément de champ enfant**|Insère un **élément de champ** nœud dans le nœud sélectionné. Pour plus d’informations sur **Fieldelement** nœuds, voir [nœuds élément de champ](../core/field-element-nodes.md).|  
|**Enregistrement frère**|Insère un **enregistrement** nœud à la fin de la séquence contenant le nœud sélectionné. Pour plus d’informations sur **enregistrement** nœuds, voir [nœuds enregistrement](../core/record-nodes.md).|  
|**Attribut de champ frère**|Insère un **attribut de champ** nœud à la fin de la **enregistrement** ou **groupe d’attributs** contenant le nœud sélectionné. Pour plus d’informations sur **attribut de champ** nœuds, voir [nœuds attribut de champ](../core/field-attribute-nodes.md).|  
|**Élément de champ frère**|Insère un **élément de champ** nœud à la fin de la séquence contenant le nœud sélectionné. Pour plus d’informations sur **Fieldelement** nœuds, voir [nœuds élément de champ](../core/field-element-nodes.md).|  
|**Groupe séquence**|Insère un **groupe séquence** nœud (\<séquence > dans l’arborescence) à la fin de la séquence dans le nœud sélectionné. Pour plus d’informations sur **groupe séquence** nœuds, voir [nœuds groupe séquence](../core/sequence-group-nodes.md).|  
|**Groupe choix**|Insère un **groupe choix** nœud (\<choix > dans l’arborescence) à la fin de la séquence dans le nœud sélectionné. Pour plus d’informations sur **groupe choix** nœuds, voir [nœuds groupe choix](../core/choice-group-nodes.md).|  
|**Groupe tous**|Insère une **groupe tous** nœud (\<tous les > dans l’arborescence) en tant que le nœud enfant non-attribut uniquement d’un **enregistrement** utilise de nœud, en remplaçant la valeur par défaut d’un **séquence** élément à l’intérieur du **enregistrement** nœud à l’aide d’un **tous les** élément. Avant de pouvoir insérer un **groupe tous** nœud, vous devez modifier le **le Type de contenu** propriété du contenant **enregistrement** nœud **ComplexContent**. Pour plus d’informations sur **groupe tous** nœuds, voir [tous les nœuds de groupe](../core/all-group-nodes.md).|  
|**Groupe d’attributs**|Insère une **groupe d’attributs** nœud (\<AttrGroup:attrGroup*N*> dans l’arborescence de commandes, où *N* est un nombre croissant) à la fin de la sélectionné **enregistrement** ou **groupe d’attributs** nœud. Pour plus d’informations sur **groupe d’attributs** nœuds, voir [nœuds groupe attribut](../core/attribute-group-nodes.md).|  
|**Tout élément**|Insère une **tout élément** nœud (**\<**tout **>**  dans l’arborescence) à la fin de la séquence dans l’élément **enregistrement** , **Groupe séquence**, **groupe choix**, ou **groupe tous** nœud. Pour plus d’informations sur **tout élément** nœuds, voir [nœuds tout élément](../core/any-element-nodes.md).|  
|**Tout attribut**|Insère une **tout attribut** nœud (**\<**AnyAttribute **>**  dans l’arborescence) à la fin de la séquence dans le sélectionné**Enregistrement** ou **groupe d’attributs** nœud. Pour plus d’informations sur **tout attribut** nœuds, voir [nœuds tout attribut](../core/any-attribute-nodes.md).|  
  
 Dans bien des cas, l'ajout d'un seul nœud dans l'Éditeur BizTalk provoque l'ajout de plusieurs éléments imbriqués dans la représentation XSD correspondante du schéma. La syntaxe de ces éléments imbriqués pouvant être complexe, le recours à l'Éditeur BizTalk pour agencer graphiquement les nœuds permet de réduire le risque d'erreurs, par rapport à l'approche de la modification manuelle du XSD, quand on construit des schémas XSD. L'autre facteur à prendre en compte est qu'utiliser toujours l'Éditeur BizTalk pour construire des schémas XSD fait que le sous-ensemble de XSD utilisé dans les descriptions de schéma est plus contrôlé.  
  
 De manière générale, l’Éditeur BizTalk combine une approche simplifiée pour créer des schémas XSD à l’aide des concepts génériques des enregistrements et champs avec un contrôle plus explicit de XSD particulier construit, tel que **séquence**,  **choix**, **tout**, et **anyattribute** éléments.  
  
 Chaque type de nœud possède un ensemble unique de propriétés qui peuvent être configurées dans la fenêtre Propriétés de Visual Studio. En général, ces propriétés correspondent à des attributs des éléments XSD dans la représentation XSD correspondante du schéma. Pour plus d’informations sur les propriétés d’un nœud, consultez **propriétés d’un nœud** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].
  
 Cette section décrit les types de nœuds utilisés dans l'Éditeur BizTalk, aborde rapidement leurs propriétés et fournit des liens donnant accès à des informations de référence sur ces dernières.  
  
## <a name="next-steps"></a>Étapes suivantes
  
-   [Nœuds qui correspondent directement aux données d’Instance de Message et la Structure](../core/nodes-that-correspond-directly-to-message-instance-data-and-structure.md)  
  
-   [Nœuds contrôlant la Structure de Message d’Instance et les Variations](../core/nodes-that-control-instance-message-structure-and-variations.md)  
  
-   [Nœuds qui simplifient la création de schémas](../core/nodes-that-simplify-schema-creation.md)  
  
-   [Nœuds qui fournissent des fonctionnalités de caractères génériques](../core/nodes-that-provide-wildcard-capabilities.md)  
  
-   [Propriétés de nœud](../core/node-properties.md)