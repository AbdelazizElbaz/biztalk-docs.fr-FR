---
title: "Erreur - première entrée du fonctoid Extracteur de Table non valide | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: bts10.map.error.firstInputToTableExtractorNotValid
ms.assetid: 5b197531-9bf4-49c6-ad3a-b3ba92d37701
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 86d501c18bf104a0f538ef90d10510e7d9ec0f02
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="error---first-input-to-table-extractor-functoid-not-valid"></a><span data-ttu-id="df891-102">Erreur - première entrée du fonctoid Extracteur de Table non valide</span><span class="sxs-lookup"><span data-stu-id="df891-102">Error - First Input to Table Extractor Functoid Not Valid</span></span>
<span data-ttu-id="df891-103">**Code d’erreur**</span><span class="sxs-lookup"><span data-stu-id="df891-103">**Error Code**</span></span>  
  
 <span data-ttu-id="df891-104">btm1019</span><span class="sxs-lookup"><span data-stu-id="df891-104">btm1019</span></span>  
  
 <span data-ttu-id="df891-105">**Explication**</span><span class="sxs-lookup"><span data-stu-id="df891-105">**Explanation**</span></span>  
  
 <span data-ttu-id="df891-106">Le premier paramètre d’entrée pour le fonctoid **extracteur de Table** fonctoid n’est pas un lien entre un **bouclage de Table** fonctoid, en fonction des besoins.</span><span class="sxs-lookup"><span data-stu-id="df891-106">The first input parameter to the indicated **Table Extractor** functoid is not a link from a **Table Looping** functoid, as required.</span></span>  
  
 <span data-ttu-id="df891-107">**Action de l’utilisateur**</span><span class="sxs-lookup"><span data-stu-id="df891-107">**User Action**</span></span>  
  
 <span data-ttu-id="df891-108">Créer un lien entre le **extracteur de Table** fonctoid et approprié **bouclage de Table** fonctoid en faisant glisser un d’eux à l’autre.</span><span class="sxs-lookup"><span data-stu-id="df891-108">Create a link between the indicated **Table Extractor** functoid and the appropriate **Table Looping** functoid by dragging one of them to the other.</span></span> <span data-ttu-id="df891-109">Dans une page de grille de mappage, le premier doit toujours se trouver à droite du second.</span><span class="sxs-lookup"><span data-stu-id="df891-109">The former functoid must be located to the right of the latter functoid in a map grid page.</span></span> <span data-ttu-id="df891-110">En outre, à l’aide de la **configurer \<fonctoid\> fonctoid** boîte de dialogue zone, vérifiez que le nouveau lien est le premier paramètre d’entrée pour le fonctoid **extracteur de Table** fonctoid.</span><span class="sxs-lookup"><span data-stu-id="df891-110">Also, using the **Configure \<Functoid\> Functoid** dialog box, ensure that the newly created link is the first input parameter to the indicated **Table Extractor** functoid.</span></span>