---
title: Test de charge de saturation | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- LoadGen tool, simulating floodgate events
- performance, floodgate peaks
- floodgate events [performance]
ms.assetid: 937f2478-339b-4ae2-b107-56f3a4bfc579
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 74954d8b94207832ceee5bbb699a7de1a245f61b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="floodgate-load-test"></a><span data-ttu-id="57d40-102">Test de l'état de saturation</span><span class="sxs-lookup"><span data-stu-id="57d40-102">Floodgate Load Test</span></span>
<span data-ttu-id="57d40-103">Les informations contenues dans cette rubrique fait référence aux tests décrits dans [des scénarios de Test pour mesurer le débit maximal acceptable du moteur de](../core/test-scenarios-for-measuring-mst-of-the-engine.md).</span><span class="sxs-lookup"><span data-stu-id="57d40-103">The information in this topic refers to the tests explained in [Test Scenarios for Measuring MST of the Engine](../core/test-scenarios-for-measuring-mst-of-the-engine.md).</span></span>  
  
## <a name="what-causes-floodgate-events"></a><span data-ttu-id="57d40-104">Origines des événements de saturation</span><span class="sxs-lookup"><span data-stu-id="57d40-104">What Causes Floodgate Events?</span></span>  
 <span data-ttu-id="57d40-105">Il existe plusieurs scénarios où il y a seulement quelques pics (également appelé **événements de saturation**) massives de messages au niveau du système chaque jour.</span><span class="sxs-lookup"><span data-stu-id="57d40-105">There are a number of scenarios where just a few large peaks (also known as **floodgate events**) of messages arrive at the system each day.</span></span> <span data-ttu-id="57d40-106">Entre ces pics d'activité, le débit peut être très modeste.</span><span class="sxs-lookup"><span data-stu-id="57d40-106">Between these peaks, the throughput can be very low.</span></span> <span data-ttu-id="57d40-107">Voici quelques exemples de ces scénarios :</span><span class="sxs-lookup"><span data-stu-id="57d40-107">Examples of these types of scenarios include:</span></span>  
  
-   <span data-ttu-id="57d40-108">les opérations sur les actions, à l'ouverture et à la clôture du marché ;</span><span class="sxs-lookup"><span data-stu-id="57d40-108">Equity trading, for example, at market open and market close</span></span>  
  
-   <span data-ttu-id="57d40-109">les systèmes bancaires, par exemple pendant le rapprochement des transactions en fin de journée.</span><span class="sxs-lookup"><span data-stu-id="57d40-109">Banking systems, for example, during end of day transaction reconciliation</span></span>  
  
 <span data-ttu-id="57d40-110">D'autres types d'événements peuvent causer des retards similaires à ceux provoqués par les événements de saturation.</span><span class="sxs-lookup"><span data-stu-id="57d40-110">Other types of events can cause backlog behavior similar to floodgate events.</span></span> <span data-ttu-id="57d40-111">Par exemple, si l'adresse d'envoi d'un partenaire devient indisponible et que les messages destinés à cette adresse doivent être renvoyés et/ou suspendus, cela peut entraîner une accumulation de travaux en retard.</span><span class="sxs-lookup"><span data-stu-id="57d40-111">For example, if a partner send address goes off line so that messages destined for that address must be re-tried and/or suspended, this can result in backlog building up.</span></span> <span data-ttu-id="57d40-112">Quand le partenaire est à nouveau connecté, il risque d'y avoir un volume considérable de messages suspendus qu'il faut reprendre, ce qui génère un autre type d'événement de saturation.</span><span class="sxs-lookup"><span data-stu-id="57d40-112">When the partner comes back on line, there may be a large number of suspended messages that need to be resumed, resulting in another type of floodgate event.</span></span> <span data-ttu-id="57d40-113">Le test suivant du système illustre ce fonctionnement :</span><span class="sxs-lookup"><span data-stu-id="57d40-113">The following test of the system illustrates this behavior.</span></span>  
  
