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
ms.openlocfilehash: 31814f9bd38bd07a75be0d4a2cc3e9d8b838720e
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="attribute-group-nodes"></a><span data-ttu-id="aa25e-102">Nœuds Groupe Attribut</span><span class="sxs-lookup"><span data-stu-id="aa25e-102">Attribute Group Nodes</span></span>

## <a name="overview"></a><span data-ttu-id="aa25e-103">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="aa25e-103">Overview</span></span>
<span data-ttu-id="aa25e-104">Dans l’Éditeur BizTalk, vous pouvez ajouter un **groupe d’attributs** nœud à un **enregistrement** nœud ou à un autre **groupe d’attributs** nœud destiné à contenir un groupe d’attributs que vous prévoyez d’utiliser plus plusieurs **enregistrement** nœud.</span><span class="sxs-lookup"><span data-stu-id="aa25e-104">In BizTalk Editor, you can add an **Attribute Group** node to a **Record** node or to another **Attribute Group** node to contain a group of attributes that you expect to use in more than one **Record** node.</span></span> <span data-ttu-id="aa25e-105">Ajout d’un **groupe d’attributs** nœud vers un autre **groupe d’attributs** nœud réalise l’imbrication de groupes d’attributs.</span><span class="sxs-lookup"><span data-stu-id="aa25e-105">Adding an **Attribute Group** node to another **Attribute Group** node achieves attribute group nesting.</span></span> <span data-ttu-id="aa25e-106">Cela vous permet de définir un groupe d’attributs dans un emplacement qui peut être utilisé dans plusieurs **enregistrement** ou **groupe d’attributs** nœuds.</span><span class="sxs-lookup"><span data-stu-id="aa25e-106">This allows you to define a group of attributes in one place that can be used in multiple **Record** or **Attribute Group** nodes.</span></span> <span data-ttu-id="aa25e-107">Les modifications apportées par la suite au groupe d'attributs se propageront vers tous les nœuds auxquels il est associé </span><span class="sxs-lookup"><span data-stu-id="aa25e-107">Subsequent modifications to the attribute group will propagate to all of the nodes with which that attribute group is associated.</span></span> <span data-ttu-id="aa25e-108">et ce, quel que soit le contexte de nœud dans lequel les modifications sont effectuées.</span><span class="sxs-lookup"><span data-stu-id="aa25e-108">This is true regardless of the node context in which the modifications are made.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="aa25e-109">Dans l’Éditeur BizTalk, le **AttributeGroup** nœud est représenté par défaut par la chaîne \<AttribGroup:attribGroup*N* \> dans l’arborescence du schéma, où  *N* est un nombre croissant.</span><span class="sxs-lookup"><span data-stu-id="aa25e-109">In BizTalk Editor, the **AttributeGroup** node is represented by default with the string \<AttribGroup:attribGroup*N*\> in the schema tree view, where *N* is a monotonically increasing numeral.</span></span> <span data-ttu-id="aa25e-110">Vous pouvez modifier la partie attribGroup*N* partie de son nom en tapant un nouveau nom unique dans son **référence du groupe** propriété.</span><span class="sxs-lookup"><span data-stu-id="aa25e-110">You can change the attribGroup*N* portion of its name by typing a new unique name in its **Group Reference** property.</span></span>  
  
 <span data-ttu-id="aa25e-111">Lorsque vous créez initialement un **groupe d’attributs** nœud, vous simplement l’insérer dans un de la **enregistrement** ou **groupe d’attributs** nœuds dans lequel il sera utilisé et éventuellement modifier son nom dans sa **référence du groupe** propriété.</span><span class="sxs-lookup"><span data-stu-id="aa25e-111">When initially creating an **Attribute Group** node, you simply insert it into one of the **Record** or **Attribute Group** nodes in which it will be used, and optionally change its name in its **Group Reference** property.</span></span> <span data-ttu-id="aa25e-112">Il existe deux façons d’utiliser le même groupe d’attributs dans un autre **enregistrement** ou **groupe d’attributs** nœud :</span><span class="sxs-lookup"><span data-stu-id="aa25e-112">There are two ways to use the same attribute group in another **Record** or **Attribute Group** node:</span></span>  
  
