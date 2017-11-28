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
ms.openlocfilehash: f2449f6c5572a3a29b620becdc4310f4152f2eac
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="error---first-input-to-table-extractor-functoid-not-valid"></a><span data-ttu-id="faaa1-102">Erreur - première entrée du fonctoid Extracteur de Table non valide</span><span class="sxs-lookup"><span data-stu-id="faaa1-102">Error - First Input to Table Extractor Functoid Not Valid</span></span>
<span data-ttu-id="faaa1-103">**Code d’erreur**</span><span class="sxs-lookup"><span data-stu-id="faaa1-103">**Error Code**</span></span>  
  
 <span data-ttu-id="faaa1-104">btm1019</span><span class="sxs-lookup"><span data-stu-id="faaa1-104">btm1019</span></span>  
  
 <span data-ttu-id="faaa1-105">**Explication**</span><span class="sxs-lookup"><span data-stu-id="faaa1-105">**Explanation**</span></span>  
  
 <span data-ttu-id="faaa1-106">Le premier paramètre d’entrée pour le fonctoid **extracteur de Table** fonctoid n’est pas un lien entre un **bouclage de Table** fonctoid, en fonction des besoins.</span><span class="sxs-lookup"><span data-stu-id="faaa1-106">The first input parameter to the indicated **Table Extractor** functoid is not a link from a **Table Looping** functoid, as required.</span></span>  
  
 <span data-ttu-id="faaa1-107">**Action de l’utilisateur**</span><span class="sxs-lookup"><span data-stu-id="faaa1-107">**User Action**</span></span>  
  
 <span data-ttu-id="faaa1-108">Créer un lien entre le **extracteur de Table** fonctoid et approprié **bouclage de Table** fonctoid en faisant glisser un d’eux à l’autre.</span><span class="sxs-lookup"><span data-stu-id="faaa1-108">Create a link between the indicated **Table Extractor** functoid and the appropriate **Table Looping** functoid by dragging one of them to the other.</span></span> <span data-ttu-id="faaa1-109">Dans une page de grille de mappage, le premier doit toujours se trouver à droite du second.</span><span class="sxs-lookup"><span data-stu-id="faaa1-109">The former functoid must be located to the right of the latter functoid in a map grid page.</span></span> <span data-ttu-id="faaa1-110">En outre, à l’aide de la **configurer \<fonctoid > fonctoid** boîte de dialogue zone, vérifiez que le nouveau lien est le premier paramètre d’entrée pour le fonctoid **extracteur de Table** fonctoid.</span><span class="sxs-lookup"><span data-stu-id="faaa1-110">Also, using the **Configure \<Functoid> Functoid** dialog box, ensure that the newly created link is the first input parameter to the indicated **Table Extractor** functoid.</span></span>