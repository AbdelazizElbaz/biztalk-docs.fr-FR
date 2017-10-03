---
title: "Tous les nœuds de groupe | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0e28d98c-746a-44d8-bed2-ba539b8432aa
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f51d6420b7d754ffb8706e2bc729a02df00b4338
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="all-group-nodes"></a><span data-ttu-id="5e5eb-102">Nœuds Groupe Tous</span><span class="sxs-lookup"><span data-stu-id="5e5eb-102">All Group Nodes</span></span>
<span data-ttu-id="5e5eb-103">Dans l’Éditeur BizTalk, vous pouvez insérer un **groupe tous** nœud destiné à contenir d’autres nœuds qui apparaîtront zéro ou une fois, dans n’importe quel ordre.</span><span class="sxs-lookup"><span data-stu-id="5e5eb-103">In BizTalk Editor, you can insert an **All Group** node to contain other nodes that will appear zero or one time, in any order.</span></span> <span data-ttu-id="5e5eb-104">Dans le langage de XML Schema definition (XSD), le **tous les groupe** présente des limitations d’utilisation plus que **séquence** et **choix** groupes, ce qui se traduit par certaines situations dans L’Éditeur BizTalk où vous serez en mesure de créer un **groupe tous** nœud.</span><span class="sxs-lookup"><span data-stu-id="5e5eb-104">In XML Schema definition (XSD) language, the **All group** has more usage limitations than **Sequence** and **Choice** groups, which translates to few situations within BizTalk Editor where you will be able to create an **All Group** node.</span></span>  
  
 <span data-ttu-id="5e5eb-105">Pour utiliser un **groupe tous** nœud dans l’Éditeur BizTalk, vous devez suivre des étapes supplémentaires : le moyen le plus simple pour créer un **groupe tous** nœud consiste à modifier la valeur de la **Group Order Type** propriété du parent **enregistrement** nœud **tous les**.</span><span class="sxs-lookup"><span data-stu-id="5e5eb-105">To use an **All Group** node in BizTalk Editor, you need to follow some extra steps: The easiest way to create an **All Group** node is to change the value of the **Group Order Type** property of the parent **Record** node to **All**.</span></span> <span data-ttu-id="5e5eb-106">Cela garantit que tous les nœuds subordonnés de le **enregistrement** nœud sont contenus dans le **groupe tous** nœud.</span><span class="sxs-lookup"><span data-stu-id="5e5eb-106">This ensures that all of the subordinate nodes of the **Record** node are contained within the **All Group** node.</span></span>  <span data-ttu-id="5e5eb-107">Consultez **Type d’ordre de groupe** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span><span class="sxs-lookup"><span data-stu-id="5e5eb-107">See **Group Order Type** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span>
  
 <span data-ttu-id="5e5eb-108">Une autre façon d’utiliser un **groupe tous** dans l’Éditeur BizTalk commence par insérer un nouveau **enregistrement** nœud.</span><span class="sxs-lookup"><span data-stu-id="5e5eb-108">Another way to use an **All Group** node in BizTalk Editor begins with inserting a new **Record** node.</span></span> <span data-ttu-id="5e5eb-109">Après avoir inséré la nouvelle **enregistrement** nœud, modifier son **le Type de contenu** propriété **ComplexContent**.</span><span class="sxs-lookup"><span data-stu-id="5e5eb-109">After inserting the new **Record** node, change its **Content Type** property to **ComplexContent**.</span></span> <span data-ttu-id="5e5eb-110">Vous pouvez ensuite insérer un **groupe tous** nœud en tant qu’enfant de la **enregistrement** nœud.</span><span class="sxs-lookup"><span data-stu-id="5e5eb-110">Then you can insert an **All Group** node as a child of the **Record** node.</span></span> <span data-ttu-id="5e5eb-111">Cela est nécessaire car le **groupe tous** ne peuvent être insérés lors d’un héritage.</span><span class="sxs-lookup"><span data-stu-id="5e5eb-111">This is required because the **All Group** can only be inserted when inheritance is involved.</span></span> <span data-ttu-id="5e5eb-112">En spécifiant que le contenant **enregistrement** nœud contient du contenu complexe, son type de données est alors basé sur le type de données **xs : anyType**, dérivé par extension.</span><span class="sxs-lookup"><span data-stu-id="5e5eb-112">By specifying that the containing **Record** node contains complex content, its data type becomes based on the data type **xs:anyType**, derived by extension.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5e5eb-113">Dans l’Éditeur BizTalk, le **groupe tous** nœud est représenté par la chaîne \<tous > dans l’arborescence de schéma.</span><span class="sxs-lookup"><span data-stu-id="5e5eb-113">In BizTalk Editor, the **All Group** node is represented with the string \<All> in the schema tree view.</span></span> <span data-ttu-id="5e5eb-114">Si vous définissez une référence à un **groupe tous** nœud, telles que x, elle est représentée en tant que \<Group : x > dans l’arborescence de schéma.</span><span class="sxs-lookup"><span data-stu-id="5e5eb-114">If you set a reference to an **All Group** node, such as to x, it is represented as \<Group:x> in the schema tree view.</span></span>  
  
