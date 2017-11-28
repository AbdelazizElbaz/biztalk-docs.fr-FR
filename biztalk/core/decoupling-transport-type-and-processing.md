---
title: Dissocation du Type de Transport et traitement | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- transport types, decoupling processing
- processing, decoupling transport types
- transport types
- transport types, service solutions
- service solution tutorial, MQSeries adapters
- processing, service solutions
- service solution tutorial, decoupling transport type and processing
- correlations, MQSeries adapters
- MQSeries adapters, correlations
- MQSeries adapters, service solutions
ms.assetid: 0b2c733a-e2c7-42ff-a733-f712fde38f7e
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0b14522c6bbf9393bc22f632c4db5eeb5e4a22a6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="decoupling-transport-type-and-processing"></a><span data-ttu-id="fd42f-102">Dissocation du type de transport et du traitement</span><span class="sxs-lookup"><span data-stu-id="fd42f-102">Decoupling Transport Type and Processing</span></span>
<span data-ttu-id="fd42f-103">Dans une solution orientée services, le processus d'entreprise et les spécificités de transmission ou de réception des messages ont souvent un fonctionnement bien distinct.</span><span class="sxs-lookup"><span data-stu-id="fd42f-103">In a service oriented solution, a clear line often exists between the business processing and the specifics of transmitting and receiving messages.</span></span> <span data-ttu-id="fd42f-104">Ceci permet de modifier le processus d'entreprise ou la fonctionnalité de messagerie de la solution de façon indépendante.</span><span class="sxs-lookup"><span data-stu-id="fd42f-104">This enables you to change the business process or the messaging part of the solution independently.</span></span>  
  
 <span data-ttu-id="fd42f-105">La solution orientée services respecte ce principe de conception, à une exception près.</span><span class="sxs-lookup"><span data-stu-id="fd42f-105">The service oriented solution violates this design principle in one place.</span></span> <span data-ttu-id="fd42f-106">Cette section décrit l'exception en question, les alternatives possibles et la structure sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="fd42f-106">This section describes the situation, the possible alternatives, and the selected structure.</span></span>  
  
