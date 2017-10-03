---
title: "Adaptateur d’envoi des interfaces pour une type sollicitation-réponse | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c54650e8-dbfb-4c66-843b-0b82c8183dd4
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fb8ce9b625bfea144f9a4a615a604efdbe2a3cb1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="interfaces-for-a-solicit-response-send-adapter"></a><span data-ttu-id="c47ee-102">Interfaces pour un adaptateur d'envoi de sollicitation-réponse</span><span class="sxs-lookup"><span data-stu-id="c47ee-102">Interfaces for a Solicit-Response Send Adapter</span></span>
<span data-ttu-id="c47ee-103">Les adaptateurs d'envoi utilisent le même mécanisme de lot que les adaptateurs de réception pour envoyer les messages de réponse au serveur.</span><span class="sxs-lookup"><span data-stu-id="c47ee-103">Send adapters use the same batch mechanism as receive adapters to submit response messages back into the server.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c47ee-104">Il est recommandé qu'un adaptateur de sollicitation-réponse traite les messages de manière asynchrone.</span><span class="sxs-lookup"><span data-stu-id="c47ee-104">It is recommended that a solicit-response adapter is process messages asynchronously.</span></span> <span data-ttu-id="c47ee-105">S'il traite les messages de manière synchrone, ces derniers risquent d'être dupliqués.</span><span class="sxs-lookup"><span data-stu-id="c47ee-105">If the adapter processes message in a synchronous manner, there is a risk of message duplication.</span></span>  
  
 <span data-ttu-id="c47ee-106">Les adaptateurs d'envoi doivent implémenter les interfaces suivantes pour fonctionner en mode de sollicitation-réponse :</span><span class="sxs-lookup"><span data-stu-id="c47ee-106">Send adapters need to implement the following interfaces to work in solicit-response mode:</span></span>  
  
-   <span data-ttu-id="c47ee-107">**IBTTransport**</span><span class="sxs-lookup"><span data-stu-id="c47ee-107">**IBTTransport**</span></span>  
  
-   <span data-ttu-id="c47ee-108">**IBaseComponent**</span><span class="sxs-lookup"><span data-stu-id="c47ee-108">**IBaseComponent**</span></span>  
  
-   <span data-ttu-id="c47ee-109">**IBTTransportControl**</span><span class="sxs-lookup"><span data-stu-id="c47ee-109">**IBTTransportControl**</span></span>  
  
-   <span data-ttu-id="c47ee-110">**IPersistPropertyBag**</span><span class="sxs-lookup"><span data-stu-id="c47ee-110">**IPersistPropertyBag**</span></span>  
  
-   <span data-ttu-id="c47ee-111">**IBTTransmitter**</span><span class="sxs-lookup"><span data-stu-id="c47ee-111">**IBTTransmitter**</span></span>  
  
-   <span data-ttu-id="c47ee-112">**IBTTransmitterBatch** et **IBTBatchTransmitter** (si le traitement par lot d’envoi est requis)</span><span class="sxs-lookup"><span data-stu-id="c47ee-112">**IBTTransmitterBatch** and **IBTBatchTransmitter** (if send batching is required)</span></span>  
  
-   <span data-ttu-id="c47ee-113">**IBTBatchCallBack**</span><span class="sxs-lookup"><span data-stu-id="c47ee-113">**IBTBatchCallBack**</span></span>  
  
 <span data-ttu-id="c47ee-114">Les étapes de l'interaction des objets sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="c47ee-114">The steps involved in the object interaction are as follows:</span></span>  
  
1.  <span data-ttu-id="c47ee-115">Une fois que l'adaptateur a envoyé un message de sollicitation, il reçoit en retour un message de réponse du serveur de destination.</span><span class="sxs-lookup"><span data-stu-id="c47ee-115">After the adapter sends a solicit message, it receives back a response message from that destination server.</span></span> <span data-ttu-id="c47ee-116">Il obtient alors un lot du proxy de transport.</span><span class="sxs-lookup"><span data-stu-id="c47ee-116">It then obtains a batch from the transport proxy.</span></span>  
  
2.  <span data-ttu-id="c47ee-117">L’adaptateur ajoute le message de réponse au lot en appelant **IBTTransportProxy::SubmitResponseMessage**.</span><span class="sxs-lookup"><span data-stu-id="c47ee-117">The adapter adds the response message to the batch by calling **IBTTransportProxy::SubmitResponseMessage**.</span></span>  
  
