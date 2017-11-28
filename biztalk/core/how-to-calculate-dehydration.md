---
title: Comment calculer la mise en attente | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 88f2d09c-60db-4daf-b850-23f2c8915502
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4a327695099ec575f2a13ccb75b4152e4a7de1af
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-calculate-dehydration"></a><span data-ttu-id="0a9c2-102">Calcul de la mise en attente</span><span class="sxs-lookup"><span data-stu-id="0a9c2-102">How to Calculate Dehydration</span></span>
<span data-ttu-id="0a9c2-103">Pour calculer la mise en attente, vous utilisez les propriétés configurées et des valeurs d'exécution spécifiques.</span><span class="sxs-lookup"><span data-stu-id="0a9c2-103">To calculate dehydration, you use the configured properties and certain run-time values.</span></span> <span data-ttu-id="0a9c2-104">L'exemple de code suivant montre comment calculer un scénario de mise en attente hypothétique.</span><span class="sxs-lookup"><span data-stu-id="0a9c2-104">The following example demonstrates how to calculate a hypothetical dehydration scenario.</span></span>  
  
### <a name="to-calculate-dehydration"></a><span data-ttu-id="0a9c2-105">Pour calculer la mise en attente</span><span class="sxs-lookup"><span data-stu-id="0a9c2-105">To calculate dehydration</span></span>  
  
1.  <span data-ttu-id="0a9c2-106">Laissez alpha représenter un facteur compris entre 0 et 1 mesurant la contrainte de mémoire.</span><span class="sxs-lookup"><span data-stu-id="0a9c2-106">Let alpha represent a factor between 0 and 1 that measures memory stress.</span></span>  <span data-ttu-id="0a9c2-107">En pratique, alpha possède un composant pour chacun des 3 critères de limitation basée sur la mémoire (propriétés de mise en attente) ; dans cet exemple, ils sont désignés par alpha(virtual), alpha(private) et alpha(physical).</span><span class="sxs-lookup"><span data-stu-id="0a9c2-107">In practice, alpha has a component for each of the three memory throttling criteria (dehydration properties); in this example we denote them as alpha(virtual), alpha(private) and alpha(physical).</span></span> <span data-ttu-id="0a9c2-108">Définissez les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="0a9c2-108">Define the following:</span></span>  
  
    ```  
    IF ActualPrivateBytes < OptimalUsage  
       alpha(private) = 1  
    ELSE IF ActualPrivateBytes > MaximalUsage  
       alpha(private) = 0  
    ELSE  
       alpha(private) = (MaximalUsage - ActualPrivateBytes) / (MaximalUsage - OptimalUsage)  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="0a9c2-109">Les éléments OptimalUsage et MaximalUsage possèdent des valeurs par défaut pour chaque propriété de mise en attente.</span><span class="sxs-lookup"><span data-stu-id="0a9c2-109">OptimalUsage and MaximalUsage have default values for each dehydration property.</span></span> <span data-ttu-id="0a9c2-110">Ces valeurs peuvent être modifiées dans le fichier BTSNTSvc.exe.config.</span><span class="sxs-lookup"><span data-stu-id="0a9c2-110">These values can be changed in the BTSNTSvc.exe.config file.</span></span> <span data-ttu-id="0a9c2-111">Pour plus d’informations, consultez [propriétés par défaut de mise en attente](../core/dehydration-default-properties.md).</span><span class="sxs-lookup"><span data-stu-id="0a9c2-111">For more information, see [Dehydration Default Properties](../core/dehydration-default-properties.md).</span></span>  
  
2.  <span data-ttu-id="0a9c2-112">Définissez les autres composants alpha de la même façon.</span><span class="sxs-lookup"><span data-stu-id="0a9c2-112">Define the other alpha components analogously.</span></span> <span data-ttu-id="0a9c2-113">Définissez les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="0a9c2-113">Define the following:</span></span>  
  
    ```  
    alpha = Minimum { alpha(virtual), alpha(private), alpha(physical) }  
    where alpha(…) = 1 whenever IsActive=false for that given memory unit  
    ```  
  
3.  <span data-ttu-id="0a9c2-114">Définissez ensuite l'élément TestThreshold (l'unité de TestThreshold, MinThreshold et MaxThreshold est la seconde) :</span><span class="sxs-lookup"><span data-stu-id="0a9c2-114">Then define TestThreshold (TestThreshold, MinThreshold, and MaxThreshold are defined in seconds):</span></span>  
  
    ```  
    TestThreshold = MinThreshold + (alpha * (MaxThreshold – MinThreshold))  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="0a9c2-115">Valeur par défaut de MinThreshold = 1.</span><span class="sxs-lookup"><span data-stu-id="0a9c2-115">MinThreshold default value = 1.</span></span> <span data-ttu-id="0a9c2-116">Valeur par défaut de MaxThreshold = 1800.</span><span class="sxs-lookup"><span data-stu-id="0a9c2-116">MaxThreshold default value = 1800.</span></span> <span data-ttu-id="0a9c2-117">Ces valeurs peuvent être modifiées dans le fichier BTSNTSvc.exe.config.</span><span class="sxs-lookup"><span data-stu-id="0a9c2-117">These values can be changed in the BTSNTSvc.exe.config file.</span></span> <span data-ttu-id="0a9c2-118">Pour plus d’informations, consultez [propriétés par défaut de mise en attente](../core/dehydration-default-properties.md).</span><span class="sxs-lookup"><span data-stu-id="0a9c2-118">For more information, see [Dehydration Default Properties](../core/dehydration-default-properties.md).</span></span>  
  
