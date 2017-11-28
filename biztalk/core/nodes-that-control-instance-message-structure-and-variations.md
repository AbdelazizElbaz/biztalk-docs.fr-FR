---
title: "Nœuds contrôlant l’Instance de Structure et les Variations de Message | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3af8e6ce-282d-4318-a538-046b423ef033
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0733be2e3331e02bff38a7b93d31b8cafd5ec582
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="nodes-that-control-instance-message-structure-and-variations"></a><span data-ttu-id="3eb06-102">Nœuds contrôlant la structure et les variations de message d'instance</span><span class="sxs-lookup"><span data-stu-id="3eb06-102">Nodes That Control Instance Message Structure and Variations</span></span>
<span data-ttu-id="3eb06-103">Certains types de nœuds que vous utilisez pour créer des schémas dans l’Éditeur BizTalk contrôlent la structure des messages d’instance et leurs variations.</span><span class="sxs-lookup"><span data-stu-id="3eb06-103">Some of the node types that you use to create schemas in BizTalk Editor control the structure of, and variations within, instance messages.</span></span> <span data-ttu-id="3eb06-104">Vous utilisez **groupe séquence** nœuds pour spécifier qu’une séquence d’éléments doit se produire dans un ordre spécifique dans l’emplacement correspondant dans un message d’instance.</span><span class="sxs-lookup"><span data-stu-id="3eb06-104">You use **Sequence Group** nodes to specify that a sequence of elements must occur in a specific order in the corresponding location in an instance message.</span></span> <span data-ttu-id="3eb06-105">Vous utilisez **groupe choix** nœuds pour spécifier qu’un élément d’une collection d’éléments peuvent se produire dans l’emplacement correspondant dans un message d’instance.</span><span class="sxs-lookup"><span data-stu-id="3eb06-105">You use **Choice Group** nodes to specify that one element from a collection of elements can occur in the corresponding location in an instance message.</span></span> <span data-ttu-id="3eb06-106">Vous utilisez **groupe tous** nœuds pour spécifier que tous les éléments spécifiés peuvent se produire dans n’importe quel ordre, mais une seule fois, à l’emplacement correspondant dans un message d’instance.</span><span class="sxs-lookup"><span data-stu-id="3eb06-106">You use **All Group** nodes to specify that all of the specified elements can occur in any order, but only once, at the corresponding location in an instance message.</span></span> <span data-ttu-id="3eb06-107">**\<Équivalent >** nœuds et leurs nœuds enfants sont affichés dans l’arborescence du schéma pour indiquer les emplacements dans les messages de l’instance où le polymorphisme par dérivation est en vigueur, celle qui permet de nombreuses données complexes connexes types se produise dans correspondant emplacement dans un message d’instance.</span><span class="sxs-lookup"><span data-stu-id="3eb06-107">**\<Equivalent>** nodes and their child nodes are displayed in the schema tree to indicate locations in instance messages where derivation-based polymorphism is in effect, allowing one of many related complex data types to occur in the corresponding location in an instance message.</span></span>  
  
 <span data-ttu-id="3eb06-108">Le reste de cette section propose des informations supplémentaires concernant cette classe de nœuds.</span><span class="sxs-lookup"><span data-stu-id="3eb06-108">The remainder of this section provides additional information about this class of nodes.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3eb06-109">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="3eb06-109">In This Section</span></span>  
  
-   [<span data-ttu-id="3eb06-110">Nœuds groupe séquence</span><span class="sxs-lookup"><span data-stu-id="3eb06-110">Sequence Group Nodes</span></span>](../core/sequence-group-nodes.md)  
  
-   [<span data-ttu-id="3eb06-111">Nœuds groupe choix</span><span class="sxs-lookup"><span data-stu-id="3eb06-111">Choice Group Nodes</span></span>](../core/choice-group-nodes.md)  
  
-   [<span data-ttu-id="3eb06-112">Tous les nœuds de groupe</span><span class="sxs-lookup"><span data-stu-id="3eb06-112">All Group Nodes</span></span>](../core/all-group-nodes.md)  
  
-   [<span data-ttu-id="3eb06-113">\<Équivalent > nœuds et leurs nœuds enfants</span><span class="sxs-lookup"><span data-stu-id="3eb06-113">\<Equivalent> Nodes and Their Child Nodes</span></span>](../core/equivalent-nodes-and-their-child-nodes.md)