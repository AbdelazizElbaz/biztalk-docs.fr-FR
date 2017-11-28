---
title: "Enregistrer des nœuds | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 43af077d-5db8-43ca-8bd0-e3a9e3ebe2b0
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4486b875693827c6fed74e9293bdb68b2c3dc3b2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="record-nodes"></a><span data-ttu-id="87d44-102">Nœuds Enregistrement</span><span class="sxs-lookup"><span data-stu-id="87d44-102">Record Nodes</span></span>
<span data-ttu-id="87d44-103">Dans l’Éditeur BizTalk, vous utilisez un **enregistrement** nœud pour représenter une collection d’informations, les éléments individuels qui peuvent être :</span><span class="sxs-lookup"><span data-stu-id="87d44-103">In BizTalk Editor, you use a **Record** node to represent a collection of information, the individual items of which can be:</span></span>  
  
-   <span data-ttu-id="87d44-104">des types d'informations simples, telles que des chaînes et des nombres, représentés sous forme de nœuds de champs enfants.</span><span class="sxs-lookup"><span data-stu-id="87d44-104">Simple types of information, such as strings and numbers, represented as child field nodes.</span></span> <span data-ttu-id="87d44-105">Ces nœuds de champ enfant peuvent être **Fieldelement** nœuds ou **attribut de champ** nœuds.</span><span class="sxs-lookup"><span data-stu-id="87d44-105">These child field nodes can be either **Field Element** nodes or **Field Attribute** nodes.</span></span> <span data-ttu-id="87d44-106">Pour plus d’informations sur ces deux types de nœuds de champ, consultez [nœuds élément de champ](../core/field-element-nodes.md) et [nœuds attribut de champ](../core/field-attribute-nodes.md).</span><span class="sxs-lookup"><span data-stu-id="87d44-106">For additional information about these two types of field nodes, see [Field Element Nodes](../core/field-element-nodes.md) and [Field Attribute Nodes](../core/field-attribute-nodes.md).</span></span>  
  
-   <span data-ttu-id="87d44-107">Les types complexes d’informations, représentée en tant qu’enfant **enregistrement** nœuds ou sous la forme d’un nœud de groupe (**groupe séquence** nœud, **groupe choix** nœud, ou **groupe** nœud).</span><span class="sxs-lookup"><span data-stu-id="87d44-107">Complex types of information, represented as child **Record** nodes or as a group node (**Sequence Group** node, **Choice Group** node, or **All Group** node).</span></span>  
  
-   <span data-ttu-id="87d44-108">N’importe quel type sans examen d’informations, représentée en tant qu’enfant **tout élément** ou **tout attribut** nœuds.</span><span class="sxs-lookup"><span data-stu-id="87d44-108">Any unexamined type of information, represented as child **Any Element** or **Any Attribute** nodes.</span></span>  
  
-   <span data-ttu-id="87d44-109">Groupes d’attributs représentés par une **groupe d’attributs** nœud.</span><span class="sxs-lookup"><span data-stu-id="87d44-109">Groups of attributes represented by an **Attribute Group** node.</span></span>  
  
 <span data-ttu-id="87d44-110">Lorsque vous insérez un nouveau nœud enfant dans un **enregistrement** nœud, le nœud enfant est toujours inséré à la fin des nœuds enfants en cours.</span><span class="sxs-lookup"><span data-stu-id="87d44-110">When you insert a new child node into a **Record** node, the child node is always inserted at the end of the current child nodes.</span></span> <span data-ttu-id="87d44-111">Dans la représentation de langage XML Schema definition (XSD), les nouveaux éléments sont ajoutés à la fin de leurs zones correspondants, ce qui signifie que les éléments non-attribut sont ajoutées à la fin des éléments dans le **séquence**, **choix**, **tous les**, ou **groupe** élément et attribut des éléments sont ajoutés à la fin de tous les autres éléments d’attribut, qui se produisent après le **séquence** , **choix**, **tous les**, ou **groupe** élément.</span><span class="sxs-lookup"><span data-stu-id="87d44-111">Within the XML Schema definition (XSD) language representation, new elements are added to the end of their corresponding areas, meaning that nonattribute elements are added to the end of the elements within the **sequence**, **choice**, **all**, or **group** element, and attribute elements are added to the end of any other attribute elements, all of which occur after the **sequence**, **choice**, **all**, or **group** element.</span></span>  
  
