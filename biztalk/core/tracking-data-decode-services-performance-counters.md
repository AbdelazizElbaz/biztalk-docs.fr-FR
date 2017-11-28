---
title: "Données de suivi décoder des compteurs de Performance Services | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 733450b1-71b5-48a4-9ac3-cd880324440c
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 99ec03138e455c671e9ccb69aa8bc4c5588d287c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="tracking-data-decode-services-performance-counters"></a><span data-ttu-id="cd0ac-102">Compteurs de performance du service de décodage des données de suivi</span><span class="sxs-lookup"><span data-stu-id="cd0ac-102">Tracking Data Decode Services Performance Counters</span></span>
<span data-ttu-id="cd0ac-103">Les compteurs de performance permettent d'analyser des aspects spécifiques du travail effectué sur le site ou le système par un service.</span><span class="sxs-lookup"><span data-stu-id="cd0ac-103">Performance counters allow you to monitor specific aspects of work performed on the site or system by service.</span></span> <span data-ttu-id="cd0ac-104">Ils peuvent vous aider à identifier et à résoudre des problèmes de performances de serveur.</span><span class="sxs-lookup"><span data-stu-id="cd0ac-104">Performance counters can help you identify and troubleshoot server performance issues.</span></span>  
  
 <span data-ttu-id="cd0ac-105">Les compteurs de performances suivants sont accessibles pour chaque instance d’hôte sous le **TDDS** catégorie d’objet de performances :</span><span class="sxs-lookup"><span data-stu-id="cd0ac-105">The following performance counters are accessible for each host instance under the **BizTalk:TDDS** performance object category:</span></span>  
  
