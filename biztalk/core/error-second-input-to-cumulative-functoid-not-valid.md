---
title: "Erreur - deuxième entrée du fonctoid cumulé n’est pas valide. | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: bts10.map.error.secondInputToCumulativeNotValid
ms.assetid: e41a58a7-e0a2-4284-bd19-279578a8915d
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a288bdaa9427cd26191571d180d39ad2dde9f9f5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="error---second-input-to-cumulative-functoid-not-valid"></a><span data-ttu-id="bc4d4-102">Erreur - deuxième entrée du fonctoid cumulé n’est pas valide.</span><span class="sxs-lookup"><span data-stu-id="bc4d4-102">Error - Second Input to Cumulative Functoid Not Valid</span></span>
<span data-ttu-id="bc4d4-103">**Code d’erreur**</span><span class="sxs-lookup"><span data-stu-id="bc4d4-103">**Error Code**</span></span>  
  
 <span data-ttu-id="bc4d4-104">btm1031</span><span class="sxs-lookup"><span data-stu-id="bc4d4-104">btm1031</span></span>  
  
 <span data-ttu-id="bc4d4-105">**Explication**</span><span class="sxs-lookup"><span data-stu-id="bc4d4-105">**Explanation**</span></span>  
  
 <span data-ttu-id="bc4d4-106">Le fonctoid **Cumulative** fonctoid a un deuxième paramètre d’entrée qui n’est pas valide.</span><span class="sxs-lookup"><span data-stu-id="bc4d4-106">The indicated **Cumulative** functoid has a second input parameter that is not valid.</span></span> <span data-ttu-id="bc4d4-107">Lorsqu'il est associé à un fonctoid cumulé, celui-ci doit être un entier positif qui indique la plage du schéma source dans laquelle l'accumulation est effectuée.</span><span class="sxs-lookup"><span data-stu-id="bc4d4-107">The second input parameter to cumulative functoids must be a positive integer that indicates the range within the source schema over which the accumulation will be performed.</span></span>  
  
 <span data-ttu-id="bc4d4-108">**Action de l’utilisateur**</span><span class="sxs-lookup"><span data-stu-id="bc4d4-108">**User Action**</span></span>  
  
 <span data-ttu-id="bc4d4-109">Sélectionnez le **Cumulative** fonctoid, cliquez sur le bouton de sélection (**...** ) associés à la **ordre les entrées de fonctoid** propriété de Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] fenêtre Propriétés, puis, dans le **configurer \<fonctoid > fonctoid** boîte de dialogue zone, vérifiez que le second paramètre d’entrée, le cas échéant, est un entier positif.</span><span class="sxs-lookup"><span data-stu-id="bc4d4-109">Select the indicated **Cumulative** functoid, click the ellipsis (**...**) button associated with the **Order Functoid Inputs** property in the Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window, and then in the **Configure \<Functoid> Functoid** dialog box, ensure that the second input parameter, if any, is a positive integer.</span></span>