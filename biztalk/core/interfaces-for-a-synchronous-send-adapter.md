---
title: Interfaces pour un envoi synchrone adaptateur | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0e1b397a-3a35-4447-8522-d8a5f39a42d7
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1012b52bf5c6ab564cc219926b97445e43f60dd1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="interfaces-for-a-synchronous-send-adapter"></a><span data-ttu-id="20b49-102">Interfaces pour un adaptateur d'envoi synchrone</span><span class="sxs-lookup"><span data-stu-id="20b49-102">Interfaces for a Synchronous Send Adapter</span></span>
<span data-ttu-id="20b49-103">Un adaptateur envoie les messages de manière synchrone lorsqu'il bloque le thread appelant du moteur de messagerie tout en effectuant son opération d'envoi.</span><span class="sxs-lookup"><span data-stu-id="20b49-103">An adapter sends messages synchronously when it blocks the incoming Messaging Engine calling thread while performing its send operation.</span></span> <span data-ttu-id="20b49-104">Pour pouvoir envoyer les messages de manière synchrone, l'adaptateur doit implémenter les interfaces suivantes :</span><span class="sxs-lookup"><span data-stu-id="20b49-104">To be able to send messages synchronously, an adapter needs to implement the following interfaces:</span></span>  
  
-   <span data-ttu-id="20b49-105">**IBTTransport**</span><span class="sxs-lookup"><span data-stu-id="20b49-105">**IBTTransport**</span></span>  
  
-   <span data-ttu-id="20b49-106">**IBaseComponent**</span><span class="sxs-lookup"><span data-stu-id="20b49-106">**IBaseComponent**</span></span>  
  
-   <span data-ttu-id="20b49-107">**IBTTransportControl**</span><span class="sxs-lookup"><span data-stu-id="20b49-107">**IBTTransportControl**</span></span>  
  
-   <span data-ttu-id="20b49-108">**IPersistPropertyBag**</span><span class="sxs-lookup"><span data-stu-id="20b49-108">**IPersistPropertyBag**</span></span>  
  
-   <span data-ttu-id="20b49-109">**IBTTransmitter**</span><span class="sxs-lookup"><span data-stu-id="20b49-109">**IBTTransmitter**</span></span>  
  
 <span data-ttu-id="20b49-110">Dans un envoi synchrone, l’adaptateur envoie le message tout en bloquant **TransmitMessage**, et après le retour de la transmission réussie`True.`</span><span class="sxs-lookup"><span data-stu-id="20b49-110">In a synchronous send, the adapter sends the message while blocking **TransmitMessage**, and after successful transmission returns `True.`</span></span>  
  
 <span data-ttu-id="20b49-111">Le schéma ci-dessous indique les interactions d'objets impliquées dans la création d'un adaptateur d'envoi synchrone.</span><span class="sxs-lookup"><span data-stu-id="20b49-111">The following figure shows the object interactions involved in creating a synchronous send adapter.</span></span>  
  
 ![](../core/media/ebiz-sdk-devadapter4.gif "ebiz_sdk_devadapter4")  
<span data-ttu-id="20b49-112">Flux de travail pour envoyer un message de façon synchrone</span><span class="sxs-lookup"><span data-stu-id="20b49-112">Workflow for sending a message synchronously</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20b49-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="20b49-113">See Also</span></span>  
 <span data-ttu-id="20b49-114">[Variables d’adaptateur](../core/adapter-variables.md) </span><span class="sxs-lookup"><span data-stu-id="20b49-114">[Adapter Variables](../core/adapter-variables.md) </span></span>  
 <span data-ttu-id="20b49-115">[Développement d’un adaptateur d’envoi](../core/developing-a-send-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="20b49-115">[Developing a Send Adapter](../core/developing-a-send-adapter.md) </span></span>  
 <span data-ttu-id="20b49-116">[Instanciation et initialisation d’un adaptateur d’envoi](../core/instantiating-and-initializing-a-send-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="20b49-116">[Instantiating and Initializing a Send Adapter](../core/instantiating-and-initializing-a-send-adapter.md) </span></span>  
 <span data-ttu-id="20b49-117">[Interfaces pour un envoi asynchrone adaptateur](../core/interfaces-for-an-asynchronous-send-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="20b49-117">[Interfaces for an Asynchronous Send Adapter](../core/interfaces-for-an-asynchronous-send-adapter.md) </span></span>  
 <span data-ttu-id="20b49-118">[Interfaces pour un adaptateur d’envoi synchrone de lot est pris en charge](../core/interfaces-for-a-synchronous-batch-supported-send-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="20b49-118">[Interfaces for a Synchronous Batch-Supported Send Adapter](../core/interfaces-for-a-synchronous-batch-supported-send-adapter.md) </span></span>  
 <span data-ttu-id="20b49-119">[Interfaces pour un adaptateur d’envoi asynchrone de lot est pris en charge](../core/interfaces-for-an-asynchronous-batch-supported-send-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="20b49-119">[Interfaces for an Asynchronous Batch-Supported Send Adapter](../core/interfaces-for-an-asynchronous-batch-supported-send-adapter.md) </span></span>  
 <span data-ttu-id="20b49-120">[Interfaces pour un adaptateur d’envoi de lot est pris en charge asynchrone transactionnelle](../core/interfaces-for-a-transactional-asynchronous-batch-supported-send-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="20b49-120">[Interfaces for a Transactional Asynchronous Batch-Supported Send Adapter](../core/interfaces-for-a-transactional-asynchronous-batch-supported-send-adapter.md) </span></span>  
 [<span data-ttu-id="20b49-121">Adaptateur d’envoi des interfaces pour une type sollicitation-réponse</span><span class="sxs-lookup"><span data-stu-id="20b49-121">Interfaces for a Solicit-Response Send Adapter</span></span>](../core/interfaces-for-a-solicit-response-send-adapter.md)