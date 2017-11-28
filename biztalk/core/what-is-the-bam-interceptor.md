---
title: "Présentation de l'intercepteur BAM | Microsoft Docs"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BAM Interceptor object
- BAM, collecting data
- BAM, Interceptor object
- data, collecting [BAM]
ms.assetid: e0213c4e-e2f4-4bb0-bd27-e5810f7e39d9
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9400e80a2f8e8acfdeb12e3d6e61a046151d1e7e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="what-is-the-bam-interceptor"></a><span data-ttu-id="2161d-103">Présentation de l'intercepteur BAM</span><span class="sxs-lookup"><span data-stu-id="2161d-103">What Is the BAM Interceptor?</span></span>
## <a name="overview"></a><span data-ttu-id="2161d-104">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="2161d-104">Overview</span></span> 

<span data-ttu-id="2161d-105">L'intercepteur de l'analyse BAM est un objet qui vous permet d'instrumenter votre application pour capturer des données d'intérêt.</span><span class="sxs-lookup"><span data-stu-id="2161d-105">The BAM Interceptor is an object that lets you instrument your application to capture data of interest.</span></span> <span data-ttu-id="2161d-106">Le diagramme suivant illustre le rôle de l'intercepteur de l'analyse BAM et son interaction avec les autres composants BAM :</span><span class="sxs-lookup"><span data-stu-id="2161d-106">The following diagram shows the role of the BAM interceptor and its interaction with the other BAM components:</span></span>  
  
 ![](../core/media/bam-config-api.gif "bam_config_api")  
<span data-ttu-id="2161d-107">Intercepteur de l'analyse BAM</span><span class="sxs-lookup"><span data-stu-id="2161d-107">BAM Interceptor</span></span>  
  
 <span data-ttu-id="2161d-108">Dans chaque étape de votre application où vous pourriez avoir des données d'intérêt, vous appelez Interceptor OnStep, fournissez un identificateur pour l'étape ainsi qu'un objet arbitraire ou de données quelconque que vous utilisez dans votre application.</span><span class="sxs-lookup"><span data-stu-id="2161d-108">In each step of your application where you could have data of interest, you call Interceptor OnStep, provide an identifier for the step, and provide some data or arbitrary object that you are using in your application.</span></span>  
  
 <span data-ttu-id="2161d-109">Vous devez implémenter une fonction de rappel de manière à ce que votre procédure de rappel obtienne l'ID d'étape actuel et vos objets de données lors du rappel.</span><span class="sxs-lookup"><span data-stu-id="2161d-109">You must implement a callback function so when the callback occurs, your callback procedure gets the current step ID and your data object.</span></span> <span data-ttu-id="2161d-110">Essentiellement, l'intercepteur de l'analyse BAM se borne à propager l'objet de données vers le rappel.</span><span class="sxs-lookup"><span data-stu-id="2161d-110">Essentially, the BAM interceptor is simply propagating the data object to the callback.</span></span> <span data-ttu-id="2161d-111">La logique réelle d'extraction des données réside dans votre application.</span><span class="sxs-lookup"><span data-stu-id="2161d-111">The actual logic of extracting data resides in your application.</span></span> <span data-ttu-id="2161d-112">Par exemple, si vos données prennent la forme de messages XML, le rappel utilisera des XPath.</span><span class="sxs-lookup"><span data-stu-id="2161d-112">For example, if your data takes the form of XML messages, then the callback will use XPaths.</span></span> <span data-ttu-id="2161d-113">Pour plus d’informations sur XPath, consultez [à l’aide de XPath dans une assignation du Message](../core/using-xpaths-in-message-assignments.md).</span><span class="sxs-lookup"><span data-stu-id="2161d-113">For more information about XPaths, see [Using XPaths in Message Assignment](../core/using-xpaths-in-message-assignments.md).</span></span>  
  
 <span data-ttu-id="2161d-114">Sur la base d'une configuration que vous pouvez créer de façon programmée, l'intercepteur de l'analyse BAM décide des données à requérir à chaque étape.</span><span class="sxs-lookup"><span data-stu-id="2161d-114">The BAM interceptor decides which data to request at each step, based on the configuration that you can create programmatically.</span></span> <span data-ttu-id="2161d-115">Il se sert ensuite des données obtenues pour appeler DirectEventStream ou BufferedEventStream, que vous devez conserver et transmettre à chaque fois en tant qu'argument à OnStep.</span><span class="sxs-lookup"><span data-stu-id="2161d-115">The BAM Interceptor then uses the obtained data to call either DirectEventStream or BufferedEventStream that you need to keep around and pass each time as an argument to OnStep.</span></span>  
  
 <span data-ttu-id="2161d-116">L'appel de l'intercepteur à chaque étape ne demande pas beaucoup de ressources.</span><span class="sxs-lookup"><span data-stu-id="2161d-116">Calling the interceptor for each step is not a resource-intensive operation.</span></span> <span data-ttu-id="2161d-117">Si, suite à l'appel, vous n'inscrivez rien pour l'étape, l'intercepteur repart immédiatement.</span><span class="sxs-lookup"><span data-stu-id="2161d-117">If you call and you register nothing for this step, the interceptor returns immediately.</span></span> <span data-ttu-id="2161d-118">Cela signifie que n'a lieu aucune opération disque, aucune transaction et même aucune affectation mémoire, et que cela n'a donc presque aucune incidence sur les performances.</span><span class="sxs-lookup"><span data-stu-id="2161d-118">This means that there are no disk operations, no transactions, not even memory allocations, and thus almost no performance impact.</span></span> <span data-ttu-id="2161d-119">Parallèlement, vous avez la possibilité d'extraire toutes les données que vous souhaitez pour l'analyse BAM si nécessaire.</span><span class="sxs-lookup"><span data-stu-id="2161d-119">At the same time, you have the opportunity to extract any data for BAM if necessary.</span></span> <span data-ttu-id="2161d-120">L’impact des performances sur les étapes impliquant l’extraction de données et la disponibilité des données dépend de votre implémentation de la `IBAMDataExtractor Interface`.</span><span class="sxs-lookup"><span data-stu-id="2161d-120">The performance impact on the steps involving data extraction and the availability of the data will depend on your implementation of the `IBAMDataExtractor Interface`.</span></span>  
  
 <span data-ttu-id="2161d-121">Les exemples de code suivants illustrent l'utilisation de l'intercepteur pendant la configuration et l'exécution.</span><span class="sxs-lookup"><span data-stu-id="2161d-121">The following code examples demonstrate the use of the interceptor during configuration and run time.</span></span>  
  
