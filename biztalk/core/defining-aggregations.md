---
title: "Définition des agrégations | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- aggregations [BAM], creating
- Excel add-in [BAM], creating aggregations
- aggregations [BAM], Excel add-in
- aggregations [BAM], about aggregations
ms.assetid: d5bf22d5-f491-4b08-a604-c7158e6e282f
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3412615d03fc9a9776d86fddfb062ab343c5aaeb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="defining-aggregations"></a><span data-ttu-id="ae0ac-102">Définition des agrégations</span><span class="sxs-lookup"><span data-stu-id="ae0ac-102">Defining Aggregations</span></span>
<span data-ttu-id="ae0ac-103">Excel définit **agrégations** des résumés précalculés de données qui améliorent les temps de réponse de requête les réponses étant prêtes avant que les questions soient posées.</span><span class="sxs-lookup"><span data-stu-id="ae0ac-103">Excel defines **aggregations** as pre-calculated summaries of data that improve query response time by having the answers ready before the questions are asked.</span></span> <span data-ttu-id="ae0ac-104">Par exemple, lorsqu'une table de faits d'un entrepôt de données contient des centaines de milliers de lignes, la réponse à une requête demandant les calendriers d'expédition de deux produits particuliers peut s'avérer être longue si le calcul de la réponse nécessite l'analyse de la table de faits.</span><span class="sxs-lookup"><span data-stu-id="ae0ac-104">For example, when a data warehouse fact table contains hundreds of thousands of rows, a query requesting the shipping schedules for two particular products can take a long time to answer if the fact table has to be scanned to compute the answer.</span></span> <span data-ttu-id="ae0ac-105">En revanche, la réponse peut être presque immédiate si les données récapitulatives fournies en réponse à cette requête ont été précalculées.</span><span class="sxs-lookup"><span data-stu-id="ae0ac-105">However, the response can be almost immediate if the summarization data to answer this query has been pre-calculated.</span></span>  
  
 <span data-ttu-id="ae0ac-106">L'illustration suivante montre un exemple de données d'agrégation précalculées.</span><span class="sxs-lookup"><span data-stu-id="ae0ac-106">The following figure displays an example of pre-calculated aggregation data.</span></span>  
  
 ![](../core/media/bam-olap-cube.gif "bam_olap_cube")  
<span data-ttu-id="ae0ac-107">Données d'agrégation précalculées</span><span class="sxs-lookup"><span data-stu-id="ae0ac-107">Pre-calculated Aggregation Data</span></span>  
  
 <span data-ttu-id="ae0ac-108">La figure ci-dessous récapitule les quantités de chaque produit livrées à des emplacements spécifiques sur une période de deux mois.</span><span class="sxs-lookup"><span data-stu-id="ae0ac-108">The above figure summarizes the numbers of each product, shipped to specific locations over a two-month time period.</span></span> <span data-ttu-id="ae0ac-109">Excel définit généralement ces données en tant que **mesure**.</span><span class="sxs-lookup"><span data-stu-id="ae0ac-109">Excel typically defines this data as **measure**.</span></span> <span data-ttu-id="ae0ac-110">Les données utilisées pour le filtrage et la catégorisation, Excel définit comme **dimension**.</span><span class="sxs-lookup"><span data-stu-id="ae0ac-110">The data used for filtering and categorization, Excel defines as **dimension**.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ae0ac-111">L'analyse BAM ne prend pas en charge les instances nommées de [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Analysis Services.</span><span class="sxs-lookup"><span data-stu-id="ae0ac-111">BAM does not support using named instances for [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Analysis Services.</span></span>  
  
 <span data-ttu-id="ae0ac-112">L'expérience utilisateur de recherche de données multidimensionnelles figure à la rubrique de l'aide d'Excel consacrée aux tableaux croisés dynamiques.</span><span class="sxs-lookup"><span data-stu-id="ae0ac-112">For the user experience of browsing multidimensional data, see the Pivot table topic in Excel Help.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ae0ac-113">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="ae0ac-113">In This Section</span></span>  
  
-   [<span data-ttu-id="ae0ac-114">Comment définir des mesures</span><span class="sxs-lookup"><span data-stu-id="ae0ac-114">How to Define Measures</span></span>](../core/how-to-define-measures.md)  
  
-   [<span data-ttu-id="ae0ac-115">Définition des Dimensions</span><span class="sxs-lookup"><span data-stu-id="ae0ac-115">Defining Dimensions</span></span>](../core/defining-dimensions.md)  
  
-   [<span data-ttu-id="ae0ac-116">Comment utiliser le tableau croisé dynamique</span><span class="sxs-lookup"><span data-stu-id="ae0ac-116">How to Use the PivotTable</span></span>](../core/how-to-use-the-pivottable.md)  
  
-   [<span data-ttu-id="ae0ac-117">Définition des agrégations en temps réel</span><span class="sxs-lookup"><span data-stu-id="ae0ac-117">Defining Real-Time Aggregations</span></span>](../core/defining-real-time-aggregations.md)  
  
## <a name="see-also"></a><span data-ttu-id="ae0ac-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ae0ac-118">See Also</span></span>  
 [<span data-ttu-id="ae0ac-119">Définition d’une vue BAM</span><span class="sxs-lookup"><span data-stu-id="ae0ac-119">Defining a BAM View</span></span>](../core/defining-a-bam-view.md)