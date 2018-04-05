---
title: 'Erreur : trop d’entrées de données pour ce nœud | Documents Microsoft'
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- bts10.map.error.tooManyDataInputsToNode
ms.assetid: 176805f0-2d6d-4072-b866-132b98c7e4b5
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c9e465f861c4048708f41ea86f04ffd52375dec9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="error---too-many-data-inputs-to-node"></a><span data-ttu-id="5f4fc-102">Erreur : trop d’entrées de données pour ce nœud</span><span class="sxs-lookup"><span data-stu-id="5f4fc-102">Error - Too Many Data Inputs to Node</span></span>
<span data-ttu-id="5f4fc-103">**Code d’erreur**</span><span class="sxs-lookup"><span data-stu-id="5f4fc-103">**Error Code**</span></span>  
  
 <span data-ttu-id="5f4fc-104">btm1005</span><span class="sxs-lookup"><span data-stu-id="5f4fc-104">btm1005</span></span>  
  
 <span data-ttu-id="5f4fc-105">**Explication**</span><span class="sxs-lookup"><span data-stu-id="5f4fc-105">**Explanation**</span></span>  
  
 <span data-ttu-id="5f4fc-106">Il existe un plus grand nombre de liens connectés au nœud indiqué dans le schéma de destination que le nombre de liens d’entrée le **bouclage** fonctoid qui est connecté à un nœud d’ancêtre du nœud indiqué.</span><span class="sxs-lookup"><span data-stu-id="5f4fc-106">There are a greater number of links connected to the indicated node in the destination schema than the number of input links to the **Looping** functoid that is connected to an ancestor node of the indicated node.</span></span> <span data-ttu-id="5f4fc-107">Ces deux nombres doivent être identiques.</span><span class="sxs-lookup"><span data-stu-id="5f4fc-107">The number of links of the former and latter types should match.</span></span>  
  
 <span data-ttu-id="5f4fc-108">**Action de l’utilisateur**</span><span class="sxs-lookup"><span data-stu-id="5f4fc-108">**User Action**</span></span>  
  
 <span data-ttu-id="5f4fc-109">Reprendre le nombre de liens connecté au nœud indiqué et en le **bouclage** connectés au nœud de niveau supérieur afin qu’elles correspondent.</span><span class="sxs-lookup"><span data-stu-id="5f4fc-109">Rework the number of links connected to the indicated node and to the **Looping** functoid connected to the ancestor node so that they match.</span></span>