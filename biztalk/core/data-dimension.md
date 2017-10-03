---
title: "Dimension données | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Data dimension [BAM]
- aggregations [BAM], data dimensions
ms.assetid: 07b5e56a-4fd5-4c88-a98a-758e514d0621
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b7138cf31a9cb86a9ba949142129ac5c906754b1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="data-dimension"></a>Dimension Données
Définir une dimension de données permet d'utiliser la valeur de certains éléments de texte de l'activité BAM dans des lignes ou des colonnes. Par exemple, une dimension de données nommée Produit peut être utilisée pour créer le tableau suivant :  
  
|Product|Compter|  
|-------------|-----------|  
|Raquettes de tennis|100|  
|Ballons de football|200|  
  
 De même, plusieurs dimensions de données peuvent être définies dans l'Assistant Vue BAM. Par exemple, définissez une dimension de données nommée **emplacement** avec les niveaux **état** et **Ville** peut être utilisé pour créer le tableau suivant :  
  
|||||  
|-|-|-|-|  
||California||Washington|  
||Los Angeles|San Francisco|Seattle|  
|Raquettes de tennis|50|20|30|  
|Ballons de football|130|50|20|  
  
 Dans ce tableau, la dimension Produit a été utilisée sur les lignes et la dimension Lieu sur les colonnes.  
  
## <a name="see-also"></a>Voir aussi  
 [Dimension de temps](../core/time-dimension.md)   
 [Dimension de progression](../core/progress-dimension.md)   
 [Dimension de plage numérique](../core/numeric-range-dimension.md)   
 [Définition des Dimensions](../core/defining-dimensions.md)