## <a name="correlation-and-the-mqseries-adapter"></a><span data-ttu-id="fd42f-107">Corrélation et adaptateur MQSeries</span><span class="sxs-lookup"><span data-stu-id="fd42f-107">Correlation and the MQSeries Adapter</span></span>  
 <span data-ttu-id="fd42f-108">Afin d'utiliser l'adaptateur MQSeries, vous ne pouvez pas utiliser les identificateurs de corrélation BizTalk Server standard.</span><span class="sxs-lookup"><span data-stu-id="fd42f-108">In order to use the MQSeries adapter, you cannot use the standard BizTalk Server correlation identifiers.</span></span> <span data-ttu-id="fd42f-109">En effet, l'identificateur de corrélation est envoyé à un système IBM principal qui possède son propre système d'identificateurs de corrélation.</span><span class="sxs-lookup"><span data-stu-id="fd42f-109">This is because the correlation identifier goes to an IBM back-end system that has its own system of correlation identifiers.</span></span> <span data-ttu-id="fd42f-110">Au lieu de cela, vous devez utiliser le **MQSeries.MQMD_CorrelId** et **MQSeries.MQMD_MsgID** propriétés.</span><span class="sxs-lookup"><span data-stu-id="fd42f-110">Instead, you must use the **MQSeries.MQMD_CorrelId** and **MQSeries.MQMD_MsgID** properties.</span></span> <span data-ttu-id="fd42f-111">afin de placer les informations spécifiques au transport dans l'orchestration et donc, dans le processus d'entreprise.</span><span class="sxs-lookup"><span data-stu-id="fd42f-111">Using these properties potentially puts transport-specific information in the orchestration and, thus, in the business process.</span></span>  
  
 <span data-ttu-id="fd42f-112">Pour gérer cette dépendance, vous pouvez utiliser l'identificateur de corrélation BizTalk Server, ainsi qu'un composant de pipeline personnalisé pour convertir l'identificateur de corrélation pour MQSeries.</span><span class="sxs-lookup"><span data-stu-id="fd42f-112">One way to handle this dependency would be to use the BizTalk Server correlation identifier and use a custom pipeline component to translate the correlation identifier for MQSeries.</span></span> <span data-ttu-id="fd42f-113">Cet ajout complexifie le scénario.</span><span class="sxs-lookup"><span data-stu-id="fd42f-113">This adds complexity to the scenario.</span></span> <span data-ttu-id="fd42f-114">En outre, si le transport est modifié, deux composants du pipeline doivent l'être également.</span><span class="sxs-lookup"><span data-stu-id="fd42f-114">In addition, if the transport changes, two pipeline components must be changed.</span></span> <span data-ttu-id="fd42f-115">Enfin, cette opération déplace la dépendance (dans le composant du pipeline) sans la résoudre.</span><span class="sxs-lookup"><span data-stu-id="fd42f-115">And, ultimately, it relocates the dependency (in the pipeline component) rather than resolving it.</span></span>  
  
 <span data-ttu-id="fd42f-116">Une autre option consiste à isoler la gestion de la corrélation spécifique à MQSeries dans une orchestration distincte et d'appeler cette dernière.</span><span class="sxs-lookup"><span data-stu-id="fd42f-116">Another option would be to isolate the MQSeries-specific correlation handling to a separate orchestration and call that orchestration.</span></span> <span data-ttu-id="fd42f-117">De cette manière, l'indépendance du processus d'entreprise est préservée.</span><span class="sxs-lookup"><span data-stu-id="fd42f-117">This would preserve the independence of the business process.</span></span> <span data-ttu-id="fd42f-118">Toutefois, cela provoque une dépendance de compilation entre les orchestrations.</span><span class="sxs-lookup"><span data-stu-id="fd42f-118">However, this introduces a compile-time dependency between the orchestrations.</span></span> <span data-ttu-id="fd42f-119">La modification du transport nécessite une recompilation des deux orchestrations (par exemple, du stub vers la version de l'adaptateur de la solution).</span><span class="sxs-lookup"><span data-stu-id="fd42f-119">Modifying the transport requires recompiling both orchestrations (as, for example, in going from the stub to the adapter version of the solution).</span></span> <span data-ttu-id="fd42f-120">L'appel s'ajoute également au temps de réponse de la solution.</span><span class="sxs-lookup"><span data-stu-id="fd42f-120">The call also adds to the response time for the solution.</span></span>  
  
 <span data-ttu-id="fd42f-121">Étant donné la complexité supplémentaire et la réduction éventuelle des performances, il semble plus simple d'utiliser la corrélation MQSeries directement dans l'orchestration.</span><span class="sxs-lookup"><span data-stu-id="fd42f-121">Given the additional complexity and possible decrease in performance, it seemed simplest to use the MQSeries correlation directly in the orchestration.</span></span>  
  
 <span data-ttu-id="fd42f-122">Pour plus d’informations sur la carte et les corrélations dans les orchestrations, consultez [MQSCorrelationSetOrchestration (exemple BizTalk Server)](../core/mqscorrelationsetorchestration-biztalk-server-sample.md).</span><span class="sxs-lookup"><span data-stu-id="fd42f-122">For more information about the adapter and correlations in orchestrations, see [MQSCorrelationSetOrchestration (BizTalk Server Sample)](../core/mqscorrelationsetorchestration-biztalk-server-sample.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd42f-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fd42f-123">See Also</span></span>  
 <span data-ttu-id="fd42f-124">[Caractéristiques de l’implémentation du Service orienté solutions](../core/implementation-highlights-of-the-service-oriented-solution.md) </span><span class="sxs-lookup"><span data-stu-id="fd42f-124">[Implementation Highlights of the Service Oriented Solution](../core/implementation-highlights-of-the-service-oriented-solution.md) </span></span>  
 [<span data-ttu-id="fd42f-125">MQSCorrelationSetOrchestration (exemple BizTalk Server)</span><span class="sxs-lookup"><span data-stu-id="fd42f-125">MQSCorrelationSetOrchestration (BizTalk Server Sample)</span></span>](../core/mqscorrelationsetorchestration-biztalk-server-sample.md)