3.  <span data-ttu-id="c47ee-118">L’adaptateur envoie le lot en appelant **IBTTransportProxy::Done** en passant un pointeur vers son **IBTBatchComplete** interface pour le rappel du moteur de messagerie.</span><span class="sxs-lookup"><span data-stu-id="c47ee-118">The adapter submits the batch by calling **IBTTransportProxy::Done** passing in a pointer to its **IBTBatchComplete** interface for the callback from the Messaging Engine.</span></span>  
  
4.  <span data-ttu-id="c47ee-119">Le moteur de messagerie appelle l’adaptateur **IBTBatchCallBack::BatchComplete** méthode de rappel à l’aide du proxy de transport informer du résultat de l’opération d’envoi.</span><span class="sxs-lookup"><span data-stu-id="c47ee-119">The Messaging Engine calls the adapter's **IBTBatchCallBack::BatchComplete** callback method using the transport proxy notifying it of the result of submission operation.</span></span>  
  
 <span data-ttu-id="c47ee-120">Le schéma ci-dessous indique les interactions d'objets impliquées dans la création d'un adaptateur d'envoi de sollicitation-réponse.</span><span class="sxs-lookup"><span data-stu-id="c47ee-120">The following figure shows the object interactions involved in creating a solicit-response send adapter.</span></span>  
  
 ![](../core/media/ebiz-sdk-devadapter13.gif "ebiz_sdk_devadapter13")  
<span data-ttu-id="c47ee-121">Diagramme d'interaction d'un adaptateur d'envoi de sollicitation-réponse</span><span class="sxs-lookup"><span data-stu-id="c47ee-121">Interaction diagram for a solicit-response send adapter</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c47ee-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c47ee-122">See Also</span></span>  
 <span data-ttu-id="c47ee-123">[Variables d’adaptateur](../core/adapter-variables.md) </span><span class="sxs-lookup"><span data-stu-id="c47ee-123">[Adapter Variables](../core/adapter-variables.md) </span></span>  
 <span data-ttu-id="c47ee-124">[Développement d’un adaptateur d’envoi](../core/developing-a-send-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="c47ee-124">[Developing a Send Adapter](../core/developing-a-send-adapter.md) </span></span>  
 <span data-ttu-id="c47ee-125">[Instanciation et initialisation d’un adaptateur d’envoi](../core/instantiating-and-initializing-a-send-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="c47ee-125">[Instantiating and Initializing a Send Adapter](../core/instantiating-and-initializing-a-send-adapter.md) </span></span>  
 <span data-ttu-id="c47ee-126">[Interfaces pour un envoi synchrone adaptateur](../core/interfaces-for-a-synchronous-send-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="c47ee-126">[Interfaces for a Synchronous Send Adapter](../core/interfaces-for-a-synchronous-send-adapter.md) </span></span>  
 <span data-ttu-id="c47ee-127">[Interfaces pour un envoi asynchrone adaptateur](../core/interfaces-for-an-asynchronous-send-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="c47ee-127">[Interfaces for an Asynchronous Send Adapter](../core/interfaces-for-an-asynchronous-send-adapter.md) </span></span>  
 <span data-ttu-id="c47ee-128">[Interfaces pour un adaptateur d’envoi synchrone de lot est pris en charge](../core/interfaces-for-a-synchronous-batch-supported-send-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="c47ee-128">[Interfaces for a Synchronous Batch-Supported Send Adapter](../core/interfaces-for-a-synchronous-batch-supported-send-adapter.md) </span></span>  
 <span data-ttu-id="c47ee-129">[Interfaces pour un adaptateur d’envoi asynchrone de lot est pris en charge](../core/interfaces-for-an-asynchronous-batch-supported-send-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="c47ee-129">[Interfaces for an Asynchronous Batch-Supported Send Adapter](../core/interfaces-for-an-asynchronous-batch-supported-send-adapter.md) </span></span>  
 [<span data-ttu-id="c47ee-130">Interfaces pour un adaptateur d’envoi de lot est pris en charge asynchrone transactionnelle</span><span class="sxs-lookup"><span data-stu-id="c47ee-130">Interfaces for a Transactional Asynchronous Batch-Supported Send Adapter</span></span>](../core/interfaces-for-a-transactional-asynchronous-batch-supported-send-adapter.md)