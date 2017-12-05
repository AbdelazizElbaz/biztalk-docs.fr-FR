---
title: "La gestion avec l’adaptateur MSMQ de transaction | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MSMQ adapters, transaction handling
- transactions, MSMQ adapters
ms.assetid: 2e5dd0da-3852-48bf-9372-b019ecab23be
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1bea79413042ec99cfd1cbc5bc6dee500aef4ac4
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="transaction-handling-with-the-msmq-adapter"></a><span data-ttu-id="57a42-102">La gestion avec l’adaptateur MSMQ de transaction</span><span class="sxs-lookup"><span data-stu-id="57a42-102">Transaction Handling with the MSMQ Adapter</span></span>
<span data-ttu-id="57a42-103">Cette section traite de la manière dont les transactions fonctionnent en réception et en envoi.</span><span class="sxs-lookup"><span data-stu-id="57a42-103">This section discusses how transactions work in receiving and sending.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="57a42-104">Pour l'adaptateur MSMQ, une transaction s'étend de la base de données MessageBox BizTalk à la file d'attente Message Queuing locale, même si vous utilisez une file d'attente distante.</span><span class="sxs-lookup"><span data-stu-id="57a42-104">For the MSMQ adapter, a transaction extends from the BizTalk MessageBox database to the local Message Queuing queue even if you are using a remote queue.</span></span>  
  
 <span data-ttu-id="57a42-105">Vous pouvez utiliser des transactions sur l'envoi et la réception avec l'adaptateur MSMQ.</span><span class="sxs-lookup"><span data-stu-id="57a42-105">You can use transactions on both send and receive with the MSMQ adapter.</span></span> <span data-ttu-id="57a42-106">Sur les envois traités, l'adaptateur accumule les messages jusqu'à obtenir un lot complet.</span><span class="sxs-lookup"><span data-stu-id="57a42-106">On transacted sends, the adapter accumulates messages until it has a complete batch.</span></span> <span data-ttu-id="57a42-107">L'adaptateur soumet ensuite le lot au service Message Queuing local comme une transaction unique.</span><span class="sxs-lookup"><span data-stu-id="57a42-107">The adapter then submits the batch to the local Message Queuing service as a single transaction.</span></span> <span data-ttu-id="57a42-108">En cas d'échec de l'opération, l'adaptateur réessaie de soumettre le lot.</span><span class="sxs-lookup"><span data-stu-id="57a42-108">If the submission fails, the adapter tries to resubmit the batch.</span></span> <span data-ttu-id="57a42-109">Si la nouvelle tentative échoue, l'adaptateur passe au transport secondaire.</span><span class="sxs-lookup"><span data-stu-id="57a42-109">If the resubmission fails, the adapter moves to the secondary transport.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="57a42-110">L'adaptateur prend en charge les lectures transactionnelles des files d'attente distantes uniquement avec Message Queuing 4.0 ou une version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="57a42-110">The adapter supports transactional reads of remote queues with Message Queuing 4.0 or later only.</span></span> <span data-ttu-id="57a42-111">Dans ce scénario BizTalk Server et le serveur Message Queuing distant doivent exécuter Message Queuing 4.0 ou version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="57a42-111">In this scenario both the BizTalk Server and the remote Message Queuing server must be running Message Queuing 4.0 or later.</span></span>  
  
 <span data-ttu-id="57a42-112">Sur les réceptions traitées, l'adaptateur suspend les messages ayant échoué de façon à n'en perdre aucun.</span><span class="sxs-lookup"><span data-stu-id="57a42-112">On transacted receives, the adapter suspends failed messages so that it does not lose any one of the messages.</span></span> <span data-ttu-id="57a42-113">Au cours d'une réception traitée, l'adaptateur ajoute des messages à un lot jusqu'à ce que ce dernier soit complet.</span><span class="sxs-lookup"><span data-stu-id="57a42-113">During a transacted receive the adapter adds messages to a batch until the batch is complete.</span></span> <span data-ttu-id="57a42-114">Il soumet ensuite le lot :</span><span class="sxs-lookup"><span data-stu-id="57a42-114">It then submits the batch:</span></span>  
  
-   <span data-ttu-id="57a42-115">S'il n'y a pas de problème et que le serveur reçoit les messages, l'adaptateur valide la transaction.</span><span class="sxs-lookup"><span data-stu-id="57a42-115">If there are no problems and the server receives the messages, the adapter commits the transaction.</span></span>  
  
