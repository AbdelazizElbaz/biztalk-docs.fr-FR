---
title: "Nœuds d’attribut de champ | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9e964c07-53e5-473f-84f2-05af4796cbbe
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 701acadc9d1612cc5b05a05970fc2c1b92bfbb9a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="field-attribute-nodes"></a><span data-ttu-id="c5590-102">Nœuds Attribut de champ</span><span class="sxs-lookup"><span data-stu-id="c5590-102">Field Attribute Nodes</span></span>

## <a name="overview"></a><span data-ttu-id="c5590-103">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="c5590-103">Overview</span></span>
<span data-ttu-id="c5590-104">Dans l’Éditeur BizTalk, vous utilisez **attribut de champ** nœuds pour décrire les éléments d’information sont simples, tels que les chaînes et les nombres.</span><span class="sxs-lookup"><span data-stu-id="c5590-104">In BizTalk Editor, you use **Field Attribute** nodes to describe items of information that are simple in nature, such as strings and numbers.</span></span> <span data-ttu-id="c5590-105">Ils sont également utilisés lorsque les informations en question apparaissent sous la forme de la valeur d'un attribut dans une instance actuelle d'un message, et non pas comme le contenu d'un élément XML.</span><span class="sxs-lookup"><span data-stu-id="c5590-105">Further, they are used when the information in question appears as the value of an attribute in an actual instance of a message, as opposed to appearing as the content of an XML element.</span></span> <span data-ttu-id="c5590-106">Pour plus d’informations sur les informations sont stockées en tant que contenu de l’élément, consultez [nœuds élément de champ](../core/field-element-nodes.md).</span><span class="sxs-lookup"><span data-stu-id="c5590-106">For additional information about information that is stored as element content, see [Field Element Nodes](../core/field-element-nodes.md).</span></span>  
  
 <span data-ttu-id="c5590-107">Bien que le plus simple utilisation de **attribut de champ** nœuds est en tant que nœuds enfants du **enregistrement** nœuds, elles peuvent également servir en tant que nœuds enfants du **groupe d’attributs** nœuds.</span><span class="sxs-lookup"><span data-stu-id="c5590-107">Although the most straightforward use of **Field Attribute** nodes is as child nodes of **Record** nodes, they can also be used as child nodes of **Attribute Group** nodes.</span></span> <span data-ttu-id="c5590-108">Dans ce cas, le **attribut de champ** les nœuds qui sont des enfants une **groupe d’attributs** nœud sont disponibles en tant qu’attributs de n’importe quel **enregistrement** nœud qui inclut ce  **Groupe d’attributs** nœud.</span><span class="sxs-lookup"><span data-stu-id="c5590-108">In the latter case, the **Field Attribute** nodes that are children of an **Attribute Group** node are available as attributes of any **Record** node that includes that **Attribute Group** node.</span></span> <span data-ttu-id="c5590-109">Pour plus d’informations sur **groupe d’attributs** nœuds, voir [nœuds groupe attribut](../core/attribute-group-nodes.md).</span><span class="sxs-lookup"><span data-stu-id="c5590-109">For more information about **Attribute Group** nodes, see [Attribute Group Nodes](../core/attribute-group-nodes.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c5590-110">Dans l’Éditeur BizTalk, l’élément et les éléments de l’attribut peuvent être représentés par un **champ** nœud, même si elles ont des icônes différentes associées dans l’arborescence du schéma, une représentation XML différente dans la fenêtre XSD, et propriétés différentes dans la fenêtre Propriétés de Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c5590-110">In BizTalk Editor, both the element and attribute elements can be represented by a **Field** node, though they have different icons associated with them in the schema tree view, a different XML representation in the XSD window, and different properties in the Visual Studio Properties window.</span></span>  
  
 <span data-ttu-id="c5590-111">Pour tout élément d'information d'un message XML, lorsque « élément d'information » désigne un unique type simple discret tel qu'une chaîne ou un nombre, il faut toujours se poser la question de savoir si cette information doit être représentée en tant qu'attribut d'un élément ou en tant que sous-élément de cet élément.</span><span class="sxs-lookup"><span data-stu-id="c5590-111">For any given item of information in an XML message, where item of information means a single discrete simple type, such as a string or number, there is always a question regarding whether that information should be represented as the attribute of an element, or as a subelement of that element.</span></span> <span data-ttu-id="c5590-112">En règle générale, représenter un élément d'information sous la forme d'un attribut a tendance à être plus approprié lorsque les valeurs possibles sont discrètes, peu nombreuses et tendent à modifier la sémantique de l'élément lui-même.</span><span class="sxs-lookup"><span data-stu-id="c5590-112">As a general rule, representing an item of information as an attribute tends to be more appropriate when the possible values are discrete, few in number, and tend to modify the semantics of the element itself.</span></span> <span data-ttu-id="c5590-113">Représenter un élément d'information sous la forme d'un sous-élément est souvent plus approprié lorsque les valeurs possibles peuvent se répéter un nombre variable de fois, sont susceptibles d'avoir des valeurs dont la fourchette sera plus étendue, peuvent être longues, comme c'est le cas avec les chaînes longues, et font partie de plusieurs valeurs frères pour lesquelles leur ordre est pertinent.</span><span class="sxs-lookup"><span data-stu-id="c5590-113">Representing an item of information as a subelement tends to be more appropriate when the possible values can repeat a variable number of times, are likely to have more widely ranging values, might be long, as in long strings, and are one of several sibling values where their order is relevant.</span></span> <span data-ttu-id="c5590-114">Si vous créez un schéma pour un type existant de code XML de document, votre choix d’utiliser un **élément de champ** nœud ou un **attribut de champ** nœud pour un élément d’information particulier a déjà été fait pour vous, et Vous devez utiliser le nœud correspondant au document XML.</span><span class="sxs-lookup"><span data-stu-id="c5590-114">If you are creating a schema for an existing type of XML document, your choice of using a **Field Element** node or a **Field Attribute** node for a particular item of information has already been made for you, and you must use the node that matches the XML.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c5590-115">Nœuds racine ne peuvent pas avoir **champ** attributs.</span><span class="sxs-lookup"><span data-stu-id="c5590-115">Root nodes may not have **Field** attributes.</span></span> <span data-ttu-id="c5590-116">**Champ** attributs attaché à la **racine** nœud ne sont pas enregistrées avec le schéma.</span><span class="sxs-lookup"><span data-stu-id="c5590-116">**Field** attributes attached to the **Root** node are not saved with the schema.</span></span>  
  
## <a name="xsd-representation"></a><span data-ttu-id="c5590-117">Représentation XSD</span><span class="sxs-lookup"><span data-stu-id="c5590-117">XSD representation</span></span>  
 <span data-ttu-id="c5590-118">Lorsqu’un **attribut de champ** nœud est inséré dans un **enregistrement** nœud, il est inséré à la fin de n’importe quel autre nœud enfant dans le **enregistrement** nœud.</span><span class="sxs-lookup"><span data-stu-id="c5590-118">When a **Field Attribute** node is inserted into a **Record** node, it is inserted at the end of any other child nodes in the **Record** node.</span></span> <span data-ttu-id="c5590-119">Être inséré après le **séquence**, **choix**, ou **tous les** élément contenant tous les nœuds non-attribut et après les nœuds d’attribut qui ont été précédemment inséré.</span><span class="sxs-lookup"><span data-stu-id="c5590-119">This includes being inserted after the **sequence**, **choice**, or **all** element containing any nonattribute nodes, and after any attribute nodes that were previously inserted.</span></span> <span data-ttu-id="c5590-120">L’exemple suivant montre un nouveau **attribut de champ** nœud, en gras, inséré à la fin d’un **enregistrement** nœud (les nœuds nommés pour clarifier leur identité).</span><span class="sxs-lookup"><span data-stu-id="c5590-120">The following example shows a new **Field Attribute** node, in bold, inserted at the end of a **Record** node (with nodes named to clarify their identity).</span></span>  
  
```  
<xs:element name="ContainingRecord">  
    <xs:complexType>  
        <xs:sequence>  
            <xs:element name="FieldElement" type="xs:string" />  
            <xs:element name="EmptyNestedRecord">  
                <xs:complexType />  
            </xs:element>  
        </xs:sequence>  
        <xs:attribute name="ExistingFieldAttribute" type="xs:string" />  
  
    </xs:complexType>  
</xs:element>  
  
```  
  
## <a name="see-also"></a><span data-ttu-id="c5590-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c5590-121">See Also</span></span>  
-  [<span data-ttu-id="c5590-122">Représentation BizTalk de schémas</span><span class="sxs-lookup"><span data-stu-id="c5590-122">BizTalk Representation of Schemas</span></span>](../core/biztalk-representation-of-schemas.md)   
-  [<span data-ttu-id="c5590-123">Propriétés de nœud</span><span class="sxs-lookup"><span data-stu-id="c5590-123">Node Properties</span></span>](../core/node-properties.md)   
-  <span data-ttu-id="c5590-124">**Propriétés de nœud d’élément de champ**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span><span class="sxs-lookup"><span data-stu-id="c5590-124">**Field Element Node Properties** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span></span>  
-  [<span data-ttu-id="c5590-125">Comment définir les propriétés de nœud</span><span class="sxs-lookup"><span data-stu-id="c5590-125">How to Set Node Properties</span></span>](../core/how-to-set-node-properties.md)   
-  [<span data-ttu-id="c5590-126">Nœuds groupe attribut</span><span class="sxs-lookup"><span data-stu-id="c5590-126">Attribute Group Nodes</span></span>](../core/attribute-group-nodes.md)