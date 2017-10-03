---
title: "Continuation d’activités | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- continuation tokens
- activities [BAM], code samples
- activities [BAM], continuation tokens
- continuations, activities [BAM]
- code samples, activities [BAM]
ms.assetid: 47d91ae6-77c1-4efb-940f-a7b3a325e5bd
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c7568da0647ae9847c3de2d060d75a53466b9709
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="activity-continuation"></a><span data-ttu-id="b2b56-102">Continuation d'activités</span><span class="sxs-lookup"><span data-stu-id="b2b56-102">Activity Continuation</span></span>
<span data-ttu-id="b2b56-103">L'activité d'analyse BAM (également appelée activité d'entreprise) peut englober plusieurs applications hétérogènes (par exemple un pipeline, deux orchestrations, une application sectorielle et un autre pipeline).</span><span class="sxs-lookup"><span data-stu-id="b2b56-103">The BAM activity (also called the business activity) can span multiple heterogeneous applications (for example, a pipeline, two orchestrations, a line-of-business application, and then another pipeline).</span></span> <span data-ttu-id="b2b56-104">L’infrastructure BAM peut mettre en corrélation les événements à partir de plusieurs applications avec un peu d’aide du développeur – un concept appelé «*Continuation*, » qui est indiqué dans l’illustration suivante.</span><span class="sxs-lookup"><span data-stu-id="b2b56-104">The BAM infrastructure can correlate the events from multiple applications with a little help from the developer – a concept called "*Continuation*," which is shown in the following figure.</span></span>  
  
 ![](../core/media/ebiz-prog-bam-fig4-app-scopes-cont-tokens.gif "ebiz_prog_bam_fig4_app_scopes_cont_tokens")  

## <a name="applications"></a><span data-ttu-id="b2b56-105">Applications</span><span class="sxs-lookup"><span data-stu-id="b2b56-105">Applications</span></span>  
 <span data-ttu-id="b2b56-106">La première partie de l'activité se produit dans l'application des ventes, la deuxième dans l'application d'emballage et d'assemblage en palettes et la troisième, traitant le suivi de la livraison, est disponible dans l'application d'expédition.</span><span class="sxs-lookup"><span data-stu-id="b2b56-106">The first part of the activity happens in the Sales application, the second part of the activity happens in the Packaging & Assembly application, and finally, the delivery progress is available in the Shipping application.</span></span> <span data-ttu-id="b2b56-107">Chaque application utilise différents des ID de l’unité de travail actuelle : fournisseur numéro de commande (PO), le numéro de commande (ainsi) et le numéro de commande d’expédition (UPS).</span><span class="sxs-lookup"><span data-stu-id="b2b56-107">Each application uses different IDs for the current work unit: purchase order number (PO), sales order number (SO), and shipping order number (UPS).</span></span> <span data-ttu-id="b2b56-108">Pour mettre des événements en corrélation entre deux applications différentes, vous devez :</span><span class="sxs-lookup"><span data-stu-id="b2b56-108">To correlate the events between two different applications, you must:</span></span>  
  
-   <span data-ttu-id="b2b56-109">identifier le jeton de continuation, donnée unique disponible pour les deux applications (par exemple, la partie du message échangé) ;</span><span class="sxs-lookup"><span data-stu-id="b2b56-109">Identify the continuation token – a unique piece of data that is available to both applications (for example, the part of the message being exchanged).</span></span>  
  
-   <span data-ttu-id="b2b56-110">appeler l'événement EnableContinuation dans la première application et transmettre le jeton de continuation en même temps que l'ID d'activité actuel ;</span><span class="sxs-lookup"><span data-stu-id="b2b56-110">Call EnableContinuation in the first application and pass the continuation token along with the current ActivityID.</span></span>  
  
-   <span data-ttu-id="b2b56-111">éviter absolument d'appeler l'événement BeginActivity dans la deuxième application ;</span><span class="sxs-lookup"><span data-stu-id="b2b56-111">Do not call BeginActivity in the second application.</span></span>  
  
-   <span data-ttu-id="b2b56-112">déclencher tous les événements suivants dans la deuxième application en utilisant le jeton de continuation au lieu de l'ID d'activité.</span><span class="sxs-lookup"><span data-stu-id="b2b56-112">Fire all subsequent events in the second application by using the continuation token instead of ActivityID.</span></span>  
  
 <span data-ttu-id="b2b56-113">Le code ci-dessous est un exemple de l'utilisation d'une continuation d'activités entre trois applications :</span><span class="sxs-lookup"><span data-stu-id="b2b56-113">The following code example illustrates the use of activity continuation among three applications:</span></span>  
  
 <span data-ttu-id="b2b56-114">**Application de bon de commande**</span><span class="sxs-lookup"><span data-stu-id="b2b56-114">**Purchase Order Application**</span></span>  
  
```  
string oID="PO#123";  
string soID="SO#265";  
es.BeginActivity("PurchaseOrder",poID);  
es.UpdateActivity("PurchaseOrder",poID,  
    "POReceived",DateTime.UtcNow,  
    "POAmount",100,  
"CustomerCity","Seattle");  
es.EnableContinuation(  
   "PurchaseOrder",poId,soID);  
es.EndActivity("PurchaseOrder",poID);  
```  
  
 <span data-ttu-id="b2b56-115">**Application de traitement**</span><span class="sxs-lookup"><span data-stu-id="b2b56-115">**Fulfillment Application**</span></span>  
  
```  
string soID="SO#265";  
string upsID="UPS#97892";  
es.UpdateActivity("PurchaseOrder",soID,  
    "POApproved",DateTime.UtcNow,  
    "ProductName","ProductA");  
es.EnableContinuation(  
   "PurchaseOrder",soID,upsID);  
es.EndActivity("PurchaseOrder",soID);  
```  
  
 <span data-ttu-id="b2b56-116">**Application d’expédition**</span><span class="sxs-lookup"><span data-stu-id="b2b56-116">**Shipping Application**</span></span>  
  
```  
string upsID="UPS#97892"  
es.UpdateActivity("PurchaseOrder", upsID,  
"POShipped",DateTime.UtcNow);  
es.EndActivity("PurchaseOrder",upsID)  
  
```  
  
 <span data-ttu-id="b2b56-117">Tenez compte des instructions suivantes pour intégrer la continuation d'activités dans votre code :</span><span class="sxs-lookup"><span data-stu-id="b2b56-117">Follow these guidelines to use activity continuation in your code:</span></span>  
  
-   <span data-ttu-id="b2b56-118">Utilisez la continuation uniquement quand l'utilisateur final doit traiter le travail d'applications différentes dans une seule activité.</span><span class="sxs-lookup"><span data-stu-id="b2b56-118">Only use continuation when the end user must treat the work of different applications as part of the same activity.</span></span> <span data-ttu-id="b2b56-119">Utilisez des activités distinctes pour chaque application et créez une relation d'activité si l'utilisateur final considère le travail de chaque application comme des activités suffisamment significatives.</span><span class="sxs-lookup"><span data-stu-id="b2b56-119">Use separate activities for each application and create an activity relationship if the end user views the work in each applications as meaningful activities.</span></span>  
  
-   <span data-ttu-id="b2b56-120">Si les unités de travail des applications n'utilisent pas une relation de type un-à-un, vous pouvez leur appliquer des relations d'activité au lieu d'une continuation, dans le cas où plusieurs expéditions sont prévues pour une même commande par exemple.</span><span class="sxs-lookup"><span data-stu-id="b2b56-120">If the work units in the applications do not have a one-to-one relationship, you can use activity relationships but not continuation, for example, when multiple shipments exist for a sales order.</span></span>  
  
-   <span data-ttu-id="b2b56-121">Lorsque vous envoyez de manière synchrone des données à l'analyse BAM (à l'aide de la classe DirectEventStream) et que l'ID d'activité est propagé à tous les composants concernés, vous n'avez pas besoin d'utiliser la continuation.</span><span class="sxs-lookup"><span data-stu-id="b2b56-121">If you send data to BAM synchronously (using DirectEventStream) and the ActivityID is propagated to all involved components, then you do not need to use continuation.</span></span>  
  
