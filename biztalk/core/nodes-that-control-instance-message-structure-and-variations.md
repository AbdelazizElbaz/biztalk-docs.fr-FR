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
ms.openlocfilehash: baa82def3f62c6a603ef67e098e53b48a49013a3
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="nodes-that-control-instance-message-structure-and-variations"></a><span data-ttu-id="a63f6-102">Nœuds contrôlant la structure et les variations de message d'instance</span><span class="sxs-lookup"><span data-stu-id="a63f6-102">Nodes That Control Instance Message Structure and Variations</span></span>
<span data-ttu-id="a63f6-103">Certains types de nœuds que vous utilisez pour créer des schémas dans l’Éditeur BizTalk contrôlent la structure des messages d’instance et leurs variations.</span><span class="sxs-lookup"><span data-stu-id="a63f6-103">Some of the node types that you use to create schemas in BizTalk Editor control the structure of, and variations within, instance messages.</span></span> <span data-ttu-id="a63f6-104">Vous utilisez **groupe séquence** nœuds pour spécifier qu’une séquence d’éléments doit se produire dans un ordre spécifique dans l’emplacement correspondant dans un message d’instance.</span><span class="sxs-lookup"><span data-stu-id="a63f6-104">You use **Sequence Group** nodes to specify that a sequence of elements must occur in a specific order in the corresponding location in an instance message.</span></span> <span data-ttu-id="a63f6-105">Vous utilisez **groupe choix** nœuds pour spécifier qu’un élément d’une collection d’éléments peuvent se produire dans l’emplacement correspondant dans un message d’instance.</span><span class="sxs-lookup"><span data-stu-id="a63f6-105">You use **Choice Group** nodes to specify that one element from a collection of elements can occur in the corresponding location in an instance message.</span></span> <span data-ttu-id="a63f6-106">Vous utilisez **groupe tous** nœuds pour spécifier que tous les éléments spécifiés peuvent se produire dans n’importe quel ordre, mais une seule fois, à l’emplacement correspondant dans un message d’instance.</span><span class="sxs-lookup"><span data-stu-id="a63f6-106">You use **All Group** nodes to specify that all of the specified elements can occur in any order, but only once, at the corresponding location in an instance message.</span></span> <span data-ttu-id="a63f6-107">**\<Équivalent\>**  nœuds et leurs nœuds enfants sont affichés dans l’arborescence du schéma pour indiquer les emplacements dans les messages de l’instance où le polymorphisme par dérivation est en vigueur, celle qui permet de nombreuses données complexes connexes types se produire dans les emplacement correspondant dans un message d’instance.</span><span class="sxs-lookup"><span data-stu-id="a63f6-107">**\<Equivalent\>** nodes and their child nodes are displayed in the schema tree to indicate locations in instance messages where derivation-based polymorphism is in effect, allowing one of many related complex data types to occur in the corresponding location in an instance message.</span></span>  
  
 <span data-ttu-id="a63f6-108">Le reste de cette section propose des informations supplémentaires concernant cette classe de nœuds.</span><span class="sxs-lookup"><span data-stu-id="a63f6-108">The remainder of this section provides additional information about this class of nodes.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a63f6-109">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="a63f6-109">In This Section</span></span>  
  
-   [<span data-ttu-id="a63f6-110">Nœuds Groupe Séquence</span><span class="sxs-lookup"><span data-stu-id="a63f6-110">Sequence Group Nodes</span></span>](../core/sequence-group-nodes.md)  
  
-   [<span data-ttu-id="a63f6-111">Nœuds Groupe Choix</span><span class="sxs-lookup"><span data-stu-id="a63f6-111">Choice Group Nodes</span></span>](../core/choice-group-nodes.md)  
  
-   [<span data-ttu-id="a63f6-112">Nœuds Groupe Tous</span><span class="sxs-lookup"><span data-stu-id="a63f6-112">All Group Nodes</span></span>](../core/all-group-nodes.md)  
  
-   [<span data-ttu-id="a63f6-113">\<Équivalent\> nœuds et leurs nœuds enfants</span><span class="sxs-lookup"><span data-stu-id="a63f6-113">\<Equivalent\> Nodes and Their Child Nodes</span></span>](../core/equivalent-nodes-and-their-child-nodes.md)