|<span data-ttu-id="cd0ac-106">**Catégorie**</span><span class="sxs-lookup"><span data-stu-id="cd0ac-106">**Category**</span></span>|<span data-ttu-id="cd0ac-107">**Compteur**</span><span class="sxs-lookup"><span data-stu-id="cd0ac-107">**Counter**</span></span>|<span data-ttu-id="cd0ac-108">**Description**</span><span class="sxs-lookup"><span data-stu-id="cd0ac-108">**Description**</span></span>|  
|------------------|-----------------|---------------------|  
|<span data-ttu-id="cd0ac-109">BizTalk:TDDS</span><span class="sxs-lookup"><span data-stu-id="cd0ac-109">BizTalk:TDDS</span></span>|<span data-ttu-id="cd0ac-110">Lots traités</span><span class="sxs-lookup"><span data-stu-id="cd0ac-110">Batches being processed</span></span>|<span data-ttu-id="cd0ac-111">Nombre de lots en cours de traitement dans la transaction SQL actuelle.</span><span class="sxs-lookup"><span data-stu-id="cd0ac-111">The number of batches that are being processed inside the current SQL transaction.</span></span>|  
||<span data-ttu-id="cd0ac-112">Lots validés</span><span class="sxs-lookup"><span data-stu-id="cd0ac-112">Batches committed</span></span>|<span data-ttu-id="cd0ac-113">Nombre de lots validés dans la base de données de destination.</span><span class="sxs-lookup"><span data-stu-id="cd0ac-113">The number of batches committed to the destination database.</span></span>|  
||<span data-ttu-id="cd0ac-114">Événements traités</span><span class="sxs-lookup"><span data-stu-id="cd0ac-114">Events being processed</span></span>|<span data-ttu-id="cd0ac-115">Nombre d'événements en cours de traitement dans la transaction SQL actuelle.</span><span class="sxs-lookup"><span data-stu-id="cd0ac-115">The number of events that are being processed inside of the current SQL transaction.</span></span>|  
||<span data-ttu-id="cd0ac-116">Événements validés</span><span class="sxs-lookup"><span data-stu-id="cd0ac-116">Event Committed</span></span>|<span data-ttu-id="cd0ac-117">Nombre d'événements validés dans la base de données de destination durant la seconde écoulée.</span><span class="sxs-lookup"><span data-stu-id="cd0ac-117">The number of events committed to the destination database within this second.</span></span>|  
||<span data-ttu-id="cd0ac-118">Enregistrements traités</span><span class="sxs-lookup"><span data-stu-id="cd0ac-118">Records being processed</span></span>|<span data-ttu-id="cd0ac-119">Nombre d'enregistrements en cours de traitement dans la transaction SQL actuelle.</span><span class="sxs-lookup"><span data-stu-id="cd0ac-119">The number of records that are being processed inside the current SQL transaction.</span></span>|  
||<span data-ttu-id="cd0ac-120">Enregistrements validés</span><span class="sxs-lookup"><span data-stu-id="cd0ac-120">Records Committed</span></span>|<span data-ttu-id="cd0ac-121">Nombre d'enregistrements validés dans la base de données de destination durant la seconde écoulée.</span><span class="sxs-lookup"><span data-stu-id="cd0ac-121">The number of records committed to the destination database during this second.</span></span>|  
||<span data-ttu-id="cd0ac-122">Nombre total de lots</span><span class="sxs-lookup"><span data-stu-id="cd0ac-122">Total Batches</span></span>|<span data-ttu-id="cd0ac-123">Nombre total de lots traités par le service TDDS.</span><span class="sxs-lookup"><span data-stu-id="cd0ac-123">Total batches processed by TDDS.</span></span>|  
||<span data-ttu-id="cd0ac-124">Nombre total d'événements</span><span class="sxs-lookup"><span data-stu-id="cd0ac-124">Total Events</span></span>|<span data-ttu-id="cd0ac-125">Nombre total d'événements traités par le service TDDS.</span><span class="sxs-lookup"><span data-stu-id="cd0ac-125">Total events processed by TDDS.</span></span>|  
||<span data-ttu-id="cd0ac-126">Nombre total échec de lots</span><span class="sxs-lookup"><span data-stu-id="cd0ac-126">Total Failed Batches</span></span>|<span data-ttu-id="cd0ac-127">Nombre total de lots que le service TDDS n'a pas pu exécuter.</span><span class="sxs-lookup"><span data-stu-id="cd0ac-127">Total batches failed to run by TDDS.</span></span>|  
||<span data-ttu-id="cd0ac-128">Nombre total échec d'événements</span><span class="sxs-lookup"><span data-stu-id="cd0ac-128">Total Failed Events</span></span>|<span data-ttu-id="cd0ac-129">Nombre total d'événements que le service TDDS n'a pas pu exécuter.</span><span class="sxs-lookup"><span data-stu-id="cd0ac-129">Total events failed to run by TDDS.</span></span>|  
||<span data-ttu-id="cd0ac-130">Nombre total d'enregistrements</span><span class="sxs-lookup"><span data-stu-id="cd0ac-130">Total Records</span></span>|<span data-ttu-id="cd0ac-131">Nombre total d'enregistrements traités par le service TDDS.</span><span class="sxs-lookup"><span data-stu-id="cd0ac-131">Total records processed by TDDS.</span></span>|  
  
## <a name="to-access-performance-counters"></a><span data-ttu-id="cd0ac-132">Pour accéder aux compteurs de performance</span><span class="sxs-lookup"><span data-stu-id="cd0ac-132">To access performance counters</span></span>  
 <span data-ttu-id="cd0ac-133">Utilisez la procédure suivante pour accéder aux compteurs de performances.</span><span class="sxs-lookup"><span data-stu-id="cd0ac-133">Use the following steps to access the performance counters.</span></span>  
  
#### <a name="if-you-are-using-windows-2008"></a><span data-ttu-id="cd0ac-134">Si vous exécutez Windows 2008</span><span class="sxs-lookup"><span data-stu-id="cd0ac-134">If you are using Windows 2008</span></span>  
  
