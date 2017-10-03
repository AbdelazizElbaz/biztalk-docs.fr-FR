---
title: "Les agrégations en temps réel | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BAM, aggregations
- aggregations [BAM], real-time data
ms.assetid: 0ef44641-e067-4108-b318-f4373ca8fa8f
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c1bc335c1c53fe106c460b7dcb5a27b803db97b1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="real-time-aggregations"></a>Agrégations RTA (Real-Time Aggregations)
Dans certains cas, des tranches spécifiques d'agrégations multidimensionnelles varient tellement rapidement dans le temps qu'elles doivent être disponibles en temps réel. Supposons que votre entreprise vende des denrées périssables et que vous souhaitiez que l'agrégation des quantités de produits aux différentes étapes de la livraison soit disponible en temps réel. D'autre part, vous voulez disposer d'autres agrégations, comme celle de l'âge du consommateur moyen, mais uniquement à la fin du mois en vue d'une analyse Business Intelligence.  
  
 Le composant BAM met alors en place une agrégation RTA sous forme de table gérée par des déclencheurs provenant eux-mêmes des tables de stockage de l'activité. En considérant que votre activité implique l'utilisation de bons de commandes (BC), l'agrégation RTA est susceptible de s'afficher comme présenté dans la figure ci-après.  
  
 ![](../core/media/bam-realtime-aggregations.gif "bam_realtime_aggregations")  
Agrégations RTA BAM  
  
 Dans ce schéma, si un nouveau bon de commande de 100 dollars provenant de Redmond est reçu, l'analyse BAM ajoute une contribution dans les cellules de la ligne {Redmond, InProcess} en effectuant une opération telle que `Count=Count+1` et `Amount=Amount+$100`.  
  
 Lorsque cette commande passe à l'étape de l'expédition, l'analyse BAM supprime la contribution de la ligne {Redmond, InProcess} et l'ajoute à la ligne {Redmond, Shipped}.  
  
 L'analyse BAM gère les données d'une agrégation RTA pour une fenêtre en ligne donnée, puis les supprime. Vous pouvez configurer la fenêtre en ligne en modifiant la ligne correspondante de la table **bam_Metadata_RealTimeAggregations**.  
  
 En matière d'agrégations en temps réél, prenez également en compte les considérations suivantes :  
  
-   Les agrégations en temps réel ont un impact non négligeable sur la vitesse à laquelle le composant BAM peut écrire les données. Il est donc recommandé de définir en tant qu'agrégations RTA uniquement les tranches de données les plus importantes de votre structure d'agrégations.  
  
-   La limitation des niveaux de dimension pour les agrégations en temps réel est 14. Par exemple, si vous créez un emplacement de la Dimension de données pour l’état et ville, cela compte comme deux niveaux (état et ville). Pour les dimensions de la progression, le nombre de niveaux possible correspond à celui de l'arborescence et pour les dimensions de temps, le nombre de niveaux correspond au nombre de sous-éléments. Par exemple, une Dimension de temps pour l’année, mois, jour, heure sera comptée comme quatre niveaux.  
  
-   BAM ne prend pas en charge les agrégations en temps réel de type **Min** et **Max**. Les agrégations BAM prend en charge sont **nombre**, **somme**, et **moyenne**.  
  
-   Vous devez systématiquement créer une dimension de temps pour une agrégation RTA et l'utiliser pour toutes les tranches de données. En effet, les données d'une agrégation RTA évoluent en fonction des date et heure du serveur et non des étapes majeures d'un processus d'entreprise particulier.  
  
-   Ne définissez pas plusieurs RTA utilisant une même activité BAM. Si vous le faites, les données RTA seront incorrectes lors de l'archivage des données BAM.  
  
 Les agrégations en temps réel ont un impact non négligeable sur la vitesse à laquelle le composant BAM peut écrire les données. Il est donc recommandé de définir en tant qu'agrégations RTA uniquement les tranches de données les plus importantes de votre structure d'agrégations.  
  
 La limitation des niveaux de dimension pour les agrégations en temps réel est 14. Par exemple, si vous créez un emplacement de la Dimension de données pour l’état et ville, cela compte comme deux niveaux (état et ville). Pour les dimensions de la progression, le nombre de niveaux possible correspond à celui de l'arborescence et pour les dimensions de temps, le nombre de niveaux correspond au nombre de sous-éléments. Par exemple, une Dimension de temps pour l’année, mois, jour, heure sera comptée comme quatre niveaux.  
  
 BAM ne prend pas en charge les agrégations en temps réel de type **Min** et **Max**. Les agrégations BAM prend en charge sont **nombre**, **somme**, et **moyenne**.  
  
 Ne définissez pas plusieurs RTA utilisant une même activité BAM. Si vous le faites, les données RTA seront incorrectes lors de l'archivage des données BAM.  
  
## <a name="see-also"></a>Voir aussi  
 [Qu’est une agrégation ?](../core/what-is-an-aggregation.md)