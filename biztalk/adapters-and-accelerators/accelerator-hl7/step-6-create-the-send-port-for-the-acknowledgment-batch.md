---
title: "Étape 6 : Créer le Port d’envoi pour le traitement de l’accusé de réception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f2a0f1ee-e060-4fb9-923e-ebe8168777d9
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d88607133c4ffde7baeb9742755c9393bd73196c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-6-create-the-send-port-for-the-acknowledgment-batch"></a><span data-ttu-id="628e6-102">Étape 6 : Créer le Port d’envoi pour le traitement de l’accusé de réception</span><span class="sxs-lookup"><span data-stu-id="628e6-102">Step 6: Create the Send Port for the Acknowledgment Batch</span></span>
<span data-ttu-id="628e6-103">Dans cette étape, vous créez un port d’envoi pour fournir le traitement de l’accusé de réception que vous créez à la partie de la source.</span><span class="sxs-lookup"><span data-stu-id="628e6-103">In this step, you create a send port to deliver the acknowledgment batch that you create to the source party.</span></span> <span data-ttu-id="628e6-104">Il s’agit d’un port statique unidirectionnel avec un type d’adaptateur FILE.</span><span class="sxs-lookup"><span data-stu-id="628e6-104">This is a static one-way port with a FILE adapter type.</span></span> <span data-ttu-id="628e6-105">Vous désignez un dossier de fichiers pour la source (\Tutorial_BatchACKDrop), où [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] supprimera le fichier de commandes d’accusé de réception.</span><span class="sxs-lookup"><span data-stu-id="628e6-105">You designate a file folder for the source (\Tutorial_BatchACKDrop), where [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] will drop the acknowledgment batch file.</span></span> <span data-ttu-id="628e6-106">Vous définissez un filtre pour le port qui indique le type de lots d’accusé de réception envoie les ports.</span><span class="sxs-lookup"><span data-stu-id="628e6-106">You define a filter for the port indicating what type of acknowledgment batches the ports will send.</span></span> <span data-ttu-id="628e6-107">Le filtre spécifie la source de Tutorial_BatchSource et le type de message de OutboundBatch.</span><span class="sxs-lookup"><span data-stu-id="628e6-107">The filter specifies the source of Tutorial_BatchSource and the message type of OutboundBatch.</span></span>  
  
### <a name="to-create-the-send-port-for-the-acknowledgment-batch"></a><span data-ttu-id="628e6-108">Pour créer le port d’envoi pour le traitement de l’accusé de réception</span><span class="sxs-lookup"><span data-stu-id="628e6-108">To create the send port for the acknowledgment batch</span></span>  
  
1.  <span data-ttu-id="628e6-109">Dans la Console Administration de BizTalk Server, cliquez sur **Ports d’envoi**, pointez sur **nouveau**, puis cliquez sur **Port d’envoi unidirectionnel statique**.</span><span class="sxs-lookup"><span data-stu-id="628e6-109">In the BizTalk Server Administration Console, right-click **Send Ports**, point to **New**, and then click **Static One-way Send Port**.</span></span>  
  
2.  <span data-ttu-id="628e6-110">Dans la boîte de dialogue Propriétés de Port d’envoi, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="628e6-110">In the Send Port Properties dialog box, do the following:</span></span>  
  
    |<span data-ttu-id="628e6-111">Utiliser</span><span class="sxs-lookup"><span data-stu-id="628e6-111">Use this</span></span>|<span data-ttu-id="628e6-112">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="628e6-112">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="628e6-113">**Nom**</span><span class="sxs-lookup"><span data-stu-id="628e6-113">**Name**</span></span>|<span data-ttu-id="628e6-114">Type **Tutorial_BatchSource**.</span><span class="sxs-lookup"><span data-stu-id="628e6-114">Type **Tutorial_BatchSource**.</span></span>|  
    |<span data-ttu-id="628e6-115">**Type**</span><span class="sxs-lookup"><span data-stu-id="628e6-115">**Type**</span></span>|<span data-ttu-id="628e6-116">Sélectionnez **fichier** dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="628e6-116">Select **FILE** from the drop-down list.</span></span>|  
    |<span data-ttu-id="628e6-117">**Configurer**</span><span class="sxs-lookup"><span data-stu-id="628e6-117">**Configure**</span></span>|<span data-ttu-id="628e6-118">Cliquez sur **configurer** pour ouvrir la boîte de dialogue Propriétés du Transport FILE.</span><span class="sxs-lookup"><span data-stu-id="628e6-118">Click **Configure** to open the FILE Transport Properties dialog box.</span></span>|  
  
