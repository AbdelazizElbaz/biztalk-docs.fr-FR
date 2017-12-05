---
title: "Étape 5 : Créer le Port d’envoi pour le lot de messages | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5db815df-5b76-4ba4-99ab-c7766b0c301a
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a5749166c8a9b34d5e5a04849c4179ac4427201c
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="step-5-create-the-send-port-for-the-message-batch"></a><span data-ttu-id="c1e36-102">Étape 5 : Créer le Port d’envoi pour le lot de messages</span><span class="sxs-lookup"><span data-stu-id="c1e36-102">Step 5: Create the Send Port for the Message Batch</span></span>
<span data-ttu-id="c1e36-103">Dans cette étape, vous créez un port d’envoi pour remettre le lot de messages que vous créez au tiers de destination.</span><span class="sxs-lookup"><span data-stu-id="c1e36-103">In this step, you create a send port to deliver the message batch that you create to the destination party.</span></span> <span data-ttu-id="c1e36-104">Il s’agit d’un port statique unidirectionnel avec un type d’adaptateur FILE.</span><span class="sxs-lookup"><span data-stu-id="c1e36-104">This is a static one-way port with a FILE adapter type.</span></span> <span data-ttu-id="c1e36-105">Vous désignez un dossier de fichiers pour la destination (\Tutorial_BatchMsgDrop) où [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] supprimera le fichier de commandes de message.</span><span class="sxs-lookup"><span data-stu-id="c1e36-105">You designate a file folder for the destination (\Tutorial_BatchMsgDrop) where [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] will drop the message batch file.</span></span> <span data-ttu-id="c1e36-106">Vous définissez un filtre pour le port qui indique le type de lots de messages envoie les ports.</span><span class="sxs-lookup"><span data-stu-id="c1e36-106">You define a filter for the port indicating what type of message batches the ports will send.</span></span> <span data-ttu-id="c1e36-107">Le filtre spécifie la destination des Tutorial_BatchDest et le type de message de OutboundBatch.</span><span class="sxs-lookup"><span data-stu-id="c1e36-107">The filter specifies the destination of Tutorial_BatchDest and the message type of OutboundBatch.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c1e36-108">Lors de l’exécution de cette partie du didacticiel, vous pouvez simplifier les résultats en arrêtant le port d’envoi utilisé dans la partie 2 du didacticiel : le **Tutorial_BTAHL7Drop** port d’envoi.</span><span class="sxs-lookup"><span data-stu-id="c1e36-108">When running this part of the tutorial, you can simplify the results by stopping the send port used in Part 2 of the tutorial: the **Tutorial_BTAHL7Drop** send port.</span></span>  
  
### <a name="to-create-the-send-port-for-the-message-batch"></a><span data-ttu-id="c1e36-109">Pour créer le port d’envoi pour le lot de messages</span><span class="sxs-lookup"><span data-stu-id="c1e36-109">To create the send port for the message batch</span></span>  
  
1.  <span data-ttu-id="c1e36-110">Dans la Console Administration de BizTalk Server, cliquez sur **Ports d’envoi**, pointez sur **nouveau**, puis cliquez sur **Port d’envoi unidirectionnel statique**.</span><span class="sxs-lookup"><span data-stu-id="c1e36-110">In the BizTalk Server Administration Console, right-click **Send Ports**, point to **New**, and then click **Static One-way Send Port**.</span></span>  
  
2.  <span data-ttu-id="c1e36-111">Dans la boîte de dialogue Propriétés de Port d’envoi, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="c1e36-111">In the Send Port Properties dialog box, do the following:</span></span>  
  
    |<span data-ttu-id="c1e36-112">Utiliser</span><span class="sxs-lookup"><span data-stu-id="c1e36-112">Use this</span></span>|<span data-ttu-id="c1e36-113">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="c1e36-113">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="c1e36-114">**Nom**</span><span class="sxs-lookup"><span data-stu-id="c1e36-114">**Name**</span></span>|<span data-ttu-id="c1e36-115">Type **Tutorial_BatchDest**.</span><span class="sxs-lookup"><span data-stu-id="c1e36-115">Type **Tutorial_BatchDest**.</span></span>|  
    |<span data-ttu-id="c1e36-116">**Type**</span><span class="sxs-lookup"><span data-stu-id="c1e36-116">**Type**</span></span>|<span data-ttu-id="c1e36-117">Sélectionnez **fichier** dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="c1e36-117">Select **FILE** from the drop-down list.</span></span>|  
    |<span data-ttu-id="c1e36-118">**Configurer**</span><span class="sxs-lookup"><span data-stu-id="c1e36-118">**Configure**</span></span>|<span data-ttu-id="c1e36-119">Cliquez sur **configurer** pour ouvrir la boîte de dialogue Propriétés du Transport FILE.</span><span class="sxs-lookup"><span data-stu-id="c1e36-119">Click **Configure** to open the FILE Transport Properties dialog box.</span></span>|  
  
