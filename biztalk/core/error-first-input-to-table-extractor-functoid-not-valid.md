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
# <a name="error---first-input-to-table-extractor-functoid-not-valid"></a>Erreur - première entrée du fonctoid Extracteur de Table non valide
**Code d’erreur**  
  
 btm1019  
  
 **Explication**  
  
 Le premier paramètre d’entrée pour le fonctoid **extracteur de Table** fonctoid n’est pas un lien entre un **bouclage de Table** fonctoid, en fonction des besoins.  
  
 **Action de l’utilisateur**  
  
 Créer un lien entre le **extracteur de Table** fonctoid et approprié **bouclage de Table** fonctoid en faisant glisser un d’eux à l’autre. Dans une page de grille de mappage, le premier doit toujours se trouver à droite du second. En outre, à l’aide de la **configurer \<fonctoid > fonctoid** boîte de dialogue zone, vérifiez que le nouveau lien est le premier paramètre d’entrée pour le fonctoid **extracteur de Table** fonctoid.