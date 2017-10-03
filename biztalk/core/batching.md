---
title: Le traitement par lots | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- batching
- Messaging Engine, batching
- batching, batch size
- batching, about batching
- batching, configuring
- batching, Messaging Engine
ms.assetid: eadc177a-d395-4f99-8dab-aa706fd8ea00
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ca31344e60daa88a37c21d0f90b6cf2d2a8aa5a7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="batching"></a><span data-ttu-id="b0d3b-102">Traitement par lot</span><span class="sxs-lookup"><span data-stu-id="b0d3b-102">Batching</span></span>
<span data-ttu-id="b0d3b-103">*Le traitement par lot* est un traitement sérialisé d’un ensemble de messages qui permet des optimisations en rapport à la base de données avec des boucles.</span><span class="sxs-lookup"><span data-stu-id="b0d3b-103">*Batching* is a serialized processing of a set of messages that allows for optimizations with respect to database round trips.</span></span> <span data-ttu-id="b0d3b-104">Un lot est une unité de travail atomique, c'est-à-dire qui réussit globalement ou échoue globalement.</span><span class="sxs-lookup"><span data-stu-id="b0d3b-104">A batch is a unit of work that is atomic; that is, it either all succeeds or all fails.</span></span> <span data-ttu-id="b0d3b-105">Si une opération d'un lot réussit mais qu'une autre opération échoue, toutes les opérations qui constituent ce lot sont invalidées et doivent être répétées.</span><span class="sxs-lookup"><span data-stu-id="b0d3b-105">If one operation in a batch succeeds but another operation fails, all the operations that make up the batch are invalidated and must be repeated.</span></span>  
  
 <span data-ttu-id="b0d3b-106">BizTalk Server utilise le traitement par lot pour :</span><span class="sxs-lookup"><span data-stu-id="b0d3b-106">BizTalk Server uses batching to:</span></span>  
  
-   <span data-ttu-id="b0d3b-107">amortir le coût de la transaction sur plusieurs messages ;</span><span class="sxs-lookup"><span data-stu-id="b0d3b-107">Amortize the cost of the transaction across many messages.</span></span>  
  
-   <span data-ttu-id="b0d3b-108">augmenter la vitesse en réduisant le nombre interne d'allers-retours vers une base de données ;</span><span class="sxs-lookup"><span data-stu-id="b0d3b-108">Increase speed by reducing the internal number of database round trips.</span></span>  
  
-   <span data-ttu-id="b0d3b-109">optimiser l'utilisation de la réserve de threads de BizTalk Server en utilisant l'API asynchrone BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="b0d3b-109">Make more efficient use of the BizTalk Server thread pool by using the BizTalk Server Asynchronous API.</span></span>  
  
## <a name="applying-batching"></a><span data-ttu-id="b0d3b-110">Application d'un traitement par lot</span><span class="sxs-lookup"><span data-stu-id="b0d3b-110">Applying Batching</span></span>  
 <span data-ttu-id="b0d3b-111">Le traitement par lot est configuré dans les propriétés avancées d'un emplacement de réception et est automatiquement activé du côté des ports d'envoi.</span><span class="sxs-lookup"><span data-stu-id="b0d3b-111">Batching is configured in the advanced properties for a receive location and is enabled automatically on the send port side.</span></span>  
  
## <a name="lowering-the-batch-size"></a><span data-ttu-id="b0d3b-112">Réduction de la taille d'un lot</span><span class="sxs-lookup"><span data-stu-id="b0d3b-112">Lowering the Batch Size</span></span>  
 <span data-ttu-id="b0d3b-113">Vous devez réduire la taille des lots dans les cas suivants :</span><span class="sxs-lookup"><span data-stu-id="b0d3b-113">You should lower the batch size if in the following instances:</span></span>  
  
-   <span data-ttu-id="b0d3b-114">lors du traitement de messages volumineux ;</span><span class="sxs-lookup"><span data-stu-id="b0d3b-114">When processing large messages</span></span>  
  
-   <span data-ttu-id="b0d3b-115">lorsque les allers-retours vers la base de données ne constituent pas l'engorgement.</span><span class="sxs-lookup"><span data-stu-id="b0d3b-115">When database round trips are not your bottleneck</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b0d3b-116">Soyez prudent lorsque vous modifiez le **LargeMessageThreshold** paramètre.</span><span class="sxs-lookup"><span data-stu-id="b0d3b-116">Be careful when changing the **LargeMessageThreshold** setting.</span></span> <span data-ttu-id="b0d3b-117">La taille de lot multipliée par la taille moyenne des messages doit être inférieure à la **LargeMessageThreshold** définition, sauf si la taille de lot est 1.</span><span class="sxs-lookup"><span data-stu-id="b0d3b-117">The batch size multiplied by the average message size should be less than the **LargeMessageThreshold** setting unless the batch size is 1.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0d3b-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b0d3b-118">See Also</span></span>  
 <span data-ttu-id="b0d3b-119">[Le moteur de messagerie](../core/the-messaging-engine.md) </span><span class="sxs-lookup"><span data-stu-id="b0d3b-119">[The Messaging Engine](../core/the-messaging-engine.md) </span></span>  
 <span data-ttu-id="b0d3b-120">[Traitement par lot des Messages pour le traitement de réception](../core/batching-messages-for-receive-processing.md) </span><span class="sxs-lookup"><span data-stu-id="b0d3b-120">[Batching Messages for Receive Processing](../core/batching-messages-for-receive-processing.md) </span></span>  
 [<span data-ttu-id="b0d3b-121">Traitement par lot des Messages pour le traitement d’envoi</span><span class="sxs-lookup"><span data-stu-id="b0d3b-121">Batching Messages for Send Processing</span></span>](../core/batching-messages-for-send-processing.md)