-   <span data-ttu-id="aa25e-113">Vous pouvez copier existants **groupe d’attributs** nœud et le coller ensuite dans l’autre **enregistrement** nœud.</span><span class="sxs-lookup"><span data-stu-id="aa25e-113">You can copy the existing **Attribute Group** node and then paste it into that other **Record** node.</span></span>  
  
-   <span data-ttu-id="aa25e-114">Vous pouvez insérer un nouveau **groupe d’attributs** nœud dans l’autre **enregistrement** nœud et définissez la **référence du groupe** propriété du nouveau **grouped’attributs** nœud pour référencer un existant **groupe d’attributs** nœud.</span><span class="sxs-lookup"><span data-stu-id="aa25e-114">You can insert a new **Attribute Group** node into that other **Record** node, and then set the **Group Reference** property of the new **Attribute Group** node to reference an existing **Attribute Group** node.</span></span>  
  
 <span data-ttu-id="aa25e-115">Par la suite, vous pouvez modifier le **groupe d’attributs** nœud — par exemple, en ajoutant ou supprimant un **attribut de champ** nœud, dans le contexte de n’importe quel **enregistrement** ou  **Groupe d’attributs** nœud dans lequel vous l’avez collé.</span><span class="sxs-lookup"><span data-stu-id="aa25e-115">Thereafter, you can modify the **Attribute Group** node—for example, by adding or deleting a **Field Attribute** node—in the context of any **Record** or **Attribute Group** node into which you pasted it.</span></span> <span data-ttu-id="aa25e-116">Cette modification se propage à tous les autres **enregistrement** ou **groupe d’attributs** nœuds auquel le groupe d’attributs est associé.</span><span class="sxs-lookup"><span data-stu-id="aa25e-116">That change will propagate to all other **Record** or **Attribute Group** nodes with which the attribute group is associated.</span></span>  
  
 <span data-ttu-id="aa25e-117">Il est inutile d’ajouter un **groupe d’attributs** nœud sans ajouter au moins un nœud approprié, où les nœuds appropriés contiennent **attribut de champ** nœuds, **tout attribut**nœuds et (imbriquée) **groupe d’attributs** nœuds.</span><span class="sxs-lookup"><span data-stu-id="aa25e-117">It would be pointless to add an **Attribute Group** node without adding at least one relevant node to it, where relevant nodes include **Field Attribute** nodes, **Any Attribute** nodes, and (nested) **Attribute Group** nodes.</span></span> <span data-ttu-id="aa25e-118">En fait, un groupe d'attributs contenant seulement un attribut unique n'est guère souhaitable à moins que l'idée ne soit d'ajouter d'autres attributs par la suite.</span><span class="sxs-lookup"><span data-stu-id="aa25e-118">In fact, an attribute group that contains only a single attribute is somewhat ill-conceived, unless you are making a point of planning for the addition of more attributes in the future.</span></span>  
  
 <span data-ttu-id="aa25e-119">**Groupe d’attributs** nœuds peuvent être imbriqués, ce qui permet de plus de possibilités de comment les groupes d’attributs peuvent être construites et combinés.</span><span class="sxs-lookup"><span data-stu-id="aa25e-119">**Attribute Group** nodes can be nested, allowing more possibilities in how groups of attributes can be constructed and combined.</span></span> <span data-ttu-id="aa25e-120">**Groupe d’attributs** peuvent également contenir des nœuds de la **tout attribut** nœud, ce qui permet de contenir des fonctions de caractères génériques en ce qui concerne les instances d’attribut qu’il peut prendre en charge d’un groupe d’attributs.</span><span class="sxs-lookup"><span data-stu-id="aa25e-120">**Attribute Group** nodes can also contain the **Any Attribute** node, allowing an attribute group to contain wildcard character capabilities with respect to the attribute instances it can accommodate.</span></span>  
  
