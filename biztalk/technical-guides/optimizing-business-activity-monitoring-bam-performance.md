---
title: "Optimisation de l’analyse des performances de (l’analyse BAM) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c9ed29b2-0be6-4a37-be68-9476832fd49f
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 83801a4e147b3e1eaf34c5e264d6adecfbdf8f9f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="optimizing-business-activity-monitoring-bam-performance"></a><span data-ttu-id="3534f-102">Optimisation de l’analyse des performances de l’analyse BAM)</span><span class="sxs-lookup"><span data-stu-id="3534f-102">Optimizing Business Activity Monitoring (BAM) Performance</span></span>
<span data-ttu-id="3534f-103">Cette rubrique décrit les facteurs de performances d’analyse BAM (Business Activity).</span><span class="sxs-lookup"><span data-stu-id="3534f-103">This topic describes Business Activity Monitoring (BAM) performance factors.</span></span>  
  
## <a name="bam-disk-usage-configuration"></a><span data-ttu-id="3534f-104">Configuration de l’utilisation de disque BAM</span><span class="sxs-lookup"><span data-stu-id="3534f-104">BAM disk usage configuration</span></span>  
 <span data-ttu-id="3534f-105">BAM entraîne une surcharge significative lorsqu’un système BizTalk est sous charge en raison de la quantité importante de données qui sont rendue persistante dans la base de données BAM.</span><span class="sxs-lookup"><span data-stu-id="3534f-105">BAM incurs significant overhead when a BizTalk system is under load because of the significant amount of data that is persisted to the BAM database.</span></span> <span data-ttu-id="3534f-106">Par conséquent, une utilisation judicieuse des techniques d’e/s disque pour la base de données BAM est extrêmement importante.</span><span class="sxs-lookup"><span data-stu-id="3534f-106">Therefore, judicious use of disk I/O techniques for the BAM database is critically important.</span></span>  
  
## <a name="bam-eventstream-apis"></a><span data-ttu-id="3534f-107">API EventStream BAM</span><span class="sxs-lookup"><span data-stu-id="3534f-107">BAM EventStream APIs</span></span>  
 <span data-ttu-id="3534f-108">Quatre types de flux d’événements sont disponibles pour une utilisation dans un scénario BizTalk BAM :</span><span class="sxs-lookup"><span data-stu-id="3534f-108">Four types of EventStreams are available for use in a BizTalk BAM scenario:</span></span>  
  
-   <span data-ttu-id="3534f-109">DirectEventStream (DES)</span><span class="sxs-lookup"><span data-stu-id="3534f-109">DirectEventStream (DES)</span></span>  
  
-   <span data-ttu-id="3534f-110">BufferedEventStream (BES)</span><span class="sxs-lookup"><span data-stu-id="3534f-110">BufferedEventStream (BES)</span></span>  
  
-   <span data-ttu-id="3534f-111">OrchestrationEventStream (OES)</span><span class="sxs-lookup"><span data-stu-id="3534f-111">OrchestrationEventStream (OES)</span></span>  
  
-   <span data-ttu-id="3534f-112">MessageEventStream (MES)</span><span class="sxs-lookup"><span data-stu-id="3534f-112">MessageEventStream (MES)</span></span>  
  
 <span data-ttu-id="3534f-113">Vous devez choisir une de ces API basées sur les facteurs suivants :</span><span class="sxs-lookup"><span data-stu-id="3534f-113">You should choose one of these APIs based on the following factors:</span></span>  
  
-   <span data-ttu-id="3534f-114">Si votre préoccupation est la latence, choisissez DES, les données étant conservées de manière synchrone dans la base de données d'importation principale BAM.</span><span class="sxs-lookup"><span data-stu-id="3534f-114">If your concern is latency, choose DES, where data is persisted synchronously to the BAM Primary Import database.</span></span>  
  
-   <span data-ttu-id="3534f-115">Si votre préoccupation est les performances et le débit d’insertion des événements, choisissez une API asynchrone (BES, OES ou MES).</span><span class="sxs-lookup"><span data-stu-id="3534f-115">If your concern is performance and throughput of event insertion, choose an asynchronous API (BES, OES or MES).</span></span>  
  
