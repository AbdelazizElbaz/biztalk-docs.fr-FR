---
title: "Modèles de filtre des événements courants | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fc80168b-25bd-4228-b84c-d38bf4e2fe4a
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ef90a4533b8b12929488d3a323dae47976eace0a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="common-event-filter-patterns"></a><span data-ttu-id="f0064-102">Modèles de filtre des événements communs</span><span class="sxs-lookup"><span data-stu-id="f0064-102">Common Event Filter Patterns</span></span>
<span data-ttu-id="f0064-103">Lorsque vous travaillez avec l'intercepteur BAM de Windows Workflow Foundation (WF), il est probable que vous notiez une utilisation fréquente d'un ensemble de modèles de filtre communs dans vos fichiers de configuration de l'intercepteur.</span><span class="sxs-lookup"><span data-stu-id="f0064-103">As you work with the BAM Interceptor for Windows Workflow Foundation (WF), you will likely notice that there are a set of common filter patterns that you will use frequently in your interceptor configuration files.</span></span> <span data-ttu-id="f0064-104">Tandis que certains de ces modèles de filtre sont spécifiques à vos applications et environnements, de nombreux modèles peuvent être utilisés sur des applications et environnements divers.</span><span class="sxs-lookup"><span data-stu-id="f0064-104">While some of these filter patterns will be unique to your applications and environments, many patterns can be used across environments and in diverse applications.</span></span>  
  
 <span data-ttu-id="f0064-105">Cette rubrique rassemble de nombreux modèles de filtre communs utilisés par les fichiers de configuration de l'intercepteur et écrits pour des applications WF.</span><span class="sxs-lookup"><span data-stu-id="f0064-105">This topic collects many of the common filter patterns used by interceptor configuration files written for WF applications.</span></span> <span data-ttu-id="f0064-106">Les modèles sont regroupés par événement de suivi Windows Workflow Foundation :</span><span class="sxs-lookup"><span data-stu-id="f0064-106">Patterns are grouped by Windows Workflow Foundation tracking event:</span></span>  
  
-   <span data-ttu-id="f0064-107">Événements d'état d'activité</span><span class="sxs-lookup"><span data-stu-id="f0064-107">Activity status events</span></span>  
  
-   <span data-ttu-id="f0064-108">Événements d'état de workflow</span><span class="sxs-lookup"><span data-stu-id="f0064-108">Workflow status events</span></span>  
  
-   <span data-ttu-id="f0064-109">Événements utilisateur</span><span class="sxs-lookup"><span data-stu-id="f0064-109">User events</span></span>  
  
 <span data-ttu-id="f0064-110">Chaque modèle peut être copié dans votre fichier de configuration de l'intercepteur et adapté à votre application.</span><span class="sxs-lookup"><span data-stu-id="f0064-110">Each pattern can be copied into your interceptor configuration file and modified to suit your application.</span></span>  
  
## <a name="activity-status-event-filter-patterns"></a><span data-ttu-id="f0064-111">Modèles de filtre des événements d'état d'activité</span><span class="sxs-lookup"><span data-stu-id="f0064-111">Activity Status Event Filter Patterns</span></span>  
 <span data-ttu-id="f0064-112">Les activités sont les blocs de construction fondamentaux des workflows.</span><span class="sxs-lookup"><span data-stu-id="f0064-112">Activities are the fundamental building blocks of workflows.</span></span> <span data-ttu-id="f0064-113">Un workflow est un ensemble d'activités qui sont organisées hiérarchiquement dans une structure arborescente.</span><span class="sxs-lookup"><span data-stu-id="f0064-113">A workflow is a set of activities that are organized hierarchically in a tree structure.</span></span> <span data-ttu-id="f0064-114">Une activité représente une action dans un workflow.</span><span class="sxs-lookup"><span data-stu-id="f0064-114">An activity represents an action in a workflow.</span></span> <span data-ttu-id="f0064-115">Il peut s'agir d'une action simple, telle qu'un délai, ou d'une activité composite comprenant plusieurs activités enfants.</span><span class="sxs-lookup"><span data-stu-id="f0064-115">It can be a simple action such as a delay, or it can be a composite activity that consists of several child activities.</span></span>  
  
 <span data-ttu-id="f0064-116">Les filtres de cette section filtrent les activités et utilisent une ou plusieurs opérations personnalisées suivantes pour l'intercepteur WF BAM :</span><span class="sxs-lookup"><span data-stu-id="f0064-116">The filters in this section filter activities and use one or more of the following BAM Interceptor for WF custom operations:</span></span>  
  
