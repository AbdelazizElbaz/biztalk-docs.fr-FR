---
title: "Comment définir des mesures | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Excel add-in [BAM], creating measures
- aggregations [BAM], measures
- BAM views, measures
ms.assetid: fd3dfe6b-cc63-4306-8aad-a9d2a9af01e8
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e56fea736baaec3f259fc8831a7256e28eaabc9a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-define-measures"></a><span data-ttu-id="585c3-102">Définition des mesures</span><span class="sxs-lookup"><span data-stu-id="585c3-102">How to Define Measures</span></span>
<span data-ttu-id="585c3-103">Une mesure définit la manière dont une activité est calculée.</span><span class="sxs-lookup"><span data-stu-id="585c3-103">A measure defines how an activity is calculated.</span></span> <span data-ttu-id="585c3-104">Lorsque vous créez une vue BAM, vous pouvez définir une mesure pour l'activité figurant dans la vue.</span><span class="sxs-lookup"><span data-stu-id="585c3-104">When you create a BAM view you can define a measure for the activity in the view.</span></span> <span data-ttu-id="585c3-105">Par exemple, pour une activité de bon de commande, vous pouvez calculer le montant total des bons de commande, le nombre de bons de commande, le montant moyen des bons de commande, etc.</span><span class="sxs-lookup"><span data-stu-id="585c3-105">For example, for a purchase order activity, you can calculate the total PO amount, the number of POs, the average PO amount, and so on.</span></span>  
  
 <span data-ttu-id="585c3-106">Les mesures prises en charge par l'analyse BAM sont notamment les suivantes :</span><span class="sxs-lookup"><span data-stu-id="585c3-106">BAM supported measures include:</span></span>  
  
-   <span data-ttu-id="585c3-107">Sum</span><span class="sxs-lookup"><span data-stu-id="585c3-107">Sum</span></span>  
  
-   <span data-ttu-id="585c3-108">Compter</span><span class="sxs-lookup"><span data-stu-id="585c3-108">Count</span></span>  
  
-   <span data-ttu-id="585c3-109">Moyenne</span><span class="sxs-lookup"><span data-stu-id="585c3-109">Average</span></span>  
  
-   <span data-ttu-id="585c3-110">Minimum</span><span class="sxs-lookup"><span data-stu-id="585c3-110">Minimum</span></span>  
  
-   <span data-ttu-id="585c3-111">Maximum</span><span class="sxs-lookup"><span data-stu-id="585c3-111">Maximum</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="585c3-112">Actuellement, le composant RTA (Real-time Aggregation, agrégation en temps réel) de l'analyse BAM ne prend pas en charge les mesures Minimum et Maximum.</span><span class="sxs-lookup"><span data-stu-id="585c3-112">The BAM Real-time Aggregation (RTA) feature doesn't currently support Minimum and Maximum measures.</span></span> <span data-ttu-id="585c3-113">Vous pouvez utiliser ces mesures, mais lorsque vous marquez le tableau croisé dynamique Excel comme une agrégation RTA, les mesures Minimum et Maximum sont ignorées.</span><span class="sxs-lookup"><span data-stu-id="585c3-113">You can use those measures, but when you mark the Excel pivot table as an RTA, Minimum and Maximum are ignored.</span></span>  
  
### <a name="to-add-new-measures"></a><span data-ttu-id="585c3-114">Pour ajouter de nouvelles mesures</span><span class="sxs-lookup"><span data-stu-id="585c3-114">To add new measures</span></span>  
  
1.  <span data-ttu-id="585c3-115">Dans l’Assistant Vue BAM, cliquez sur **suivant** jusqu'à ce que vous voyiez la **nouvelle vue BAM : Dimensions et l’agrégation des mesures** page.</span><span class="sxs-lookup"><span data-stu-id="585c3-115">In the BAM View wizard, click **Next** until you see the **New BAM View: Aggregation Dimensions and Measures** page.</span></span> <span data-ttu-id="585c3-116">Cliquez sur **de nouvelles mesures**.</span><span class="sxs-lookup"><span data-stu-id="585c3-116">Click **New Measures**.</span></span>  
  