4.  <span data-ttu-id="0a9c2-119">Définissez ensuite les éléments TimeBlocked et EstimatedTime :</span><span class="sxs-lookup"><span data-stu-id="0a9c2-119">Then define TimeBlocked and EstimatedTime:</span></span>  
  
    -   <span data-ttu-id="0a9c2-120">TimeBlocked = durée d'attente réelle pour que l'abonnement soit satisfait</span><span class="sxs-lookup"><span data-stu-id="0a9c2-120">TimeBlocked = actual time we have been waiting for this subscription to be satisfied</span></span>  
  
    -   <span data-ttu-id="0a9c2-121">EstimatedTime = durée d'inactivité estimée pour cette orchestration (par ex., le délai d'attente restant pour l'écoute)</span><span class="sxs-lookup"><span data-stu-id="0a9c2-121">EstimatedTime = estimated time that this orchestration will remain idle (e.g. remaining timeout on the listen)</span></span>  
  
 <span data-ttu-id="0a9c2-122">La décision de mise en attente dépend du résultat de la condition booléenne suivante (true = mise en attente) :</span><span class="sxs-lookup"><span data-stu-id="0a9c2-122">The decision whether to dehydrate is the result of the following Boolean condition (true = dehydrate):</span></span>  
  
-   <span data-ttu-id="0a9c2-123">Mise en attente = (EstimatedTime > TestThreshold OU TimeBlocked > (2* TestThreshold))</span><span class="sxs-lookup"><span data-stu-id="0a9c2-123">Dehydrate = (EstimatedTime > TestThreshold OR TimeBlocked > (2* TestThreshold))</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0a9c2-124">La durée estimée correspond à la durée restante avant l'expiration du délai (si l'attente est de 5 minutes et si deux minutes se sont déjà écoulées, TimeBlocked=120 secondes, EstimatedTime=180 secondes).</span><span class="sxs-lookup"><span data-stu-id="0a9c2-124">Estimated time is the time remaining until the delay is ended (if delayed for 5 minutes and 2 minutes has passed, TimeBlocked=120 seconds, EstimatedTime=180 seconds).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a9c2-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0a9c2-125">See Also</span></span>  
 <span data-ttu-id="0a9c2-126">[Propriétés par défaut de mise en attente](../core/dehydration-default-properties.md) </span><span class="sxs-lookup"><span data-stu-id="0a9c2-126">[Dehydration Default Properties](../core/dehydration-default-properties.md) </span></span>  
 [<span data-ttu-id="0a9c2-127">Fichier BTSNTSvc.exe.config</span><span class="sxs-lookup"><span data-stu-id="0a9c2-127">BTSNTSvc.exe.config File</span></span>](../core/btsntsvc-exe-config-file.md)