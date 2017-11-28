---
title: Test de charge maximale | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- sustainable load test
- LoadGen tool, sustainable load test
ms.assetid: a9d752ff-aff1-4445-8af5-8f84609880e2
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0a32f7ab31435cb81bee9e4ed52afc1f7d5194e8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="sustainable-load-test"></a><span data-ttu-id="dbd42-102">Test de charge maximale</span><span class="sxs-lookup"><span data-stu-id="dbd42-102">Sustainable Load Test</span></span>
<span data-ttu-id="dbd42-103">Les informations contenues dans cette rubrique fait référence aux tests décrits dans [des scénarios de Test pour mesurer le débit maximal acceptable du moteur de](../core/test-scenarios-for-measuring-mst-of-the-engine.md).</span><span class="sxs-lookup"><span data-stu-id="dbd42-103">The information in this topic refers to the tests explained in [Test Scenarios for Measuring MST of the Engine](../core/test-scenarios-for-measuring-mst-of-the-engine.md).</span></span>  
  
 <span data-ttu-id="dbd42-104">Pour le premier test, le système a fonctionné à son débit maximal acceptable, de façon à effectuer des observations sur un système sain.</span><span class="sxs-lookup"><span data-stu-id="dbd42-104">For the first test, the system was driven to MST so that observations of a healthy system can be made.</span></span>  
  
 <span data-ttu-id="dbd42-105">Le graphique suivant montre les indicateurs clés après l'utilisation de cette approche pour identifier le débit maximal acceptable du système de test.</span><span class="sxs-lookup"><span data-stu-id="dbd42-105">The following graph shows key indicators after using this approach to find the maximum sustainable throughput of the test system.</span></span>  
  
 <span data-ttu-id="dbd42-106">**Profil de charge du test de charge maximale**</span><span class="sxs-lookup"><span data-stu-id="dbd42-106">**Load profile of sustainable load test**</span></span>  
  
 <span data-ttu-id="dbd42-107">![L’Analyseur de performances mesure charge maximale](../core/media/bts06-sustainable-load.gif "BTS06_Sustainable_Load")</span><span class="sxs-lookup"><span data-stu-id="dbd42-107">![Performance monitor measuring sustainable load](../core/media/bts06-sustainable-load.gif "BTS06_Sustainable_Load")</span></span>  
  
 <span data-ttu-id="dbd42-108">Ce graphique montre que, pendant la durée du test, la profondeur du spouleur est restée stable et n'a pas augmenté :</span><span class="sxs-lookup"><span data-stu-id="dbd42-108">This graph shows that, for the hour of the test, the spool depth was stable and not growing:</span></span>  
  
-   <span data-ttu-id="dbd42-109">Les lignes noires en haut du graphique indiquent le nombre total de messages reçus par seconde par le système (pour les deux serveurs de réception, par exemple).</span><span class="sxs-lookup"><span data-stu-id="dbd42-109">The black lines at the top of the graph show the total messages received per second by the system (for example, for both of the receiving servers).</span></span>  
  