-   <span data-ttu-id="3534f-116">Si vous écrivez une application qui s’exécute sur un ordinateur qui n’a pas installé BizTalk Server, utilisez DES et BES ; Ces API peuvent être utilisées dans les applications non-BizTalk.</span><span class="sxs-lookup"><span data-stu-id="3534f-116">If you are writing an application that runs on a computer that does not have BizTalk Server installed, use DES and BES; these APIs can be used in non-BizTalk applications.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="3534f-117">Il existe des scénarios dans lesquels vous pouvez combiner plusieurs types EventStream.</span><span class="sxs-lookup"><span data-stu-id="3534f-117">There are scenarios in which you may want to mix EventStream types.</span></span> <span data-ttu-id="3534f-118">Par exemple, pour le traitement de pipeline, il pouvez que vous souhaitez capturer les données spécifiques de l’analyse BAM, indépendamment de si le pipeline est que sa transaction.</span><span class="sxs-lookup"><span data-stu-id="3534f-118">For example, for pipeline processing, you may want to capture the particular data in BAM regardless of whether the pipeline is rolling back its transaction.</span></span> <span data-ttu-id="3534f-119">En particulier, vous pouvez choisir de capturer des données sur le nombre de messages a échoué ou le nombre de tentatives s’est produite lors du traitement du pipeline.</span><span class="sxs-lookup"><span data-stu-id="3534f-119">In particular, you may want capture data about how many messages failed or how many retries occurred during pipeline processing.</span></span> <span data-ttu-id="3534f-120">Pour capturer les données dans ce cas précis, vous devez utiliser BES.</span><span class="sxs-lookup"><span data-stu-id="3534f-120">To capture the data in this situation you should use BES.</span></span>  
  
-   <span data-ttu-id="3534f-121">Si votre application s'exécute sur un ordinateur sur lequel BizTalk Server est installé, utilisez MES et OES.</span><span class="sxs-lookup"><span data-stu-id="3534f-121">If your application runs on a computer on which BizTalk Server is installed, use MES and OES.</span></span> <span data-ttu-id="3534f-122">(Ces API sont uniquement disponibles à partir des applications BizTalk.)</span><span class="sxs-lookup"><span data-stu-id="3534f-122">(These APIs are available only from BizTalk applications.)</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="3534f-123">OES est l'équivalent de MES, mais pour les orchestrations BizTalk.</span><span class="sxs-lookup"><span data-stu-id="3534f-123">OES is the equivalent of MES but for BizTalk orchestrations.</span></span>  
  
-   <span data-ttu-id="3534f-124">Si vous souhaitez la persistance d’événement BAM soit synchronisée avec la transaction de pipeline, vous devez utiliser un flux d’événements de messagerie (MES).</span><span class="sxs-lookup"><span data-stu-id="3534f-124">If you want BAM event persistence to be in sync with pipeline transaction, you should use a Messaging Event Stream (MES).</span></span>  
  
 <span data-ttu-id="3534f-125">Tous les flux d’événements asynchrones (BES, MES et OES) conservent les données de tout d’abord la base de données MessageBox de BizTalk.</span><span class="sxs-lookup"><span data-stu-id="3534f-125">All the asynchronous EventStreams (BES, MES, and OES) persist data first to the BizTalk MessageBox database.</span></span> <span data-ttu-id="3534f-126">Régulièrement, les données sont traitées et rendues persistantes dans la base de données Importation principale BAM par le service TDDS (Tracking Data Decode Service).</span><span class="sxs-lookup"><span data-stu-id="3534f-126">Periodically the data is processed and persisted to the BAM Primary Import database by the Tracking Data Decode Service (TDDS).</span></span>  
  
 <span data-ttu-id="3534f-127">Pour plus d’informations sur les BAM EventStream APIs, consultez [Classes EventStream](http://go.microsoft.com/fwlink/?LinkId=158046) (http://go.microsoft.com/fwlink/?LinkId=158046) dans la documentation de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="3534f-127">For more information about the BAM EventStream APIs, see [EventStream Classes](http://go.microsoft.com/fwlink/?LinkId=158046) (http://go.microsoft.com/fwlink/?LinkId=158046) in the BizTalk Server documentation.</span></span>  
  
## <a name="bam-performance-counters"></a><span data-ttu-id="3534f-128">Compteurs de performance BAM</span><span class="sxs-lookup"><span data-stu-id="3534f-128">BAM performance counters</span></span>  
 <span data-ttu-id="3534f-129">Pour obtenir une liste détaillée des compteurs de performance pour l’analyse BAM, consultez [les compteurs de Performance BAM](http://go.microsoft.com/fwlink/?LinkId=158048) (http://go.microsoft.com/fwlink/?LinkId=158048) dans la documentation de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="3534f-129">For a detailed list of the performance counters for BAM, see [BAM Performance Counters](http://go.microsoft.com/fwlink/?LinkId=158048) (http://go.microsoft.com/fwlink/?LinkId=158048) in the BizTalk Server documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3534f-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3534f-130">See Also</span></span>  
 [<span data-ttu-id="3534f-131">Optimisation des performances de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="3534f-131">Optimizing BizTalk Server Performance</span></span>](../technical-guides/optimizing-biztalk-server-performance.md)