-   <span data-ttu-id="f0064-117">GetActivityName</span><span class="sxs-lookup"><span data-stu-id="f0064-117">GetActivityName</span></span>  
  
-   <span data-ttu-id="f0064-118">GetActivityEvent</span><span class="sxs-lookup"><span data-stu-id="f0064-118">GetActivityEvent</span></span>  
  
-   <span data-ttu-id="f0064-119">GetActivityType</span><span class="sxs-lookup"><span data-stu-id="f0064-119">GetActivityType</span></span>  
  
-   <span data-ttu-id="f0064-120">GetActivityProperty</span><span class="sxs-lookup"><span data-stu-id="f0064-120">GetActivityProperty</span></span>  
  
-   <span data-ttu-id="f0064-121">GetWorkflowProperty</span><span class="sxs-lookup"><span data-stu-id="f0064-121">GetWorkflowProperty</span></span>  
  
-   <span data-ttu-id="f0064-122">GetContextProperty</span><span class="sxs-lookup"><span data-stu-id="f0064-122">GetContextProperty</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f0064-123">Si vous n'utilisez pas l'opération GetActivityEvent dans votre filtre, celui-ci recherche uniquement les événements d'activité fermée.</span><span class="sxs-lookup"><span data-stu-id="f0064-123">If you do not use the GetActivityEvent operation in your filter, your filter will look for Closed activity events only.</span></span>  
  
### <a name="filter-by-activity-name-closed-activity"></a><span data-ttu-id="f0064-124">Filtre par nom d'activité (activité fermée)</span><span class="sxs-lookup"><span data-stu-id="f0064-124">Filter by Activity Name (Closed Activity)</span></span>  
 <span data-ttu-id="f0064-125">Vous devez fréquemment filtrer les événements d'activité fermée par nom d'activité.</span><span class="sxs-lookup"><span data-stu-id="f0064-125">You will frequently need to filter for closed activity events by activity name.</span></span> <span data-ttu-id="f0064-126">Cela est utile lorsque vous devez capturer des données d'une activité spécifique, telle que la réception d'un fichier ou l'écriture de données dans une base de données.</span><span class="sxs-lookup"><span data-stu-id="f0064-126">This is useful when you need to capture data from a specific activity such as receiving a file or writing data to a database.</span></span>  
  
 <span data-ttu-id="f0064-127">Le fragment suivant filtre une activité fermée nommée « MyActivity ».</span><span class="sxs-lookup"><span data-stu-id="f0064-127">The fragment below filters for a closed activity named "MyActivity".</span></span>  
  
```  
<ic:Filter>  
  <ic:Expression>  
    <wf:Operation Name="GetActivityName" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>MyActivity</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
  </ic:Expression>  
</ic:Filter>  
```  
  
### <a name="filter-by-activity-type-closed-activity-event"></a><span data-ttu-id="f0064-128">Filtre par type d'activité (événement d'activité fermée)</span><span class="sxs-lookup"><span data-stu-id="f0064-128">Filter by Activity Type (Closed Activity Event)</span></span>  
 <span data-ttu-id="f0064-129">Vous pouvez également filtrer une activité par type plutôt que par nom.</span><span class="sxs-lookup"><span data-stu-id="f0064-129">There will be times when you want to filter an activity by type rather than name.</span></span> <span data-ttu-id="f0064-130">Par exemple, vous pouvez enregistrer un nom d'activité et un horodatage pour toutes les activités d'un workflow.</span><span class="sxs-lookup"><span data-stu-id="f0064-130">For example, you may want to save activity name and a date/time stamp for all activities in a workflow.</span></span> <span data-ttu-id="f0064-131">Pour ce faire, utilisez l'opération `GetActivityType`.</span><span class="sxs-lookup"><span data-stu-id="f0064-131">To accomplish this, you use the `GetActivityType` operation.</span></span> <span data-ttu-id="f0064-132">`GetActivityType` compare un type fourni avec le type de base et tous les types dérivés pour identifier une correspondance.</span><span class="sxs-lookup"><span data-stu-id="f0064-132">`GetActivityType` compares a supplied type against the base type and all derived types to determine a match.</span></span> <span data-ttu-id="f0064-133">La comparaison par rapport à `System.Workflow.ComponentModel.Activity` correspond dans la mesure où toutes les activités de workflow doivent en dériver.</span><span class="sxs-lookup"><span data-stu-id="f0064-133">Comparing against `System.Workflow.ComponentModel.Activity` will match since all workflow activities must derive from it.</span></span>  
  
