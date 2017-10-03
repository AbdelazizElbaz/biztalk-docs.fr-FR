---
title: Interfaces pour un envoi asynchrone adaptateur | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6a214716-8f39-400d-a111-ba1b92a284b4
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: db156f5a95a088ae706bb2b1c801d8dee89cdece
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="interfaces-for-an-asynchronous-send-adapter"></a><span data-ttu-id="da3a8-102">Interfaces pour un adaptateur d'envoi asynchrone</span><span class="sxs-lookup"><span data-stu-id="da3a8-102">Interfaces for an Asynchronous Send Adapter</span></span>
<span data-ttu-id="da3a8-103">Les adaptateurs qui envoient les messages un par un peuvent les envoyer de manière synchrone ou asynchrone.</span><span class="sxs-lookup"><span data-stu-id="da3a8-103">Adapters sending messages one at a time may send messages either synchronously or asynchronously.</span></span> <span data-ttu-id="da3a8-104">Un adaptateur envoie les messages de manière asynchrone s'il ne bloque pas le thread du proxy de transport mais qu'il utilise à la place un thread distinct pour les opérations d'envoi.</span><span class="sxs-lookup"><span data-stu-id="da3a8-104">An adapter sends messages asynchronously when it does not block the transport proxy thread but rather uses a separate thread while performing the send operations.</span></span> <span data-ttu-id="da3a8-105">Pour pouvoir envoyer les messages de manière asynchrone, l'adaptateur doit implémenter les interfaces suivantes :</span><span class="sxs-lookup"><span data-stu-id="da3a8-105">To be able to send messages asynchronously, an adapter needs to implement the following interfaces:</span></span>  
  
-   <span data-ttu-id="da3a8-106">**IBTTransport**</span><span class="sxs-lookup"><span data-stu-id="da3a8-106">**IBTTransport**</span></span>  
  
-   <span data-ttu-id="da3a8-107">**IBaseComponent**</span><span class="sxs-lookup"><span data-stu-id="da3a8-107">**IBaseComponent**</span></span>  
  
-   <span data-ttu-id="da3a8-108">**IBTTransportControl**</span><span class="sxs-lookup"><span data-stu-id="da3a8-108">**IBTTransportControl**</span></span>  
  
-   <span data-ttu-id="da3a8-109">**IPersistPropertyBag**</span><span class="sxs-lookup"><span data-stu-id="da3a8-109">**IPersistPropertyBag**</span></span>  
  
-   <span data-ttu-id="da3a8-110">**IBTTransmitter**</span><span class="sxs-lookup"><span data-stu-id="da3a8-110">**IBTTransmitter**</span></span>  
  
 <span data-ttu-id="da3a8-111">Les étapes suivantes décrivent la séquence d'actions effectuée par un adaptateur d'envoi afin de transmettre les messages à partir du serveur à la demande du moteur de messagerie.</span><span class="sxs-lookup"><span data-stu-id="da3a8-111">The following steps describe the sequence of actions that the send adapter performs to transmit messages out of the server at the request of the Messaging Engine:</span></span>  
  
1.  <span data-ttu-id="da3a8-112">Le moteur de messagerie utilise le proxy de transport pour transmettre un message sortant à un adaptateur d’envoi en appelant le **TransmitMessage** méthode de la **IBTTransmitter** interface.</span><span class="sxs-lookup"><span data-stu-id="da3a8-112">The Messaging Engine uses the transport proxy to pass an outgoing message to a send adapter by calling the **TransmitMessage** method of the **IBTTransmitter** interface.</span></span>  
  
2.  <span data-ttu-id="da3a8-113">L’adaptateur retourne immédiatement à partir de **TransmitMessage** après avoir stocké le message à envoyer à une file d’attente interne et retourne `False` pour **bDeleteMessage**.</span><span class="sxs-lookup"><span data-stu-id="da3a8-113">The adapter returns immediately from **TransmitMessage** after storing the message to be sent to some internal queue, and returns `False` for **bDeleteMessage**.</span></span> <span data-ttu-id="da3a8-114">Ceci indique au moteur de messagerie que le message sera transmis de manière asynchrone.</span><span class="sxs-lookup"><span data-stu-id="da3a8-114">This tells the Messaging Engine the message will be transmitted in an asynchronous manner.</span></span>  
  
3.  <span data-ttu-id="da3a8-115">L'adaptateur envoie le message en utilisant sa propre réserve de threads.</span><span class="sxs-lookup"><span data-stu-id="da3a8-115">The adapter sends the message using its own thread pool.</span></span>  
  
4.  <span data-ttu-id="da3a8-116">Une fois l'opération d'envoi terminée, l'adaptateur supprime le message d'origine de la base de données MessageBox.</span><span class="sxs-lookup"><span data-stu-id="da3a8-116">After the send operation completes, the adapter deletes the original message from the MessageBox database.</span></span> <span data-ttu-id="da3a8-117">Il obtient un lot du moteur de messagerie en utilisant le **IBTTransportBatch.GetBatch** méthode de proxy de transport, puis appelle **DeleteMessage**.</span><span class="sxs-lookup"><span data-stu-id="da3a8-117">It obtains a batch from the Messaging Engine using the **IBTTransportBatch.GetBatch** method of the transport proxy, and then calls **DeleteMessage**.</span></span>  
  
     <span data-ttu-id="da3a8-118">Le schéma ci-dessous indique les interactions d'objets impliquées dans la création d'un adaptateur d'envoi asynchrone.</span><span class="sxs-lookup"><span data-stu-id="da3a8-118">The following figure shows the object interactions involved in creating an asynchronous send adapter.</span></span>  
  
     ![](../core/media/ebiz-sdk-devadapter5.gif "ebiz_sdk_devadapter5")  
