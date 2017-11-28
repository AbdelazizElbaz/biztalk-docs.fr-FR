---
title: "Erreur : fonctoid Variable incompatibilité | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: bts10.map.error.functoidVariableInputMismatch
ms.assetid: fda3066b-d0de-4f61-b78f-4726f6796e1f
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c619c1eded27cb3ac17bcc5a1630a367deaad078
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="error---functoid-variable-input-mismatch"></a><span data-ttu-id="78da1-102">Erreur : fonctoid Variable incompatibilité</span><span class="sxs-lookup"><span data-stu-id="78da1-102">Error - Functoid Variable Input Mismatch</span></span>
<span data-ttu-id="78da1-103">**Code d’erreur**</span><span class="sxs-lookup"><span data-stu-id="78da1-103">**Error Code**</span></span>  
  
 <span data-ttu-id="78da1-104">btm1011</span><span class="sxs-lookup"><span data-stu-id="78da1-104">btm1011</span></span>  
  
 <span data-ttu-id="78da1-105">**Explication**</span><span class="sxs-lookup"><span data-stu-id="78da1-105">**Explanation**</span></span>  
  
 <span data-ttu-id="78da1-106">Le fonctoid indiqué ne comporte pas un nombre correct de paramètres d'entrée définis.</span><span class="sxs-lookup"><span data-stu-id="78da1-106">The indicated functoid does not have the correct number of input parameters specified.</span></span> <span data-ttu-id="78da1-107">Le nombre de paramètres d'entrée doit correspondre à la plage indiquée.</span><span class="sxs-lookup"><span data-stu-id="78da1-107">The number of input parameters must be in the specified range.</span></span>  
  
 <span data-ttu-id="78da1-108">**Action de l’utilisateur**</span><span class="sxs-lookup"><span data-stu-id="78da1-108">**User Action**</span></span>  
  
 <span data-ttu-id="78da1-109">Utilisez une ou plusieurs des méthodes suivantes pour affecter le nombre correct de paramètres d'entrée au fonctoid concerné, tout en veillant à ce que l'ordre des paramètres soit respecté :</span><span class="sxs-lookup"><span data-stu-id="78da1-109">Use one or more of the following methods to provide the indicated number of input parameters to the indicated functoid, paying particular attention to the expected order of input parameters:</span></span>  
  
-   <span data-ttu-id="78da1-110">Pour créer des liens supplémentaires, déplacez la souris pour créer un lien entre d'une part le fonctoid indiqué et d'autre part, soit des nœuds du schéma source, soit la sortie d'autres fonctoids situés à gauche du fonctoid indiqué dans la page de grille de mappage.</span><span class="sxs-lookup"><span data-stu-id="78da1-110">To create additional links, drag to create links between the indicated functoid and either nodes in the source schema or the output of other functoids that are located to the left of the indicated functoid in a map grid page.</span></span>  
  
-   <span data-ttu-id="78da1-111">Pour créer des liens supplémentaires, sélectionnez le fonctoid indiqué, cliquez sur le bouton de sélection (**...** ) associés à la **paramètres d’entrée** propriété de Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] fenêtre Propriétés, puis configurez et organisez les paramètres d’entrée dans le **configurer \<Fonctoid > fonctoid** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="78da1-111">To create additional links, select the indicated functoid, click the ellipsis (**...**) button associated with the **Input Parameters** property in the Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window, and then configure and rearrange the order of the input parameters in the **Configure \<Functoid> Functoid** dialog box.</span></span> <span data-ttu-id="78da1-112">Dans cette boîte de dialogue, vous pouvez créer des paramètres d'entrée constants, leur affecter des valeurs et les classer dans le même ordre que celui des autres paramètres d'entrée.</span><span class="sxs-lookup"><span data-stu-id="78da1-112">Constant input parameters can be created, given values, and put in the proper order relative to the other input parameters in this dialog box.</span></span>  
  
-   <span data-ttu-id="78da1-113">Pour supprimer des liens existants, chaque lien sur le côté gauche du fonctoid indiqué, cliquez sur le lien, puis **supprimer**.</span><span class="sxs-lookup"><span data-stu-id="78da1-113">To remove existing links, for each link connected to the left side of the indicated functoid, right-click the link and then click **Delete**.</span></span>  
  
-   <span data-ttu-id="78da1-114">Pour supprimer des liens existants, sélectionnez le fonctoid indiqué, cliquez sur le bouton de sélection (**...** ) associés à la **paramètres d’entrée** propriété dans le [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] fenêtre Propriétés, puis, dans le **configurer \<fonctoid > fonctoid** boîte de dialogue zone, supprimez les paramètres d’entrée tout en sélectionnant et en cliquant sur le ![](../core/media/bts-tls-paramdelete.gif "bts_tls_paramdelete") bouton pour chacun d’eux.</span><span class="sxs-lookup"><span data-stu-id="78da1-114">To remove existing links, select the indicated functoid, click the ellipsis (**...**) button associated with the **Input Parameters** property in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window, and then in the **Configure \<Functoid> Functoid** dialog box, delete all input parameters by selecting and clicking the ![](../core/media/bts-tls-paramdelete.gif "bts_tls_paramdelete") button for each of them.</span></span> <span data-ttu-id="78da1-115">Cette méthode est recommandée pour la suppression des paramètres d'entrée constants.</span><span class="sxs-lookup"><span data-stu-id="78da1-115">You must use this method to delete constant input parameters.</span></span>