---
title: "Mise en attente de l’orchestration et la réactivation | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 57d7c0bf-a707-4ebd-afab-e75dd80c3c34
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 23ec36d960173c9ce912bb89a38b1df9590f84e5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="orchestration-dehydration-and-rehydration"></a><span data-ttu-id="22dce-102">Mise en attente et réactivation des orchestrations</span><span class="sxs-lookup"><span data-stu-id="22dce-102">Orchestration Dehydration and Rehydration</span></span>
<span data-ttu-id="22dce-103">Lorsque plusieurs processus d'entreprise à long terme sont exécutés en même temps, la mémoire et les performances constituent des problèmes potentiels.</span><span class="sxs-lookup"><span data-stu-id="22dce-103">When many long-running business processes are running at the same time, memory and performance are potential issues.</span></span> <span data-ttu-id="22dce-104">Le moteur d'orchestration résout ces problèmes en « mettant en attente » et en « réalimentant » les instances d'orchestration.</span><span class="sxs-lookup"><span data-stu-id="22dce-104">The orchestration engine addresses these issues by "dehydrating" and "rehydrating" orchestration instances.</span></span>  
  
 <span data-ttu-id="22dce-105">La mise en attente est le processus qui consiste à sérialiser l'état d'une orchestration dans une base de données SQL Server.</span><span class="sxs-lookup"><span data-stu-id="22dce-105">Dehydration is the process of serializing the state of an orchestration into a SQL Server database.</span></span> <span data-ttu-id="22dce-106">La réactivation est le processus inverse : la désérialisation du dernier état d’exécution d’une orchestration à partir de la base de données.</span><span class="sxs-lookup"><span data-stu-id="22dce-106">Rehydration is the reverse of this process: deserializing the last running state of an orchestration from the database.</span></span> <span data-ttu-id="22dce-107">La mise en attente est utilisée pour réduire au maximum l'utilisation de ressources système en réduisant le nombre d'orchestrations qui doivent être instanciées simultanément.</span><span class="sxs-lookup"><span data-stu-id="22dce-107">Dehydration is used to minimize the use of system resources by reducing the number of orchestrations that have to be instantiated in memory at one time.</span></span>  
  
## <a name="dehydration"></a><span data-ttu-id="22dce-108">Mise en attente</span><span class="sxs-lookup"><span data-stu-id="22dce-108">Dehydration</span></span>  
 <span data-ttu-id="22dce-109">Le moteur d'orchestration est susceptible de déterminer qu'une instance d'orchestration est inactive depuis relativement longtemps.</span><span class="sxs-lookup"><span data-stu-id="22dce-109">The orchestration engine might determine that an orchestration instance has been idle for a relatively long period of time.</span></span> <span data-ttu-id="22dce-110">Il calcule des seuils pour déterminer le temps pendant lequel il devra attendre que diverses actions aient lieu. Si ces seuils sont dépassés, il mettra en attente l'instance.</span><span class="sxs-lookup"><span data-stu-id="22dce-110">It calculates thresholds to determine how long it will wait for various actions to take place, and if those thresholds are exceeded, it dehydrates the instance.</span></span> <span data-ttu-id="22dce-111">Cela peut se produire dans les circonstances suivantes :</span><span class="sxs-lookup"><span data-stu-id="22dce-111">This can occur under the following circumstances:</span></span>  
  
-   <span data-ttu-id="22dce-112">Quand l'orchestration attend de recevoir un message et que l'attente est plus longue qu'un seuil déterminé par le moteur.</span><span class="sxs-lookup"><span data-stu-id="22dce-112">When the orchestration is waiting to receive a message, and the wait is longer than a threshold determined by the engine.</span></span>  
  
-   <span data-ttu-id="22dce-113">Lorsque l’orchestration « écoute » pour un message, comme lorsque vous utilisez un **écouter** forme et qu’aucune branche est déclenchée avant un seuil déterminé par le moteur.</span><span class="sxs-lookup"><span data-stu-id="22dce-113">When the orchestration is "listening" for a message, as it does when you use a **Listen** shape, and no branch is triggered before a threshold determined by the engine.</span></span> <span data-ttu-id="22dce-114">La seule exception est lorsque le **écouter** forme contient une activation de réception.</span><span class="sxs-lookup"><span data-stu-id="22dce-114">The only exception to this is when the **Listen** shape contains an activation receive.</span></span>  
  
-   <span data-ttu-id="22dce-115">Quand, dans l'orchestration, un délai est plus long qu'un seuil déterminé par le moteur.</span><span class="sxs-lookup"><span data-stu-id="22dce-115">When a delay in the orchestration is longer than a threshold determined by the engine.</span></span>  
  
 <span data-ttu-id="22dce-116">Le moteur met l'instance en attente en enregistrant l'état et libère la mémoire requise par l'instance.</span><span class="sxs-lookup"><span data-stu-id="22dce-116">The engine dehydrates the instance by saving the state, and frees up the memory required by the instance.</span></span> <span data-ttu-id="22dce-117">En mettant les instances d’orchestration dormantes, le moteur rend possible pour un grand nombre de processus d’entreprise longue à s’exécuter simultanément sur le même ordinateur.</span><span class="sxs-lookup"><span data-stu-id="22dce-117">By dehydrating dormant orchestration instances, the engine makes it possible for a large number of long-running business processes to run concurrently on the same computer.</span></span>  
  
 <span data-ttu-id="22dce-118">Douze propriétés sont disponibles pour configurer le fonctionnement de la mise en attente dans BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="22dce-118">You can set 12 properties to configure how dehydration works in BizTalk Server.</span></span> <span data-ttu-id="22dce-119">Les rubriques de cette section fournissent une description de ces propriétés et de leur valeur par défaut, et présentent la manière dont les différentes valeurs affectent le comportement de la mise en attente.</span><span class="sxs-lookup"><span data-stu-id="22dce-119">The topics in this section list and describe these properties and their default values, and discuss how various values affect dehydration behavior.</span></span>  
  
