---
title: "Configuration d’un Port d’envoi pour recevoir des accusés de réception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- send ports, acknowledgements
- creating, send ports
- acknowledgements, send ports
- send ports, creating
ms.assetid: bb683e72-36e2-4a8f-acc2-8b37ed23746f
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e81b33982273088e498e719fc074db5c454b0e59
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="setting-up-a-send-port-for-receiving-acks"></a><span data-ttu-id="4ef36-102">Configuration d’un Port d’envoi pour recevoir des accusés de réception</span><span class="sxs-lookup"><span data-stu-id="4ef36-102">Setting Up a Send Port for Receiving ACKs</span></span>
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]<span data-ttu-id="4ef36-103">BizTalk Accelerator pour HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) peut recevoir des accusés de réception (ACK) sur un port d’envoi unidirectionnel.</span><span class="sxs-lookup"><span data-stu-id="4ef36-103"> BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) can receive acknowledgments (ACK) on a one-way send port.</span></span> <span data-ttu-id="4ef36-104">Lorsque vous configurez un port d’envoi unidirectionnel pour recevoir les accusés de réception sur la même connexion, vous devez associer cet envoi port de réception du port unidirectionnel.</span><span class="sxs-lookup"><span data-stu-id="4ef36-104">When you set up a new one-way send port for receiving ACKs on the same connection, you must associate that send port with a one-way receive port.</span></span>  
  
 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="4ef36-105">le programme d’installation crée un unidirectionnel port de réception (appelé **TwoWayAckReceivePort**) et l’emplacement de réception (appelé **TwoWayAckReceiveLocation**).</span><span class="sxs-lookup"><span data-stu-id="4ef36-105"> setup creates a one-way receive port (called **TwoWayAckReceivePort**) and receive location (called **TwoWayAckReceiveLocation**).</span></span> <span data-ttu-id="4ef36-106">L’emplacement de réception utilise le type de transport de protocole de couche inférieure minimale (MLLP), a un URI de « 127.0.0.1:65535 » et utilise le **BTAHL72XReceivePipeline**.</span><span class="sxs-lookup"><span data-stu-id="4ef36-106">The receive location uses the Minimal Lower Layer Protocol (MLLP) transport type, has a URI of "127.0.0.1:65535", and uses the **BTAHL72XReceivePipeline**.</span></span> <span data-ttu-id="4ef36-107">Voici les paramètres requis pour la réception et le traitement d’un accusé de réception reçu un message envoyé par le [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] , l’adaptateur d’envoi en mode bidirectionnel.</span><span class="sxs-lookup"><span data-stu-id="4ef36-107">These are the settings required for receiving and processing an ACK received against a message sent out by the [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] send adapter, in two-way mode.</span></span> <span data-ttu-id="4ef36-108">Cet emplacement de réception ne doit pas être supprimé ou utilisée à d’autres fins.</span><span class="sxs-lookup"><span data-stu-id="4ef36-108">This receive location should not be deleted or used for any other purposes.</span></span> <span data-ttu-id="4ef36-109">Ne jamais envoyer de données à cet emplacement de réception.</span><span class="sxs-lookup"><span data-stu-id="4ef36-109">Never send data to this receive location.</span></span> [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="4ef36-110">permet à cet emplacement par de réception par défaut.</span><span class="sxs-lookup"><span data-stu-id="4ef36-110"> enables this receive location by default.</span></span>  
  
 <span data-ttu-id="4ef36-111">**TwoWayAckReceiveLocation**, qui le [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Assistant installation crée, utilise le **BizTalkServerApplication** en tant que le Gestionnaire de réception.</span><span class="sxs-lookup"><span data-stu-id="4ef36-111">**TwoWayAckReceiveLocation**, which the [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Setup Wizard creates, uses the **BizTalkServerApplication** as the receive handler.</span></span> <span data-ttu-id="4ef36-112">Toutefois, si vous choisissez de créer un nouvel hôte et l’utiliser en tant que le Gestionnaire de réception pour MLLP, puis vous devez procédez comme suit pour créer un nouveau **TwoWayAckReceiveLocation**:</span><span class="sxs-lookup"><span data-stu-id="4ef36-112">However, if you choose to create a new host and use it as the receive handler for MLLP, then you must do the following to create a new **TwoWayAckReceiveLocation**:</span></span>  
  
1.  <span data-ttu-id="4ef36-113">Créer un unidirectionnel port de réception.</span><span class="sxs-lookup"><span data-stu-id="4ef36-113">Create a one-way receive port.</span></span>  
  
2.  <span data-ttu-id="4ef36-114">Créer un unidirectionnel MLLP l’emplacement de réception.</span><span class="sxs-lookup"><span data-stu-id="4ef36-114">Create a one-way MLLP receive location.</span></span>  
  
3.  <span data-ttu-id="4ef36-115">Spécifiez les valeurs appropriées pour les propriétés de transport MLLP.</span><span class="sxs-lookup"><span data-stu-id="4ef36-115">Specify the appropriate values for the MLLP transport properties.</span></span>  
  
4.  <span data-ttu-id="4ef36-116">Spécifiez le que gestionnaire de réception approprié.</span><span class="sxs-lookup"><span data-stu-id="4ef36-116">Specify the appropriate receive handler.</span></span>  
  
5.  <span data-ttu-id="4ef36-117">Activez l'emplacement de réception</span><span class="sxs-lookup"><span data-stu-id="4ef36-117">Enable the receive location.</span></span>  
  
### <a name="to-create-a-send-port-enabled-to-receive-an-ack-on-the-same-socket"></a><span data-ttu-id="4ef36-118">Pour créer un port d’envoi activé pour recevoir un accusé de réception sur le même socket</span><span class="sxs-lookup"><span data-stu-id="4ef36-118">To create a send port enabled to receive an ACK on the same socket</span></span>  
  
1.  <span data-ttu-id="4ef36-119">Ouvrez la Console Administration de BizTalk, puis **Administration de BizTalk Server**, **groupe BizTalk**, **Applications**, et **BizTalk Application 1**.</span><span class="sxs-lookup"><span data-stu-id="4ef36-119">Open the BizTalk Administration Console, and then expand **BizTalk Server Administration**, **BizTalk Group**, **Applications**, and **BizTalk Application 1**.</span></span> <span data-ttu-id="4ef36-120">Avec le bouton droit **Ports d’envoi**, pointez sur Nouveau, puis cliquez sur **Port d’envoi unidirectionnel statique**.</span><span class="sxs-lookup"><span data-stu-id="4ef36-120">Right-click **Send Ports**, point to New, and then click **Static One-way Send Port**.</span></span>  
  
2.  <span data-ttu-id="4ef36-121">Dans le **nom** , tapez le nom du port d’envoi.</span><span class="sxs-lookup"><span data-stu-id="4ef36-121">In the **Name** box, type the name of the send port.</span></span>  
  
3.  <span data-ttu-id="4ef36-122">Dans le **Transport** section, pour **Type**, sélectionnez **MLLP**.</span><span class="sxs-lookup"><span data-stu-id="4ef36-122">In the **Transport** section, for **Type**, select **MLLP**.</span></span>  
  
4.  <span data-ttu-id="4ef36-123">Cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="4ef36-123">Click **Configure**.</span></span>  
  
5.  <span data-ttu-id="4ef36-124">Dans la boîte de dialogue Propriétés du Transport MLLP, tapez un nom de connexion et un hôte (par exemple, **localhost**).</span><span class="sxs-lookup"><span data-stu-id="4ef36-124">In the MLLP Transport Properties dialog box, type a connection name and host (for instance, **localhost**).</span></span>  
  
6.  <span data-ttu-id="4ef36-125">Pour **activée de réponse de sollicitation**, sélectionnez **Oui**.</span><span class="sxs-lookup"><span data-stu-id="4ef36-125">For **Solicit Response Enabled**, select **Yes**.</span></span> <span data-ttu-id="4ef36-126">Laissez **envoyer recevoir emplacement (URI) de l’accusé de réception** vide, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="4ef36-126">Leave **Submit Receive Location (URI) for ACK** blank, and then click **OK**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4ef36-127">Lorsque vous laissez **soumettre un emplacement de réception** vide, BTAHL7 entre l’URI pour la valeur par défaut **TwoWayAckReceiveLocation**.</span><span class="sxs-lookup"><span data-stu-id="4ef36-127">When you leave **Submit Receive Location** blank, BTAHL7 enters the URI for the default **TwoWayAckReceiveLocation**.</span></span> <span data-ttu-id="4ef36-128">Vous pouvez vérifier qu’après un clic sur **OK** à l’étape 6, en cliquant sur **Configuration** à nouveau.</span><span class="sxs-lookup"><span data-stu-id="4ef36-128">You can verify that after clicking **OK** in step 6, by clicking **Configuration** again.</span></span> <span data-ttu-id="4ef36-129">L’URI de **TwoWayAckReceiveLocation** (127.0.0.1:65535) devra être entré dans **envoyer recevoir emplacement (URI) de l’accusé de réception**.</span><span class="sxs-lookup"><span data-stu-id="4ef36-129">The URI for **TwoWayAckReceiveLocation** (127.0.0.1:65535) will be entered in **Submit Receive Location (URI) for ACK**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4ef36-130">Vous devez créer un port d’envoi pour vous abonner à l’accusé de réception reçu, ou l’accusé de réception s’affichent dans un état suspendu, car aucun abonnement ont été trouvées.</span><span class="sxs-lookup"><span data-stu-id="4ef36-130">You must create a send port to subscribe to the ACK received, or the ACK will be seen in a suspended state, because no subscriptions were found.</span></span> <span data-ttu-id="4ef36-131">Pour vous abonner à l’accusé de réception reçu par le port d’envoi, utilisez des filtres, par exemple,  **BTS. MessageType == \<* MessageType*> ** et  **BTS. ReceivePortName == \<* ReceivePort*> **.</span><span class="sxs-lookup"><span data-stu-id="4ef36-131">To subscribe to the ACK received by the send port, use filters, for example, **BTS.MessageType == \<*MessageType*>** and **BTS.ReceivePortName == \<*ReceivePort*>**.</span></span> <span data-ttu-id="4ef36-132">Pour les accusés de réception statiques, le type de message est **StaticAck**.</span><span class="sxs-lookup"><span data-stu-id="4ef36-132">For static ACKs, the message type is **StaticAck**.</span></span>  
  
7.  <span data-ttu-id="4ef36-133">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="4ef36-133">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ef36-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4ef36-134">See Also</span></span>  
 <span data-ttu-id="4ef36-135">[Création et le traitement des accusés de réception](../../adapters-and-accelerators/accelerator-hl7/creating-and-processing-acknowledgments.md) </span><span class="sxs-lookup"><span data-stu-id="4ef36-135">[Creating and Processing Acknowledgments](../../adapters-and-accelerators/accelerator-hl7/creating-and-processing-acknowledgments.md) </span></span>  
 <span data-ttu-id="4ef36-136">[Types de schémas de Message de l’accusé de réception](../../adapters-and-accelerators/accelerator-hl7/ack-message-schema-types.md) </span><span class="sxs-lookup"><span data-stu-id="4ef36-136">[ACK Message Schema Types](../../adapters-and-accelerators/accelerator-hl7/ack-message-schema-types.md) </span></span>  
 <span data-ttu-id="4ef36-137">[Segment de message d’accusé de réception](../../adapters-and-accelerators/accelerator-hl7/message-acknowledgment-segment.md) </span><span class="sxs-lookup"><span data-stu-id="4ef36-137">[Message Acknowledgment Segment](../../adapters-and-accelerators/accelerator-hl7/message-acknowledgment-segment.md) </span></span>  
 [<span data-ttu-id="4ef36-138">Conditions d’erreur d’accusé de réception</span><span class="sxs-lookup"><span data-stu-id="4ef36-138">Acknowledgment Error Conditions</span></span>](../../adapters-and-accelerators/accelerator-hl7/acknowledgment-error-conditions.md)