---
title: "Créer une orchestration BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 16c637ae-f94f-40f8-8ce7-73a7b7df9f8f
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bb9c2347a989dd59b97125e119ea79a9996c53ec
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="create-a-biztalk-server-orchestration"></a><span data-ttu-id="2d1bc-102">Créer une orchestration BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="2d1bc-102">Create a BizTalk Server orchestration</span></span>
> [!NOTE]
>  <span data-ttu-id="2d1bc-103">Ce didacticiel s'applique uniquement à [!INCLUDE[prague](../includes/prague-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2d1bc-103">This tutorial applies to [!INCLUDE[prague](../includes/prague-md.md)] only.</span></span>  
  
 <span data-ttu-id="2d1bc-104">Créez une orchestration [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] qui, une fois déployée, reçoit un message de bon de commande JSON, le transforme en facture XML, puis envoie une facture JSON.</span><span class="sxs-lookup"><span data-stu-id="2d1bc-104">Create a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] orchestration that, when deployed, receives a JSON purchase order message, transforms it to an XML invoice, and then sends out a JSON invoice.</span></span>  
  
## <a name="define-message-and-message-types"></a><span data-ttu-id="2d1bc-105">Définir les messages et les types de messages</span><span class="sxs-lookup"><span data-stu-id="2d1bc-105">Define message and message types</span></span>  
 <span data-ttu-id="2d1bc-106">Cette solution fonctionne avec deux messages de base - les bons de commande et les factures.</span><span class="sxs-lookup"><span data-stu-id="2d1bc-106">This solution works with two basic messages – purchase order and invoice.</span></span> <span data-ttu-id="2d1bc-107">Nous avons déjà généré le schéma du bon de commande d'un message JSON en utilisant l' Assistant Schéma de JSON.</span><span class="sxs-lookup"><span data-stu-id="2d1bc-107">We already generated the schema of the purchase order from a JSON message using the JSON schema wizard.</span></span> <span data-ttu-id="2d1bc-108">L'exemple fourni pour ce didacticiel dispose déjà du schéma pour le message de la facture.</span><span class="sxs-lookup"><span data-stu-id="2d1bc-108">The sample provided for this tutorial already has the schema for the invoice message.</span></span> <span data-ttu-id="2d1bc-109">Nous utilisons ces schémas pour créer les types de messages dans l'application [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2d1bc-109">We use these schemas to create the message types in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] application.</span></span>  
  
1.  <span data-ttu-id="2d1bc-110">Ajoutez une orchestration au projet BizTalk et ouvrez la vue Orchestration.</span><span class="sxs-lookup"><span data-stu-id="2d1bc-110">Add an orchestration to the BizTalk project and open the Orchestration view.</span></span>  
  
2.  <span data-ttu-id="2d1bc-111">Dans la vue Orchestration, cliquez sur **Messages**, puis cliquez sur **nouveau Message**.</span><span class="sxs-lookup"><span data-stu-id="2d1bc-111">In the Orchestration View, right-click **Messages**, and then click **New Message**.</span></span>  
  
3.  <span data-ttu-id="2d1bc-112">Cliquez sur le message qui vient d’être créé, puis sélectionnez **fenêtre Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="2d1bc-112">Right-click the newly created message, and then select **Properties Window**.</span></span>  
  
4.  <span data-ttu-id="2d1bc-113">Dans le **propriétés** volet pour le **Message_1**, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="2d1bc-113">In the **Properties** pane for the **Message_1**, do the following:</span></span>  
  
    |<span data-ttu-id="2d1bc-114">Utiliser</span><span class="sxs-lookup"><span data-stu-id="2d1bc-114">Use this</span></span>|<span data-ttu-id="2d1bc-115">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="2d1bc-115">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="2d1bc-116">Identificateur</span><span class="sxs-lookup"><span data-stu-id="2d1bc-116">Identifier</span></span>|<span data-ttu-id="2d1bc-117">Type`PurchaseOrder`</span><span class="sxs-lookup"><span data-stu-id="2d1bc-117">Type `PurchaseOrder`</span></span>|  
    |<span data-ttu-id="2d1bc-118">Type de message</span><span class="sxs-lookup"><span data-stu-id="2d1bc-118">Message Type</span></span>|<span data-ttu-id="2d1bc-119">Dans la liste déroulante, développez **schémas**, puis sélectionnez *BTSJSON. Bon de commande*, où *BTSJSON* est le nom de votre projet BizTalk.</span><span class="sxs-lookup"><span data-stu-id="2d1bc-119">From the drop-down list, expand **Schemas**, and then select *BTSJSON.PO*, where *BTSJSON* is the name of your BizTalk project.</span></span>|  
  
5.  <span data-ttu-id="2d1bc-120">Répétez l'étape précédente pour créer un nouveau type de message pour le message de la facture.</span><span class="sxs-lookup"><span data-stu-id="2d1bc-120">Repeat the previous step to create a new message type for the invoice message.</span></span> <span data-ttu-id="2d1bc-121">Dans le **propriétés** volet pour le nouveau message, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="2d1bc-121">In the **Properties** pane for the new message, do the following:</span></span>  
  
    |<span data-ttu-id="2d1bc-122">Utiliser</span><span class="sxs-lookup"><span data-stu-id="2d1bc-122">Use this</span></span>|<span data-ttu-id="2d1bc-123">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="2d1bc-123">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="2d1bc-124">Identificateur</span><span class="sxs-lookup"><span data-stu-id="2d1bc-124">Identifier</span></span>|<span data-ttu-id="2d1bc-125">Type`InvoiceMsg`</span><span class="sxs-lookup"><span data-stu-id="2d1bc-125">Type `InvoiceMsg`</span></span>|  
    |<span data-ttu-id="2d1bc-126">Type de message</span><span class="sxs-lookup"><span data-stu-id="2d1bc-126">Message Type</span></span>|<span data-ttu-id="2d1bc-127">Dans la liste déroulante, développez **schémas**, puis sélectionnez *BTSJSON. Facture*.</span><span class="sxs-lookup"><span data-stu-id="2d1bc-127">From the drop-down list, expand **Schemas**, and then select *BTSJSON.Invoice*.</span></span>|  
  
## <a name="set-up-the-orchestration"></a><span data-ttu-id="2d1bc-128">Configurer l'orchestration</span><span class="sxs-lookup"><span data-stu-id="2d1bc-128">Set up the orchestration</span></span>  
 <span data-ttu-id="2d1bc-129">Dans cette étape, vous ajoutez des ports et des formes de message pour créer une orchestration.</span><span class="sxs-lookup"><span data-stu-id="2d1bc-129">In this step, you add message shapes and ports to create an orchestration.</span></span>  
  
### <a name="add-message-shapes"></a><span data-ttu-id="2d1bc-130">Ajouter des formes de messages</span><span class="sxs-lookup"><span data-stu-id="2d1bc-130">Add message shapes</span></span>  
 <span data-ttu-id="2d1bc-131">Ouvrez le fichier d'orchestration dans l'Explorateur de solutions, puis ajoutez les formes de messages suivantes.</span><span class="sxs-lookup"><span data-stu-id="2d1bc-131">Open the orchestration file from Solution Explorer, and add the following message shapes.</span></span>  
  
-   <span data-ttu-id="2d1bc-132">Ajouter une forme réception, définissez son nom sur **ReceivePO**et le type de message **PurchaseOrder**.</span><span class="sxs-lookup"><span data-stu-id="2d1bc-132">Add a Receive shape, set its name to **ReceivePO**, and message type to **PurchaseOrder**.</span></span>  
  
-   <span data-ttu-id="2d1bc-133">Ajoutez une forme envoi, définissez son nom sur **SendInvoice**et le type de message **InvoiceMsg**.</span><span class="sxs-lookup"><span data-stu-id="2d1bc-133">Add a Send shape, set its name to **SendInvoice**, and message type to **InvoiceMsg**.</span></span>  
  
-   <span data-ttu-id="2d1bc-134">Ajoutez une forme construire un Message et définissez la **Messages construits** propriété de la forme construire un Message à **InvoiceMsg**.</span><span class="sxs-lookup"><span data-stu-id="2d1bc-134">Add a Construct Message shape and set the **Messages Constructed** property of the Construct Message shape to **InvoiceMsg**.</span></span>  
  
-   <span data-ttu-id="2d1bc-135">Ajoutez une forme Transformer dans la forme Construire un message.</span><span class="sxs-lookup"><span data-stu-id="2d1bc-135">Add a Transform shape within the Construct Message shape.</span></span> <span data-ttu-id="2d1bc-136">Double-cliquez sur la forme Transformer et dans le **transformer la Configuration** boîte de dialogue, sélectionnez le **mappage existant** option et sélectionnez **BTSJSON. POToInvoice** carte.</span><span class="sxs-lookup"><span data-stu-id="2d1bc-136">Double-click the Transform shape and in the **Transform Configuration** dialog box, select the **Existing Map** option, and then select **BTSJSON.POToInvoice** map.</span></span> <span data-ttu-id="2d1bc-137">Ce mappage est fourni dans le cadre de l'exemple.</span><span class="sxs-lookup"><span data-stu-id="2d1bc-137">This map is provided as part of the sample.</span></span> <span data-ttu-id="2d1bc-138">Dans la boîte de dialogue, définissez **Source** à **PurchaseOrder** et **Destination** à **InvoiceMsg**.</span><span class="sxs-lookup"><span data-stu-id="2d1bc-138">In the dialog box, set **Source** to **PurchaseOrder** and set **Destination** to **InvoiceMsg**.</span></span> <span data-ttu-id="2d1bc-139">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="2d1bc-139">Click **OK**.</span></span>  
  
### <a name="add-ports"></a><span data-ttu-id="2d1bc-140">ajouter des ports</span><span class="sxs-lookup"><span data-stu-id="2d1bc-140">Add ports</span></span>  
 <span data-ttu-id="2d1bc-141">Ajoutez deux ports à l'orchestration – un pour la réception des messages et un pour l'envoi des messages.</span><span class="sxs-lookup"><span data-stu-id="2d1bc-141">Add two ports to the orchestration – one for receiving messages and one for sending messages.</span></span> <span data-ttu-id="2d1bc-142">Utilisez les propriétés suivantes pour les ports :</span><span class="sxs-lookup"><span data-stu-id="2d1bc-142">Use the following properties for the ports.</span></span>  
  
|<span data-ttu-id="2d1bc-143">Port</span><span class="sxs-lookup"><span data-stu-id="2d1bc-143">Port</span></span>|<span data-ttu-id="2d1bc-144">Propriétés</span><span class="sxs-lookup"><span data-stu-id="2d1bc-144">Properties</span></span>|  
|----------|----------------|  
|<span data-ttu-id="2d1bc-145">MessageIn</span><span class="sxs-lookup"><span data-stu-id="2d1bc-145">MessageIn</span></span>|<span data-ttu-id="2d1bc-146">-Définissez **identificateur** à *ReceiveJSONPO*</span><span class="sxs-lookup"><span data-stu-id="2d1bc-146">-   Set **Identifier** to *ReceiveJSONPO*</span></span><br /><span data-ttu-id="2d1bc-147">-Définissez **modèle de Communication** à *à sens unique*</span><span class="sxs-lookup"><span data-stu-id="2d1bc-147">-   Set **Communication Pattern** to *One-Way*</span></span><br /><span data-ttu-id="2d1bc-148">-Définissez **Direction de Communication** à *de réception*</span><span class="sxs-lookup"><span data-stu-id="2d1bc-148">-   Set **Communication Direction** to *Receive*</span></span>|  
|<span data-ttu-id="2d1bc-149">ResponseOut</span><span class="sxs-lookup"><span data-stu-id="2d1bc-149">ResponseOut</span></span>|<span data-ttu-id="2d1bc-150">-Définissez **identificateur** à *SendJSONInvoice*</span><span class="sxs-lookup"><span data-stu-id="2d1bc-150">-   Set **Identifier** to *SendJSONInvoice*</span></span><br /><span data-ttu-id="2d1bc-151">-Définissez **modèle de Communication** à *à sens unique*</span><span class="sxs-lookup"><span data-stu-id="2d1bc-151">-   Set **Communication Pattern** to *One-Way*</span></span><br /><span data-ttu-id="2d1bc-152">-Définissez **Direction de Communication** à *envoyer*</span><span class="sxs-lookup"><span data-stu-id="2d1bc-152">-   Set **Communication Direction** to *Send*</span></span>|  
  
 <span data-ttu-id="2d1bc-153">Connectez les ports et la forme de message, comme indiqué dans la capture d'écran ci-dessous, puis enregistrez les modifications apportées au projet.</span><span class="sxs-lookup"><span data-stu-id="2d1bc-153">Connect the ports and message shape, as shown in the screenshot below, and save changes to the project.</span></span>  
  
 <span data-ttu-id="2d1bc-154">![Orchestration pour traiter les messages JSON](../core/media/btsjson-orchestration.png "BTSJSON_Orchestration")</span><span class="sxs-lookup"><span data-stu-id="2d1bc-154">![Orchestration to process JSON messages](../core/media/btsjson-orchestration.png "BTSJSON_Orchestration")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d1bc-155">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2d1bc-155">See Also</span></span>  
 [<span data-ttu-id="2d1bc-156">Traitement des messages JSON à l’aide de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="2d1bc-156">Processing JSON messages using BizTalk Server</span></span>](../core/processing-json-messages-using-biztalk-server.md)