## <a name="simulating-a-floodgate-event"></a><span data-ttu-id="57d40-114">Simulation d'un événement de saturation</span><span class="sxs-lookup"><span data-stu-id="57d40-114">Simulating a Floodgate Event</span></span>  
 <span data-ttu-id="57d40-115">Pour ce test, le système a fonctionné initialement à la moitié environ de son débit maximum et était donc très stable.</span><span class="sxs-lookup"><span data-stu-id="57d40-115">For this test, the system was initially driven at around half the maximum sustainable throughput which of course was very stable.</span></span> <span data-ttu-id="57d40-116">Ensuite, pour simuler un événement de saturation, l'outil de génération de charge a été configuré afin d'envoyer 410 msg/s environ pendant un temps très court (le même que pour le test de surcharge).</span><span class="sxs-lookup"><span data-stu-id="57d40-116">Then, to simulate a floodgate event, the load generation tool was configured to send in about 410 msgs/sec for a short period of time (the same as for the overdrive test).</span></span> <span data-ttu-id="57d40-117">Le profil de charge obtenu, qui mesure les messages reçus par seconde et la profondeur du spouleur, est affiché ci-après.</span><span class="sxs-lookup"><span data-stu-id="57d40-117">The resultant load profile measuring messages received per second and spool depth is displayed below.</span></span>  
  
 <span data-ttu-id="57d40-118">**Profil de charge du test de charge de saturation**</span><span class="sxs-lookup"><span data-stu-id="57d40-118">**Load profile of floodgate load test**</span></span>  
  
 <span data-ttu-id="57d40-119">![Moniteur de performances de l’état de saturation](../core/media/bts06-floodgate-load.gif "BTS06_Floodgate_Load")</span><span class="sxs-lookup"><span data-stu-id="57d40-119">![Performance monitor display of floodgate load](../core/media/bts06-floodgate-load.gif "BTS06_Floodgate_Load")</span></span>  
  
 <span data-ttu-id="57d40-120">Notez que dans les tables de mise en file d'attente, le nombre de messages en attente de traitement augmente très vite pendant l'événement de saturation.</span><span class="sxs-lookup"><span data-stu-id="57d40-120">Note from the graph that the spool tables quickly built up a backlog during the floodgate event.</span></span> <span data-ttu-id="57d40-121">Toutefois, l'événement étant relativement court et le taux de réception après l'événement inférieur au taux maximal, les fonctions de nettoyage ont pu s'exécuter et le système a pu récupérer de l'événement sans qu'il soit nécessaire d'interrompre la réception des messages.</span><span class="sxs-lookup"><span data-stu-id="57d40-121">However, because the event was relatively short lived and the subsequent receive rate after the event was below the maximum sustainable rate, the cleanup jobs were able to run and recover from the event without requiring a system receive outage.</span></span> <span data-ttu-id="57d40-122">Pour ce test particulier, qui a duré 45 minutes environ, la base de données MessageBox était hébergée par SQL Server 2005.</span><span class="sxs-lookup"><span data-stu-id="57d40-122">For this particular test, the MessageBox was housed on SQL Server 2005; the duration of this test from beginning to end was approximately 45 minutes.</span></span>  
  
 <span data-ttu-id="57d40-123">Bien sûr, chaque système est différent, et les « valeurs limites » varieront de l'un à l'autre.</span><span class="sxs-lookup"><span data-stu-id="57d40-123">Of course, every system is different, so "your mileage will vary."</span></span> <span data-ttu-id="57d40-124">Le meilleur moyen de vérifier qu'une récupération est possible consiste à faire un test avec une charge représentative avant le passage en production.</span><span class="sxs-lookup"><span data-stu-id="57d40-124">The best way to verify that you can recover is to test with a representative load before going into production.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57d40-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="57d40-125">See Also</span></span>  
 <span data-ttu-id="57d40-126">[Scénarios de test pour mesurer le débit maximal acceptable du moteur](../core/test-scenarios-for-measuring-mst-of-the-engine.md) </span><span class="sxs-lookup"><span data-stu-id="57d40-126">[Test Scenarios for Measuring MST of the Engine](../core/test-scenarios-for-measuring-mst-of-the-engine.md) </span></span>  
 <span data-ttu-id="57d40-127">[À l’aide du Panneau de configuration de BizTalk Server réglage des performances](../core/using-settings-dashboard-for-biztalk-server-performance-tuning.md) </span><span class="sxs-lookup"><span data-stu-id="57d40-127">[Using Settings Dashboard for BizTalk Server Performance Tuning](../core/using-settings-dashboard-for-biztalk-server-performance-tuning.md) </span></span>  
 <span data-ttu-id="57d40-128">[Test de surcharge](../core/overdrive-load-test.md) </span><span class="sxs-lookup"><span data-stu-id="57d40-128">[Overdrive Load Test](../core/overdrive-load-test.md) </span></span>  
 [<span data-ttu-id="57d40-129">Test de charge maximale</span><span class="sxs-lookup"><span data-stu-id="57d40-129">Sustainable Load Test</span></span>](../core/sustainable-load-test.md)