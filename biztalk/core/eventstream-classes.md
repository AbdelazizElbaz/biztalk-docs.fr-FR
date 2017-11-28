---
title: Classes EventStream | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a3e7a6b3-69cc-4312-9074-acccd1175d37
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 89eafdced54927007bcc8dfc02e4834641e2ae2f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="eventstream-classes"></a><span data-ttu-id="c7ea3-102">Classes EventStream</span><span class="sxs-lookup"><span data-stu-id="c7ea3-102">EventStream Classes</span></span>
<span data-ttu-id="c7ea3-103">Les API EventStream de l'analyse BAM résident dans l'espace de noms Microsoft.BizTalk.BAM.EventObservation.</span><span class="sxs-lookup"><span data-stu-id="c7ea3-103">The EventStream APIs for BAM reside in the Microsoft.BizTalk.BAM.EventObservation namespace.</span></span> <span data-ttu-id="c7ea3-104">Pour coder ces API, vous devez installer les DLL suivantes sur votre ordinateur de développement :</span><span class="sxs-lookup"><span data-stu-id="c7ea3-104">To code against the APIs, you must install the following DLLs on your development computer:</span></span>  
  
-   <span data-ttu-id="c7ea3-105">Microsoft.BizTalk.BAM.EventObservation.dll</span><span class="sxs-lookup"><span data-stu-id="c7ea3-105">Microsoft.BizTalk.BAM.EventObservation.dll</span></span>  
  
-   <span data-ttu-id="c7ea3-106">Microsoft.Biztalk.BAM.Xlangs.dll : Cette DLL est requise lors du codage pour les flux d’événements d’Orchestration.</span><span class="sxs-lookup"><span data-stu-id="c7ea3-106">Microsoft.Biztalk.BAM.Xlangs.dll: This DLL is required when coding for Orchestration event streams.</span></span>  
  
-   <span data-ttu-id="c7ea3-107">Microsoft.BizTalk.Pipeline.dll : Cette DLL est requise lors de l’utilisation de contextes de pipeline de codage pour le flux d’événements de messagerie.</span><span class="sxs-lookup"><span data-stu-id="c7ea3-107">Microsoft.BizTalk.Pipeline.dll: This DLL required when using coding pipeline contexts for Messaging event streams.</span></span>  
  
 <span data-ttu-id="c7ea3-108">Ajoutez la DLL à votre référence de projet et incluez l'espace de noms dans votre code à l'aide de l'instruction using suivante :</span><span class="sxs-lookup"><span data-stu-id="c7ea3-108">Add the DLL to your project reference and include the namespace in your code with the following using statement:</span></span>  
  
```  
using Microsoft.BizTalk.Bam.EventObservation;  
```  
  
 <span data-ttu-id="c7ea3-109">**Classes**</span><span class="sxs-lookup"><span data-stu-id="c7ea3-109">**Classes**</span></span>  
  
|<span data-ttu-id="c7ea3-110">Nom</span><span class="sxs-lookup"><span data-stu-id="c7ea3-110">Name</span></span>|<span data-ttu-id="c7ea3-111"> Description</span><span class="sxs-lookup"><span data-stu-id="c7ea3-111">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="c7ea3-112">DirectEventStream (DES)</span><span class="sxs-lookup"><span data-stu-id="c7ea3-112">DirectEventStream (DES)</span></span>|<span data-ttu-id="c7ea3-113">Synchrone, pas de latence</span><span class="sxs-lookup"><span data-stu-id="c7ea3-113">Synchronous, no latency</span></span>|  
|<span data-ttu-id="c7ea3-114">BufferedEventStream (BES)</span><span class="sxs-lookup"><span data-stu-id="c7ea3-114">BufferedEventStream (BES)</span></span>|<span data-ttu-id="c7ea3-115">Asynchrone, débit élevé, certaine latence</span><span class="sxs-lookup"><span data-stu-id="c7ea3-115">Asynchronous, high throughput, some latency</span></span>|  
|<span data-ttu-id="c7ea3-116">OrchestrationEventStream (OES)</span><span class="sxs-lookup"><span data-stu-id="c7ea3-116">OrchestrationEventStream (OES)</span></span>|<span data-ttu-id="c7ea3-117">Asynchrone, participe aux transactions d'orchestration BizTalk</span><span class="sxs-lookup"><span data-stu-id="c7ea3-117">Asynchronous, participates in BizTalk orchestration transactions</span></span>|  
|<span data-ttu-id="c7ea3-118">Interface IPipelineContext</span><span class="sxs-lookup"><span data-stu-id="c7ea3-118">IPipelineContext Interface</span></span>|<span data-ttu-id="c7ea3-119">Asynchrone, participe aux transactions de pipeline BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="c7ea3-119">Asynchronous, participates in BizTalk Server pipeline transactions.</span></span> <span data-ttu-id="c7ea3-120">Permet de créer des flux d'événements de messagerie (MES).</span><span class="sxs-lookup"><span data-stu-id="c7ea3-120">Used to create Messaging Event Streams (MES).</span></span>|  
  
 <span data-ttu-id="c7ea3-121">Vous devez choisir une API en fonction des facteurs suivants :</span><span class="sxs-lookup"><span data-stu-id="c7ea3-121">You should choose an API based on the following factors:</span></span>  
  
