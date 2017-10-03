---
title: "Interfaces pour une demande-réponse synchrone adaptateur de réception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d0c60832-52b5-4d2c-81ec-94c46c375b15
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9abd84bab5da623c2dff61c6e07a5898110588af
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="interfaces-for-a-synchronous-request-response-receive-adapter"></a><span data-ttu-id="3a4df-102">Interfaces pour adaptateur de réception synchrone de type requête-réponse</span><span class="sxs-lookup"><span data-stu-id="3a4df-102">Interfaces for a Synchronous Request-Response Receive Adapter</span></span>
<span data-ttu-id="3a4df-103">Tous les adaptateurs de réception doivent implémenter les interfaces suivantes pour fonctionner en mode de requête-réponse :</span><span class="sxs-lookup"><span data-stu-id="3a4df-103">All receive adapters need to implement the following interfaces to work in request-response mode:</span></span>  
  
-   <span data-ttu-id="3a4df-104">**IBTTransport**</span><span class="sxs-lookup"><span data-stu-id="3a4df-104">**IBTTransport**</span></span>  
  
-   <span data-ttu-id="3a4df-105">**IBTTransportControl** (adaptateurs normaux uniquement)</span><span class="sxs-lookup"><span data-stu-id="3a4df-105">**IBTTransportControl** (regular adapters only)</span></span>  
  
-   <span data-ttu-id="3a4df-106">**IBTTransportConfig**</span><span class="sxs-lookup"><span data-stu-id="3a4df-106">**IBTTransportConfig**</span></span>  
  
-   <span data-ttu-id="3a4df-107">**IBaseComponent**</span><span class="sxs-lookup"><span data-stu-id="3a4df-107">**IBaseComponent**</span></span>  
  
-   <span data-ttu-id="3a4df-108">**IPersistPropertyBag**</span><span class="sxs-lookup"><span data-stu-id="3a4df-108">**IPersistPropertyBag**</span></span>  
  
-   <span data-ttu-id="3a4df-109">**IBTBatchCallBack**</span><span class="sxs-lookup"><span data-stu-id="3a4df-109">**IBTBatchCallBack**</span></span>  
  
