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
# <a name="generating-category-0-and-mt121-forms"></a>Catégorie de génération 0 et MT121 formulaires
Catégorie 0 et génération de formulaires InfoPath de MT121 les fichiers de modèle différent. Formulaires de catégorie 0 sont divisées en 5 catégories. Les messages des catégories générales sont générés de la même façon, comme le reste des catégories MT. Exemples d’autres 4 catégories avec leurs noms de message sont les suivants :  
  
-   **Pour générer des formulaires de GAHeader catégorie 0 (MT036, MT042, MT047, MT072, MT077 et MT085) :**  
  
     `FormGenerator.exe -b -2 “C:\FormGeneratorUtility2008\GAHeader” " C:\FormGeneratorUtility2008\TemplateDS\InfoPath Form Template" c:\generatedforms c:\schemas -f GAHeaderForms.txt\`  
  
-   **Pour générer des formulaires de NoTextBlocks catégorie 0 (MT035, MT043, MT048 et MT049) :**  
  
     `FormGenerator.exe -b -2 “C:\FormGeneratorUtility2008\NoTextBlocks” " C:\FormGeneratorUtility2008\TemplateDS\InfoPath Form Template" c:\generatedforms c:\schemas –f NoTextBlocksForms.txt`  
  
-   **Pour générer des formulaires de NoTrailer catégorie 0 (MT021) :**  
  
     `FormGenerator.exe -b -2 “C:\FormGeneratorUtility2008\NoTrailer” " C:\FormGeneratorUtility2008\TemplateDS\InfoPath Form Template" c:\generatedforms c:\schemas –f NoTrailerForms.txt`  
  
-   **Pour générer des formulaires de NoTrailerTextBlocks catégorie 0 (MT082) :**  
  
     `FormGenerator.exe -b -2 “C:\FormGeneratorUtility2008\NoTrailerTextBlocks” " C:\FormGeneratorUtility2008\TemplateDS\InfoPath Form Template" c:\generatedforms c:\schemas –f NoTrailerTextBlocks.txt`  
  
-   **Pour générer des formulaires de NoHeaderTextBlock catégorie 1 (MT121) :**  
  
     `FormGenerator.exe -b -2 “C:\FormGeneratorUtility2008\ NoHeaderTextBlock” " C:\FormGeneratorUtility2008\TemplateDS\InfoPath Form Template" c:\generatedforms c:\schemas -f NoHeaderTextBlockForms.txt`