-   <span data-ttu-id="b2b56-122">Si vous envoyez des données de façon asynchrone à l'analyse BAM (à l'aide de la classe BufferedEventStream ou depuis des orchestrations), vous devez utiliser la continuation, même si l'ID d'activité est propagé à tous les composants.</span><span class="sxs-lookup"><span data-stu-id="b2b56-122">If you send data to BAM asynchronously (using BufferedEventStream or from orchestrations), then you must use continuation even if the ActivityID is propagated to all components.</span></span> <span data-ttu-id="b2b56-123">Dans ce cas, utilisez un ID d'activité différent dans chaque application en lui ajoutant un préfixe sous la forme d'une chaîne unique (le nom de l'application, par exemple).</span><span class="sxs-lookup"><span data-stu-id="b2b56-123">In this case, you need to use a different ActivityID in each application by prefixing it with a unique string (for example, Application Name).</span></span> <span data-ttu-id="b2b56-124">Cette opération est nécessaire dans la mesure où les données des différentes applications sont susceptibles d'arriver au composant BAM dans un ordre aléatoire et que ce dernier doit masquer les événements arrivant dans le désordre pour garantir des résultats d'interrogation et d'agrégation corrects.</span><span class="sxs-lookup"><span data-stu-id="b2b56-124">This is necessary because the data from different applications may arrive to BAM in random order and BAM has to hide the out-of-order events to ensure correct query and aggregation results.</span></span>  
  
-   <span data-ttu-id="b2b56-125">La continuation ne vous oblige pas à réécrire vos applications pour qu'elles puissent échanger des données supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="b2b56-125">Continuation does not require rewriting your applications to exchange more data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2b56-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b2b56-126">See Also</span></span>  
  
 <span data-ttu-id="b2b56-127">[Infrastructure dynamique BAM](../core/bam-dynamic-infrastructure.md) </span><span class="sxs-lookup"><span data-stu-id="b2b56-127">[BAM Dynamic Infrastructure](../core/bam-dynamic-infrastructure.md) </span></span>  
 <span data-ttu-id="b2b56-128">[API BAM (exemple BizTalk Server)](../core/bam-api-biztalk-server-sample.md) </span><span class="sxs-lookup"><span data-stu-id="b2b56-128">[BAM API (BizTalk Server Sample)](../core/bam-api-biztalk-server-sample.md) </span></span>  
 [<span data-ttu-id="b2b56-129">BAM de bout en bout (exemple BizTalk Server)</span><span class="sxs-lookup"><span data-stu-id="b2b56-129">BAM End-to-End (BizTalk Server Sample)</span></span>](../core/bam-end-to-end-biztalk-server-sample.md)