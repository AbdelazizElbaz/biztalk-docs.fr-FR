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
ms.openlocfilehash: b92c2165a84e5d539eac434ab140389c145b24b4
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="sequence-group-nodes"></a><span data-ttu-id="3adda-102">Nœuds Groupe Séquence</span><span class="sxs-lookup"><span data-stu-id="3adda-102">Sequence Group Nodes</span></span>

## <a name="overview"></a><span data-ttu-id="3adda-103">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="3adda-103">Overview</span></span>
<span data-ttu-id="3adda-104">Dans l’Éditeur BizTalk, vous pouvez insérer un **groupe séquence** nœud destiné à contenir d’autres nœuds qui doivent apparaître dans un message d’instance dans le même ordre que celui dans lequel ils apparaissent dans le **groupe séquence** nœud.</span><span class="sxs-lookup"><span data-stu-id="3adda-104">In BizTalk Editor, you can insert a **Sequence Group** node to contain other nodes that must appear in an instance message in the same order in which they appear within the **Sequence Group** node.</span></span> <span data-ttu-id="3adda-105">Les nœuds contenus doivent correspondre à des éléments XML, et non à des attributs XML.</span><span class="sxs-lookup"><span data-stu-id="3adda-105">The contained nodes must be nodes that correspond to XML elements, but cannot be nodes that correspond to XML attributes.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3adda-106">Dans l’Éditeur BizTalk, le **groupe séquence** nœud est représenté par défaut par la chaîne \<séquence\> dans l’arborescence de schéma.</span><span class="sxs-lookup"><span data-stu-id="3adda-106">In BizTalk Editor, the **Sequence Group** node is represented by default with the string \<Sequence\> in the schema tree view.</span></span> <span data-ttu-id="3adda-107">Si vous définissez une référence à un **groupe séquence** nœud, tel que x, elle est représentée en tant que \<Group : x\> dans l’arborescence de schéma.</span><span class="sxs-lookup"><span data-stu-id="3adda-107">If you set a reference to a **Sequence Group** node, such as x, it is represented as \<Group:x\> in the schema tree view.</span></span>  
  
 <span data-ttu-id="3adda-108">Il pouvez que vous souhaitez ajouter un **groupe séquence** pour déclarer un groupe de l’élément global.</span><span class="sxs-lookup"><span data-stu-id="3adda-108">You may want to add a **Sequence Group** to declare a global element group.</span></span>  
  
 <span data-ttu-id="3adda-109">Vous pouvez avoir besoin de créer un schéma pour XML comme indiqué ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="3adda-109">You may need to create a schema for XML as follows.</span></span>  
  
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
  
 <span data-ttu-id="3adda-110">GroupItem1 et GroupItem2 existant dans les deux cas, vous pouvez déclarer un groupe de séquence global qui correspond à un enfant à la fois de Record1 et de Record2.</span><span class="sxs-lookup"><span data-stu-id="3adda-110">Because GroupItem1 and GroupItem2 exist in both cases, you may declare a global sequence group that is a child of both Record1 and Record2.</span></span> <span data-ttu-id="3adda-111">Pour obtenir des instructions sur la façon de déclarer un groupe de séquences global, consultez [création de références à un autre nœud ou Type](../core/how-to-create-references-to-another-node-or-type.md).</span><span class="sxs-lookup"><span data-stu-id="3adda-111">For step-by-step instructions about how to declare a global sequence group, see [Creating References to Another Node or Type](../core/how-to-create-references-to-another-node-or-type.md).</span></span>  
  
 <span data-ttu-id="3adda-112">Un utilisateur peut modifier le groupe masqué pour être un **groupe choix** nœud ou un **groupe tous** nœud (afin qu’il n’est pas nécessairement un **groupe séquence** nœud) en modifiant le  **Type de l’ordre de groupe** propriété.</span><span class="sxs-lookup"><span data-stu-id="3adda-112">A user can change the hidden group to be a **Choice Group** node or an **All Group** node (so it is not necessarily a **Sequence Group** node) by changing the **Group Order Type** property.</span></span> <span data-ttu-id="3adda-113">Plus de détails sur cette propriété [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span><span class="sxs-lookup"><span data-stu-id="3adda-113">More details on this property [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span>
  
## <a name="xsd-representation"></a><span data-ttu-id="3adda-114">Représentation XSD</span><span class="sxs-lookup"><span data-stu-id="3adda-114">XSD representation</span></span>  
 <span data-ttu-id="3adda-115">Lorsqu’un **groupe séquence** nœud est inséré dans un **enregistrement** nœud, il est inséré à la fin de n’importe quel autre nœud enfant au sein de la **séquence**, **choix**, ou **tous les** élément dans le **enregistrement** nœud.</span><span class="sxs-lookup"><span data-stu-id="3adda-115">When a **Sequence Group** node is inserted into a **Record** node, it is inserted at the end of any other child nodes within the **sequence**, **choice**, or **all** element in the **Record** node.</span></span> <span data-ttu-id="3adda-116">L’exemple suivant montre un nouveau **groupe séquence** nœud, en caractères gras, inséré à la fin de la **séquence** élément dans une **enregistrement** nœud (les nœuds sont nommés pour clarifier leur identité).</span><span class="sxs-lookup"><span data-stu-id="3adda-116">The following example shows a new **Sequence Group** node, in bold type, inserted at the end of the **sequence** element in a **Record** node (with nodes named to clarify their identity).</span></span>  
  
```  
<xs:element name="ContainingRecord">  
    <xs:complexType>  
        <xs:sequence>  
            <xs:element name="ExistingFieldElement" type="xs:string" />  
        </xs:sequence>  
    </xs:complexType>  
</xs:element>  
  
```  
  
## <a name="see-also"></a><span data-ttu-id="3adda-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3adda-117">See Also</span></span>  
-  [<span data-ttu-id="3adda-118">Représentation BizTalk de schémas</span><span class="sxs-lookup"><span data-stu-id="3adda-118">BizTalk Representation of Schemas</span></span>](../core/biztalk-representation-of-schemas.md)   
-  [<span data-ttu-id="3adda-119">Propriétés de nœud</span><span class="sxs-lookup"><span data-stu-id="3adda-119">Node Properties</span></span>](../core/node-properties.md)   
-  <span data-ttu-id="3adda-120">**Propriétés d’un nœud groupe séquence**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span><span class="sxs-lookup"><span data-stu-id="3adda-120">**Sequence Group Node Properties** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span></span>
-  [<span data-ttu-id="3adda-121">Comment définir les propriétés de nœud</span><span class="sxs-lookup"><span data-stu-id="3adda-121">How to Set Node Properties</span></span>](../core/how-to-set-node-properties.md)