## <a name="rehydration"></a><span data-ttu-id="22dce-120">Réactivation</span><span class="sxs-lookup"><span data-stu-id="22dce-120">Rehydration</span></span>  
 <span data-ttu-id="22dce-121">Le moteur d'orchestration peut être amené à réalimenter une instance d'orchestration suite à la réception d'un message ou à l'expiration d'un délai spécifié dans une forme Attente.</span><span class="sxs-lookup"><span data-stu-id="22dce-121">The orchestration engine can be triggered to rehydrate an orchestration instance by the receipt of a message or by the expiration of a time-out specified in a Delay shape.</span></span> <span data-ttu-id="22dce-122">Il charge l’instance d’orchestration enregistrée dans la mémoire, restaure son état et il s’exécute à partir du point où elle s’est arrêté.</span><span class="sxs-lookup"><span data-stu-id="22dce-122">It then loads the saved orchestration instance into memory, restores its state, and runs it from the point where it left off.</span></span> <span data-ttu-id="22dce-123">Pour plus d’informations sur l’utilisation des formes dans les orchestrations, consultez [formes d’Orchestration](../core/orchestration-shapes.md).</span><span class="sxs-lookup"><span data-stu-id="22dce-123">For more information about using shapes in orchestrations, see [Orchestration Shapes](../core/orchestration-shapes.md).</span></span>  
  
 <span data-ttu-id="22dce-124">Il est possible de configurer une orchestration pour qu'elle s'exécute sur plusieurs serveurs.</span><span class="sxs-lookup"><span data-stu-id="22dce-124">An orchestration can be configured to run on more than one server.</span></span> <span data-ttu-id="22dce-125">Après sa mise en attente, une instance d'orchestration peut être réalimentée sur n'importe lequel de ces serveurs.</span><span class="sxs-lookup"><span data-stu-id="22dce-125">After an orchestration instance has been dehydrated, it can be rehydrated on any of these servers.</span></span> <span data-ttu-id="22dce-126">Si un serveur tombe en panne, le moteur continue d’exécuter l’orchestration sur un autre serveur, à partir de son état précédent.</span><span class="sxs-lookup"><span data-stu-id="22dce-126">If one server goes down, the engine continues to run the orchestration on a different server, continuing from its previous state.</span></span> <span data-ttu-id="22dce-127">Cette fonctionnalité permet également au moteur d'implémenter l'équilibrage des charges sur les serveurs.</span><span class="sxs-lookup"><span data-stu-id="22dce-127">The engine also takes advantage of this feature to implement load balancing across servers.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="22dce-128">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="22dce-128">In This Section</span></span>  
  
-   [<span data-ttu-id="22dce-129">Modifications des stratégies de mise en attente de BizTalk Server 2004</span><span class="sxs-lookup"><span data-stu-id="22dce-129">Changes in Dehydration Policy from BizTalk Server 2004</span></span>](../core/changes-in-dehydration-policy-from-biztalk-server-2004.md)  
  
-   [<span data-ttu-id="22dce-130">Propriétés par défaut de mise en attente</span><span class="sxs-lookup"><span data-stu-id="22dce-130">Dehydration Default Properties</span></span>](../core/dehydration-default-properties.md)  
  
-   [<span data-ttu-id="22dce-131">Mode de mise en attente de calcul</span><span class="sxs-lookup"><span data-stu-id="22dce-131">How to Calculate Dehydration</span></span>](../core/how-to-calculate-dehydration.md)  
  
-   [<span data-ttu-id="22dce-132">Exemple de calcul de mise en attente</span><span class="sxs-lookup"><span data-stu-id="22dce-132">Sample Dehydration Calculation</span></span>](../core/sample-dehydration-calculation.md)  
  
-   [<span data-ttu-id="22dce-133">Compteurs de performances de mise en attente d’orchestration</span><span class="sxs-lookup"><span data-stu-id="22dce-133">Orchestration Dehydration Performance Counters</span></span>](../core/orchestration-dehydration-performance-counters.md)  
  
-   [<span data-ttu-id="22dce-134">Fichier BTSNTSvc.exe.config</span><span class="sxs-lookup"><span data-stu-id="22dce-134">BTSNTSvc.exe.config File</span></span>](../core/btsntsvc-exe-config-file.md)  
  
-   [<span data-ttu-id="22dce-135">Autres activités qui peuvent affecter le comportement de mise en attente</span><span class="sxs-lookup"><span data-stu-id="22dce-135">Other Activities That Can Affect Dehydration Behavior</span></span>](../core/other-activities-that-can-affect-dehydration-behavior.md)