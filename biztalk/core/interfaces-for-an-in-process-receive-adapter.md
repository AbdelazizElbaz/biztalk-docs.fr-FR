---
title: "Adaptateur de réception des interfaces pour In-Process | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4ed668d9-7512-4026-a8f3-df05aeed4df6
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7135471700cf640f61b56506ad159b5c47c7d877
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="interfaces-for-an-in-process-receive-adapter"></a><span data-ttu-id="d7096-102">Interfaces d'un adaptateur de réception In-process</span><span class="sxs-lookup"><span data-stu-id="d7096-102">Interfaces for an In-Process Receive Adapter</span></span>
<span data-ttu-id="d7096-103">Le moteur de messagerie instancie et configure les adaptateurs In-process, en transmettant le proxy de transport afin de permettre à l'adaptateur d'accéder à sa fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="d7096-103">The Messaging Engine instantiates and configures in-process adapters, passing in the transport proxy to allow the adapter to access its functionality.</span></span> <span data-ttu-id="d7096-104">Pour permettre la configuration et la liaison vers le proxy de transport, les adaptateurs doivent implémenter les interfaces de configuration suivantes :</span><span class="sxs-lookup"><span data-stu-id="d7096-104">To enable configuration and binding to the transport proxy, adapters must implement the following configuration interfaces:</span></span>  
  
-   <span data-ttu-id="d7096-105">**IBTTransport**</span><span class="sxs-lookup"><span data-stu-id="d7096-105">**IBTTransport**</span></span>  
  
-   <span data-ttu-id="d7096-106">**IBTTransportControl**</span><span class="sxs-lookup"><span data-stu-id="d7096-106">**IBTTransportControl**</span></span>  
  
-   <span data-ttu-id="d7096-107">**IBTTransportConfig**</span><span class="sxs-lookup"><span data-stu-id="d7096-107">**IBTTransportConfig**</span></span>  
  
-   <span data-ttu-id="d7096-108">**IBaseComponent**</span><span class="sxs-lookup"><span data-stu-id="d7096-108">**IBaseComponent**</span></span>  
  
 <span data-ttu-id="d7096-109">Si vous le souhaitez si l’adaptateur souhaite recevoir des informations de gestionnaire lors de l’initialisation qu’il doit implémenter **IPersistPropertyBag**.</span><span class="sxs-lookup"><span data-stu-id="d7096-109">Optionally if the adapter wants to receive handler information during initialization it needs to implement **IPersistPropertyBag**.</span></span>  
  
 <span data-ttu-id="d7096-110">Le moteur de messagerie crée une instance d'un adaptateur, l'initialise et définit la configuration des emplacements de réception.</span><span class="sxs-lookup"><span data-stu-id="d7096-110">The Messaging Engine creates an instance of an adapter, initializes it, and sets the configuration of receive locations.</span></span> <span data-ttu-id="d7096-111">Le moteur de messagerie transmet un sac de propriétés à une carte le **AddReceiveEndpoint** appel de méthode.</span><span class="sxs-lookup"><span data-stu-id="d7096-111">The Messaging Engine passes a property bag to an adapter on the **AddReceiveEndpoint** method call.</span></span> <span data-ttu-id="d7096-112">Ce jeu de propriétés contient la configuration de l'emplacement et du gestionnaire de réception.</span><span class="sxs-lookup"><span data-stu-id="d7096-112">The property bag contains the configuration for the receive location and receive handler.</span></span> <span data-ttu-id="d7096-113">La configuration est stockée dans la base de données sous la forme d'un jeu de propriétés XML.</span><span class="sxs-lookup"><span data-stu-id="d7096-113">The configuration is stored in the database in the form of an XML-styled property bag.</span></span> <span data-ttu-id="d7096-114">Le moteur de messagerie lit les données XML et à partir de ces données, réalimente un jeu de propriétés.</span><span class="sxs-lookup"><span data-stu-id="d7096-114">The Messaging Engine reads the XML and rehydrates a property bag from the XML.</span></span> <span data-ttu-id="d7096-115">Après l'ajout d'au moins un point de terminaison (emplacement de réception), l'adaptateur peut commencer à envoyer des messages.</span><span class="sxs-lookup"><span data-stu-id="d7096-115">After at least one endpoint (receive location) is added, the adapter can start submitting messages.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d7096-116">Adaptateurs ne doivent pas empêcher le moteur de messagerie appelle comme **IBTTransportControl.Initialize**, **IPersistPropertyBag.Load**, et **IBTTransportConfig.AddReceiveEndpoint**.</span><span class="sxs-lookup"><span data-stu-id="d7096-116">Adapters should not block Messaging Engine calls such as **IBTTransportControl.Initialize**, **IPersistPropertyBag.Load**, and **IBTTransportConfig.AddReceiveEndpoint**.</span></span> <span data-ttu-id="d7096-117">Traitement excessif dans ces appels affectera le temps de démarrage du service.</span><span class="sxs-lookup"><span data-stu-id="d7096-117">Performing excessive processing in these calls will affect service startup time.</span></span>  
  
 <span data-ttu-id="d7096-118">L'illustration suivante montre les interactions d'objets impliquées dans la création d'un adaptateur de réception in-process.</span><span class="sxs-lookup"><span data-stu-id="d7096-118">The following figure shows the object interactions involved in creating an in-process receive adapter.</span></span>  
  
 ![](../core/media/ebiz-sdk-devadapter11.gif "ebiz_sdk_devadapter11")  
