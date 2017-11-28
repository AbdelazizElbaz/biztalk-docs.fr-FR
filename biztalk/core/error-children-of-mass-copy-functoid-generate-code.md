---
title: "Erreur : Code généré par les enfants du fonctoid copie de masse | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: bts10.map.error.massCopyChildtenGenCode
ms.assetid: c791009b-241b-4004-b0c6-f1536bb119c5
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 68183a90be46b176d13100b02cbed2798fe24b34
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="error---children-of-mass-copy-functoid-generate-code"></a><span data-ttu-id="100fd-102">Erreur : Code généré par les enfants du fonctoid copie de masse</span><span class="sxs-lookup"><span data-stu-id="100fd-102">Error - Children of Mass Copy Functoid Generate Code</span></span>
<span data-ttu-id="100fd-103">**Code d’erreur**</span><span class="sxs-lookup"><span data-stu-id="100fd-103">**Error Code**</span></span>  
  
 <span data-ttu-id="100fd-104">btm1068</span><span class="sxs-lookup"><span data-stu-id="100fd-104">btm1068</span></span>  
  
 <span data-ttu-id="100fd-105">**Explication**</span><span class="sxs-lookup"><span data-stu-id="100fd-105">**Explanation**</span></span>  
  
 <span data-ttu-id="100fd-106">Un scénario qui se révèle contradictoire avec la fonctionnalité de la **copie de masse** fonctoid a été trouvé dans le mappage.</span><span class="sxs-lookup"><span data-stu-id="100fd-106">A scenario that contradicts the functionality of the **Mass Copy** functoid was found in the map.</span></span> <span data-ttu-id="100fd-107">Dans le schéma de destination, les descendants d’un nœud qui est lié à la sortie d’un **copie de masse** fonctoid tentent de générer leur propre code XSLT.</span><span class="sxs-lookup"><span data-stu-id="100fd-107">In the destination schema, descendent nodes of a node that is linked to the output of a **Mass Copy** functoid are attempting to generate XSLT code of their own.</span></span>  
  
 <span data-ttu-id="100fd-108">**Action de l’utilisateur**</span><span class="sxs-lookup"><span data-stu-id="100fd-108">**User Action**</span></span>  
  
 <span data-ttu-id="100fd-109">Supprimer l’incompatibilité en modifiant l’utilisation de la **copie de masse** fonctoid ou modifiez les nœuds enfants, tels qu’ils ne sont plus de générer leur propre code XSLT.</span><span class="sxs-lookup"><span data-stu-id="100fd-109">Remove the incompatibility by changing the usage of the relevant **Mass Copy** functoid or changing the child nodes such that they no longer generate XSLT code of their own.</span></span>