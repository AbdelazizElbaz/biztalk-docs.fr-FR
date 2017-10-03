---
title: "Envoi d’un accusé de réception EDI | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4a036d08-8a65-43ad-b72c-2a246d302792
caps.latest.revision: "31"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5a47a3fbe13f4cf054b6114050b8777231c4b217
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="sending-an-edi-acknowledgment"></a><span data-ttu-id="306b2-102">Envoi d'un accusé de réception EDI</span><span class="sxs-lookup"><span data-stu-id="306b2-102">Sending an EDI Acknowledgment</span></span>
<span data-ttu-id="306b2-103">Les accusés de réception indiquent l'état de transmission du message EDI.</span><span class="sxs-lookup"><span data-stu-id="306b2-103">Acknowledgments indicate the status of EDI message transmission.</span></span> <span data-ttu-id="306b2-104">Une fois que [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] a reçu un échange EDI, il renvoie un ou plusieurs accusés de réception à l'expéditeur d'un échange EDI, selon les accusés de réception activés.</span><span class="sxs-lookup"><span data-stu-id="306b2-104">After [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] receives an EDI interchange, it will return one or more acknowledgments to the sender of an EDI interchange, depending upon which acknowledgments have been enabled.</span></span>  
  
 <span data-ttu-id="306b2-105">En fonction du niveau de validation, les accusés de réception de message EDI se répartissent en deux types :</span><span class="sxs-lookup"><span data-stu-id="306b2-105">Based on the level of validation, EDI message acknowledgments fall into two types:</span></span>  
  
-   <span data-ttu-id="306b2-106">A **accusé de réception technique** générée en raison de la validation de l’en-tête.</span><span class="sxs-lookup"><span data-stu-id="306b2-106">A **Technical Acknowledgment** generated as a result of header validation.</span></span> <span data-ttu-id="306b2-107">L'accusé de réception technique indique l'état du traitement de l'en-tête et du code de fin d'un échange par le récepteur d'adresse.</span><span class="sxs-lookup"><span data-stu-id="306b2-107">The technical acknowledgment reports the status of the processing of an interchange header and trailer by the address receiver.</span></span>  
  
-   <span data-ttu-id="306b2-108">A **accusé de réception fonctionnel** générée en raison de la validation du corps.</span><span class="sxs-lookup"><span data-stu-id="306b2-108">A **Functional Acknowledgment** generated as a result of body validation.</span></span> <span data-ttu-id="306b2-109">L'accusé de réception fonctionnel signale chaque erreur rencontrée lors du traitement du document reçu.</span><span class="sxs-lookup"><span data-stu-id="306b2-109">The functional acknowledgment reports each error encountered while processing the received document.</span></span>  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="306b2-110"> peut renvoyer des accusés de réception techniques et fonctionnels en réponse à un échange unique.</span><span class="sxs-lookup"><span data-stu-id="306b2-110"> can return both technical and functional acknowledgments in response to a single interchange.</span></span> [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="306b2-111"> renvoie un seul accusé de réception technique par échange.</span><span class="sxs-lookup"><span data-stu-id="306b2-111"> returns a single technical acknowledgment for each interchange.</span></span> <span data-ttu-id="306b2-112">Pour les échanges X12, il renvoie un accusé de réception fonctionnel par groupe reçu.</span><span class="sxs-lookup"><span data-stu-id="306b2-112">For X12 interchanges, it will return a functional acknowledgment for each group received.</span></span> <span data-ttu-id="306b2-113">Pour les échanges EDIFACT, il renvoie un accusé de réception fonctionnel par échange, quel que soit le nombre de groupes dans l'échange.</span><span class="sxs-lookup"><span data-stu-id="306b2-113">For EDIFACT interchanges, it will return a functional acknowledgment for each interchange, no matter how many groups that interchange contains.</span></span>  
  
