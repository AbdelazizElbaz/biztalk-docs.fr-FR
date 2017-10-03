---
title: "Comment insérer un enregistrement, un élément de champ ou un nœud d’attribut de champ | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c26f2281-f1b8-4788-8593-8d6ad29a53f0
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1341a0f2d89070d42620396a8c86d497b5d646ef
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-insert-a-record-field-element-or-field-attribute-node"></a><span data-ttu-id="2edcc-102">Comment insérer un enregistrement, un élément de champ ou un nœud d’attribut de champ</span><span class="sxs-lookup"><span data-stu-id="2edcc-102">How to Insert a Record, Field Element, or Field Attribute Node</span></span>
<span data-ttu-id="2edcc-103">**Enregistrement** nœuds (y compris le **racine** nœud), **attribut de champ** nœuds, et **élément de champ** nœuds sont uniques dans la mesure où ils peuvent être renommés afin que leurs les noms représentent les noms des éléments réels, nom personnalisé dans un message d’instance correspondant.</span><span class="sxs-lookup"><span data-stu-id="2edcc-103">**Record** nodes (including the **Root** node), **Field Attribute** nodes, and **Field Element** nodes are unique in that they can be renamed so that their names represent the names of the actual, custom-named elements in a corresponding instance message.</span></span> <span data-ttu-id="2edcc-104">Par exemple, si vous le nommez un **enregistrement** nœud FullName, à l’emplacement correspondant dans un message d’instance un élément XML nommé FullName est attendu.</span><span class="sxs-lookup"><span data-stu-id="2edcc-104">For example, if you name a **Record** node FullName, at the corresponding location in an instance message an XML element named FullName is expected.</span></span> <span data-ttu-id="2edcc-105">Si ce **enregistrement** nœud nommé FullName possède un enfant **attribut de champ** nœud nommé RequireFullMiddleName (avec ses **Min Occurs** et **Max Occurs** propriétés **1**), la **FullName** élément dans un message d’instance correspondant doivent avoir un attribut nommé **RequireFullMiddleName** associé.</span><span class="sxs-lookup"><span data-stu-id="2edcc-105">If that **Record** node named FullName has a child **Field Attribute** node named RequireFullMiddleName (with its **Min Occurs** and **Max Occurs** properties set to **1**), the **FullName** element in a corresponding instance message will need to have an attribute named **RequireFullMiddleName** associated with it.</span></span>  
  
 <span data-ttu-id="2edcc-106">Tous les **enregistrement** , lors de leur insertion sont représentés dans l’affichage XSD avec un **complexType** élément, mais pas avec une ultérieure **séquence**, **choix** , ou **tous les** élément.</span><span class="sxs-lookup"><span data-stu-id="2edcc-106">All **Record** nodes, when initially inserted, are represented in the XSD as with a **complexType** element, but not with a subsequent **sequence**, **choice**, or **all** element.</span></span> <span data-ttu-id="2edcc-107">Pour cette raison, le **Group Order Type**, **Group Max Occurs**, et **Group Min Occurs** propriétés de la **enregistrement** nœud ne sont pas disponibles pour la modification.</span><span class="sxs-lookup"><span data-stu-id="2edcc-107">For this reason, the **Group Order Type**, **Group Max Occurs**, and **Group Min Occurs** properties of the **Record** node are not available for modification.</span></span>  
  
 <span data-ttu-id="2edcc-108">Dès que vous ajoutez un enfant **enregistrement** ou **élément de champ** nœud à la **enregistrement** nœud, un **séquence** élément est ajouté pour le schéma XSD représentation dans le **complexType** élément doit contenir ce premier nœud enfant et le **Group Order Type** propriété de la **enregistrement** nœud affiche une valeur de **séquence**.</span><span class="sxs-lookup"><span data-stu-id="2edcc-108">As soon as you add a child **Record** or **Field Element** node to the **Record** node, a **sequence** element is added to the XSD representation within the **complexType** element to contain this first child node, and the **Group Order Type** property of the **Record** node shows a value of **Sequence**.</span></span> <span data-ttu-id="2edcc-109">Dans la plupart des cas, vous pouvez modifier le **Group Order Type** propriété à partir de **séquence** à **choix**et dans des circonstances plus limitées, à partir de **séquence**  à **tous les**, ce qui permet la modification de la paire d’élément qui contient les nœuds enfants correspondant soit **complexType/choix** ou **complexType/tous**, respectivement.</span><span class="sxs-lookup"><span data-stu-id="2edcc-109">In most circumstances, you can change the **Group Order Type** property from **Sequence** to **Choice**, and in more limited circumstances, from **Sequence** to **All**, thereby changing the element pair that contains the corresponding child nodes to either **complexType/choice** or **complexType/all**, respectively.</span></span>  
  
 <span data-ttu-id="2edcc-110">**Attribut de champ** nœuds ne peuvent pas avoir les mêmes noms de nœud dans la même portée.</span><span class="sxs-lookup"><span data-stu-id="2edcc-110">**Field Attribute** nodes cannot have the same node names while in the same scope.</span></span>  
  
 <span data-ttu-id="2edcc-111">**Enregistrement** et **élément de champ** nœuds peuvent avoir les mêmes noms de nœud dans la même portée uniquement si les conditions suivantes sont remplies :</span><span class="sxs-lookup"><span data-stu-id="2edcc-111">**Record** and **Field Element** nodes can have the same node names while in the same scope only if the following conditions are met:</span></span>  
  
