---
title: "Opérations de mappage simples et complexes | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Max Occurs property
- maps, operation types
- source schemas, code sample
- BizTalk Mapper, mapping
- complex maps
- Table Looping functoids
- source schemas, maps
- maps, complex maps
- output instances
- destination schemas, code sample
- BizTalk Mapper, complex mapping
- destination schemas, maps
- maps, source schemas
- SrcLoopingRecord node
- functoid types, Looping
- DstLoopingRecord node
- Table Extractor functoids
- maps, basic maps
- BizTalk Mapper, basic mapping
- functoid types, Table Extractor
- messages, examples
- functoid types, Table Looping
- code samples, destination schemas
- Looping functoids
- input instances, code sample
- code samples, output instances
- basic maps
- code samples, input instances
- maps, map types
- code samples, source schemas
- maps, destination schemas
ms.assetid: da864b48-6255-4847-9a6f-13e489e8658d
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0d0fe41a85f23cdce3c4a070893cf54cb1b44a73
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="basic-and-complex-mapping-operations"></a>Opérations de mappage simples et complexes
Le Mappeur BizTalk propose des solutions pour divers scénarios de mappage, des opérations simples de type arborescence des relations parent-enfant jusqu'aux opérations détaillées et complexes impliquant des hiérarchies et des enregistrements de boucle. La complexité d’un scénario de mappage dépend de vos préférences et des besoins de l’entreprise ; le langage XSD (XML Schema Definition) vous offre une grande flexibilité pour la définition des formats structurés. Presque tous les scénarios de mappage se répartissent en deux catégories : mappage simple et mappage complexe.  
  
## <a name="basic-mapping"></a>Mappage simple  
 Le mappage simple est le type de mappage le plus courant. Dans un mappage simple, les éléments d’entrée et de sortie ont une relation un-à-un. À un élément d'entrée correspond un et un seul élément de sortie. Bien que de nombreux types de transformations et les traductions sont possibles avec le mappage de base, telles que l’utilisation de plusieurs *fonctoids* et en cascade pour manipuler la valeur en cours de copie, le scénario sous-jacent reste relativement simple. Les opérations de mappage simple incluent également le mappage de champs issus de deux enregistrements parents différents (se produisant une seule fois) avec des champs d’un seul enregistrement parent dans le schéma de destination.  
  
## <a name="complex-mapping"></a>Mappage complexe  
 Mappage complexe implique des enregistrements ou des champs qui apparaissent plusieurs fois pour une instance unique de la **enregistrement** ou **élément de champ** nœud dans l’arborescence du schéma. Ces nœuds possèdent leurs **Max Occurs** propriété définie sur une valeur supérieure à un (1), qui indique un message d’instance peut contenir plusieurs éléments correspondants. Lorsqu’un mappage BizTalk utilise ce type de mappage du nombre variable (également appelé *bouclage*), le compilateur de feuille de style de feuille de style XSL (Extensible Language) doit être en mesure de déterminer le bon chemin de bouclage sur lequel vous souhaitez effectuer une itération pour produire le sortie requise.  
  
 En règle générale, vous pouvez lier un champ d’un enregistrement de bouclage du schéma source à un champ se trouvant dans un enregistrement de bouclage du schéma de destination. Du nombre d’éléments correspondants dans un message d'instance d'entrée dépend le nombre d'éléments créés dans le message d'instance de sortie. Prenons l’exemple des fragments XSD suivants issus de schémas source et de destination hypothétiques.  
  
### <a name="source-schema-fragment"></a>Fragment de schéma source  
  
```  
<xs:element minOccurs="1" maxOccurs="5"  
            name="SrcLoopingRecord">  
  <xs:complexType>  
    <xs:sequence>  
      <xs:element name="" type="xs:string" />   
      <xs:element name="" type="xs:integer" />   
    </xs:sequence>  
  </xs:complexType>  
</xs:element>  
  
```  
  
### <a name="destination-schema-fragment"></a>Fragment de schéma de destination  
  
```  
<xs:element minOccurs="0" maxOccurs="unbounded"  
            name="DstLoopingRecord">  
  <xs:complexType>  
    <xs:sequence>  
      <xs:element name="" type="xs:string" />   
      <xs:element name="" type="xs:integer" />   
      </xs:sequence>  
    </xs:complexType>  
  </xs:element>  
  
```  
  
 Dans ces fragments :  
  
