---
title: "Les agrégations sur le portail BAM Page | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- aggregations [BAM], alerts
- aggregations [BAM], viewing results
- alerts, aggregations
- Aggregations page [BAM portal]
- BAM portal, aggregations
ms.assetid: 6bc1a6f2-9e9a-4db6-aaa1-188ed2f2641f
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a61df22bf5d07bd1b4d955f2baf884459de52998
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="aggregations-on-the-bam-portal-page"></a><span data-ttu-id="e64d2-102">Agrégations dans la page du portail BAM</span><span class="sxs-lookup"><span data-stu-id="e64d2-102">Aggregations on the BAM Portal Page</span></span>
<span data-ttu-id="e64d2-103">Les utilisateurs finaux des activités, les développeurs et les analystes d'entreprise utilisent la page du portail BAM lorsqu'ils ont besoin de présenter des données agrégées, c'est-à-dire, des résumés précalculés d'un ensemble de données communiquant les caractéristiques représentatives de cet ensemble de données.</span><span class="sxs-lookup"><span data-stu-id="e64d2-103">Business end users, developers, and business analysts use the BAM portal page when they need to present aggregated data, which are precalculated summaries of a data set that convey representative characteristics of that data set.</span></span> <span data-ttu-id="e64d2-104">La page d'agrégations du portail BAM vous permet d'afficher des données agrégées sous la forme d'un graphique accompagné d'un rapport de tableau croisé dynamique.</span><span class="sxs-lookup"><span data-stu-id="e64d2-104">The Aggregations page of the BAM portal allows you to display aggregated data in the form of a graphical chart and accompanying PivotTable report.</span></span>  
  
## <a name="the-aggregations-page"></a><span data-ttu-id="e64d2-105">Page Agrégations</span><span class="sxs-lookup"><span data-stu-id="e64d2-105">The Aggregations page</span></span>  
 <span data-ttu-id="e64d2-106">La page Agrégations affiche les résultats d'une activité regroupant des informations sur le fonctionnement du processus ou sur le fonctionnement général.</span><span class="sxs-lookup"><span data-stu-id="e64d2-106">The Aggregations page displays the results of an activity that collectively convey the health of the process or of the overall business.</span></span> <span data-ttu-id="e64d2-107">Par exemple, un utilisateur peut afficher un graphique à secteurs simple, présentant le détail de 1 000 factures reçues en fonction de leur phase de traitement (400 factures toujours en évaluation, 400 rejetées, 100 payées et 100 toujours en attente).</span><span class="sxs-lookup"><span data-stu-id="e64d2-107">For example, a user may want to see a simple pie chart that shows a breakdown of the 1,000 invoices received in terms of what stage of processing has been reached by each invoice (400 still in "evaluation," 400 rejected, 100 paid, and 100 still in "fund allocation").</span></span>  
  
### <a name="creating-alerts-for-aggregations"></a><span data-ttu-id="e64d2-108">Création d'alertes pour les agrégations</span><span class="sxs-lookup"><span data-stu-id="e64d2-108">Creating alerts for aggregations</span></span>  
 <span data-ttu-id="e64d2-109">Vous pouvez utiliser des agrégations comme base de création d'une alerte telle que « Avertissez-moi lorsque le nombre de factures en évaluation est supérieur à 500 ».</span><span class="sxs-lookup"><span data-stu-id="e64d2-109">You can use aggregations as the basis for creating an alert ("Notify me if there are ever more than 500 invoices in the "evaluation" stage of the process).</span></span> <span data-ttu-id="e64d2-110">Pour ce faire, cliquez sur n’importe quelle cellule de tableau croisé dynamique, sélectionnez **définir l’alerte**, ou cliquez sur une cellule et cliquez sur le **définir l’alerte** situé à droite du rapport de tableau croisé dynamique.</span><span class="sxs-lookup"><span data-stu-id="e64d2-110">To do this, you right-click any PivotTable cell and select **Set Alert**, or you click a cell and click the **Set Alert** button to the right of the PivotTable report.</span></span> <span data-ttu-id="e64d2-111">Pour plus d’informations sur la création d’une alerte, consultez [comment définir une alerte](../core/how-to-set-an-alert.md).</span><span class="sxs-lookup"><span data-stu-id="e64d2-111">For more information about creating an alert, see [How to Set an Alert](../core/how-to-set-an-alert.md).</span></span>  
  
### <a name="viewing-individual-results-of-aggregations"></a><span data-ttu-id="e64d2-112">Affichage des résultats spécifiques à une agrégation</span><span class="sxs-lookup"><span data-stu-id="e64d2-112">Viewing individual results of aggregations</span></span>  
 <span data-ttu-id="e64d2-113">Vous pouvez sélectionner n'importe quelle quantité agrégée (ex. : 400 factures en évaluation) et afficher les résultats de l'agrégation de façon individuelle.</span><span class="sxs-lookup"><span data-stu-id="e64d2-113">You can also select any aggregate amount (for example, 400 invoices still in "evaluation") and see the individual results for the aggregation.</span></span> <span data-ttu-id="e64d2-114">Pour accéder à des résultats individuels en cliquant n’importe quelle cellule de tableau croisé dynamique et en sélectionnant **afficher les résultats**.</span><span class="sxs-lookup"><span data-stu-id="e64d2-114">You access the individual results by right-clicking any PivotTable cell and selecting **Show Results**.</span></span> <span data-ttu-id="e64d2-115">Cette opération vous dirige vers la page Recherche d'activité où la recherche est automatiquement définie et les résultats affichés (dans l'exemple mentionné plus haut, un enregistrement par facture, soit 400 enregistrements).</span><span class="sxs-lookup"><span data-stu-id="e64d2-115">In response to this action, you are sent to the Activity Search page, the search itself is automatically constructed, and the results are displayed (in this example, one record for each of the 400 invoices).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e64d2-116">Certains affichages de l'analyse BAM n'ont pas d'agrégation qui leur soit associée. Par conséquent, selon la façon dont la vue a été créée, il se peut qu'aucune information ne soit accessible.</span><span class="sxs-lookup"><span data-stu-id="e64d2-116">Some BAM views do not have aggregations associated with them, and so there may be no information to access depending on how the view was created.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e64d2-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e64d2-117">See Also</span></span>  
 <span data-ttu-id="e64d2-118">[Portail BAM](../core/bam-portal.md) </span><span class="sxs-lookup"><span data-stu-id="e64d2-118">[BAM Portal](../core/bam-portal.md) </span></span>  
 <span data-ttu-id="e64d2-119">[Recherche d’activité sur le portail BAM Page](../core/activity-search-on-the-bam-portal-page.md) </span><span class="sxs-lookup"><span data-stu-id="e64d2-119">[Activity Search on the BAM Portal Page](../core/activity-search-on-the-bam-portal-page.md) </span></span>  
 [<span data-ttu-id="e64d2-120">Alert Manager sur le portail BAM Page</span><span class="sxs-lookup"><span data-stu-id="e64d2-120">Alert Manager on the BAM Portal Page</span></span>](../core/alert-manager-on-the-bam-portal-page.md)