---
title: Orchestration de FRR | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- messages, promoted properties
- orchestrations, message subscriptions
- promoted properties, messages
- FRR, orchestrations
- subscriptions, messages
- orchestrations, reconciliation time-out
- messages, message/response correlation
- message/response correlation
- promoted properties, FIN Response Reconciliation
- orchestrations, FRR
- outbound messages
- FIN Response Reconciliation, promoted properties
- direct bindings
- reconciliation time-out
- bindings, direct
- messages, subscriptions
- subscriptions, orchestrations
- messages, outbound
- MessageBox database
ms.assetid: ea8d31c2-ac3b-44ac-8064-d008da4f7f72
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 43dd7d6245546f8d35760bfe2ed2224482d9d4bd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="frr-orchestration"></a><span data-ttu-id="de93b-102">Orchestration de FRR</span><span class="sxs-lookup"><span data-stu-id="de93b-102">FRR Orchestration</span></span>
[!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]<span data-ttu-id="de93b-103">implémente FRR via l’orchestration FRR.</span><span class="sxs-lookup"><span data-stu-id="de93b-103"> implements FRR through the FRR orchestration.</span></span> <span data-ttu-id="de93b-104">L’orchestration détermine si le jeton de corrélation de la réponse FIN correspond à l’ID de message du message d’origine.</span><span class="sxs-lookup"><span data-stu-id="de93b-104">The orchestration determines whether the Correlation Token of the FIN response matches the message ID of the original message.</span></span> <span data-ttu-id="de93b-105">Il traite le message en parallèle avec les fonctions d’envoi effectuées par le port d’envoi qui envoie le message à SAA et les fonctions de réception effectuées par l’emplacement de réception qui reçoit le message de SAA.</span><span class="sxs-lookup"><span data-stu-id="de93b-105">It processes the message in parallel with the send functions performed by the send port that sends the message to SAA, and with the receive functions performed by the receive location that receives the message from SAA.</span></span>  
  
 <span data-ttu-id="de93b-106">Le niveau le plus élevé, une instance de l’orchestration effectue le traitement suivant :</span><span class="sxs-lookup"><span data-stu-id="de93b-106">At the highest level, an instance of the orchestration does the following processing:</span></span>  
  
