---
title: Le traitement par lot des messages | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- batching
- batching, about batching
- messages, batching
- batching, messages
ms.assetid: d852cf00-3882-4f0f-a4c3-2a39483710ee
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 849f14113d5a5e4776c303ef7a5ea4e1e50a552b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="message-batching"></a><span data-ttu-id="5ad55-102">Le traitement par lots du message</span><span class="sxs-lookup"><span data-stu-id="5ad55-102">Message Batching</span></span>
<span data-ttu-id="5ad55-103">La nécessité de messages par lot peuvent encourager les normes des protocoles, les problèmes de planification ou les limitations de taille de message.</span><span class="sxs-lookup"><span data-stu-id="5ad55-103">Protocol standards, scheduling issues, or message size limitations may motivate the need to batch messages.</span></span> <span data-ttu-id="5ad55-104">Un lot de contrôle d’intégrité au niveau sept (HL7) se compose de messages délimités par un en-tête de lot HL7 et le code de fin du lot.</span><span class="sxs-lookup"><span data-stu-id="5ad55-104">A Health Level Seven (HL7) batch consists of messages enclosed by an HL7 batch header and batch trailer.</span></span> <span data-ttu-id="5ad55-105">Séparateurs de message séparer les messages individuels dans le lot.</span><span class="sxs-lookup"><span data-stu-id="5ad55-105">Message separators separate the individual messages within the batch.</span></span>  
  
 [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]<span data-ttu-id="5ad55-106">[!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)] message prend en charge les trois suivantes des scénarios de traitement par lot :</span><span class="sxs-lookup"><span data-stu-id="5ad55-106"> [!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)] supports the following three message batching scenarios:</span></span>  
  
-   <span data-ttu-id="5ad55-107">**Par lot entrant fragmenté**.</span><span class="sxs-lookup"><span data-stu-id="5ad55-107">**Fragmented inbound batch**.</span></span> <span data-ttu-id="5ad55-108">Dans ce scénario, BTAHL7 reçoit un lot de messages HL7, puis achemine les messages individuels dans le système de destination.</span><span class="sxs-lookup"><span data-stu-id="5ad55-108">In this scenario, BTAHL7 receives an HL7 message batch, and then routes the individual messages to the destination system.</span></span>  
  
-   <span data-ttu-id="5ad55-109">**Traitement par lots dans / hors du lot**. Dans ce scénario, BTAHL7 reçoit un lot de messages HL7, vérifie les messages individuels dans le lot et achemine ensuite le lot de messages pour le système de destination.</span><span class="sxs-lookup"><span data-stu-id="5ad55-109">**Batch in/batch out**. In this scenario, BTAHL7 receives an HL7 message batch, verifies the individual messages within the batch, and then routes the message batch to the destination system.</span></span>  
  
-   <span data-ttu-id="5ad55-110">**Créer le lot ou le traitement par lot sortant**.</span><span class="sxs-lookup"><span data-stu-id="5ad55-110">**Create batch or outbound batching**.</span></span> <span data-ttu-id="5ad55-111">Dans ce scénario, BTAHL7 reçoit des messages individuels et les lots avant de les router vers le système de destination.</span><span class="sxs-lookup"><span data-stu-id="5ad55-111">In this scenario, BTAHL7 receives individual messages and batches them before routing them to the destination system.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="5ad55-112">BTAHL7 n’active pas le traitement par lots du message pour le traitement par lot sortant par défaut.</span><span class="sxs-lookup"><span data-stu-id="5ad55-112">BTAHL7 does not enable message batching for outbound batching by default.</span></span> <span data-ttu-id="5ad55-113">Vous devez utiliser l’Explorateur BizTalk pour tout d’abord inscrire l’orchestration de traitement par lots de BTAHL7 et puis démarrer l’orchestration de traitement par lots.</span><span class="sxs-lookup"><span data-stu-id="5ad55-113">You must use BizTalk Explorer to first enlist the BTAHL7 batch orchestration, and then start the batch orchestration.</span></span> <span data-ttu-id="5ad55-114">Pour plus d’informations sur l’activation du message de traitement par lot, consultez [configuration de traitement par lot](../../adapters-and-accelerators/accelerator-hl7/configuring-batching.md).</span><span class="sxs-lookup"><span data-stu-id="5ad55-114">For more information about enabling message batching, see [Configuring Batching](../../adapters-and-accelerators/accelerator-hl7/configuring-batching.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5ad55-115">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="5ad55-115">In This Section</span></span>  
  
-   [<span data-ttu-id="5ad55-116">Par lot entrant fragmenté</span><span class="sxs-lookup"><span data-stu-id="5ad55-116">Fragmented Inbound Batch</span></span>](../../adapters-and-accelerators/accelerator-hl7/fragmented-inbound-batch.md)  
  
-   [<span data-ttu-id="5ad55-117">Configurer le traitement par lot</span><span class="sxs-lookup"><span data-stu-id="5ad55-117">Configuring Batching</span></span>](../../adapters-and-accelerators/accelerator-hl7/configuring-batching.md)  
  
-   [<span data-ttu-id="5ad55-118">Planification de traitement par lot</span><span class="sxs-lookup"><span data-stu-id="5ad55-118">Scheduling Batching</span></span>](../../adapters-and-accelerators/accelerator-hl7/scheduling-batching.md)  
  
-   [<span data-ttu-id="5ad55-119">Configuration des accusés de réception de traitement par lot</span><span class="sxs-lookup"><span data-stu-id="5ad55-119">Configuring Batching Acknowledgments</span></span>](../../adapters-and-accelerators/accelerator-hl7/configuring-batching-acknowledgments.md)