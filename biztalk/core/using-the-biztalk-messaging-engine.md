---
title: "À l’aide de la messagerie BizTalk moteur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- adapters, Messaging Engine
- adapters, TransportProxy object
- Messaging Engine, adapters
- Messaging Engine, architecture
- TransportProxy object
- Messaging Engine, how to
- architecture, Messaging Engine
- messages, Messaging Engine
ms.assetid: e6b6d1ec-38cd-4721-9673-ae40da003dec
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 701ed3e82eb75b98a948313a99bb4debc65a8cce
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="using-the-biztalk-messaging-engine"></a><span data-ttu-id="8c6c1-102">Utilisation du moteur de messagerie BizTalk</span><span class="sxs-lookup"><span data-stu-id="8c6c1-102">Using the BizTalk Messaging Engine</span></span>
<span data-ttu-id="8c6c1-103">Le diagramme suivant illustre l'architecture du moteur de messagerie.</span><span class="sxs-lookup"><span data-stu-id="8c6c1-103">The following diagram illustrates the architecture of the Messaging Engine.</span></span> <span data-ttu-id="8c6c1-104">Il reflète un scénario dans lequel un message est reçu par un adaptateur et est envoyé dans BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="8c6c1-104">It shows a scenario in which a message is received by an adapter and submitted into BizTalk Server.</span></span>  
  
 ![](../core/media/ebiz-prog-messaging1.gif "ebiz_prog_messaging1")  
<span data-ttu-id="8c6c1-105">Architecture du moteur de messagerie</span><span class="sxs-lookup"><span data-stu-id="8c6c1-105">Architecture of the Messaging Engine</span></span>  
  
 <span data-ttu-id="8c6c1-106">Chaque adaptateur possède sa propre instance d’un **TransportProxy** objet qu’il utilise pour interagir avec le moteur de messagerie.</span><span class="sxs-lookup"><span data-stu-id="8c6c1-106">Each adapter has its own instance of a **TransportProxy** object that it uses to interact with the Messaging Engine.</span></span> <span data-ttu-id="8c6c1-107">Les adaptateurs fonctionnent par lots en fonction du moteur de messagerie. Ces lots sont traités de façon atomique.</span><span class="sxs-lookup"><span data-stu-id="8c6c1-107">Adapters perform work against the Messaging Engine in batches, which are processed atomically.</span></span> <span data-ttu-id="8c6c1-108">Un lot est un ensemble d'opérations tel que SubmitMessage, SuspendMessage ou DeleteMessage.</span><span class="sxs-lookup"><span data-stu-id="8c6c1-108">A batch is a collection of operations such as SubmitMessage, SuspendMessage, or DeleteMessage.</span></span>  
  
 <span data-ttu-id="8c6c1-109">Ce qui suit est la séquence d'événements correspondant au scénario dans lequel un adaptateur envoie un message au moteur de messagerie :</span><span class="sxs-lookup"><span data-stu-id="8c6c1-109">The following is the sequence of events for the scenario where an adapter submits a message to the Messaging Engine:</span></span>  
  
1.  <span data-ttu-id="8c6c1-110">L'adaptateur crée un message et connecte le flux de données au message.</span><span class="sxs-lookup"><span data-stu-id="8c6c1-110">The adapter creates a new message and connects the data stream to the message.</span></span>  
  
2.  <span data-ttu-id="8c6c1-111">L'adaptateur reçoit un nouveau lot du moteur de messagerie.</span><span class="sxs-lookup"><span data-stu-id="8c6c1-111">The adapter gets a new batch from the Messaging Engine.</span></span>  
  
3.  <span data-ttu-id="8c6c1-112">L'adaptateur ajoute le message au lot à envoyer.</span><span class="sxs-lookup"><span data-stu-id="8c6c1-112">The adapter adds the message to the batch to be submitted.</span></span>  
  
4.  <span data-ttu-id="8c6c1-113">Le lot est validé et mis en file d'attente dans la réserve de threads du moteur de messagerie.</span><span class="sxs-lookup"><span data-stu-id="8c6c1-113">The batch is committed and queued up on the Messaging Engine thread pool.</span></span>  
  
5.  <span data-ttu-id="8c6c1-114">La réserve de threads du moteur de messagerie commence à traiter le nouveau lot.</span><span class="sxs-lookup"><span data-stu-id="8c6c1-114">The Messaging Engine thread pool starts processing the new batch.</span></span>  
  
6.  <span data-ttu-id="8c6c1-115">Le message est traité dans le pipeline de réception.</span><span class="sxs-lookup"><span data-stu-id="8c6c1-115">The message is processed in the receive pipeline.</span></span>  
  
