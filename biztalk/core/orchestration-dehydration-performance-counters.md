---
title: "Compteurs de performances de mise en attente d’orchestration | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3ab92e0e-6a33-4aaa-ab14-0c82322b04d5
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4e81052f0061ff4ad802a084536c09d48cb6cb55
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="orchestration-dehydration-performance-counters"></a><span data-ttu-id="4b2f2-102">Compteurs de performances de la mise en attente des orchestrations</span><span class="sxs-lookup"><span data-stu-id="4b2f2-102">Orchestration Dehydration Performance Counters</span></span>
<span data-ttu-id="4b2f2-103">Le tableau suivant répertorie les noms des compteurs de performance du moteur d'orchestration propres à la surveillance du comportement de mise en attente.</span><span class="sxs-lookup"><span data-stu-id="4b2f2-103">The following table lists the names of Orchestration Engine performance counters that are specific to monitoring the behavior of dehydration.</span></span> <span data-ttu-id="4b2f2-104">Servez-vous de l'Analyseur de performances pour observer ces compteurs pendant le réglage des paramètres de mise en attente.</span><span class="sxs-lookup"><span data-stu-id="4b2f2-104">Use Performance Monitor to watch these counters while tuning your dehydration parameters.</span></span>  
  
|<span data-ttu-id="4b2f2-105">Compteurs de performance de la mise en attente</span><span class="sxs-lookup"><span data-stu-id="4b2f2-105">Dehydration Performance Counter</span></span>|<span data-ttu-id="4b2f2-106">Description</span><span class="sxs-lookup"><span data-stu-id="4b2f2-106">Description</span></span>|  
|-------------------------------------|-----------------|  
|<span data-ttu-id="4b2f2-107">Orchestrations pouvant être en attente</span><span class="sxs-lookup"><span data-stu-id="4b2f2-107">Dehydratable orchestrations</span></span>|<span data-ttu-id="4b2f2-108">Nombre d'instances d'orchestration pouvant être mises en attente et actuellement hébergées par l'instance de l'hôte.</span><span class="sxs-lookup"><span data-stu-id="4b2f2-108">Number of orchestrations instances that can be dehydrated which are currently hosted by the host instance.</span></span>|  
|<span data-ttu-id="4b2f2-109">Mise en attente des orchestrations</span><span class="sxs-lookup"><span data-stu-id="4b2f2-109">Dehydrating orchestrations</span></span>|<span data-ttu-id="4b2f2-110">Nombre d'orchestrations qui se trouvent dans le processus de mise en attente.</span><span class="sxs-lookup"><span data-stu-id="4b2f2-110">Number of orchestrations that are in the process of dehydrating.</span></span>|  
|<span data-ttu-id="4b2f2-111">Cycle de mise en attente en cours</span><span class="sxs-lookup"><span data-stu-id="4b2f2-111">Dehydration cycle in progress</span></span>|<span data-ttu-id="4b2f2-112">Indique s'il y a un cycle de mise en attente actuellement en cours.</span><span class="sxs-lookup"><span data-stu-id="4b2f2-112">Indicates whether there is a dehydration cycle currently in progress.</span></span>|  
|<span data-ttu-id="4b2f2-113">Cycles de mise en attente</span><span class="sxs-lookup"><span data-stu-id="4b2f2-113">Dehydration cycles</span></span>|<span data-ttu-id="4b2f2-114">Nombre de cycles de mise en attente réussis.</span><span class="sxs-lookup"><span data-stu-id="4b2f2-114">Number of dehydration cycles completed.</span></span>|  
|<span data-ttu-id="4b2f2-115">Seuil de mise en attente</span><span class="sxs-lookup"><span data-stu-id="4b2f2-115">Dehydration threshold</span></span>|<span data-ttu-id="4b2f2-116">Nombre, en millisecondes, qui détermine la rapidité avec laquelle les orchestrations sont mises en attente.</span><span class="sxs-lookup"><span data-stu-id="4b2f2-116">Number in milliseconds that determines how aggressively orchestrations are being dehydrated.</span></span> <span data-ttu-id="4b2f2-117">Si le moteur d'orchestration prévoit qu'une instance pourra être mise en attente dans un délai supérieur à ce seuil, il la met en attente.</span><span class="sxs-lookup"><span data-stu-id="4b2f2-117">If the orchestration engine predicts that an instance will be dehydratable for an amount of time longer than this threshold, it will dehydrate the instance.</span></span>|  
|<span data-ttu-id="4b2f2-118">Orchestrations dehydrated (Orchestrations mises en attente)</span><span class="sxs-lookup"><span data-stu-id="4b2f2-118">Orchestrations dehydrated</span></span>|<span data-ttu-id="4b2f2-119">Nombre d'instances d'orchestration mises en attente depuis le démarrage de l'instance de l'hôte.</span><span class="sxs-lookup"><span data-stu-id="4b2f2-119">Number of orchestration instances dehydrated since the host instance started.</span></span>|  
|<span data-ttu-id="4b2f2-120">Orchestrations dehydrated/sec (Orchestrations mises en attente par seconde)</span><span class="sxs-lookup"><span data-stu-id="4b2f2-120">Orchestrations dehydrated/sec</span></span>|<span data-ttu-id="4b2f2-121">Nombre moyen d'orchestrations mises en attente par seconde.</span><span class="sxs-lookup"><span data-stu-id="4b2f2-121">Average number dehydrated per second.</span></span>|  
|<span data-ttu-id="4b2f2-122">Orchestrations rehydrated (Orchestrations réalimentées)</span><span class="sxs-lookup"><span data-stu-id="4b2f2-122">Orchestrations rehydrated</span></span>|<span data-ttu-id="4b2f2-123">Nombre d'instances d'orchestration réalimentées depuis le démarrage de l'instance de l'hôte.</span><span class="sxs-lookup"><span data-stu-id="4b2f2-123">Number of orchestration instances rehydrated since the host instance started.</span></span>|  
|<span data-ttu-id="4b2f2-124">Orchestrations rehydrated/sec (Orchestrations réalimentées par seconde)</span><span class="sxs-lookup"><span data-stu-id="4b2f2-124">Orchestrations rehydrated/sec</span></span>|<span data-ttu-id="4b2f2-125">Nombre moyen d'orchestrations réalimentées par seconde</span><span class="sxs-lookup"><span data-stu-id="4b2f2-125">Average number rehydrated per second</span></span>|  
|<span data-ttu-id="4b2f2-126">Orchestrations avec mise en attente planifiée</span><span class="sxs-lookup"><span data-stu-id="4b2f2-126">Orchestrations scheduled for dehydration</span></span>|<span data-ttu-id="4b2f2-127">Nombre d'orchestrations pouvant être mises en attente pour lesquelles une requête de mise en attente est en cours.</span><span class="sxs-lookup"><span data-stu-id="4b2f2-127">Number of dehydratable orchestrations for which there is a dehydration request pending.</span></span>|