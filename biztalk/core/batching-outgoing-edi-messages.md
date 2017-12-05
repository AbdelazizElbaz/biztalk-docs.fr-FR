---
title: Le traitement par lot des Messages EDI sortants | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 93a2bd68-4974-4927-938a-8eaf8f007566
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 852b85e0de23e01e39891adba56053683d18a9b8
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="batching-outgoing-edi-messages"></a><span data-ttu-id="858f2-102">Traitement par lot des messages EDI sortants</span><span class="sxs-lookup"><span data-stu-id="858f2-102">Batching Outgoing EDI Messages</span></span>
<span data-ttu-id="858f2-103">Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] traitera les groupes EDI par lot si le traitement par lot a été activé pour l'accord associé au partenaire commercial qui les recevra.</span><span class="sxs-lookup"><span data-stu-id="858f2-103">Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will batch EDI transaction sets if batching has been enabled for the agreement associated with the business partner that will be receiving it.</span></span> <span data-ttu-id="858f2-104">Les propriétés EDI d'un accord vous permettent d'effectuer les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="858f2-104">The EDI properties for an agreement enable you to do the following:</span></span>  
  
-   <span data-ttu-id="858f2-105">Définir plusieurs lots sortants</span><span class="sxs-lookup"><span data-stu-id="858f2-105">Define multiple outgoing batches</span></span>  
  
-   <span data-ttu-id="858f2-106">Définir l'échange</span><span class="sxs-lookup"><span data-stu-id="858f2-106">Define the interchange</span></span>  
  
-   <span data-ttu-id="858f2-107">Définir les groupes de l'échange</span><span class="sxs-lookup"><span data-stu-id="858f2-107">Define the groups in the interchange</span></span>  
  
-   <span data-ttu-id="858f2-108">Définir les critères de déclenchement de lot</span><span class="sxs-lookup"><span data-stu-id="858f2-108">Set the batch release criteria</span></span>  
  
-   <span data-ttu-id="858f2-109">Définir les critères d'activation de lot</span><span class="sxs-lookup"><span data-stu-id="858f2-109">Set the batch activation criteria.</span></span>  
  
 <span data-ttu-id="858f2-110">Microsoft BizTalk Server EDI et AS2 permet le traitement suivant des échanges EDI :</span><span class="sxs-lookup"><span data-stu-id="858f2-110">Microsoft BizTalk Server EDI and AS2 enables the following processing of EDI interchanges:</span></span>  
  
-   <span data-ttu-id="858f2-111">Les échanges EDI peuvent inclure les documents informatisés et/ou les accusés de réception.</span><span class="sxs-lookup"><span data-stu-id="858f2-111">EDI interchanges can include transaction sets and/or acknowledgments.</span></span>  
  
-   <span data-ttu-id="858f2-112">Le pipeline de réception EDI peut fractionner un échange en documents informatisés XML pour un traitement ultérieur par [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], ou il peut préserver l'échange, en le transmettant via [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] au format dans lequel il a été reçu.</span><span class="sxs-lookup"><span data-stu-id="858f2-112">The EDI receive pipeline can split an interchange into XML transaction sets for further processing by [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], or it can preserve the interchange, passing it through [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] in its received form.</span></span>  
  
-   <span data-ttu-id="858f2-113">L'orchestration de routage EDI permet à [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] de traiter par lot un document informatisé unique dans plusieurs échanges sortants.</span><span class="sxs-lookup"><span data-stu-id="858f2-113">The EDI routing orchestration enables [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to batch a single transaction set into more than one outgoing interchange.</span></span>  
  
-   <span data-ttu-id="858f2-114">L'orchestration du traitement par lot EDI assemble les documents informatisés XML dans un échange EDI, et valide et livre l'échange en respectant les propriétés EDI d'un accord.</span><span class="sxs-lookup"><span data-stu-id="858f2-114">The EDI batching orchestration assembles XML transaction sets into an EDI interchange, and validates and delivers the interchange according to an agreement's EDI properties.</span></span>  
  
 <span data-ttu-id="858f2-115">Les lots EDI, appelés échanges, incluent des groupes de messages, qui contiennent des messages individuels.</span><span class="sxs-lookup"><span data-stu-id="858f2-115">EDI batches, called interchanges, contain message groups, and message groups contain individual messages.</span></span> <span data-ttu-id="858f2-116">Les lots sortants peuvent inclure plusieurs groupes, mais seulement un groupe par type de document.</span><span class="sxs-lookup"><span data-stu-id="858f2-116">Outgoing batches can include multiple groups, but only one group per document type.</span></span> <span data-ttu-id="858f2-117">Un groupe peut contenir plusieurs documents informatisés, mais chacun d'eux doit avoir le même type de document.</span><span class="sxs-lookup"><span data-stu-id="858f2-117">A group can contain multiple transaction sets, but each must have the same document type.</span></span> <span data-ttu-id="858f2-118">Les enveloppes de message sont utilisées pour envelopper les documents informatisés individuels, les groupes individuels et l'intégralité de l'échange.</span><span class="sxs-lookup"><span data-stu-id="858f2-118">Message envelopes are used to wrap individual transaction sets, individual groups, and the entire interchange.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="858f2-119">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="858f2-119">In This Section</span></span>  
  
-   [<span data-ttu-id="858f2-120">Configuration d’un lot sortant</span><span class="sxs-lookup"><span data-stu-id="858f2-120">Configuring an Outgoing Batch</span></span>](../core/configuring-an-outgoing-batch.md)  
  
-   [<span data-ttu-id="858f2-121">Assemblage d’un échange EDI traité par lot</span><span class="sxs-lookup"><span data-stu-id="858f2-121">Assembling a Batched EDI Interchange</span></span>](../core/assembling-a-batched-edi-interchange.md)  
  
-   [<span data-ttu-id="858f2-122">Envoi d’un échange de lot conservé</span><span class="sxs-lookup"><span data-stu-id="858f2-122">Sending a Preserved Batch Interchange</span></span>](../core/sending-a-preserved-batch-interchange.md)