-   <span data-ttu-id="3a4df-110">**IBTTransmitter**</span><span class="sxs-lookup"><span data-stu-id="3a4df-110">**IBTTransmitter**</span></span>  
  
 <span data-ttu-id="3a4df-111">Les adaptateurs de réception qui prennent en charge les protocoles de requête-réponse (l'adaptateur de réception HTTP par exemple) effectuent les opérations suivantes lorsqu'ils envoient des messages de requête :</span><span class="sxs-lookup"><span data-stu-id="3a4df-111">Receive adapters that support request-response protocols (for example, the HTTP receive adapter) perform the following actions when submitting request messages:</span></span>  
  
1.  <span data-ttu-id="3a4df-112">L'adaptateur de réception reçoit les messages de requête entrants.</span><span class="sxs-lookup"><span data-stu-id="3a4df-112">The receive adapter receives incoming request messages.</span></span> <span data-ttu-id="3a4df-113">Il obtient un lot du proxy de transport en appelant le **GetBatch** méthode de la **IBTTransportProxy** interface.</span><span class="sxs-lookup"><span data-stu-id="3a4df-113">It obtains a batch from the transport proxy by calling the **GetBatch** method of the **IBTTransportProxy** interface.</span></span> <span data-ttu-id="3a4df-114">Dans cet appel, l’adaptateur transmet un pointeur de rappel à son implémentation de la **IBTBatchCallBack.BatchComplete** (méthode).</span><span class="sxs-lookup"><span data-stu-id="3a4df-114">In this call the adapter passes in a callback pointer to its implementation of the **IBTBatchCallBack.BatchComplete** method.</span></span>  
  
2.  <span data-ttu-id="3a4df-115">L’adaptateur ajoute les messages de demande dans le lot en appelant le **SubmitRequestMessage** méthode de la **IBTTransportBatch** interface, une fois pour chaque message de demande.</span><span class="sxs-lookup"><span data-stu-id="3a4df-115">The adapter adds request messages into the batch by calling the **SubmitRequestMessage** method of the **IBTTransportBatch** interface, once for each request message.</span></span>  
  
3.  <span data-ttu-id="3a4df-116">Lorsque tous les messages ont été ajoutés, l’adaptateur appelle la **fait**méthode de la **IBTTransportBatch** interface, qui envoie le lot au moteur de messagerie via le proxy de transport.</span><span class="sxs-lookup"><span data-stu-id="3a4df-116">When all the messages have been added, the adapter calls the **Done**method of the **IBTTransportBatch** interface, which submits the batch to the Messaging Engine through the transport proxy.</span></span>  
  
4.  <span data-ttu-id="3a4df-117">Une fois que le lot a été traité, le moteur de messagerie appelle l’adaptateur **IBTBatchCallBack.BatchComplete** méthode de rappel via le proxy de transport.</span><span class="sxs-lookup"><span data-stu-id="3a4df-117">After the batch has been processed, the Messaging Engine invokes the adapter's **IBTBatchCallBack.BatchComplete** callback method through the transport proxy.</span></span> <span data-ttu-id="3a4df-118">L'état de l'envoi est transmis à l'adaptateur sous forme de tableau de valeurs HRESULT correspondant à chaque message du lot.</span><span class="sxs-lookup"><span data-stu-id="3a4df-118">The status of the submission is passed to the adapter as an array of HRESULT values corresponding to each message in the batch.</span></span> <span data-ttu-id="3a4df-119">Si le lot échoue, que ce soit dans le pipeline ou dans l'orchestration, le message d'erreur SOAP est retourné à l'adaptateur en réponse.</span><span class="sxs-lookup"><span data-stu-id="3a4df-119">If the batch fails, either in the pipeline or in the orchestration, the SOAP fault message is returned to the adapter as a response.</span></span>  
  
5.  <span data-ttu-id="3a4df-120">Les messages de requête entrants sont susceptibles d'avoir des abonnés à l'orchestration.</span><span class="sxs-lookup"><span data-stu-id="3a4df-120">The incoming request messages may have orchestration subscribers.</span></span> <span data-ttu-id="3a4df-121">Une fois que l’orchestration terminée et le message de demande a été traité, le moteur de messagerie envoie le message de réponse via le proxy de transport à l’adaptateur en appelant l’adaptateur **TransmitMessage** à partir de la (méthode) **IBTTransmitter** interface.</span><span class="sxs-lookup"><span data-stu-id="3a4df-121">After the orchestration completes and the request message has been processed, the Messaging Engine sends the response message through the transport proxy to the adapter by calling the adapter's **TransmitMessage** method from the **IBTTransmitter** interface.</span></span>  
  
6.  <span data-ttu-id="3a4df-122">L'adaptateur envoie un message de réponse et supprime le message d'origine de la base de données MessageBox.</span><span class="sxs-lookup"><span data-stu-id="3a4df-122">The adapter sends a response message and deletes the original message from the MessageBox database.</span></span>  
  
 <span data-ttu-id="3a4df-123">Le schéma ci-dessous indique les interactions d'objets impliquées dans la création d'un adaptateur de réception synchrone de type requête-réponse.</span><span class="sxs-lookup"><span data-stu-id="3a4df-123">The following figure shows the object interactions involved in creating a synchronous request-response receive adapter.</span></span>  
  
 ![](../core/media/ebiz-sdk-devadapter3.gif "ebiz_sdk_devadapter3")  
<span data-ttu-id="3a4df-124">Workflow d'un adaptateur de réception envoyant un message synchrone</span><span class="sxs-lookup"><span data-stu-id="3a4df-124">Workflow for a receive adapter submitting a synchronous message</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a4df-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3a4df-125">See Also</span></span>  
 <span data-ttu-id="3a4df-126">[Variables d’adaptateur](../core/adapter-variables.md) </span><span class="sxs-lookup"><span data-stu-id="3a4df-126">[Adapter Variables](../core/adapter-variables.md) </span></span>  
 <span data-ttu-id="3a4df-127">[Développement d’un adaptateur de réception](../core/developing-a-receive-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="3a4df-127">[Developing a Receive Adapter](../core/developing-a-receive-adapter.md) </span></span>  
 <span data-ttu-id="3a4df-128">[Instanciation et initialisation un adaptateur de réception](../core/instantiating-and-initializing-a-receive-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="3a4df-128">[Instantiating and Initializing a Receive Adapter](../core/instantiating-and-initializing-a-receive-adapter.md) </span></span>  
 <span data-ttu-id="3a4df-129">[Adaptateur de réception des interfaces pour In-Process](../core/interfaces-for-an-in-process-receive-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="3a4df-129">[Interfaces for an In-Process Receive Adapter](../core/interfaces-for-an-in-process-receive-adapter.md) </span></span>  
 <span data-ttu-id="3a4df-130">[Adaptateur de réception des interfaces pour un hôte isolé](../core/interfaces-for-an-isolated-receive-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="3a4df-130">[Interfaces for an Isolated Receive Adapter](../core/interfaces-for-an-isolated-receive-adapter.md) </span></span>  
 <span data-ttu-id="3a4df-131">[Interfaces pour un lot pris en charge par l’adaptateur de réception](../core/interfaces-for-a-batch-supported-receive-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="3a4df-131">[Interfaces for a Batch-Supported Receive Adapter](../core/interfaces-for-a-batch-supported-receive-adapter.md) </span></span>  
 [<span data-ttu-id="3a4df-132">Adaptateur de réception des interfaces pour un transactionnel pris en charge par lot</span><span class="sxs-lookup"><span data-stu-id="3a4df-132">Interfaces for a Transactional Batch-Supported Receive Adapter</span></span>](../core/interfaces-for-a-transactional-batch-supported-receive-adapter.md)