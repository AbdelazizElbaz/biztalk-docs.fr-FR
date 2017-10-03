---
title: "Nœuds groupe attribut | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ea02fae8-4e03-486a-8d9d-185ae230d3a0
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 04db816f1209b7cd503b9a162cdd2a030ba86292
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="attribute-group-nodes"></a>Nœuds Groupe Attribut

## <a name="overview"></a>Vue d'ensemble
Dans l’Éditeur BizTalk, vous pouvez ajouter un **groupe d’attributs** nœud à un **enregistrement** nœud ou à un autre **groupe d’attributs** nœud destiné à contenir un groupe d’attributs que vous prévoyez d’utiliser plus plusieurs **enregistrement** nœud. Ajout d’un **groupe d’attributs** nœud vers un autre **groupe d’attributs** nœud réalise l’imbrication de groupes d’attributs. Cela vous permet de définir un groupe d’attributs dans un emplacement qui peut être utilisé dans plusieurs **enregistrement** ou **groupe d’attributs** nœuds. Les modifications apportées par la suite au groupe d'attributs se propageront vers tous les nœuds auxquels il est associé  et ce, quel que soit le contexte de nœud dans lequel les modifications sont effectuées.  
  
> [!NOTE]
>  Dans l’Éditeur BizTalk, le **AttributeGroup** nœud est représenté par défaut par la chaîne \<AttribGroup:attribGroup*N*> dans l’arborescence du schéma, où *N*est un nombre croissant. Vous pouvez modifier la partie attribGroup*N* partie de son nom en tapant un nouveau nom unique dans son **référence du groupe** propriété.  
  
 Lorsque vous créez initialement un **groupe d’attributs** nœud, vous simplement l’insérer dans un de la **enregistrement** ou **groupe d’attributs** nœuds dans lequel il sera utilisé et éventuellement modifier son nom dans sa **référence du groupe** propriété. Il existe deux façons d’utiliser le même groupe d’attributs dans un autre **enregistrement** ou **groupe d’attributs** nœud :  
  
-   Vous pouvez copier existants **groupe d’attributs** nœud et le coller ensuite dans l’autre **enregistrement** nœud.  
  
-   Vous pouvez insérer un nouveau **groupe d’attributs** nœud dans l’autre **enregistrement** nœud et définissez la **référence du groupe** propriété du nouveau **grouped’attributs** nœud pour référencer un existant **groupe d’attributs** nœud.  
  
 Par la suite, vous pouvez modifier le **groupe d’attributs** nœud — par exemple, en ajoutant ou supprimant un **attribut de champ** nœud, dans le contexte de n’importe quel **enregistrement** ou  **Groupe d’attributs** nœud dans lequel vous l’avez collé. Cette modification se propage à tous les autres **enregistrement** ou **groupe d’attributs** nœuds auquel le groupe d’attributs est associé.  
  
 Il est inutile d’ajouter un **groupe d’attributs** nœud sans ajouter au moins un nœud approprié, où les nœuds appropriés contiennent **attribut de champ** nœuds, **tout attribut**nœuds et (imbriquée) **groupe d’attributs** nœuds. En fait, un groupe d'attributs contenant seulement un attribut unique n'est guère souhaitable à moins que l'idée ne soit d'ajouter d'autres attributs par la suite.  
  
 **Groupe d’attributs** nœuds peuvent être imbriqués, ce qui permet de plus de possibilités de comment les groupes d’attributs peuvent être construites et combinés. **Groupe d’attributs** peuvent également contenir des nœuds de la **tout attribut** nœud, ce qui permet de contenir des fonctions de caractères génériques en ce qui concerne les instances d’attribut qu’il peut prendre en charge d’un groupe d’attributs.  
  
## <a name="xsd-representation"></a>Représentation XSD  
 Lorsqu’un **groupe d’attributs** nœud est ajouté pour la première fois à un **enregistrement** nœud ou à une autre **groupe d’attributs** nœud, deux zones distinctes de la définition de schéma XML (XSD) correspondante représentation de langage du schéma sont affectées. Dans l’exemple suivant, un nouveau **groupe d’attributs** nœud, en gras, a été ajouté à un fichier **enregistrement** nœud qui contient déjà un existant **élément de champ** nœud.  
  
```  
        ...  
        <xs:element name="ExistingRecord">  
            <xs:complexType>  
                <xs:sequence>  
                    <xs:element name="ExistingFieldElement" type="xs:string" />  
                </xs:sequence>  
                <xs:attributeGroup ref="attrGroup0" />  
            </xs:complexType>  
        </xs:element>  
        ...   
    <xs:attributeGroup name="attrGroup0" />  
</xs:schema>  
```  
  
 Remarque la **attributeGroup** élément au sein de la représentation XSD du **enregistrement** nœud fait référence à un élément global **attributeGroup** élément est ajouté en tant qu’enfant de la **schéma** élément. Cette définition globale du groupe d'attributs dans la représentation XSD du schéma permet au groupe d'attributs d'être référencé à plusieurs emplacements du schéma.  
  
> [!NOTE]
>  Noms de groupe d’attributs par défaut sont fournis automatiquement la forme ont*N*, où *N* est un nombre croissant. Vous pouvez renommer un groupe d’attributs en fournissant un nouveau nom unique dans son **référence du groupe** propriété. Un groupe d'attributs ne peut pas être renommé directement dans l'arborescence de schéma.  
  
## <a name="see-also"></a>Voir aussi  
-  [Représentation BizTalk de schémas](../core/biztalk-representation-of-schemas.md)   
-  [Propriétés de nœud](../core/node-properties.md)   
-  **Propriétés d’un nœud groupe séquence**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]  
-  [Comment définir les propriétés de nœud](../core/how-to-set-node-properties.md)   
-  [Nœuds attribut de champ](../core/field-attribute-nodes.md)   
-  [Nœuds tout attribut](../core/any-attribute-nodes.md)