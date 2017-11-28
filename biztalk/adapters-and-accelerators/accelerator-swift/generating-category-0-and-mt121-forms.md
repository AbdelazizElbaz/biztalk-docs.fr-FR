---
title: "Génération de catégorie 0 et les formulaires MT121 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1470b8e1-0008-4f15-8958-ba4c7ecbffd8
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 40f9de5ff6e5f988422574640e13a45f8fd81632
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="generating-category-0-and-mt121-forms"></a><span data-ttu-id="91f72-102">Catégorie de génération 0 et MT121 formulaires</span><span class="sxs-lookup"><span data-stu-id="91f72-102">Generating Category 0 and MT121 Forms</span></span>
<span data-ttu-id="91f72-103">Catégorie 0 et génération de formulaires InfoPath de MT121 les fichiers de modèle différent.</span><span class="sxs-lookup"><span data-stu-id="91f72-103">Category 0 and MT121 InfoPath forms generation require different template files.</span></span> <span data-ttu-id="91f72-104">Formulaires de catégorie 0 sont divisées en 5 catégories.</span><span class="sxs-lookup"><span data-stu-id="91f72-104">Category 0 forms are divided into 5 categories.</span></span> <span data-ttu-id="91f72-105">Les messages des catégories générales sont générés de la même façon, comme le reste des catégories MT.</span><span class="sxs-lookup"><span data-stu-id="91f72-105">General categories messages are generated in the same way as do the rest of the MT categories.</span></span> <span data-ttu-id="91f72-106">Exemples d’autres 4 catégories avec leurs noms de message sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="91f72-106">Examples of other 4 categories with their message names are given below:</span></span>  
  
-   <span data-ttu-id="91f72-107">**Pour générer des formulaires de GAHeader catégorie 0 (MT036, MT042, MT047, MT072, MT077 et MT085) :**</span><span class="sxs-lookup"><span data-stu-id="91f72-107">**To generate category 0 GAHeader forms (MT036, MT042, MT047, MT072, MT077, and MT085):**</span></span>  
  
     `FormGenerator.exe -b -2 “C:\FormGeneratorUtility2008\GAHeader” " C:\FormGeneratorUtility2008\TemplateDS\InfoPath Form Template" c:\generatedforms c:\schemas -f GAHeaderForms.txt\`  
  
-   <span data-ttu-id="91f72-108">**Pour générer des formulaires de NoTextBlocks catégorie 0 (MT035, MT043, MT048 et MT049) :**</span><span class="sxs-lookup"><span data-stu-id="91f72-108">**To generate category 0 NoTextBlocks forms (MT035, MT043, MT048, and MT049):**</span></span>  
  
     `FormGenerator.exe -b -2 “C:\FormGeneratorUtility2008\NoTextBlocks” " C:\FormGeneratorUtility2008\TemplateDS\InfoPath Form Template" c:\generatedforms c:\schemas –f NoTextBlocksForms.txt`  
  
-   <span data-ttu-id="91f72-109">**Pour générer des formulaires de NoTrailer catégorie 0 (MT021) :**</span><span class="sxs-lookup"><span data-stu-id="91f72-109">**To generate category 0 NoTrailer forms (MT021):**</span></span>  
  
     `FormGenerator.exe -b -2 “C:\FormGeneratorUtility2008\NoTrailer” " C:\FormGeneratorUtility2008\TemplateDS\InfoPath Form Template" c:\generatedforms c:\schemas –f NoTrailerForms.txt`  
  
-   <span data-ttu-id="91f72-110">**Pour générer des formulaires de NoTrailerTextBlocks catégorie 0 (MT082) :**</span><span class="sxs-lookup"><span data-stu-id="91f72-110">**To generate category 0 NoTrailerTextBlocks forms (MT082):**</span></span>  
  
     `FormGenerator.exe -b -2 “C:\FormGeneratorUtility2008\NoTrailerTextBlocks” " C:\FormGeneratorUtility2008\TemplateDS\InfoPath Form Template" c:\generatedforms c:\schemas –f NoTrailerTextBlocks.txt`  
  
-   <span data-ttu-id="91f72-111">**Pour générer des formulaires de NoHeaderTextBlock catégorie 1 (MT121) :**</span><span class="sxs-lookup"><span data-stu-id="91f72-111">**To generate category 1 NoHeaderTextBlock forms (MT121):**</span></span>  
  
     `FormGenerator.exe -b -2 “C:\FormGeneratorUtility2008\ NoHeaderTextBlock” " C:\FormGeneratorUtility2008\TemplateDS\InfoPath Form Template" c:\generatedforms c:\schemas -f NoHeaderTextBlockForms.txt`