## <a name="xsd-representation"></a><span data-ttu-id="5e5eb-115">Représentation XSD</span><span class="sxs-lookup"><span data-stu-id="5e5eb-115">XSD representation</span></span>  
 <span data-ttu-id="5e5eb-116">Un **groupe tous** nœud peut être inséré dans un **enregistrement** nœud, mais uniquement si elle est le nœud enfant non-attribut uniquement de ce **enregistrement** nœud.</span><span class="sxs-lookup"><span data-stu-id="5e5eb-116">An **All Group** node can be inserted into a **Record** node, but only if it is the only non-attribute child node of that **Record** node.</span></span> <span data-ttu-id="5e5eb-117">L’exemple suivant illustre les étapes, un nouveau **groupe tous** nœud est représenté dans le langage de XML Schema definition (XSD) en tant qu’un **tous les** élément comme les étapes dans l’Éditeur BizTalk sont effectuées (avec les nœuds nommés pour les identifier).</span><span class="sxs-lookup"><span data-stu-id="5e5eb-117">The following example shows, in steps, how a new **All Group** node is represented in the XML Schema definition (XSD) language as an **all** element as the steps in BizTalk Editor are performed (with nodes named to clarify their identity).</span></span>  
  
```  
<xs:element name="NewRecord">  
    <xs:complexType />   
</xs:element>  
```  
  
 <span data-ttu-id="5e5eb-118">Après avoir ajouté un nouvel enregistrement, comme indiqué dans le fragment XSD précédent, sa **le Type de contenu** propriété **ComplexContent**, se traduisant par les modifications XSD suivantes.</span><span class="sxs-lookup"><span data-stu-id="5e5eb-118">After adding a new record as shown in the preceding XSD fragment, its **Content Type** property is changed to **ComplexContent**, resulting in the following XSD modifications.</span></span>  
  
```  
<xs:element name="NewRecord">  
    <xs:complexType>  
        <xs:complexContent mixed="false">  
             <xs:extension base="xs:anyType" />  
        </xs:complexContent>  
    </xs:complexType>  
</xs:element>  
```  
  
 <span data-ttu-id="5e5eb-119">Maintenant le **groupe tous** nœud peut être inséré en tant qu’enfant du nouvel enregistrement, comme indiqué dans le fragment XSD suivant.</span><span class="sxs-lookup"><span data-stu-id="5e5eb-119">Now the **All Group** node can be inserted as a child of the new record, as shown in the following XSD fragment.</span></span>  
  
```  
<xs:element name="NewRecord">  
    <xs:complexType>  
        <xs:complexContent mixed="false">  
            <xs:extension base="xs:anyType">  
                <xs:all />   
             </xs:extension>  
          </xs:complexContent>  
     </xs:complexType>  
</xs:element>  
```  
  
 <span data-ttu-id="5e5eb-120">Enfin, vous pouvez insérer des nœuds appropriés en tant qu’enfants du nouveau **groupe tous** nœud.</span><span class="sxs-lookup"><span data-stu-id="5e5eb-120">Finally, you can insert appropriate nodes as children of the new **All Group** node.</span></span> <span data-ttu-id="5e5eb-121">L’exemple suivant montre un **enregistrement** nœud et un **élément de champ** nœud inséré en tant que nœuds enfants du nouveau **groupe tous** nœud.</span><span class="sxs-lookup"><span data-stu-id="5e5eb-121">The following example shows a **Record** node and a **Field Element** node inserted as child nodes of the new **All Group** node.</span></span>  
  
```  
<xs:element name="NewRecord">  
    <xs:complexType>  
        <xs:complexContent mixed="false">  
            <xs:extension base="xs:anyType">  
                <xs:all>  
                    <xs:element name="RecordChildOfAllGroup">  
                        <xs:complexType />  
                    </xs:element>  
                    <xs:element name="FieldElementChildOfAllGroup" type="xs:string" />  
                </xs:all>  
            </xs:extension>  
        </xs:complexContent>  
    </xs:complexType>  
</xs:element>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5e5eb-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5e5eb-122">See Also</span></span>  
-  [<span data-ttu-id="5e5eb-123">Représentation BizTalk de schémas</span><span class="sxs-lookup"><span data-stu-id="5e5eb-123">BizTalk Representation of Schemas</span></span>](../core/biztalk-representation-of-schemas.md)   
-  [<span data-ttu-id="5e5eb-124">Propriétés de nœud</span><span class="sxs-lookup"><span data-stu-id="5e5eb-124">Node Properties</span></span>](../core/node-properties.md)   
-  <span data-ttu-id="5e5eb-125">**Propriétés d’un nœud groupe séquence**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span><span class="sxs-lookup"><span data-stu-id="5e5eb-125">**Sequence Group Node Properties** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span></span> 
-  [<span data-ttu-id="5e5eb-126">Comment définir les propriétés de nœud</span><span class="sxs-lookup"><span data-stu-id="5e5eb-126">How to Set Node Properties</span></span>](../core/how-to-set-node-properties.md)