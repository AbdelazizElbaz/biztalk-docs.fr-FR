---
title: "Définition de Type Global complexe et d’affectation de noms | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b5a12956-7b77-4be8-b323-38363d04fcbc
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: afe00c68f22dde956279f2dd5ac06d03bf9cb84d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="complex-global-type-definition-and-naming"></a>Définition et attribution de nom à un type global complexe
Dans l'Éditeur BizTalk, pour commencer à définir un type global complexe, vous définissez la première occurrence du type complexe dans l'un des emplacements où le type global sera utilisé, après sa conversion en un type global. Dans le cas d'une adresse, vous pouvez définir le type d'adresse complexe pendant la définition d'une adresse de livraison dans le schéma.  
  
 Une fois que le type complexe a été défini, vous pouvez le convertir en un type complexe global en lui attribuant un nom de type. Pour cela, sélectionnez le nœud qui correspond au type complexe, généralement un **enregistrement** nœud, puis en tapant un nouveau nom de type dans le **Data Structure Type** propriété de ce nœud. Bien qu’aucun changement visible ne se produire dans l’arborescence de schéma quand vous attribuez un nom à cette propriété (par exemple, **GlobalAddrType**, comme dans l’exemple suivant), si vous examinez ce qui se passe au sein de la représentation XSD sous-jacente du schéma, vous voyez la modification (abrégée) suivante.  
  
 Avant, avec la structure d’adresse d’abord définie dans le contexte de la **ShippingAddress** les éléments suivants de l’élément, s’est produite.  
  
```  
<xs:schema>  
  <xs:element name="Root">  
    <xs:complexType>  
      <xs:sequence>  
        <xs:element name="ShippingAddress">  
        [address structure initially defined here.]  
        </xs:element>  
      </xs:sequence>  
    </xs:complexType>  
  </xs:element>  
</xs:schema>  
```  
  
 Après le **ShippingAddress** nœud a été attribué un nom unique dans son **Data Structure Type** propriété, à l’origine qu’il devienne disponible comme un type global complexe et réutilisation en plusieurs endroits dans le schéma, les événements suivants se produisent.  
  
```  
<xs:schema>  
  <xs:element name="Root">  
    <xs:complexType>  
      <xs:sequence>  
        <xs:element name="ShippingAddress" type="GlobalAddrType" />  
      </xs:sequence>  
    </xs:complexType>  
  </xs:element>  
  <xs:complexType name="GlobalAddrType">  
  [address structure now defined globally here.]  
  </xs:complexType>  
</xs:schema>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Type réutilisation et dérivations](../core/type-reuse-and-derivations.md)   
 [Comment créer des références à un autre nœud ou Type](../core/how-to-create-references-to-another-node-or-type.md)