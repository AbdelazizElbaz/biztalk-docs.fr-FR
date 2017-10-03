---
title: "Nœuds facultatifs | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- testing, BizTalk Mapper
- maps, testing
- testing, maps
- BizTalk Mapper, testing
- maps, optional nodes
ms.assetid: 7dcd203e-fb23-438a-87d1-42323acd87cc
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 96cf7d8b22ee8469a7e52dba7bbad899209c5274
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="optional-nodes"></a><span data-ttu-id="087d4-102">Nœuds facultatifs</span><span class="sxs-lookup"><span data-stu-id="087d4-102">Optional Nodes</span></span>
<span data-ttu-id="087d4-103">L'utilisation de nœuds facultatifs produira un avertissement lorsque vous testerez votre mappage.</span><span class="sxs-lookup"><span data-stu-id="087d4-103">Using optional nodes will produce a warning when you test your map.</span></span> <span data-ttu-id="087d4-104">Voici les deux cas dans lesquels un nœud source peut être considéré comme facultatif :</span><span class="sxs-lookup"><span data-stu-id="087d4-104">There are two conditions in which a source node may be considered optional:</span></span>  
  
-   <span data-ttu-id="087d4-105">L'enregistrement ou le champ actuel est facultatif.</span><span class="sxs-lookup"><span data-stu-id="087d4-105">The actual record or field is optional.</span></span>  
  
-   <span data-ttu-id="087d4-106">L'enregistrement ou le champ source est obligatoire mais un parent, un grand-parent et les niveaux hiérarchiques supérieurs sont facultatifs.</span><span class="sxs-lookup"><span data-stu-id="087d4-106">The source record or field is required, but a parent, grandparent, and farther up the hierarchy is optional.</span></span>  
  
 <span data-ttu-id="087d4-107">Il peut arriver que des enregistrements et des champs d'un schéma source soient facultatifs, mais que le schéma de destination requiert les enregistrements et champs correspondants.</span><span class="sxs-lookup"><span data-stu-id="087d4-107">You may have situations when you have records and fields in a source schema that are optional, but the destination schema requires the corresponding records or fields.</span></span>  
  
 <span data-ttu-id="087d4-108">Dans les deux cas, le test de votre mappage génère un avertissement dans le **sortie** fenêtre.</span><span class="sxs-lookup"><span data-stu-id="087d4-108">In both of the possible conditions, testing your map produces a warning in the **Output** window.</span></span> <span data-ttu-id="087d4-109">De plus, les données de sortie n'incluent pas le nœud cible.</span><span class="sxs-lookup"><span data-stu-id="087d4-109">In addition, the output data will not include the target node.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="087d4-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="087d4-110">See Also</span></span>  
 [<span data-ttu-id="087d4-111">Test de mappages</span><span class="sxs-lookup"><span data-stu-id="087d4-111">Testing Maps</span></span>](../core/testing-maps.md)