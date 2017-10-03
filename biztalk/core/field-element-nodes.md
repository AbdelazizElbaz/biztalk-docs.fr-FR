---
title: "Nœuds d’élément de champ | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 65b5e1f6-283f-4172-9bc2-f04a0ea6753d
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 74c3732ee315ad307f49760e367449216c3e01da
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="field-element-nodes"></a>Nœuds Élément de champ

## <a name="overview"></a>Vue d'ensemble
Dans l’Éditeur BizTalk, vous utilisez **élément de champ** nœuds pour décrire les éléments d’information sont simples, tels que les chaînes et les nombres. Ils sont également utilisés lorsque les informations en question apparaissent comme contenu d'un élément XML de l'instance actuelle d'un message, et non pas comme la valeur d'un attribut associé à un élément XML. Pour plus d’informations sur les informations sont stockées en tant que valeurs d’attribut, consultez [nœuds attribut de champ](../core/field-attribute-nodes.md).  
  
> [!NOTE]
>  Dans l’Éditeur BizTalk, l’élément et les éléments de l’attribut peuvent être représentés par un **champ** nœud, même si elles ont des icônes différentes associées dans l’arborescence du schéma, une représentation XML différente dans la fenêtre XSD, et propriétés différentes dans la fenêtre Propriétés de Visual Studio.  
  
 Pour tout élément d'information d'un message XML, lorsque « élément d'information » désigne un unique type simple discret tel qu'une chaîne ou un nombre, il faut toujours se poser la question de savoir si cette information doit être représentée en tant qu'attribut d'un élément ou en tant que sous-élément de cet élément. En règle générale, représenter un élément d'information sous la forme d'un attribut a tendance à être plus approprié lorsque les valeurs possibles sont discrètes, peu nombreuses et tendent à modifier la sémantique de l'élément lui-même. Représenter un élément d'information sous la forme d'un sous-élément est souvent plus approprié lorsque les valeurs possibles peuvent se répéter un nombre variable de fois, sont susceptibles d'avoir des valeurs dont la fourchette sera plus étendue, peuvent être longues, comme c'est le cas avec les chaînes longues, et font partie de plusieurs valeurs frères pour lesquelles leur ordre est pertinent. Si vous créez simplement un schéma pour un type existant de code XML de document, votre choix d’utiliser un **élément de champ** nœud ou un **attribut de champ** nœud pour un élément d’information particulier a déjà été fait pour vous, et vous devez utiliser le nœud correspondant au document XML.  
  
## <a name="xsd-representation"></a>Représentation XSD  
 Lorsqu’un **élément de champ** nœud est inséré dans un **enregistrement** nœud, il est inséré à la fin de n’importe quel autre nœud enfant au sein de la **séquence** élément dans le  **Enregistrement** nœud. L’exemple suivant montre un nouveau **élément de champ** nœud, en gras, inséré à la fin de la **séquence** élément dans une **enregistrement** nœud (les nœuds sont nommés pour clarifier leur identité ).  
  
```  
<xs:element name="ContainingRecord">  
    <xs:complexType>  
        <xs:sequence>  
            <xs:element name="ExistingFieldElement" type="xs:string" />  
            <xs:element name="EmptyNestedRecord">  
                <xs:complexType />  
            </xs:element>  
  
        </xs:sequence>  
        <xs:attribute name="ExistingFieldAttribute" type="xs:string" />  
    </xs:complexType>  
</xs:element>  
  
```  
  
## <a name="see-also"></a>Voir aussi  
-  [Représentation BizTalk de schémas](../core/biztalk-representation-of-schemas.md)   
-  [Propriétés de nœud](../core/node-properties.md)   
-  **Propriétés de nœud d’élément de champ**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]
-  [Comment définir les propriétés de nœud](../core/how-to-set-node-properties.md)