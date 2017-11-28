---
title: "Insertion d’un groupe de séquences, un groupe de choix ou un nœud groupe tous | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 19aee400-1369-4310-b1b4-1bfeb2643236
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e498eb5ec8e7aa1398cfb58732f978faa9d0b415
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-insert-a-sequence-group-choice-group-or-all-group-node"></a><span data-ttu-id="c6edc-102">Insertion d’un groupe de séquences, un groupe de choix ou un nœud groupe tous</span><span class="sxs-lookup"><span data-stu-id="c6edc-102">How to Insert a Sequence Group, Choice Group, or All Group Node</span></span>
<span data-ttu-id="c6edc-103">L’Éditeur BizTalk prend en charge trois types de nœuds de groupe pour les éléments : **groupe séquence**, **groupe choix**, et **groupe tous**.</span><span class="sxs-lookup"><span data-stu-id="c6edc-103">BizTalk Editor supports three types of group nodes for elements: **Sequence Group**, **Choice Group**, and **All Group**.</span></span> <span data-ttu-id="c6edc-104">Ces différents types de nœuds de groupe établissent des contraintes différentes sur les nœuds enfants du groupe dans les messages d'instance correspondants.</span><span class="sxs-lookup"><span data-stu-id="c6edc-104">These different types of group nodes establish different constraints on the child nodes of the group in corresponding instance messages.</span></span> <span data-ttu-id="c6edc-105">Pour obtenir des informations sur les contraintes appliquées à ces différents types de groupes, consultez directement les informations concernant le langage XSD (XML Schema definition) sur le Web.</span><span class="sxs-lookup"><span data-stu-id="c6edc-105">For information about the constraints of these different types of groups, you should refer directly to information about the XML Schema definition (XSD) language on the Web.</span></span> <span data-ttu-id="c6edc-106">Pour accéder à ces informations, voir [ressources XSD sur le Web](../core/xsd-resources-on-the-web.md).</span><span class="sxs-lookup"><span data-stu-id="c6edc-106">For links to this information, see [XSD Resources on the Web](../core/xsd-resources-on-the-web.md).</span></span>  
  
 <span data-ttu-id="c6edc-107">L’Éditeur BizTalk prend également en charge un nœud de groupe pour les attributs, la **groupe d’attributs** nœud.</span><span class="sxs-lookup"><span data-stu-id="c6edc-107">BizTalk Editor also supports a group node for attributes, the **Attribute Group** node.</span></span> <span data-ttu-id="c6edc-108">Ce type de nœud permet un ensemble d’attributs pour être défini une fois et ensuite être associé à plusieurs **enregistrement** nœud dans le schéma.</span><span class="sxs-lookup"><span data-stu-id="c6edc-108">This type of node allows a set of attributes to be defined once, and then be associated with more than one **Record** node within the schema.</span></span>  
  
 <span data-ttu-id="c6edc-109">Lorsque vous créez une structure dans votre schéma, **enregistrement** nœuds sont supposés pour contenir les séquences ordonnées de nœuds enfants par défaut et sont représentées à l’aide de **séquence** éléments dans la représentation XSD du le schéma.</span><span class="sxs-lookup"><span data-stu-id="c6edc-109">When you build structure into your schema, **Record** nodes are assumed to contain ordered sequences of child nodes by default, and are represented by using **sequence** elements in the XSD representation of the schema.</span></span> <span data-ttu-id="c6edc-110">Vous pouvez modifier le type d’un nœud de groupe en modifiant son **Type d’ordre** propriété.</span><span class="sxs-lookup"><span data-stu-id="c6edc-110">You can change the type of a group node by changing its **Order Type** property.</span></span>  
  
### <a name="to-insert-a-sequence-group-node-or-a-choice-group-node"></a><span data-ttu-id="c6edc-111">Pour insérer un nœud Groupe Séquence ou Groupe Choix </span><span class="sxs-lookup"><span data-stu-id="c6edc-111">To insert a Sequence Group node or a Choice Group node</span></span>  
  
1.  <span data-ttu-id="c6edc-112">Dans l’arborescence du schéma, sélectionnez le **enregistrement** nœud dans lequel vous souhaitez insérer le **groupe séquence** nœud ou la **groupe choix** nœud.</span><span class="sxs-lookup"><span data-stu-id="c6edc-112">In the schema tree view, select the **Record** node in which you want to insert the **Sequence Group** node or the **Choice Group** node.</span></span>  
  