3.  <span data-ttu-id="628e6-119">Dans la boîte de dialogue Propriétés du Transport FILE, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="628e6-119">In the FILE Transport Properties dialog box, do the following:</span></span>  
  
    |<span data-ttu-id="628e6-120">Utiliser</span><span class="sxs-lookup"><span data-stu-id="628e6-120">Use this</span></span>|<span data-ttu-id="628e6-121">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="628e6-121">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="628e6-122">**Dossier de destination**</span><span class="sxs-lookup"><span data-stu-id="628e6-122">**Destination folder**</span></span>|<span data-ttu-id="628e6-123">Accédez à  **\<* lecteur*: > \Program Files\Microsoft BizTalk \<version > Accelerator for HL7\SDK\End en bout Tutorial\Tutorial_BatchACKDrop **.</span><span class="sxs-lookup"><span data-stu-id="628e6-123">Browse to **\<*drive*:>\Program Files\Microsoft BizTalk \<version> Accelerator for HL7\SDK\End-to-End Tutorial\Tutorial_BatchACKDrop**.</span></span> <span data-ttu-id="628e6-124">Il s’agit du chemin d’accès à l’emplacement sur le système de fichiers ou le partage public auquel [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] réécrit le fichier contenant le lot d’accusé de réception.</span><span class="sxs-lookup"><span data-stu-id="628e6-124">This is the path to the location on the file system or public share to which [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] will write the file containing the acknowledgment batch.</span></span>|  
    |<span data-ttu-id="628e6-125">**Nom de fichier**</span><span class="sxs-lookup"><span data-stu-id="628e6-125">**File name**</span></span>|<span data-ttu-id="628e6-126">Type **%MessageID%.txt** (remplacez l’extension .xml avec l’extension .txt).</span><span class="sxs-lookup"><span data-stu-id="628e6-126">Type **%MessageID%.txt** (replace the .xml extension with the .txt extension).</span></span>|  
    |<span data-ttu-id="628e6-127">**Mode de copie**</span><span class="sxs-lookup"><span data-stu-id="628e6-127">**Copy mode**</span></span>|<span data-ttu-id="628e6-128">Sélectionnez **créer de nouveaux**.</span><span class="sxs-lookup"><span data-stu-id="628e6-128">Select **Create New**.</span></span>|  
  
4.  <span data-ttu-id="628e6-129">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="628e6-129">Click **OK**.</span></span>  
  
5.  <span data-ttu-id="628e6-130">Dans la boîte de dialogue Propriétés de Port d’envoi pour **pipeline d’envoi**, sélectionnez **BTAHL72XPipelines.BTAHL72XSendPipeline**.</span><span class="sxs-lookup"><span data-stu-id="628e6-130">In the Send Port Properties dialog box, for **Send pipeline**, select **BTAHL72XPipelines.BTAHL72XSendPipeline**.</span></span>  
  