-   <span data-ttu-id="dbd42-110">Les lignes au bas du graphique indiquent la profondeur du spouleur MessageBox sur chaque serveur SQL Server.</span><span class="sxs-lookup"><span data-stu-id="dbd42-110">The lines at the bottom of the graph indicate the MessageBox spool depth on each of the SQL Servers.</span></span>  
  
 <span data-ttu-id="dbd42-111">Une fois que le système fonctionne à la profondeur de spouleur stable maximale, le débit maximal acceptable est déterminé par le nombre de messages reçus par seconde.</span><span class="sxs-lookup"><span data-stu-id="dbd42-111">Once the system is driven to the point of the maximum stable spool depth, MST is measured by the number of messages received per second.</span></span> <span data-ttu-id="dbd42-112">Pour ce scénario et avec le matériel décrit, un débit maximal acceptable de 290 messages par seconde a été atteint.</span><span class="sxs-lookup"><span data-stu-id="dbd42-112">For this scenario, on the hardware described, an MST of 290 messages per second was achieved.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="dbd42-113">Une fois que le système fonctionne à une profondeur de spouleur dont la stabilité ne peut plus être garantie, le débit maximal acceptable est dépassé.</span><span class="sxs-lookup"><span data-stu-id="dbd42-113">Once the system is driven to a point where the spool depth is no longer stable over time, MST has been exceeded.</span></span> <span data-ttu-id="dbd42-114">Plusieurs exécution du test avec des charges différentes peuvent être nécessaires pour évaluer la charge maximale à laquelle la profondeur du spouleur reste stable et à laquelle le système peut gérer les messages accumulés sans risque de saturation.</span><span class="sxs-lookup"><span data-stu-id="dbd42-114">Several test runs with varying load may be required to evaluate the maximum load at which spool depth remains stable and your system can handle the message backlog without incurring additional message backlog.</span></span>  
  
 <span data-ttu-id="dbd42-115">Toute analyse des performances d'un déploiement BizTalk doit passer par la vérification de certains indicateurs clés permettant d'anticiper les engorgements de ressources.</span><span class="sxs-lookup"><span data-stu-id="dbd42-115">Part of any analysis of a BizTalk deployment performance should include checking some key indicators to understand resource bottlenecks.</span></span> <span data-ttu-id="dbd42-116">Les mesures clés et les valeurs correspondantes suivantes ont été utilisées pour ce déploiement fonctionnant au débit maximal acceptables :</span><span class="sxs-lookup"><span data-stu-id="dbd42-116">The key measures and their values used for this deployment running under maximum sustainable throughput were as follows:</span></span>  
  
 <span data-ttu-id="dbd42-117">**Utilisation du processeur**</span><span class="sxs-lookup"><span data-stu-id="dbd42-117">**CPU Utilization**</span></span>  
  
|<span data-ttu-id="dbd42-118">Server</span><span class="sxs-lookup"><span data-stu-id="dbd42-118">Server</span></span>|<span data-ttu-id="dbd42-119">Utilisation moyenne de l'UC</span><span class="sxs-lookup"><span data-stu-id="dbd42-119">Average CPU Utilization</span></span>|  
|------------|-----------------------------|  
|<span data-ttu-id="dbd42-120">Serveurs BizTalk</span><span class="sxs-lookup"><span data-stu-id="dbd42-120">BizTalk Servers</span></span>|<span data-ttu-id="dbd42-121">55%</span><span class="sxs-lookup"><span data-stu-id="dbd42-121">55%</span></span>|  
|<span data-ttu-id="dbd42-122">Serveur SQL Server (serveur MessageBox maître)</span><span class="sxs-lookup"><span data-stu-id="dbd42-122">SQL Server (Master MessageBox Server)</span></span>|<span data-ttu-id="dbd42-123">76%</span><span class="sxs-lookup"><span data-stu-id="dbd42-123">76%</span></span>|  
|<span data-ttu-id="dbd42-124">Serveur SQL Server (autres serveurs MessageBox)</span><span class="sxs-lookup"><span data-stu-id="dbd42-124">SQL Server (Other MessageBox Servers)</span></span>|<span data-ttu-id="dbd42-125">83%</span><span class="sxs-lookup"><span data-stu-id="dbd42-125">83%</span></span>|  
  
 <span data-ttu-id="dbd42-126">**Durée d’inactivité disque physique**</span><span class="sxs-lookup"><span data-stu-id="dbd42-126">**Physical Disk Idle Time**</span></span>  
  
|<span data-ttu-id="dbd42-127">Server</span><span class="sxs-lookup"><span data-stu-id="dbd42-127">Server</span></span>|<span data-ttu-id="dbd42-128">Durée d'inactivité moyenne du disque</span><span class="sxs-lookup"><span data-stu-id="dbd42-128">Average Disk Idle Time</span></span>|  
|------------|----------------------------|  
|<span data-ttu-id="dbd42-129">Moyenne pour tous les serveurs SQL Server</span><span class="sxs-lookup"><span data-stu-id="dbd42-129">Average for all SQL Servers</span></span>|<span data-ttu-id="dbd42-130">69%</span><span class="sxs-lookup"><span data-stu-id="dbd42-130">69%</span></span>|  
  
 <span data-ttu-id="dbd42-131">**Verrous SQL sur SQL Server**</span><span class="sxs-lookup"><span data-stu-id="dbd42-131">**SQL Locks on SQL Server**</span></span>  
  