-   <span data-ttu-id="c7ea3-122">Si votre préoccupation est la latence, choisissez DES, les données étant conservées de manière synchrone dans la base de données d'importation principale BAM.</span><span class="sxs-lookup"><span data-stu-id="c7ea3-122">If your concern is latency, choose DES, where data is persisted synchronously to the BAM Primary Import database.</span></span> <span data-ttu-id="c7ea3-123">À l'exception de DES, toutes les autres classes EventStream sont asynchrones et ont une latence.</span><span class="sxs-lookup"><span data-stu-id="c7ea3-123">Except for DES, all other EventStream classes are asynchronous and have some latency.</span></span> <span data-ttu-id="c7ea3-124">Les données sont d'abord conservées dans MessageBox, puis traitées par TDDS qui les déplace vers la base de données BAMPrimaryImport.</span><span class="sxs-lookup"><span data-stu-id="c7ea3-124">The data is first persisted to MessageBox and subsequently processed by TDDS which moves data into the BAMPrimaryImport database.</span></span>  
  
-   <span data-ttu-id="c7ea3-125">Si votre préoccupation est la performance et la capacité d'insertion des événements, choisissez une API asynchrone.</span><span class="sxs-lookup"><span data-stu-id="c7ea3-125">If your concern is performance and throughput of event insertion, choose an asynchronous API.</span></span>  
  
-   <span data-ttu-id="c7ea3-126">Si vous écrivez une application qui s'exécute sur un ordinateur sur lequel BizTalk Server n'est pas installé, utilisez DES et BES.</span><span class="sxs-lookup"><span data-stu-id="c7ea3-126">If you are writing an application that runs on a computer that does not have BizTalk Server installed, use DES and BES.</span></span> <span data-ttu-id="c7ea3-127">(En d'autres termes, ces API peuvent être utilisées dans des applications non-BizTalk.)</span><span class="sxs-lookup"><span data-stu-id="c7ea3-127">(In other words, these APIs can be used in non-BizTalk applications.)</span></span>  
  
-   <span data-ttu-id="c7ea3-128">Si votre application s'exécute sur un ordinateur sur lequel BizTalk Server est installé, utilisez MES et OES.</span><span class="sxs-lookup"><span data-stu-id="c7ea3-128">If your application runs on a computer on which BizTalk Server is installed, use MES and OES.</span></span> <span data-ttu-id="c7ea3-129">(Ces API sont uniquement disponibles à partir des applications BizTalk.)</span><span class="sxs-lookup"><span data-stu-id="c7ea3-129">(These APIs are available only from BizTalk applications.)</span></span>  
  
    -   <span data-ttu-id="c7ea3-130">Si vous souhaitez que la persistance d'événement BAM soit synchronisée avec la transaction de pipeline, utilisez un flux d'événements de messagerie.</span><span class="sxs-lookup"><span data-stu-id="c7ea3-130">If you want BAM event persistence to be in sync with pipeline transaction, you should use a Messaging Event Stream.</span></span>  
  
    -   <span data-ttu-id="c7ea3-131">OES est l'équivalent de MES, mais pour les orchestrations BizTalk.</span><span class="sxs-lookup"><span data-stu-id="c7ea3-131">OES is the equivalent of MES but for BizTalk orchestrations.</span></span>  
  
 <span data-ttu-id="c7ea3-132">Il existe des scénarios dans lesquels vous pouvez combiner plusieurs types EventStream.</span><span class="sxs-lookup"><span data-stu-id="c7ea3-132">There are scenarios in which you may want to mix EventStream types.</span></span> <span data-ttu-id="c7ea3-133">Par exemple, dans un traitement de pipeline, vous pouvez capturer les données spécifiques de l'analyse BAM que le pipeline restaure ou non sa transaction.</span><span class="sxs-lookup"><span data-stu-id="c7ea3-133">For example, in a pipeline processing, you may want to capture the particular data in BAM regardless of whether the pipeline is rolling back its transaction.</span></span> <span data-ttu-id="c7ea3-134">Plus précisément, vous pouvez capturer des données sur le nombre de messages dont le traitement à échoué ou le nombre de tentatives lors du traitement de pipeline.</span><span class="sxs-lookup"><span data-stu-id="c7ea3-134">In particular, you may want capture data about how many messages failed or how many retries there were during pipeline processing.</span></span> <span data-ttu-id="c7ea3-135">Pour capturer les données dans ce cas précis, vous devez utiliser BES.</span><span class="sxs-lookup"><span data-stu-id="c7ea3-135">To capture the data in this situation you should use BES.</span></span>  
  
 <span data-ttu-id="c7ea3-136">Tous les flux d'événements asynchrones (BES, MES et OES) conservent d'abord les données dans la base de données MessageBox BizTalk.</span><span class="sxs-lookup"><span data-stu-id="c7ea3-136">All the asynchronous EventStreams (BES, MES, and OES) persist data first in the BizTalk MessageBox database.</span></span> <span data-ttu-id="c7ea3-137">Régulièrement, les données sont traitées et rendues persistantes dans la base de données Importation principale BAM par le service TDDS (Tracking Data Decode Service).</span><span class="sxs-lookup"><span data-stu-id="c7ea3-137">Periodically the data is processed and persisted to the BAM Primary Import database by the Tracking Data Decode Service (TDDS).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c7ea3-138">Pour s'assurer que les appels EventStream ne créent pas de goulot d'étranglement à partir d'une application BizTalk, nous vous recommandons d'utiliser des API asynchrones.</span><span class="sxs-lookup"><span data-stu-id="c7ea3-138">To ensure that EventStream calls do not create a bottleneck from a BizTalk application, we recommend that you use asynchronous APIs.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c7ea3-139">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="c7ea3-139">In This Section</span></span>  
  
-   [<span data-ttu-id="c7ea3-140">OrchestrationEventStream</span><span class="sxs-lookup"><span data-stu-id="c7ea3-140">OrchestrationEventStream</span></span>](../core/orchestrationeventstream.md)  
  
-   [<span data-ttu-id="c7ea3-141">Flux d’événements de messagerie</span><span class="sxs-lookup"><span data-stu-id="c7ea3-141">Messaging Event Streams</span></span>](../core/messaging-event-streams.md)