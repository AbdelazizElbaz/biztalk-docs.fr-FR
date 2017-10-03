---
title: GetWorkflowEvent | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2534e0b8-26df-4554-b0df-742014deb64d
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f8dc753bd45452af6ab586a11f216bc65f9539fb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="getworkflowevent"></a><span data-ttu-id="d2842-102">GetWorkflowEvent</span><span class="sxs-lookup"><span data-stu-id="d2842-102">GetWorkflowEvent</span></span>
<span data-ttu-id="d2842-103">Transmet le nom de l'événement de flux de travail en cours sur la pile.</span><span class="sxs-lookup"><span data-stu-id="d2842-103">Pushes the name of the current workflow event onto the stack.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2842-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d2842-104">Syntax</span></span>  
  
```  
  
<wf:Operation Name="GetWorkflowEvent" />  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d2842-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d2842-105">Parameters</span></span>  
 <span data-ttu-id="d2842-106">Aucun.</span><span class="sxs-lookup"><span data-stu-id="d2842-106">None.</span></span>  
  
## <a name="pushed-value"></a><span data-ttu-id="d2842-107">Valeur transmise</span><span class="sxs-lookup"><span data-stu-id="d2842-107">Pushed Value</span></span>  
 <span data-ttu-id="d2842-108">Chaîne contenant l'événement de flux de travail en cours.</span><span class="sxs-lookup"><span data-stu-id="d2842-108">String containing the current workflow event.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d2842-109">Notes</span><span class="sxs-lookup"><span data-stu-id="d2842-109">Remarks</span></span>  
 <span data-ttu-id="d2842-110">Une instance de flux de travail peut passer par plusieurs états au cours de son exécution.</span><span class="sxs-lookup"><span data-stu-id="d2842-110">A workflow instance can pass through several states during the course of its execution.</span></span> <span data-ttu-id="d2842-111">Par exemple, une instance de flux de travail peut devenir inactive ou être suspendue.</span><span class="sxs-lookup"><span data-stu-id="d2842-111">For example, a workflow instance may become idle, or it may be suspended.</span></span> <span data-ttu-id="d2842-112">Chaque fois que l'instance de flux de travail change d'état, elle transmet un événement d'état de flux de travail à l'infrastructure de suivi d'exécution.</span><span class="sxs-lookup"><span data-stu-id="d2842-112">Every time the workflow instance changes state, it emits a workflow status event to the runtime tracking infrastructure.</span></span> <span data-ttu-id="d2842-113">L'intercepteur BAM de Windows Workflow Foundation prend en charge la plupart des événements définis par l'énumération `System.Workflow.Runtime.Tracking.TrackingWorkflowEvent`, comme illustré dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="d2842-113">The Windows Workflow Foundation BAM interceptor supports most of the events defined by the `System.Workflow.Runtime.Tracking.TrackingWorkflowEvent` enumeration, as shown in the following table.</span></span>  
  
|<span data-ttu-id="d2842-114">Événement d'activité</span><span class="sxs-lookup"><span data-stu-id="d2842-114">Activity event</span></span>|<span data-ttu-id="d2842-115"> Description</span><span class="sxs-lookup"><span data-stu-id="d2842-115">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="d2842-116">Modifié</span><span class="sxs-lookup"><span data-stu-id="d2842-116">Changed</span></span>|<span data-ttu-id="d2842-117">Une modification de flux de travail s'est produite sur l'instance de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="d2842-117">A workflow change has occurred on the workflow instance.</span></span>|  
|<span data-ttu-id="d2842-118">Terminé</span><span class="sxs-lookup"><span data-stu-id="d2842-118">Completed</span></span>|<span data-ttu-id="d2842-119">L'instance de flux de travail est terminée.</span><span class="sxs-lookup"><span data-stu-id="d2842-119">The workflow instance has completed.</span></span>|  
|<span data-ttu-id="d2842-120">Créé le</span><span class="sxs-lookup"><span data-stu-id="d2842-120">Created</span></span>|<span data-ttu-id="d2842-121">L'instance de flux de travail a été créée.</span><span class="sxs-lookup"><span data-stu-id="d2842-121">The workflow instance has been created.</span></span>|  
|<span data-ttu-id="d2842-122">Exception</span><span class="sxs-lookup"><span data-stu-id="d2842-122">Exception</span></span>|<span data-ttu-id="d2842-123">Une exception non gérée a été levée.</span><span class="sxs-lookup"><span data-stu-id="d2842-123">An unhandled exception has occurred.</span></span>|  
|<span data-ttu-id="d2842-124">Idle</span><span class="sxs-lookup"><span data-stu-id="d2842-124">Idle</span></span>|<span data-ttu-id="d2842-125">L'instance de flux de travail est inactive.</span><span class="sxs-lookup"><span data-stu-id="d2842-125">The workflow instance is idle.</span></span>|  
|<span data-ttu-id="d2842-126">Loaded</span><span class="sxs-lookup"><span data-stu-id="d2842-126">Loaded</span></span>|<span data-ttu-id="d2842-127">L'instance de flux de travail a été chargée en mémoire.</span><span class="sxs-lookup"><span data-stu-id="d2842-127">The workflow instance has been loaded into memory.</span></span>|  
|<span data-ttu-id="d2842-128">Persisted</span><span class="sxs-lookup"><span data-stu-id="d2842-128">Persisted</span></span>|<span data-ttu-id="d2842-129">L'instance de flux de travail a été rendue persistance.</span><span class="sxs-lookup"><span data-stu-id="d2842-129">The workflow instance has been persisted.</span></span>|  
|<span data-ttu-id="d2842-130">Resumed</span><span class="sxs-lookup"><span data-stu-id="d2842-130">Resumed</span></span>|<span data-ttu-id="d2842-131">L'exécution d'une instance de flux de travail précédemment suspendue a repris.</span><span class="sxs-lookup"><span data-stu-id="d2842-131">A previously suspended workflow instance has resumed running.</span></span>|  
|<span data-ttu-id="d2842-132">Démarré</span><span class="sxs-lookup"><span data-stu-id="d2842-132">Started</span></span>|<span data-ttu-id="d2842-133">L'instance de flux de travail a été démarrée.</span><span class="sxs-lookup"><span data-stu-id="d2842-133">The workflow instance has been started.</span></span>|  
|<span data-ttu-id="d2842-134">Suspendu</span><span class="sxs-lookup"><span data-stu-id="d2842-134">Suspended</span></span>|<span data-ttu-id="d2842-135">L'instance de flux de travail a été suspendue.</span><span class="sxs-lookup"><span data-stu-id="d2842-135">The workflow instance has been suspended.</span></span>|  
|<span data-ttu-id="d2842-136">Arrêté</span><span class="sxs-lookup"><span data-stu-id="d2842-136">Terminated</span></span>|<span data-ttu-id="d2842-137">L'instance de flux de travail a été interrompue.</span><span class="sxs-lookup"><span data-stu-id="d2842-137">The workflow instance has been terminated.</span></span>|  
|<span data-ttu-id="d2842-138">Unloaded</span><span class="sxs-lookup"><span data-stu-id="d2842-138">Unloaded</span></span>|<span data-ttu-id="d2842-139">L'instance de flux de travail a été déchargée de la mémoire.</span><span class="sxs-lookup"><span data-stu-id="d2842-139">The workflow instance has been unloaded from memory.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="d2842-140">Vous ne pouvez pas utiliser `GetWorkflowEvent` et `GetActivityEvent` dans le même élément OnEvent.</span><span class="sxs-lookup"><span data-stu-id="d2842-140">You cannot use both `GetWorkflowEvent` and `GetActivityEvent` in the same OnEvent element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d2842-141">Exemple</span><span class="sxs-lookup"><span data-stu-id="d2842-141">Example</span></span>  
 <span data-ttu-id="d2842-142">L'exemple suivant contient un filtre configuré pour rechercher une activité spécifique (« FoodAndDrinksPolicy ») dans un flux de travail.</span><span class="sxs-lookup"><span data-stu-id="d2842-142">The following sample contains a filter that is configured to find a specific activity—"FoodAndDrinksPolicy"—in a workflow.</span></span> <span data-ttu-id="d2842-143">Dans l'exemple, un filtre est configuré pour rechercher l'activité nommée « FoodAndDrinksPolicy » dans un flux de travail fermé.</span><span class="sxs-lookup"><span data-stu-id="d2842-143">In the sample, a filter is configured to find the activity named "FoodAndDrinksPolicy" in a closed workflow.</span></span> <span data-ttu-id="d2842-144">Cette opération est effectuée en comparant la valeur retournée par `GetWorkflowEvent` à la constante « Created ».</span><span class="sxs-lookup"><span data-stu-id="d2842-144">This is done by comparing the value returned by `GetWorkflowEvent` to the constant "Created".</span></span>  
  
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
  
 <span data-ttu-id="d2842-145">Cette opération est utile pour le suivi de la durée de vie d'un flux de travail et pour la détection d'exceptions ou d'autres problèmes liés au flux de travail.</span><span class="sxs-lookup"><span data-stu-id="d2842-145">This operation is useful for tracking the lifetime of a workflow and for detecting exceptions or other problems with the workflow.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2842-146">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d2842-146">See Also</span></span>  
 [<span data-ttu-id="d2842-147">Énumération de System.Workflow.Runtime.Tracking.TrackingWorkflowEvent</span><span class="sxs-lookup"><span data-stu-id="d2842-147">System.Workflow.Runtime.Tracking.TrackingWorkflowEvent enumeration</span></span>](http://go.microsoft.com/fwlink/?LinkId=119568)