---
title: "Adaptateur de réception des interfaces pour une prise en charge de traitement par lots | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5289e8b8-4447-4196-9f7c-5e60c6598d8d
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 27b51a67f63f3088ce64c9db35c368289ce156d2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="interfaces-for-a-transactional-batch-supported-receive-adapter"></a><span data-ttu-id="94c70-102">Interfaces pour un adaptateur de réception transactionnel pris en charge par lot</span><span class="sxs-lookup"><span data-stu-id="94c70-102">Interfaces for a Transactional Batch-Supported Receive Adapter</span></span>
<span data-ttu-id="94c70-103">Un adaptateur de réception crée et contrôle les transactions lorsque l'envoi transactionnel des messages est requis.</span><span class="sxs-lookup"><span data-stu-id="94c70-103">A receive adapter creates and controls transactions when the transactional submission of messages is required.</span></span>  
  
 <span data-ttu-id="94c70-104">Réception transactionnel adaptateur crée et passe un pointeur à une transaction Microsoft Distributed Transaction Coordinator (MSDTC) le **fait** méthode de la **IBTTransportBatch** interface.</span><span class="sxs-lookup"><span data-stu-id="94c70-104">A transactional receive adapter creates and passes a pointer to a Microsoft Distributed Transaction Coordinator (MSDTC) transaction on the **Done** method of the **IBTTransportBatch** interface.</span></span> <span data-ttu-id="94c70-105">Ce faisant, toutes les opérations de traitement par lot sont réalisées dans l'étendue de cet objet transaction spécifique.</span><span class="sxs-lookup"><span data-stu-id="94c70-105">This ensures that all batch operations are performed in the scope of that specific transaction object.</span></span> <span data-ttu-id="94c70-106">Lorsque l'envoi du lot est terminé, la méthode de rappel de l'adaptateur valide ou annule la transaction.</span><span class="sxs-lookup"><span data-stu-id="94c70-106">When the batch submission completes, the adapter callback method commits or rolls back the transaction.</span></span> <span data-ttu-id="94c70-107">L'action ensuite réalisée dépend de l'état renvoyé par le proxy de transport, et éventuellement d'autres travaux associés à la transaction réalisés par l'adaptateur et non visibles pour le proxy de transport.</span><span class="sxs-lookup"><span data-stu-id="94c70-107">Which action it takes depends upon the status returned from the transport proxy, and possibly upon other transaction-related work that the adapter does that is not visible to the transport proxy.</span></span> <span data-ttu-id="94c70-108">L'adaptateur détermine si la transaction est un échec ou un succès.</span><span class="sxs-lookup"><span data-stu-id="94c70-108">The adapter determines whether the transaction failed or succeeded.</span></span> <span data-ttu-id="94c70-109">L’adaptateur renvoie le résultat de la transaction (commit ou rollback) pour le proxy de transport à l’aide de la **DTCCommitConfirm** méthode de la**IBTDTCCommitConfirm** interface.</span><span class="sxs-lookup"><span data-stu-id="94c70-109">The adapter reports the result of the transaction (commit or rollback) back to the transport proxy by using the **DTCCommitConfirm** method of the**IBTDTCCommitConfirm** interface.</span></span> <span data-ttu-id="94c70-110">Il transmet la valeur `true` en cas de succès de la transaction ou la valeur `false` en cas d'échec.</span><span class="sxs-lookup"><span data-stu-id="94c70-110">It passes in `true` for a successful transaction or `false` for a failure.</span></span>  
  
 <span data-ttu-id="94c70-111">L'illustration suivante indique les interactions d'objets impliquées dans la création d'un adaptateur de réception transactionnel pris en charge par lot.</span><span class="sxs-lookup"><span data-stu-id="94c70-111">The following figure shows the object interactions involved in creating a transactional batch-supported receive adapter.</span></span>  
  
 ![](../core/media/ebiz-sdk-devadapter2.gif "ebiz_sdk_devadapter2")  
<span data-ttu-id="94c70-112">Workflow d'un adaptateur de réception envoyant un lot de messages à l'aide de transactions DTC</span><span class="sxs-lookup"><span data-stu-id="94c70-112">Workflow for a receive adapter submitting a batch of messages using DTC transactions</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94c70-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="94c70-113">See Also</span></span>  
 <span data-ttu-id="94c70-114">[Variables d’adaptateur](../core/adapter-variables.md) </span><span class="sxs-lookup"><span data-stu-id="94c70-114">[Adapter Variables](../core/adapter-variables.md) </span></span>  
 <span data-ttu-id="94c70-115">[Développement d’un adaptateur de réception](../core/developing-a-receive-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="94c70-115">[Developing a Receive Adapter](../core/developing-a-receive-adapter.md) </span></span>  
 <span data-ttu-id="94c70-116">[Instanciation et initialisation un adaptateur de réception](../core/instantiating-and-initializing-a-receive-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="94c70-116">[Instantiating and Initializing a Receive Adapter](../core/instantiating-and-initializing-a-receive-adapter.md) </span></span>  
 <span data-ttu-id="94c70-117">[Adaptateur de réception des interfaces pour In-Process](../core/interfaces-for-an-in-process-receive-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="94c70-117">[Interfaces for an In-Process Receive Adapter](../core/interfaces-for-an-in-process-receive-adapter.md) </span></span>  
 <span data-ttu-id="94c70-118">[Adaptateur de réception des interfaces pour un hôte isolé](../core/interfaces-for-an-isolated-receive-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="94c70-118">[Interfaces for an Isolated Receive Adapter](../core/interfaces-for-an-isolated-receive-adapter.md) </span></span>  
 <span data-ttu-id="94c70-119">[Interfaces pour un lot pris en charge par l’adaptateur de réception](../core/interfaces-for-a-batch-supported-receive-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="94c70-119">[Interfaces for a Batch-Supported Receive Adapter](../core/interfaces-for-a-batch-supported-receive-adapter.md) </span></span>  
 [<span data-ttu-id="94c70-120">Adaptateur de réception des interfaces pour une demande-réponse synchrone</span><span class="sxs-lookup"><span data-stu-id="94c70-120">Interfaces for a Synchronous Request-Response Receive Adapter</span></span>](../core/interfaces-for-a-synchronous-request-response-receive-adapter.md)