---
title: Compteurs de Performance BAM | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing [BAM], performance counters
- performance, counters [BAM]
ms.assetid: e23f7038-36a5-4957-bc73-47011763d109
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4307f72f149405fbc04e4e6cc51efe87229c2bff
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="bam-performance-counters"></a><span data-ttu-id="5e957-102">Compteurs de performances BAM</span><span class="sxs-lookup"><span data-stu-id="5e957-102">BAM Performance Counters</span></span>
<span data-ttu-id="5e957-103">Les compteurs de performance vous permettent d'analyser des aspects spécifiques du travail effectué par le service Bus d'événements BAM.</span><span class="sxs-lookup"><span data-stu-id="5e957-103">Performance counters allow you to monitor specific aspects of work performed by the BAM Event Bus Service.</span></span> <span data-ttu-id="5e957-104">Ils peuvent vous aider à identifier et à résoudre des problèmes de performances de serveur.</span><span class="sxs-lookup"><span data-stu-id="5e957-104">Performance counters can help you identify and troubleshoot server performance issues.</span></span>  
  
 <span data-ttu-id="5e957-105">Le tableau suivant répertorie les compteurs de performance disponibles dans l'analyse BAM.</span><span class="sxs-lookup"><span data-stu-id="5e957-105">The following table lists the performance counters available in Business Activity Monitoring.</span></span>  
  