2.  <span data-ttu-id="585c3-117">Entrez le nom de la mesure.</span><span class="sxs-lookup"><span data-stu-id="585c3-117">Type a name for your measure.</span></span>  
  
3.  <span data-ttu-id="585c3-118">Dans la liste déroulante, sélectionnez le **élément de Base de données**.</span><span class="sxs-lookup"><span data-stu-id="585c3-118">From the drop-down list, select the **Base data item**.</span></span>  
  
4.  <span data-ttu-id="585c3-119">Cliquez sur le **type d’agrégation** vous souhaitez utiliser.</span><span class="sxs-lookup"><span data-stu-id="585c3-119">Click the **Aggregation type** you want to use.</span></span> <span data-ttu-id="585c3-120">Les choix possibles sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="585c3-120">The choices include:</span></span>  
  
    -   <span data-ttu-id="585c3-121">Sum</span><span class="sxs-lookup"><span data-stu-id="585c3-121">Sum</span></span>  
  
    -   <span data-ttu-id="585c3-122">Compter</span><span class="sxs-lookup"><span data-stu-id="585c3-122">Count</span></span>  
  
    -   <span data-ttu-id="585c3-123">Moyenne</span><span class="sxs-lookup"><span data-stu-id="585c3-123">Average</span></span>  
  
    -   <span data-ttu-id="585c3-124">Minimum (non pris en charge pour les RTA).</span><span class="sxs-lookup"><span data-stu-id="585c3-124">Minimum (not supported for RTAs).</span></span>  
  
    -   <span data-ttu-id="585c3-125">Maximum (non pris en charge pour les RTA)</span><span class="sxs-lookup"><span data-stu-id="585c3-125">Maximum (not supported for RTAs)</span></span>  
  
5.  <span data-ttu-id="585c3-126">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="585c3-126">Click **OK**.</span></span> <span data-ttu-id="585c3-127">Lorsque vous avez terminé l’ajout de dimensions et mesures, cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="585c3-127">When you finish adding dimensions and measures, click **Next**.</span></span>  
  
6.  <span data-ttu-id="585c3-128">Sur le **nouvelle vue BAM : résumé** page, passez en revue les informations relatives à votre nouvelle vue, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="585c3-128">On the **New BAM View: Summary** page, review the information regarding your new view, and then click **Next**.</span></span>  
  
7.  <span data-ttu-id="585c3-129">Cliquez sur **Terminer** pour terminer le **Assistant Vue BAM**.</span><span class="sxs-lookup"><span data-stu-id="585c3-129">Click **Finish** to complete the **BAM View Wizard**.</span></span>  
  
 <span data-ttu-id="585c3-130">Si vous avez ajouté des mesures et des dimensions à la vue BAM, vous pouvez ajouter ces éléments dans le tableau croisé dynamique du classeur Excel.</span><span class="sxs-lookup"><span data-stu-id="585c3-130">If you added measures and dimensions to your BAM view, you can add those items to the PivotTable in the Excel workbook.</span></span> <span data-ttu-id="585c3-131">Pour plus d’informations sur la création d’un tableau croisé dynamique, consultez [comment utiliser le tableau croisé dynamique](../core/how-to-use-the-pivottable.md).</span><span class="sxs-lookup"><span data-stu-id="585c3-131">For more information about creating a PivotTable, see [How to Use the PivotTable](../core/how-to-use-the-pivottable.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="585c3-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="585c3-132">See Also</span></span>  
 [<span data-ttu-id="585c3-133">Définition des Dimensions</span><span class="sxs-lookup"><span data-stu-id="585c3-133">Defining Dimensions</span></span>](../core/defining-dimensions.md)