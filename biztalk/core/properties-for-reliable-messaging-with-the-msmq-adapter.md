---
title: "Propriétés de la messagerie fiable avec l’adaptateur MSMQ | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MSMQ adapters, properties
- queues, MSMQ adapters
- MSMQ adapters, dead letters
- queues, failures [MSMQ adapters]
- MSMQ adapters, impersonation
- MSMQ adapters, remote queues
- queues
- reliability, MSMQ adapters
- impersonation, MSMQ adapters
- MSMQ adapters, queue failures
- clustering, MSMQ adapters
- queues, remote
- MSMQ adapters, reliability
- MSMQ adapters, clustering
ms.assetid: 34bfe028-b2aa-4816-a437-3679d19dffb2
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 49aebf12c86ae72d5dcb224d078c62afefcb8f46
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="properties-for-reliable-messaging-with-the-msmq-adapter"></a><span data-ttu-id="51b2a-102">Propriétés de la messagerie fiable avec l’adaptateur MSMQ</span><span class="sxs-lookup"><span data-stu-id="51b2a-102">Properties for Reliable Messaging with the MSMQ Adapter</span></span>
<span data-ttu-id="51b2a-103">La fiabilité de l'envoi et de la réception de messages via l'adaptateur MSMQ peut être améliorée selon la manière dont vous configurez ce dernier.</span><span class="sxs-lookup"><span data-stu-id="51b2a-103">You can improve the reliability of sending and receiving messages with the MSMQ adapter by the way you configure the MSMQ adapter.</span></span> <span data-ttu-id="51b2a-104">Cette rubrique traite de l'utilisation de plusieurs propriétés de configuration pour garantir la fiabilité de la messagerie.</span><span class="sxs-lookup"><span data-stu-id="51b2a-104">This topic discusses using several configuration properties for reliable messaging.</span></span>  
  
## <a name="running-msmq-adapter-handlers-within-a-clustered-biztalk-host"></a><span data-ttu-id="51b2a-105">Exécution des gestionnaires d'adaptateur MSMQ au sein d'un hôte BizTalk en cluster</span><span class="sxs-lookup"><span data-stu-id="51b2a-105">Running MSMQ Adapter Handlers Within a Clustered BizTalk Host</span></span>  
 <span data-ttu-id="51b2a-106">Une approche de haute disponibilité consiste à exécuter simultanément des gestionnaires de l'adaptateur dans plusieurs instances de l'hôte et sur plusieurs serveurs BizTalk.</span><span class="sxs-lookup"><span data-stu-id="51b2a-106">One approach to high availability is to run adapter handlers in multiple host instances on different BizTalk servers simultaneously.</span></span> <span data-ttu-id="51b2a-107">Toutefois, il n'est pas recommandé d'employer cette méthode avec les gestionnaires de l'adaptateur MSMQ, car MSMQ ne prend pas en charge les opérations de lectures traitées distantes et car le gestionnaire d'envoi MSMQ conserve une dépendance vis à vis de l'instance du service MSMQ exécutée localement.</span><span class="sxs-lookup"><span data-stu-id="51b2a-107">This approach is not recommended for the MSMQ adapter handlers, because MSMQ does not support remote transacted reads and because the MSMQ send handler maintains a dependency on the locally running instance of the MSMQ service.</span></span> <span data-ttu-id="51b2a-108">Pour obtenir des gestionnaires d'envoi et de réception MSMQ haute disponibilité, il est recommandé d'exécuter les gestionnaires de l'adaptateur MSMQ dans une instance d'hôte BizTalk mise en cluster.</span><span class="sxs-lookup"><span data-stu-id="51b2a-108">To provide high availability for the MSMQ send and receive handlers it is recommended that you run the MSMQ adapter handlers in a clustered instance of a BizTalk Host.</span></span> <span data-ttu-id="51b2a-109">Pour plus d’informations, consultez [considérations pour les gestionnaires d’adaptateur en cours d’exécution au sein d’un ordinateur hôte en cluster](../core/considerations-for-running-adapter-handlers-within-a-clustered-host1.md).</span><span class="sxs-lookup"><span data-stu-id="51b2a-109">For more information, see [Considerations for Running Adapter Handlers within a Clustered Host](../core/considerations-for-running-adapter-handlers-within-a-clustered-host1.md).</span></span>  
  