3.  <span data-ttu-id="c1e36-120">Dans le **propriétés du Transport FILE** boîte de dialogue zone, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="c1e36-120">In the **FILE Transport Properties** dialog box, do the following:</span></span>  
  
    |<span data-ttu-id="c1e36-121">Utiliser</span><span class="sxs-lookup"><span data-stu-id="c1e36-121">Use this</span></span>|<span data-ttu-id="c1e36-122">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="c1e36-122">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="c1e36-123">**Dossier de destination**</span><span class="sxs-lookup"><span data-stu-id="c1e36-123">**Destination folder**</span></span>|<span data-ttu-id="c1e36-124">Accédez à  **\<* lecteur*:\>\Program Files\Microsoft BizTalk \<version\> Accelerator for HL7\SDK\End en bout Tutorial\Tutorial_ BatchMsgDrop **.</span><span class="sxs-lookup"><span data-stu-id="c1e36-124">Browse to **\<*drive*:\>\Program Files\Microsoft  BizTalk \<version\> Accelerator for HL7\SDK\End-to-End Tutorial\Tutorial_BatchMsgDrop**.</span></span> <span data-ttu-id="c1e36-125">Il s’agit du chemin d’accès à l’emplacement sur le système de fichiers ou le partage public auquel [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] réécrit le fichier contenant le lot de messages.</span><span class="sxs-lookup"><span data-stu-id="c1e36-125">This is the path to the location on the file system or public share to which [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] will write the file containing the message batch.</span></span>|  
    |<span data-ttu-id="c1e36-126">**Nom de fichier**</span><span class="sxs-lookup"><span data-stu-id="c1e36-126">**File name**</span></span>|<span data-ttu-id="c1e36-127">Type **%MessageID%.txt** (remplacez l’extension .xml avec l’extension .txt).</span><span class="sxs-lookup"><span data-stu-id="c1e36-127">Type **%MessageID%.txt** (replace the .xml extension with the .txt extension).</span></span>|  
    |<span data-ttu-id="c1e36-128">**Mode de copie**</span><span class="sxs-lookup"><span data-stu-id="c1e36-128">**Copy mode**</span></span>|<span data-ttu-id="c1e36-129">Sélectionnez **créer de nouveaux**.</span><span class="sxs-lookup"><span data-stu-id="c1e36-129">Select **Create New**.</span></span>|  
  
4.  <span data-ttu-id="c1e36-130">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="c1e36-130">Click **OK**.</span></span>  
  
5.  <span data-ttu-id="c1e36-131">Dans la boîte de dialogue Propriétés de Port d’envoi pour **pipeline d’envoi**, sélectionnez **BTAHL72XPipelines.BTAHL72XSendPipeline**.</span><span class="sxs-lookup"><span data-stu-id="c1e36-131">In the Send Port Properties dialog box, for **Send pipeline**, select **BTAHL72XPipelines.BTAHL72XSendPipeline**.</span></span>  
  
6.  <span data-ttu-id="c1e36-132">Dans l’arborescence de la console, cliquez sur **filtres**, puis procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="c1e36-132">In the console tree, click **Filters**, and then do the following:</span></span>  
  
    |<span data-ttu-id="c1e36-133">Utiliser</span><span class="sxs-lookup"><span data-stu-id="c1e36-133">Use this</span></span>|<span data-ttu-id="c1e36-134">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="c1e36-134">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="c1e36-135">**Propriété**</span><span class="sxs-lookup"><span data-stu-id="c1e36-135">**Property**</span></span>|<span data-ttu-id="c1e36-136">Cliquez sur le champ sous **propriété**, puis sélectionnez **Microsoft.Solutions.BTAHL7.BatchOrchestration.Party** dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="c1e36-136">Click the field under **Property**, and then select **Microsoft.Solutions.BTAHL7.BatchOrchestration.Party** from the drop-down list.</span></span>|  
    |<span data-ttu-id="c1e36-137">**Opérateur**</span><span class="sxs-lookup"><span data-stu-id="c1e36-137">**Operator**</span></span>|<span data-ttu-id="c1e36-138">Laissez  **==**  comme l’opérateur.</span><span class="sxs-lookup"><span data-stu-id="c1e36-138">Leave **==** as the operator.</span></span>|  
    |<span data-ttu-id="c1e36-139">**Valeur**</span><span class="sxs-lookup"><span data-stu-id="c1e36-139">**Value**</span></span>|<span data-ttu-id="c1e36-140">Type **Tutorial_BatchDest**.</span><span class="sxs-lookup"><span data-stu-id="c1e36-140">Type **Tutorial_BatchDest**.</span></span>|  
    |<span data-ttu-id="c1e36-141">**Regrouper par**</span><span class="sxs-lookup"><span data-stu-id="c1e36-141">**Group By**</span></span>|<span data-ttu-id="c1e36-142">Sélectionnez **et** dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="c1e36-142">Select **And** from the drop-down list.</span></span>|  
    |<span data-ttu-id="c1e36-143">**Propriété**</span><span class="sxs-lookup"><span data-stu-id="c1e36-143">**Property**</span></span>|<span data-ttu-id="c1e36-144">Sélectionnez **BTAHL7Schemas.BTAHL7MessageType**.</span><span class="sxs-lookup"><span data-stu-id="c1e36-144">Select **BTAHL7Schemas.BTAHL7MessageType**.</span></span>|  
    |<span data-ttu-id="c1e36-145">**Opérateur**</span><span class="sxs-lookup"><span data-stu-id="c1e36-145">**Operator**</span></span>|<span data-ttu-id="c1e36-146">Laissez  **==**  comme l’opérateur.</span><span class="sxs-lookup"><span data-stu-id="c1e36-146">Leave **==** as the operator.</span></span>|  
    |<span data-ttu-id="c1e36-147">**Valeur**</span><span class="sxs-lookup"><span data-stu-id="c1e36-147">**Value**</span></span>|<span data-ttu-id="c1e36-148">Type **OutboundBatch**.</span><span class="sxs-lookup"><span data-stu-id="c1e36-148">Type **OutboundBatch**.</span></span>|  
  
