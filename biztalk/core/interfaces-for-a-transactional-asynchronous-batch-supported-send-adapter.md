---
title: "Interfaces pour un adaptateur d’envoi de lot est pris en charge asynchrone transactionnelle | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e5b2dbdf-e6ba-4b58-a0a5-fc78feaf5c35
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 948000883c092c8e247b1d4f41fb2bc7e2280e40
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="interfaces-for-a-transactional-asynchronous-batch-supported-send-adapter"></a><span data-ttu-id="6bfee-102">Interfaces pour un adaptateur d'envoi asynchrone transactionnel pris en charge par lot</span><span class="sxs-lookup"><span data-stu-id="6bfee-102">Interfaces for a Transactional Asynchronous Batch-Supported Send Adapter</span></span>
<span data-ttu-id="6bfee-103">Un adaptateur d'envoi peut créer et contrôler des transactions lorsque la transmission transactionnelle des messages est requise.</span><span class="sxs-lookup"><span data-stu-id="6bfee-103">A send adapter can create and control transactions when transactional transmission of messages is required.</span></span> <span data-ttu-id="6bfee-104">Pour prendre en charge l'envoi transactionnel, l'adaptateur doit implémenter les interfaces suivantes :</span><span class="sxs-lookup"><span data-stu-id="6bfee-104">To support transactional send, an adapter needs to implement the following interfaces:</span></span>  
  
-   <span data-ttu-id="6bfee-105">**IBTTransport**</span><span class="sxs-lookup"><span data-stu-id="6bfee-105">**IBTTransport**</span></span>  
  
-   <span data-ttu-id="6bfee-106">**IBaseComponent**</span><span class="sxs-lookup"><span data-stu-id="6bfee-106">**IBaseComponent**</span></span>  
  
-   <span data-ttu-id="6bfee-107">**IBTTransportControl**</span><span class="sxs-lookup"><span data-stu-id="6bfee-107">**IBTTransportControl**</span></span>  
  
-   <span data-ttu-id="6bfee-108">**IPersistPropertyBag**</span><span class="sxs-lookup"><span data-stu-id="6bfee-108">**IPersistPropertyBag**</span></span>  
  
-   <span data-ttu-id="6bfee-109">**IBTBatchTransmitter**</span><span class="sxs-lookup"><span data-stu-id="6bfee-109">**IBTBatchTransmitter**</span></span>  
  
-   <span data-ttu-id="6bfee-110">**IBTTransmitterBatch**</span><span class="sxs-lookup"><span data-stu-id="6bfee-110">**IBTTransmitterBatch**</span></span>  
  
-   <span data-ttu-id="6bfee-111">**IBTBatchCallBack**</span><span class="sxs-lookup"><span data-stu-id="6bfee-111">**IBTBatchCallBack**</span></span>  
  
 <span data-ttu-id="6bfee-112">Un adaptateur crée une transaction MSDTC et retourne un pointeur vers cet objet dans l’appel à la **BeginBatch** méthode de la **IBTTransmitterBatch** interface.</span><span class="sxs-lookup"><span data-stu-id="6bfee-112">An adapter creates an MSDTC transaction and returns a pointer to that object in the call to the **BeginBatch** method of the **IBTTransmitterBatch** interface.</span></span> <span data-ttu-id="6bfee-113">Le moteur de messagerie appelle cette méthode pour obtenir un lot grâce auquel il envoie les messages sortants vers l'adaptateur d'envoi.</span><span class="sxs-lookup"><span data-stu-id="6bfee-113">The Messaging Engine calls this method to obtain a batch with which it posts outgoing messages to the send adapter.</span></span> <span data-ttu-id="6bfee-114">Lorsque l’adaptateur termine l’opération d’envoi et valide ou annule une transaction, il notifie le moteur de messagerie du résultat de la transaction à l’aide de la **DTCCommitConfirm** méthode de la **IBTDTCCommitConfirm**  interface.</span><span class="sxs-lookup"><span data-stu-id="6bfee-114">When the adapter finishes the send operation and commits or rolls back a transaction, it notifies the Messaging Engine of the result of the transaction by using the **DTCCommitConfirm** method of the **IBTDTCCommitConfirm** interface.</span></span>  
  
 <span data-ttu-id="6bfee-115">L'illustration suivante indique l'interaction entre le proxy de transport et l'adaptateur d'envoi lors d'une opération d'envoi transactionnel.</span><span class="sxs-lookup"><span data-stu-id="6bfee-115">The following figure shows the interaction between the transport proxy and the send adapter when performing a transactional send operation.</span></span>  
  
 ![](../core/media/ebiz-sdk-devadapter8.gif "ebiz_sdk_devadapter8")  
<span data-ttu-id="6bfee-116">Workflow pour l'envoi d'un message transactionnel de manière asynchrone</span><span class="sxs-lookup"><span data-stu-id="6bfee-116">Workflow for sending a transactional message asynchronously</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6bfee-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6bfee-117">See Also</span></span>  
 <span data-ttu-id="6bfee-118">[Variables d’adaptateur](../core/adapter-variables.md) </span><span class="sxs-lookup"><span data-stu-id="6bfee-118">[Adapter Variables](../core/adapter-variables.md) </span></span>  
 <span data-ttu-id="6bfee-119">[Développement d’un adaptateur d’envoi](../core/developing-a-send-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="6bfee-119">[Developing a Send Adapter](../core/developing-a-send-adapter.md) </span></span>  
 <span data-ttu-id="6bfee-120">[Instanciation et initialisation d’un adaptateur d’envoi](../core/instantiating-and-initializing-a-send-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="6bfee-120">[Instantiating and Initializing a Send Adapter](../core/instantiating-and-initializing-a-send-adapter.md) </span></span>  
 <span data-ttu-id="6bfee-121">[Interfaces pour un envoi synchrone adaptateur](../core/interfaces-for-a-synchronous-send-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="6bfee-121">[Interfaces for a Synchronous Send Adapter](../core/interfaces-for-a-synchronous-send-adapter.md) </span></span>  
 <span data-ttu-id="6bfee-122">[Interfaces pour un envoi asynchrone adaptateur](../core/interfaces-for-an-asynchronous-send-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="6bfee-122">[Interfaces for an Asynchronous Send Adapter](../core/interfaces-for-an-asynchronous-send-adapter.md) </span></span>  
 <span data-ttu-id="6bfee-123">[Interfaces pour un adaptateur d’envoi synchrone de lot est pris en charge](../core/interfaces-for-a-synchronous-batch-supported-send-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="6bfee-123">[Interfaces for a Synchronous Batch-Supported Send Adapter](../core/interfaces-for-a-synchronous-batch-supported-send-adapter.md) </span></span>  
 <span data-ttu-id="6bfee-124">[Interfaces pour un adaptateur d’envoi asynchrone de lot est pris en charge](../core/interfaces-for-an-asynchronous-batch-supported-send-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="6bfee-124">[Interfaces for an Asynchronous Batch-Supported Send Adapter](../core/interfaces-for-an-asynchronous-batch-supported-send-adapter.md) </span></span>  
 [<span data-ttu-id="6bfee-125">Adaptateur d’envoi des interfaces pour une type sollicitation-réponse</span><span class="sxs-lookup"><span data-stu-id="6bfee-125">Interfaces for a Solicit-Response Send Adapter</span></span>](../core/interfaces-for-a-solicit-response-send-adapter.md)