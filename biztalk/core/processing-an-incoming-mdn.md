---
title: "Traitement d’un MDN entrant | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fd78e84c-4989-47e4-b95b-80582084ddec
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e599e9ebbc7a05a466cc047d891699222c2dabac
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="processing-an-incoming-mdn"></a><span data-ttu-id="103a1-102">Traitement d'un MDN entrant</span><span class="sxs-lookup"><span data-stu-id="103a1-102">Processing an Incoming MDN</span></span>
<span data-ttu-id="103a1-103">AS2 pipelines de réception (AS2EDIReceive et AS2Receive) traitent un MDN entrant en fonction des propriétés de l’accord pour le tiers comme récepteur des messages AS2.</span><span class="sxs-lookup"><span data-stu-id="103a1-103">The AS2 receive pipelines (AS2EDIReceive and AS2Receive) process an incoming MDN based upon the agreement properties for the party as an AS2 message receiver.</span></span> [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="103a1-104">met automatiquement en corrélation le MDN au message AS2 sortant.</span><span class="sxs-lookup"><span data-stu-id="103a1-104"> automatically correlates the MDN to the outgoing AS2 message.</span></span>  
  
 <span data-ttu-id="103a1-105">Les étapes effectuées par chaque pipeline sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="103a1-105">The steps each pipeline performs are as follows:</span></span>  
  
-   <span data-ttu-id="103a1-106">Détermine le tiers expéditeur en faisant correspondre AS2-à partir de la valeur de l’en-tête AS2 du message avec la valeur pour AS2-à partir de la liste dans le **identificateurs** page de l’onglet d’accord AS2 unidirectionnel de la **Propriétésdel’accord** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="103a1-106">Determines the sending party by matching the AS2-From value in the AS2 header of the message with the value for AS2-From list in the **Identifiers** page of the one-way AS2 agreement tab of the **Agreement Properties** dialog box.</span></span> <span data-ttu-id="103a1-107">Si aucune correspondance n'est trouvée, le pipeline abandonne le traitement et lève une exception.</span><span class="sxs-lookup"><span data-stu-id="103a1-107">If a match is not found, the pipeline aborts processing and raises an exception.</span></span>  
  
-   <span data-ttu-id="103a1-108">Promeut les propriétés AS2 suivantes vers le contexte :</span><span class="sxs-lookup"><span data-stu-id="103a1-108">Promotes the following AS2 properties to the context:</span></span>  
  
    -   <span data-ttu-id="103a1-109">IsAS2FailedMessage</span><span class="sxs-lookup"><span data-stu-id="103a1-109">IsAS2FailedMessage</span></span>  
  
    -   <span data-ttu-id="103a1-110">DispositionType</span><span class="sxs-lookup"><span data-stu-id="103a1-110">DispositionType</span></span>  
  
    -   <span data-ttu-id="103a1-111">GenerateAsynchronous200OKOnly</span><span class="sxs-lookup"><span data-stu-id="103a1-111">GenerateAsynchronous200OKOnly</span></span>  
  
    -   <span data-ttu-id="103a1-112">IsAS2MdnResponseMessage</span><span class="sxs-lookup"><span data-stu-id="103a1-112">IsAS2MdnResponseMessage</span></span>  
  
    -   <span data-ttu-id="103a1-113">IsAS2MessageSigned</span><span class="sxs-lookup"><span data-stu-id="103a1-113">IsAS2MessageSigned</span></span>  
  
    -   <span data-ttu-id="103a1-114">OriginalMessageId</span><span class="sxs-lookup"><span data-stu-id="103a1-114">OriginalMessageId</span></span>  
  
    -   <span data-ttu-id="103a1-115">ReceivedContentMic</span><span class="sxs-lookup"><span data-stu-id="103a1-115">ReceivedContentMic</span></span>  
  
    -   <span data-ttu-id="103a1-116">DispositionMode</span><span class="sxs-lookup"><span data-stu-id="103a1-116">DispositionMode</span></span>  
  
    -   <span data-ttu-id="103a1-117">MessageId</span><span class="sxs-lookup"><span data-stu-id="103a1-117">MessageId</span></span>  
  
-   <span data-ttu-id="103a1-118">Définit la propriété InboundHttpHeaders sur tous les en-têtes HTTP du message et la promeut vers le contexte du message.</span><span class="sxs-lookup"><span data-stu-id="103a1-118">Sets the InboundHttpHeaders property to all the HTTP headers of the message, and promotes it to the context of the message.</span></span>  
  
-   <span data-ttu-id="103a1-119">Crée une copie du MDN (au format câble) et la stocke dans la base de données de non-répudiation (table EdiMessageContent de la base de données BizTalkDTADb), si celle-ci est activée dans les propriétés de l'accord AS2 unidirectionnel.</span><span class="sxs-lookup"><span data-stu-id="103a1-119">Makes a copy of the MDN (in wire format), and stores the copy in the non-repudiation database (the EdiMessageContent table of the BizTalkDTADb database), if enabled in the one-way AS2 agreement properties.</span></span>  
  
-   <span data-ttu-id="103a1-120">Exécute un traitement MIME, notamment la vérification de la signature du MDN le cas échéant.</span><span class="sxs-lookup"><span data-stu-id="103a1-120">Performs MIME processing, including verifying the signature if the MDN was signed.</span></span>  
  
-   <span data-ttu-id="103a1-121">Compare la vérification de l'intégrité du message du MDN avec celle du magasin de données calculée par le pipeline AS2Send lorsque celui-ci a envoyé le message d'origine, le cas échéant.</span><span class="sxs-lookup"><span data-stu-id="103a1-121">Compares the MIC (Message Integrity Check) in the MDN with the MIC in the data store that was computed by the AS2Send pipeline when it sent out the original message (if applicable).</span></span> <span data-ttu-id="103a1-122">Pour plus d’informations, consultez [Messages MDN](../core/mdn-messages.md).</span><span class="sxs-lookup"><span data-stu-id="103a1-122">For more information, see [MDN Messages](../core/mdn-messages.md).</span></span>  
  
-   <span data-ttu-id="103a1-123">Crée des entrées de corrélation dans la base de données de non-répudiation.</span><span class="sxs-lookup"><span data-stu-id="103a1-123">Makes correlation entries in the non-repudiation database.</span></span>  
  
-   <span data-ttu-id="103a1-124">Supprime le MDN, sauf si le **traiter le MDN entrant dans MessageBox pour les options de routage/livraison** propriété est définie dans le **paramètres MDN de l’expéditeur** page de l’onglet d’accord AS2 unidirectionnel de la  **Propriétés de l’accord** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="103a1-124">Deletes the MDN, unless the **Process inbound MDN into MessageBox for routing/delivery options** property is set in the **Sender MDN Settings** page of the one-way AS2 agreement tab of the **Agreement Properties** dialog box.</span></span>  
  
-   <span data-ttu-id="103a1-125">Si le **traiter le MDN entrant dans MessageBox pour les options de routage/livraison** propriété est définie dans le **paramètres MDN de l’expéditeur** page de l’onglet d’accord AS2 unidirectionnel de la **propriétés de l’accord**  boîte de dialogue, le pipeline de réception achemine le MDN au format câble via le décodeur AS2 en tant que message de transfert et le dépose dans la MessageBox.</span><span class="sxs-lookup"><span data-stu-id="103a1-125">If the **Process inbound MDN into MessageBox for routing/delivery options** property is set in the **Sender MDN Settings** page of the one-way AS2 agreement tab of the **Agreement Properties** dialog box, the receive pipeline routes the MDN in wire format through the AS2 Decoder as a passthrough message and drops it into the MessageBox.</span></span> <span data-ttu-id="103a1-126">Le MDN au format câble contient tous les en-têtes HTTP.</span><span class="sxs-lookup"><span data-stu-id="103a1-126">The MDN in wire format contains all HTTP headers.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="103a1-127">Vous pouvez configurer un port d'envoi pour créer un abonnement à un MDN reçu déposé dans la base de données MessageBox.</span><span class="sxs-lookup"><span data-stu-id="103a1-127">You can set up a send port to subscribe to a received MDN that has been dropped into the MessageBox.</span></span> <span data-ttu-id="103a1-128">Pour créer un abonnement au MDN reçu, définissez le filtre du port d'envoi sur `IsAS2MdnResponseMessage==True`.</span><span class="sxs-lookup"><span data-stu-id="103a1-128">To subscribe to the received MDN, set the send port filter to `IsAS2MdnResponseMessage==True`.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="103a1-129">Si vous utilisez le pipeline AS2EdiReceive pour traiter un MDN reçu, vous ne pouvez pas acheminer le MDN dans la MessageBox en définissant le **traiter le MDN entrant dans MessageBox pour les options de routage/livraison** propriété dans le **expéditeur MDN Paramètres** page de l’onglet d’accord AS2 unidirectionnel de la **propriétés de l’accord** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="103a1-129">If you use the AS2EdiReceive pipeline to process a received MDN, you cannot route the MDN into the MessageBox by setting the **Process inbound MDN into MessageBox for routing/delivery options** property in the **Sender MDN Settings** page of the one-way AS2 agreement tab of the **Agreement Properties** dialog box.</span></span> <span data-ttu-id="103a1-130">Si vous essayez de le faire, une erreur EDI est générée car le MDN est transmis au décodeur EDI, qui ne peut pas traiter un MDN.</span><span class="sxs-lookup"><span data-stu-id="103a1-130">Trying to do so will result in an EDI error because the MDN will be passed to the EDI Decoder, which cannot process an MDN.</span></span> <span data-ttu-id="103a1-131">Si le MDN n'est pas envoyé à la base de données MessageBox, le décodeur AS2Decoder utilise le MDN, qui n'est par conséquent pas transmis au décodeur EDI.</span><span class="sxs-lookup"><span data-stu-id="103a1-131">If the MDN is not sent to the MessageBox, the AS2Decoder will consume the MDN, so it will not be passed to the EDI Decoder.</span></span>  
  
## <a name="message-integrity-check"></a><span data-ttu-id="103a1-132">Vérification de l'intégrité du message</span><span class="sxs-lookup"><span data-stu-id="103a1-132">Message Integrity Check</span></span>  
 <span data-ttu-id="103a1-133">La vérification de l'intégrité du message permet de vérifier qu'un MDN est mis en corrélation avec le message envoyé d'origine.</span><span class="sxs-lookup"><span data-stu-id="103a1-133">The Message Integrity Check (MIC) is used to verify that an MDN correlates to the original sent message.</span></span> <span data-ttu-id="103a1-134">Le pipeline d'envoi AS2Send calcule la vérification de l'intégrité du message à partir de la charge du message lorsqu'il génère le message AS2 d'origine et stocke la vérification de l'intégrité du message dans le magasin de données.</span><span class="sxs-lookup"><span data-stu-id="103a1-134">The AS2Send send pipeline calculates the MIC from the message payload when it generates the original AS2 message, and stores the MIC in the data store.</span></span> <span data-ttu-id="103a1-135">Lorsqu'un MDN est obligatoire, le destinataire du message d'origine génère une vérification de l'intégrité du message et l'ajoute au MDN.</span><span class="sxs-lookup"><span data-stu-id="103a1-135">When an MDN is required, the recipient of the original message generates an MIC and adds it to the MDN.</span></span> <span data-ttu-id="103a1-136">Lorsque le pipeline de réception AS2MdnReceive reçoit le MDN, si un MDN signé a été demandé, il compare la vérification de l'intégrité du message du MDN avec celle du magasin de données.</span><span class="sxs-lookup"><span data-stu-id="103a1-136">When the AS2MdnReceive receive pipeline receives the MDN, if a signed MDN was requested, it compares the MIC in the MDN with the MIC in the data store.</span></span>  
  
 <span data-ttu-id="103a1-137">Une incohérence entre la vérification de l'intégrité du message du MDN et celle du magasin de données indique qu'une erreur s'est produite au cours de la transmission ou de la réception du message par le tiers de réception.</span><span class="sxs-lookup"><span data-stu-id="103a1-137">A mismatch between the MIC in the MDN and the MIC in the data store indicates that there was an error during transmission or receipt of the message by the receiving party.</span></span> <span data-ttu-id="103a1-138">Les valeurs signalées dans ce type d'échec sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="103a1-138">The values reported in such a failure are the following:</span></span>  
  
-   <span data-ttu-id="103a1-139">AS2DispositionType : échec</span><span class="sxs-lookup"><span data-stu-id="103a1-139">AS2DispositionType: Failed</span></span>  
  
-   <span data-ttu-id="103a1-140">AS2DispositionModifierExtensionType : erreur</span><span class="sxs-lookup"><span data-stu-id="103a1-140">AS2DispositionModifierExtensionType: Error</span></span>  
  
-   <span data-ttu-id="103a1-141">AS2DispositionModifierExtensionDescription : échec de la vérification de l'intégrité</span><span class="sxs-lookup"><span data-stu-id="103a1-141">AS2DispositionModifierExtensionDescription: Integrity Check Failed</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="103a1-142">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="103a1-142">See Also</span></span>  
 <span data-ttu-id="103a1-143">[Réception des Messages AS2 par BizTalk Server](../core/how-biztalk-server-receives-as2-messages.md) </span><span class="sxs-lookup"><span data-stu-id="103a1-143">[How BizTalk Server Receives AS2 Messages](../core/how-biztalk-server-receives-as2-messages.md) </span></span>  
 [<span data-ttu-id="103a1-144">Messages MDN</span><span class="sxs-lookup"><span data-stu-id="103a1-144">MDN Messages</span></span>](../core/mdn-messages.md)