---
title: "Création de Ports d’envoi pour envoyer aux gestionnaires personnalisés FRR | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- creating, send ports
- send ports, creating
- FRR, creating send ports
ms.assetid: 036f1f97-17a2-4e02-a85a-a52739a48528
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4a6326ae6e82e819d3cdf76ecc4d81e2a377ea65
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="creating-the-frr-send-ports-for-sending-to-the-custom-handlers"></a><span data-ttu-id="b1322-102">Création de Ports d’envoi pour envoyer aux gestionnaires personnalisés FRR</span><span class="sxs-lookup"><span data-stu-id="b1322-102">Creating the FRR Send Ports for Sending to the Custom Handlers</span></span>
<span data-ttu-id="b1322-103">Pour effectuer le rapprochement de réponse de FIN, vous devez créer une série de ports d’envoi, chacun d’eux envoie un message (message d’origine ou réponse) à partir de [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] aux gestionnaires personnalisés qui traitent les messages corrélés.</span><span class="sxs-lookup"><span data-stu-id="b1322-103">To perform FIN Response Reconciliation, you need to create a series of send ports, each of which sends a message (original message or response) from [!INCLUDE[btaA4SWIFT2.3abbrevnonumber](../../includes/btaa4swift2-3abbrevnonumber-md.md)] to the custom handlers that process the correlated messages.</span></span>  
  
 <span data-ttu-id="b1322-104">**Résumé**</span><span class="sxs-lookup"><span data-stu-id="b1322-104">**Summary**</span></span>  
  
 <span data-ttu-id="b1322-105">Créer une série de ports d’envoi avec les propriétés suivantes et les composants, chacun d’eux différencié par la valeur de BizTalk Server. Opération dans le filtre :</span><span class="sxs-lookup"><span data-stu-id="b1322-105">Create a series of send ports with the following properties and components, each one distinguished by the value of BTS.Operation in the filter:</span></span>  
  
|<span data-ttu-id="b1322-106">Propriété/composant</span><span class="sxs-lookup"><span data-stu-id="b1322-106">Property/Component</span></span>|<span data-ttu-id="b1322-107">Paramètre</span><span class="sxs-lookup"><span data-stu-id="b1322-107">Setting</span></span>|  
|-------------------------|-------------|  
|<span data-ttu-id="b1322-108">Port d'envoi</span><span class="sxs-lookup"><span data-stu-id="b1322-108">Send port</span></span>|<span data-ttu-id="b1322-109">Port statique unidirectionnel</span><span class="sxs-lookup"><span data-stu-id="b1322-109">Static one-way port</span></span>|  
|<span data-ttu-id="b1322-110">Type de transport </span><span class="sxs-lookup"><span data-stu-id="b1322-110">Transport type</span></span>|<span data-ttu-id="b1322-111">FILE</span><span class="sxs-lookup"><span data-stu-id="b1322-111">FILE</span></span>|  
|<span data-ttu-id="b1322-112">Dossier de destination (adresse URI)</span><span class="sxs-lookup"><span data-stu-id="b1322-112">Destination folder (Address URI)</span></span>|<span data-ttu-id="b1322-113">Le dossier que vous souhaitez envoyer le message</span><span class="sxs-lookup"><span data-stu-id="b1322-113">The folder that you want to send the message to</span></span>|  
|<span data-ttu-id="b1322-114">Nom de fichier (adresse URI)</span><span class="sxs-lookup"><span data-stu-id="b1322-114">File name (Address URI)</span></span>|<span data-ttu-id="b1322-115">%MessageID%.txt</span><span class="sxs-lookup"><span data-stu-id="b1322-115">%MessageID%.txt</span></span>|  
|<span data-ttu-id="b1322-116">Pipeline d’envoi</span><span class="sxs-lookup"><span data-stu-id="b1322-116">Send pipeline</span></span>|[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]<span data-ttu-id="b1322-117">. BizTalk.DefaultPipelines.</span><span class="sxs-lookup"><span data-stu-id="b1322-117">.BizTalk.DefaultPipelines.</span></span> <span data-ttu-id="b1322-118">PassThruTransmit</span><span class="sxs-lookup"><span data-stu-id="b1322-118">PassThruTransmit</span></span>|  
|<span data-ttu-id="b1322-119">Filtres</span><span class="sxs-lookup"><span data-stu-id="b1322-119">Filters</span></span>|<span data-ttu-id="b1322-120">Comme indiqué dans les tableaux ci-dessous</span><span class="sxs-lookup"><span data-stu-id="b1322-120">As shown in the tables below</span></span>|  
  
 <span data-ttu-id="b1322-121">Les ports d’envoi pour les différents messages sont distinguent par la valeur de BizTalk Server. Opération dans les filtre du port d’envoi.</span><span class="sxs-lookup"><span data-stu-id="b1322-121">The send ports for the different messages are distinguished by the value of BTS.Operation in the send port's filter.</span></span>  
  