## <a name="xsd-representation"></a><span data-ttu-id="87d44-112">Représentation XSD</span><span class="sxs-lookup"><span data-stu-id="87d44-112">XSD representation</span></span>  
 <span data-ttu-id="87d44-113">Lors de la première insertion, la représentation XSD d’un nouveau **enregistrement** nœud se compose de trois lignes uniquement, comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="87d44-113">When first inserted, the XSD representation of a new **Record** node consists of only three lines, as shown in the following example.</span></span>  
  
```  
<xs:element name="Record">  
      <xs:complexType />  
</xs:element>  
```  
  
 <span data-ttu-id="87d44-114">Lorsque n’importe quel nœud enfant autre qu’un des nœuds de le trois attribut (**attribut de champ**, **groupe d’attributs**, et **tout attribut**) est ajouté à un **enregistrement** nœud, par défaut, il est placé dans un **séquence** élément dans le **complexType** élément.</span><span class="sxs-lookup"><span data-stu-id="87d44-114">When any child node other than one of the three attribute nodes (**Field Attribute**, **Attribute Group**, and **Any Attribute**) is added to a **Record** node, by default it is placed within a **sequence** element within the **complexType** element.</span></span> <span data-ttu-id="87d44-115">Le **séquence** élément est ajouté lorsque le premier nœud non-attribut enfant est ajouté et supprimé si tous les nœuds enfants non-attributs sont supprimés.</span><span class="sxs-lookup"><span data-stu-id="87d44-115">The **sequence** element is added when the first nonattribute child node is added, and removed if all the nonattribute child nodes are deleted.</span></span> <span data-ttu-id="87d44-116">Les trois types de nœuds d’attribut sont ajoutées au sein de la **complexType** élément, mais à l’extérieur et après chaque **séquence** élément.</span><span class="sxs-lookup"><span data-stu-id="87d44-116">All three types of attribute nodes are added within the **complexType** element, but outside and after any **sequence** element.</span></span>  
  
 <span data-ttu-id="87d44-117">Le **séquence** élément au sein de quel non-attribut nœuds enfants sont ajoutés peut également être un **choix** ou **tous les** élément si vous modifiez le **Group Order Type (nœud Propriété de tous les schémas)** propriété du nœud correspondant dans l’arborescence du schéma à **choix** ou **tous les**, respectivement.</span><span class="sxs-lookup"><span data-stu-id="87d44-117">The **sequence** element within which nonattribute child nodes are added can also be a **choice** or **all** element if you change the **Group Order Type (Node Property of All Schemas)** property of the corresponding node in the schema tree to **Choice** or **All**, respectively.</span></span>  
  
 <span data-ttu-id="87d44-118">Dans l’exemple suivant, la **enregistrement** nœud a été renommé en shipTo.</span><span class="sxs-lookup"><span data-stu-id="87d44-118">In the following example, the **Record** node has been renamed shipTo.</span></span> <span data-ttu-id="87d44-119">Les emplacements dans le **enregistrement** nœud où les nœuds d’attribut et non-attributs sont ajoutés sont indiqués entre crochets.</span><span class="sxs-lookup"><span data-stu-id="87d44-119">The locations within the **Record** node where attribute and nonattribute nodes are added are shown in brackets.</span></span>  
  
```  
<xs:element name="">  
    <xs:complexType>  
        <xs:sequence>  
            [Nonattribute child nodes of the record go here.]  
            [Always add new nonattribute child nodes to the end.]  
        </xs:sequence>  
            [Attribute child nodes of the record go here.]  
            [Always add new attribute child nodes to the end.]  
    </xs:complexType>  
</xs:element>  
  
```  
  
## <a name="see-also"></a><span data-ttu-id="87d44-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="87d44-120">See Also</span></span>  
-  [<span data-ttu-id="87d44-121">Représentation BizTalk de schémas</span><span class="sxs-lookup"><span data-stu-id="87d44-121">BizTalk Representation of Schemas</span></span>](../core/biztalk-representation-of-schemas.md)   
-  [<span data-ttu-id="87d44-122">Propriétés de nœud</span><span class="sxs-lookup"><span data-stu-id="87d44-122">Node Properties</span></span>](../core/node-properties.md)   
-  <span data-ttu-id="87d44-123">**Enregistrer les propriétés d’un nœud** et **Order Type (propriété de nœud de tous les schémas) de groupe**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span><span class="sxs-lookup"><span data-stu-id="87d44-123">**Record Node Properties** and **Group Order Type (Node Property of All Schemas)** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span></span>
-  [<span data-ttu-id="87d44-124">Comment définir les propriétés de nœud</span><span class="sxs-lookup"><span data-stu-id="87d44-124">How to Set Node Properties</span></span>](../core/how-to-set-node-properties.md)