-   <span data-ttu-id="2edcc-112">Ils doivent avoir le même type de données.</span><span class="sxs-lookup"><span data-stu-id="2edcc-112">They have the same data type.</span></span>  
  
-   <span data-ttu-id="2edcc-113">Ils ne sont pas dans un **groupe tous** nœud.</span><span class="sxs-lookup"><span data-stu-id="2edcc-113">They are not within an **All Group** node.</span></span>  
  
### <a name="to-insert-a-new-child-record-node-field-element-node-or-field-attribute-node-within-the-schema-node-or-an-existing-record-node"></a><span data-ttu-id="2edcc-114">Pour insérer un nouveau nœud enfant Enregistrement, Élément de champ ou Attribut de champ dans le nœud Schéma ou un nœud Enregistrement existant</span><span class="sxs-lookup"><span data-stu-id="2edcc-114">To insert a new child Record node, Field Element node, or Field Attribute node within the Schema node or an existing Record node</span></span>  
  
1.  <span data-ttu-id="2edcc-115">Sélectionnez le **schéma** nœud ou un **enregistrement** nœud.</span><span class="sxs-lookup"><span data-stu-id="2edcc-115">Select the **Schema** node or an existing **Record** node.</span></span>  
  
2.  <span data-ttu-id="2edcc-116">Sur le **BizTalk** menu, pointez sur **insérer un nœud de schéma**, puis cliquez sur **enregistrement enfant**, **élément de champ enfant**, ou  **Attribut de champ enfant**, le cas échéant.</span><span class="sxs-lookup"><span data-stu-id="2edcc-116">On the **BizTalk** menu, point to **Insert Schema Node**, and then click **Child Record**, **Child Field Element**, or **Child Field Attribute**, as appropriate.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="2edcc-117">Un nœud enfant du type choisi est ajouté après le dernier nœud dans l’arborescence de schéma (lors de l’insertion dans la **schéma** nœud) ou après le dernier nœud enfant existant du **enregistrement** nœud (lorsque insertion dans un existant **enregistrement** nœud).</span><span class="sxs-lookup"><span data-stu-id="2edcc-117">A child node of the chosen type is added after either the last node in the schema tree (when inserting within the **Schema** node) or after the last existing child node of the selected **Record** node (when inserting within an existing **Record** node).</span></span>  
  
3.  <span data-ttu-id="2edcc-118">Tapez un nom pour le nouvellement inséré **enregistrement**, **Fieldelement**, ou **attribut de champ** nœud, puis appuyez sur ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="2edcc-118">Type a name for the newly inserted **Record**, **Field Element**, or **Field Attribute** node, and then press ENTER.</span></span>  
  
### <a name="to-insert-a-sibling-record-node-field-attribute-node-or-field-element-node-within-an-existing-record-node"></a><span data-ttu-id="2edcc-119">Pour insérer un nœud « frère » Enregistrement, Élément de champ ou Attribut de champ dans un nœud Enregistrement existant</span><span class="sxs-lookup"><span data-stu-id="2edcc-119">To insert a sibling Record node, Field Attribute node, or Field Element node within an existing Record node</span></span>  
  
1.  <span data-ttu-id="2edcc-120">Sélectionnez n’importe quel nœud enfant de la **enregistrement** dans lequel vous souhaitez insérer le frère de nœud **enregistrement**, **attribut de champ**, ou **élément de champ** nœud.</span><span class="sxs-lookup"><span data-stu-id="2edcc-120">Select any child node of the **Record** node into which you want to insert the sibling **Record**, **Field Attribute**, or **Field Element** node.</span></span>  
  
2.  <span data-ttu-id="2edcc-121">Sur le **BizTalk** menu, pointez sur **insérer un nœud de schéma**, puis cliquez sur **enregistrement frère**, **attribut de champ frère**, ou **Élément de champ frère**, le cas échéant.</span><span class="sxs-lookup"><span data-stu-id="2edcc-121">On the **BizTalk** menu, point to **Insert Schema Node**, and then click **Sibling Record**, **Sibling Field Attribute**, or **Sibling Field Element**, as appropriate.</span></span>  
  
     <span data-ttu-id="2edcc-122">Un nœud frère du type choisi est alors inséré à l'extrémité des frères du nœud sélectionné.</span><span class="sxs-lookup"><span data-stu-id="2edcc-122">A sibling node of the chosen type is inserted at the end of the siblings of the selected node.</span></span>  
  
3.  <span data-ttu-id="2edcc-123">Tapez un nom pour le nouvellement inséré **enregistrement**, **attribut de champ**, ou **élément de champ** nœud, puis appuyez sur ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="2edcc-123">Type a name for the newly inserted **Record**, **Field Attribute**, or **Field Element** node, and then press ENTER.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2edcc-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2edcc-124">See Also</span></span>  
 [<span data-ttu-id="2edcc-125">Insertion de nœuds dans un schéma</span><span class="sxs-lookup"><span data-stu-id="2edcc-125">Inserting Nodes into a Schema</span></span>](../core/inserting-nodes-into-a-schema.md)