1.  <span data-ttu-id="de93b-107">Caches une copie du message sortant lié pour SAA en écoutant sur la MessageBox.</span><span class="sxs-lookup"><span data-stu-id="de93b-107">Caches a copy of the original outbound message bound for SAA by listening on the MessageBox.</span></span>  
  
    > [!NOTE]
    >  [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="de93b-108">Crée une instance de l’orchestration lorsque [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] achemine le message d’origine vers la MessageBox.</span><span class="sxs-lookup"><span data-stu-id="de93b-108"> creates an instance of the orchestration when [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] routes the original message to the MessageBox.</span></span>  
  
2.  <span data-ttu-id="de93b-109">Attend que [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] pour publier une réponse FIN SAA vers la MessageBox.</span><span class="sxs-lookup"><span data-stu-id="de93b-109">Waits for [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] to publish a FIN response from SAA to the MessageBox.</span></span>  
  
3.  <span data-ttu-id="de93b-110">Définit les propriétés de la copie du message d’origine en fonction de la nature de la réponse FIN promues.</span><span class="sxs-lookup"><span data-stu-id="de93b-110">Sets promoted properties of the copy of the original message depending upon the nature of the FIN response.</span></span>  
  
4.  <span data-ttu-id="de93b-111">Republie la copie du message d’origine dans la MessageBox.</span><span class="sxs-lookup"><span data-stu-id="de93b-111">Publishes the copy of the original message back to the MessageBox.</span></span> <span data-ttu-id="de93b-112">Gestionnaires personnalisés peuvent ensuite s’abonner pour récupérer et traiter le message en fonction des besoins.</span><span class="sxs-lookup"><span data-stu-id="de93b-112">Custom handlers can then subscribe to, retrieve, and handle the message as required.</span></span>  
  
## <a name="subscription-to-outbound-messages"></a><span data-ttu-id="de93b-113">Abonnement aux Messages sortants</span><span class="sxs-lookup"><span data-stu-id="de93b-113">Subscription to Outbound Messages</span></span>  
 <span data-ttu-id="de93b-114">L’orchestration FRR est directement liée à la MessageBox.</span><span class="sxs-lookup"><span data-stu-id="de93b-114">The FRR orchestration is directly bound to the MessageBox.</span></span> <span data-ttu-id="de93b-115">L’orchestration FRR s’abonne à tous les messages sortants pour le réseau rapide qui ne contiennent pas d’erreurs de validation, en vous abonnant aux propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="de93b-115">The FRR orchestration subscribes to all outbound messages bound for the SWIFT network that do not contain validation errors, by subscribing to the following properties:</span></span>  
  
-   [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]<span data-ttu-id="de93b-116">_Failed == false (comme défini par le processus de validation SWIFT désassembleur)</span><span class="sxs-lookup"><span data-stu-id="de93b-116">_Failed==False (as set by the SWIFT Disassembler validation process)</span></span>  
  
-   [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]<span data-ttu-id="de93b-117">_Swiftbound == true (comme défini par le processus de configuration SWIFT désassembleur)</span><span class="sxs-lookup"><span data-stu-id="de93b-117">_Swiftbound==True (as set by the SWIFT Disassembler configuration process)</span></span>  
  
## <a name="messageresponse-correlation"></a><span data-ttu-id="de93b-118">Corrélation de message de réponse</span><span class="sxs-lookup"><span data-stu-id="de93b-118">Message/Response Correlation</span></span>  
 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="de93b-119">met en corrélation du message sortant original de FIN pour le message de réponse FIN entrant en comparant les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="de93b-119"> correlates the original outbound FIN message to the inbound FIN response message by comparing the following properties:</span></span>  
  
-   <span data-ttu-id="de93b-120">La propriété de contexte MQMD_CorrelID de la réponse FIN</span><span class="sxs-lookup"><span data-stu-id="de93b-120">The MQMD_CorrelID context property of the FIN response</span></span>  
  
-   <span data-ttu-id="de93b-121">Le [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]propriété _FRRCorrelationToken du message sortant MTXYY.</span><span class="sxs-lookup"><span data-stu-id="de93b-121">The [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_FRRCorrelationToken property of the outbound MTXYY message.</span></span> <span data-ttu-id="de93b-122">Cette propriété est promue par la phase de résolution de tiers du pipeline de réception.</span><span class="sxs-lookup"><span data-stu-id="de93b-122">This property is promoted by the party-resolution stage of the receive pipeline.</span></span>  
  
 <span data-ttu-id="de93b-123">Les valeurs de ces propriétés doivent être identiques.</span><span class="sxs-lookup"><span data-stu-id="de93b-123">The values of these properties must be identical.</span></span> <span data-ttu-id="de93b-124">L’étape de l’encodeur du pipeline d’envoi de messages liés pour SWIFT définit la propriété MQMD_MsgID du message sortant à la valeur de la [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_FRRCorrelationToken propriété.</span><span class="sxs-lookup"><span data-stu-id="de93b-124">The encoder stage of the send pipeline for messages bound for SWIFT sets the MQMD_MsgID property of the outgoing message to the value of the [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_FRRCorrelationToken property.</span></span> <span data-ttu-id="de93b-125">SAA définit la propriété MQMD_CorrelID du message de réponse à la valeur de MQMD_MsgID.</span><span class="sxs-lookup"><span data-stu-id="de93b-125">SAA sets the MQMD_CorrelID property of the response message to the value of MQMD_MsgID.</span></span>  
  
## <a name="setting-of-promoted-properties"></a><span data-ttu-id="de93b-126">Définition des propriétés promues</span><span class="sxs-lookup"><span data-stu-id="de93b-126">Setting of Promoted Properties</span></span>  
 <span data-ttu-id="de93b-127">Après réception d’une réponse FIN et corrélation à la copie du message d’origine, l’orchestration FRR définit les propriétés promues suivantes de la copie du message d’origine en fonction de la nature de la réponse :</span><span class="sxs-lookup"><span data-stu-id="de93b-127">After receiving a FIN response and correlating it to the copy of the original message, the FRR orchestration sets the following promoted properties of the copy of the original message according to the nature of the response:</span></span>  
  
-   [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]<span data-ttu-id="de93b-128">_FRRFailed à la valeur True si la réponse était un accusé de réception ou un faux si la réponse était un NAK</span><span class="sxs-lookup"><span data-stu-id="de93b-128">_FRRFailed to True if the response was an ACK or False if the response was a NAK</span></span>  
  
-   [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]<span data-ttu-id="de93b-129">_FRRFailedReason à l’une des valeurs suivantes, si la réponse était un NAK :</span><span class="sxs-lookup"><span data-stu-id="de93b-129">_FRRFailedReason to the one of the following values, if the response was a NAK:</span></span>  
  
    -   <span data-ttu-id="de93b-130">*\<Code d’erreur >* (à partir du champ 405 du message accusé de réception négatif MTS21_FIN_ACKNAK)</span><span class="sxs-lookup"><span data-stu-id="de93b-130">*\<ErrorCode>* (from the 405 field of the MTS21_FIN_ACKNAK negative-acknowledgment message)</span></span>  
  
    -   <span data-ttu-id="de93b-131">TransportError (à partir d’un message MQ Series panoramique/NAN)</span><span class="sxs-lookup"><span data-stu-id="de93b-131">TransportError (from an MQ Series PAN/NAN message)</span></span>  
  
    -   <span data-ttu-id="de93b-132">DelayedNAK (à partir d’un message MT015 (DNK))</span><span class="sxs-lookup"><span data-stu-id="de93b-132">DelayedNAK (from an MT015 (DNK) message)</span></span>  
  
    -   <span data-ttu-id="de93b-133">AbortReceived (à partir d’un MT019 message (Notification abandonner))</span><span class="sxs-lookup"><span data-stu-id="de93b-133">AbortReceived (from an MT019 (Abort Notification) message)</span></span>  
  
-   [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]<span data-ttu-id="de93b-134">_FRRFailedReason à TimedOut si [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] n’a pas reçu de réponse dans le délai imparti.</span><span class="sxs-lookup"><span data-stu-id="de93b-134">_FRRFailedReason to TimedOut if [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] did not receive a response within the timeout period.</span></span> <span data-ttu-id="de93b-135">Pour plus d’informations sur le délai d’expiration de délai FRR, consultez la section « Délai d’attente de la réconciliation » ci-dessous ou [définir le délai d’expiration du délai de FRR](../../adapters-and-accelerators/accelerator-swift/setting-the-frr-delay-time-out.md).</span><span class="sxs-lookup"><span data-stu-id="de93b-135">For more information about the FRR Delay Time-out, see the "Reconciliation Time-Out" section below or [Setting the FRR Delay Time-Out](../../adapters-and-accelerators/accelerator-swift/setting-the-frr-delay-time-out.md).</span></span>  
  
-   [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]<span data-ttu-id="de93b-136">_SendingServiceType à [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_FrrService</span><span class="sxs-lookup"><span data-stu-id="de93b-136">_SendingServiceType to [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_FrrService</span></span>  
  
-   <span data-ttu-id="de93b-137">BIZTALK SERVER. Opération à la valeur correspondant au type de réponse du message.</span><span class="sxs-lookup"><span data-stu-id="de93b-137">BTS.Operation to the value corresponding to the type of message response.</span></span> <span data-ttu-id="de93b-138">Pour plus d’informations, consultez [créer les Ports d’envoi FRR à envoyer aux gestionnaires personnalisé](../../adapters-and-accelerators/accelerator-swift/creating-the-frr-send-ports-for-sending-to-the-custom-handlers.md).</span><span class="sxs-lookup"><span data-stu-id="de93b-138">For more information, see [Creating the FRR Send Ports for Sending to the Custom Handlers](../../adapters-and-accelerators/accelerator-swift/creating-the-frr-send-ports-for-sending-to-the-custom-handlers.md).</span></span>  
  
    -   [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]<span data-ttu-id="de93b-139">_FrrSendTransport pour un message MQ Series panoramique/NAN (au niveau du transport MQSeries l’accusé de réception/NON-RÉCEPTION)</span><span class="sxs-lookup"><span data-stu-id="de93b-139">_FrrSendTransport for an MQ Series PAN/NAN message (MQ Series transport-level ACK/NAK)</span></span>  
  
    -   [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]<span data-ttu-id="de93b-140">_FrrSend010NDW pour un message MT010 (avertissement de Non remise)</span><span class="sxs-lookup"><span data-stu-id="de93b-140">_FrrSend010NDW for an MT010 message (Non-Delivery Warning)</span></span>  
  
    -   [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]<span data-ttu-id="de93b-141">_FrrSend011Delivered pour un message MT011 (accusé de réception)</span><span class="sxs-lookup"><span data-stu-id="de93b-141">_FrrSend011Delivered for an MT011 message (Delivery Notification)</span></span>  
  
    -   [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]<span data-ttu-id="de93b-142">_FrrSend012SenderACK pour un message MT012 (Sender Notification)</span><span class="sxs-lookup"><span data-stu-id="de93b-142">_FrrSend012SenderACK for an MT012 message (Sender Notification)</span></span>  
  
    -   [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]<span data-ttu-id="de93b-143">_FrrSend015DNK pour un message MT015 (DNK ou NAK de retardée)</span><span class="sxs-lookup"><span data-stu-id="de93b-143">_FrrSend015DNK for an MT015 message (DNK, or Delayed NAK)</span></span>  
  
    -   [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]<span data-ttu-id="de93b-144">_FrrSend019Abort pour un message MT019 (abandonner un Notification)</span><span class="sxs-lookup"><span data-stu-id="de93b-144">_FrrSend019Abort for an MT019 message (Abort Notification)</span></span>  
  
    -   [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]<span data-ttu-id="de93b-145">_FrrSendS21ACK pour un message d’accusé de réception MTS21_FIN_ACKNAK (accusé de réception d’un message FIN envoyé par un LT)</span><span class="sxs-lookup"><span data-stu-id="de93b-145">_FrrSendS21ACK for an MTS21_FIN_ACKNAK acknowledgment message (ACK of a FIN message sent by an LT)</span></span>  
  
    -   [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]<span data-ttu-id="de93b-146">_FrrSendS21NAK pour un message de-accusé de réception négatif (NAK d’un message FIN envoyé par un LT) MTS21_FIN_ACKNAK</span><span class="sxs-lookup"><span data-stu-id="de93b-146">_FrrSendS21NAK for an MTS21_FIN_ACKNAK negative-acknowledgment message (NAK of a FIN message sent by an LT)</span></span>  
  
## <a name="direct-binding"></a><span data-ttu-id="de93b-147">Liaison directe</span><span class="sxs-lookup"><span data-stu-id="de93b-147">Direct Binding</span></span>  
 <span data-ttu-id="de93b-148">Recevoir des entrées de l’orchestration sont définies par les abonnements par l’orchestration vers la MessageBox.</span><span class="sxs-lookup"><span data-stu-id="de93b-148">Receive inputs for the orchestration are defined by subscriptions that the orchestration makes to the MessageBox.</span></span> <span data-ttu-id="de93b-149">Propriétés de contexte et de valeurs promues par l’orchestration définissent les sorties de l’envoi d’un message de l’orchestration publie vers la MessageBox.</span><span class="sxs-lookup"><span data-stu-id="de93b-149">Context properties and values promoted by the orchestration define the send outputs for a message that the orchestration publishes to the MessageBox.</span></span> <span data-ttu-id="de93b-150">En raison de cette liaison directe vers la MessageBox, l’orchestration est dissociée de la manière suivante :</span><span class="sxs-lookup"><span data-stu-id="de93b-150">Because of this direct binding to the MessageBox, the orchestration is decoupled from the following:</span></span>  
  
-   <span data-ttu-id="de93b-151">Emplacements de réception des messages sortants à partir de l’application principale pour le routage à SAA de réception physique</span><span class="sxs-lookup"><span data-stu-id="de93b-151">The physical receive locations that receive outbound messages from the back-end application for routing to SAA</span></span>  
  
-   <span data-ttu-id="de93b-152">Les ports d’envoi qui envoient sortants FIN des messages à partir de [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] pour l’accès de Alliance SWIFT (SAA)</span><span class="sxs-lookup"><span data-stu-id="de93b-152">The send ports that send outbound FIN messages from [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] to the SWIFT Alliance Access (SAA)</span></span>  
  
-   <span data-ttu-id="de93b-153">Les emplacements de réception qui reçoivent des messages de réponse entrants FIN de SAA</span><span class="sxs-lookup"><span data-stu-id="de93b-153">The receive locations that receive incoming FIN response messages from SAA</span></span>  
  
-   <span data-ttu-id="de93b-154">Les files d’attente MQSeries physiques où les réponses FIN sont déposés par SAA</span><span class="sxs-lookup"><span data-stu-id="de93b-154">The physical MQSeries queues where FIN responses are deposited by SAA</span></span>  
  
## <a name="reconciliation-time-out"></a><span data-ttu-id="de93b-155">Délai d’attente de rapprochement</span><span class="sxs-lookup"><span data-stu-id="de93b-155">Reconciliation Time-Out</span></span>  
 <span data-ttu-id="de93b-156">Lorsque [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] crée une nouvelle instance de l’orchestration FRR, le démarrage de l’orchestration en attente de réponses FIN.</span><span class="sxs-lookup"><span data-stu-id="de93b-156">When [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] creates a new instance of the FRR orchestration, the orchestration starts waiting for FIN responses.</span></span> <span data-ttu-id="de93b-157">Au moment de l’exécution, vous devez configurer l’orchestration expire après une durée, afin qu’il n’attendra pas la réponse indéfiniment.</span><span class="sxs-lookup"><span data-stu-id="de93b-157">At run time, you must configure the orchestration to time out after some duration, so that it will not wait for the response indefinitely.</span></span> <span data-ttu-id="de93b-158">Lorsque la durée du délai d’attente expire, l’orchestration FRR promeut le [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_FRRFailedReason propriété et lui affecte la valeur de délai d’attente.</span><span class="sxs-lookup"><span data-stu-id="de93b-158">When the time-out duration expires, the FRR orchestration promotes the [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]_FRRFailedReason property and sets it to TimedOut.</span></span> <span data-ttu-id="de93b-159">Il publie des messages sortants dans la MessageBox et se termine.</span><span class="sxs-lookup"><span data-stu-id="de93b-159">It then publishes messages out to the MessageBox, and terminates.</span></span> <span data-ttu-id="de93b-160">Si le délai d’attente, l’ID de corrélation a disparu.</span><span class="sxs-lookup"><span data-stu-id="de93b-160">If you time out, the correlation ID is gone.</span></span>  
  
 <span data-ttu-id="de93b-161">Vous pouvez créer un gestionnaire personnalisé pour traiter les messages expiré (la copie du message sortant d’origine).</span><span class="sxs-lookup"><span data-stu-id="de93b-161">You can create a custom handler to process timed-out messages (the copy of the original outbound message).</span></span> [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)]<span data-ttu-id="de93b-162">serait cela à l’aide d’une forme écouter dans l’orchestration.</span><span class="sxs-lookup"><span data-stu-id="de93b-162"> would accomplish this by using a Listen shape in the orchestration.</span></span> <span data-ttu-id="de93b-163">Pour plus d’informations, consultez [définir le délai d’expiration du délai de FRR](../../adapters-and-accelerators/accelerator-swift/setting-the-frr-delay-time-out.md).</span><span class="sxs-lookup"><span data-stu-id="de93b-163">For more information, see [Setting the FRR Delay Time-Out](../../adapters-and-accelerators/accelerator-swift/setting-the-frr-delay-time-out.md).</span></span>