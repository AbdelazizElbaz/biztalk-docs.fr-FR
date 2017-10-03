---
title: "Les nœuds d’attribut | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fa2d25bc-3a8f-4fd9-acad-341b8e80c737
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: aa3542c2703dfba986d158b40e54982f92b8543c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="any-attribute-nodes"></a>Nœuds Tout Attribut
Dans l’Éditeur BizTalk, vous pouvez utiliser un **tout attribut** nœud pour indiquer un élément (connu) au sein d’un message d’instance qui peuvent contenir zéro ou plusieurs attributs inconnus. C'est une parade aux situations dans lesquelles vous savez qu'un élément particulier sera présent à un emplacement particulier d'un message d'instance sans connaître exactement quels attributs cet élément est susceptible de comporter. Si vous placez un **tout attribut** nœud dans le **enregistrement** nœud associé à l’élément approprié, BizTalk peut traiter ce, à la seule condition est que tous les attributs associés sont corriger syntaxe (attributeName = « attributeValue »).  
  
> [!NOTE]
>  Dans l’Éditeur BizTalk, le **tout attribut** nœud est représenté par la chaîne \<AnyAttribute > dans l’arborescence de schéma.  
  
> [!NOTE]
>  Vous pouvez contrôler le degré auquel la portion inconnue du message est validée en tant que XML bien formé à l’aide de la **Process Contents** propriété. Dans de nombreux cas, vous devrez définir le **Process Contents** propriété **ignorer** pour le contenu d’un message d’instance à l’emplacement de la **tout attribut** nœud à traiter . En conservant la valeur par défaut **Strict** pour le **Process Contents** propriété empêchera la validation de message d’instance à partir de la transmission.  
>
> Plus de détails sur cette propriété [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].
  
## <a name="xsd-representation"></a>Représentation XSD  
 Lorsqu’un **tout attribut** nœud est ajouté à un **enregistrement** nœud ou à un **groupe d’attributs** nœud, une seule balise XML est ajouté à la définition de schéma XML correspondante de langage (XSD) représentation du schéma. Dans l’exemple suivant, un nouveau **tout attribut** nœud, dont la représentation XSD est affichée en gras, a été ajouté à un fichier **enregistrement** nœud qui contient déjà un **élément de champ** nœud.  
  
```  
<xs:element name="ExistingRecord">  
    <xs:complexType>  
        <xs:sequence>  
            <xs:element name="ExistingFieldElement" type="xs:string" />  
        </xs:sequence>  
        <xs:anyAttribute />  
    </xs:complexType>  
</xs:element  
```  
  
 Dans l’exemple précédent, la représentation XSD du nouveau **tout attribut** nœud ajoute un **anyAttribute** élément à la fin du conteneur (**enregistrement** nœud) **élément** élément, en dehors du **séquence** élément et, dans le **complexType** élément. Cette propriété est si tous les **attribut** éléments, autres que celles avec un **groupe d’attributs** nœud, sont ajoutés à leurs **élément** éléments.  
  
 Maintenant et en supposant que le **Process Contents** propriété de la **tout attribut** nœud a la valeur **ignorer**, à l’intérieur un message d’instance est régie par ce fragment de schéma, un  **ExistingRecord** élément est attendu, et il peut contenir des attributs afin qu’elles sont bien formées en ce qui concerne la syntaxe XML. (Pour le rendre conforme au fragment XSD dans cet exemple, il doit également contenir le **ExistingFieldElement** élément.)  
  
## <a name="see-also"></a>Voir aussi  
 [Représentation BizTalk de schémas](../core/biztalk-representation-of-schemas.md)   
 [Propriétés de nœud](../core/node-properties.md)   
 [Comment définir les propriétés de nœud](../core/how-to-set-node-properties.md)   
 [Nœuds tout élément](../core/any-element-nodes.md)