## <a name="queue-failure-and-the-dead-letter-queue"></a><span data-ttu-id="51b2a-110">Échec de la file d'attente et file d'attente de messages non distribués</span><span class="sxs-lookup"><span data-stu-id="51b2a-110">Queue Failure and the Dead Letter Queue</span></span>  
 <span data-ttu-id="51b2a-111">Après l'envoi d'un message, aucune erreur n'est générée pour indiquer aux messages suivants que la file d'attente de réception est désactivée ou a été supprimée.</span><span class="sxs-lookup"><span data-stu-id="51b2a-111">After successfully sending a message, there is no error for subsequent messages if the receiving queue is disabled or deleted.</span></span> <span data-ttu-id="51b2a-112">Une telle situation peut entraîner la perte de messages.</span><span class="sxs-lookup"><span data-stu-id="51b2a-112">This situation could cause loss of messages.</span></span>  
  
 <span data-ttu-id="51b2a-113">Définition de la **file d’attente de lettres mortes utilisation** propriété configuration **True** vous empêche de perdre des messages.</span><span class="sxs-lookup"><span data-stu-id="51b2a-113">Setting the **Use Dead Letter Queue** configuration property to **True** prevents you from losing messages.</span></span> <span data-ttu-id="51b2a-114">Lorsque la propriété a la valeur `True`, les messages que la file d'attente ne reçoit pas sont placés dans la file d'attente des messages non distribués.</span><span class="sxs-lookup"><span data-stu-id="51b2a-114">When the property is `True` (the default), messages that the queue does not receive go into the dead letter queue.</span></span>  
  
## <a name="impersonation-and-remote-queues"></a><span data-ttu-id="51b2a-115">Emprunt d'identité et files d'attente distantes</span><span class="sxs-lookup"><span data-stu-id="51b2a-115">Impersonation and Remote Queues</span></span>  
 <span data-ttu-id="51b2a-116">Vous devez également définir le **file d’attente de lettres mortes utiliser** propriété configuration **True** lorsque vous utilisez des files d’attente distantes.</span><span class="sxs-lookup"><span data-stu-id="51b2a-116">You also have to set the **Use Dead Letter Queue** configuration property to **True** when you use remote queues.</span></span> <span data-ttu-id="51b2a-117">Si l'adaptateur pour MSMQ emprunte l'identité d'un utilisateur sans disposer de l'autorisation pour utiliser la file d'attente, le message risque d'être perdu.</span><span class="sxs-lookup"><span data-stu-id="51b2a-117">If the adapter for MSMQ impersonates a user without permission to use the remote queue, the message could be lost.</span></span>  
  
 <span data-ttu-id="51b2a-118">Lorsque la propriété est **True** et l’utilisateur représenté ne dispose pas d’autorisation d’utiliser la file d’attente distante, il est placé dans la file d’attente de lettres mortes sur l’ordinateur local ou distant.</span><span class="sxs-lookup"><span data-stu-id="51b2a-118">When the property is **True** and the impersonated user does not have permission to use the remote queue, the message goes to the dead letter queue on either the local or remote computer.</span></span> <span data-ttu-id="51b2a-119">Dans le cas d'un envoi transactionnel, le message est placé dans la file d'attente des messages non distribués de l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="51b2a-119">In a transactional send, the message goes to the dead letter queue on the local computer.</span></span> <span data-ttu-id="51b2a-120">Dans le cas d'un envoi non transactionnel, il est placé dans celle de l'ordinateur distant.</span><span class="sxs-lookup"><span data-stu-id="51b2a-120">In a non-transactional send, the message goes to the dead letter queue on the remote computer.</span></span>  
  
## <a name="recoverable-and-use-journal-queue-properties"></a><span data-ttu-id="51b2a-121">Propriétés Récupérable et Utiliser file d'attente journal</span><span class="sxs-lookup"><span data-stu-id="51b2a-121">Recoverable and Use Journal Queue Properties</span></span>  
 <span data-ttu-id="51b2a-122">Les deux le **récupérable** et **file d’attente du Journal utilisation** propriétés enregistrent des copies des messages envoyés.</span><span class="sxs-lookup"><span data-stu-id="51b2a-122">Both the **Recoverable** and **Use Journal Queue** properties save copies of sent messages.</span></span> <span data-ttu-id="51b2a-123">Pour plus d’informations sur ces propriétés, consultez [comment configurer un emplacement de réception MSMQ](../core/how-to-configure-an-msmq-receive-location.md) et [comment configurer un Port d’envoi MSMQ](../core/how-to-configure-an-msmq-send-port.md).</span><span class="sxs-lookup"><span data-stu-id="51b2a-123">For more information about these properties, see [How to Configure an MSMQ Receive Location](../core/how-to-configure-an-msmq-receive-location.md) and [How to Configure an MSMQ Send Port](../core/how-to-configure-an-msmq-send-port.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51b2a-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="51b2a-124">See Also</span></span>  
 <span data-ttu-id="51b2a-125">[Messagerie fiable avec l’adaptateur MSMQ](../core/reliable-messaging-with-the-msmq-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="51b2a-125">[Reliable Messaging with the MSMQ Adapter](../core/reliable-messaging-with-the-msmq-adapter.md) </span></span>  
 [<span data-ttu-id="51b2a-126">Considérations pour l’exécution des gestionnaires d’adaptateur au sein d’un hôte en cluster</span><span class="sxs-lookup"><span data-stu-id="51b2a-126">Considerations for Running Adapter Handlers within a Clustered Host</span></span>](../core/considerations-for-running-adapter-handlers-within-a-clustered-host1.md)