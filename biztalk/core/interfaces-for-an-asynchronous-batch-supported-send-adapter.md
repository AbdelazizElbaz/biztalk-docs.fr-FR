---
title: "Adaptateur d’envoi de lot est pris en charge des interfaces pour asynchrone | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d38b8b87-508a-499b-86b2-846938050b44
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4af0a5c116c19c4cb1fa728cc016144594f42f13
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="interfaces-for-an-asynchronous-batch-supported-send-adapter"></a><span data-ttu-id="6bf45-102">Interfaces pour un adaptateur d'envoi asynchrone pris en charge par lot</span><span class="sxs-lookup"><span data-stu-id="6bf45-102">Interfaces for an Asynchronous Batch-Supported Send Adapter</span></span>
<span data-ttu-id="6bf45-103">Les adaptateurs qui reconnaissent les lots peuvent envoyer des messages de manière synchrone ou asynchrone, ainsi qu'effectuer des opérations de traitement des envois.</span><span class="sxs-lookup"><span data-stu-id="6bf45-103">Batch-aware adapters may send messages synchronously or asynchronously, and may perform transacted sends.</span></span> <span data-ttu-id="6bf45-104">Pour pouvoir envoyer des lots de messages, un adaptateur d'envoi doit implémenter les interfaces suivantes :</span><span class="sxs-lookup"><span data-stu-id="6bf45-104">To send batches of messages, a send adapter must implement the following interfaces:</span></span>  
  
-   <span data-ttu-id="6bf45-105">**IBTTransport**</span><span class="sxs-lookup"><span data-stu-id="6bf45-105">**IBTTransport**</span></span>  
  
-   <span data-ttu-id="6bf45-106">**IBaseComponent**</span><span class="sxs-lookup"><span data-stu-id="6bf45-106">**IBaseComponent**</span></span>  
  
-   <span data-ttu-id="6bf45-107">**IBTTransportControl**</span><span class="sxs-lookup"><span data-stu-id="6bf45-107">**IBTTransportControl**</span></span>  
  
-   <span data-ttu-id="6bf45-108">**IPersistPropertyBag**</span><span class="sxs-lookup"><span data-stu-id="6bf45-108">**IPersistPropertyBag**</span></span>  
  
-   <span data-ttu-id="6bf45-109">**IBTBatchTransmitter**</span><span class="sxs-lookup"><span data-stu-id="6bf45-109">**IBTBatchTransmitter**</span></span>  
  
-   <span data-ttu-id="6bf45-110">**IBTTransmitterBatch**</span><span class="sxs-lookup"><span data-stu-id="6bf45-110">**IBTTransmitterBatch**</span></span>  
  
 <span data-ttu-id="6bf45-111">Dans le cas de l'envoi asynchrone de lot, le moteur de messagerie reçoit un lot de la part de l'adaptateur et ajoute les messages à transmettre à ce lot.</span><span class="sxs-lookup"><span data-stu-id="6bf45-111">For the asynchronous batch send, the Messaging Engine gets a batch from the adapter and adds messages to be transmitted to that batch.</span></span> <span data-ttu-id="6bf45-112">Les messages sont envoyés uniquement lorsque le moteur de messagerie appelle la **fait** méthode sur le lot.</span><span class="sxs-lookup"><span data-stu-id="6bf45-112">The messages are only sent when the Messaging Engine calls the **Done** method on the batch.</span></span> <span data-ttu-id="6bf45-113">L'adaptateur retourne `False` pour chaque message transmis de manière asynchrone.</span><span class="sxs-lookup"><span data-stu-id="6bf45-113">The adapter returns `False` for each message that it intends to transmit asynchronously.</span></span> <span data-ttu-id="6bf45-114">L'adaptateur reçoit ensuite un lot de la part du proxy de l'adaptateur et supprime les messages déjà transmis.</span><span class="sxs-lookup"><span data-stu-id="6bf45-114">The adapter then gets a batch from the adapter proxy and deletes those messages that it successfully transmitted.</span></span>  
  
 <span data-ttu-id="6bf45-115">Le schéma ci-dessous indique les interactions d'objets impliquées dans la création d'un adaptateur d'envoi asynchrone prenant en charge les lots.</span><span class="sxs-lookup"><span data-stu-id="6bf45-115">The following figure shows the object interactions involved in creating an asynchronous batch-supported send adapter.</span></span>  
  
 ![](../core/media/ebiz-sdk-devadapter7.gif "ebiz_sdk_devadapter7")  
<span data-ttu-id="6bf45-116">Workflow pour l'envoi d'un message de manière asynchrone</span><span class="sxs-lookup"><span data-stu-id="6bf45-116">Workflow for sending a message asynchronously</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6bf45-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6bf45-117">See Also</span></span>  
 <span data-ttu-id="6bf45-118">[Variables d’adaptateur](../core/adapter-variables.md) </span><span class="sxs-lookup"><span data-stu-id="6bf45-118">[Adapter Variables](../core/adapter-variables.md) </span></span>  
 <span data-ttu-id="6bf45-119">[Développement d’un adaptateur d’envoi](../core/developing-a-send-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="6bf45-119">[Developing a Send Adapter](../core/developing-a-send-adapter.md) </span></span>  
 <span data-ttu-id="6bf45-120">[Instanciation et initialisation d’un adaptateur d’envoi](../core/instantiating-and-initializing-a-send-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="6bf45-120">[Instantiating and Initializing a Send Adapter](../core/instantiating-and-initializing-a-send-adapter.md) </span></span>  
 <span data-ttu-id="6bf45-121">[Interfaces pour un envoi synchrone adaptateur](../core/interfaces-for-a-synchronous-send-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="6bf45-121">[Interfaces for a Synchronous Send Adapter](../core/interfaces-for-a-synchronous-send-adapter.md) </span></span>  
 <span data-ttu-id="6bf45-122">[Interfaces pour un envoi asynchrone adaptateur](../core/interfaces-for-an-asynchronous-send-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="6bf45-122">[Interfaces for an Asynchronous Send Adapter](../core/interfaces-for-an-asynchronous-send-adapter.md) </span></span>  
 <span data-ttu-id="6bf45-123">[Interfaces pour un adaptateur d’envoi synchrone de lot est pris en charge](../core/interfaces-for-a-synchronous-batch-supported-send-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="6bf45-123">[Interfaces for a Synchronous Batch-Supported Send Adapter](../core/interfaces-for-a-synchronous-batch-supported-send-adapter.md) </span></span>  
 <span data-ttu-id="6bf45-124">[Interfaces pour un adaptateur d’envoi de lot est pris en charge asynchrone transactionnelle](../core/interfaces-for-a-transactional-asynchronous-batch-supported-send-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="6bf45-124">[Interfaces for a Transactional Asynchronous Batch-Supported Send Adapter](../core/interfaces-for-a-transactional-asynchronous-batch-supported-send-adapter.md) </span></span>  
 [<span data-ttu-id="6bf45-125">Adaptateur d’envoi des interfaces pour une type sollicitation-réponse</span><span class="sxs-lookup"><span data-stu-id="6bf45-125">Interfaces for a Solicit-Response Send Adapter</span></span>](../core/interfaces-for-a-solicit-response-send-adapter.md)