-   **SrcLoopingRecord**, un **enregistrement** nœud dans les messages d’instance d’entrée, peut se produire une à cinq fois. Il contient également l’enfant **Fieldelement** nœuds **Field1** (chaîne) et **Field2** (entier) qui se produisent une fois pour chaque instance de leur parent.  
  
-   **DstLoopingRecord**, un **enregistrement** nœud dans les messages d’instance de sortie, qui peut se produire zéro (0) ou plusieurs fois, non lié. Il contient également l’enfant **Fieldelement** nœuds **FieldA** (chaîne) et **FieldB** (entier) qui se produisent une fois pour chaque instance de leur parent.  
  
 En supposant que Field1 soit mappé sur FieldA et Field2 sur FieldB, et que le fragment suivant d'un message d'instance d'entrée ait traité ces mappages, le fragment suivant d'un message d'instance de sortie serait produit.  
  
### <a name="input-instance-message-fragment"></a>Fragment de message d’instance d’entrée  
  
```  
<SrcLoopingRecord>  
    <Field1>A string</Field1>  
    <Field2>10</Field2>  
</SrcLoopingRecord>  
<SrcLoopingRecord>  
    <Field1>Another string</Field1>  
    <Field2>11</Field2>  
</SrcLoopingRecord>  
<SrcLoopingRecord>  
    <Field1>A ball of string</Field1>  
    <Field2>12</Field2>  
</SrcLoopingRecord>  
```  
  
### <a name="output-instance-message-fragment"></a>Fragment de message d’instance de sortie  
  
```  
<DstLoopingRecord>  
    <FieldA>A string</FieldA>  
    <FieldB>10</FieldB>  
</DstLoopingRecord>  
<DstLoopingRecord>  
  <FieldA>Another string</FieldA>  
  <FieldB>11</FieldB>  
</DstLoopingRecord>  
<DstLoopingRecord>  
    <FieldA>A ball of string</FieldA>  
    <FieldB>12</FieldB>  
</DstLoopingRecord>  
```  
  
 Le nombre d’occurrences de la **SrcLoopingRecord** élément dans le message d’instance d’entrée (3) détermine le nombre d’occurrences de la **DstLoopingRecord** élément dans le message d’instance de sortie.  
  
 Le Mappeur BizTalk ne prend pas en charge le type de mappage présentant plusieurs chemins de bouclage. Ce type de mappage implique des champs de deux enregistrements de boucle ou plus dans le schéma source qui est mappé sur les champs d’un seul enregistrement de boucle dans le schéma de destination. Cela pose un problème dans la mesure où il n’y a pas de moyen efficace permettant de déterminer le nombre d’éléments à produire dans le message d’instance de sortie. La présence de plusieurs chemins de bouclage donne lieu à un avertissement de compilation de mappage indiquant que le nœud de destination comporte plusieurs chemins de bouclage source. Il ne s’agit, toutefois, que d’un avertissement, et le nombre d’itérations dans le premier chemin de bouclage source est utilisé pour déterminer le nombre d’éléments produits dans le message d’instance de sortie. Vous pouvez contrôler explicitement comportement de bouclage à l’aide de la **bouclage** fonctoid.  
  
 Microsoft [!INCLUDE[btsBizTalkServer2004](../includes/btsbiztalkserver2004-md.md)] a présenté un nouveau type de bouclage appelé bouclage piloté par la table. Le bouclage piloté par la table est utile lorsque le message d’instance de sortie doit être basé sur des données du message d’instance d’entrée en combinaison avec une ou plusieurs constantes, des liens du schéma source ou avec des fonctoids. Dans ces cas de figure, le message d'instance de sortie peut disposer de plusieurs enregistrements basés sur des données d'un seul enregistrement dans le message d’instance d’entrée combinées avec différentes constantes, ou basés sur des données issues de plusieurs enregistrements dans le message d’instance d’entrée. Pour plus d’informations sur piloté par table de bouclage à l’aide de la **bouclage de Table** et **extracteur de Table** fonctoids, consultez [bouclage de Table et de fonctoids Extracteur de Table](../core/table-looping-and-table-extractor-functoids.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Mappages](../core/maps.md)   
 [Création de mappages à l’aide du Mappeur BizTalk](../core/creating-maps-using-biztalk-mapper.md)