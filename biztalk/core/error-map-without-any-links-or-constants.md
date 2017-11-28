---
title: "Erreur : mappage sans lien ni constante | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: bts10.map.error.mapWithoutAnyLinksOrConstants
ms.assetid: 8d1cdbcd-4bd0-4ddc-9e94-746e82b6ec48
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d697d6d053f2c0a36d0f5cb45002dca28a92f005
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="error---map-without-any-links-or-constants"></a><span data-ttu-id="65b35-102">Erreur : mappage sans lien ni constante</span><span class="sxs-lookup"><span data-stu-id="65b35-102">Error - Map Without Any Links or Constants</span></span>
<span data-ttu-id="65b35-103">**Code d’erreur**</span><span class="sxs-lookup"><span data-stu-id="65b35-103">**Error Code**</span></span>  
  
 <span data-ttu-id="65b35-104">btm1000</span><span class="sxs-lookup"><span data-stu-id="65b35-104">btm1000</span></span>  
  
 <span data-ttu-id="65b35-105">**Explication**</span><span class="sxs-lookup"><span data-stu-id="65b35-105">**Explanation**</span></span>  
  
 <span data-ttu-id="65b35-106">Le mappage ne comporte ni lien entre les schémas ni valeur constante dans le schéma de destination.</span><span class="sxs-lookup"><span data-stu-id="65b35-106">The map does not contain any links between the schemas, or constant values in the destination schema.</span></span> <span data-ttu-id="65b35-107">Par conséquent, ce mappage ne comportera aucune sortie.</span><span class="sxs-lookup"><span data-stu-id="65b35-107">Therefore, no output can be created from this map.</span></span>  
  
 <span data-ttu-id="65b35-108">**Action de l’utilisateur**</span><span class="sxs-lookup"><span data-stu-id="65b35-108">**User Action**</span></span>  
  
 <span data-ttu-id="65b35-109">Ajoutez les liens et les fonctoids nécessaires à la grille de mappage ou ajoutez des constantes au schéma de destination pour indiquer la méthode de transformation des messages d'instance correspondant au schéma source en messages d'instance correspondant au schéma de destination.</span><span class="sxs-lookup"><span data-stu-id="65b35-109">Add the appropriate links and, if appropriate, functoids to the map grid, or constants to the destination schema, to specify how instance messages conforming to the source schema should be transformed into instance messages conforming to the destination schema.</span></span>