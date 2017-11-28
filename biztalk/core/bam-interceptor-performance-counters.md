---
title: "Compteurs de Performance de l’intercepteur BAM | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b9b64ae1-4d94-4c3c-add1-fa020713be5c
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 989316edff34463905c7547db815b3daaf4d4a46
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="bam-interceptor-performance-counters"></a><span data-ttu-id="aec68-102">Compteurs de performance de l'intercepteur BAM</span><span class="sxs-lookup"><span data-stu-id="aec68-102">BAM Interceptor Performance Counters</span></span>
<span data-ttu-id="aec68-103">Les compteurs de performance vous permettent d'analyser des aspects spécifiques du travail effectué par les intercepteurs BAM.</span><span class="sxs-lookup"><span data-stu-id="aec68-103">Performance counters allow you to monitor specific aspects of work performed by the BAM interceptors.</span></span> <span data-ttu-id="aec68-104">Ils peuvent vous aider à identifier et à résoudre des problèmes de performances de serveur.</span><span class="sxs-lookup"><span data-stu-id="aec68-104">Performance counters can help you identify and troubleshoot server performance issues.</span></span>  
  
 <span data-ttu-id="aec68-105">Le tableau suivant répertorie les compteurs de performance disponibles pour les intercepteurs BAM.</span><span class="sxs-lookup"><span data-stu-id="aec68-105">The following table lists the performance counters available for the BAM interceptors.</span></span> <span data-ttu-id="aec68-106">La catégorie des compteurs de performance est « Intercepteur BAM ».</span><span class="sxs-lookup"><span data-stu-id="aec68-106">The performance counters category is “BAM Interceptor.”</span></span>  
  
|<span data-ttu-id="aec68-107">Compteur</span><span class="sxs-lookup"><span data-stu-id="aec68-107">Counter</span></span>|<span data-ttu-id="aec68-108"> Description</span><span class="sxs-lookup"><span data-stu-id="aec68-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="aec68-109">Nombre moyen Moyenne de vidage/des événements BAM ayant échoué</span><span class="sxs-lookup"><span data-stu-id="aec68-109">Avg. Failed BAM Events/Flush Avg</span></span>|<span data-ttu-id="aec68-110">Nombre moyen d'événements BAM ayant échoué pendant une opération de vidage de données dans la base de données d'importation principale.</span><span class="sxs-lookup"><span data-stu-id="aec68-110">The average number of failed BAM events that occurred during a flush of data to the Primary Import database.</span></span>|  
|<span data-ttu-id="aec68-111">Réussites événements BAM/vidage</span><span class="sxs-lookup"><span data-stu-id="aec68-111">Successful BAM Events/Flush</span></span>|<span data-ttu-id="aec68-112">Nombre moyen d'événements BAM ayant réussi pendant une opération de vidage de données dans la base de données d'importation principale.</span><span class="sxs-lookup"><span data-stu-id="aec68-112">The average number of successful BAM events that occurred during a data flush to the Primary Import database.</span></span> <span data-ttu-id="aec68-113">Si la transaction est annulée, ces événements ne seront pas conservés dans la base de données.</span><span class="sxs-lookup"><span data-stu-id="aec68-113">The events may not be persisted to the database if the transaction is rolled back.</span></span>|  
|<span data-ttu-id="aec68-114">Nombre moyen Extraction s/BAM événement</span><span class="sxs-lookup"><span data-stu-id="aec68-114">Avg. Extraction sec/BAM Event</span></span>|<span data-ttu-id="aec68-115">Durée moyenne d'extraction des événements BAM.</span><span class="sxs-lookup"><span data-stu-id="aec68-115">The average amount of time spent extracting BAM events.</span></span>|  
|<span data-ttu-id="aec68-116">Nombre moyen Vider s/BAM événement</span><span class="sxs-lookup"><span data-stu-id="aec68-116">Avg. Flush sec/BAM Event</span></span>|<span data-ttu-id="aec68-117">Durée moyenne de vidage des événements BAM.</span><span class="sxs-lookup"><span data-stu-id="aec68-117">The average amount of time spent flushing BAM events.</span></span>|  
|<span data-ttu-id="aec68-118">Total échecs événements BAM pendant vidage</span><span class="sxs-lookup"><span data-stu-id="aec68-118">Total Failed BAM Events During Flush</span></span>|<span data-ttu-id="aec68-119">Nombre total d'événements BAM ayant échoué au cours de l'opération de vidage de données</span><span class="sxs-lookup"><span data-stu-id="aec68-119">The total number of failed BAM events that occurred during the data flush</span></span>|  
|<span data-ttu-id="aec68-120">Total réussite événements BAM pendant vidage</span><span class="sxs-lookup"><span data-stu-id="aec68-120">Total Successful BAM Events During Flush</span></span>|<span data-ttu-id="aec68-121">Nombre total d'événements BAM ayant réussi pendant l'opération de vidage dans la base de données d'importation principale.</span><span class="sxs-lookup"><span data-stu-id="aec68-121">The total number of successful BAM events flushed to the Primary Import database.</span></span> <span data-ttu-id="aec68-122">Si la transaction est annulée, ces événements ne seront pas conservés dans la base de données.</span><span class="sxs-lookup"><span data-stu-id="aec68-122">The events may not be persisted to the database if the transaction is rolled back.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="aec68-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="aec68-123">See Also</span></span>  
 [<span data-ttu-id="aec68-124">Compteurs de Performance BAM</span><span class="sxs-lookup"><span data-stu-id="aec68-124">BAM Performance Counters</span></span>](../core/bam-performance-counters.md)