## <a name="configuration-time"></a><span data-ttu-id="2161d-122">Lors de la configuration</span><span class="sxs-lookup"><span data-stu-id="2161d-122">Configuration time</span></span>  
 <span data-ttu-id="2161d-123">Le code suivant vous montre comment configurer l'Intercepteur de manière à ce qu'il s'arrête lors de l'étape recvPO de l'application et à ce qu'il demande le nom du client (Customer Name) et son numéro de sécurité sociale (Customer SSN) :</span><span class="sxs-lookup"><span data-stu-id="2161d-123">The following code shows how you configure the Interceptor to stop at step recvPO of the application, and ask for Customer Name and Customer SSN:</span></span>  
  
```  
ActivityInterceptorConfiguration cfg= new ActivityInterceptorConfiguration ("PurchaseOrder");  
...  
cfg.RegisterDataExtraction("CustomerName",recvPO,XpathName);  
cfg.RegisterDataExtraction("CustomerSSN",recvPO,XpathSSN);  
...  
BAMInterceptor interceptor=new BAMInterceptor();  
cfg.UpdateInterceptor(interceptor);  
...  
// The interceptor instance is ready.  
```  
  
 <span data-ttu-id="2161d-124">Une fois que vous avez créé une instance d'intercepteur, vous pouvez la stocker pour une utilisation ultérieure durant l'exécution.</span><span class="sxs-lookup"><span data-stu-id="2161d-124">After you create an interceptor instance, you can store it for later use at runtime.</span></span>  
  
 <span data-ttu-id="2161d-125">Vous pouvez conserver différents intercepteurs pré-créés différents représentant diverses préférences pour les données et étapes majeures destinées à l'analyse BAM.</span><span class="sxs-lookup"><span data-stu-id="2161d-125">You may keep different pre-created interceptors representing different preferences for the data and milestones for BAM.</span></span> <span data-ttu-id="2161d-126">Pour optimiser les performances, sérialisez les instances d'intercepteur à l'aide de la classe BinaryFormatter.</span><span class="sxs-lookup"><span data-stu-id="2161d-126">For best performance, serialize the Interceptor instances using the BinaryFormatter class.</span></span>  
  