```  
<ic:Filter>  
  <ic:Expression>  
    <wf:Operation Name="GetActivityType" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>System.Workflow.ComponentModel.Activity, System.Workflow.ComponentModel, Version=3.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
  </ic:Expression>  
</ic:Filter>  
```  
  
### <a name="filter-by-activity-event-any-activity-type"></a><span data-ttu-id="f0064-134">Filtre par événement d'activité (tout type d'activité)</span><span class="sxs-lookup"><span data-stu-id="f0064-134">Filter by Activity Event (Any Activity Type)</span></span>  
 <span data-ttu-id="f0064-135">Ce filtre utilise l'opération GetActivityEvent pour rechercher les activités fermées.</span><span class="sxs-lookup"><span data-stu-id="f0064-135">This filter uses the GetActivityEvent operation to find closed activities.</span></span> <span data-ttu-id="f0064-136">Il permet de capturer des informations sur tous les événements fermés (par rapport à un événement spécifique par nom ou type).</span><span class="sxs-lookup"><span data-stu-id="f0064-136">It is useful for capturing information about all closed events (versus a specific event by name or type).</span></span>  
  
```  
<ic:Filter>  
  <ic:Expression>  
    <wf:Operation Name="GetActivityEvent" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>Closed</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
  </ic:Expression>  
</ic:Filter>  
```  
  
### <a name="filter-by-activity-name-and-type-closed-activity-event"></a><span data-ttu-id="f0064-137">Filtre par nom et type d'activité (événement d'activité fermée)</span><span class="sxs-lookup"><span data-stu-id="f0064-137">Filter by Activity Name and Type (Closed Activity Event)</span></span>  
 <span data-ttu-id="f0064-138">Vous pouvez filtrer les activités par nom d'activité et type d'activité si vous voulez spécifier le type exact d'activité (architecture de processeur incluse) à rechercher.</span><span class="sxs-lookup"><span data-stu-id="f0064-138">You may choose to filter activities by activity name and activity type if you want to specify the exact type of activity (including processor architecture) that you are interested in finding.</span></span> <span data-ttu-id="f0064-139">L'exemple suivant recherche « MyActivity » dérivant de `System.Workflow.ComponentModel.Activity`. Vous pouvez le modifier en un type dérivé pour le rendre plus restrictif.</span><span class="sxs-lookup"><span data-stu-id="f0064-139">The sample below looks for "MyActivity" deriving from `System.Workflow.ComponentModel.Activity`; you can change this to a derived type to make it more restrictive.</span></span>  
  
```  
<ic:Filter>  
  <ic:Expression>  
    <wf:Operation Name="GetActivityName" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>MyActivity</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <wf:Operation Name="GetActivityType" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>System.Workflow.ComponentModel.Activity, System.Workflow.ComponentModel, Version=3.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
<ic:Operation Name="And" />  
  </ic:Expression>  
</ic:Filter>  
```  
  
### <a name="filter-by-activity-name-and-event-any-activity-type"></a><span data-ttu-id="f0064-140">Filtre par nom et événement d'activité (tout type d'activité)</span><span class="sxs-lookup"><span data-stu-id="f0064-140">Filter by Activity Name and Event (Any Activity Type)</span></span>  
 <span data-ttu-id="f0064-141">Cette expression filtre par nom d'activité et événement d'activité.</span><span class="sxs-lookup"><span data-stu-id="f0064-141">This expression filters based on activity name and activity event.</span></span> <span data-ttu-id="f0064-142">Cela permet de capturer des informations relatives à une activité ou un événement spécifique ou de capturer des données de plusieurs événements d'une activité donnée.</span><span class="sxs-lookup"><span data-stu-id="f0064-142">This is useful when you want to capture information for a specific activity and event or when capturing data from more than one activity event for a given activity.</span></span> <span data-ttu-id="f0064-143">Par exemple, vous pouvez rechercher deux éléments OnEvent différents, l'un pour MyActivity lorsqu'il est en cours d'exécution et l'autre lorsqu'il est fermé, comme suit :</span><span class="sxs-lookup"><span data-stu-id="f0064-143">For example, you may want two different OnEvent elements, one for MyActivity when it is Executing and one for when it is Closed as shown below.</span></span>  
  
