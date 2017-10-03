---
title: "Définition des Dimensions | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- aggregations [BAM], dimensions
- BAM, dimensions
- BAM views, dimensions
- Excel add-in [BAM], creating dimensions
- dimensions [BAM]
ms.assetid: c00e0c45-eef2-42d9-832c-4be08d79203f
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 916e8f29d7f1e48a7bab5f9ad78e65cb78e51802
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="defining-dimensions"></a>Définition des dimensions
Microsoft Excel définit les dimensions comme des catégories permettant d'organiser les données d'une table en niveaux en vue de leur utilisation pour l'analyse. Par exemple, une dimension de données concernant les lieux peut contenir des niveaux de type Ville, Département/Province et Pays/Région. Lors de la création de vues BAM à l'aide de l'Assistant correspondant, vous pouvez ajouter au moins une des dimensions suivantes :  
  
-   [Dimension de progression](../core/progress-dimension.md)  
  
-   [Dimension données](../core/data-dimension.md)  
  
-   [Dimension de temps](../core/time-dimension.md)  
  
-   [Dimension de plage numérique](../core/numeric-range-dimension.md)  
  
 ![](../core/media/bam-olap-cube.gif "bam_olap_cube")  
Données d'agrégation précalculées  
  
 De nouvelles dimensions sont ajoutées dans l'Assistant de la vue BAM. Pour pouvoir ajouter des dimensions, vous devez d'abord créer des Vues Activité d'entreprise à l'aide de l'Assistant. Pour plus d’informations sur l’utilisation de l’Assistant, consultez [définir des activités d’entreprise et les vues dans Excel](../core/defining-business-activities-and-views-in-excel.md).  
  
### <a name="to-add-new-dimensions"></a>Pour ajouter de nouvelles dimensions  
  
1.  Dans l’Assistant Vue BAM, cliquez sur **suivant** jusqu'à ce que vous voyiez la **nouvelle vue BAM : Dimensions et l’agrégation des mesures** page. Cliquez sur **de nouvelles Dimensions**.  
  
2.  Entrez un nom pour la dimension.  
  
3.  Dans la liste déroulante, sélectionnez un type de dimension.  
  
4.  Selon le type de dimension que vous avez sélectionné, renseignez les données appropriées, puis cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [Dimension de progression](../core/progress-dimension.md)