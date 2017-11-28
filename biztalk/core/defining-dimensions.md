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
# <a name="defining-dimensions"></a><span data-ttu-id="f5470-102">Définition des dimensions</span><span class="sxs-lookup"><span data-stu-id="f5470-102">Defining Dimensions</span></span>
<span data-ttu-id="f5470-103">Microsoft Excel définit les dimensions comme des catégories permettant d'organiser les données d'une table en niveaux en vue de leur utilisation pour l'analyse.</span><span class="sxs-lookup"><span data-stu-id="f5470-103">Microsoft Excel defines dimensions as categories used to organize data in a table into levels that will be used for analysis.</span></span> <span data-ttu-id="f5470-104">Par exemple, une dimension de données concernant les lieux peut contenir des niveaux de type Ville, Département/Province et Pays/Région.</span><span class="sxs-lookup"><span data-stu-id="f5470-104">For example, a location data dimension might contain levels such as city, state/province, and country/region.</span></span> <span data-ttu-id="f5470-105">Lors de la création de vues BAM à l'aide de l'Assistant correspondant, vous pouvez ajouter au moins une des dimensions suivantes :</span><span class="sxs-lookup"><span data-stu-id="f5470-105">When creating BAM Views in the BAM View wizard, you can add one or more of the following dimension types:</span></span>  
  
-   [<span data-ttu-id="f5470-106">Dimension de progression</span><span class="sxs-lookup"><span data-stu-id="f5470-106">Progress Dimension</span></span>](../core/progress-dimension.md)  
  
-   [<span data-ttu-id="f5470-107">Dimension données</span><span class="sxs-lookup"><span data-stu-id="f5470-107">Data Dimension</span></span>](../core/data-dimension.md)  
  
-   [<span data-ttu-id="f5470-108">Dimension de temps</span><span class="sxs-lookup"><span data-stu-id="f5470-108">Time Dimension</span></span>](../core/time-dimension.md)  
  
-   [<span data-ttu-id="f5470-109">Dimension de plage numérique</span><span class="sxs-lookup"><span data-stu-id="f5470-109">Numeric Range Dimension</span></span>](../core/numeric-range-dimension.md)  
  
 ![](../core/media/bam-olap-cube.gif "bam_olap_cube")  
<span data-ttu-id="f5470-110">Données d'agrégation précalculées</span><span class="sxs-lookup"><span data-stu-id="f5470-110">Pre-calculated Aggregation Data</span></span>  
  
 <span data-ttu-id="f5470-111">De nouvelles dimensions sont ajoutées dans l'Assistant de la vue BAM.</span><span class="sxs-lookup"><span data-stu-id="f5470-111">You add new dimensions in the BAM View wizard.</span></span> <span data-ttu-id="f5470-112">Pour pouvoir ajouter des dimensions, vous devez d'abord créer des Vues Activité d'entreprise à l'aide de l'Assistant.</span><span class="sxs-lookup"><span data-stu-id="f5470-112">Before you can add dimensions, you need to use the wizard to create business activity views.</span></span> <span data-ttu-id="f5470-113">Pour plus d’informations sur l’utilisation de l’Assistant, consultez [définir des activités d’entreprise et les vues dans Excel](../core/defining-business-activities-and-views-in-excel.md).</span><span class="sxs-lookup"><span data-stu-id="f5470-113">For more information about using the wizard, see [Define Business Activities and Views in Excel](../core/defining-business-activities-and-views-in-excel.md).</span></span>  
  
### <a name="to-add-new-dimensions"></a><span data-ttu-id="f5470-114">Pour ajouter de nouvelles dimensions</span><span class="sxs-lookup"><span data-stu-id="f5470-114">To add new dimensions</span></span>  
  
1.  <span data-ttu-id="f5470-115">Dans l’Assistant Vue BAM, cliquez sur **suivant** jusqu'à ce que vous voyiez la **nouvelle vue BAM : Dimensions et l’agrégation des mesures** page.</span><span class="sxs-lookup"><span data-stu-id="f5470-115">In the BAM View wizard, click **Next** until you see the **New BAM View: Aggregation Dimensions and Measures** page.</span></span> <span data-ttu-id="f5470-116">Cliquez sur **de nouvelles Dimensions**.</span><span class="sxs-lookup"><span data-stu-id="f5470-116">Click **New Dimensions**.</span></span>  
  
2.  <span data-ttu-id="f5470-117">Entrez un nom pour la dimension.</span><span class="sxs-lookup"><span data-stu-id="f5470-117">Type a name for the dimension.</span></span>  
  
3.  <span data-ttu-id="f5470-118">Dans la liste déroulante, sélectionnez un type de dimension.</span><span class="sxs-lookup"><span data-stu-id="f5470-118">From the drop-down list, select a dimension type.</span></span>  
  
4.  <span data-ttu-id="f5470-119">Selon le type de dimension que vous avez sélectionné, renseignez les données appropriées, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="f5470-119">Based on the dimension type you selected, fill in the appropriate data, and then click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5470-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f5470-120">See Also</span></span>  
 [<span data-ttu-id="f5470-121">Dimension de progression</span><span class="sxs-lookup"><span data-stu-id="f5470-121">Progress Dimension</span></span>](../core/progress-dimension.md)