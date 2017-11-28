---
title: "Qu'est-ce qu'une définition BAM ? | Microsoft Docs"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- definitions [BAM], observation models
- definitions [BAM], about BAM definitions
- definitions [BAM]
ms.assetid: 1ba1f45e-85fe-492f-8a2e-98bf3570c633
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6cbc600f66be7167aabb4cf0273cb1c0bda78973
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="what-is-a-bam-definition"></a><span data-ttu-id="0f1fe-103">Qu'est-ce qu'une définition BAM ?</span><span class="sxs-lookup"><span data-stu-id="0f1fe-103">What Is a BAM Definition?</span></span>
<span data-ttu-id="0f1fe-104">Une définition BAM est une représentation XML d'un modèle d'observation de l'analyse BAM, c'est-à-dire une définition de niveau élevé pour un processus d'entreprise que vous souhaitez analyser.</span><span class="sxs-lookup"><span data-stu-id="0f1fe-104">A BAM definition is an XML representation of a BAM observation model, which is a high-level definition a business process that you want to monitor.</span></span> <span data-ttu-id="0f1fe-105">Un modèle d'observation -et, par conséquent, une définition BAM- est constitué des trois éléments principaux suivants : les étapes majeures et les événements de données (l'activité BAM), une description des agrégations de données et la façon dont les informations sont présentées à l'utilisateur (la vue BAM).</span><span class="sxs-lookup"><span data-stu-id="0f1fe-105">The main parts of the observation model, and therefore the BAM definition, are the milestone and data events to collect (the BAM activity); a description of any data aggregations; and how to present the information to users (the BAM view).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0f1fe-106">Vous avez également la possibilité de créer un fichier XML manuellement en fonction du schéma BAM. Cependant, nous vous déconseillons de créer une définition BAM de cette manière car la définition générée n'est pas validée.</span><span class="sxs-lookup"><span data-stu-id="0f1fe-106">You can also manually create an XML file that follows the BAM schema, but this is not a recommended way to create the BAM definition as it does not provide a definition that has been validated.</span></span>  
  
 <span data-ttu-id="0f1fe-107">Les définitions BAM peuvent contenir les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="0f1fe-107">BAM definitions can contain the following items:</span></span>  
  
-   <span data-ttu-id="0f1fe-108">Activités d'entreprise : une définition BAM est valide si elle contient une activité d'entreprise (ou activité BAM).</span><span class="sxs-lookup"><span data-stu-id="0f1fe-108">Business activities - A valid BAM definition must contain a business activity (also referred to as a BAM activity).</span></span> <span data-ttu-id="0f1fe-109">Tous les autres éléments de la définition sont facultatifs.</span><span class="sxs-lookup"><span data-stu-id="0f1fe-109">All other items in the definition are optional.</span></span> <span data-ttu-id="0f1fe-110">Pour plus d’informations sur l’ajout d’une activité d’entreprise à une définition, consultez [la définition d’une activité d’entreprise](../core/how-to-define-a-business-activity.md).</span><span class="sxs-lookup"><span data-stu-id="0f1fe-110">For information about adding a business activity to a definition, see [How to Define a Business Activity](../core/how-to-define-a-business-activity.md).</span></span>  
  
-   <span data-ttu-id="0f1fe-111">Vues : elles définissent l'ensemble des utilisateurs ayant accès aux données définies par l'activité d'entreprise.</span><span class="sxs-lookup"><span data-stu-id="0f1fe-111">Views – Views define the set of users that can access the data defined by the business activity.</span></span> <span data-ttu-id="0f1fe-112">Elles permettent d'afficher des données filtrées ainsi que des agrégations de ces données et de présenter ces données filtrées de différentes manières (dans un graphique croisé dynamique, par exemple).</span><span class="sxs-lookup"><span data-stu-id="0f1fe-112">Views consist of filtered data, aggregations of the filtered data, and ways of presenting the filtered data, such as a PivotChart report.</span></span> <span data-ttu-id="0f1fe-113">L'analyse BAM prend en charge la définition d'une ou de plusieurs vues par activité.</span><span class="sxs-lookup"><span data-stu-id="0f1fe-113">BAM supports the definition of one or more views per activity.</span></span>  
  
     <span data-ttu-id="0f1fe-114">Dans une vue, il est possible de définir les processus d'entreprise suivants :</span><span class="sxs-lookup"><span data-stu-id="0f1fe-114">In a view you can define the following business processes:</span></span>  
  
    -   <span data-ttu-id="0f1fe-115">Attribution d'alias aux données d'entreprise : elle permet d'attribuer des noms conviviaux aux éléments de données.</span><span class="sxs-lookup"><span data-stu-id="0f1fe-115">Aliased business data - Aliasing allows you to apply friendly names to data items.</span></span> <span data-ttu-id="0f1fe-116">Par exemple, le développeur peut définir un élément de données appelé « PNom ».</span><span class="sxs-lookup"><span data-stu-id="0f1fe-116">For example, a developer may define a data item called “LName.”</span></span> <span data-ttu-id="0f1fe-117">De votre côté, vous pouvez créer un alias de sorte que « PNom » s'affiche sous la forme « Prénom » lorsque vous consultez les données actives BAM.</span><span class="sxs-lookup"><span data-stu-id="0f1fe-117">You can create an alias so that the “LName” is displayed as “Last Name” when viewing the BAM live data.</span></span>  <span data-ttu-id="0f1fe-118">Pour plus d’informations sur les alias, consultez [comment afficher les éléments de renommer](../core/how-to-rename-view-items.md).</span><span class="sxs-lookup"><span data-stu-id="0f1fe-118">For more information about aliasing, see [How to Rename View Items](../core/how-to-rename-view-items.md).</span></span>  
  
    -   <span data-ttu-id="0f1fe-119">Durée : période de temps au cours de laquelle l'activité est analysée.</span><span class="sxs-lookup"><span data-stu-id="0f1fe-119">Duration - The time period over which the activity is monitored.</span></span>  
  
    -   <span data-ttu-id="0f1fe-120">Groupes d'étapes majeures : ensembles d'étapes majeures commerciales.</span><span class="sxs-lookup"><span data-stu-id="0f1fe-120">Milestone groups - Sets of business milestones.</span></span> <span data-ttu-id="0f1fe-121">Vous pouvez utiliser un groupe en tant qu'étape majeure commerciale de début ou de fin de la période d'analyse.</span><span class="sxs-lookup"><span data-stu-id="0f1fe-121">You can use a group as either the starting or ending business milestone of a duration.</span></span>  
  
    -   <span data-ttu-id="0f1fe-122">Agrégations : il peut s'agir d'agrégations RTA (real-time aggregations) ou d'agrégations planifiées (également appelées « traitement analytique en ligne » ou OLAP), constituées des éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="0f1fe-122">Aggregations -  These can be either real-time aggregations (RTAs) or scheduled aggregations (also referred to as online analytical processing (OLAP)), and consist of the following items:</span></span>  
  
-   <span data-ttu-id="0f1fe-123">Mesures : ensemble de valeurs numériques dans un cube Analysis Services (OLAP) reposant sur une colonne de la table de faits du cube.</span><span class="sxs-lookup"><span data-stu-id="0f1fe-123">Measures - A set of numeric values in an Analysis Services (OLAP) cube based on a column in the fact table of the cube.</span></span>  
  
-   <span data-ttu-id="0f1fe-124">Dimension de la progression : représente la création d'agrégations en fonction de la progression des activités toujours en cours.</span><span class="sxs-lookup"><span data-stu-id="0f1fe-124">Progress dimension - Represents the creation of aggregations with respect to the progress of activities that are still in process.</span></span>  
  
-   <span data-ttu-id="0f1fe-125">Dimension Données : permet de classer une agrégation selon sa catégorie.</span><span class="sxs-lookup"><span data-stu-id="0f1fe-125">Data dimension - Used to categorize an aggregation.</span></span> <span data-ttu-id="0f1fe-126">Les dimensions de données sont fonction de la valeur des éléments de données existant sous forme de chaîne mise en forme dans l'activité BAM.</span><span class="sxs-lookup"><span data-stu-id="0f1fe-126">Data dimensions are based on the value of string formatted data items in the BAM activity.</span></span>  
  
-   <span data-ttu-id="0f1fe-127">Dimension de temps : permet de créer des agrégations pour les segments de temps indiqués.</span><span class="sxs-lookup"><span data-stu-id="0f1fe-127">Time dimension - Used to create aggregations across defined time segments.</span></span>  
  
-   <span data-ttu-id="0f1fe-128">Dimension de la plage numérique : permet de classer les agrégations par catégories en fonction du nom convivial des plages numériques données.</span><span class="sxs-lookup"><span data-stu-id="0f1fe-128">Numeric range dimension - Used to categorize aggregations based on friendly names of given numeric ranges.</span></span>  
  
 <span data-ttu-id="0f1fe-129">Les définitions BAM peuvent contenir des alertes ayant été paramétrées dans les vues BAM.</span><span class="sxs-lookup"><span data-stu-id="0f1fe-129">BAM definitions can contain alert definitions that are defined in the views.</span></span> <span data-ttu-id="0f1fe-130">Elles peuvent également comprendre des données présentées sous forme de tableaux croisés dynamiques.</span><span class="sxs-lookup"><span data-stu-id="0f1fe-130">BAM definitions can also contain PivotTable layouts.</span></span> <span data-ttu-id="0f1fe-131">Une fois la définition BAM déployée, les rapports de tableau croisé dynamique contiennent les données d'entreprise actives pouvant être visualisées à l'aide du classeur Excel des données actives ou du portail BAM.</span><span class="sxs-lookup"><span data-stu-id="0f1fe-131">Once the BAM definition is deployed, the PivotTable reports containing the live business data that can be viewed using the Excel livedata workbook or through the BAM portal.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0f1fe-132">Les définitions BAM créées à l’aide de la macro complémentaire d’analyse BAM pour Excel ne peut pas contenir d’alertes.</span><span class="sxs-lookup"><span data-stu-id="0f1fe-132">BAM definitions created using the BAM Add-in for Excel cannot contain alerts.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f1fe-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0f1fe-133">See Also</span></span>  
 <span data-ttu-id="0f1fe-134">[Définir des vues et des activités d’entreprise dans Excel](../core/defining-business-activities-and-views-in-excel.md) </span><span class="sxs-lookup"><span data-stu-id="0f1fe-134">[Defining Business Activities and Views in Excel](../core/defining-business-activities-and-views-in-excel.md) </span></span>  
 <span data-ttu-id="0f1fe-135">[Portail BAM](../core/bam-portal.md) </span><span class="sxs-lookup"><span data-stu-id="0f1fe-135">[BAM Portal](../core/bam-portal.md) </span></span>  
 [<span data-ttu-id="0f1fe-136">Infrastructure dynamique BAM</span><span class="sxs-lookup"><span data-stu-id="0f1fe-136">BAM Dynamic Infrastructure</span></span>](../core/bam-dynamic-infrastructure.md)