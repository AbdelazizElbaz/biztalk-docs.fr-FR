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
ms.openlocfilehash: ec6edafcb01e2c0ce155585e4fbe2f9d61b1cf1c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="choice-group-nodes"></a><span data-ttu-id="bf5d7-102">Nœuds Groupe Choix</span><span class="sxs-lookup"><span data-stu-id="bf5d7-102">Choice Group Nodes</span></span>
<span data-ttu-id="bf5d7-103">Dans l’Éditeur BizTalk, vous pouvez insérer un **groupe choix** nœud destiné à contenir les autres nœuds (ou des sous-arborescences entières de nœuds), un seul d'entre eux peut s’afficher dans un message d’instance.</span><span class="sxs-lookup"><span data-stu-id="bf5d7-103">In BizTalk Editor, you can insert a **Choice Group** node to contain other nodes (or entire subtrees of nodes), only one of which can appear in an instance message.</span></span> <span data-ttu-id="bf5d7-104">Un message d’instance donné, s’il est valide, ne comportera que l'un des choix présents.</span><span class="sxs-lookup"><span data-stu-id="bf5d7-104">A given instance message, if valid, will have only one of the choices present.</span></span> <span data-ttu-id="bf5d7-105">Les nœuds contenus doivent correspondre à des éléments XML, et non à des attributs XML.</span><span class="sxs-lookup"><span data-stu-id="bf5d7-105">The contained nodes must be nodes that correspond to XML elements, but cannot be nodes that correspond to XML attributes.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bf5d7-106">Dans l’Éditeur BizTalk, le **groupe choix** nœud est représenté par la chaîne \<choix > dans l’arborescence de schéma.</span><span class="sxs-lookup"><span data-stu-id="bf5d7-106">In BizTalk Editor, the **Choice Group** node is represented with the string \<Choice> in the schema tree view.</span></span> <span data-ttu-id="bf5d7-107">Si vous définissez une référence à un **groupe choix** nœud, tel que x, elle est représentée en tant que \<Group : x > dans l’arborescence de schéma.</span><span class="sxs-lookup"><span data-stu-id="bf5d7-107">If you set a reference to a **Choice Group** node, such as x, it is represented as \<Group:x> in the schema tree view.</span></span>  
  
## <a name="xsd-representation"></a><span data-ttu-id="bf5d7-108">Représentation XSD</span><span class="sxs-lookup"><span data-stu-id="bf5d7-108">XSD representation</span></span>  
 <span data-ttu-id="bf5d7-109">Quand un **groupe choix** nœud est inséré dans un **enregistrement** nœud, il est inséré à la fin de n’importe quel autre nœud enfant au sein de la **séquence**, **choix**, ou **tous les** élément dans le **enregistrement** nœud.</span><span class="sxs-lookup"><span data-stu-id="bf5d7-109">When a **Choice Group** node is inserted into a **Record** node, it is inserted at the end of any other child nodes within the **sequence**, **choice**, or **all** element in the **Record** node.</span></span> <span data-ttu-id="bf5d7-110">L’exemple suivant montre, en caractères gras, un nouveau **groupe choix** nœud est représenté dans le langage de XML Schema definition (XSD) en tant qu’un **choix** élément inséré à la fin de la **séquence**  élément dans une **enregistrement** nœud (les nœuds nommés pour clarifier leur identité).</span><span class="sxs-lookup"><span data-stu-id="bf5d7-110">The following example shows, in bold type, how a new **Choice Group** node is represented in the XML Schema definition (XSD) language as a **choice** element inserted at the end of the **sequence** element in a **Record** node (with nodes named to clarify their identity).</span></span>  
  
```  
<xs:element name="ContainingRecord">  
    <xs:complexType>  
        <xs:sequence>  
            <xs:element name="ExistingFieldElement" type="xs:string" />  
        </xs:sequence>  
    </xs:complexType>  
</xs:element>  
  
```  
  
 <span data-ttu-id="bf5d7-111">Par défaut, le **choix** élément reçoit un **minOccurs** attribut la valeur zéro (0), indiquant qu’aucun choix doivent se produire.</span><span class="sxs-lookup"><span data-stu-id="bf5d7-111">By default, the **choice** element is given a **minOccurs** attribute value of zero (0), indicating that none of the choices need occur.</span></span> <span data-ttu-id="bf5d7-112">Vous pouvez modifier cette valeur dans la fenêtre Propriétés de Visual Studio lorsque le **groupe choix** nœud est sélectionné dans l’arborescence du schéma.</span><span class="sxs-lookup"><span data-stu-id="bf5d7-112">You can change this value in the Visual Studio Properties window when the **Choice Group** node is selected in the schema tree view.</span></span>  
  
 <span data-ttu-id="bf5d7-113">L’exemple suivant montre la même **choix** élément avec le XSD **élément** éléments correspondant aux deux subordonné **enregistrement** nœuds.</span><span class="sxs-lookup"><span data-stu-id="bf5d7-113">The following example shows the same **choice** element with the XSD **element** elements corresponding to two subordinate **Record** nodes.</span></span>  
  
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
  
 <span data-ttu-id="bf5d7-114">Dans cet exemple, deux frères **enregistrement** nœuds sont utilisés pour décrire le fait qu’un message d’instance sera avoir un enregistrement avec les informations d’adresse des États-Unis, ou un enregistrement avec les informations d’adresse dans le monde entier.</span><span class="sxs-lookup"><span data-stu-id="bf5d7-114">In this example, two sibling **Record** nodes are used to describe the fact that an instance message will either have a record with United States address information in it, or a record with worldwide address information in it.</span></span> <span data-ttu-id="bf5d7-115">En outre, le **minOccurs** et **maxOccurs** propriétés de la **groupe choix** nœud ont été définis sur un (1) dans la fenêtre Propriétés de Visual Studio, ce qui entraîne la *minOccurs* et *maxOccurs* les attributs de la **choix** élément définie sur un (1) dans la représentation XSD.</span><span class="sxs-lookup"><span data-stu-id="bf5d7-115">Further, the **minOccurs** and **maxOccurs** properties of the **Choice Group** node have both been set to one (1) in the Visual Studio Properties window, resulting in the *minOccurs* and *maxOccurs* attributes of the **choice** element being set to one (1) in the XSD representation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf5d7-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bf5d7-116">See Also</span></span>  
-  [<span data-ttu-id="bf5d7-117">Représentation BizTalk de schémas</span><span class="sxs-lookup"><span data-stu-id="bf5d7-117">BizTalk Representation of Schemas</span></span>](../core/biztalk-representation-of-schemas.md)   
-  [<span data-ttu-id="bf5d7-118">Propriétés de nœud</span><span class="sxs-lookup"><span data-stu-id="bf5d7-118">Node Properties</span></span>](../core/node-properties.md)   
-  <span data-ttu-id="bf5d7-119">**Propriétés d’un nœud groupe séquence**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span><span class="sxs-lookup"><span data-stu-id="bf5d7-119">**Sequence Group Node Properties** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span></span>     
-  [<span data-ttu-id="bf5d7-120">Comment définir les propriétés de nœud</span><span class="sxs-lookup"><span data-stu-id="bf5d7-120">How to Set Node Properties</span></span>](../core/how-to-set-node-properties.md)