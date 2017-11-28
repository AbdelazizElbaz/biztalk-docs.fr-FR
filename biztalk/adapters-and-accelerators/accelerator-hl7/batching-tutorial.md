---
title: Didacticiel de traitement par lots | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- batching tutorial
- tutorials, batching tutorial
- batching tutorial, about the tutorial
- batching, tutorial
ms.assetid: e9010638-74cf-47cd-8cc9-9d6fd08a1b8d
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 27e2aff66468c697c92adb4c452250b70dae2e59
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="batching-tutorial"></a><span data-ttu-id="044ec-102">Didacticiel de traitement par lot</span><span class="sxs-lookup"><span data-stu-id="044ec-102">Batching Tutorial</span></span>
<span data-ttu-id="044ec-103">Ce didacticiel fournit des instructions détaillées pour l’utilisation de [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)] pour recevoir et envoyer des messages par lot.</span><span class="sxs-lookup"><span data-stu-id="044ec-103">This tutorial provides step-by-step procedures for using [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)] to receive and send batched messages.</span></span> <span data-ttu-id="044ec-104">Le traitement par lot implique de recevoir et/ou envoyer un groupe de messages individuels (ou les accusés de réception) en tant qu’un seul message composite.</span><span class="sxs-lookup"><span data-stu-id="044ec-104">Batching involves receiving and/or sending a group of individual messages (or acknowledgments) as a single composite message.</span></span>  
  
 <span data-ttu-id="044ec-105">Scénarios de traitement par lot de messages prend en charge de BTAHL7 les trois suivantes :</span><span class="sxs-lookup"><span data-stu-id="044ec-105">BTAHL7 supports the following three message batching scenarios:</span></span>  
  
-   <span data-ttu-id="044ec-106">**Par lot entrant fragmenté**.</span><span class="sxs-lookup"><span data-stu-id="044ec-106">**Fragmented inbound batch**.</span></span> <span data-ttu-id="044ec-107">Dans ce scénario, BTAHL7 reçoit un lot de messages HL7, puis achemine les messages individuels dans le système de destination.</span><span class="sxs-lookup"><span data-stu-id="044ec-107">In this scenario, BTAHL7 receives an HL7 message batch, and then routes the individual messages to the destination system.</span></span>  
  
-   <span data-ttu-id="044ec-108">**Traitement par lots dans / hors du lot**. BTAHL7 reçoit un lot de messages HL7, vérifie les messages individuels dans le lot, puis achemine le lot de messages vers le système de destination.</span><span class="sxs-lookup"><span data-stu-id="044ec-108">**Batch in/batch out**. BTAHL7 receives an HL7 message batch, verifies the individual messages within the batch, and then routes the message batch to the destination system.</span></span>  
  
-   <span data-ttu-id="044ec-109">**Créer (ou un lot de traitement par lot sortant)**.</span><span class="sxs-lookup"><span data-stu-id="044ec-109">**Create batch (or outbound batching)**.</span></span> <span data-ttu-id="044ec-110">BTAHL7 reçoit des messages individuels et les lots avant de les router vers le système de destination.</span><span class="sxs-lookup"><span data-stu-id="044ec-110">BTAHL7 receives individual messages and batches them before routing them to the destination system.</span></span>  
  
 <span data-ttu-id="044ec-111">Ce didacticiel inclut des composants pour chacun des trois scénarios de traitement par lot.</span><span class="sxs-lookup"><span data-stu-id="044ec-111">This tutorial includes parts for each of the three batching scenarios.</span></span> <span data-ttu-id="044ec-112">Utilisez les trois parties du didacticiel dans l’ordre fourni ; partie 1 contient les étapes requises pour la partie 2 et 3.</span><span class="sxs-lookup"><span data-stu-id="044ec-112">Use the three parts of the tutorial in the order provided; part 1 contains prerequisite steps for part 2 and part 3.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="044ec-113">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="044ec-113">In This Section</span></span>  
  
-   [<span data-ttu-id="044ec-114">Préparation à l’utilisation du didacticiel de traitement par lot</span><span class="sxs-lookup"><span data-stu-id="044ec-114">Preparing to Use the Batching Tutorial</span></span>](../../adapters-and-accelerators/accelerator-hl7/preparing-to-use-the-batching-tutorial.md)  
  
-   [<span data-ttu-id="044ec-115">Partie 1 : Scénario de lot entrant fragmenté</span><span class="sxs-lookup"><span data-stu-id="044ec-115">Part 1: Fragmented Inbound Batch Scenario</span></span>](../../adapters-and-accelerators/accelerator-hl7/part-1-fragmented-inbound-batch-scenario.md)  
  
-   [<span data-ttu-id="044ec-116">Partie 2 : Traitement par lots de dans / lots scénario</span><span class="sxs-lookup"><span data-stu-id="044ec-116">Part 2: Batch In/Batch Out Scenario</span></span>](../../adapters-and-accelerators/accelerator-hl7/part-2-batch-in-batch-out-scenario.md)  
  
-   [<span data-ttu-id="044ec-117">Partie 3 : Scénario de traitement par lots Créer</span><span class="sxs-lookup"><span data-stu-id="044ec-117">Part 3: Create-Batch Scenario</span></span>](../../adapters-and-accelerators/accelerator-hl7/part-3-create-batch-scenario.md)