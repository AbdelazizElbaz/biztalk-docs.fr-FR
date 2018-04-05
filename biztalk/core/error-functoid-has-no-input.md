---
title: 'Erreur : le fonctoid ne comporte aucune entrée | Documents Microsoft'
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- bts10.map.error.functiodHasNoInput
ms.assetid: ea59b902-953d-4a5f-aa28-dbaa0a017dca
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: edf8f6b74fb6aa69c0b822b07e8f712ea9a5007b
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="error---functoid-has-no-input"></a><span data-ttu-id="c6763-102">Erreur : le fonctoid ne comporte aucune entrée.</span><span class="sxs-lookup"><span data-stu-id="c6763-102">Error - Functoid Has No Input</span></span>
<span data-ttu-id="c6763-103">**Code d’erreur**</span><span class="sxs-lookup"><span data-stu-id="c6763-103">**Error Code**</span></span>  
  
 <span data-ttu-id="c6763-104">btm1012</span><span class="sxs-lookup"><span data-stu-id="c6763-104">btm1012</span></span>  
  
 <span data-ttu-id="c6763-105">**Explication**</span><span class="sxs-lookup"><span data-stu-id="c6763-105">**Explanation**</span></span>  
  
 <span data-ttu-id="c6763-106">Aucun paramètre d'entrée n'a été spécifié alors que le fonctoid indiqué en requiert au moins un.</span><span class="sxs-lookup"><span data-stu-id="c6763-106">The indicated functoid requires at least one input parameter, but no input parameters have been specified.</span></span>  
  
 <span data-ttu-id="c6763-107">**Action de l’utilisateur**</span><span class="sxs-lookup"><span data-stu-id="c6763-107">**User Action**</span></span>  
  
 <span data-ttu-id="c6763-108">Utilisez l'une ou l'autre des méthodes suivantes pour affecter le nombre correct de paramètres d'entrée au fonctoid concerné, tout en veillant à ce que l'ordre des paramètres soit respecté :</span><span class="sxs-lookup"><span data-stu-id="c6763-108">Use one or both of the following methods to provide the appropriate number of input parameters to the indicated functoid, paying particular attention to the expected order of input parameters:</span></span>  
  
-   <span data-ttu-id="c6763-109">Déplacez la souris pour créer un lien entre d'une part le fonctoid indiqué et d'autre part, soit des nœuds du schéma source, soit la sortie d'autres fonctoids situés à gauche du fonctoid indiqué dans la page de grille de mappage.</span><span class="sxs-lookup"><span data-stu-id="c6763-109">Drag to create links between the indicated functoid and either nodes in the source schema or the output of other functoids that are located to the left of the indicated functoid in a map grid page.</span></span>  
  
-   <span data-ttu-id="c6763-110">Sélectionnez le fonctoid indiqué, cliquez sur le bouton de sélection (**...** ) associés à la **paramètres d’entrée** propriété de Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] fenêtre Propriétés, puis configurez et organisez les paramètres d’entrée dans le **configurer \<Fonctoid\> fonctoid** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="c6763-110">Select the indicated functoid, click the ellipsis (**...**) button associated with the **Input Parameters** property in the Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window, and then configure and rearrange the order of the input parameters in the **Configure \<Functoid\> Functoid** dialog box.</span></span> <span data-ttu-id="c6763-111">Dans cette boîte de dialogue, vous pouvez créer des paramètres d'entrée constants, leur affecter des valeurs et les classer dans le même ordre que celui des autres paramètres d'entrée.</span><span class="sxs-lookup"><span data-stu-id="c6763-111">Constant input parameters can be created, given values, and put in the proper order relative to the other input parameters in this dialog box.</span></span>