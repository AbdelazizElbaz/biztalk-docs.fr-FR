---
title: Fragmentation par lot entrant | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- batching, fragmenting messages
- messages, fragmenting
- fragmenting messages
ms.assetid: 5844710e-f662-48a3-bf1a-bc1ba91e678a
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0807bbe83ea2f477a7e1625488ebbecf578f3adc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="fragmented-inbound-batch"></a><span data-ttu-id="a4de9-102">Par lot entrant fragmenté</span><span class="sxs-lookup"><span data-stu-id="a4de9-102">Fragmented Inbound Batch</span></span>
<span data-ttu-id="a4de9-103">Vous pouvez configurer [!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)] pour recevoir un lot de messages, extraire les messages du lot, puis d’acheminer les messages individuels dans le système de destination.</span><span class="sxs-lookup"><span data-stu-id="a4de9-103">You can configure [!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)] to receive a message batch, extract the messages from the batch, and then route the individual messages to the destination system.</span></span> <span data-ttu-id="a4de9-104">Si vous activez la fragmentation, les fragments par lot entrant en messages individuels ; dans le cas contraire, le lot est traité et routé comme un seul 'batch' ou l’échange.</span><span class="sxs-lookup"><span data-stu-id="a4de9-104">If you enable fragmentation, the inbound batch fragments into individual messages; otherwise, the batch is processed and routed as a single 'batch' or interchange.</span></span> <span data-ttu-id="a4de9-105">BTAHL7 Configuration Explorer vous permet d’activer le traitement par lot.</span><span class="sxs-lookup"><span data-stu-id="a4de9-105">You use BTAHL7 Configuration Explorer to enable batching.</span></span> <span data-ttu-id="a4de9-106">Pour plus d’informations sur l’activation de traitement par lot, consultez [configuration de traitement par lot](../../adapters-and-accelerators/accelerator-hl7/configuring-batching.md).</span><span class="sxs-lookup"><span data-stu-id="a4de9-106">For more information about enabling batching, see [Configuring Batching](../../adapters-and-accelerators/accelerator-hl7/configuring-batching.md).</span></span>  
  
 <span data-ttu-id="a4de9-107">La section suivante décrit un scénario typique par lot entrant fragmentés :</span><span class="sxs-lookup"><span data-stu-id="a4de9-107">The following describes a typical fragmented inbound batch scenario:</span></span>  
  
1.  <span data-ttu-id="a4de9-108">Une application line-of-business, en cours d’exécution sur le système A, envoie un lot de messages BTAHL7.</span><span class="sxs-lookup"><span data-stu-id="a4de9-108">A line-of-business application, running on System A, sends a message batch to BTAHL7.</span></span>  
  
     <span data-ttu-id="a4de9-109">Messages par lot peuvent être dans deux formats.</span><span class="sxs-lookup"><span data-stu-id="a4de9-109">Batch messages can be in two different formats.</span></span> <span data-ttu-id="a4de9-110">BTAHL7 peut traiter les formats suivants :</span><span class="sxs-lookup"><span data-stu-id="a4de9-110">BTAHL7 can process the following formats:</span></span>  
  
    -   <span data-ttu-id="a4de9-111">Format 1 : Inclut un en-tête de fichier et la paire de code de fin (FHS/FTS) et au moins un en-tête de lot et codes de fin (BHS/BTS).</span><span class="sxs-lookup"><span data-stu-id="a4de9-111">Format 1: Includes one file header and trailer (FHS/FTS) pair and one or more batch header and trailers (BHS/BTS).</span></span>  
  
        ```  
        FHS  
        BHS  
        MSH  
        .............  
        MSH  
        ...........  
        BTS  
        BHS  
        MSH  
        ..............  
        MSH  
        ...............  
        BTS  
        FTS  
        ```  
  
    -   <span data-ttu-id="a4de9-112">Format 2 : Ne contient pas de wrappers de fichiers et de traitement par lots HL7 défini et suspend une série de messages dans un flux de données.</span><span class="sxs-lookup"><span data-stu-id="a4de9-112">Format 2: Does not contain HL7 defined file and batch wrappers, and suspends a series are messages in a stream.</span></span>  
  
        ```  
        MSH  
        .......  
        MSH  
        ........  
        MSH  
        .........  
        ```  
  
2.  <span data-ttu-id="a4de9-113">BTAHL7 crée des messages individuels à partir du lot, puis vérifie les messages individuels par rapport aux schémas appropriés.</span><span class="sxs-lookup"><span data-stu-id="a4de9-113">BTAHL7 creates individual messages from the batch and then verifies the individual messages against the appropriate schemas.</span></span>  
  
3.  <span data-ttu-id="a4de9-114">BTAHL7 envoie un message d’accusé de réception distincts au système A pour chaque message extrait à partir du lot.</span><span class="sxs-lookup"><span data-stu-id="a4de9-114">BTAHL7 sends a separate acknowledgment message to System A for each message extracted from the batch.</span></span>  
  
4.  <span data-ttu-id="a4de9-115">BTAHL7 achemine les messages individuels dans le système de destination selon les informations de routage des messages individuels, plutôt que l’en-tête de lot de messages.</span><span class="sxs-lookup"><span data-stu-id="a4de9-115">BTAHL7 routes the individual messages to the destination system based on the routing information in the individual messages, rather than the message batch header.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="a4de9-116">BTAHL7 ne valide pas le lot et le fichier en-têtes/codes de fin lorsque la **FHS3** champ (expéditeur) contient un partenaire commercial qui a activé la fragmentation.</span><span class="sxs-lookup"><span data-stu-id="a4de9-116">BTAHL7 does not validate batch and file headers/trailers when the **FHS3** field (sending party) contains a trading partner that has fragmentation enabled.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4de9-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a4de9-117">See Also</span></span>  
 [<span data-ttu-id="a4de9-118">Configurer le traitement par lot</span><span class="sxs-lookup"><span data-stu-id="a4de9-118">Configuring Batching</span></span>](../../adapters-and-accelerators/accelerator-hl7/configuring-batching.md)