### <a name="to-add-frr-send-ports-for-sending-to-the-custom-handlers"></a><span data-ttu-id="b1322-122">Pour ajouter des ports d’envoi FRR pour l’envoi aux gestionnaires personnalisés</span><span class="sxs-lookup"><span data-stu-id="b1322-122">To add FRR send ports for sending to the custom handlers</span></span>  
  
1.  <span data-ttu-id="b1322-123">Dans la Console Administration de BizTalk Server, cliquez sur **Ports d’envoi**, pointez sur **nouveau**, puis cliquez sur **Static-waySend un Port**.</span><span class="sxs-lookup"><span data-stu-id="b1322-123">In the BizTalk Server Administration Console, right-click **Send Ports**, point to **New**, and then click **Static One-waySend Port**.</span></span>  
  
2.  <span data-ttu-id="b1322-124">Dans la boîte de dialogue Propriétés de Port d’envoi dans le **nom** , tapez un nom pour le port d’envoi, par exemple FRRCustomHandlersSendPort.</span><span class="sxs-lookup"><span data-stu-id="b1322-124">In the Send Port Properties dialog box, in the **Name** box, type a name for the send port, such as FRRCustomHandlersSendPort.</span></span>  
  
3.  <span data-ttu-id="b1322-125">Pour **Type**, sélectionnez **fichier**.</span><span class="sxs-lookup"><span data-stu-id="b1322-125">For **Type**, select **FILE**.</span></span>  
  
4.  <span data-ttu-id="b1322-126">Cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="b1322-126">Click **Configure**.</span></span>  
  
5.  <span data-ttu-id="b1322-127">Dans la boîte de dialogue Propriétés du Transport FILE, cliquez sur **Parcourir**.</span><span class="sxs-lookup"><span data-stu-id="b1322-127">In the FILE Transport Properties dialog box, click **Browse**.</span></span>  
  
6.  <span data-ttu-id="b1322-128">Dans la boîte de dialogue Rechercher un dossier, déplacer vers le dossier que vous souhaitez envoyer des messages à partir de.</span><span class="sxs-lookup"><span data-stu-id="b1322-128">In the Browse For Folder dialog box, move to the folder that you want to send messages from.</span></span> <span data-ttu-id="b1322-129">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="b1322-129">Click **OK**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b1322-130">Si ce dossier n’existe pas, vous pouvez créer à l’aide de la **créer un nouveau dossier** commande.</span><span class="sxs-lookup"><span data-stu-id="b1322-130">If this folder does not exist, you can create it using the **Make New Folder** command.</span></span>  
  
7.  <span data-ttu-id="b1322-131">Dans le **nom de fichier** , tapez **%MessageID%.txt**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="b1322-131">In the **File name** box, type **%MessageID%.txt**, and then click **OK**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b1322-132">Vous pouvez créer un dossier différent pour chaque type de message.</span><span class="sxs-lookup"><span data-stu-id="b1322-132">You can create a different folder for each type of message.</span></span>  
  
8.  <span data-ttu-id="b1322-133">Dans la boîte de dialogue Propriétés de Port d’envoi pour le Gestionnaire d’envoi, vérifiez que **BizTalkServerApplication** est sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="b1322-133">In the Send Port Properties dialog box, for Send handler, verify that **BizTalkServerApplication** is selected.</span></span>  
  
9. <span data-ttu-id="b1322-134">Pour **Pipeline d’envoi**, sélectionnez **PassThruTransmit**.</span><span class="sxs-lookup"><span data-stu-id="b1322-134">For **Send Pipeline**, select **PassThruTransmit**.</span></span>  
  
