---
title: "Erreur : fonctoid Index ne comporte aucun Index | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: bts10.map.error.indexFunctoidHasNoIndex
ms.assetid: a523705e-6134-4d98-8ea6-dbfc7b43dae5
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0159d308c9befc90590d281351409ba571921a53
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="error---index-functoid-has-no-index"></a><span data-ttu-id="04a8e-102">Erreur : fonctoid Index ne comporte aucun Index</span><span class="sxs-lookup"><span data-stu-id="04a8e-102">Error - Index Functoid Has No Index</span></span>
<span data-ttu-id="04a8e-103">**Code d’erreur**</span><span class="sxs-lookup"><span data-stu-id="04a8e-103">**Error Code**</span></span>  
  
 <span data-ttu-id="04a8e-104">btm1014</span><span class="sxs-lookup"><span data-stu-id="04a8e-104">btm1014</span></span>  
  
 <span data-ttu-id="04a8e-105">**Explication**</span><span class="sxs-lookup"><span data-stu-id="04a8e-105">**Explanation**</span></span>  
  
 <span data-ttu-id="04a8e-106">Aucune valeur d’index n’ont été fournis pour le fonctoid **Index** fonctoid.</span><span class="sxs-lookup"><span data-stu-id="04a8e-106">No index value(s) have been provided for the indicated **Index** functoid.</span></span>  
  
 <span data-ttu-id="04a8e-107">**Action de l’utilisateur**</span><span class="sxs-lookup"><span data-stu-id="04a8e-107">**User Action**</span></span>  
  
 <span data-ttu-id="04a8e-108">Fournir un nombre approprié de paramètres d’entrée d’index pour le fonctoid **Index** fonctoid, où le nombre approprié est déterminé par le nombre de bouclage **enregistrement** nœuds au sein de laquelle le **Champ** nœud dans le schéma source est imbriqué.</span><span class="sxs-lookup"><span data-stu-id="04a8e-108">Provide an appropriate number of index input parameters for the indicated **Index** functoid, where the appropriate number is determined by the number of looping **Record** nodes within which the **Field** node in the source schema is nested.</span></span> <span data-ttu-id="04a8e-109">Pour la création des paramètres d’entrée d’index, sélectionnez le fonctoid indiqué, cliquez sur le bouton de sélection (**...** ) associés à la **paramètres d’entrée** propriété de Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] fenêtre Propriétés, puis utiliser le ![ ] (../core/media/bts-tls-paraminsert.gif "bts_tls_paraminsert") bouton dans le **configurer \<fonctoid\> fonctoid** boîte de dialogue pour ajouter un ou plusieurs paramètres d’entrée constants, où la première représente un index dans le parent immédiat bouclage **enregistrement** nœud et les index suivant entrées paramètres représentent la boucle de niveau supérieur en plus distante **enregistrement** nœuds.</span><span class="sxs-lookup"><span data-stu-id="04a8e-109">To created index input parameters, select the indicated functoid, click the ellipsis (**...**) button associated with the **Input Parameters** property in the Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window, and then use the  ![](../core/media/bts-tls-paraminsert.gif "bts_tls_paraminsert") button within the **Configure \<Functoid\> Functoid** dialog box to add one or more constant input parameters, where the first one represents an index into the immediate parent looping **Record** node, and subsequent index input parameters represent increasingly remote ancestor looping **Record** nodes.</span></span>