2.  <span data-ttu-id="c6edc-113">Sur le **BizTalk** menu, pointez sur **insérer un nœud de schéma**, puis cliquez sur **groupe séquence** ou **groupe choix**, le cas échéant.</span><span class="sxs-lookup"><span data-stu-id="c6edc-113">On the **BizTalk** menu, point to **Insert Schema Node**, and then click **Sequence Group** or **Choice Group**, as appropriate.</span></span>  
  
### <a name="to-insert-an-all-group-node"></a><span data-ttu-id="c6edc-114">Pour insérer un nœud Groupe Tous</span><span class="sxs-lookup"><span data-stu-id="c6edc-114">To insert an All Group node</span></span>  
  
1.  <span data-ttu-id="c6edc-115">Dans l’arborescence du schéma, sélectionnez la nouvelle **enregistrement** nœud dans lequel vous souhaitez insérer le **groupe tous** nœud.</span><span class="sxs-lookup"><span data-stu-id="c6edc-115">In the schema tree view, select the new **Record** node in which you want to insert the **All Group** node.</span></span>  
  
2.  <span data-ttu-id="c6edc-116">Sur le **BizTalk** menu, pointez sur **insérer un nœud de schéma**, puis cliquez sur **groupe tous**.</span><span class="sxs-lookup"><span data-stu-id="c6edc-116">On the **BizTalk** menu, point to **Insert Schema Node**, and then click **All Group**.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c6edc-117">Le **groupe tous** option est uniquement disponible dans le menu BizTalk (ou raccourci) lorsque le parent pertinentes **enregistrement** nœud satisfasse aux contraintes imposées par XSD sur l’utilisation de la **tousles**élément.</span><span class="sxs-lookup"><span data-stu-id="c6edc-117">The **All Group** choice is only available on the BizTalk (or shortcut) menu when the relevant parent **Record** node meets the constraints that XSD imposes on the use of the **all** element.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c6edc-118">Le **groupe tous** choix requiert que le **enregistrement** nœud ont un type de base de données.</span><span class="sxs-lookup"><span data-stu-id="c6edc-118">The **All Group** choice requires that the **Record** node have a base data type.</span></span> <span data-ttu-id="c6edc-119">Un moyen rapide de donner le nœud à un type de données consiste à définir son **le Type de contenu** à **complexes**.</span><span class="sxs-lookup"><span data-stu-id="c6edc-119">A quick way to give the node a data type is to set its **Content Type** to **Complex**.</span></span>  
  
### <a name="to-insert-an-attribute-group-node"></a><span data-ttu-id="c6edc-120">Pour insérer un nœud Groupe Attribut</span><span class="sxs-lookup"><span data-stu-id="c6edc-120">To insert an Attribute Group node</span></span>  
  
1.  <span data-ttu-id="c6edc-121">Dans l’arborescence du schéma, sélectionnez le **enregistrement** nœud dans lequel vous souhaitez insérer le **groupe d’attributs** nœud.</span><span class="sxs-lookup"><span data-stu-id="c6edc-121">In the schema tree view, select the **Record** node in which you want to insert the **Attribute Group** node.</span></span>  
  
2.  <span data-ttu-id="c6edc-122">Sur le **BizTalk** menu, pointez sur **insérer un nœud de schéma**, puis cliquez sur **groupe d’attributs**.</span><span class="sxs-lookup"><span data-stu-id="c6edc-122">On the **BizTalk** menu, point to **Insert Schema Node**, and then click **Attribute Group**.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c6edc-123">Si vous souhaitez modifier le nom de récemment insérées **groupe d’attributs** nœud, tapez le nouveau nom dans sa **référence du groupe** propriété.</span><span class="sxs-lookup"><span data-stu-id="c6edc-123">If you want to change the name of the newly inserted **Attribute Group** node, type the new name in its **Group Reference** property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6edc-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c6edc-124">See Also</span></span>  
 [<span data-ttu-id="c6edc-125">Insertion de nœuds dans un schéma</span><span class="sxs-lookup"><span data-stu-id="c6edc-125">Inserting Nodes into a Schema</span></span>](../core/inserting-nodes-into-a-schema.md)