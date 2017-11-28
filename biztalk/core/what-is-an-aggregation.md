---
title: "Qu'est-ce qu'une agrégation ? | Microsoft Docs"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- OLAP cubes, BAM
- BAM, aggregations
- BAM, OLAP cubes
- aggregations [BAM], OLAP cubes
- aggregations [BAM], about aggregations
- aggregations [BAM]
ms.assetid: 77d40602-ef56-4a5b-a18f-56ccbff573a4
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: df24dced4d7075e85b8b002bf90b821ce745f91e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="what-is-an-aggregation"></a><span data-ttu-id="88055-103">Qu'est-ce qu'une agrégation ?</span><span class="sxs-lookup"><span data-stu-id="88055-103">What Is an Aggregation?</span></span>
<span data-ttu-id="88055-104">Dans Excel, les agrégations sont des résumés précalculés de données qui améliorent le temps de réponse de requête, les réponses étant prêtes avant que les questions ne soient posées.</span><span class="sxs-lookup"><span data-stu-id="88055-104">Excel defines aggregations as pre-calculated summaries of data that improve query response time by having the answers ready before the questions are asked.</span></span> <span data-ttu-id="88055-105">Par exemple, lorsqu'une table de faits d'un entrepôt de données contient des centaines de milliers de lignes, la réponse à une requête demandant les calendriers d'expédition de deux produits particuliers peut s'avérer être longue si le calcul de la réponse nécessite l'analyse de la table de faits.</span><span class="sxs-lookup"><span data-stu-id="88055-105">For example, when a data warehouse fact table contains hundreds of thousands of rows, a query requesting the shipping schedules for two particular products can take a long time to answer if the fact table has to be scanned to compute the answer.</span></span> <span data-ttu-id="88055-106">En revanche, la réponse peut être presque immédiate si les données récapitulatives fournies en réponse à cette requête ont été précalculées.</span><span class="sxs-lookup"><span data-stu-id="88055-106">However, the response can be almost immediate if the summarization data to answer this query has been pre-calculated.</span></span>  
  
 <span data-ttu-id="88055-107">L'illustration suivante montre un exemple de données d'agrégation précalculées.</span><span class="sxs-lookup"><span data-stu-id="88055-107">The following figure displays an example of pre-calculated aggregation data.</span></span>  
  
 ![](../core/media/bam-olap-cube.gif "bam_olap_cube")  
<span data-ttu-id="88055-108">Cube OLAP BAM</span><span class="sxs-lookup"><span data-stu-id="88055-108">BAM OLAP Cube</span></span>  
  
 <span data-ttu-id="88055-109">La figure ci-dessous récapitule les quantités de chaque produit livrées à des emplacements spécifiques sur une période de deux mois.</span><span class="sxs-lookup"><span data-stu-id="88055-109">The above figure summarizes the numbers of each product, shipped to specific locations over a two-month time period.</span></span> <span data-ttu-id="88055-110">Excel définit généralement ces données comme une mesure.</span><span class="sxs-lookup"><span data-stu-id="88055-110">Excel typically defines this data as measure.</span></span> <span data-ttu-id="88055-111">Les données utilisées pour le filtrage et la catégorisation sont définies dans Excel comme une dimension.</span><span class="sxs-lookup"><span data-stu-id="88055-111">The data used for filtering and categorization, Excel defines as dimension.</span></span>  
  
 <span data-ttu-id="88055-112">Pour plus d'informations sur l'exploration des données multidimensionnelles, consultez la rubrique de l'aide d'Excel consacrée aux tableaux croisés dynamiques.</span><span class="sxs-lookup"><span data-stu-id="88055-112">For the user experience of browsing multidimensional data, see the PivotTable topic in Excel Help.</span></span>  
  
 <span data-ttu-id="88055-113">Vous pouvez créer des agrégations d'activités multidimensionnelles basées sur les données disponibles dans une vue spécifique.</span><span class="sxs-lookup"><span data-stu-id="88055-113">You can create multidimensional activity aggregations based on the data available in a specific view.</span></span> <span data-ttu-id="88055-114">Ces agrégations contiennent des mesures (données à agréger, telles que des montants en euros) et des dimensions (utilisées pour filtrer ou regrouper, telles que État ou Ville).</span><span class="sxs-lookup"><span data-stu-id="88055-114">Those aggregations contain measures (data to aggregate, such as dollar amount) and dimensions (used for filtering or grouping, such as State and City).</span></span>  
  
 <span data-ttu-id="88055-115">Vous pouvez créer des agrégations sous la forme de cubes de traitement analytique en ligne (OLAP), qui représentent un instantané de l'entreprise à un moment précis, ou sous la forme d'agrégations RTA, déterminées par le scénario d'entreprise et que vous visualisez à l'aide de la structure multidimensionnelle en temps réel.</span><span class="sxs-lookup"><span data-stu-id="88055-115">You can create the aggregations in the form of online analytical processing (OLAP) cubes, which represent a snapshot of the business at a specific time, or as real-time aggregations, which the business scenario determines and you see using the multidimensional structure in real time.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="88055-116">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="88055-116">In This Section</span></span>  
  
-   [<span data-ttu-id="88055-117">Agrégations planifiées</span><span class="sxs-lookup"><span data-stu-id="88055-117">Scheduled Aggregations</span></span>](../core/scheduled-aggregations.md)  
  
-   [<span data-ttu-id="88055-118">Agrégations en temps réel</span><span class="sxs-lookup"><span data-stu-id="88055-118">Real-Time Aggregations</span></span>](../core/real-time-aggregations.md)