<span data-ttu-id="d7096-119">Workflow d'un adaptateur de réception In-process</span><span class="sxs-lookup"><span data-stu-id="d7096-119">Workflow for an in-process receive adapter</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7096-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d7096-120">See Also</span></span>  
 <span data-ttu-id="d7096-121">[Variables d’adaptateur](../core/adapter-variables.md) </span><span class="sxs-lookup"><span data-stu-id="d7096-121">[Adapter Variables](../core/adapter-variables.md) </span></span>  
 <span data-ttu-id="d7096-122">[Développement d’un adaptateur de réception](../core/developing-a-receive-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="d7096-122">[Developing a Receive Adapter](../core/developing-a-receive-adapter.md) </span></span>  
 <span data-ttu-id="d7096-123">[Instanciation et initialisation un adaptateur de réception](../core/instantiating-and-initializing-a-receive-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="d7096-123">[Instantiating and Initializing a Receive Adapter](../core/instantiating-and-initializing-a-receive-adapter.md) </span></span>  
 <span data-ttu-id="d7096-124">[Adaptateur de réception des interfaces pour un hôte isolé](../core/interfaces-for-an-isolated-receive-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="d7096-124">[Interfaces for an Isolated Receive Adapter](../core/interfaces-for-an-isolated-receive-adapter.md) </span></span>  
 <span data-ttu-id="d7096-125">[Interfaces pour un lot pris en charge par l’adaptateur de réception](../core/interfaces-for-a-batch-supported-receive-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="d7096-125">[Interfaces for a Batch-Supported Receive Adapter](../core/interfaces-for-a-batch-supported-receive-adapter.md) </span></span>  
 <span data-ttu-id="d7096-126">[Adaptateur de réception des interfaces pour un transactionnel pris en charge par lot](../core/interfaces-for-a-transactional-batch-supported-receive-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="d7096-126">[Interfaces for a Transactional Batch-Supported Receive Adapter](../core/interfaces-for-a-transactional-batch-supported-receive-adapter.md) </span></span>  
 [<span data-ttu-id="d7096-127">Adaptateur de réception des interfaces pour une demande-réponse synchrone</span><span class="sxs-lookup"><span data-stu-id="d7096-127">Interfaces for a Synchronous Request-Response Receive Adapter</span></span>](../core/interfaces-for-a-synchronous-request-response-receive-adapter.md)