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
# <a name="complex-global-type-definition-and-naming"></a><span data-ttu-id="4a092-102">Définition et attribution de nom à un type global complexe</span><span class="sxs-lookup"><span data-stu-id="4a092-102">Complex Global Type Definition and Naming</span></span>
<span data-ttu-id="4a092-103">Dans l'Éditeur BizTalk, pour commencer à définir un type global complexe, vous définissez la première occurrence du type complexe dans l'un des emplacements où le type global sera utilisé, après sa conversion en un type global.</span><span class="sxs-lookup"><span data-stu-id="4a092-103">Within BizTalk Editor, you begin to define a complex global type by defining the first occurrence of the complex type in one of the locations where the global type will be used, after it has been converted to a global type.</span></span> <span data-ttu-id="4a092-104">Dans le cas d'une adresse, vous pouvez définir le type d'adresse complexe pendant la définition d'une adresse de livraison dans le schéma.</span><span class="sxs-lookup"><span data-stu-id="4a092-104">Continuing with the address example, you might define the complex address type in the course of defining a shipping address within the schema.</span></span>  
  
 <span data-ttu-id="4a092-105">Une fois que le type complexe a été défini, vous pouvez le convertir en un type complexe global en lui attribuant un nom de type.</span><span class="sxs-lookup"><span data-stu-id="4a092-105">After the complex type is defined, you can convert it to a global complex type by giving it a type name.</span></span> <span data-ttu-id="4a092-106">Pour cela, sélectionnez le nœud qui correspond au type complexe, généralement un **enregistrement** nœud, puis en tapant un nouveau nom de type dans le **Data Structure Type** propriété de ce nœud.</span><span class="sxs-lookup"><span data-stu-id="4a092-106">You do this by selecting the node that corresponds to the complex type, which will generally be a **Record** node, and then typing a new type name into the **Data Structure Type** property of that node.</span></span> <span data-ttu-id="4a092-107">Bien qu’aucun changement visible ne se produire dans l’arborescence de schéma quand vous attribuez un nom à cette propriété (par exemple, **GlobalAddrType**, comme dans l’exemple suivant), si vous examinez ce qui se passe au sein de la représentation XSD sous-jacente du schéma, vous voyez la modification (abrégée) suivante.</span><span class="sxs-lookup"><span data-stu-id="4a092-107">Although no visible changes occur in the schema tree when you give this property a name (such as, **GlobalAddrType**, as in the following example), if you examine what happens within the underlying XSD representation of the schema, you would see the following (abbreviated) change.</span></span>  
  
 <span data-ttu-id="4a092-108">Avant, avec la structure d’adresse d’abord définie dans le contexte de la **ShippingAddress** les éléments suivants de l’élément, s’est produite.</span><span class="sxs-lookup"><span data-stu-id="4a092-108">Before, with the address structure first defined within the context of the **ShippingAddress** element, the following occurred.</span></span>  
  
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
  
 <span data-ttu-id="4a092-109">Après le **ShippingAddress** nœud a été attribué un nom unique dans son **Data Structure Type** propriété, à l’origine qu’il devienne disponible comme un type global complexe et réutilisation en plusieurs endroits dans le schéma, les événements suivants se produisent.</span><span class="sxs-lookup"><span data-stu-id="4a092-109">After the **ShippingAddress** node has been given a unique name in its **Data Structure Type** property, causing it to become available as a complex global type and subject to reuse in multiple places within the schema, the following occurs.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4a092-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4a092-110">See Also</span></span>  
 <span data-ttu-id="4a092-111">[Type réutilisation et dérivations](../core/type-reuse-and-derivations.md) </span><span class="sxs-lookup"><span data-stu-id="4a092-111">[Type Reuse and Derivations](../core/type-reuse-and-derivations.md) </span></span>  
 [<span data-ttu-id="4a092-112">Comment créer des références à un autre nœud ou Type</span><span class="sxs-lookup"><span data-stu-id="4a092-112">How to Create References to Another Node or Type</span></span>](../core/how-to-create-references-to-another-node-or-type.md)