|<span data-ttu-id="5e957-106">Compteur</span><span class="sxs-lookup"><span data-stu-id="5e957-106">Counter</span></span>|<span data-ttu-id="5e957-107"> Description</span><span class="sxs-lookup"><span data-stu-id="5e957-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5e957-108">Événements traités</span><span class="sxs-lookup"><span data-stu-id="5e957-108">Events being processed</span></span>|<span data-ttu-id="5e957-109">Nombre d'événements que le service Bus d'événements BAM est en train de traiter.</span><span class="sxs-lookup"><span data-stu-id="5e957-109">The number of events the BAM Event Bus Service is currently processing</span></span>|  
|<span data-ttu-id="5e957-110">Lots traités</span><span class="sxs-lookup"><span data-stu-id="5e957-110">Batches being processed</span></span>|<span data-ttu-id="5e957-111">Nombre de lots que le service Bus d'événements BAM est en train de traiter.</span><span class="sxs-lookup"><span data-stu-id="5e957-111">The number of batches the BAM Event Bus Service is currently processing</span></span>|  
|<span data-ttu-id="5e957-112">Événements validés</span><span class="sxs-lookup"><span data-stu-id="5e957-112">Events Committed</span></span>|<span data-ttu-id="5e957-113">Nombre d'événements que le service Bus d'événements BAM a validés dans SQL Server durant la seconde écoulée.</span><span class="sxs-lookup"><span data-stu-id="5e957-113">The number of events the BAM Event Bus Service has committed to SQL Server in the last second.</span></span>|  
|<span data-ttu-id="5e957-114">Enregistrements validés</span><span class="sxs-lookup"><span data-stu-id="5e957-114">Records Committed</span></span>|<span data-ttu-id="5e957-115">Nombre d'enregistrements que le service Bus d'événements BAM a validés dans SQL Server durant la seconde écoulée.</span><span class="sxs-lookup"><span data-stu-id="5e957-115">The number of records the BAM Event Bus Service has committed to SQL Server in the last second.</span></span>|  
|<span data-ttu-id="5e957-116">Lots validés</span><span class="sxs-lookup"><span data-stu-id="5e957-116">Batches Committed</span></span>|<span data-ttu-id="5e957-117">Nombre de lots que le service Bus d'événements BAM a validés dans SQL Server durant la seconde écoulée.</span><span class="sxs-lookup"><span data-stu-id="5e957-117">The number of batches the BAM Event Bus Service has committed to SQL Server in the last second.</span></span>|  
|<span data-ttu-id="5e957-118">Nombre total d'événements</span><span class="sxs-lookup"><span data-stu-id="5e957-118">Total Events</span></span>|<span data-ttu-id="5e957-119">Nombre d'événements que le service Bus d'événements BAM a traités depuis que vous l'avez lancé.</span><span class="sxs-lookup"><span data-stu-id="5e957-119">The number of events the BAM Event Bus Service has processed since you started it.</span></span>|  
|<span data-ttu-id="5e957-120">Nombre total d'enregistrements</span><span class="sxs-lookup"><span data-stu-id="5e957-120">Total Records</span></span>|<span data-ttu-id="5e957-121">Nombre d'enregistrements que le service Bus d'événements BAM a traités depuis que vous l'avez lancé.</span><span class="sxs-lookup"><span data-stu-id="5e957-121">Then number of records the BAM Event Bus Service has processed since you started it.</span></span>|  
|<span data-ttu-id="5e957-122">Nombre total de lots</span><span class="sxs-lookup"><span data-stu-id="5e957-122">Total Batches</span></span>|<span data-ttu-id="5e957-123">Nombre de lots que le service Bus d'événements BAM a traités depuis que vous l'avez lancé.</span><span class="sxs-lookup"><span data-stu-id="5e957-123">Then number of batches the BAM Event Bus Service has processed since you started it.</span></span>|  
|<span data-ttu-id="5e957-124">Nombre total échec de lots</span><span class="sxs-lookup"><span data-stu-id="5e957-124">Total Failed Batches</span></span>|<span data-ttu-id="5e957-125">Nombre de lots que le service Bus d'événements BAM n'a pas correctement traités depuis que vous l'avez lancé.</span><span class="sxs-lookup"><span data-stu-id="5e957-125">Then number of batches the BAM Event Bus Service has failed to process since you started it.</span></span>|  
|<span data-ttu-id="5e957-126">Nombre total échec d'événements</span><span class="sxs-lookup"><span data-stu-id="5e957-126">Total Failed Events</span></span>|<span data-ttu-id="5e957-127">Nombre d'événements que le service Bus d'événements BAM n'a pas correctement traités depuis que vous l'avez lancé.</span><span class="sxs-lookup"><span data-stu-id="5e957-127">Then number of events the BAM Event Bus Service has failed to process since you started it.</span></span>|  
  
 <span data-ttu-id="5e957-128">Les compteurs de performance sont situés dans l'Analyseur de performances (perfmon), sous l'objet de performance BizTalk:TDDS.</span><span class="sxs-lookup"><span data-stu-id="5e957-128">The performance counters are located in the Performance Monitor (perfmon) under the BizTalk:TDDS performance object.</span></span> <span data-ttu-id="5e957-129">Le nom d'instance des compteurs de performance est une combinaison du nom de serveur source et du nom de la base de données source.</span><span class="sxs-lookup"><span data-stu-id="5e957-129">The instance name of the performance counters are a combination of the source server name and the name of the source database.</span></span> <span data-ttu-id="5e957-130">Si deux des services Bus d'événements BAM sont exécutés sur le même ordinateur pour deux bases de données source différentes, vous aurez deux instances des compteurs du service Bus d'événements BAM.</span><span class="sxs-lookup"><span data-stu-id="5e957-130">If two of the BAM Event Bus Services are running on the same computer against two different source databases, you will see two instances of the BAM Event Bus Service counters.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e957-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5e957-131">See Also</span></span>  
 <span data-ttu-id="5e957-132">[La gestion de Service Bus d’événements BAM](../core/managing-the-bam-event-bus-service.md) </span><span class="sxs-lookup"><span data-stu-id="5e957-132">[Managing the BAM Event Bus Service](../core/managing-the-bam-event-bus-service.md) </span></span>  
 <span data-ttu-id="5e957-133">[Recommandations de sécurité BAM](../core/bam-security-recommendations.md) </span><span class="sxs-lookup"><span data-stu-id="5e957-133">[BAM Security Recommendations](../core/bam-security-recommendations.md) </span></span>  
 [<span data-ttu-id="5e957-134">La gestion BAM</span><span class="sxs-lookup"><span data-stu-id="5e957-134">Managing BAM</span></span>](../core/managing-bam.md)