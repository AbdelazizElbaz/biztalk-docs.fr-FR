---
title: "Nœuds groupe choix | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 466b525d-4d8c-4b8e-830d-eee27845c0dc
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 21d3007897343b7d517c11599a271b72e92d3710
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="choice-group-nodes"></a>Nœuds Groupe Choix
Dans l’Éditeur BizTalk, vous pouvez insérer un **groupe choix** nœud destiné à contenir les autres nœuds (ou des sous-arborescences entières de nœuds), un seul d'entre eux peut s’afficher dans un message d’instance. Un message d’instance donné, s’il est valide, ne comportera que l'un des choix présents. Les nœuds contenus doivent correspondre à des éléments XML, et non à des attributs XML.  
  
> [!NOTE]
>  Dans l’Éditeur BizTalk, le **groupe choix** nœud est représenté par la chaîne \<choix\> dans l’arborescence de schéma. Si vous définissez une référence à un **groupe choix** nœud, tel que x, elle est représentée en tant que \<Group : x\> dans l’arborescence de schéma.  
  
## <a name="xsd-representation"></a>Représentation XSD  
 Quand un **groupe choix** nœud est inséré dans un **enregistrement** nœud, il est inséré à la fin de n’importe quel autre nœud enfant au sein de la **séquence**, **choix**, ou **tous les** élément dans le **enregistrement** nœud. L’exemple suivant montre, en caractères gras, un nouveau **groupe choix** nœud est représenté dans le langage de XML Schema definition (XSD) en tant qu’un **choix** élément inséré à la fin de la **séquence**  élément dans une **enregistrement** nœud (les nœuds nommés pour clarifier leur identité).  
  
```  
<xs:element name="ContainingRecord">  
    <xs:complexType>  
        <xs:sequence>  
            <xs:element name="ExistingFieldElement" type="xs:string" />  
        </xs:sequence>  
    </xs:complexType>  
</xs:element>  
  
```  
  
 Par défaut, le **choix** élément reçoit un **minOccurs** attribut la valeur zéro (0), indiquant qu’aucun choix doivent se produire. Vous pouvez modifier cette valeur dans la fenêtre Propriétés de Visual Studio lorsque le **groupe choix** nœud est sélectionné dans l’arborescence du schéma.  
  
 L’exemple suivant montre la même **choix** élément avec le XSD **élément** éléments correspondant aux deux subordonné **enregistrement** nœuds.  
  
```  
<xs:element name="ContainingRecord">  
    <xs:complexType>  
        <xs:sequence>  
            <xs:element name="ExistingFieldElement" type="xs:string" />  
            <xs:choice minOccurs="1" maxOccurs="1">  
                <xs:element name="usAddress">  
                    <xs:complexType>  
                        <xs:sequence>  
                        </xs:sequence>  
                    </xs:complexType>  
                </xs:element>  
                <xs:element name="foreignAddress">  
                    <xs:complexType>  
                        <xs:sequence>  
                        </xs:sequence>  
                    </xs:complexType>  
                </xs:element>  
            </xs:choice>  
        </xs:sequence>  
    </xs:complexType>  
</xs:element>  
```  
  
 Dans cet exemple, deux frères **enregistrement** nœuds sont utilisés pour décrire le fait qu’un message d’instance sera avoir un enregistrement avec les informations d’adresse des États-Unis, ou un enregistrement avec les informations d’adresse dans le monde entier. En outre, le **minOccurs** et **maxOccurs** propriétés de la **groupe choix** nœud ont été définis sur un (1) dans la fenêtre Propriétés de Visual Studio, ce qui entraîne la *minOccurs* et *maxOccurs* les attributs de la **choix** élément définie sur un (1) dans la représentation XSD.  
  
## <a name="see-also"></a>Voir aussi  
-  [Représentation BizTalk de schémas](../core/biztalk-representation-of-schemas.md)   
-  [Propriétés de nœud](../core/node-properties.md)   
-  **Propriétés d’un nœud groupe séquence**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]     
-  [Comment définir les propriétés de nœud](../core/how-to-set-node-properties.md)