```  
<ic:Filter>  
  <ic:Expression>  
    <wf:Operation Name="GetActivityName" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>MyActivity</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <wf:Operation Name="GetActivityEvent" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>Closed</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <ic:Operation Name="And" />  
  </ic:Expression>  
</ic:Filter>  
```  
  
### <a name="filter-by-activity-type-and-event"></a><span data-ttu-id="f0064-144">Filtre par type et événement d'activité</span><span class="sxs-lookup"><span data-stu-id="f0064-144">Filter by Activity Type and Event</span></span>  
 <span data-ttu-id="f0064-145">Ce filtre permet de capturer des informations sur toutes les activités qui dérivent d'un type spécifique au cours d'un événement d'activité unique.</span><span class="sxs-lookup"><span data-stu-id="f0064-145">This filter is useful for capturing information about all activities that derive from a specific type during a single activity event.</span></span> <span data-ttu-id="f0064-146">Par exemple, vous pouvez suivre un ID de bon de commande et un horodatage d'un bon de commande lorsqu'il transite par un workflow.</span><span class="sxs-lookup"><span data-stu-id="f0064-146">For example, you may be interested in tracking a purchase order ID and date/time stamp from a purchase order as it flows through a workflow.</span></span> <span data-ttu-id="f0064-147">Pour ce faire, utilisez les opérations `GetActivityEvent` et `GetActivityType`.</span><span class="sxs-lookup"><span data-stu-id="f0064-147">To accomplish this, you use the `GetActivityEvent` and the `GetActivityType` operations.</span></span> <span data-ttu-id="f0064-148">`GetActivityType` compare un type fourni avec le type de base et tous les types dérivés pour identifier une correspondance.</span><span class="sxs-lookup"><span data-stu-id="f0064-148">`GetActivityType` compares a supplied type against the base type and all derived types to determine a match.</span></span> <span data-ttu-id="f0064-149">La comparaison par rapport à `System.Workflow.ComponentModel.Activity` correspond dans la mesure où toutes les activités de workflow doivent en dériver.</span><span class="sxs-lookup"><span data-stu-id="f0064-149">Comparing against `System.Workflow.ComponentModel.Activity` will match since all workflow activities must derive from it.</span></span>  
  
```  
<ic:Filter>  
  <ic:Expression>  
    <wf:Operation Name="GetActivityEvent" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>Closed</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <wf:Operation Name="GetActivityType" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>System.Workflow.ComponentModel.Activity, System.Workflow.ComponentModel, Version=3.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <ic:Operation Name="And" />  
  </ic:Expression>  
</ic:Filter>  
```  
  
### <a name="filter-by-activity-name-type-and-event"></a><span data-ttu-id="f0064-150">Filtre par nom, type et événement d'activité</span><span class="sxs-lookup"><span data-stu-id="f0064-150">Filter by Activity Name, Type, and Event</span></span>  
 <span data-ttu-id="f0064-151">Filtrer une activité par nom, type et événement peut être utile pour mieux qualifier l'activité à suivre.</span><span class="sxs-lookup"><span data-stu-id="f0064-151">Filtering an activity by name, type and event can be useful when you want to better qualify the activity you are interested in tracking.</span></span> <span data-ttu-id="f0064-152">Par exemple, le filtre suivant recherche l'activité fermée « MyActivity » dont le type est égal à ou dérive de `System.Workflow.ComponentModel.Activity`.</span><span class="sxs-lookup"><span data-stu-id="f0064-152">For example, the filter below looks for the closed activity "MyActivity" that has a type that is equal to or derives from `System.Workflow.ComponentModel.Activity`.</span></span>  
  
```  
<ic:Filter>  
  <ic:Expression>  
    <wf:Operation Name="GetActivityName" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>MyActivity</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <wf:Operation Name="GetActivityEvent" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>Closed</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <ic:Operation Name="And" />  
    <wf:Operation Name="GetActivityType" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>System.Workflow.ComponentModel.Activity, System.Workflow.ComponentModel, Version=3.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <ic:Operation Name="And" />  
  </ic:Expression>  
</ic:Filter>  
```  
  
