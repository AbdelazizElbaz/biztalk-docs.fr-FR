---
title: Directives de compilateur et les liens | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- compilier directives
- maps, compiling
- BizTalk Mapper, compiler directives
- links [maps], compiling
ms.assetid: 1655e10c-af98-4100-849d-b8214f93cfe9
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b598638072d59e635fd75c8e00836829d9459078
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="compiler-directives-and-links"></a><span data-ttu-id="a41d7-102">Directives et liaisons du compilateur</span><span class="sxs-lookup"><span data-stu-id="a41d7-102">Compiler Directives and Links</span></span>
<span data-ttu-id="a41d7-103">Vous pouvez configurer les deux directives de compilateur suivantes lien par lien :</span><span class="sxs-lookup"><span data-stu-id="a41d7-103">You can configure the following two compiler directives on a link-by-link basis:</span></span>  
  
-   <span data-ttu-id="a41d7-104">Les données du message d’instance d’entrée qui sont récupérées et copiées comme valeur d’attribut ou d'élément pertinente dans le message d'instance de sortie</span><span class="sxs-lookup"><span data-stu-id="a41d7-104">What data from the input instance message is retrieved and copied as the relevant element or attribute value in the output instance message.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a41d7-105">Cela comprend la possibilité de copier le nom de l’élément ou de l’attribut lui-même plutôt qu'une valeur associée à l’élément ou à l'attribut.</span><span class="sxs-lookup"><span data-stu-id="a41d7-105">Data here includes the option to copy the name of the element or attribute itself, rather than any value associated with the element or attribute.</span></span> <span data-ttu-id="a41d7-106">Les noms d’élément et d’attribut ne sont normalement pas considérés comme faisant partie des données contenues dans un message d’instance XML.</span><span class="sxs-lookup"><span data-stu-id="a41d7-106">Element and attribute names are not normally thought of as part of the data carried in an XML instance message.</span></span>  
  
-   <span data-ttu-id="a41d7-107">Le mode d'exécution d'une correspondance de nœuds entre les schémas source et de destination</span><span class="sxs-lookup"><span data-stu-id="a41d7-107">How node-matching is performed between the source and destination schemas.</span></span>  
  
 <span data-ttu-id="a41d7-108">Cette section propose une explication détaillée de ces options disponibles pour ces directives.</span><span class="sxs-lookup"><span data-stu-id="a41d7-108">This section provides a detailed explanation of these options available for these directives.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a41d7-109">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="a41d7-109">In This Section</span></span>  
  
-   [<span data-ttu-id="a41d7-110">Configuration de Transformation de données</span><span class="sxs-lookup"><span data-stu-id="a41d7-110">Data Transformation Configuration</span></span>](../core/data-transformation-configuration.md)  
  
-   [<span data-ttu-id="a41d7-111">Correspondance au niveau de hiérarchie de nœuds</span><span class="sxs-lookup"><span data-stu-id="a41d7-111">Node-Hierarchy Level Matching</span></span>](../core/node-hierarchy-level-matching.md)