-   <span data-ttu-id="57a42-116">En cas de problème, l'adaptateur crée un lot faisant partie de la transaction actuelle.</span><span class="sxs-lookup"><span data-stu-id="57a42-116">If there are problems, the adapter creates a new batch as part of the current transaction.</span></span> <span data-ttu-id="57a42-117">Il déplace ensuite les messages problématiques vers ce nouveau lot.</span><span class="sxs-lookup"><span data-stu-id="57a42-117">It then moves any problem messages into the new batch.</span></span> <span data-ttu-id="57a42-118">Puis, il soumet à nouveau le premier lot et envoie le nouveau lot en tant que lot de messages suspendus.</span><span class="sxs-lookup"><span data-stu-id="57a42-118">It then resubmits the first batch and submits the new batch as suspended messages.</span></span> <span data-ttu-id="57a42-119">L'adaptateur valide la transaction si cette nouvelle soumission ne génère pas de problème.</span><span class="sxs-lookup"><span data-stu-id="57a42-119">The adapter commits the transaction if there are no problems during this resubmission.</span></span>  
  
 <span data-ttu-id="57a42-120">Si vous exécutez un gestionnaire d'envoi d'adaptateur MSMQ dans une instance de l'hôte BizTalk en cluster, vous devez mettre en cluster le service MSMQ dans le même groupe de clusters pour garantir la cohérence transactionnelle.</span><span class="sxs-lookup"><span data-stu-id="57a42-120">If you are running an MSMQ adapter send handler in a clustered BizTalk Host instance, you should cluster the MSMQ service in the same cluster group to ensure transactional consistency.</span></span>  
  
 <span data-ttu-id="57a42-121">Si l'« accès DTC réseau » est désactivé dans l'utilitaire DCOMCNFG, une opération de réception distante transactionnelle de MSMQ échoue en générant un message d'erreur chiffré.</span><span class="sxs-lookup"><span data-stu-id="57a42-121">If "Network DTC Access" is disabled in the DCOMCNFG utility, a MSMQ transactional remote receive operation will fail with a cryptic error message.</span></span>  <span data-ttu-id="57a42-122">Pour opérer une réception distante transactionnelle avec l'adaptateur MSMQ, l'« accès DTC réseau » doit être activé.</span><span class="sxs-lookup"><span data-stu-id="57a42-122">To do a transactional remote receive with the MSMQ adapter, "Network DTC Access" must be enabled.</span></span> <span data-ttu-id="57a42-123">Plus d’informations, consultez [http://go.microsoft.com/fwlink/?LinkId=124623](http://go.microsoft.com/fwlink/?LinkId=124623).</span><span class="sxs-lookup"><span data-stu-id="57a42-123">More information can be found at [http://go.microsoft.com/fwlink/?LinkId=124623](http://go.microsoft.com/fwlink/?LinkId=124623).</span></span>  
  
 <span data-ttu-id="57a42-124">Si vous exécutez un gestionnaire de réception d'adaptateur MSMQ dans une instance de l'hôte BizTalk en cluster, vous devez mettre en cluster le service MSMQ dans le même groupe de clusters de façon à prendre en charge les lectures traitées locales, car MSMQ ne prend pas en charge les lectures transactionnelles distantes.</span><span class="sxs-lookup"><span data-stu-id="57a42-124">If you are running an MSMQ adapter receive handler in a clustered BizTalk Host instance, you should cluster the MSMQ service in the same cluster group to support local transacted reads because MSMQ does not support remote transactional reads.</span></span> <span data-ttu-id="57a42-125">Pour plus d’informations sur l’exécution des gestionnaires d’adaptateur MSMQ dans une instance en cluster d’un hôte BizTalk, consultez [considérations pour les gestionnaires d’adaptateur en cours d’exécution dans un cluster hôte](../core/considerations-for-running-adapter-handlers-within-a-clustered-host1.md).</span><span class="sxs-lookup"><span data-stu-id="57a42-125">For more information about running MSMQ adapter handlers in a clustered instance of a BizTalk Host, see [Considerations for Running Adapter Handlers within a Clustered Host](../core/considerations-for-running-adapter-handlers-within-a-clustered-host1.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57a42-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="57a42-126">See Also</span></span>  
 [<span data-ttu-id="57a42-127">Messagerie sécurisée à l’aide de l’adaptateur MSMQ</span><span class="sxs-lookup"><span data-stu-id="57a42-127">Reliable Messaging with the MSMQ Adapter</span></span>](../core/reliable-messaging-with-the-msmq-adapter.md)