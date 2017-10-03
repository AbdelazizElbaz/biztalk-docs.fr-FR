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
# <a name="aggregations-in-the-bam-portal"></a><span data-ttu-id="daea0-102">Agrégations dans le portail BAM</span><span class="sxs-lookup"><span data-stu-id="daea0-102">Aggregations in the BAM Portal</span></span>
<span data-ttu-id="daea0-103">Les agrégations sont des tables contenant des données précalculées que vous pouvez utiliser pour un traitement analytique à l'aide d'un cube OLAP.</span><span class="sxs-lookup"><span data-stu-id="daea0-103">Aggregations are tables of precalculated data you can use for analytical processing with an OLAP cube.</span></span> <span data-ttu-id="daea0-104">Elles rendent l'interrogation des bases de données multidimensionnelles simple et efficace.</span><span class="sxs-lookup"><span data-stu-id="daea0-104">Aggregations facilitate the efficient querying of multidimensional databases.</span></span> <span data-ttu-id="daea0-105">Lorsque vous créez et que vous déployez votre modèle d'observation (c'est-à-dire, une définition de niveau élevé de vos données d'entreprise) à l'aide du complément BAM pour Excel, vous créez des agrégations permettant d'évaluer rapidement des collections de données relatives aux indicateurs de performance clés (KPI).</span><span class="sxs-lookup"><span data-stu-id="daea0-105">When you create and deploy your observation model (the high-level definition of your business data) using the BAM Add-In for Excel, you create aggregations that you can use to quickly evaluate collections of data relating your Key Performance Indicators (KPIs).</span></span>  
  
## <a name="types-of-aggregations"></a><span data-ttu-id="daea0-106">Types d'agrégations</span><span class="sxs-lookup"><span data-stu-id="daea0-106">Types of aggregations</span></span>  
 <span data-ttu-id="daea0-107">Les agrégations peuvent être planifiées ou RTA (agrégations en temps réel).</span><span class="sxs-lookup"><span data-stu-id="daea0-107">Aggregations can be either scheduled or real-time.</span></span> <span data-ttu-id="daea0-108">Les agrégations planifiées sont des cubes OLAP correspondant à une capture instantanée de vos données d'entreprise à un moment que vous précisez.</span><span class="sxs-lookup"><span data-stu-id="daea0-108">Scheduled aggregations are OLAP cubes, which represent a snapshot of your business data at a time you specify.</span></span> <span data-ttu-id="daea0-109">Les agrégations en temps réel vous permettent de visualiser vos données d'entreprise en fonction de points d'arrêt déclencheurs que vous spécifiez. Le système BAM se sert de ces points pour vous avertir au moyen d'une alerte lorsque la valeur de l'indicateur de performance clé est atteinte.</span><span class="sxs-lookup"><span data-stu-id="daea0-109">Real-time aggregations allow a view of your business data based on trigger points that you specify, allowing the BAM system to notify you through an alert as soon as a KPI has been reached.</span></span>  
  
