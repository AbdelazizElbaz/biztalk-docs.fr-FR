---
title: "Définition des agrégations en temps réel | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- real-time data, aggregating
- aggregations [BAM], real-time data
ms.assetid: cb3d7124-1663-4af2-9540-4171cc51568a
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b2b2df32149f67a002a5a6281b6f1abd848523a6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="defining-real-time-aggregations"></a>Définition des agrégations en temps réel
Dans certains cas, le temps constituant un paramètre primordial pour des tranches déterminées d'agrégations multidimensionnelles, il est nécessaire de rendre ces agrégations disponibles en temps réel. Supposons que votre entreprise vende des denrées périssables et que vous souhaitiez que l'agrégation des quantités de produits aux différentes étapes de la livraison soit disponible en temps réel. D'autre part, vous voulez disposer d'autres agrégations, comme celle de l'âge du consommateur moyen, mais uniquement à la fin du mois en vue d'une analyse Business Intelligence.  
  
-   À l’aide de la **tableau croisé dynamique** barre d’outils, marquez le tableau croisé dynamique sélectionné comme une agrégation en temps réel (RTA), le cas échéant. Le type de données contenu dans le tableau croisé dynamique doit déterminer s'il doit être affiché en temps réel. Par exemple, un rapport effectuant le suivi heure par heure des commandes sur le Web doit être affiché en temps réel, tandis qu'un rapport qui effectue le suivi journalier des totaux des ventes ne nécessite pas un affichage en temps réel.  
  
     ![](../core/media/ebiz-sdk-sample-bam12.gif "ebiz_sdk_sample_bam12")  
Bouton RTA  
  
> [!IMPORTANT]
>  Ne définissez pas plusieurs RTA utilisant une même activité BAM. Si vous le faites, les données RTA seront incorrectes lors de l'archivage des données BAM.  
  
 Pour plus d'informations sur les tableaux croisés dynamiques, consultez l'aide en ligne d'Excel. Après avoir créé votre tableau croisé dynamique, vous pouvez afficher vos données BAM actives.  
  
## <a name="see-also"></a>Voir aussi  
 [Affichage des données BAM actives](../core/viewing-live-bam-data.md)   
 [Dimension de progression](../core/progress-dimension.md)   
 [Dimension données](../core/data-dimension.md)   
 [Dimension de temps](../core/time-dimension.md)   
 [Dimension de plage numérique](../core/numeric-range-dimension.md)   
 [Définition des Dimensions](../core/defining-dimensions.md)