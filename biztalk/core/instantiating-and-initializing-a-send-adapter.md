---
title: "Instanciation et initialisation d’un adaptateur d’envoi | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f10e6507-3351-4173-95f5-48546ca5f5c4
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 07ed590b73d31a03a4b3316a4d84edfc1e39eb0f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="instantiating-and-initializing-a-send-adapter"></a><span data-ttu-id="3a3a3-102">Instanciation et initialisation d'un adaptateur d'envoi</span><span class="sxs-lookup"><span data-stu-id="3a3a3-102">Instantiating and Initializing a Send Adapter</span></span>
<span data-ttu-id="3a3a3-103">Par défaut, les adaptateurs d'envoi ne sont pas instanciés tant qu'un premier message ne leur a pas été remis. Ce processus est appelé « création différée ».</span><span class="sxs-lookup"><span data-stu-id="3a3a3-103">By default, send adapters are not instantiated until the first message is delivered to them, a process known as "lazy creation."</span></span> <span data-ttu-id="3a3a3-104">L'approche de création différée par défaut permet de préserver les ressources système.</span><span class="sxs-lookup"><span data-stu-id="3a3a3-104">The default lazy creation approach helps to conserve system resources.</span></span> <span data-ttu-id="3a3a3-105">Une fois l'adaptateur d'envoi créé, il est mis en cache et est actif jusqu'à ce que le service BizTalk Server soit arrêté.</span><span class="sxs-lookup"><span data-stu-id="3a3a3-105">After the send adapter is created, it is cached and lives until the BizTalk Server service is stopped.</span></span>  
  
 <span data-ttu-id="3a3a3-106">Le **InitTransmitterOnServiceStart** membre de la **fonctionnalités** énumération dirige le moteur de messagerie pour créer l’adaptateur d’envoi sur le démarrage du service, au lieu d’utiliser la création différée par défaut, Si cela est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="3a3a3-106">The **InitTransmitterOnServiceStart** member of the **Capabilities** enumeration directs the Messaging Engine to create the send adapter on service startup, rather than using the default lazy creation, if this is desired.</span></span>  
  
 <span data-ttu-id="3a3a3-107">L'envoi d'un message diffère de la réception en ce qui concerne le traitement par lots des messages.</span><span class="sxs-lookup"><span data-stu-id="3a3a3-107">Sending a message is a different model than receiving a message with respect to batching of messages.</span></span> <span data-ttu-id="3a3a3-108">Lors de la réception, l'adaptateur dispose de messages entrants à insérer dans un lot transmis par le moteur de messagerie.</span><span class="sxs-lookup"><span data-stu-id="3a3a3-108">In the receive case the adapter has incoming messages to insert into a batch obtained from the Messaging Engine.</span></span> <span data-ttu-id="3a3a3-109">Dans le cas de l'envoi, le moteur de messagerie reçoit un lot de la part de l'adaptateur et envoie les messages à l'adaptateur pour transmission.</span><span class="sxs-lookup"><span data-stu-id="3a3a3-109">In the send case the Messaging Engine obtains a batch from the adapter and sends messages to the adapter to be transmitted.</span></span> <span data-ttu-id="3a3a3-110">Les deux processus utilisent le proxy de transport pour obtenir les objets du lot de messages.</span><span class="sxs-lookup"><span data-stu-id="3a3a3-110">Both use the transport proxy to obtain the message batch objects.</span></span>  
  
## <a name="how-a-send-adapter-is-initialized"></a><span data-ttu-id="3a3a3-111">Initialisation d'un adaptateur d'envoi</span><span class="sxs-lookup"><span data-stu-id="3a3a3-111">How a Send Adapter Is Initialized</span></span>  
 <span data-ttu-id="3a3a3-112">Pour permettre la configuration et la liaison vers le proxy de transport, les adaptateurs doivent implémenter les interfaces de configuration suivantes :</span><span class="sxs-lookup"><span data-stu-id="3a3a3-112">To enable configuration and binding to the transport proxy, adapters must implement the following configuration interfaces:</span></span>  
  
-   <span data-ttu-id="3a3a3-113">**IBTTransport**</span><span class="sxs-lookup"><span data-stu-id="3a3a3-113">**IBTTransport**</span></span>  
  
-   <span data-ttu-id="3a3a3-114">**IBaseComponent**</span><span class="sxs-lookup"><span data-stu-id="3a3a3-114">**IBaseComponent**</span></span>  
  
-   <span data-ttu-id="3a3a3-115">**IBTTransportControl**</span><span class="sxs-lookup"><span data-stu-id="3a3a3-115">**IBTTransportControl**</span></span>  
  
-   <span data-ttu-id="3a3a3-116">**IPersistPropertyBag**</span><span class="sxs-lookup"><span data-stu-id="3a3a3-116">**IPersistPropertyBag**</span></span>  
  
 <span data-ttu-id="3a3a3-117">Les étapes suivantes décrivent la séquence d'événements impliqués dans l'initialisation d'un adaptateur d'envoi :</span><span class="sxs-lookup"><span data-stu-id="3a3a3-117">The following steps describe the sequence of events involved in initializing a send adapter:</span></span>  
  