## <a name="pivottable-view"></a><span data-ttu-id="daea0-110">Vue de tableau croisé dynamique</span><span class="sxs-lookup"><span data-stu-id="daea0-110">PivotTable View</span></span>  
 <span data-ttu-id="daea0-111">La zone réservée à la vue de tableau croisé dynamique permet d'afficher le rapport de tableau croisé dynamique que vous élaborez à l'aide du complément BAM pour Excel.</span><span class="sxs-lookup"><span data-stu-id="daea0-111">The PivotTable View area displays the PivotTable report that you design using the BAM Add-In for Excel.</span></span> <span data-ttu-id="daea0-112">Les composants Web Office permettent de manipuler le rapport de tableau croisé dynamique pour présenter la vue des données qui répond à vos besoins...</span><span class="sxs-lookup"><span data-stu-id="daea0-112">The Office Web Components allow you to manipulate the PivotTable report to present the view of the data that best fits your needs..</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="daea0-113">Dans l'affichage d'un rapport de tableau croisé dynamique, il se peut que certaines lignes contiennent des données nulles à la fois pour les agrégations RTA et pour les agrégations précalculées (implémentation OLAP) si les étapes majeures de l'activité ont été atteintes mais ne sont pas utilisées dans la dimension de progression.</span><span class="sxs-lookup"><span data-stu-id="daea0-113">When viewing a PivotTable report it is possible that some rows could contain null data in both real-time aggregations (RTAs) and precalculated aggregations (an OLAP implementation) if the milestones in the activity have been reached but are not used in the progress dimension.</span></span> <span data-ttu-id="daea0-114">Il également possible de rencontrer des lignes comportant des données nulles si la dimension de temps est utilisée par une dimension de progression et qu'elle est rattachée à une étape majeure « acquittée » au lieu d'être « rattachée », par exemple.</span><span class="sxs-lookup"><span data-stu-id="daea0-114">It is also possible to encounter rows with null data if the time dimension is used in the context of a progress dimension and is anchored to a milestone such as "acknowledged" instead of "received."</span></span> <span data-ttu-id="daea0-115">Dans ce cas, une instance d'activité est générée et déclenche l'étape majeure reçue, sans avoir déclenché l'étape majeure acquittée. La valeur zéro apparaît alors dans la ligne correspondant à la dimension de temps.</span><span class="sxs-lookup"><span data-stu-id="daea0-115">In this case an activity instance is received and triggers the received milestone, but the activity has not yet triggered the acknowledge milestone and a zero will appear in the time dimension row.</span></span>  <span data-ttu-id="daea0-116">Afin d'éviter ce type de problème, liez la dimension de temps en remontant jusqu'à l'étape majeure acquittée.</span><span class="sxs-lookup"><span data-stu-id="daea0-116">To avoid this situation, link the time dimension up to the received milestone.</span></span>  
  
 ![](../core/media/aggregationpivottabletotal.gif "AggregationPivotTableTotal")  
  
 <span data-ttu-id="daea0-117">Tenez compte des considérations suivantes lorsque vous utilisez les composants Office Web Components dans le portail BAM afin de modifier votre rapport de tableau croisé dynamique :</span><span class="sxs-lookup"><span data-stu-id="daea0-117">Keep these points in mind when using the Office Web Components in the BAM portal to modify your PivotTable report:</span></span>  
  
-   <span data-ttu-id="daea0-118">Dans Excel, les rapports de tableau croisé dynamique incluent un champ Page où vous pouvez insérer une dimension de tranche horaire.</span><span class="sxs-lookup"><span data-stu-id="daea0-118">PivotTable reports in Excel include a Page field where you can put a time slice dimension.</span></span> <span data-ttu-id="daea0-119">Office Web Components utilisés par le portail BAM n’incluent pas d’un champ de Page.</span><span class="sxs-lookup"><span data-stu-id="daea0-119">The Office Web Components used by the BAM portal do not include a Page field.</span></span> <span data-ttu-id="daea0-120">Si votre rapport de tableau croisé dynamique Excel utilise le champ Page pour une ou plusieurs dimensions, les données correspondant à ce champ dans le rapport du portail BAM ne s'affichent pas.</span><span class="sxs-lookup"><span data-stu-id="daea0-120">If your Excel PivotTable report uses the Page field for any dimensions, the data for this field is not displayed in your PivotTable report in the BAM portal.</span></span>  
  
