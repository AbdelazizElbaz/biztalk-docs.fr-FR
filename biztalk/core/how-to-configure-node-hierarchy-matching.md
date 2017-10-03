---
title: "Comment configurer la hiérarchie de nœuds correspondant à | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5302e194-cbc7-4d26-b25b-eb4e38abfe23
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d29a794db6f34d7e8251c32bbf428b3a336601fe
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-node-hierarchy-matching"></a><span data-ttu-id="6a456-102">Configuration d'une correspondance de hiérarchie de nœuds</span><span class="sxs-lookup"><span data-stu-id="6a456-102">How to Configure Node Hierarchy Matching</span></span>
<span data-ttu-id="6a456-103">Lorsque vous créez un lien dans un mappage, le Mappeur BizTalk crée automatiquement des liens de compilateur pour implémenter le lien que vous avez établi.</span><span class="sxs-lookup"><span data-stu-id="6a456-103">When you create a link in a map, the BizTalk Mapper automatically creates compiler links to implement the link you have drawn.</span></span> <span data-ttu-id="6a456-104">Le **liaisons cibles** propriété d’un lien contrôle la manière dont le Mappeur BizTalk crée les liens de compilateur.</span><span class="sxs-lookup"><span data-stu-id="6a456-104">The **Target Links** property of a link controls how the BizTalk Mapper draws the compiler links.</span></span> <span data-ttu-id="6a456-105">Cette rubrique fournit des informations sur la configuration des liaisons cibles.</span><span class="sxs-lookup"><span data-stu-id="6a456-105">This topic provides information about how to set the target links.</span></span>  
  
 <span data-ttu-id="6a456-106">Le **liaisons sources** propriété spécifie comment une valeur est récupérée à partir du nœud source et appliquée au nœud de destination.</span><span class="sxs-lookup"><span data-stu-id="6a456-106">The **Source Links** property specifies how a value is retrieved from the source node and applied to the destination node.</span></span> <span data-ttu-id="6a456-107">Pour plus d’informations sur la définition des liaisons sources, consultez [comment définir la valeur du compilateur de liens Source](../core/how-to-set-the-source-links-compiler-value.md).</span><span class="sxs-lookup"><span data-stu-id="6a456-107">For information about how to set source links, see [How to Set the Source Links Compiler Value](../core/how-to-set-the-source-links-compiler-value.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6a456-108">Cette opération nécessite l'exécution du Mappeur BizTalk.</span><span class="sxs-lookup"><span data-stu-id="6a456-108">This operation requires that BizTalk Mapper is running.</span></span>  
  
### <a name="to-set-the-target-links-property"></a><span data-ttu-id="6a456-109">Pour définir la propriété Liaisons cibles</span><span class="sxs-lookup"><span data-stu-id="6a456-109">To set the Target Links property</span></span>  
  
1.  <span data-ttu-id="6a456-110">Dans la page de grille de mappage, cliquez sur un lien pour lequel définir la propriété Liaisons cibles.</span><span class="sxs-lookup"><span data-stu-id="6a456-110">On the map grid page, click a link to which you want to set the target links property.</span></span>  
  
2.  <span data-ttu-id="6a456-111">Dans le [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] **propriétés** , configurez la **liaisons cibles** propriété à une des options suivantes :</span><span class="sxs-lookup"><span data-stu-id="6a456-111">In the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]**Properties** window, set the **Target Links** property to one of the following choices:</span></span>  
  
    -   <span data-ttu-id="6a456-112">**Liaisons aplaties.**</span><span class="sxs-lookup"><span data-stu-id="6a456-112">**Flatten Links.**</span></span> <span data-ttu-id="6a456-113">la hiérarchie du nœud d'enregistrement source est mise à plat au niveau du nœud d'enregistrement auquel elle est reliée dans le schéma de destination.</span><span class="sxs-lookup"><span data-stu-id="6a456-113">The hierarchy in the source record node is flattened to the linked-to-record node in the destination schema.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="6a456-114">Par défaut, le Mappeur BizTalk définit le **liaisons cibles** propriété **Flatten**.</span><span class="sxs-lookup"><span data-stu-id="6a456-114">By default, the BizTalk Mapper sets the **Target Links** property to **Flatten**.</span></span>  
  
    -   <span data-ttu-id="6a456-115">**Correspondance descendante des liaisons.**</span><span class="sxs-lookup"><span data-stu-id="6a456-115">**Match Links Top Down.**</span></span> <span data-ttu-id="6a456-116">la correspondance des nœuds est réalisée niveau par niveau de façon descendante.</span><span class="sxs-lookup"><span data-stu-id="6a456-116">Node matching is performed level-to-level from the top down.</span></span>  
  
    -   <span data-ttu-id="6a456-117">**Correspondance ascendante des liaisons.**</span><span class="sxs-lookup"><span data-stu-id="6a456-117">**Match Links Bottom Up.**</span></span> <span data-ttu-id="6a456-118">la correspondance des nœuds est réalisée niveau par niveau de façon ascendante.</span><span class="sxs-lookup"><span data-stu-id="6a456-118">Node matching is performed level-to-level from the bottom up.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a456-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6a456-119">See Also</span></span>  
 <span data-ttu-id="6a456-120">[Correspondance au niveau de hiérarchie de nœuds](../core/node-hierarchy-level-matching.md) </span><span class="sxs-lookup"><span data-stu-id="6a456-120">[Node-Hierarchy Level Matching](../core/node-hierarchy-level-matching.md) </span></span>  
 <span data-ttu-id="6a456-121">[Liens et des Directives de compilateur](../core/compiler-directives-and-links.md) </span><span class="sxs-lookup"><span data-stu-id="6a456-121">[Compiler Directives and Links](../core/compiler-directives-and-links.md) </span></span>  
 [<span data-ttu-id="6a456-122">À l’aide de liens pour spécifier l’enregistrement et les mappages de champs</span><span class="sxs-lookup"><span data-stu-id="6a456-122">Using Links to Specify Record and Field Mappings</span></span>](../core/using-links-to-specify-record-and-field-mappings.md)