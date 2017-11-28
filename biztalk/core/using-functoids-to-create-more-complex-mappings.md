---
title: "À l’aide des fonctoids pour créer des mappages plus complexes | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7d53e3a3-5ccd-4733-8c2f-3101e41fca61
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 736b6fa99844182c59db582182056faea1d3f322
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="using-functoids-to-create-more-complex-mappings"></a><span data-ttu-id="66e51-102">Utilisation de fonctoids pour créer des mappages plus complexes</span><span class="sxs-lookup"><span data-stu-id="66e51-102">Using Functoids to Create More Complex Mappings</span></span>

## <a name="overview"></a><span data-ttu-id="66e51-103">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="66e51-103">Overview</span></span>
<span data-ttu-id="66e51-104">Les fonctoids jouent un rôle essentiel dans de nombreux scénarios de mappage.</span><span class="sxs-lookup"><span data-stu-id="66e51-104">Functoids play a crucial role in many mapping scenarios.</span></span> <span data-ttu-id="66e51-105">Sans les fonctoids, vous pouvez copier des données d'éléments et d'attributs, mais vous ne pouvez pas vraiment manipuler les valeurs elles-mêmes.</span><span class="sxs-lookup"><span data-stu-id="66e51-105">Without functoids, you can copy element and attribute data, but you cannot, to any significant extent, manipulate the values themselves.</span></span> <span data-ttu-id="66e51-106">Les fonctoids autorisent presque toutes les transformations.</span><span class="sxs-lookup"><span data-stu-id="66e51-106">Using functoids, almost any transformation is possible.</span></span> <span data-ttu-id="66e51-107">Par exemple, à l'aide d'un fonctoid, vous pouvez prendre deux valeurs issues de deux emplacements complètement différents, les ajouter et placer le résultat dans le schéma de destination.</span><span class="sxs-lookup"><span data-stu-id="66e51-107">For example, with a functoid you can take two values from entirely different locations, add them together, and place the sum in the destination schema.</span></span>  
  
 <span data-ttu-id="66e51-108">Les fonctoids apparaissent dans la boîte à outils [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], un onglet de boîte à outils par catégorie, lorsque vous modifiez un mappage BizTalk.</span><span class="sxs-lookup"><span data-stu-id="66e51-108">Functoids appear in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Toolbox, one toolbox tab per category, when you are editing a BizTalk map.</span></span> <span data-ttu-id="66e51-109">Une fois que vous avez ouvert la boîte à outils et choisi une catégorie de fonctoids en cliquant sur l'onglet correspondant, faites glisser votre fonctoid sur une page de grille.</span><span class="sxs-lookup"><span data-stu-id="66e51-109">After you open the Toolbox and choose a category of functoids by clicking on the corresponding tab, you drag the functoid onto a grid page.</span></span> <span data-ttu-id="66e51-110">Créez ensuite des liens d'entrée et de sortie entre le fonctoid et l'un ou l'autre des nœuds de schéma ou un autre fonctoid.</span><span class="sxs-lookup"><span data-stu-id="66e51-110">Then you create input and output links between the functoid and either schema nodes or another functoid.</span></span> <span data-ttu-id="66e51-111">Les liens d'entrée correspondent aux paramètres d'entrée et conduisent à un fonctoid à partir de la gauche. Quant au lien de sortie, il correspond au paramètre de sortie et abandonne le fonctoid par la droite.</span><span class="sxs-lookup"><span data-stu-id="66e51-111">Input links correspond to input parameters and lead to a functoid from the left; an output link corresponds to the output parameter and leaves a functoid to the right.</span></span>  
  
 <span data-ttu-id="66e51-112">Tout comme d'autres éléments de mappage, les fonctoids ont des propriétés.</span><span class="sxs-lookup"><span data-stu-id="66e51-112">Like other map elements, functoids have properties.</span></span> <span data-ttu-id="66e51-113">L'une des propriétés les plus importantes des fonctoids est leur ensemble de paramètres d'entrée.</span><span class="sxs-lookup"><span data-stu-id="66e51-113">One of the most important properties of a functoid is its set of input parameters.</span></span> <span data-ttu-id="66e51-114">Pour plus d’informations, consultez [comment ajouter des fonctoids à un mappage](../core/how-to-add-basic-functoids-to-a-map.md).</span><span class="sxs-lookup"><span data-stu-id="66e51-114">For more information, see [How to Add Basic Functoids to a Map](../core/how-to-add-basic-functoids-to-a-map.md).</span></span>  
  
 <span data-ttu-id="66e51-115">Cette section contient des instructions détaillées concernant l'utilisation de fonctoids dans les mappages BizTalk.</span><span class="sxs-lookup"><span data-stu-id="66e51-115">This section provides step-by-step instructions for working with functoids within BizTalk maps.</span></span> <span data-ttu-id="66e51-116">Pour plus d’informations de référence sur les fonctoids, consultez le **référence du fonctoid** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span><span class="sxs-lookup"><span data-stu-id="66e51-116">For reference information about functoids, see the **Functoid Reference** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span>
  
## <a name="next-steps"></a><span data-ttu-id="66e51-117">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="66e51-117">Next steps</span></span> 
  
-   [<span data-ttu-id="66e51-118">Comment ouvrir la boîte à outils des fonctoids</span><span class="sxs-lookup"><span data-stu-id="66e51-118">How to Open the Functoid Toolbox</span></span>](../core/how-to-open-the-functoid-toolbox.md)  
  
-   [<span data-ttu-id="66e51-119">Ajout de fonctoids de base à une carte</span><span class="sxs-lookup"><span data-stu-id="66e51-119">How to Add Basic Functoids to a Map</span></span>](../core/how-to-add-basic-functoids-to-a-map.md)  
  
-   [<span data-ttu-id="66e51-120">Ajout de fonctoids avancés à une carte</span><span class="sxs-lookup"><span data-stu-id="66e51-120">Adding Advanced Functoids to a Map</span></span>](../core/adding-advanced-functoids-to-a-map.md)  
  
-   [<span data-ttu-id="66e51-121">Modification des propriétés des fonctoids et des paramètres d’entrée</span><span class="sxs-lookup"><span data-stu-id="66e51-121">Editing Functoid Properties and Input Parameters</span></span>](../core/editing-functoid-properties-and-input-parameters.md)  
  
-   [<span data-ttu-id="66e51-122">Comment sélectionner plusieurs fonctoids</span><span class="sxs-lookup"><span data-stu-id="66e51-122">How to Select Multiple Functoids</span></span>](../core/how-to-select-multiple-functoids.md)  
  
-   [<span data-ttu-id="66e51-123">Comment supprimer des fonctoids</span><span class="sxs-lookup"><span data-stu-id="66e51-123">How to Delete Functoids</span></span>](../core/how-to-delete-functoids.md)  
  
-   [<span data-ttu-id="66e51-124">Comment copier, couper et coller un fonctoid</span><span class="sxs-lookup"><span data-stu-id="66e51-124">How to Copy, Cut, and Paste a Functoid</span></span>](../core/how-to-copy-cut-and-paste-a-functoid.md)