---
title: "Erreur : plusieurs chemins de bouclage | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: bts10.map.error.multipleLoopPaths
ms.assetid: 3f7c0c1c-5aaa-4da9-99ab-78bac536b8dd
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: afdcb1a235c71163552fd5f6b255e572feef8dc5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="error---multiple-loop-paths"></a><span data-ttu-id="81f39-102">Erreur : plusieurs chemins de bouclage</span><span class="sxs-lookup"><span data-stu-id="81f39-102">Error - Multiple Loop Paths</span></span>
<span data-ttu-id="81f39-103">**Code d’erreur**</span><span class="sxs-lookup"><span data-stu-id="81f39-103">**Error Code**</span></span>  
  
 <span data-ttu-id="81f39-104">btm1030</span><span class="sxs-lookup"><span data-stu-id="81f39-104">btm1030</span></span>  
  
 <span data-ttu-id="81f39-105">**Explication**</span><span class="sxs-lookup"><span data-stu-id="81f39-105">**Explanation**</span></span>  
  
 <span data-ttu-id="81f39-106">Le nœud indiqué dans le schéma de destination possède plusieurs chemins de bouclage sources.</span><span class="sxs-lookup"><span data-stu-id="81f39-106">The indicated node in the destination schema has multiple source loop paths.</span></span>  
  
 <span data-ttu-id="81f39-107">**Action de l’utilisateur**</span><span class="sxs-lookup"><span data-stu-id="81f39-107">**User Action**</span></span>  
  
 <span data-ttu-id="81f39-108">Utilisez un **bouclage** fonctoid pour spécifier explicitement le nœud dans le schéma source sur laquelle le bouclage sera effectué.</span><span class="sxs-lookup"><span data-stu-id="81f39-108">Use a **Looping** functoid to explicitly specify the node in the source schema over which the looping will be performed.</span></span>