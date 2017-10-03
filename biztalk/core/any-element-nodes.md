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
# <a name="any-element-nodes"></a><span data-ttu-id="bee91-102">Nœuds Tout élément</span><span class="sxs-lookup"><span data-stu-id="bee91-102">Any Element Nodes</span></span>
<span data-ttu-id="bee91-103">Dans l’Éditeur BizTalk, vous pouvez utiliser un **tout élément** nœud pour indiquer un emplacement au sein d’un message d’instance dans laquelle les éléments inconnus peuvent apparaître.</span><span class="sxs-lookup"><span data-stu-id="bee91-103">In BizTalk Editor, you can use an **Any Element** node to indicate a location within an instance message where unknown elements may appear.</span></span> <span data-ttu-id="bee91-104">Cela vous permet de parer aux situations où des éléments risquent d'apparaître à un emplacement particulier d'un message d'instance sans que vous en connaissiez le nom ou la complexité.</span><span class="sxs-lookup"><span data-stu-id="bee91-104">This accommodates situations in which you know that some element might appear at a particular location within an instance message, but you do not know the name of the element, or how complicated it might be.</span></span> <span data-ttu-id="bee91-105">Si vous placez un **tout élément** nœud à l’emplacement approprié dans le schéma, BizTalk peut traiter ces parties inconnues d’un message.</span><span class="sxs-lookup"><span data-stu-id="bee91-105">If you place an **Any Element** node at the appropriate location within the schema, BizTalk can process such unknown portions of a message.</span></span> <span data-ttu-id="bee91-106">La seule condition obligatoire est que l'XML correspondant soit bien formé.</span><span class="sxs-lookup"><span data-stu-id="bee91-106">The only requirement is that the corresponding XML is well-formed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bee91-107">Dans l’Éditeur BizTalk, le **tout élément** nœud est représenté par la chaîne \<tout > dans l’arborescence de schéma.</span><span class="sxs-lookup"><span data-stu-id="bee91-107">In BizTalk Editor, the **Any Element** node is represented with the string \<Any> in the schema tree view.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bee91-108">Vous pouvez contrôler le degré auquel la portion inconnue du message est validée en tant que XML bien formé à l’aide de la **Process Contents** propriété.</span><span class="sxs-lookup"><span data-stu-id="bee91-108">You can control the degree to which the unknown portion of the message is validated as well-formed XML by using the **Process Contents** property.</span></span> <span data-ttu-id="bee91-109">Dans de nombreux cas, vous devrez définir le **Process Contents** propriété **ignorer** pour le contenu d’un message d’instance à l’emplacement de la **tout élément** nœud à traiter.</span><span class="sxs-lookup"><span data-stu-id="bee91-109">In many cases you may need to set the **Process Contents** property to **Skip** for the contents of an instance message at the location of the **Any Element** node to be processed.</span></span> <span data-ttu-id="bee91-110">En conservant la valeur par défaut **Strict** pour le **Process Contents** propriété empêchera la validation de message d’instance à partir de la transmission.</span><span class="sxs-lookup"><span data-stu-id="bee91-110">Retaining the default value of **Strict** for the **Process Contents** property will prevent instance message validation from passing.</span></span>  
> 
> <span data-ttu-id="bee91-111">Plus de détails sur cette propriété [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span><span class="sxs-lookup"><span data-stu-id="bee91-111">More details on this property [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span>
  
## <a name="xsd-representation"></a><span data-ttu-id="bee91-112">Représentation XSD</span><span class="sxs-lookup"><span data-stu-id="bee91-112">XSD representation</span></span>  
 <span data-ttu-id="bee91-113">Lorsqu’un **tout élément** nœud est ajouté à un **enregistrement** nœud, ou vers un autre nœud auquel il peut être ajouté comme un **groupe séquence**, **le groupe choix**, ou **groupe tous** nœud, une seule balise XML est ajouté à la définition de schéma XML correspondante représentation de langage (XSD) du schéma.</span><span class="sxs-lookup"><span data-stu-id="bee91-113">When an **Any Element** node is added to a **Record** node, or to another node to which it can be added such as a **Sequence Group**, **Choice Group**, or **All Group** node, a single XML tag is added to the corresponding XML Schema definition (XSD) language representation of the schema.</span></span> <span data-ttu-id="bee91-114">Dans l’exemple suivant, un nouveau **tout élément** nœud, dont la représentation XSD est affichée en gras, a été ajouté à un fichier **enregistrement** nœud qui contient déjà un **élément de champ** nœud.</span><span class="sxs-lookup"><span data-stu-id="bee91-114">In the following example, a new **Any Element** node, whose XSD representation is shown in bold type, has been added to an existing **Record** node that already contains a **Field Element** node.</span></span>  
  
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
  
 <span data-ttu-id="bee91-115">En supposant que le **Process Contents** propriété de la **tout élément** nœud a la valeur **ignorer**, dans un message d’instance est régie par ce fragment de schéma, un **ExistingRecord** élément doit contenir un **ExistingFieldElement** élément contenant les données de chaîne, suivie de n’importe quel élément unique d’une complexité arbitraire.</span><span class="sxs-lookup"><span data-stu-id="bee91-115">Assuming that the **Process Contents** property of the **Any Element** node is set to **Skip**, within an instance message governed by this schema fragment, an **ExistingRecord** element is expected to contain an **ExistingFieldElement** element containing string data, followed by any single element of arbitrary complexity.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bee91-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bee91-116">See Also</span></span>  
 <span data-ttu-id="bee91-117">[Représentation BizTalk de schémas](../core/biztalk-representation-of-schemas.md) </span><span class="sxs-lookup"><span data-stu-id="bee91-117">[BizTalk Representation of Schemas](../core/biztalk-representation-of-schemas.md) </span></span>  
 <span data-ttu-id="bee91-118">[Propriétés de nœud](../core/node-properties.md) </span><span class="sxs-lookup"><span data-stu-id="bee91-118">[Node Properties](../core/node-properties.md) </span></span>  
 <span data-ttu-id="bee91-119">[Comment définir les propriétés de nœud](../core/how-to-set-node-properties.md) </span><span class="sxs-lookup"><span data-stu-id="bee91-119">[How to Set Node Properties](../core/how-to-set-node-properties.md) </span></span>  
 [<span data-ttu-id="bee91-120">Nœuds tout attribut</span><span class="sxs-lookup"><span data-stu-id="bee91-120">Any Attribute Nodes</span></span>](../core/any-attribute-nodes.md)