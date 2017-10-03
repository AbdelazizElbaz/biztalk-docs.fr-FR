---
title: Lots de messages | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5f893d16-2670-4463-9a89-6f5be912a045
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 25866ac076d77eae13d2ab5378a7582f584b6670
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="message-batches"></a><span data-ttu-id="8d1cd-102">Lots de messages</span><span class="sxs-lookup"><span data-stu-id="8d1cd-102">Message Batches</span></span>
<span data-ttu-id="8d1cd-103">Lorsque votre adaptateur possède un groupe de messages devant être traités en même temps, il est préférable de les regrouper par lot afin d'optimiser les performances.</span><span class="sxs-lookup"><span data-stu-id="8d1cd-103">When your adapter has a group of messages that need to be processed at one time, you should batch these messages to optimize performance.</span></span> <span data-ttu-id="8d1cd-104">Dans le contexte de la programmation, les lots de messages sont des ensembles de messages associés à une opération.</span><span class="sxs-lookup"><span data-stu-id="8d1cd-104">Programmatically, message batches are collections of messages with an associated operation.</span></span> <span data-ttu-id="8d1cd-105">En regroupant les messages dans un lot au lieu de l’envoi de chaque message individuellement, vous optimisez l’utilisation des ressources et des tâches de traitement.</span><span class="sxs-lookup"><span data-stu-id="8d1cd-105">By grouping messages in a batch rather than submitting each message individually, you optimize the use of resources and processing tasks.</span></span> [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="8d1cd-106">utilise le traitement par lot pour :</span><span class="sxs-lookup"><span data-stu-id="8d1cd-106"> uses batching to:</span></span>  
  
-   <span data-ttu-id="8d1cd-107">amortir le coût de la transaction sur plusieurs messages ;</span><span class="sxs-lookup"><span data-stu-id="8d1cd-107">Amortize the cost of the transaction across many messages.</span></span>  
  
-   <span data-ttu-id="8d1cd-108">augmenter la vitesse en réduisant le nombre interne d'allers-retours vers une base de données ;</span><span class="sxs-lookup"><span data-stu-id="8d1cd-108">Increase speed by reducing the internal number of database round trips.</span></span>  
  
-   <span data-ttu-id="8d1cd-109">optimiser l'utilisation de la réserve de threads de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] en traitant les messages de manière asynchrone.</span><span class="sxs-lookup"><span data-stu-id="8d1cd-109">Make more efficient use of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] thread pool by processing the messages asynchronously.</span></span>  
  
 <span data-ttu-id="8d1cd-110">Un lot est une unité de travail atomique.</span><span class="sxs-lookup"><span data-stu-id="8d1cd-110">A batch is a unit of work that is atomic.</span></span> <span data-ttu-id="8d1cd-111">En d'autres termes, soit toutes les opérations qu'il contient réussissent, soit elles échouent toutes.</span><span class="sxs-lookup"><span data-stu-id="8d1cd-111">That is, either all operations in it succeed or all operations in it fail.</span></span> <span data-ttu-id="8d1cd-112">Si une opération d'un lot réussit mais qu'une autre opération échoue, toutes les opérations qui constituent ce lot sont invalidées et les messages doivent être resoumis.</span><span class="sxs-lookup"><span data-stu-id="8d1cd-112">If one operation in a batch succeeds but another operation fails, all the operations that make up the batch are invalidated and the messages must be resubmitted.</span></span> <span data-ttu-id="8d1cd-113">Cela signifie qu'un adaptateur doit effectuer trois actions lorsqu'un lot échoue :</span><span class="sxs-lookup"><span data-stu-id="8d1cd-113">This means that an adapter must do three things in response to a failed batch:</span></span>  
  
-   <span data-ttu-id="8d1cd-114">déterminer les messages ayant échoué ;</span><span class="sxs-lookup"><span data-stu-id="8d1cd-114">Determine which messages failed.</span></span>  
  
-   <span data-ttu-id="8d1cd-115">décider de ce qu'il doit advenir des messages ayant échoué ;</span><span class="sxs-lookup"><span data-stu-id="8d1cd-115">Decide what to do with the failed messages.</span></span>  
  
-   <span data-ttu-id="8d1cd-116">resoumettre les messages qui n'ont pas échoué.</span><span class="sxs-lookup"><span data-stu-id="8d1cd-116">Resubmit the messages that did not fail.</span></span>