## <a name="workflow-status-event-filter-patterns"></a><span data-ttu-id="f0064-153">Modèles de filtre des événements d'état de workflow</span><span class="sxs-lookup"><span data-stu-id="f0064-153">Workflow Status Event Filter Patterns</span></span>  
 <span data-ttu-id="f0064-154">Les filtres de cette section filtrent les événements de workflow et utilisent une ou plusieurs opérations personnalisées suivantes pour l'intercepteur WF BAM :</span><span class="sxs-lookup"><span data-stu-id="f0064-154">The filters in this section filter workflow events and use one or more of the following BAM Interceptor for WF custom operations:</span></span>  
  
-   <span data-ttu-id="f0064-155">GetWorkflowEvent</span><span class="sxs-lookup"><span data-stu-id="f0064-155">GetWorkflowEvent</span></span>  
  
-   <span data-ttu-id="f0064-156">GetContextProperty</span><span class="sxs-lookup"><span data-stu-id="f0064-156">GetContextProperty</span></span>  
  
### <a name="filter-by-workflow-event"></a><span data-ttu-id="f0064-157">Filtre par événement de workflow</span><span class="sxs-lookup"><span data-stu-id="f0064-157">Filter by Workflow Event</span></span>  
 <span data-ttu-id="f0064-158">Cette expression filtre par événement de workflow.</span><span class="sxs-lookup"><span data-stu-id="f0064-158">This expression filters by workflow event.</span></span>  
  
```  
<ic:Filter>  
  <ic:Expression>  
    <wf:Operation Name="GetWorkflowEvent" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>Created</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
  </ic:Expression>  
</ic:Filter>  
```  
  
## <a name="user-event-filter-patterns"></a><span data-ttu-id="f0064-159">Modèles de filtre des événements utilisateur</span><span class="sxs-lookup"><span data-stu-id="f0064-159">User Event Filter Patterns</span></span>  
 <span data-ttu-id="f0064-160">Si votre application suit les informations personnalisées par le biais de la méthode TrackData, vous pouvez filtrer en fonction des caractéristiques des données à l'aide d'une ou de plusieurs opérations de données utilisateur personnalisées suivantes pour l'intercepteur WF BAM :</span><span class="sxs-lookup"><span data-stu-id="f0064-160">If your application tracks custom information using the TrackData method, you can filter based on the characteristics of the data using one or more of the following BAM Interceptor for WF custom user data operations:</span></span>  
  
-   <span data-ttu-id="f0064-161">GetUserDataType</span><span class="sxs-lookup"><span data-stu-id="f0064-161">GetUserDataType</span></span>  
  
-   <span data-ttu-id="f0064-162">GetUserKey</span><span class="sxs-lookup"><span data-stu-id="f0064-162">GetUserKey</span></span>  
  
-   <span data-ttu-id="f0064-163">GetUserData</span><span class="sxs-lookup"><span data-stu-id="f0064-163">GetUserData</span></span>  
  
 <span data-ttu-id="f0064-164">Le filtre peut combiner ces opérations avec les opérations suivantes pour créer une expression plus complexe :</span><span class="sxs-lookup"><span data-stu-id="f0064-164">The filter can combine these operations with the following to create a more complex expression:</span></span>  
  
-   <span data-ttu-id="f0064-165">GetActivityName</span><span class="sxs-lookup"><span data-stu-id="f0064-165">GetActivityName</span></span>  
  
-   <span data-ttu-id="f0064-166">GetActivityType</span><span class="sxs-lookup"><span data-stu-id="f0064-166">GetActivityType</span></span>  
  
-   <span data-ttu-id="f0064-167">GetActivityProperty</span><span class="sxs-lookup"><span data-stu-id="f0064-167">GetActivityProperty</span></span>  
  
-   <span data-ttu-id="f0064-168">GetWorkflowProperty</span><span class="sxs-lookup"><span data-stu-id="f0064-168">GetWorkflowProperty</span></span>  
  
-   <span data-ttu-id="f0064-169">GetContextProperty</span><span class="sxs-lookup"><span data-stu-id="f0064-169">GetContextProperty</span></span>  
  
 <span data-ttu-id="f0064-170">Si votre filtre n'inclut pas au moins une opération de données utilisateur, votre filtre n'est pas un filtre d'événements utilisateur et l'OnEvent associé génère une erreur (si une opération utilisateur apparaît dans une expression de mise à jour correspondante) ou est identifié comme un trackpoint d'activité et non d'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="f0064-170">If your filter does not include at least one user data operation, your filter will not be a user event filter and the enclosing OnEvent will cause an error (if a user operation appears in a corresponding update expression) or will be identified as an activity track point and not a user track point.</span></span>  
  