6.  <span data-ttu-id="628e6-131">Dans l’arborescence de la console, cliquez sur **filtres**, puis procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="628e6-131">In the console tree, click **Filters**, and then do the following:</span></span>  
  
    |<span data-ttu-id="628e6-132">Utiliser</span><span class="sxs-lookup"><span data-stu-id="628e6-132">Use this</span></span>|<span data-ttu-id="628e6-133">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="628e6-133">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="628e6-134">**Propriété**</span><span class="sxs-lookup"><span data-stu-id="628e6-134">**Property**</span></span>|<span data-ttu-id="628e6-135">Cliquez sur le champ sous **propriété**, puis sélectionnez **Microsoft.Solutions.BTAHL7.BatchOrchestration.Party** dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="628e6-135">Click the field under **Property**, and then select **Microsoft.Solutions.BTAHL7.BatchOrchestration.Party** from the drop-down list.</span></span>|  
    |<span data-ttu-id="628e6-136">**Opérateur**</span><span class="sxs-lookup"><span data-stu-id="628e6-136">**Operator**</span></span>|<span data-ttu-id="628e6-137">Laissez  **==**  comme l’opérateur.</span><span class="sxs-lookup"><span data-stu-id="628e6-137">Leave **==** as the operator.</span></span>|  
    |<span data-ttu-id="628e6-138">**Valeur**</span><span class="sxs-lookup"><span data-stu-id="628e6-138">**Value**</span></span>|<span data-ttu-id="628e6-139">Type **Tutorial_BatchSource**.</span><span class="sxs-lookup"><span data-stu-id="628e6-139">Type **Tutorial_BatchSource**.</span></span>|  
    |<span data-ttu-id="628e6-140">**Regrouper par**</span><span class="sxs-lookup"><span data-stu-id="628e6-140">**Group By**</span></span>|<span data-ttu-id="628e6-141">Sélectionnez **et** dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="628e6-141">Select **And** from the drop-down list.</span></span>|  
    |<span data-ttu-id="628e6-142">**Propriété**</span><span class="sxs-lookup"><span data-stu-id="628e6-142">**Property**</span></span>|<span data-ttu-id="628e6-143">Sélectionnez **BTAHL7Schemas.BTAHL7MessageType**.</span><span class="sxs-lookup"><span data-stu-id="628e6-143">Select **BTAHL7Schemas.BTAHL7MessageType**.</span></span>|  
    |<span data-ttu-id="628e6-144">**Opérateur**</span><span class="sxs-lookup"><span data-stu-id="628e6-144">**Operator**</span></span>|<span data-ttu-id="628e6-145">Laissez  **==**  comme l’opérateur.</span><span class="sxs-lookup"><span data-stu-id="628e6-145">Leave **==** as the operator.</span></span>|  
    |<span data-ttu-id="628e6-146">**Valeur**</span><span class="sxs-lookup"><span data-stu-id="628e6-146">**Value**</span></span>|<span data-ttu-id="628e6-147">Type **OutboundBatch**.</span><span class="sxs-lookup"><span data-stu-id="628e6-147">Type **OutboundBatch**.</span></span>|  
  
7.  <span data-ttu-id="628e6-148">Appuyez sur **Entrée**.</span><span class="sxs-lookup"><span data-stu-id="628e6-148">Press **Enter**.</span></span> <span data-ttu-id="628e6-149">Dans le volet du bas de la boîte de dialogue, vérifiez que vous avez correctement entré l’expression de filtre, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="628e6-149">In the pane at the bottom of the dialog box, verify that you entered the filter expression correctly, and then click **OK**.</span></span>  
  
8.  <span data-ttu-id="628e6-150">Dans la Console Administration de BizTalk, sélectionnez **Ports d’envoi**, avec le bouton droit **Tutorial_BatchSource**, puis cliquez sur **Démarrer**.</span><span class="sxs-lookup"><span data-stu-id="628e6-150">In the BizTalk Administration Console, select **Send Ports**, right-click **Tutorial_BatchSource**, and then click **Start**.</span></span>  
  
### <a name="to-associate-the-send-port-with-the-source-party"></a><span data-ttu-id="628e6-151">Pour associer le port d’envoi du tiers source</span><span class="sxs-lookup"><span data-stu-id="628e6-151">To associate the send port with the source party</span></span>  
  
1.  <span data-ttu-id="628e6-152">Dans la Console Administration de BizTalk, cliquez sur **Parties**.</span><span class="sxs-lookup"><span data-stu-id="628e6-152">In the BizTalk Administration Console, click **Parties**.</span></span> <span data-ttu-id="628e6-153">Avec le bouton droit **Tutorial_BatchSource**, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="628e6-153">Right-click **Tutorial_BatchSource**, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="628e6-154">Dans la boîte de dialogue Propriétés du tiers, cliquez sur **Ports d’envoi** dans l’arborescence de la console.</span><span class="sxs-lookup"><span data-stu-id="628e6-154">In the Party Properties dialog box, click **Send Ports** in the console tree.</span></span> <span data-ttu-id="628e6-155">Pour **Ports d’envoi**, sélectionnez **Tutorial_BatchSource** dans la liste déroulante, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="628e6-155">For **Send Ports**, select **Tutorial_BatchSource** from the drop-down list, and then click **OK**.</span></span>  
  
 <span data-ttu-id="628e6-156">Passez à [étape 7 : démarrer l’Orchestration et redémarrez le serveur BizTalk](../../adapters-and-accelerators/accelerator-hl7/step-7-start-the-orchestration-and-restart-biztalk-server.md).</span><span class="sxs-lookup"><span data-stu-id="628e6-156">Proceed to [Step 7: Start the Orchestration and Restart BizTalk Server](../../adapters-and-accelerators/accelerator-hl7/step-7-start-the-orchestration-and-restart-biztalk-server.md).</span></span>