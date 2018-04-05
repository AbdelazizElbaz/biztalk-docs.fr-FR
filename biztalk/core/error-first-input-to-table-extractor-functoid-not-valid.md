---
title: Erreur - première entrée du fonctoid Extracteur de Table non valide | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- bts10.map.error.firstInputToTableExtractorNotValid
ms.assetid: 5b197531-9bf4-49c6-ad3a-b3ba92d37701
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 86d501c18bf104a0f538ef90d10510e7d9ec0f02
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="error---first-input-to-table-extractor-functoid-not-valid"></a>Erreur - première entrée du fonctoid Extracteur de Table non valide
**Code d’erreur**  
  
 btm1019  
  
 **Explication**  
  
 Le premier paramètre d’entrée pour le fonctoid **extracteur de Table** fonctoid n’est pas un lien entre un **bouclage de Table** fonctoid, en fonction des besoins.  
  
 **Action de l’utilisateur**  
  
 Créer un lien entre le **extracteur de Table** fonctoid et approprié **bouclage de Table** fonctoid en faisant glisser un d’eux à l’autre. Dans une page de grille de mappage, le premier doit toujours se trouver à droite du second. En outre, à l’aide de la **configurer \<fonctoid\> fonctoid** boîte de dialogue zone, vérifiez que le nouveau lien est le premier paramètre d’entrée pour le fonctoid **extracteur de Table** fonctoid.