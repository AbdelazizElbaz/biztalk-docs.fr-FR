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
ms.openlocfilehash: 82490a114149e3d4f71e3598900be5599c8a36e2
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="any-attribute-nodes"></a><span data-ttu-id="96282-102">Nœuds Tout Attribut</span><span class="sxs-lookup"><span data-stu-id="96282-102">Any Attribute Nodes</span></span>
<span data-ttu-id="96282-103">Dans l’Éditeur BizTalk, vous pouvez utiliser un **tout attribut** nœud pour indiquer un élément (connu) au sein d’un message d’instance qui peuvent contenir zéro ou plusieurs attributs inconnus.</span><span class="sxs-lookup"><span data-stu-id="96282-103">In BizTalk Editor, you can use an **Any Attribute** node to indicate a (known) element within an instance message for which zero or more unknown attributes may appear.</span></span> <span data-ttu-id="96282-104">C'est une parade aux situations dans lesquelles vous savez qu'un élément particulier sera présent à un emplacement particulier d'un message d'instance sans connaître exactement quels attributs cet élément est susceptible de comporter.</span><span class="sxs-lookup"><span data-stu-id="96282-104">This accommodates situations in which you know that a particular element will be present at a particular location within an instance message, but you are not sure exactly what attributes that element might include.</span></span> <span data-ttu-id="96282-105">Si vous placez un **tout attribut** nœud dans le **enregistrement** nœud associé à l’élément approprié, BizTalk peut traiter ce, à la seule condition est que tous les attributs associés sont corriger syntaxe (attributeName = « attributeValue »).</span><span class="sxs-lookup"><span data-stu-id="96282-105">If you place an **Any Attribute** node within the **Record** node associated with the relevant element, BizTalk can process that element, with the only requirement being that any associated attributes are syntactically correct (attributeName="attributeValue").</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="96282-106">Dans l’Éditeur BizTalk, le **tout attribut** nœud est représenté par la chaîne \<AnyAttribute\> dans l’arborescence de schéma.</span><span class="sxs-lookup"><span data-stu-id="96282-106">In BizTalk Editor, the **Any Attribute** node is represented with the string \<AnyAttribute\> in the schema tree view.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="96282-107">Vous pouvez contrôler le degré auquel la portion inconnue du message est validée en tant que XML bien formé à l’aide de la **Process Contents** propriété.</span><span class="sxs-lookup"><span data-stu-id="96282-107">You can control the degree to which the unknown portion of the message is validated as well-formed XML by using the **Process Contents** property.</span></span> <span data-ttu-id="96282-108">Dans de nombreux cas, vous devrez définir le **Process Contents** propriété **ignorer** pour le contenu d’un message d’instance à l’emplacement de la **tout attribut** nœud à traiter .</span><span class="sxs-lookup"><span data-stu-id="96282-108">In many cases you may need to set the **Process Contents** property to **Skip** for the contents of an instance message at the location of the **Any Attribute** node to be processed.</span></span> <span data-ttu-id="96282-109">En conservant la valeur par défaut **Strict** pour le **Process Contents** propriété empêchera la validation de message d’instance à partir de la transmission.</span><span class="sxs-lookup"><span data-stu-id="96282-109">Retaining the default value of **Strict** for the **Process Contents** property will prevent instance message validation from passing.</span></span>  
>
> <span data-ttu-id="96282-110">Plus de détails sur cette propriété [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span><span class="sxs-lookup"><span data-stu-id="96282-110">More details on this property [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span>
  
## <a name="xsd-representation"></a><span data-ttu-id="96282-111">Représentation XSD</span><span class="sxs-lookup"><span data-stu-id="96282-111">XSD representation</span></span>  
 <span data-ttu-id="96282-112">Lorsqu’un **tout attribut** nœud est ajouté à un **enregistrement** nœud ou à un **groupe d’attributs** nœud, une seule balise XML est ajouté à la définition de schéma XML correspondante de langage (XSD) représentation du schéma.</span><span class="sxs-lookup"><span data-stu-id="96282-112">When an **Any Attribute** node is added to a **Record** node or to an **Attribute Group** node, a single XML tag is added to the corresponding XML Schema definition (XSD) language representation of the schema.</span></span> <span data-ttu-id="96282-113">Dans l’exemple suivant, un nouveau **tout attribut** nœud, dont la représentation XSD est affichée en gras, a été ajouté à un fichier **enregistrement** nœud qui contient déjà un **élément de champ** nœud.</span><span class="sxs-lookup"><span data-stu-id="96282-113">In the following example, a new **Any Attribute** node, whose XSD representation is shown in bold, has been added to an existing **Record** node that already contains a **Field Element** node.</span></span>  
  
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
  
 <span data-ttu-id="96282-114">Dans l’exemple précédent, la représentation XSD du nouveau **tout attribut** nœud ajoute un **anyAttribute** élément à la fin du conteneur (**enregistrement** nœud) **élément** élément, en dehors du **séquence** élément et, dans le **complexType** élément.</span><span class="sxs-lookup"><span data-stu-id="96282-114">In the preceding example, the XSD representation of the new **Any Attribute** node adds an **anyAttribute** element to the end of the containing (**Record** node) **element** element, outside the **sequence** element and within the **complexType** element.</span></span> <span data-ttu-id="96282-115">Cette propriété est si tous les **attribut** éléments, autres que celles avec un **groupe d’attributs** nœud, sont ajoutés à leurs **élément** éléments.</span><span class="sxs-lookup"><span data-stu-id="96282-115">This is where all **attribute** elements, other than those with an **Attribute Group** node, are added to their containing **element** elements.</span></span>  
  
 <span data-ttu-id="96282-116">Maintenant et en supposant que le **Process Contents** propriété de la **tout attribut** nœud a la valeur **ignorer**, à l’intérieur un message d’instance est régie par ce fragment de schéma, un  **ExistingRecord** élément est attendu, et il peut contenir des attributs afin qu’elles sont bien formées en ce qui concerne la syntaxe XML.</span><span class="sxs-lookup"><span data-stu-id="96282-116">Now, and assuming that the **Process Contents** property of the **Any Attribute** node is set to **Skip**, within an instance message governed by this schema fragment, an **ExistingRecord** element is expected, and it can contain any attributes so long as they are well-formed with respect to XML syntax.</span></span> <span data-ttu-id="96282-117">(Pour le rendre conforme au fragment XSD dans cet exemple, il doit également contenir le **ExistingFieldElement** élément.)</span><span class="sxs-lookup"><span data-stu-id="96282-117">(To conform to the XSD fragment in this example, it must also contain the **ExistingFieldElement** element as well.)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96282-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="96282-118">See Also</span></span>  
 <span data-ttu-id="96282-119">[Représentation BizTalk de schémas](../core/biztalk-representation-of-schemas.md) </span><span class="sxs-lookup"><span data-stu-id="96282-119">[BizTalk Representation of Schemas](../core/biztalk-representation-of-schemas.md) </span></span>  
 <span data-ttu-id="96282-120">[Propriétés de nœud](../core/node-properties.md) </span><span class="sxs-lookup"><span data-stu-id="96282-120">[Node Properties](../core/node-properties.md) </span></span>  
 <span data-ttu-id="96282-121">[Comment définir les propriétés de nœud](../core/how-to-set-node-properties.md) </span><span class="sxs-lookup"><span data-stu-id="96282-121">[How to Set Node Properties](../core/how-to-set-node-properties.md) </span></span>  
 [<span data-ttu-id="96282-122">Nœuds Tout élément</span><span class="sxs-lookup"><span data-stu-id="96282-122">Any Element Nodes</span></span>](../core/any-element-nodes.md)