1.  <span data-ttu-id="3a3a3-118">Lorsque le moteur de messagerie Initialise un adaptateur d’envoi, elle effectue d’abord un **QueryInterface** pour **IPersistPropertyBag**, qui est une interface facultative.</span><span class="sxs-lookup"><span data-stu-id="3a3a3-118">When the Messaging Engine initializes a send adapter, it first performs a **QueryInterface** for **IPersistPropertyBag**, which is an optional interface.</span></span> <span data-ttu-id="3a3a3-119">Si l’adaptateur implémente l’interface, la configuration du gestionnaire est transmise à l’adaptateur dans le **charge** appel de méthode.</span><span class="sxs-lookup"><span data-stu-id="3a3a3-119">If the adapter implements the interface, the handler configuration is passed to the adapter in the **Load** method call.</span></span> <span data-ttu-id="3a3a3-120">L'adaptateur utilise ces informations pour vérifier sa bonne configuration.</span><span class="sxs-lookup"><span data-stu-id="3a3a3-120">The adapter uses this information to ensure it is configured correctly.</span></span>  
  
2.  <span data-ttu-id="3a3a3-121">Le moteur de messagerie effectue une **QueryInterface** pour **IBTTransportControl**, qui est une interface obligatoire.</span><span class="sxs-lookup"><span data-stu-id="3a3a3-121">The Messaging Engine performs a **QueryInterface** for **IBTTransportControl**, which is a mandatory interface.</span></span>  
  
3.  <span data-ttu-id="3a3a3-122">Le moteur appelle **IBTTransportControl.Initialize**, en passant le proxy de transport pour la carte.</span><span class="sxs-lookup"><span data-stu-id="3a3a3-122">The engine calls **IBTTransportControl.Initialize**, passing in the transport proxy for the adapter.</span></span>  
  
4.  <span data-ttu-id="3a3a3-123">Le moteur de messagerie effectue une **QueryInterface** pour **IBTTransmitter**.</span><span class="sxs-lookup"><span data-stu-id="3a3a3-123">The Messaging Engine performs a **QueryInterface** for **IBTTransmitter**.</span></span>  
  
     <span data-ttu-id="3a3a3-124">Si le moteur de messagerie découvre cette interface, l'adaptateur est traité comme un émetteur ne dépendant pas des lots.</span><span class="sxs-lookup"><span data-stu-id="3a3a3-124">If the Messaging Engine discovers this interface, the adapter is treated as a batch-unaware transmitter.</span></span>  
  
     <span data-ttu-id="3a3a3-125">Si le moteur de messagerie ne découvre pas cette interface, le moteur de messagerie effectue une **QueryInterface** pour **IBTBatchTransmitter**, dont la découverte indique que l’adaptateur est un lot prenant en charge émetteur.</span><span class="sxs-lookup"><span data-stu-id="3a3a3-125">If the Messaging Engine does not discover this interface, the Messaging Engine performs a **QueryInterface** for **IBTBatchTransmitter**, discovery of which indicates that the adapter is a batch-aware transmitter.</span></span>  
  
     <span data-ttu-id="3a3a3-126">Si le moteur de messagerie ne découvre aucune de ces interfaces, une erreur survient, qui entraîne l'échec de l'initialisation.</span><span class="sxs-lookup"><span data-stu-id="3a3a3-126">If the Messaging Engine discovers neither of these interfaces, an error condition results, causing the initialization to fail.</span></span> <span data-ttu-id="3a3a3-127">L'initialisation échoue si les interfaces obligatoires ne sont pas découvertes.</span><span class="sxs-lookup"><span data-stu-id="3a3a3-127">The initialization fails if any mandatory interfaces are not discovered.</span></span>  
  
 <span data-ttu-id="3a3a3-128">Le schéma ci-dessous illustre cette séquence d'appels d'API. Les interfaces en bleu sont implémentées par l'adaptateur.</span><span class="sxs-lookup"><span data-stu-id="3a3a3-128">The following diagram illustrates this sequence of API calls; the interfaces in blue are implemented by the adapter.</span></span>  
  
 ![](../core/media/transmit-adapter-init.gif "Transmit_adapter_init")  
  
 <span data-ttu-id="3a3a3-129">L'adaptateur peut envoyer des messages dès qu'il est initialisé et configuré.</span><span class="sxs-lookup"><span data-stu-id="3a3a3-129">The adapter can send messages as soon as it is initialized and configured.</span></span>  
  
 <span data-ttu-id="3a3a3-130">Le schéma ci-dessous indique les interactions d'objets impliquées dans l'initialisation d'un adaptateur d'envoi.</span><span class="sxs-lookup"><span data-stu-id="3a3a3-130">The following figure shows the object interactions involved in initializing a send adapter.</span></span>  
  
 ![](../core/media/ebiz-sdk-devadapter10.gif "ebiz_sdk_devadapter10")  
<span data-ttu-id="3a3a3-131">Workflow d'initialisation d'un adaptateur d'envoi</span><span class="sxs-lookup"><span data-stu-id="3a3a3-131">Workflow for initializing a send adapter</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3a3a3-132">Adaptateurs ne doivent pas empêcher le moteur de messagerie telles que **IBTTransportControl.Initialize** et **IPersistPropertyBag.Load**.</span><span class="sxs-lookup"><span data-stu-id="3a3a3-132">Adapters should not block the Messaging Engine in calls such as **IBTTransportControl.Initialize** and **IPersistPropertyBag.Load**.</span></span> <span data-ttu-id="3a3a3-133">Un traitement excessif dans ces appels peut avoir un impact négatif sur le délai de démarrage du service.</span><span class="sxs-lookup"><span data-stu-id="3a3a3-133">Performing excessive processing in these calls affects service startup time.</span></span>