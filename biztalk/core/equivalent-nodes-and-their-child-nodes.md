---
title: "Nœuds équivalents et leurs nœuds enfants | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6a85c6a1-6121-4849-b958-7c4bd1c7c552
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 05c5603cf1882aa7b262ecc5393a9d91dc93da10
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="equivalent-nodes-and-their-child-nodes"></a><span data-ttu-id="c0411-102">Nœuds équivalents et leurs nœuds enfants</span><span class="sxs-lookup"><span data-stu-id="c0411-102">Equivalent Nodes and Their Child Nodes</span></span>

## <a name="overview"></a><span data-ttu-id="c0411-103">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="c0411-103">Overview</span></span>
<span data-ttu-id="c0411-104">Le  **\<équivalent\>**  nœud et ses enfants sont utilisés dans l’arborescence de schéma pour afficher des occurences de polymorphisme de type de données complexes.</span><span class="sxs-lookup"><span data-stu-id="c0411-104">The **\<Equivalent\>** node and its children are used in the schema tree to display occurrences of complex data type polymorphism.</span></span> <span data-ttu-id="c0411-105">Lorsque vous dérivez un type de données complexe d'un autre type de données complexe, le polymorphisme dans XSD permet à ces deux types de données d'apparaître dans des messages d'instance à des endroits pour lesquels le type de données complexe de base a été spécifié.</span><span class="sxs-lookup"><span data-stu-id="c0411-105">When you derive one complex data type from another complex data type, polymorphism within XSD allows either of these data types to occur in instance messages in locations for which the base complex data type has been specified.</span></span> <span data-ttu-id="c0411-106">Lors de la validation de schéma, le fait qu’un seul de plusieurs types de données complexes est autorisé à un emplacement particulier est implicitement représenté par le nom de type de données complexe de base associé à la **base** attribut de la **extension** ou **restriction** éléments des types de données complexes dérivés.</span><span class="sxs-lookup"><span data-stu-id="c0411-106">During schema validation, the fact that one of multiple possible complex data types is allowed at a particular location is represented implicitly by the base complex data type name associated with the **base** attribute of the **extension** or **restriction** elements of the derived complex data types.</span></span> <span data-ttu-id="c0411-107">Pour rendre ce polymorphisme plus évident dans l’arborescence du schéma, le  **\<équivalent\>**  nœud et ses nœuds enfants sont affichés explicitement.</span><span class="sxs-lookup"><span data-stu-id="c0411-107">To make this polymorphism more obvious in the schema tree, the **\<Equivalent\>** node and its child nodes are displayed explicitly.</span></span>  
  
 <span data-ttu-id="c0411-108">Le  **\<équivalent\>**  nœud est affiché comme un nœud enfant d’occurrences du type de base de données complexe, indiquant qu’il existe plusieurs types de données complexes qui peuvent se produire à cette position dans une instance Message.</span><span class="sxs-lookup"><span data-stu-id="c0411-108">The **\<Equivalent\>** node is displayed as a child node of occurrences of the base complex data type, indicating that there are multiple complex data types that could occur at that position in an instance message.</span></span> <span data-ttu-id="c0411-109">Les nœuds enfants de la  **\<équivalent\>**  nœud sont affichés sous forme de la valeur de la **nom** attribut correspondantes **complexType** élément dans la représentation XSD du polymorphisme, affiché entre crochets (\<nom\>).</span><span class="sxs-lookup"><span data-stu-id="c0411-109">The child nodes of the **\<Equivalent\>** node are displayed as the value of the **name** attribute of the corresponding **complexType** element in the XSD representation of the polymorphism, displayed within angle brackets (\<name\>).</span></span>  
  
 <span data-ttu-id="c0411-110">Le  **\<équivalent\>**  chaque nœud et ses enfants ont uniquement deux propriétés associées :</span><span class="sxs-lookup"><span data-stu-id="c0411-110">The **\<Equivalent\>** node and its children each have only two properties associated with them:</span></span>  
  
-   <span data-ttu-id="c0411-111">**\<Équivalent\>**  nœud : **nom de nœud** et **Type de Base**</span><span class="sxs-lookup"><span data-stu-id="c0411-111">**\<Equivalent\>** node: **Node Name** and **Base Type**</span></span>
  
-   <span data-ttu-id="c0411-112">Nœuds enfants : **nom de nœud** et **Type de dérivation**</span><span class="sxs-lookup"><span data-stu-id="c0411-112">Child nodes: **Node Name** and **Derivation Type**</span></span>

<span data-ttu-id="c0411-113">Plus d’informations sur ces propriétés [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span><span class="sxs-lookup"><span data-stu-id="c0411-113">More details on these properties [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span>
  
## <a name="xsd-representation"></a><span data-ttu-id="c0411-114">Représentation XSD</span><span class="sxs-lookup"><span data-stu-id="c0411-114">XSD representation</span></span>  
 <span data-ttu-id="c0411-115">Il n’existe aucune représentation XSD directe de la  **\<équivalent\>**  nœud et ses enfants.</span><span class="sxs-lookup"><span data-stu-id="c0411-115">There is no direct XSD representation of the **\<Equivalent\>** node and its children.</span></span> <span data-ttu-id="c0411-116">Ce nœud est utilisé dans l'arborescence pour rendre le polymorphisme de type de données complexe plus visible et évident.</span><span class="sxs-lookup"><span data-stu-id="c0411-116">This node is used within the schema tree to make complex data type polymorphism more visible and obvious.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0411-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c0411-117">See Also</span></span>  
-  [<span data-ttu-id="c0411-118">Représentation BizTalk de schémas</span><span class="sxs-lookup"><span data-stu-id="c0411-118">BizTalk Representation of Schemas</span></span>](../core/biztalk-representation-of-schemas.md)   
-  [<span data-ttu-id="c0411-119">Propriétés de nœud</span><span class="sxs-lookup"><span data-stu-id="c0411-119">Node Properties</span></span>](../core/node-properties.md)   
-  <span data-ttu-id="c0411-120">**Propriétés d’un nœud groupe séquence**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span><span class="sxs-lookup"><span data-stu-id="c0411-120">**Sequence Group Node Properties** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span></span>  
-  [<span data-ttu-id="c0411-121">Comment définir les propriétés de nœud</span><span class="sxs-lookup"><span data-stu-id="c0411-121">How to Set Node Properties</span></span>](../core/how-to-set-node-properties.md)