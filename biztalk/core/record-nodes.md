---
title: "Enregistrer des nœuds | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 43af077d-5db8-43ca-8bd0-e3a9e3ebe2b0
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4486b875693827c6fed74e9293bdb68b2c3dc3b2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="record-nodes"></a>Nœuds Enregistrement
Dans l’Éditeur BizTalk, vous utilisez un **enregistrement** nœud pour représenter une collection d’informations, les éléments individuels qui peuvent être :  
  
-   des types d'informations simples, telles que des chaînes et des nombres, représentés sous forme de nœuds de champs enfants. Ces nœuds de champ enfant peuvent être **Fieldelement** nœuds ou **attribut de champ** nœuds. Pour plus d’informations sur ces deux types de nœuds de champ, consultez [nœuds élément de champ](../core/field-element-nodes.md) et [nœuds attribut de champ](../core/field-attribute-nodes.md).  
  
-   Les types complexes d’informations, représentée en tant qu’enfant **enregistrement** nœuds ou sous la forme d’un nœud de groupe (**groupe séquence** nœud, **groupe choix** nœud, ou **groupe** nœud).  
  
-   N’importe quel type sans examen d’informations, représentée en tant qu’enfant **tout élément** ou **tout attribut** nœuds.  
  
-   Groupes d’attributs représentés par une **groupe d’attributs** nœud.  
  
 Lorsque vous insérez un nouveau nœud enfant dans un **enregistrement** nœud, le nœud enfant est toujours inséré à la fin des nœuds enfants en cours. Dans la représentation de langage XML Schema definition (XSD), les nouveaux éléments sont ajoutés à la fin de leurs zones correspondants, ce qui signifie que les éléments non-attribut sont ajoutées à la fin des éléments dans le **séquence**, **choix**, **tous les**, ou **groupe** élément et attribut des éléments sont ajoutés à la fin de tous les autres éléments d’attribut, qui se produisent après le **séquence** , **choix**, **tous les**, ou **groupe** élément.  
  
## <a name="xsd-representation"></a>Représentation XSD  
 Lors de la première insertion, la représentation XSD d’un nouveau **enregistrement** nœud se compose de trois lignes uniquement, comme indiqué dans l’exemple suivant.  
  
```  
<xs:element name="Record">  
      <xs:complexType />  
</xs:element>  
```  
  
 Lorsque n’importe quel nœud enfant autre qu’un des nœuds de le trois attribut (**attribut de champ**, **groupe d’attributs**, et **tout attribut**) est ajouté à un **enregistrement** nœud, par défaut, il est placé dans un **séquence** élément dans le **complexType** élément. Le **séquence** élément est ajouté lorsque le premier nœud non-attribut enfant est ajouté et supprimé si tous les nœuds enfants non-attributs sont supprimés. Les trois types de nœuds d’attribut sont ajoutées au sein de la **complexType** élément, mais à l’extérieur et après chaque **séquence** élément.  
  
 Le **séquence** élément au sein de quel non-attribut nœuds enfants sont ajoutés peut également être un **choix** ou **tous les** élément si vous modifiez le **Group Order Type (nœud Propriété de tous les schémas)** propriété du nœud correspondant dans l’arborescence du schéma à **choix** ou **tous les**, respectivement.  
  
 Dans l’exemple suivant, la **enregistrement** nœud a été renommé en shipTo. Les emplacements dans le **enregistrement** nœud où les nœuds d’attribut et non-attributs sont ajoutés sont indiqués entre crochets.  
  
```  
<xs:element name="">  
    <xs:complexType>  
        <xs:sequence>  
            [Nonattribute child nodes of the record go here.]  
            [Always add new nonattribute child nodes to the end.]  
        </xs:sequence>  
            [Attribute child nodes of the record go here.]  
            [Always add new attribute child nodes to the end.]  
    </xs:complexType>  
</xs:element>  
  
```  
  
## <a name="see-also"></a>Voir aussi  
-  [Représentation BizTalk de schémas](../core/biztalk-representation-of-schemas.md)   
-  [Propriétés de nœud](../core/node-properties.md)   
-  **Enregistrer les propriétés d’un nœud** et **Order Type (propriété de nœud de tous les schémas) de groupe**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]
-  [Comment définir les propriétés de nœud](../core/how-to-set-node-properties.md)