## <a name="x12-acknowledgments"></a><span data-ttu-id="306b2-114">Accusés de réception X12</span><span class="sxs-lookup"><span data-stu-id="306b2-114">X12 Acknowledgments</span></span>  
 <span data-ttu-id="306b2-115">**X12 accusé de réception technique**</span><span class="sxs-lookup"><span data-stu-id="306b2-115">**X12 Technical Acknowledgment**</span></span>  
  
 <span data-ttu-id="306b2-116">Un accusé de réception TA1 positif est envoyé si l'en-tête ISA et le code de fin IEA d'un message X12 sont valides (indépendamment de tout autre contenu).</span><span class="sxs-lookup"><span data-stu-id="306b2-116">A positive TA1 acknowledgment is sent if the ISA header and the IEA trailer of an X12 message are valid (irrespective of other content).</span></span> <span data-ttu-id="306b2-117">Pour plus d’informations sur le contenu d’un accusé de réception TA1, consultez [X12 accusé de réception TA1](../core/x12-ta1-acknowledgment.md).</span><span class="sxs-lookup"><span data-stu-id="306b2-117">For more information on the contents of a TA1 acknowledgment, see [X12 TA1 Acknowledgment](../core/x12-ta1-acknowledgment.md).</span></span>  
  
 <span data-ttu-id="306b2-118">**X12 accusé de réception fonctionnel**</span><span class="sxs-lookup"><span data-stu-id="306b2-118">**X12 Functional Acknowledgment**</span></span>  
  
 <span data-ttu-id="306b2-119">Un accusé de réception 997 sert à confirmer la réception d'un échange ou d'un groupe fonctionnel, à accepter ou refuser un ou plusieurs groupes fonctionnels ou une ou plusieurs documents et à vérifier ou signaler la conformité aux standard.</span><span class="sxs-lookup"><span data-stu-id="306b2-119">A 997 acknowledgment is used to acknowledge receipt of an interchange or a functional group, to accept or reject one or more functional groups or one or more transactions, and to verify and report compliance with the standard.</span></span> <span data-ttu-id="306b2-120">Si [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] reçoit un échange avec plusieurs groupes, il renvoie un accusé de réception par groupe.</span><span class="sxs-lookup"><span data-stu-id="306b2-120">If [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] receives an interchange with multiple groups, it will return an acknowledgment for each group.</span></span> <span data-ttu-id="306b2-121">Si un groupe contient plusieurs documents informatisés, l'accusé de réception pour ce groupe comporte plusieurs boucles AK2, une par document informatisé, selon qu'il convient de générer des boucles AK2 pour les documents informatisés acceptés.</span><span class="sxs-lookup"><span data-stu-id="306b2-121">If a group contains multiple transaction sets, the acknowledgment for that group will contain multiple AK2 loops, one for each transaction set, depending upon whether AK2 loops are generated for accepted transaction sets.</span></span> <span data-ttu-id="306b2-122">Pour plus d’informations sur le contenu d’un accusé de réception 997, consultez [X12 accusé de réception 997](../core/x12-997-acknowledgment.md).</span><span class="sxs-lookup"><span data-stu-id="306b2-122">For more information on the contents of a 997 acknowledgment, see [X12 997 Acknowledgment](../core/x12-997-acknowledgment.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="306b2-123">Lorsque le pipeline de réception EDI crée le segment En-tête de groupe fonctionnel (GS) pour l'accusé de réception fonctionnel X12, les codes de l'expéditeur de l'application (GS02) et du récepteur de l'application (GS03) proviennent du groupe fonctionnel dont il est accusé réception.</span><span class="sxs-lookup"><span data-stu-id="306b2-123">When the EDI receive pipeline builds the Functional Group Header (GS) segment for the X12 functional ACK, the Application Sender Code (GS02) and Application Receiver Code (GS03) are taken from the functional group being acknowledged.</span></span> <span data-ttu-id="306b2-124">Cependant, GS02 sur le message entrant est mappé à GS03 sur l'accusé de réception et GS03 sur le message entrant est mappé à GS02 sur l'accusé de réception.</span><span class="sxs-lookup"><span data-stu-id="306b2-124">However, GS02 on incoming message is mapped to GS03 on the ACK and GS03 on incoming message is mapped to GS02 on the ACK.</span></span>  
  
## <a name="edifact-acknowledgments"></a><span data-ttu-id="306b2-125">Accusés de réception EDIFACT</span><span class="sxs-lookup"><span data-stu-id="306b2-125">EDIFACT Acknowledgments</span></span>  
 <span data-ttu-id="306b2-126">**Accusé de réception technique EDIFACT**</span><span class="sxs-lookup"><span data-stu-id="306b2-126">**EDIFACT Technical Acknowledgment**</span></span>  
  
 <span data-ttu-id="306b2-127">Pour EDIFACT, un accusé de réception technique distinct n'est pas utilisé, mais des sections de l'accusé de réception fonctionnel ou de l'accusé de réception CONTRL (voir ci-après) sont réutilisées pour l'accusé de réception.</span><span class="sxs-lookup"><span data-stu-id="306b2-127">For EDIFACT, a separate technical acknowledgment is not used, but sections of the functional acknowledgment or CONTRL ACK (see below) are reused for the receipt ACK.</span></span> <span data-ttu-id="306b2-128">Il émule un accusé de réception technique.</span><span class="sxs-lookup"><span data-stu-id="306b2-128">This emulates a technical acknowledgment.</span></span>  
  
 <span data-ttu-id="306b2-129">Pour plus d’informations sur l’accusé de réception technique CONTRL, consultez [Message de CONTRL EDIFACT comme accusé de réception technique](../core/edifact-contrl-message-as-technical-acknowledgment.md).</span><span class="sxs-lookup"><span data-stu-id="306b2-129">For more information on the technical CONTRL acknowledgment, see [EDIFACT CONTRL Message as Technical Acknowledgment](../core/edifact-contrl-message-as-technical-acknowledgment.md).</span></span>  
  
 <span data-ttu-id="306b2-130">**Accusé de réception fonctionnel EDIFACT**</span><span class="sxs-lookup"><span data-stu-id="306b2-130">**EDIFACT Functional Acknowledgment**</span></span>  
  
 <span data-ttu-id="306b2-131">Pour EDIFACT, l'accusé de réception fonctionnel CONTRL sert à confirmer la réception d'un échange, d'un groupe et d'un message reçus, à accepter ou refuser un échange, un groupe et un message reçus, et à répertorier toute erreur syntaxique ou fonctionnalité non prise en charge qu'ils pourraient contenir.</span><span class="sxs-lookup"><span data-stu-id="306b2-131">For EDIFACT, the functional CONTRL acknowledgment is used to acknowledge a received interchange, group, and message; accept or reject a received interchange, group, and message; and to list any syntactical errors or unsupported functionality contained in them.</span></span> <span data-ttu-id="306b2-132">L'accusé de réception CONTRL communique les résultats d'une vérification syntaxique de l'échange complet reçu.</span><span class="sxs-lookup"><span data-stu-id="306b2-132">The CONTRL ACK reports the results of a syntactical check of the complete received interchange.</span></span>  
  
 <span data-ttu-id="306b2-133">Pour plus d’informations sur l’accusé de réception fonctionnel CONTRL, consultez [Message de CONTRL EDIFACT comme accusé de réception fonctionnel](../core/edifact-contrl-message-as-functional-acknowledgment.md).</span><span class="sxs-lookup"><span data-stu-id="306b2-133">For more information on the functional CONTRL acknowledgment, see [EDIFACT CONTRL Message as Functional Acknowledgment](../core/edifact-contrl-message-as-functional-acknowledgment.md).</span></span>  
  
## <a name="when-an-acknowledgment-is-generated"></a><span data-ttu-id="306b2-134">Lorsqu'un accusé de réception est généré</span><span class="sxs-lookup"><span data-stu-id="306b2-134">When an Acknowledgment Is Generated</span></span>  
 <span data-ttu-id="306b2-135">Le pipeline de réception EDI génère un accusé de réception si l'une des conditions suivantes est remplie :</span><span class="sxs-lookup"><span data-stu-id="306b2-135">The EDI receive pipeline will generate an acknowledgment if either of the following conditions are met:</span></span>  
  
-   <span data-ttu-id="306b2-136">Un élément de données dans l'échange reçu demande l'accusé de réception.</span><span class="sxs-lookup"><span data-stu-id="306b2-136">A data element in the received interchange prompts the acknowledgment.</span></span> <span data-ttu-id="306b2-137">Pour les messages X12, le pipeline de réception génère un accusé de réception technique TA1 si l'élément de données ISA12 est défini sur 1.</span><span class="sxs-lookup"><span data-stu-id="306b2-137">For X12-encoded messages, the receive pipeline will generate a technical TA1 ACK if the ISA14 data element is set to 1.</span></span> <span data-ttu-id="306b2-138">Pour les messages EDIFACT, le pipeline de réception génère un accusé de réception technique CONTRL si l'élément de données UNB9 est défini sur 2 et un accusé de réception fonctionnel CONTRL si l'élément de données UNB9 est défini sur 1.</span><span class="sxs-lookup"><span data-stu-id="306b2-138">For EDIFACT-encoded messages, the receive pipeline will generate a technical CONTRL ACK if the UNB9 data element is set to 2, and it will generate a functional CONTRL ACK if the UNB9 data element is set to 1.</span></span>  
  
-   <span data-ttu-id="306b2-139">Une propriété d'accord demande l'accusé de réception.</span><span class="sxs-lookup"><span data-stu-id="306b2-139">An agreement property prompts the acknowledgment.</span></span> <span data-ttu-id="306b2-140">Pour les échanges de X12, ces propriétés sont les **TA1 attendu** et **997 attendu** propriétés dans le **accusés de réception** page d’onglets de l’accord bidirectionnel de la **Propriétés de l’accord** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="306b2-140">For X12 interchanges, these properties are the **TA1 Expected** and **997 Expected** properties in the **Acknowledgements** page of the bi-directional agreement tabs of the **Agreement Properties** dialog box.</span></span> <span data-ttu-id="306b2-141">Pour les échanges EDIFACT, ces propriétés sont les **réception du message (CONTRL) attendu** et **accusé de réception (CONTRL) attendu** dans les **accusés de réception** page de les onglets d’accord bidirectionnel de la **propriétés de l’accord** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="306b2-141">For EDIFACT interchanges, these properties are the **Receipt of message (CONTRL) expected** and **Acknowledgement (CONTRL) expected** in the **Acknowledgements** page of the bi-directional agreement tabs of the **Agreement Properties** dialog box.</span></span> <span data-ttu-id="306b2-142">Lorsque vous activez un type d'accusé de réception, vous pouvez également indiquer s'il convient de le traiter par lot.</span><span class="sxs-lookup"><span data-stu-id="306b2-142">When you enable a type of acknowledgment, you can also indicate whether to batch that type of acknowledgment.</span></span>  
  
-   <span data-ttu-id="306b2-143">Une propriété globale demande l'accusé de réception lorsqu'aucun accord n'est déterminé pour l'échange.</span><span class="sxs-lookup"><span data-stu-id="306b2-143">A global property prompts the acknowledgment when no agreement is determined for the interchange.</span></span> <span data-ttu-id="306b2-144">Ces propriétés sont les propriétés</span><span class="sxs-lookup"><span data-stu-id="306b2-144">These properties are the</span></span>  
  
    -   <span data-ttu-id="306b2-145">**TA1 attendu** et **997 attendu** propriétés dans le **accusés de réception** page de l’onglet d’accord de la **X12 paramètres de secours** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="306b2-145">**TA1 Expected** and **997 Expected** properties in the **Acknowledgements** page of the agreement tab of the **X12 Fallback Settings** dialog box.</span></span>  
  
    -   <span data-ttu-id="306b2-146">**Réception du message (CONTRL) attendu** et **accusé de réception (CONTRL) attendu** dans les **accusés de réception** page de l’onglet d’accord de la **EDIFACT secours Paramètres** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="306b2-146">**Receipt of message (CONTRL) expected** and **Acknowledgement (CONTRL) expected** in the **Acknowledgements** page of the agreement tab of the **EDIFACT Fallback Settings** dialog box.</span></span>  
  
 <span data-ttu-id="306b2-147">Pour EDIFACT, le pipeline de réception EDI renvoie deux accusés de réception CONTRL distincts si un accusé de réception technique et un accusé de réception fonctionnel sont demandés.</span><span class="sxs-lookup"><span data-stu-id="306b2-147">For EDIFACT, the EDI receive pipeline will return two separate CONTRL acknowledgments if both a technical acknowledgment and a functional acknowledgment are prompted.</span></span> <span data-ttu-id="306b2-148">L'accusé de réception technique CONTRL inclut uniquement des informations de l'accusé de réception.</span><span class="sxs-lookup"><span data-stu-id="306b2-148">The technical CONTRL ACK will include receipt acknowledgment information only.</span></span> <span data-ttu-id="306b2-149">L'accusé de réception fonctionnel CONTRL inclut des informations sur la réception et des informations de l'accusé de réception fonctionnel.</span><span class="sxs-lookup"><span data-stu-id="306b2-149">The functional CONTRL ACK will include both receipt information and functional acknowledgment information.</span></span> <span data-ttu-id="306b2-150">Pour plus d’informations, consultez [accusé de réception EDIFACT CONTRL](../core/edifact-contrl-acknowledgment.md).</span><span class="sxs-lookup"><span data-stu-id="306b2-150">For more information, see [EDIFACT CONTRL Acknowledgment](../core/edifact-contrl-acknowledgment.md).</span></span>  
  
## <a name="identifying-an-acknowledgment-with-a-control-number"></a><span data-ttu-id="306b2-151">Identification d'un accusé de réception avec un nombre de contrôle</span><span class="sxs-lookup"><span data-stu-id="306b2-151">Identifying an Acknowledgment with a Control Number</span></span>  
 <span data-ttu-id="306b2-152">Chaque accusé de réception doit être identifié par un numéro de contrôle du document informatisé pour X12 (élément de données ST2) ou un numéro de référence du document informatisé pour EDIFACT (élément de données UNH1).</span><span class="sxs-lookup"><span data-stu-id="306b2-152">Each acknowledgment needs to be identified by a transaction set control number for X12 (the ST2 data element) or a transaction set reference number for EDIFACT (the UNH1 data element).</span></span> <span data-ttu-id="306b2-153">Si un accord est configuré pour l'accusé de réception sortant, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] définit le numéro de contrôle ou le numéro de référence du document informatisé sur la valeur définie pour l'accord, comme suit :</span><span class="sxs-lookup"><span data-stu-id="306b2-153">If an agreement is configured for the outgoing acknowledgment, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will set the transaction set control or reference number to the value set for the agreement based on the following:</span></span>  
  
-   <span data-ttu-id="306b2-154">**Pour X12 accusés de réception** – (**numéro de contrôle de l’accusé de réception (ST02)** propriété dans **paramètres d’hôte Local** Page (**paramètres du récepteur** section) de l’accord onglet **propriétés de l’accord** boîte de dialogue</span><span class="sxs-lookup"><span data-stu-id="306b2-154">**For X12 acknowledgements** – (**ACK Control number (ST02)** property in **Local Host Settings** Page (**Receiver’s Settings** section) of the agreement tab in **Agreement Properties** dialog box</span></span>  
  
-   <span data-ttu-id="306b2-155">**Pour les accusés de réception EDIFACT** – (**numéro de contrôle de l’accusé de réception Edifact** propriété dans **paramètres d’hôte Local** Page (**paramètres du récepteur** section) de la onglet d’accord de **propriétés de l’accord** boîte de dialogue</span><span class="sxs-lookup"><span data-stu-id="306b2-155">**For EDIFACT acknowledgements** – (**Edifact Ack Control number** property in **Local Host Settings** Page (**Receiver’s Settings** section) of the agreement tab in **Agreement Properties** dialog box</span></span>  
  
 <span data-ttu-id="306b2-156">Si [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ne détermine pas l’accord pour l’accusé de réception, il utilise les mêmes propriétés comme mentionnées précédemment mais disponibles sous l’onglet d’accord dans le **X12 paramètres de secours** ad **EDIFACT secours Paramètres** boîtes de dialogue.</span><span class="sxs-lookup"><span data-stu-id="306b2-156">If [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] does not determine the agreement for the acknowledgment, it will use the same properties as mentioned above but available on the agreement tab in the **X12 Fallback Settings** ad **EDIFACT Fallback Settings** dialog boxes.</span></span> <span data-ttu-id="306b2-157">Ce paramétrage s'applique aux accusés de réception techniques et fonctionnels si les deux sont configurés.</span><span class="sxs-lookup"><span data-stu-id="306b2-157">This setting applies to both the technical and functional acknowledgments if both are configured.</span></span> <span data-ttu-id="306b2-158">Cet entier est incrémenté d'une unité pour chaque accusé de réception ou échange généré.</span><span class="sxs-lookup"><span data-stu-id="306b2-158">This integer will be incremented by one for each acknowledgment or interchange generated.</span></span>  
  
 <span data-ttu-id="306b2-159">L'enveloppe d'un accusé de réception est créée à partir des données du message reçu, selon le schéma de contrôle d'accusé de réception.</span><span class="sxs-lookup"><span data-stu-id="306b2-159">The envelope of an acknowledgment is built from data in the received message according to the acknowledgment control schema.</span></span>  
  
## <a name="preparing-the-acknowledgment"></a><span data-ttu-id="306b2-160">Préparation de l'accusé de réception</span><span class="sxs-lookup"><span data-stu-id="306b2-160">Preparing the Acknowledgment</span></span>  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="306b2-161"> crée l'enveloppe pour un accusé de réception comme il crée une enveloppe pour un message, en examinant les définitions de l'en-tête de contrôle de l'échange et de l'en-tête de groupe fonctionnel.</span><span class="sxs-lookup"><span data-stu-id="306b2-161"> builds the envelope for an acknowledgment just as it builds an envelope for a message, by looking at the definitions of the Interchange Control Header and the Functional Group Header.</span></span> <span data-ttu-id="306b2-162">Pour plus d’informations, consultez [résolution de l’accord et détermination du schéma pour les Messages EDI sortants](../core/agreement-resolution-and-schema-determination-for-outgoing-edi-messages.md).</span><span class="sxs-lookup"><span data-stu-id="306b2-162">For more information, see [Agreement Resolution and Schema Determination for Outgoing EDI Messages](../core/agreement-resolution-and-schema-determination-for-outgoing-edi-messages.md).</span></span>  
  
 <span data-ttu-id="306b2-163">Pour activer le routage sans problème de l'accusé de réception généré (TA1, 997 ou CONTRL), le Désassembleur EDI renseigne les propriétés `DestinationPartyReceiverQualifier`, `DestinationPartyReceiverIdentifier`, `DestinationPartySenderQualifier` et `DestinationPartySenderIdentifier` sur l'accusé de réception.</span><span class="sxs-lookup"><span data-stu-id="306b2-163">To enable seamless routing of the generated acknowledgment (TA1, 997, or CONTRL), the EDI Disassembler will populate the `DestinationPartyReceiverQualifier`, `DestinationPartyReceiverIdentifier`, `DestinationPartySenderQualifier`, and `DestinationPartySenderIdentifier` properties on the acknowledgment.</span></span>  
  
## <a name="synchronous-and-asynchronous-acknowledgments"></a><span data-ttu-id="306b2-164">Accusés de réception synchrones et asynchrones</span><span class="sxs-lookup"><span data-stu-id="306b2-164">Synchronous and Asynchronous Acknowledgments</span></span>  
 <span data-ttu-id="306b2-165">Vous pouvez choisir d'envoyer des accusés de réception EDI de manière synchrone ou asynchrone.</span><span class="sxs-lookup"><span data-stu-id="306b2-165">You can choose to send EDI acknowledgments either synchronously or asynchronously.</span></span> <span data-ttu-id="306b2-166">En mode synchrone, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] route l'accusé de réception directement vers le pipeline d'envoi du port de réception requête-réponse bidirectionnel.</span><span class="sxs-lookup"><span data-stu-id="306b2-166">If synchronous, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will route the acknowledgment directly to the send pipeline of a two-way request-response receive port.</span></span> <span data-ttu-id="306b2-167">En mode asynchrone, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] route l'accusé de réception vers la base de données MessageBox et un port d'envoi s'abonne à ce message.</span><span class="sxs-lookup"><span data-stu-id="306b2-167">If asynchronous, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will route the acknowledgment to the MessageBox, and a send port will subscribe to that message.</span></span>  
  
 <span data-ttu-id="306b2-168">Pour spécifier que [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] envoie l’accusé de réception de façon synchrone, sélectionnez **port de réception de l’accusé de réception itinéraire un pipeline d’envoi de requête-réponse** dans les **paramètres d’hôte Local** page ( **Paramètres du récepteur** section) sous **paramètres de l’échange** dans l’onglet d’accord bidirectionnel (pour les accords X12 et EDIFACT).</span><span class="sxs-lookup"><span data-stu-id="306b2-168">To specify that [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sends the acknowledgment synchronously, select **Route ACK to send pipeline on request-response receive port** in the **Local Host Settings** page (**Receiver’s Settings** section) under **Interchange Settings** in the bi-directional agreement tab (for both X12 and EDIFACT agreements).</span></span> <span data-ttu-id="306b2-169">Si vous supprimez cette propriété, le pipeline d'envoi du port de réception bidirectionnel doit être configuré pour renvoyer un échange EDI.</span><span class="sxs-lookup"><span data-stu-id="306b2-169">If you clear this property, the send pipeline of the two-way receive port must be set up to return an EDI interchange.</span></span>  
  
 <span data-ttu-id="306b2-170">Si un scénario utilise un port de réception requête-réponse et qu'un accusé de réception technique et un accusé de réception fonctionnel sont activés, l'accusé de réception technique est renvoyé de manière synchrone et l'accusé de réception fonctionnel, de manière asynchrone.</span><span class="sxs-lookup"><span data-stu-id="306b2-170">If a scenario uses a request-response receive port, and both a technical acknowledgment and a functional acknowledgment are enabled, the technical acknowledgment will be sent back synchronously, and the functional acknowledgment will be sent back asynchronously.</span></span>  
  
 <span data-ttu-id="306b2-171">Lors de la réception d'un message EDIINT/AS2 via HTTP/HTTPS, si un MDN est envoyé en réponse à une charge EDI encapsulée dans un MIME (sur le même socket), alors un accusé de réception EDI n'est pas envoyé de manière synchrone.</span><span class="sxs-lookup"><span data-stu-id="306b2-171">When receiving an EDIINT/AS2-encoded message over HTTP/HTTPS, if an MDN is sent out in response to a MIME wrapped EDI payload (on the same socket), then an EDI acknowledgment will not be sent out synchronously.</span></span> <span data-ttu-id="306b2-172">Si, dans ce cas le **port de réception de l’accusé de réception itinéraire un pipeline d’envoi de requête-réponse** propriété est activée, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ignore la propriété.</span><span class="sxs-lookup"><span data-stu-id="306b2-172">If in this case the **Route ACK to send pipeline on request-response receive port** property is checked, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will ignore the property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="306b2-173">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="306b2-173">See Also</span></span>  
 <span data-ttu-id="306b2-174">[Structure d’accusé de réception EDI](../core/edi-acknowledgment-structure.md) </span><span class="sxs-lookup"><span data-stu-id="306b2-174">[EDI Acknowledgment Structure](../core/edi-acknowledgment-structure.md) </span></span>  
 <span data-ttu-id="306b2-175">[Service EDI et des schémas de contrôle](../core/edi-service-and-control-schemas.md) </span><span class="sxs-lookup"><span data-stu-id="306b2-175">[EDI Service and Control Schemas](../core/edi-service-and-control-schemas.md) </span></span>  
 <span data-ttu-id="306b2-176">[X12 accusé de réception TA1](../core/x12-ta1-acknowledgment.md) </span><span class="sxs-lookup"><span data-stu-id="306b2-176">[X12 TA1 Acknowledgment](../core/x12-ta1-acknowledgment.md) </span></span>  
 <span data-ttu-id="306b2-177">[X12 accusé de réception 997](../core/x12-997-acknowledgment.md) </span><span class="sxs-lookup"><span data-stu-id="306b2-177">[X12 997 Acknowledgment](../core/x12-997-acknowledgment.md) </span></span>  
 <span data-ttu-id="306b2-178">[Accusé de réception EDIFACT CONTRL](../core/edifact-contrl-acknowledgment.md) </span><span class="sxs-lookup"><span data-stu-id="306b2-178">[EDIFACT CONTRL Acknowledgment](../core/edifact-contrl-acknowledgment.md) </span></span>  
 <span data-ttu-id="306b2-179">[Message CONTRL EDIFACT comme accusé de réception technique](../core/edifact-contrl-message-as-technical-acknowledgment.md) </span><span class="sxs-lookup"><span data-stu-id="306b2-179">[EDIFACT CONTRL Message as Technical Acknowledgment](../core/edifact-contrl-message-as-technical-acknowledgment.md) </span></span>  
 [<span data-ttu-id="306b2-180">Message CONTRL EDIFACT comme accusé de réception fonctionnel</span><span class="sxs-lookup"><span data-stu-id="306b2-180">EDIFACT CONTRL Message as Functional Acknowledgment</span></span>](../core/edifact-contrl-message-as-functional-acknowledgment.md)