-   <span data-ttu-id="daea0-121">Office Web Components affiche les données dans le cadre Contenu du portail BAM.</span><span class="sxs-lookup"><span data-stu-id="daea0-121">The Office Web Components display data in the content frame of the BAM portal.</span></span> <span data-ttu-id="daea0-122">L'espace disponible dans ce frame étant restreint, lorsque vous ajoutez des dimensions à partir de la liste de champs dans la zone des colonnes, il se peut que l'affichage des noms des dimensions dans le tableau croisé dynamique soit effacé, partiellement ou en totalité.</span><span class="sxs-lookup"><span data-stu-id="daea0-122">Because of the space limitations of this frame, adding dimensions from the field list to the columns area can cause the display of the PivotTable to move dimension names partly or wholly out of view.</span></span>  
  
 <span data-ttu-id="daea0-123">Pour plus d’informations sur les tableaux croisés dynamiques, consultez « Terminologie relative aux » à [http://go.microsoft.com/fwlink/?LinkId=55416](http://go.microsoft.com/fwlink/?LinkId=55416).</span><span class="sxs-lookup"><span data-stu-id="daea0-123">For more information about PivotTables, see "PivotTable terminology demystified" at [http://go.microsoft.com/fwlink/?LinkId=55416](http://go.microsoft.com/fwlink/?LinkId=55416).</span></span>  
  
## <a name="chart-view"></a><span data-ttu-id="daea0-124">Vue de graphique</span><span class="sxs-lookup"><span data-stu-id="daea0-124">Chart View</span></span>  
 <span data-ttu-id="daea0-125">La vue de graphique est une zone permettant d'afficher l'agrégation sous forme de graphique.</span><span class="sxs-lookup"><span data-stu-id="daea0-125">The Chart View area displays the aggregation in a graphical manner.</span></span> <span data-ttu-id="daea0-126">Les composants Office Web Components vous permettent de modifier les détails relatifs à une agrégation dans un graphique de façon à ajuster les données d'un rapport en fonction de vos besoins.</span><span class="sxs-lookup"><span data-stu-id="daea0-126">The Office Web Components allow you to manipulate the details of the aggregation through the chart view to adjust the reported data as needed.</span></span> <span data-ttu-id="daea0-127">Lorsque vous procédez à vos ajustements en déplaçant par glisser-déplacer les éléments de données figurant dans la liste des champs du graphique, le rapport de tableau croisé dynamique de l'agrégation est automatiquement mis à jour en conséquence.</span><span class="sxs-lookup"><span data-stu-id="daea0-127">When you adjust the aggregation by dragging and dropping data items from the Chart Field list, the PivotTable report for the aggregation is automatically updated to reflect your changes.</span></span> <span data-ttu-id="daea0-128">Vous pouvez rechercher des données dans le tableau croisé dynamique afin de créer une alerte dans la nouvelle vue d'agrégation.</span><span class="sxs-lookup"><span data-stu-id="daea0-128">You can drill through the PivotTable to create an alert on the new aggregation view.</span></span>  
  
 ![](../core/media/aggregationchartview.gif "AggregationChartView")  
  
## <a name="more"></a><span data-ttu-id="daea0-129">Plus</span><span class="sxs-lookup"><span data-stu-id="daea0-129">More</span></span>  
  
-   [<span data-ttu-id="daea0-130">Comment définir une alerte</span><span class="sxs-lookup"><span data-stu-id="daea0-130">How to Set an Alert</span></span>](../core/how-to-set-an-alert.md)  
  
-   [<span data-ttu-id="daea0-131">Comment afficher les résultats d’une recherche d’activité</span><span class="sxs-lookup"><span data-stu-id="daea0-131">How to View the Results of an Activity Search</span></span>](../core/how-to-view-the-results-of-an-activity-search.md)  
  
-   [<span data-ttu-id="daea0-132">Comment modifier une agrégation</span><span class="sxs-lookup"><span data-stu-id="daea0-132">How to Modify an Aggregation</span></span>](../core/how-to-modify-an-aggregation.md)  
  
## <a name="see-also"></a><span data-ttu-id="daea0-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="daea0-133">See Also</span></span>  
 [<span data-ttu-id="daea0-134">Qu’est une agrégation ?</span><span class="sxs-lookup"><span data-stu-id="daea0-134">What Is an Aggregation?</span></span>](../core/what-is-an-aggregation.md)