7.  <span data-ttu-id="8c6c1-116">Le pipeline de réception génère zéro ou plusieurs messages.</span><span class="sxs-lookup"><span data-stu-id="8c6c1-116">The receive pipeline produces zero or more messages.</span></span> <span data-ttu-id="8c6c1-117">Les pipelines peuvent utiliser des messages dès lors qu'ils ne renvoient pas d'erreurs.</span><span class="sxs-lookup"><span data-stu-id="8c6c1-117">Pipelines can consume messages providing they do not return any errors.</span></span> <span data-ttu-id="8c6c1-118">Les pipelines de réception peuvent produire plusieurs messages. C'est le cas généralement quand le composant désassembleur désassemble un seul échange en plusieurs messages.</span><span class="sxs-lookup"><span data-stu-id="8c6c1-118">Receive pipelines can produce more than one message; typically this happens when the dissassembler component disassembles a single interchange into many messages.</span></span> <span data-ttu-id="8c6c1-119">En général, le pipeline de réception convertit le message envoyé au format XML.</span><span class="sxs-lookup"><span data-stu-id="8c6c1-119">Typically the receive pipeline normalizes the submitted message into XML.</span></span>  
  
8.  <span data-ttu-id="8c6c1-120">Le ou les messages générés par le pipeline sont traités dans le mappeur si le mappage est configuré.</span><span class="sxs-lookup"><span data-stu-id="8c6c1-120">The message(s) produced by the pipeline will be processed in the mapper if mapping is configured.</span></span>  
  
9. <span data-ttu-id="8c6c1-121">Le ou les messages sont publiés dans l'agent des messages ou dans la base de données MessageBox.</span><span class="sxs-lookup"><span data-stu-id="8c6c1-121">The message(s) are published to the Message Agent or to the MessageBox database.</span></span>  
  
10. <span data-ttu-id="8c6c1-122">Le moteur de messagerie rappelle l'adaptateur pour l'informer du résultat du lot de travail.</span><span class="sxs-lookup"><span data-stu-id="8c6c1-122">The Messaging Engine calls back the adapter to notify it of the outcome of the batch of work.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8c6c1-123">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="8c6c1-123">In This Section</span></span>  
  
-   [<span data-ttu-id="8c6c1-124">Traitement des échanges récupérables</span><span class="sxs-lookup"><span data-stu-id="8c6c1-124">Recoverable Interchange Processing</span></span>](../core/recoverable-interchange-processing.md)  
  
-   [<span data-ttu-id="8c6c1-125">Livraison chronologique des messages</span><span class="sxs-lookup"><span data-stu-id="8c6c1-125">Ordered Delivery of Messages</span></span>](../core/ordered-delivery-of-messages.md)  
  
-   [<span data-ttu-id="8c6c1-126">Gestion des erreurs</span><span class="sxs-lookup"><span data-stu-id="8c6c1-126">Error Handling</span></span>](../core/error-handling.md)  
  
## <a name="see-also"></a><span data-ttu-id="8c6c1-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8c6c1-127">See Also</span></span>  
 <span data-ttu-id="8c6c1-128">[Comment BizTalk Server traite les Messages volumineux](../core/how-biztalk-server-processes-large-messages.md) </span><span class="sxs-lookup"><span data-stu-id="8c6c1-128">[How BizTalk Server Processes Large Messages](../core/how-biztalk-server-processes-large-messages.md) </span></span>  
 <span data-ttu-id="8c6c1-129">[Caractéristiques de performances du moteur](../core/engine-performance-characteristics.md) </span><span class="sxs-lookup"><span data-stu-id="8c6c1-129">[Engine Performance Characteristics](../core/engine-performance-characteristics.md) </span></span>  
 <span data-ttu-id="8c6c1-130">[Mesurer le débit de moteur maximal acceptable](../core/measuring-maximum-sustainable-engine-throughput.md) </span><span class="sxs-lookup"><span data-stu-id="8c6c1-130">[Measuring Maximum Sustainable Engine Throughput](../core/measuring-maximum-sustainable-engine-throughput.md) </span></span>  
 <span data-ttu-id="8c6c1-131">[Scénarios de test pour mesurer le débit maximal acceptable du moteur](../core/test-scenarios-for-measuring-mst-of-the-engine.md) </span><span class="sxs-lookup"><span data-stu-id="8c6c1-131">[Test Scenarios for Measuring MST of the Engine](../core/test-scenarios-for-measuring-mst-of-the-engine.md) </span></span>  
 [<span data-ttu-id="8c6c1-132">À l’aide de l’outil Microsoft BizTalk LoadGen 2007</span><span class="sxs-lookup"><span data-stu-id="8c6c1-132">Using the Microsoft BizTalk LoadGen 2007 Tool</span></span>](../core/using-the-microsoft-biztalk-loadgen-2007-tool.md)