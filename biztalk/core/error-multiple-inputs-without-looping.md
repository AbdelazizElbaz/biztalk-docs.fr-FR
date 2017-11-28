---
title: "Erreur : plusieurs entrées sans bouclage | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: bts10.map.error.multipleInputsWithoutLooping
ms.assetid: 7e55ad22-06a8-4a56-839d-a30b82819a68
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 93a8a11b25c3c1df52827bdbf4098f0cd37bdd8b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="error---multiple-inputs-without-looping"></a><span data-ttu-id="b6a26-102">Erreur : plusieurs entrées sans bouclage</span><span class="sxs-lookup"><span data-stu-id="b6a26-102">Error - Multiple Inputs Without Looping</span></span>
<span data-ttu-id="b6a26-103">**Code d’erreur**</span><span class="sxs-lookup"><span data-stu-id="b6a26-103">**Error Code**</span></span>  
  
 <span data-ttu-id="b6a26-104">btm1004</span><span class="sxs-lookup"><span data-stu-id="b6a26-104">btm1004</span></span>  
  
 <span data-ttu-id="b6a26-105">**Explication**</span><span class="sxs-lookup"><span data-stu-id="b6a26-105">**Explanation**</span></span>  
  
 <span data-ttu-id="b6a26-106">Plusieurs liens sont connectés au nœud indiqué dans le schéma de destination, qui est valide uniquement lorsqu’un des nœuds ancêtres du nœud indiqué est connecté à un **bouclage** fonctoid.</span><span class="sxs-lookup"><span data-stu-id="b6a26-106">Multiple links are connected to the indicated node in the destination schema, which is only valid when one of the ancestor nodes of the indicated node is connected to a **Looping** functoid.</span></span>  
  
 <span data-ttu-id="b6a26-107">**Action de l’utilisateur**</span><span class="sxs-lookup"><span data-stu-id="b6a26-107">**User Action**</span></span>  
  
 <span data-ttu-id="b6a26-108">Supprimez tous les liens, sauf un, associés au nœud indiqué dans le schéma de destination ou connectez l'un des nœuds de niveau supérieur du nœud indiqué à un fonctoid de bouclage.</span><span class="sxs-lookup"><span data-stu-id="b6a26-108">Either remove all but one of the links to the indicated node in the destination schema, or connect one of the ancestor nodes of the indicated node to a looping functoid.</span></span>