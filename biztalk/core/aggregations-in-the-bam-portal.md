---
title: "Agrégations dans le portail BAM | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BAM portal, pivot tables
- BAM, data analysis
- pivot tables [BAM portal]
- BAM portal, charts
- data, analysis [BAM]
- data, OLAP cubes
- aggregations [BAM], BAM portal
- charts, BAM portal
- BAM portal, aggregations
ms.assetid: 1c689563-714b-4573-9c18-a5b0efe97fb8
caps.latest.revision: "21"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 43ef0adfacea0a29ea47584ed545884ffb8fa8bf
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="aggregations-in-the-bam-portal"></a>Agrégations dans le portail BAM
Les agrégations sont des tables contenant des données précalculées que vous pouvez utiliser pour un traitement analytique à l'aide d'un cube OLAP. Elles rendent l'interrogation des bases de données multidimensionnelles simple et efficace. Lorsque vous créez et que vous déployez votre modèle d'observation (c'est-à-dire, une définition de niveau élevé de vos données d'entreprise) à l'aide du complément BAM pour Excel, vous créez des agrégations permettant d'évaluer rapidement des collections de données relatives aux indicateurs de performance clés (KPI).  
  
## <a name="types-of-aggregations"></a>Types d'agrégations  
 Les agrégations peuvent être planifiées ou RTA (agrégations en temps réel). Les agrégations planifiées sont des cubes OLAP correspondant à une capture instantanée de vos données d'entreprise à un moment que vous précisez. Les agrégations en temps réel vous permettent de visualiser vos données d'entreprise en fonction de points d'arrêt déclencheurs que vous spécifiez. Le système BAM se sert de ces points pour vous avertir au moyen d'une alerte lorsque la valeur de l'indicateur de performance clé est atteinte.  
  
## <a name="pivottable-view"></a>Vue de tableau croisé dynamique  
 La zone réservée à la vue de tableau croisé dynamique permet d'afficher le rapport de tableau croisé dynamique que vous élaborez à l'aide du complément BAM pour Excel. Les composants Web Office permettent de manipuler le rapport de tableau croisé dynamique pour présenter la vue des données qui répond à vos besoins...  
  
> [!NOTE]
>  Dans l'affichage d'un rapport de tableau croisé dynamique, il se peut que certaines lignes contiennent des données nulles à la fois pour les agrégations RTA et pour les agrégations précalculées (implémentation OLAP) si les étapes majeures de l'activité ont été atteintes mais ne sont pas utilisées dans la dimension de progression. Il également possible de rencontrer des lignes comportant des données nulles si la dimension de temps est utilisée par une dimension de progression et qu'elle est rattachée à une étape majeure « acquittée » au lieu d'être « rattachée », par exemple. Dans ce cas, une instance d'activité est générée et déclenche l'étape majeure reçue, sans avoir déclenché l'étape majeure acquittée. La valeur zéro apparaît alors dans la ligne correspondant à la dimension de temps.  Afin d'éviter ce type de problème, liez la dimension de temps en remontant jusqu'à l'étape majeure acquittée.  
  
 ![](../core/media/aggregationpivottabletotal.gif "AggregationPivotTableTotal")  
  
 Tenez compte des considérations suivantes lorsque vous utilisez les composants Office Web Components dans le portail BAM afin de modifier votre rapport de tableau croisé dynamique :  
  
-   Dans Excel, les rapports de tableau croisé dynamique incluent un champ Page où vous pouvez insérer une dimension de tranche horaire. Office Web Components utilisés par le portail BAM n’incluent pas d’un champ de Page. Si votre rapport de tableau croisé dynamique Excel utilise le champ Page pour une ou plusieurs dimensions, les données correspondant à ce champ dans le rapport du portail BAM ne s'affichent pas.  
  
-   Office Web Components affiche les données dans le cadre Contenu du portail BAM. L'espace disponible dans ce frame étant restreint, lorsque vous ajoutez des dimensions à partir de la liste de champs dans la zone des colonnes, il se peut que l'affichage des noms des dimensions dans le tableau croisé dynamique soit effacé, partiellement ou en totalité.  
  
 Pour plus d’informations sur les tableaux croisés dynamiques, consultez « Terminologie relative aux » à [http://go.microsoft.com/fwlink/?LinkId=55416](http://go.microsoft.com/fwlink/?LinkId=55416).  
  
## <a name="chart-view"></a>Vue de graphique  
 La vue de graphique est une zone permettant d'afficher l'agrégation sous forme de graphique. Les composants Office Web Components vous permettent de modifier les détails relatifs à une agrégation dans un graphique de façon à ajuster les données d'un rapport en fonction de vos besoins. Lorsque vous procédez à vos ajustements en déplaçant par glisser-déplacer les éléments de données figurant dans la liste des champs du graphique, le rapport de tableau croisé dynamique de l'agrégation est automatiquement mis à jour en conséquence. Vous pouvez rechercher des données dans le tableau croisé dynamique afin de créer une alerte dans la nouvelle vue d'agrégation.  
  
 ![](../core/media/aggregationchartview.gif "AggregationChartView")  
  
## <a name="more"></a>Plus  
  
-   [Comment définir une alerte](../core/how-to-set-an-alert.md)  
  
-   [Comment afficher les résultats d’une recherche d’activité](../core/how-to-view-the-results-of-an-activity-search.md)  
  
-   [Comment modifier une agrégation](../core/how-to-modify-an-aggregation.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Qu’est une agrégation ?](../core/what-is-an-aggregation.md)