### <a name="filter-by-activity-name-and-user-data-type"></a><span data-ttu-id="f0064-171">Filtre par nom d'activité et type de données utilisateur</span><span class="sxs-lookup"><span data-stu-id="f0064-171">Filter by Activity Name and User Data Type</span></span>  
 <span data-ttu-id="f0064-172">Fréquemment, vous pouvez identifier un événement par le nom d'activité et le type de données utilisateur.</span><span class="sxs-lookup"><span data-stu-id="f0064-172">Frequently you can identify an event by activity name and user data type.</span></span> <span data-ttu-id="f0064-173">L'expression suivante filtre une activité nommée « MyActivity » et un type de données utilisateur qui dérive de `System.Object`.</span><span class="sxs-lookup"><span data-stu-id="f0064-173">The following expression filters for an activity named "MyActivity" and a user data type that derives from `System.Object`.</span></span>  
  
```  
<ic:Filter>  
  <ic:Expression>  
    <wf:Operation Name="GetActivityName" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>MyActivity</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <wf:Operation Name="GetUserDataType" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>System.Object</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <ic:Operation Name="And" />  
  </ic:Expression>  
</ic:Filter>  
```  
  
### <a name="filter-by-activity-type-and-user-data-type"></a><span data-ttu-id="f0064-174">Filtre par type d'activité et type de données utilisateur</span><span class="sxs-lookup"><span data-stu-id="f0064-174">Filter by Activity Type and User Data Type</span></span>  
 <span data-ttu-id="f0064-175">Vous pouvez filtrer par type d'activité et type de données utilisateur.</span><span class="sxs-lookup"><span data-stu-id="f0064-175">You can filter based on activity type and user data type.</span></span> <span data-ttu-id="f0064-176">Cela vous permet de filtrer des événements en fonction du type dont ils dérivent car `GetActivityType` et `GetUserDataType` effectuent une comparaison par rapport au type spécifié et à tous les types dérivés.</span><span class="sxs-lookup"><span data-stu-id="f0064-176">This grants you the latitude to filter events based on the type the derive from because both `GetActivityType` and `GetUserDataType` compare against the type specified and all derived types.</span></span>  
  
```  
<ic:Filter>  
  <ic:Expression>  
    <wf:Operation Name="GetActivityType" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>System.Workflow.ComponentModel.Activity, System.Workflow.ComponentModel, Version=3.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <wf:Operation Name="GetUserDataType" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>System.Object</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <ic:Operation Name="And" />  
  </ic:Expression>  
</ic:Filter>  
```  
  
### <a name="filter-by-activity-name-activity-type-and-user-data-type"></a><span data-ttu-id="f0064-177">Filtre par nom d'activité, type d'activité et type de données utilisateur</span><span class="sxs-lookup"><span data-stu-id="f0064-177">Filter by Activity Name, Activity Type, and User Data Type</span></span>  
 <span data-ttu-id="f0064-178">Ce filtre limite davantage le modèle de filtre du type d'activité et du type de données utilisateur en incluant le nom d'activité.</span><span class="sxs-lookup"><span data-stu-id="f0064-178">This filter further restricts the activity type and user data type filter pattern by including activity name.</span></span>  
  
```  
<ic:Filter>  
  <ic:Expression>  
    <wf:Operation Name="GetActivityType" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>System.Workflow.ComponentModel.Activity, System.Workflow.ComponentModel, Version=3.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <wf:Operation Name="GetActivityName" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>MyActivity</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <ic:Operation Name="And" />  
    <wf:Operation Name="GetUserDataType" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>System.Object</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <ic:Operation Name="And" />  
  </ic:Expression>  
</ic:Filter>  
```  
  
### <a name="filter-by-activity-name-and-user-key"></a><span data-ttu-id="f0064-179">Filtre par nom d'activité et clé utilisateur</span><span class="sxs-lookup"><span data-stu-id="f0064-179">Filter by Activity Name and User Key</span></span>  
 <span data-ttu-id="f0064-180">Si votre application a une activité qui appelle `TrackData` avec une clé déterminée au moment de l'exécution, vous pouvez filtrer par nom d'activité et clé utilisateur.</span><span class="sxs-lookup"><span data-stu-id="f0064-180">If your application has an activity that calls `TrackData` with a key determined at run time, you may want to filter by activity name and user key.</span></span> <span data-ttu-id="f0064-181">Cela vous permet de déclencher un `OnEvent` basé sur une valeur de clé spécifique.</span><span class="sxs-lookup"><span data-stu-id="f0064-181">This will enable you to trigger an `OnEvent` based on a specific key value.</span></span> <span data-ttu-id="f0064-182">Par exemple, votre application peut définir plusieurs clés et sélectionner dynamiquement l'une d'elles au sein d'une activité.</span><span class="sxs-lookup"><span data-stu-id="f0064-182">For example, your application might define multiple keys and dynamically select one within an activity.</span></span>  
  
 <span data-ttu-id="f0064-183">L'expression suivante filtre « MyActivity » contenant une clé utilisateur nommée « ItemKey ».</span><span class="sxs-lookup"><span data-stu-id="f0064-183">The expression below filters for "MyActivity" containing a user key named "ItemKey".</span></span>  
  