<span data-ttu-id="da3a8-119">Workflow pour l'envoi d'un message de manière asynchrone</span><span class="sxs-lookup"><span data-stu-id="da3a8-119">Workflow for sending a message asynchronously</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="da3a8-120">Nous recommandons que l'adaptateur conserve le décompte du nombre de messages en cours de traitement.</span><span class="sxs-lookup"><span data-stu-id="da3a8-120">We recommend that the adapter keep a count of the messages currently being processed.</span></span> <span data-ttu-id="da3a8-121">L’adaptateur doit bloquer la **Terminate** méthode jusqu'à ce que le nombre de messages a atteint zéro.</span><span class="sxs-lookup"><span data-stu-id="da3a8-121">The adapter should block the **Terminate** method until the message count has reached zero.</span></span> <span data-ttu-id="da3a8-122">Pour les adaptateurs d’envoi, les messages sont en cours de traitement doivent être gérées correctement.</span><span class="sxs-lookup"><span data-stu-id="da3a8-122">For send adapters, messages that are being processed should be handled appropriately.</span></span> <span data-ttu-id="da3a8-123">Cela signifie que tout message correctement remis de manière asynchrone doit être supprimé de la file d'attente de messages de l'application privée de l'adaptateur afin d'éviter que les messages ne soient envoyés deux fois.</span><span class="sxs-lookup"><span data-stu-id="da3a8-123">This means that any message that was successfully delivered asynchronously should be deleted from the adapter's private application message queue to prevent messages from being sent twice.</span></span> <span data-ttu-id="da3a8-124">En général, après avoir **Terminate** est appelée par le moteur de messagerie, il n’accepte pas les demandes de publication des nouveaux messages à partir de l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="da3a8-124">In general, after **Terminate** is called by the Messaging Engine it does not accept requests to publish new messages from the adapter.</span></span> <span data-ttu-id="da3a8-125">La seule exception à cette règle concerne les messages de réponse liés aux paires sollicitation-réponse.</span><span class="sxs-lookup"><span data-stu-id="da3a8-125">The exception to this is response messages related to solicit-response pairs.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da3a8-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="da3a8-126">See Also</span></span>  
 <span data-ttu-id="da3a8-127">[Variables d’adaptateur](../core/adapter-variables.md) </span><span class="sxs-lookup"><span data-stu-id="da3a8-127">[Adapter Variables](../core/adapter-variables.md) </span></span>  
 <span data-ttu-id="da3a8-128">[Développement d’un adaptateur d’envoi](../core/developing-a-send-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="da3a8-128">[Developing a Send Adapter](../core/developing-a-send-adapter.md) </span></span>  
 <span data-ttu-id="da3a8-129">[Instanciation et initialisation d’un adaptateur d’envoi](../core/instantiating-and-initializing-a-send-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="da3a8-129">[Instantiating and Initializing a Send Adapter](../core/instantiating-and-initializing-a-send-adapter.md) </span></span>  
 <span data-ttu-id="da3a8-130">[Interfaces pour un envoi synchrone adaptateur](../core/interfaces-for-a-synchronous-send-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="da3a8-130">[Interfaces for a Synchronous Send Adapter](../core/interfaces-for-a-synchronous-send-adapter.md) </span></span>  
 <span data-ttu-id="da3a8-131">[Interfaces pour un adaptateur d’envoi synchrone de lot est pris en charge](../core/interfaces-for-a-synchronous-batch-supported-send-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="da3a8-131">[Interfaces for a Synchronous Batch-Supported Send Adapter](../core/interfaces-for-a-synchronous-batch-supported-send-adapter.md) </span></span>  
 <span data-ttu-id="da3a8-132">[Interfaces pour un adaptateur d’envoi asynchrone de lot est pris en charge](../core/interfaces-for-an-asynchronous-batch-supported-send-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="da3a8-132">[Interfaces for an Asynchronous Batch-Supported Send Adapter](../core/interfaces-for-an-asynchronous-batch-supported-send-adapter.md) </span></span>  
 <span data-ttu-id="da3a8-133">[Interfaces pour un adaptateur d’envoi de lot est pris en charge asynchrone transactionnelle](../core/interfaces-for-a-transactional-asynchronous-batch-supported-send-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="da3a8-133">[Interfaces for a Transactional Asynchronous Batch-Supported Send Adapter](../core/interfaces-for-a-transactional-asynchronous-batch-supported-send-adapter.md) </span></span>  
 [<span data-ttu-id="da3a8-134">Adaptateur d’envoi des interfaces pour une type sollicitation-réponse</span><span class="sxs-lookup"><span data-stu-id="da3a8-134">Interfaces for a Solicit-Response Send Adapter</span></span>](../core/interfaces-for-a-solicit-response-send-adapter.md)