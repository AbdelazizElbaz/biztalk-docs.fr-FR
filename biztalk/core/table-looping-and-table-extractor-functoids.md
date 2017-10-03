---
title: Bouclage de table et de fonctoids Extracteur de Table | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2907aada-f11a-485c-85c8-03092803ccf7
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 02d4433255ac00d51c88b45bd1a2b5205bd1c735
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="table-looping-and-table-extractor-functoids"></a>Bouclage de table et de fonctoids Extracteur de Table

## <a name="overview"></a>Vue d'ensemble
Dans un mappage, vous avez généralement une structure dans le message d'instance de sortie pour chaque structure du message d’instance d'entrée. Toutefois, dans certains cas, vous avez besoin qu’une structure d’instance d’entrée produise plusieurs structures d’instance de sortie. Le bouclage piloté par la table vous permet de créer des mappages générant de telles structures multiples.  
  
 Utilisations de bouclage piloté par les table le **bouclage de Table** fonctoid et **extracteur de Table** fonctoid. Le **bouclage de Table** le fonctoid ne comporte une table interne que vous configurez. Pour chaque d’entrée d’enregistrement ou un champ, la **bouclage de Table** fonctoid génère les lignes de la table, une à la fois. Par exemple, s’il existe dix enregistrements dans le message d’instance d’entrée et deux lignes dans la table interne de la **bouclage de Table**, le fonctoid génère un total de vingt lignes, deux pour chacun des dix enregistrements. Le **extracteur de Table** fonctoid extrait l’élément désiré à partir d’une ligne et le transmet le message d’instance de sortie.  
  
 Pour plus d’informations, consultez la **référence du fonctoid Bouclage de Table** et **référence du fonctoid Extracteur de Table** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].
  
## <a name="next-steps"></a>Étapes suivantes
  
-   [Fonctoid Bouclage de table](../core/table-looping-functoid.md)  
  
-   [Fonctoid Extracteur de table](../core/table-extractor-functoid.md)  
  
-   [Configuration de bouclage piloté par table](../core/table-driven-looping-configuration.md)  
  
-   [Exemple de bouclage piloté par table](../core/table-driven-looping-example.md)