## <a name="xsd-representation"></a><span data-ttu-id="aa25e-121">Représentation XSD</span><span class="sxs-lookup"><span data-stu-id="aa25e-121">XSD representation</span></span>  
 <span data-ttu-id="aa25e-122">Lorsqu’un **groupe d’attributs** nœud est ajouté pour la première fois à un **enregistrement** nœud ou à une autre **groupe d’attributs** nœud, deux zones distinctes de la définition de schéma XML (XSD) correspondante représentation de langage du schéma sont affectées.</span><span class="sxs-lookup"><span data-stu-id="aa25e-122">When an **Attribute Group** node is first added to a **Record** node or to another **Attribute Group** node, two distinct areas of the corresponding XML Schema definition (XSD) language representation of the schema are affected.</span></span> <span data-ttu-id="aa25e-123">Dans l’exemple suivant, un nouveau **groupe d’attributs** nœud, en gras, a été ajouté à un fichier **enregistrement** nœud qui contient déjà un existant **élément de champ** nœud.</span><span class="sxs-lookup"><span data-stu-id="aa25e-123">In the following example, a new **Attribute Group** node, in bold, has been added to an existing **Record** node that already contains an existing **Field Element** node.</span></span>  
  
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
  
 <span data-ttu-id="aa25e-124">Remarque la **attributeGroup** élément au sein de la représentation XSD du **enregistrement** nœud fait référence à un élément global **attributeGroup** élément est ajouté en tant qu’enfant de la **schéma** élément.</span><span class="sxs-lookup"><span data-stu-id="aa25e-124">Note how the **attributeGroup** element within the XSD representation of the **Record** node references a global **attributeGroup** element that is added as a child of the **schema** element.</span></span> <span data-ttu-id="aa25e-125">Cette définition globale du groupe d'attributs dans la représentation XSD du schéma permet au groupe d'attributs d'être référencé à plusieurs emplacements du schéma.</span><span class="sxs-lookup"><span data-stu-id="aa25e-125">This global definition of the attribute group within the XSD representation of the schema allows the attribute group to be referenced in multiple locations throughout the schema.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="aa25e-126">Noms de groupe d’attributs par défaut sont fournis automatiquement la forme ont*N*, où *N* est un nombre croissant.</span><span class="sxs-lookup"><span data-stu-id="aa25e-126">Default attribute group names that are supplied automatically have the form attrGroup*N*, where *N* is a monotonically increasing numeral.</span></span> <span data-ttu-id="aa25e-127">Vous pouvez renommer un groupe d’attributs en fournissant un nouveau nom unique dans son **référence du groupe** propriété.</span><span class="sxs-lookup"><span data-stu-id="aa25e-127">You can rename an attribute group by providing a new, unique name in its **Group Reference** property.</span></span> <span data-ttu-id="aa25e-128">Un groupe d'attributs ne peut pas être renommé directement dans l'arborescence de schéma.</span><span class="sxs-lookup"><span data-stu-id="aa25e-128">An attribute group cannot be renamed in place within the schema tree.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa25e-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="aa25e-129">See Also</span></span>  
-  [<span data-ttu-id="aa25e-130">Représentation BizTalk de schémas</span><span class="sxs-lookup"><span data-stu-id="aa25e-130">BizTalk Representation of Schemas</span></span>](../core/biztalk-representation-of-schemas.md)   
-  [<span data-ttu-id="aa25e-131">Propriétés de nœud</span><span class="sxs-lookup"><span data-stu-id="aa25e-131">Node Properties</span></span>](../core/node-properties.md)   
-  <span data-ttu-id="aa25e-132">**Propriétés d’un nœud groupe séquence**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span><span class="sxs-lookup"><span data-stu-id="aa25e-132">**Sequence Group Node Properties** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span></span>  
-  [<span data-ttu-id="aa25e-133">Comment définir les propriétés de nœud</span><span class="sxs-lookup"><span data-stu-id="aa25e-133">How to Set Node Properties</span></span>](../core/how-to-set-node-properties.md)   
-  [<span data-ttu-id="aa25e-134">Nœuds Attribut de champ</span><span class="sxs-lookup"><span data-stu-id="aa25e-134">Field Attribute Nodes</span></span>](../core/field-attribute-nodes.md)   
-  [<span data-ttu-id="aa25e-135">Nœuds Tout attribut</span><span class="sxs-lookup"><span data-stu-id="aa25e-135">Any Attribute Nodes</span></span>](../core/any-attribute-nodes.md)