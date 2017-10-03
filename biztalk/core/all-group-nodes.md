---
title: "Tous les nœuds de groupe | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0e28d98c-746a-44d8-bed2-ba539b8432aa
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f51d6420b7d754ffb8706e2bc729a02df00b4338
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="all-group-nodes"></a>Nœuds Groupe Tous
Dans l’Éditeur BizTalk, vous pouvez insérer un **groupe tous** nœud destiné à contenir d’autres nœuds qui apparaîtront zéro ou une fois, dans n’importe quel ordre. Dans le langage de XML Schema definition (XSD), le **tous les groupe** présente des limitations d’utilisation plus que **séquence** et **choix** groupes, ce qui se traduit par certaines situations dans L’Éditeur BizTalk où vous serez en mesure de créer un **groupe tous** nœud.  
  
 Pour utiliser un **groupe tous** nœud dans l’Éditeur BizTalk, vous devez suivre des étapes supplémentaires : le moyen le plus simple pour créer un **groupe tous** nœud consiste à modifier la valeur de la **Group Order Type** propriété du parent **enregistrement** nœud **tous les**. Cela garantit que tous les nœuds subordonnés de le **enregistrement** nœud sont contenus dans le **groupe tous** nœud.  Consultez **Type d’ordre de groupe** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].
  
 Une autre façon d’utiliser un **groupe tous** dans l’Éditeur BizTalk commence par insérer un nouveau **enregistrement** nœud. Après avoir inséré la nouvelle **enregistrement** nœud, modifier son **le Type de contenu** propriété **ComplexContent**. Vous pouvez ensuite insérer un **groupe tous** nœud en tant qu’enfant de la **enregistrement** nœud. Cela est nécessaire car le **groupe tous** ne peuvent être insérés lors d’un héritage. En spécifiant que le contenant **enregistrement** nœud contient du contenu complexe, son type de données est alors basé sur le type de données **xs : anyType**, dérivé par extension.  
  
> [!NOTE]
>  Dans l’Éditeur BizTalk, le **groupe tous** nœud est représenté par la chaîne \<tous > dans l’arborescence de schéma. Si vous définissez une référence à un **groupe tous** nœud, telles que x, elle est représentée en tant que \<Group : x > dans l’arborescence de schéma.  
  
## <a name="xsd-representation"></a>Représentation XSD  
 Un **groupe tous** nœud peut être inséré dans un **enregistrement** nœud, mais uniquement si elle est le nœud enfant non-attribut uniquement de ce **enregistrement** nœud. L’exemple suivant illustre les étapes, un nouveau **groupe tous** nœud est représenté dans le langage de XML Schema definition (XSD) en tant qu’un **tous les** élément comme les étapes dans l’Éditeur BizTalk sont effectuées (avec les nœuds nommés pour les identifier).  
  
```  
<xs:element name="NewRecord">  
    <xs:complexType />   
</xs:element>  
```  
  
 Après avoir ajouté un nouvel enregistrement, comme indiqué dans le fragment XSD précédent, sa **le Type de contenu** propriété **ComplexContent**, se traduisant par les modifications XSD suivantes.  
  
```  
<xs:element name="NewRecord">  
    <xs:complexType>  
        <xs:complexContent mixed="false">  
             <xs:extension base="xs:anyType" />  
        </xs:complexContent>  
    </xs:complexType>  
</xs:element>  
```  
  
 Maintenant le **groupe tous** nœud peut être inséré en tant qu’enfant du nouvel enregistrement, comme indiqué dans le fragment XSD suivant.  
  
```  
<xs:element name="NewRecord">  
    <xs:complexType>  
        <xs:complexContent mixed="false">  
            <xs:extension base="xs:anyType">  
                <xs:all />   
             </xs:extension>  
          </xs:complexContent>  
     </xs:complexType>  
</xs:element>  
```  
  
 Enfin, vous pouvez insérer des nœuds appropriés en tant qu’enfants du nouveau **groupe tous** nœud. L’exemple suivant montre un **enregistrement** nœud et un **élément de champ** nœud inséré en tant que nœuds enfants du nouveau **groupe tous** nœud.  
  
```  
<xs:element name="NewRecord">  
    <xs:complexType>  
        <xs:complexContent mixed="false">  
            <xs:extension base="xs:anyType">  
                <xs:all>  
                    <xs:element name="RecordChildOfAllGroup">  
                        <xs:complexType />  
                    </xs:element>  
                    <xs:element name="FieldElementChildOfAllGroup" type="xs:string" />  
                </xs:all>  
            </xs:extension>  
        </xs:complexContent>  
    </xs:complexType>  
</xs:element>  
```  
  
## <a name="see-also"></a>Voir aussi  
-  [Représentation BizTalk de schémas](../core/biztalk-representation-of-schemas.md)   
-  [Propriétés de nœud](../core/node-properties.md)   
-  **Propriétés d’un nœud groupe séquence**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)] 
-  [Comment définir les propriétés de nœud](../core/how-to-set-node-properties.md)