|<span data-ttu-id="dbd42-132">Paramètre</span><span class="sxs-lookup"><span data-stu-id="dbd42-132">Parameter</span></span>|<span data-ttu-id="dbd42-133">Valeur</span><span class="sxs-lookup"><span data-stu-id="dbd42-133">Value</span></span>|  
|---------------|-----------|  
|<span data-ttu-id="dbd42-134">Nombre total moyen de dépassements de délai de verrouillage par seconde (par serveur SQL Server)</span><span class="sxs-lookup"><span data-stu-id="dbd42-134">Average Total Lock Timeouts per second (per SQL Server)</span></span>|<span data-ttu-id="dbd42-135">1980</span><span class="sxs-lookup"><span data-stu-id="dbd42-135">1980</span></span>|  
|<span data-ttu-id="dbd42-136">Temps d'attente total moyen pour les verrouillages (ms)</span><span class="sxs-lookup"><span data-stu-id="dbd42-136">Average Total Lock Wait Time (ms)</span></span>|<span data-ttu-id="dbd42-137">495</span><span class="sxs-lookup"><span data-stu-id="dbd42-137">495</span></span>|  
  
 <span data-ttu-id="dbd42-138">Au cours de ce test, aucune erreur n'a été consignée dans le journal de l'application BizTalk ou SQL Server.</span><span class="sxs-lookup"><span data-stu-id="dbd42-138">During this test no errors were generated in the BizTalk or SQL Server application log.</span></span>  
  
 <span data-ttu-id="dbd42-139">Ces données permettent de tirer les conclusions suivantes :</span><span class="sxs-lookup"><span data-stu-id="dbd42-139">From this data, we can draw the following conclusions:</span></span>  
  
-   <span data-ttu-id="dbd42-140">Notre système ne génère aucun engorgement de ressources évident.</span><span class="sxs-lookup"><span data-stu-id="dbd42-140">There are no obvious resource bottlenecks in our system.</span></span>  
  
-   <span data-ttu-id="dbd42-141">Tous ces indicateurs se situent dans les limites acceptables.</span><span class="sxs-lookup"><span data-stu-id="dbd42-141">All of these indicators are well within healthy limits.</span></span>  
  
-   <span data-ttu-id="dbd42-142">L'utilisation de l'UC et les durées d'inactivité du disque montrent même que le système dispose encore d'une marge importante.</span><span class="sxs-lookup"><span data-stu-id="dbd42-142">CPU and Disk Idle Times show that there is plenty of headroom and they are not even close to being pegged.</span></span>  
  
-   <span data-ttu-id="dbd42-143">Les indicateurs de verrouillage SQL bonnes **des délais d’attente de verrous/s** ne commence à devenir un problème jusqu'à ce qu’autour de 5000 ou (selon votre serveur SQL Server) et les temps inférieurs à 1 seconde d’attente de verrou sont également acceptables.</span><span class="sxs-lookup"><span data-stu-id="dbd42-143">The SQL lock indicators look good, **Lock Timeouts/sec** doesn’t start to become an issue until around 5000 or so (depending on your SQL Server) and Lock Wait times under 1 second are also healthy.</span></span>  
  
 <span data-ttu-id="dbd42-144">Maintenant que nous avons indiqué comment déterminer le débit maximal acceptable et identifié les indicateurs clés d'un système sain, étudions le comportement d'un système dont les capacités de traitement et de garbage collection sont dépassées.</span><span class="sxs-lookup"><span data-stu-id="dbd42-144">Now that we have shown how to find the maximum sustainable throughput and seen what the key indicators look like for a sustainable, healthy system, let’s explore some behavior associated with a system that is receiving faster than it is processing and collecting garbage.</span></span> <span data-ttu-id="dbd42-145">Passez à [dépassement de Test de charge](../core/overdrive-load-test.md).</span><span class="sxs-lookup"><span data-stu-id="dbd42-145">Proceed to [Overdrive Load Test](../core/overdrive-load-test.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dbd42-146">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dbd42-146">See Also</span></span>  
 <span data-ttu-id="dbd42-147">[Scénarios de test pour mesurer le débit maximal acceptable du moteur](../core/test-scenarios-for-measuring-mst-of-the-engine.md) </span><span class="sxs-lookup"><span data-stu-id="dbd42-147">[Test Scenarios for Measuring MST of the Engine](../core/test-scenarios-for-measuring-mst-of-the-engine.md) </span></span>  
 [<span data-ttu-id="dbd42-148">Test de surcharge</span><span class="sxs-lookup"><span data-stu-id="dbd42-148">Overdrive Load Test</span></span>](../core/overdrive-load-test.md)