---
title: Appel de Back-end incorporation (inlining) | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MessageBox database, performance
- service solution tutorial, performance
- performance, in-line invocation
- Inline Invocation of Back-End Processes [service solutions], performance
- performance, MessageBox database
ms.assetid: 991d080f-a4cc-4f14-bab3-3b8b74636daf
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a7300429e9f74abc7bc10569c653bdaa0a4c13b1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="inlining-back-end-invocation"></a><span data-ttu-id="5850a-102">Appel de Back-end incorporation (inlining)</span><span class="sxs-lookup"><span data-stu-id="5850a-102">Inlining Back-end Invocation</span></span>
<span data-ttu-id="5850a-103">La version d'appel Inline des solutions complètes offre la durée de traitement la plus courte.</span><span class="sxs-lookup"><span data-stu-id="5850a-103">The inline call version, of the full solutions, provides the fastest processing times.</span></span> <span data-ttu-id="5850a-104">Elle élimine la charge de stockage des messages de requête et de réponse vers et à partir des systèmes principaux dans la base de données MessageBox.</span><span class="sxs-lookup"><span data-stu-id="5850a-104">The inline version eliminates the overhead of persisting the request and response messages to and from the backend systems in the MessageBox database.</span></span> <span data-ttu-id="5850a-105">Dans la version d'adaptateur, le message est acheminé d'une orchestration d'expédition vers MessageBox.</span><span class="sxs-lookup"><span data-stu-id="5850a-105">In the adapter version, the message goes from the sending orchestration to the MessageBox.</span></span> <span data-ttu-id="5850a-106">L'hôte exécutant l'adaptateur récupère le message, puis l'envoie au processus principal par l'intermédiaire de MessageBox.</span><span class="sxs-lookup"><span data-stu-id="5850a-106">The host running the adapter picks up the message, and sends the message to the back-end process by again posting it to the message box.</span></span>  
  
 <span data-ttu-id="5850a-107">L'efficacité de la version Inline est atteinte en liant l'orchestration directement aux protocoles de transport des systèmes principaux.</span><span class="sxs-lookup"><span data-stu-id="5850a-107">The efficiency of inlining comes at a cost of binding the orchestration directly to the transport protocols of the back-end systems.</span></span> <span data-ttu-id="5850a-108">Dans cette version, l'orchestration ne communique pas par l'intermédiaire de ports logiques : elle appelle les systèmes principaux via trois assemblys personnalisés.</span><span class="sxs-lookup"><span data-stu-id="5850a-108">In the inline version, rather than communicating through logical ports, the orchestration calls the back-end systems through three custom assemblies.</span></span> <span data-ttu-id="5850a-109">Si le transport d'un système principal est modifié, un assembly doit être réécrit puis recompilé.</span><span class="sxs-lookup"><span data-stu-id="5850a-109">If a back-end system transport changes, an assembly must be rewritten and recompiled.</span></span> <span data-ttu-id="5850a-110">Le tableau suivant décrit ces assemblys et leurs fonctions :</span><span class="sxs-lookup"><span data-stu-id="5850a-110">The following table describes the assemblies and their function:</span></span>  
  
|<span data-ttu-id="5850a-111">Nom de l'assembly</span><span class="sxs-lookup"><span data-stu-id="5850a-111">Assembly Name</span></span>|<span data-ttu-id="5850a-112">Connexion au système principal</span><span class="sxs-lookup"><span data-stu-id="5850a-112">Back-end Connection</span></span>|  
|-------------------|--------------------------|  
|<span data-ttu-id="5850a-113">Microsoft.Samples.BizTalk.WoodgroveBank.PaymentTrackerCall</span><span class="sxs-lookup"><span data-stu-id="5850a-113">Microsoft.Samples.BizTalk.WoodgroveBank.PaymentTrackerCall</span></span>|<span data-ttu-id="5850a-114">Fait appel à MQSeries **obtenir** et **put** fonctions de message.</span><span class="sxs-lookup"><span data-stu-id="5850a-114">Uses MQSeries **get** and **put** message functions.</span></span>|  
|<span data-ttu-id="5850a-115">Microsoft.Samples.BizTalk.WoodgroveBank.PendingTransactionsCall</span><span class="sxs-lookup"><span data-stu-id="5850a-115">Microsoft.Samples.BizTalk.WoodgroveBank.PendingTransactionsCall</span></span>|<span data-ttu-id="5850a-116">Appelle le service Web associé au système de transactions.</span><span class="sxs-lookup"><span data-stu-id="5850a-116">Invokes the Web service for the transaction system.</span></span>|  
|<span data-ttu-id="5850a-117">Microsoft.Samples.BizTalk.WoodgroveBank.SAPCall</span><span class="sxs-lookup"><span data-stu-id="5850a-117">Microsoft.Samples.BizTalk.WoodgroveBank.SAPCall</span></span>|<span data-ttu-id="5850a-118">Appelle les services Web simulant un système SAP.</span><span class="sxs-lookup"><span data-stu-id="5850a-118">Calls the web services simulating SAP.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5850a-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5850a-119">See Also</span></span>  
 <span data-ttu-id="5850a-120">[Caractéristiques de l’implémentation du Service orienté solutions](../core/implementation-highlights-of-the-service-oriented-solution.md) </span><span class="sxs-lookup"><span data-stu-id="5850a-120">[Implementation Highlights of the Service Oriented Solution](../core/implementation-highlights-of-the-service-oriented-solution.md) </span></span>  
 <span data-ttu-id="5850a-121">[Développement d’un Service de la Solution orientée services](../core/developing-a-service-oriented-solution.md) </span><span class="sxs-lookup"><span data-stu-id="5850a-121">[Developing a Service Oriented Solution](../core/developing-a-service-oriented-solution.md) </span></span>  
 <span data-ttu-id="5850a-122">[Conversion des modèles de Service, la Solution orientée services](../core/translating-the-patterns-of-the-service-oriented-solution.md) </span><span class="sxs-lookup"><span data-stu-id="5850a-122">[Translating the Patterns of the Service Oriented Solution](../core/translating-the-patterns-of-the-service-oriented-solution.md) </span></span>  
 [<span data-ttu-id="5850a-123">Le Service d’analyse de la Solution avec BAM orientée services</span><span class="sxs-lookup"><span data-stu-id="5850a-123">Monitoring the Service Oriented Solution with BAM</span></span>](../core/monitoring-the-service-oriented-solution-with-bam.md)