10. <span data-ttu-id="b1322-135">Cliquez sur **filtres** dans le volet gauche, puis procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="b1322-135">Click **Filters** in the left pane, and then do the following:</span></span>  
  
    |<span data-ttu-id="b1322-136">Utiliser</span><span class="sxs-lookup"><span data-stu-id="b1322-136">Use this</span></span>|<span data-ttu-id="b1322-137">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="b1322-137">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="b1322-138">**Propriété**</span><span class="sxs-lookup"><span data-stu-id="b1322-138">**Property**</span></span>|<span data-ttu-id="b1322-139">Sélectionnez **Microsoft.Solutions.A4SWIFT.Property.A4SWIFT_SendingServiceType**.</span><span class="sxs-lookup"><span data-stu-id="b1322-139">Select **Microsoft.Solutions.A4SWIFT.Property.A4SWIFT_SendingServiceType**.</span></span>|  
    |<span data-ttu-id="b1322-140">**Opérateur**</span><span class="sxs-lookup"><span data-stu-id="b1322-140">**Operator**</span></span>|<span data-ttu-id="b1322-141">Sélectionnez  **==** .</span><span class="sxs-lookup"><span data-stu-id="b1322-141">Select **==**.</span></span>|  
    |<span data-ttu-id="b1322-142">**Valeur**</span><span class="sxs-lookup"><span data-stu-id="b1322-142">**Value**</span></span>|<span data-ttu-id="b1322-143">Type **A4SWIFT_FrrService**.</span><span class="sxs-lookup"><span data-stu-id="b1322-143">Type **A4SWIFT_FrrService**.</span></span>|  
    |<span data-ttu-id="b1322-144">**Grouper**</span><span class="sxs-lookup"><span data-stu-id="b1322-144">**Group**</span></span>|<span data-ttu-id="b1322-145">**And**</span><span class="sxs-lookup"><span data-stu-id="b1322-145">**And**</span></span>|  
    |<span data-ttu-id="b1322-146">**Propriété**</span><span class="sxs-lookup"><span data-stu-id="b1322-146">**Property**</span></span>|<span data-ttu-id="b1322-147">Sélectionnez **BTS. Opération**.</span><span class="sxs-lookup"><span data-stu-id="b1322-147">Select **BTS.Operation**.</span></span>|  
    |<span data-ttu-id="b1322-148">**Opérateur**</span><span class="sxs-lookup"><span data-stu-id="b1322-148">**Operator**</span></span>|<span data-ttu-id="b1322-149">Sélectionnez  **==** .</span><span class="sxs-lookup"><span data-stu-id="b1322-149">Select **==**.</span></span>|  
    |<span data-ttu-id="b1322-150">**Valeur**</span><span class="sxs-lookup"><span data-stu-id="b1322-150">**Value**</span></span>|<span data-ttu-id="b1322-151">Tapez le BTS. Valeurs d’opération dans le tableau ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="b1322-151">Type one of the BTS.Operation values from the table below.</span></span>|  
  
     <span data-ttu-id="b1322-152">Pour BizTalk Server. Opération, entrez une des valeurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="b1322-152">For BTS.Operation, enter one of the following values:</span></span>  
  
    |<span data-ttu-id="b1322-153">type de message</span><span class="sxs-lookup"><span data-stu-id="b1322-153">Message type</span></span>|<span data-ttu-id="b1322-154">BIZTALK SERVER. Valeur de l’opération</span><span class="sxs-lookup"><span data-stu-id="b1322-154">BTS.Operation value</span></span>|  
    |------------------|-------------------------|  
    |<span data-ttu-id="b1322-155">Tous les types de messages SWIFT FIN catégorie 0 à 9</span><span class="sxs-lookup"><span data-stu-id="b1322-155">All Category 0 to 9 SWIFT FIN message types</span></span>|<span data-ttu-id="b1322-156">**A4SWIFT_FrrSendMTMsg**</span><span class="sxs-lookup"><span data-stu-id="b1322-156">**A4SWIFT_FrrSendMTMsg**</span></span>|  
    |<span data-ttu-id="b1322-157">MQ Series panoramique/NAN (au niveau du transport MQSeries l’accusé de réception/NON-RÉCEPTION)</span><span class="sxs-lookup"><span data-stu-id="b1322-157">MQ Series PAN/NAN (MQ Series transport-level ACK/NAK)</span></span>|<span data-ttu-id="b1322-158">**A4SWIFT_FrrSendTransport**</span><span class="sxs-lookup"><span data-stu-id="b1322-158">**A4SWIFT_FrrSendTransport**</span></span>|  
    |<span data-ttu-id="b1322-159">MT010 (avertissement de non-remise)</span><span class="sxs-lookup"><span data-stu-id="b1322-159">MT010 (Non-Delivery Warning)</span></span>|<span data-ttu-id="b1322-160">**A4SWIFT_FrrSend010NDW**</span><span class="sxs-lookup"><span data-stu-id="b1322-160">**A4SWIFT_FrrSend010NDW**</span></span>|  
    |<span data-ttu-id="b1322-161">MT011 (accusé de réception)</span><span class="sxs-lookup"><span data-stu-id="b1322-161">MT011 (Delivery Notification)</span></span>|<span data-ttu-id="b1322-162">**A4SWIFT_FrrSend011Delivered**</span><span class="sxs-lookup"><span data-stu-id="b1322-162">**A4SWIFT_FrrSend011Delivered**</span></span>|  
    |<span data-ttu-id="b1322-163">MT012 (Notification de l’expéditeur)</span><span class="sxs-lookup"><span data-stu-id="b1322-163">MT012 (Sender Notification)</span></span>|<span data-ttu-id="b1322-164">**A4SWIFT_FrrSend012SenderACK**</span><span class="sxs-lookup"><span data-stu-id="b1322-164">**A4SWIFT_FrrSend012SenderACK**</span></span>|  
    |<span data-ttu-id="b1322-165">MT015 (DNK ou NAK retardé)</span><span class="sxs-lookup"><span data-stu-id="b1322-165">MT015 (DNK, or Delayed NAK)</span></span>|<span data-ttu-id="b1322-166">**A4SWIFT_FrrSend015DNK**</span><span class="sxs-lookup"><span data-stu-id="b1322-166">**A4SWIFT_FrrSend015DNK**</span></span>|  
    |<span data-ttu-id="b1322-167">MT019 (abandon de Notification)</span><span class="sxs-lookup"><span data-stu-id="b1322-167">MT019 (Abort Notification)</span></span>|<span data-ttu-id="b1322-168">**A4SWIFT_FrrSend019Abort**</span><span class="sxs-lookup"><span data-stu-id="b1322-168">**A4SWIFT_FrrSend019Abort**</span></span>|  
    |<span data-ttu-id="b1322-169">MTS21_FIN_ACKNAK (accusé de réception d’un message FIN envoyé par un LT (accusé de réception)</span><span class="sxs-lookup"><span data-stu-id="b1322-169">MTS21_FIN_ACKNAK (Acknowledgment of a FIN message sent by an LT (ACK)</span></span>|<span data-ttu-id="b1322-170">**A4SWIFT_FrrSendS21ACK**</span><span class="sxs-lookup"><span data-stu-id="b1322-170">**A4SWIFT_FrrSendS21ACK**</span></span>|  
    |<span data-ttu-id="b1322-171">MTS21_FIN_ACKNAK (valeur négative d’accusé de réception d’un message FIN envoyé par un LT (NAK)</span><span class="sxs-lookup"><span data-stu-id="b1322-171">MTS21_FIN_ACKNAK (Negative acknowledgment of a FIN message sent by an LT (NAK)</span></span>|<span data-ttu-id="b1322-172">**A4SWIFT_FrrSendS21NAK**</span><span class="sxs-lookup"><span data-stu-id="b1322-172">**A4SWIFT_FrrSendS21NAK**</span></span>|  
  
11. <span data-ttu-id="b1322-173">Pour les messages de catégorie de 0 à 9 SWIFT FIN qui ne sont pas envoyés avec succès, procédez comme suit le **filtres** volet :</span><span class="sxs-lookup"><span data-stu-id="b1322-173">For Category 0 to 9 SWIFT FIN messages that are not successfully sent, do the following in the **Filters** pane:</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b1322-174">Le **A4SWIFT_FRRFailedReason** propriétés dans le filtre suivant doivent être regroupées.</span><span class="sxs-lookup"><span data-stu-id="b1322-174">The **A4SWIFT_FRRFailedReason** properties in the following filter should be grouped.</span></span>  
  
    |<span data-ttu-id="b1322-175">Utiliser</span><span class="sxs-lookup"><span data-stu-id="b1322-175">Use this</span></span>|<span data-ttu-id="b1322-176">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="b1322-176">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="b1322-177">**Propriété**</span><span class="sxs-lookup"><span data-stu-id="b1322-177">**Property**</span></span>|<span data-ttu-id="b1322-178">Sélectionnez **Microsoft.Solutions.A4SWIFT.Property.A4SWIFT_SendingServiceType**.</span><span class="sxs-lookup"><span data-stu-id="b1322-178">Select **Microsoft.Solutions.A4SWIFT.Property.A4SWIFT_SendingServiceType**.</span></span>|  
    |<span data-ttu-id="b1322-179">**Opérateur**</span><span class="sxs-lookup"><span data-stu-id="b1322-179">**Operator**</span></span>|<span data-ttu-id="b1322-180">Sélectionnez  **==** .</span><span class="sxs-lookup"><span data-stu-id="b1322-180">Select **==**.</span></span>|  
    |<span data-ttu-id="b1322-181">**Valeur**</span><span class="sxs-lookup"><span data-stu-id="b1322-181">**Value**</span></span>|<span data-ttu-id="b1322-182">Type **A4SWIFT_FrrService**.</span><span class="sxs-lookup"><span data-stu-id="b1322-182">Type **A4SWIFT_FrrService**.</span></span>|  
    |<span data-ttu-id="b1322-183">**Grouper**</span><span class="sxs-lookup"><span data-stu-id="b1322-183">**Group**</span></span>|<span data-ttu-id="b1322-184">**And**</span><span class="sxs-lookup"><span data-stu-id="b1322-184">**And**</span></span>|  
    |<span data-ttu-id="b1322-185">**Propriété**</span><span class="sxs-lookup"><span data-stu-id="b1322-185">**Property**</span></span>|<span data-ttu-id="b1322-186">Sélectionnez **Microsoft.Solutions.A4SWIFT.Property.A4SWIFT_FrrFailed**.</span><span class="sxs-lookup"><span data-stu-id="b1322-186">Select **Microsoft.Solutions.A4SWIFT.Property.A4SWIFT_FrrFailed**.</span></span>|  
    |<span data-ttu-id="b1322-187">**Opérateur**</span><span class="sxs-lookup"><span data-stu-id="b1322-187">**Operator**</span></span>|<span data-ttu-id="b1322-188">Sélectionnez  **==** .</span><span class="sxs-lookup"><span data-stu-id="b1322-188">Select **==**.</span></span>|  
    |<span data-ttu-id="b1322-189">**Valeur**</span><span class="sxs-lookup"><span data-stu-id="b1322-189">**Value**</span></span>|<span data-ttu-id="b1322-190">Type **True**.</span><span class="sxs-lookup"><span data-stu-id="b1322-190">Type **True**.</span></span>|  
    |<span data-ttu-id="b1322-191">**Grouper**</span><span class="sxs-lookup"><span data-stu-id="b1322-191">**Group**</span></span>|<span data-ttu-id="b1322-192">**And**</span><span class="sxs-lookup"><span data-stu-id="b1322-192">**And**</span></span>|  
    |<span data-ttu-id="b1322-193">**Propriété**</span><span class="sxs-lookup"><span data-stu-id="b1322-193">**Property**</span></span>|<span data-ttu-id="b1322-194">Sélectionnez **BTS. Opération**.</span><span class="sxs-lookup"><span data-stu-id="b1322-194">Select **BTS.Operation**.</span></span>|  
    |<span data-ttu-id="b1322-195">**Opérateur**</span><span class="sxs-lookup"><span data-stu-id="b1322-195">**Operator**</span></span>|<span data-ttu-id="b1322-196">Sélectionnez  **==** .</span><span class="sxs-lookup"><span data-stu-id="b1322-196">Select **==**.</span></span>|  
    |<span data-ttu-id="b1322-197">**Valeur**</span><span class="sxs-lookup"><span data-stu-id="b1322-197">**Value**</span></span>|<span data-ttu-id="b1322-198">Type **A4SWIFT_FrrSendMTMsg**.</span><span class="sxs-lookup"><span data-stu-id="b1322-198">Type **A4SWIFT_FrrSendMTMsg**.</span></span>|  
    |<span data-ttu-id="b1322-199">**Grouper**</span><span class="sxs-lookup"><span data-stu-id="b1322-199">**Group**</span></span>|<span data-ttu-id="b1322-200">**And**</span><span class="sxs-lookup"><span data-stu-id="b1322-200">**And**</span></span>|  
    |<span data-ttu-id="b1322-201">**Propriété**</span><span class="sxs-lookup"><span data-stu-id="b1322-201">**Property**</span></span>|<span data-ttu-id="b1322-202">Sélectionnez **Microsoft.Solutions.A4SWIFT.Property.A4SWIFT_FRRFailedReason**.</span><span class="sxs-lookup"><span data-stu-id="b1322-202">Select **Microsoft.Solutions.A4SWIFT.Property.A4SWIFT_FRRFailedReason**.</span></span>|  
    |<span data-ttu-id="b1322-203">**Opérateur**</span><span class="sxs-lookup"><span data-stu-id="b1322-203">**Operator**</span></span>|<span data-ttu-id="b1322-204">Sélectionnez  **==** .</span><span class="sxs-lookup"><span data-stu-id="b1322-204">Select **==**.</span></span>|  
    |<span data-ttu-id="b1322-205">**Valeur**</span><span class="sxs-lookup"><span data-stu-id="b1322-205">**Value**</span></span>|<span data-ttu-id="b1322-206">Type  *\<NAKErrorCode\>*, tels que « Y01 ».</span><span class="sxs-lookup"><span data-stu-id="b1322-206">Type *\<NAKErrorCode\>*, such as "Y01".</span></span>|  
    |<span data-ttu-id="b1322-207">**Grouper**</span><span class="sxs-lookup"><span data-stu-id="b1322-207">**Group**</span></span>|<span data-ttu-id="b1322-208">**Or**</span><span class="sxs-lookup"><span data-stu-id="b1322-208">**Or**</span></span>|  
    |<span data-ttu-id="b1322-209">**Propriété**</span><span class="sxs-lookup"><span data-stu-id="b1322-209">**Property**</span></span>|<span data-ttu-id="b1322-210">Sélectionnez **Microsoft.Solutions.A4SWIFT.Property.A4SWIFT_FRRFailedReason**.</span><span class="sxs-lookup"><span data-stu-id="b1322-210">Select **Microsoft.Solutions.A4SWIFT.Property.A4SWIFT_FRRFailedReason**.</span></span>|  
    |<span data-ttu-id="b1322-211">**Opérateur**</span><span class="sxs-lookup"><span data-stu-id="b1322-211">**Operator**</span></span>|<span data-ttu-id="b1322-212">Sélectionnez  **==** .</span><span class="sxs-lookup"><span data-stu-id="b1322-212">Select **==**.</span></span>|  
    |<span data-ttu-id="b1322-213">**Valeur**</span><span class="sxs-lookup"><span data-stu-id="b1322-213">**Value**</span></span>|<span data-ttu-id="b1322-214">Type **TimedOut**.</span><span class="sxs-lookup"><span data-stu-id="b1322-214">Type **TimedOut**.</span></span>|  
    |<span data-ttu-id="b1322-215">**Grouper**</span><span class="sxs-lookup"><span data-stu-id="b1322-215">**Group**</span></span>|<span data-ttu-id="b1322-216">**Or**</span><span class="sxs-lookup"><span data-stu-id="b1322-216">**Or**</span></span>|  
    |<span data-ttu-id="b1322-217">**Propriété**</span><span class="sxs-lookup"><span data-stu-id="b1322-217">**Property**</span></span>|<span data-ttu-id="b1322-218">Sélectionnez **Microsoft.Solutions.A4SWIFT.Property.A4SWIFT_FRRFailedReason**.</span><span class="sxs-lookup"><span data-stu-id="b1322-218">Select **Microsoft.Solutions.A4SWIFT.Property.A4SWIFT_FRRFailedReason**.</span></span>|  
    |<span data-ttu-id="b1322-219">**Opérateur**</span><span class="sxs-lookup"><span data-stu-id="b1322-219">**Operator**</span></span>|<span data-ttu-id="b1322-220">Sélectionnez  **==** .</span><span class="sxs-lookup"><span data-stu-id="b1322-220">Select **==**.</span></span>|  
    |<span data-ttu-id="b1322-221">**Valeur**</span><span class="sxs-lookup"><span data-stu-id="b1322-221">**Value**</span></span>|<span data-ttu-id="b1322-222">Type **TransportError**.</span><span class="sxs-lookup"><span data-stu-id="b1322-222">Type **TransportError**.</span></span>|  
    |<span data-ttu-id="b1322-223">**Grouper**</span><span class="sxs-lookup"><span data-stu-id="b1322-223">**Group**</span></span>|<span data-ttu-id="b1322-224">**Or**</span><span class="sxs-lookup"><span data-stu-id="b1322-224">**Or**</span></span>|  
    |<span data-ttu-id="b1322-225">**Propriété**</span><span class="sxs-lookup"><span data-stu-id="b1322-225">**Property**</span></span>|<span data-ttu-id="b1322-226">Sélectionnez **Microsoft.Solutions.A4SWIFT.Property.A4SWIFT_FRRFailedReason**.</span><span class="sxs-lookup"><span data-stu-id="b1322-226">Select **Microsoft.Solutions.A4SWIFT.Property.A4SWIFT_FRRFailedReason**.</span></span>|  
    |<span data-ttu-id="b1322-227">**Opérateur**</span><span class="sxs-lookup"><span data-stu-id="b1322-227">**Operator**</span></span>|<span data-ttu-id="b1322-228">Sélectionnez  **==** .</span><span class="sxs-lookup"><span data-stu-id="b1322-228">Select **==**.</span></span>|  
    |<span data-ttu-id="b1322-229">**Valeur**</span><span class="sxs-lookup"><span data-stu-id="b1322-229">**Value**</span></span>|<span data-ttu-id="b1322-230">Type **DelayedNAK**.</span><span class="sxs-lookup"><span data-stu-id="b1322-230">Type **DelayedNAK**.</span></span>|  
    |<span data-ttu-id="b1322-231">**Grouper**</span><span class="sxs-lookup"><span data-stu-id="b1322-231">**Group**</span></span>|<span data-ttu-id="b1322-232">**Or**</span><span class="sxs-lookup"><span data-stu-id="b1322-232">**Or**</span></span>|  
    |<span data-ttu-id="b1322-233">**Propriété**</span><span class="sxs-lookup"><span data-stu-id="b1322-233">**Property**</span></span>|<span data-ttu-id="b1322-234">Sélectionnez **Microsoft.Solutions.A4SWIFT.Property.A4SWIFT_FRRFailedReason**.</span><span class="sxs-lookup"><span data-stu-id="b1322-234">Select **Microsoft.Solutions.A4SWIFT.Property.A4SWIFT_FRRFailedReason**.</span></span>|  
    |<span data-ttu-id="b1322-235">**Opérateur**</span><span class="sxs-lookup"><span data-stu-id="b1322-235">**Operator**</span></span>|<span data-ttu-id="b1322-236">Sélectionnez  **==** .</span><span class="sxs-lookup"><span data-stu-id="b1322-236">Select **==**.</span></span>|  
    |<span data-ttu-id="b1322-237">**Valeur**</span><span class="sxs-lookup"><span data-stu-id="b1322-237">**Value**</span></span>|<span data-ttu-id="b1322-238">Type **AbortMessage**.</span><span class="sxs-lookup"><span data-stu-id="b1322-238">Type **AbortMessage**.</span></span>|  
  
12. <span data-ttu-id="b1322-239">Cliquez sur **appliquer**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="b1322-239">Click **Apply**, and then click **OK**.</span></span>  
  
13. <span data-ttu-id="b1322-240">Cliquez sur le port d’envoi, puis cliquez sur **Démarrer**.</span><span class="sxs-lookup"><span data-stu-id="b1322-240">Right-click the send port, and then click **Start**.</span></span>  
  
14. <span data-ttu-id="b1322-241">Répétez les étapes 2 à 13 pour créer un port d’envoi pour chaque type de message requis.</span><span class="sxs-lookup"><span data-stu-id="b1322-241">Repeat steps 2 through 13 to create a send port for each message type required.</span></span>