7.  <span data-ttu-id="c1e36-149">Appuyez sur **Entrée**.</span><span class="sxs-lookup"><span data-stu-id="c1e36-149">Press **Enter**.</span></span> <span data-ttu-id="c1e36-150">Dans le volet du bas de la boîte de dialogue, vérifiez que vous avez correctement entré l’expression de filtre, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="c1e36-150">In the pane at the bottom of the dialog box, verify that you entered the filter expression correctly, and then click **OK**.</span></span>  
  
8.  <span data-ttu-id="c1e36-151">Dans la Console Administration de BizTalk, sélectionnez **Ports d’envoi**, avec le bouton droit **Tutorial_BatchDest**, puis cliquez sur **Démarrer**.</span><span class="sxs-lookup"><span data-stu-id="c1e36-151">In the BizTalk Administration Console, select **Send Ports**, right-click **Tutorial_BatchDest**, and then click **Start**.</span></span>  
  
### <a name="to-associate-the-send-port-with-the-destination-party"></a><span data-ttu-id="c1e36-152">Pour associer le port d’envoi de tiers de destination</span><span class="sxs-lookup"><span data-stu-id="c1e36-152">To associate the send port with the destination party</span></span>  
  
1.  <span data-ttu-id="c1e36-153">Dans la Console Administration de BizTalk Server, développez **Parties**, cliquez sur **Tutorial_BatchDest**, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="c1e36-153">In the BizTalk Server Administration Console, expand **Parties**, click **Tutorial_BatchDest**, and then right-click **Properties**.</span></span>  
  
2.  <span data-ttu-id="c1e36-154">Dans la boîte de dialogue Propriétés du tiers, cliquez sur **Ports d’envoi** dans l’arborescence de la console.</span><span class="sxs-lookup"><span data-stu-id="c1e36-154">In the Party Properties dialog box, click  **Send Ports** in the console tree.</span></span>  <span data-ttu-id="c1e36-155">Sélectionnez **Tutorial_BatchDest** dans la liste déroulante, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="c1e36-155">Select **Tutorial_BatchDest** from the drop-down list, and then click **OK**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="c1e36-156">Si une violation d’accès concurrentiel se produit pendant la **Tutorial_DestBatch** tiers a été mis à jour, cliquez sur **OK** et fermer la boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="c1e36-156">If a concurrency violation occurs while the **Tutorial_DestBatch** party was being updated, click **OK** and close the dialog box.</span></span> <span data-ttu-id="c1e36-157">Dans la Console d’Administration, cliquez sur **groupe BizTalk**, cliquez sur **Actualiser**, puis répétez les étapes 1 et 2.</span><span class="sxs-lookup"><span data-stu-id="c1e36-157">In the Administration Console, right-click **BizTalk Group**, click **Refresh**, and then repeat steps 1 and 2.</span></span>  
  
 <span data-ttu-id="c1e36-158">Passez à [étape 6 : créer le Port d’envoi pour le traitement de l’accusé de réception](../../adapters-and-accelerators/accelerator-hl7/step-6-create-the-send-port-for-the-acknowledgment-batch.md).</span><span class="sxs-lookup"><span data-stu-id="c1e36-158">Proceed to [Step 6: Create the Send Port for the Acknowledgment Batch](../../adapters-and-accelerators/accelerator-hl7/step-6-create-the-send-port-for-the-acknowledgment-batch.md).</span></span>