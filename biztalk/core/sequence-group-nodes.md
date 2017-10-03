---
title: "Nœuds groupe séquence | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 139c3daa-a682-4bf7-bbb7-b5694ced0431
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2465ad10e6598a4b9e1afa88190de4c1711c1f86
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="sequence-group-nodes"></a>Nœuds Groupe Séquence

## <a name="overview"></a>Vue d'ensemble
Dans l’Éditeur BizTalk, vous pouvez insérer un **groupe séquence** nœud destiné à contenir d’autres nœuds qui doivent apparaître dans un message d’instance dans le même ordre que celui dans lequel ils apparaissent dans le **groupe séquence** nœud. Les nœuds contenus doivent correspondre à des éléments XML, et non à des attributs XML.  
  
> [!NOTE]
>  Dans l’Éditeur BizTalk, le **groupe séquence** nœud est représenté par défaut par la chaîne \<séquence > dans l’arborescence de schéma. Si vous définissez une référence à un **groupe séquence** nœud, tel que x, elle est représentée en tant que \<Group : x > dans l’arborescence de schéma.  
  
 Il pouvez que vous souhaitez ajouter un **groupe séquence** pour déclarer un groupe de l’élément global.  
  
 Vous pouvez avoir besoin de créer un schéma pour XML comme indiqué ci-dessous.  
  
```  
<Root>  
    <Record1>  
        <GroupItem1/>  
        <GroupItem2/>  
        <NotAGroupItem>  
    </Record1>  
    <Record2>  
        <GroupItem1/>  
        <GroupItem2/>  
    </Record2>  
</Root>  
  
```  
  
 GroupItem1 et GroupItem2 existant dans les deux cas, vous pouvez déclarer un groupe de séquence global qui correspond à un enfant à la fois de Record1 et de Record2. Pour obtenir des instructions sur la façon de déclarer un groupe de séquences global, consultez [création de références à un autre nœud ou Type](../core/how-to-create-references-to-another-node-or-type.md).  
  
 Un utilisateur peut modifier le groupe masqué pour être un **groupe choix** nœud ou un **groupe tous** nœud (afin qu’il n’est pas nécessairement un **groupe séquence** nœud) en modifiant le  **Type de l’ordre de groupe** propriété. Plus de détails sur cette propriété [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].
  
## <a name="xsd-representation"></a>Représentation XSD  
 Lorsqu’un **groupe séquence** nœud est inséré dans un **enregistrement** nœud, il est inséré à la fin de n’importe quel autre nœud enfant au sein de la **séquence**, **choix**, ou **tous les** élément dans le **enregistrement** nœud. L’exemple suivant montre un nouveau **groupe séquence** nœud, en caractères gras, inséré à la fin de la **séquence** élément dans une **enregistrement** nœud (les nœuds sont nommés pour clarifier leur identité).  
  
```  
<xs:element name="ContainingRecord">  
    <xs:complexType>  
        <xs:sequence>  
            <xs:element name="ExistingFieldElement" type="xs:string" />  
        </xs:sequence>  
    </xs:complexType>  
</xs:element>  
  
```  
  
## <a name="see-also"></a>Voir aussi  
-  [Représentation BizTalk de schémas](../core/biztalk-representation-of-schemas.md)   
-  [Propriétés de nœud](../core/node-properties.md)   
-  **Propriétés d’un nœud groupe séquence**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]
-  [Comment définir les propriétés de nœud](../core/how-to-set-node-properties.md)