1.  <span data-ttu-id="cd0ac-135">Cliquez sur **Démarrer**, pointez sur **outils d’administration**, puis cliquez sur **l’Analyseur de performances**.</span><span class="sxs-lookup"><span data-stu-id="cd0ac-135">Click **Start**, point to **Administrative Tools**, and then click **Performance Monitor**.</span></span>  
  
2.  <span data-ttu-id="cd0ac-136">Dans le **l’Analyseur de performances** boîte de dialogue, développez **outils d’analyse**, sélectionnez **l’Analyseur de performances**, puis cliquez sur **ajouter**.</span><span class="sxs-lookup"><span data-stu-id="cd0ac-136">In the **Performance Monitor** dialog box, expand **Monitoring Tools**, select **Performance Monitor**, and then click **Add**.</span></span>  
  
3.  <span data-ttu-id="cd0ac-137">Dans le **ajouter des compteurs** boîte de dialogue, à partir de la **compteurs disponibles** liste, développez le **TDDS** objet compteur de performance et sélectionnez les compteurs à surveiller</span><span class="sxs-lookup"><span data-stu-id="cd0ac-137">In the **Add Counters** dialog box, from the **Available Counters** list, expand the **BizTalk:TDDS** performance counter object and select the counters to be monitored</span></span>  
  
4.  <span data-ttu-id="cd0ac-138">Dans le **Instances de l’objet sélectionné** , sélectionnez les instances spécifiques à surveiller pour les compteurs sélectionnés, puis cliquez sur **ajouter**.</span><span class="sxs-lookup"><span data-stu-id="cd0ac-138">In the **Instances of Selected object** list, select the specific instances to be monitored for the selected counters and then click **Add**.</span></span>  <span data-ttu-id="cd0ac-139">Pour sélectionner toutes les instances de compteur disponibles, sélectionnez \< **toutes les instances**>.</span><span class="sxs-lookup"><span data-stu-id="cd0ac-139">To select all available counter instances, select \<**All instances**>.</span></span>  
  
5.  <span data-ttu-id="cd0ac-140">Après avoir ajouté les compteurs, cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="cd0ac-140">After adding the counters, click **OK**.</span></span>  
  
     <span data-ttu-id="cd0ac-141">Les compteurs de performances sélectionnés s’affichent sur le **l’Analyseur de performances** écran.</span><span class="sxs-lookup"><span data-stu-id="cd0ac-141">The selected performance counters appear on the **Performance Monitor** screen.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd0ac-142">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cd0ac-142">See Also</span></span>  
 <span data-ttu-id="cd0ac-143">[Trucs et astuces](../core/performance-tips-and-tricks.md) </span><span class="sxs-lookup"><span data-stu-id="cd0ac-143">[Performance Tips and Tricks](../core/performance-tips-and-tricks.md) </span></span>  
 <span data-ttu-id="cd0ac-144">[Mesurer le débit de moteur maximal acceptable](../core/measuring-maximum-sustainable-engine-throughput.md) </span><span class="sxs-lookup"><span data-stu-id="cd0ac-144">[Measuring Maximum Sustainable Engine Throughput](../core/measuring-maximum-sustainable-engine-throughput.md) </span></span>  
 <span data-ttu-id="cd0ac-145">[Mesurer le débit de suivi maximal acceptable](../core/measuring-maximum-sustainable-tracking-throughput.md) </span><span class="sxs-lookup"><span data-stu-id="cd0ac-145">[Measuring Maximum Sustainable Tracking Throughput](../core/measuring-maximum-sustainable-tracking-throughput.md) </span></span>  
 [<span data-ttu-id="cd0ac-146">Optimisation de l’utilisation des ressources via la limitation de l’hôte</span><span class="sxs-lookup"><span data-stu-id="cd0ac-146">Optimizing Resource Usage Through Host Throttling</span></span>](../core/optimizing-resource-usage-through-host-throttling.md)