```  
<ic:Filter>  
  <ic:Expression>  
    <wf:Operation Name="GetActivityName" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>MyActivity</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <wf:Operation Name="GetUserKey" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>ItemKey</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <ic:Operation Name="And" />  
  </ic:Expression>  
</ic:Filter>  
```  
  
### <a name="filter-by-activity-type-and-user-key"></a><span data-ttu-id="f0064-184">Filtre par type d'activité et clé utilisateur</span><span class="sxs-lookup"><span data-stu-id="f0064-184">Filter by Activity Type and User Key</span></span>  
 <span data-ttu-id="f0064-185">Si votre application contient plusieurs activités qui appellent `TrackData` avec une clé déterminée au moment de l'exécution, vous pouvez filtrer par nom d'activité et clé utilisateur.</span><span class="sxs-lookup"><span data-stu-id="f0064-185">If your application contain multiple activities that call `TrackData` with a key determined at run time, you may want to filter by activity name and user key.</span></span> <span data-ttu-id="f0064-186">Cela vous permet de déclencher un `OnEvent` basé sur une valeur de clé spécifique.</span><span class="sxs-lookup"><span data-stu-id="f0064-186">This will enable you to trigger an `OnEvent` based on a specific key value.</span></span> <span data-ttu-id="f0064-187">Par exemple, votre application peut définir plusieurs clés et sélectionner dynamiquement l'une d'elles au sein d'une activité.</span><span class="sxs-lookup"><span data-stu-id="f0064-187">For example, your application might define multiple keys and dynamically select one within an activity.</span></span>  
  
 <span data-ttu-id="f0064-188">L'expression suivante filtre toute activité dérivant de `System.Workflow.ComponentModel.Activity` contenant une clé utilisateur nommée « ItemKey ».</span><span class="sxs-lookup"><span data-stu-id="f0064-188">The expression below filters for any activity deriving from `System.Workflow.ComponentModel.Activity` containing a user key named "ItemKey".</span></span>  
  
```  
<ic:Filter>  
  <ic:Expression>  
    <wf:Operation Name="GetActivityType" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>System.Workflow.ComponentModel.Activity, System.Workflow.ComponentModel, Version=3.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <wf:Operation Name="GetUserKey" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>ItemKey</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <ic:Operation Name="And" />  
  </ic:Expression>  
</ic:Filter>  
```  
  
### <a name="filter-by-activity-name-activity-type-and-user-key"></a><span data-ttu-id="f0064-189">Filtre par nom d'activité, type d'activité et clé utilisateur</span><span class="sxs-lookup"><span data-stu-id="f0064-189">Filter by Activity Name, Activity Type, and User Key</span></span>  
 <span data-ttu-id="f0064-190">Ce modèle de filtre affine davantage le modèle de filtre du type d'activité et de la clé utilisateur en incluant le nom d'activité.</span><span class="sxs-lookup"><span data-stu-id="f0064-190">This filter pattern further refines the activity type and user key filter pattern by including the activity name in the filter.</span></span>  
  
```  
<ic:Filter>  
  <ic:Expression>  
    <wf:Operation Name="GetActivityType" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>System.Workflow.ComponentModel.Activity, System.Workflow.ComponentModel, Version=3.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <wf:Operation Name="GetActivityName" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>MyActivity</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <ic:Operation Name="And" />  
    <wf:Operation Name="GetUserKey" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>key</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <ic:Operation Name="And" />  
  </ic:Expression>  
</ic:Filter>  
```  
  