## <a name="run-time"></a><span data-ttu-id="2161d-127">Durée d’exécution</span><span class="sxs-lookup"><span data-stu-id="2161d-127">Run time</span></span>  
 <span data-ttu-id="2161d-128">Utilisez ce code pour utiliser l'intercepteur lors de l'exécution dans un environnement de production :</span><span class="sxs-lookup"><span data-stu-id="2161d-128">Use this code to use the interceptor at runtime in a production environment:</span></span>  
  
```  
// Deserialize the Interceptor that was prepared before  
...  
es=new DirectEventStream(...)  
...  
Interceptor.OnStep(recvPO, data1, es, callback)  
...  
Interceptor.OnStep(approvePO, data2, es, callback)  
...  
```  
  
 <span data-ttu-id="2161d-129">Où :</span><span class="sxs-lookup"><span data-stu-id="2161d-129">Where:</span></span>  
  
-   <span data-ttu-id="2161d-130">*recvPO* et *approvePO* sont des objets arbitraires que vous utilisez pour identifier les étapes dans votre application.</span><span class="sxs-lookup"><span data-stu-id="2161d-130">*recvPO* and *approvePO* are arbitrary objects you use to identify the steps in your application.</span></span>  
  
-   <span data-ttu-id="2161d-131">*Data1* et *data2* sont des objets arbitraires que vous avez à ce stade et pouvez contenir des données intéressantes, par exemple le document XML du bon de commande.</span><span class="sxs-lookup"><span data-stu-id="2161d-131">*data1* and *data2* are arbitrary objects that you have at that point and may contain interesting data – for example the XML document of the purchase order.</span></span>  
  
-   <span data-ttu-id="2161d-132">*es* est soit DirectEventStream soit Bufferedeventstream flux selon vos besoins.</span><span class="sxs-lookup"><span data-stu-id="2161d-132">*es* is either DirectEventStream or BufferedEvent stream depending on your performance requirements.</span></span>  
  
-   <span data-ttu-id="2161d-133">*rappel* est votre implémentation de la `IBAMDataExtractor Interface`.</span><span class="sxs-lookup"><span data-stu-id="2161d-133">*callback* is your implementation of the `IBAMDataExtractor Interface`.</span></span>  
  
 <span data-ttu-id="2161d-134">L’exemple du Kit de développement logiciel, [l’API BAM (exemple BizTalk Server)](../core/bam-api-biztalk-server-sample.md), illustre l’utilisation de l’intercepteur, qui contient à la fois un outil et exemple runtime application de configuration.</span><span class="sxs-lookup"><span data-stu-id="2161d-134">The SDK sample, [BAM API (BizTalk Server Sample)](../core/bam-api-biztalk-server-sample.md), demonstrates using the Interceptor, which contains both a configuration tool and example runtime application.</span></span>  
  
 <span data-ttu-id="2161d-135">Le moteur d'orchestration BizTalk autorise l'interception, ce qui permet de modifier les données à collecter pour l'analyse BAM durant l'exécution à l'aide de l'Éditeur de modèle de suivi.</span><span class="sxs-lookup"><span data-stu-id="2161d-135">The BizTalk Orchestration Engine accommodates interception, which allows changing what data is collected for BAM at runtime using the Tracking Profile Editor.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2161d-136">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="2161d-136">In This Section</span></span>  
  
-   [<span data-ttu-id="2161d-137">Comment déterminer et définir des rôles d’écriture d’événements pour les activités</span><span class="sxs-lookup"><span data-stu-id="2161d-137">How to Determine and Set Event Writer Roles for Activities</span></span>](../core/how-to-determine-and-set-event-writer-roles-for-activities.md)  
  
## <a name="see-also"></a><span data-ttu-id="2161d-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2161d-138">See Also</span></span>  
 [<span data-ttu-id="2161d-139">API BAM (exemple BizTalk Server)</span><span class="sxs-lookup"><span data-stu-id="2161d-139">BAM API (BizTalk Server Sample)</span></span>](../core/bam-api-biztalk-server-sample.md)