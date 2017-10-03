---
title: "Comment définir la Source de liens du compilateur valeur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4edd1d73-78d1-468d-806a-3f6f258ee375
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 61a7adf74d0b186f338220a383da6b6831013312
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-set-the-source-links-compiler-value"></a><span data-ttu-id="68bf6-102">Définition de la valeur du compilateur de liaisons sources</span><span class="sxs-lookup"><span data-stu-id="68bf6-102">How to Set the Source Links Compiler Value</span></span>
<span data-ttu-id="68bf6-103">Vous pouvez utiliser la **liaisons sources** propriété d’un lien pour spécifier comment une valeur est récupérée à partir du nœud source et appliquée au nœud de destination.</span><span class="sxs-lookup"><span data-stu-id="68bf6-103">You can use the **Source Links** property of a link to specify how a value is retrieved from the source node and applied to the destination node.</span></span> <span data-ttu-id="68bf6-104">Cette rubrique explique les choix disponibles et comment choisir parmi ces derniers.</span><span class="sxs-lookup"><span data-stu-id="68bf6-104">This topic explains the available choices and how to choose among them.</span></span>  
  
### <a name="to-set-the-source-links-link-property"></a><span data-ttu-id="68bf6-105">Pour définir la propriété de lien Liaisons sources</span><span class="sxs-lookup"><span data-stu-id="68bf6-105">To set the Source Links link property</span></span>  
  
1.  <span data-ttu-id="68bf6-106">Dans une page de grille du Mappeur BizTalk, cliquez sur un lien afin de le sélectionner.</span><span class="sxs-lookup"><span data-stu-id="68bf6-106">In BizTalk Mapper, in a grid page, click a link to select it.</span></span>  
  
     <span data-ttu-id="68bf6-107">Les points de terminaison d'un lien sélectionné dans la page de grille apparaissent en surbrillance.</span><span class="sxs-lookup"><span data-stu-id="68bf6-107">The endpoints of a selected link in the grid page are highlighted.</span></span>  
  
2.  <span data-ttu-id="68bf6-108">Dans le [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] fenêtre Propriétés, définissez la **liaisons sources** propriété à une des options suivantes :</span><span class="sxs-lookup"><span data-stu-id="68bf6-108">In the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window, set the **Source Links** property to one of the following choices:</span></span>  
  
    -   <span data-ttu-id="68bf6-109">**Nom de la copie.**</span><span class="sxs-lookup"><span data-stu-id="68bf6-109">**Copy Name.**</span></span> <span data-ttu-id="68bf6-110">le nom du nœud dans le schéma source est utilisé comme valeur pour le nœud lié dans le schéma de destination.</span><span class="sxs-lookup"><span data-stu-id="68bf6-110">The name of the node in the source schema is used as the value of the linked node in the destination schema.</span></span>  
  
    -   <span data-ttu-id="68bf6-111">**Copier la valeur texte.**</span><span class="sxs-lookup"><span data-stu-id="68bf6-111">**Copy Text Value.**</span></span> <span data-ttu-id="68bf6-112">la valeur correspondant au nœud dans le schéma source (données d’élément ou valeur d’attribut) est utilisée comme valeur du nœud lié dans le schéma de destination.</span><span class="sxs-lookup"><span data-stu-id="68bf6-112">The value corresponding to the node in the source schema (element data or an attribute value) is used as the value of the linked node in the destination schema.</span></span> <span data-ttu-id="68bf6-113">Il s’agit du choix par défaut.</span><span class="sxs-lookup"><span data-stu-id="68bf6-113">This choice is the default.</span></span> <span data-ttu-id="68bf6-114">Par exemple, `<Node>Hello<Name>Chris</Name>Barry</Node>` donne « Hello ».</span><span class="sxs-lookup"><span data-stu-id="68bf6-114">For example, `<Node>Hello<Name>Chris</Name>Barry</Node>` would result in "Hello".</span></span>  
  
    -   <span data-ttu-id="68bf6-115">**Copier le texte et sous-contenu : valeur.**</span><span class="sxs-lookup"><span data-stu-id="68bf6-115">**Copy Text and Subcontent Value.**</span></span> <span data-ttu-id="68bf6-116">la valeur correspondant au nœud d’enregistrement et la valeur de tous ses nœuds enfants, ainsi que leurs nœuds enfants, dans le schéma source (données d’élément et valeurs d’attribut) sont associées pour donner la valeur du nœud lié dans le schéma de destination.</span><span class="sxs-lookup"><span data-stu-id="68bf6-116">The value corresponding to the record node, and the value of all its child nodes, and their child nodes, in the source schema (element data and attribute values) are combined as the value of the linked node in the destination schema.</span></span> <span data-ttu-id="68bf6-117">Par exemple, `<Node>Hello<Name>Chris</Name>Barry</Node>` se traduit par « Hello Chris Barry ».</span><span class="sxs-lookup"><span data-stu-id="68bf6-117">For example, `<Node>Hello<Name>Chris</Name>Barry</Node>` would result in "Hello Chris Barry".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68bf6-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="68bf6-118">See Also</span></span>  
 <span data-ttu-id="68bf6-119">[À l’aide de liens pour spécifier l’enregistrement et les mappages de champs](../core/using-links-to-specify-record-and-field-mappings.md) </span><span class="sxs-lookup"><span data-stu-id="68bf6-119">[Using Links to Specify Record and Field Mappings](../core/using-links-to-specify-record-and-field-mappings.md) </span></span>  
 [<span data-ttu-id="68bf6-120">Liens et des Directives de compilateur</span><span class="sxs-lookup"><span data-stu-id="68bf6-120">Compiler Directives and Links</span></span>](../core/compiler-directives-and-links.md)