### <a name="filter-by-activity-name-user-data-type-and-user-key"></a><span data-ttu-id="f0064-191">Filtre par nom d'activité, type de données utilisateur et clé utilisateur</span><span class="sxs-lookup"><span data-stu-id="f0064-191">Filter by Activity Name, User Data Type, and User Key</span></span>  
 <span data-ttu-id="f0064-192">Ce filtre permet de limiter votre filtre à une activité nommée avec une clé utilisateur spécifique et dérivant d'un type de données spécifique.</span><span class="sxs-lookup"><span data-stu-id="f0064-192">This filter is useful when you want to restrict your filter to a named activity with a specific user key and deriving from a specific data type.</span></span> <span data-ttu-id="f0064-193">Par exemple, votre activité peut appeler TrackData à l'aide de la clé « Item » et une valeur de données de chaîne ou d'entier selon le type d'élément.</span><span class="sxs-lookup"><span data-stu-id="f0064-193">For example, your activity may call TrackData using the key "Item" and a data value of string or integer depending upon the item type.</span></span>  
  
```  
<ic:Filter>  
  <ic:Expression>  
    <wf:Operation Name="GetActivityName" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>MyActivity</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <wf:Operation Name="GetUserDataType" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>System.Object</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <ic:Operation Name="And" />  
    <wf:Operation Name="GetUserKey" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>key</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <ic:Operation Name="And" />  
  </ic:Expression>  
</ic:Filter>  
```  
  
### <a name="filter-by-activity-type-user-data-type-and-user-key"></a><span data-ttu-id="f0064-194">Filtre par type d'activité, type de données utilisateur et clé utilisateur</span><span class="sxs-lookup"><span data-stu-id="f0064-194">Filter by Activity Type, User Data Type, and User Key</span></span>  
 <span data-ttu-id="f0064-195">Ce filtre permet de limiter votre filtre à un type d'activité avec une clé utilisateur spécifique et dérivant d'un type de données spécifique.</span><span class="sxs-lookup"><span data-stu-id="f0064-195">This filter is useful when you want to restrict your filter to an activity type with a specific user key and deriving from a specific data type.</span></span> <span data-ttu-id="f0064-196">Il peut être plus ou moins restrictif que l'utilisation du nom d'activité, du type de données utilisateur et de la clé utilisateur en fonction du type utilisé.</span><span class="sxs-lookup"><span data-stu-id="f0064-196">It can be more restrictive or less restrictive than using activity name, user data type, and user key based on the type used.</span></span> <span data-ttu-id="f0064-197">Si vous spécifiez le type le plus dérivé, il peut être plus restrictif tandis que si vous spécifiez le type de base racine, il peut être moins restrictif.</span><span class="sxs-lookup"><span data-stu-id="f0064-197">If you specify the most-derived type, it could be more restrictive; if you specify the root base type, it could be less restrictive.</span></span>  
  
```  
<ic:Filter>  
  <ic:Expression>  
    <wf:Operation Name="GetActivityType" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>System.Workflow.ComponentModel.Activity, System.Workflow.ComponentModel, Version=3.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <wf:Operation Name="GetUserDataType" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>System.Object</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <ic:Operation Name="And" />  
    <wf:Operation Name="GetUserKey" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>key</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <ic:Operation Name="And" />  
  </ic:Expression>  
</ic:Filter>  
```  
  
### <a name="filter-by-activity-name-activity-type-user-data-type-and-user-key"></a><span data-ttu-id="f0064-198">Filtre par nom d'activité, type d'activité, type de données utilisateur et clé utilisateur</span><span class="sxs-lookup"><span data-stu-id="f0064-198">Filter by Activity Name, Activity Type, User Data Type, and User Key</span></span>  
 <span data-ttu-id="f0064-199">Ce filtre limite davantage le modèle de filtre du type d'activité, du type de données utilisateur et de la clé utilisateur en incluant le nom d'activité.</span><span class="sxs-lookup"><span data-stu-id="f0064-199">This filter further restricts the activity type, user data type, and user key pattern by the addition of activity name.</span></span>  
  
```  
<ic:Filter>  
  <ic:Expression>  
    <wf:Operation Name="GetActivityType" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>System.Workflow.ComponentModel.Activity, System.Workflow.ComponentModel, Version=3.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <wf:Operation Name="GetActivityName" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>MyActivity</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <ic:Operation Name="And" />  
    <wf:Operation Name="GetUserDataType" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>System.Object</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <ic:Operation Name="And" />  
    <wf:Operation Name="GetUserKey" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>key</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <ic:Operation Name="And" />  
  </ic:Expression>  
</ic:Filter>   
```