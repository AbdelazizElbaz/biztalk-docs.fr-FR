---
title: "Adaptateur d’envoi de lot est pris en charge des interfaces pour synchrone | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2b191c41-ca4f-4d2b-bd15-a93ad87a743d
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3ab61fd6624468e0464cfe0c648fcc868bd20005
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="interfaces-for-a-synchronous-batch-supported-send-adapter"></a><span data-ttu-id="3b09f-102">Interfaces pour un adaptateur d'envoi synchrone pris en charge par lot</span><span class="sxs-lookup"><span data-stu-id="3b09f-102">Interfaces for a Synchronous Batch-Supported Send Adapter</span></span>
<span data-ttu-id="3b09f-103">Les adaptateurs qui reconnaissent les lots peuvent envoyer des messages de manière synchrone ou asynchrone et effectuer des opérations de traitement des envois.</span><span class="sxs-lookup"><span data-stu-id="3b09f-103">Batch-aware adapters may send messages synchronously or asynchronously, and may perform transacted send operations.</span></span> <span data-ttu-id="3b09f-104">Pour pouvoir envoyer des lots de messages, un adaptateur d'envoi doit implémenter les interfaces suivantes :</span><span class="sxs-lookup"><span data-stu-id="3b09f-104">To send batches of messages, a send adapter must implement the following interfaces:</span></span>  
  
-   <span data-ttu-id="3b09f-105">**IBTTransport**</span><span class="sxs-lookup"><span data-stu-id="3b09f-105">**IBTTransport**</span></span>  
  
-   <span data-ttu-id="3b09f-106">**IBaseComponent**</span><span class="sxs-lookup"><span data-stu-id="3b09f-106">**IBaseComponent**</span></span>  
  
-   <span data-ttu-id="3b09f-107">**IBTTransportControl**</span><span class="sxs-lookup"><span data-stu-id="3b09f-107">**IBTTransportControl**</span></span>  
  
-   <span data-ttu-id="3b09f-108">**IPersistPropertyBag**</span><span class="sxs-lookup"><span data-stu-id="3b09f-108">**IPersistPropertyBag**</span></span>  
  
-   <span data-ttu-id="3b09f-109">**IBTBatchTransmitter**</span><span class="sxs-lookup"><span data-stu-id="3b09f-109">**IBTBatchTransmitter**</span></span>  
  
-   <span data-ttu-id="3b09f-110">**IBTTransmitterBatch**</span><span class="sxs-lookup"><span data-stu-id="3b09f-110">**IBTTransmitterBatch**</span></span>  
  
 <span data-ttu-id="3b09f-111">Dans le cas de l'envoi synchrone de lot, le moteur de messagerie reçoit un lot de la part de l'adaptateur et ajoute les messages à transmettre à ce lot.</span><span class="sxs-lookup"><span data-stu-id="3b09f-111">For the synchronous batch send, the Messaging Engine gets a batch from the adapter and adds messages to be transmitted to that batch.</span></span> <span data-ttu-id="3b09f-112">Le moteur de messagerie ajoute chaque message au lot et envoie les messages uniquement lorsqu’il appelle le **fait** méthode sur le lot.</span><span class="sxs-lookup"><span data-stu-id="3b09f-112">The Messaging Engine adds each message to the batch and sends the messages only when it calls the **Done** method on the batch.</span></span> <span data-ttu-id="3b09f-113">L’adaptateur retourne `True` pour **bDeleteMessage** pour chaque message transmis de manière synchrone.</span><span class="sxs-lookup"><span data-stu-id="3b09f-113">The adapter returns `True` for **bDeleteMessage** for each message that it intends to transmit synchronously.</span></span> <span data-ttu-id="3b09f-114">L’adaptateur doit enregistrer les données du message, par opposition à un pointeur de message, dans son **TransmitMessage** mise en œuvre.</span><span class="sxs-lookup"><span data-stu-id="3b09f-114">The adapter should save message data, as opposed to a message pointer, in its **TransmitMessage** implementation.</span></span> <span data-ttu-id="3b09f-115">Cela est dû au fait que le pointeur du message n'est plus valide une fois la valeur `True` retournée et ne doit pas être réutilisé ni mis en cache pour une utilisation ultérieure.</span><span class="sxs-lookup"><span data-stu-id="3b09f-115">This is because the message pointer is no longer valid after `True` is returned, and should not be used or cached for later use.</span></span>  
  
 <span data-ttu-id="3b09f-116">Le schéma ci-dessous indique les interactions d'objets impliquées dans la création d'un adaptateur d'envoi synchrone prenant en charge les lots.</span><span class="sxs-lookup"><span data-stu-id="3b09f-116">The following figure shows the object interactions involved in creating a synchronous batch-supported send adapter.</span></span>  
  
 ![](../core/media/ebiz-sdk-devadapter6.gif "ebiz_sdk_devadapter6")  
<span data-ttu-id="3b09f-117">Workflow pour l'envoi d'un message de manière synchrone</span><span class="sxs-lookup"><span data-stu-id="3b09f-117">Workflow for submitting a message synchronously</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b09f-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3b09f-118">See Also</span></span>  
 <span data-ttu-id="3b09f-119">[Variables d’adaptateur](../core/adapter-variables.md) </span><span class="sxs-lookup"><span data-stu-id="3b09f-119">[Adapter Variables](../core/adapter-variables.md) </span></span>  
 <span data-ttu-id="3b09f-120">[Développement d’un adaptateur d’envoi](../core/developing-a-send-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="3b09f-120">[Developing a Send Adapter](../core/developing-a-send-adapter.md) </span></span>  
 <span data-ttu-id="3b09f-121">[Instanciation et initialisation d’un adaptateur d’envoi](../core/instantiating-and-initializing-a-send-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="3b09f-121">[Instantiating and Initializing a Send Adapter](../core/instantiating-and-initializing-a-send-adapter.md) </span></span>  
 <span data-ttu-id="3b09f-122">[Interfaces pour un envoi synchrone adaptateur](../core/interfaces-for-a-synchronous-send-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="3b09f-122">[Interfaces for a Synchronous Send Adapter](../core/interfaces-for-a-synchronous-send-adapter.md) </span></span>  
 <span data-ttu-id="3b09f-123">[Interfaces pour un envoi asynchrone adaptateur](../core/interfaces-for-an-asynchronous-send-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="3b09f-123">[Interfaces for an Asynchronous Send Adapter](../core/interfaces-for-an-asynchronous-send-adapter.md) </span></span>  
 <span data-ttu-id="3b09f-124">[Interfaces pour un adaptateur d’envoi asynchrone de lot est pris en charge](../core/interfaces-for-an-asynchronous-batch-supported-send-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="3b09f-124">[Interfaces for an Asynchronous Batch-Supported Send Adapter](../core/interfaces-for-an-asynchronous-batch-supported-send-adapter.md) </span></span>  
 <span data-ttu-id="3b09f-125">[Interfaces pour un adaptateur d’envoi de lot est pris en charge asynchrone transactionnelle](../core/interfaces-for-a-transactional-asynchronous-batch-supported-send-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="3b09f-125">[Interfaces for a Transactional Asynchronous Batch-Supported Send Adapter](../core/interfaces-for-a-transactional-asynchronous-batch-supported-send-adapter.md) </span></span>  
 [<span data-ttu-id="3b09f-126">Adaptateur d’envoi des interfaces pour une type sollicitation-réponse</span><span class="sxs-lookup"><span data-stu-id="3b09f-126">Interfaces for a Solicit-Response Send Adapter</span></span>](../core/interfaces-for-a-solicit-response-send-adapter.md)