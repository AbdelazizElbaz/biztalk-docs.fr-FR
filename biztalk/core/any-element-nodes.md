---
title: "Nœuds tout élément | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c7e30fcf-31bc-4d48-9bc7-0be90e927127
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c24eb75020f715245fc2b17f4bc1f81a7e34cd35
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="any-element-nodes"></a>Nœuds Tout élément
Dans l’Éditeur BizTalk, vous pouvez utiliser un **tout élément** nœud pour indiquer un emplacement au sein d’un message d’instance dans laquelle les éléments inconnus peuvent apparaître. Cela vous permet de parer aux situations où des éléments risquent d'apparaître à un emplacement particulier d'un message d'instance sans que vous en connaissiez le nom ou la complexité. Si vous placez un **tout élément** nœud à l’emplacement approprié dans le schéma, BizTalk peut traiter ces parties inconnues d’un message. La seule condition obligatoire est que l'XML correspondant soit bien formé.  
  
> [!NOTE]
>  Dans l’Éditeur BizTalk, le **tout élément** nœud est représenté par la chaîne \<tout > dans l’arborescence de schéma.  
  
> [!NOTE]
>  Vous pouvez contrôler le degré auquel la portion inconnue du message est validée en tant que XML bien formé à l’aide de la **Process Contents** propriété. Dans de nombreux cas, vous devrez définir le **Process Contents** propriété **ignorer** pour le contenu d’un message d’instance à l’emplacement de la **tout élément** nœud à traiter. En conservant la valeur par défaut **Strict** pour le **Process Contents** propriété empêchera la validation de message d’instance à partir de la transmission.  
> 
> Plus de détails sur cette propriété [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].
  
## <a name="xsd-representation"></a>Représentation XSD  
 Lorsqu’un **tout élément** nœud est ajouté à un **enregistrement** nœud, ou vers un autre nœud auquel il peut être ajouté comme un **groupe séquence**, **le groupe choix**, ou **groupe tous** nœud, une seule balise XML est ajouté à la définition de schéma XML correspondante représentation de langage (XSD) du schéma. Dans l’exemple suivant, un nouveau **tout élément** nœud, dont la représentation XSD est affichée en gras, a été ajouté à un fichier **enregistrement** nœud qui contient déjà un **élément de champ** nœud.  
  
```  
<xs:element name="ExistingRecord">  
    <xs:complexType>  
        <xs:sequence>  
             <xs:element name="ExistingFieldElement" type="xs:string" />  
            <xs:any />  
        </xs:sequence>  
    </xs:complexType>  
</xs:element>  
```  
  
 En supposant que le **Process Contents** propriété de la **tout élément** nœud a la valeur **ignorer**, dans un message d’instance est régie par ce fragment de schéma, un **ExistingRecord** élément doit contenir un **ExistingFieldElement** élément contenant les données de chaîne, suivie de n’importe quel élément unique d’une complexité arbitraire.  
  
## <a name="see-also"></a>Voir aussi  
 [Représentation BizTalk de schémas](../core/biztalk-representation-of-schemas.md)   
 [Propriétés de nœud](../core/node-properties.md)   
 [Comment définir les propriétés de nœud](../core/how-to-set-node-properties.md)   
 [Nœuds tout attribut](../core/any-attribute-nodes.md)