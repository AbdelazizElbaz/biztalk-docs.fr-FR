---
title: 'Étape 6 : Créer un Port d’envoi pour remettre des Messages de requête | Documents Microsoft'
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- interrogative tutorial, send ports
ms.assetid: a3cfa2aa-888d-4a82-9eb3-2e9cc29ee582
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 43c373940d8ab1e847b66527d83ef24e952d84d4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-6-create-a-send-port-to-deliver-query-messages"></a><span data-ttu-id="ac9f6-102">Étape 6 : Créer un Port d’envoi pour remettre des Messages de requête</span><span class="sxs-lookup"><span data-stu-id="ac9f6-102">Step 6: Create a Send Port to Deliver Query Messages</span></span>
<span data-ttu-id="ac9f6-103">Dans cette étape, vous créez le port d’envoi pour remettre les requêtes entrantes (Req ^ Q01 messages) à l’hôpital informations système (HIS).</span><span class="sxs-lookup"><span data-stu-id="ac9f6-103">In this step, you create the send port to deliver the incoming queries (QRY^Q01 messages) to the Hospital Information System (HIS).</span></span>  
  
### <a name="to-create-the-hissend-send-port"></a><span data-ttu-id="ac9f6-104">Pour créer le port d’envoi HIS_Send</span><span class="sxs-lookup"><span data-stu-id="ac9f6-104">To create the HIS_Send send port</span></span>  
  
1.  <span data-ttu-id="ac9f6-105">Dans la Console Administration de BizTalk Server, cliquez sur **Ports d’envoi**, pointez sur **nouveau**, puis sélectionnez **Port d’envoi unidirectionnel statique**.</span><span class="sxs-lookup"><span data-stu-id="ac9f6-105">In the BizTalk Server Administration Console, right-click **Send Ports**, point to **New**, and then select **Static One-way Send Port**.</span></span>  
  
2.  <span data-ttu-id="ac9f6-106">Dans la boîte de dialogue Propriétés de Port d’envoi, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="ac9f6-106">In the Send Port Properties dialog box, do the following:</span></span>  
  
    |<span data-ttu-id="ac9f6-107">Utiliser</span><span class="sxs-lookup"><span data-stu-id="ac9f6-107">Use this</span></span>|<span data-ttu-id="ac9f6-108">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="ac9f6-108">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="ac9f6-109">**Nom**</span><span class="sxs-lookup"><span data-stu-id="ac9f6-109">**Name**</span></span>|<span data-ttu-id="ac9f6-110">Type **HIS_Send**.</span><span class="sxs-lookup"><span data-stu-id="ac9f6-110">Type **HIS_Send**.</span></span>|  
    |<span data-ttu-id="ac9f6-111">**Type de transport**</span><span class="sxs-lookup"><span data-stu-id="ac9f6-111">**Transport type**</span></span>|<span data-ttu-id="ac9f6-112">Sélectionnez **MLLP**.</span><span class="sxs-lookup"><span data-stu-id="ac9f6-112">Select **MLLP**.</span></span>|  
    |<span data-ttu-id="ac9f6-113">**Configurer**</span><span class="sxs-lookup"><span data-stu-id="ac9f6-113">**Configure**</span></span>|<span data-ttu-id="ac9f6-114">Cliquez sur le **configurer** bouton à droite de **Type**.</span><span class="sxs-lookup"><span data-stu-id="ac9f6-114">Click the **Configure** button to the right of **Type**.</span></span>|  
  
3.  <span data-ttu-id="ac9f6-115">Dans la boîte de dialogue Propriétés du Transport MLLP, entrez les informations suivantes, puis **OK**.</span><span class="sxs-lookup"><span data-stu-id="ac9f6-115">In the MLLP Transport Properties dialog box, enter the following information and then click **OK**.</span></span>  
  
    |<span data-ttu-id="ac9f6-116">Utiliser</span><span class="sxs-lookup"><span data-stu-id="ac9f6-116">Use this</span></span>|<span data-ttu-id="ac9f6-117">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="ac9f6-117">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="ac9f6-118">**Nom de la connexion**</span><span class="sxs-lookup"><span data-stu-id="ac9f6-118">**Connection Name**</span></span>|<span data-ttu-id="ac9f6-119">Type **HIS_SendMLLP**.</span><span class="sxs-lookup"><span data-stu-id="ac9f6-119">Type **HIS_SendMLLP**.</span></span>|  
    |<span data-ttu-id="ac9f6-120">**Hôte**</span><span class="sxs-lookup"><span data-stu-id="ac9f6-120">**Host**</span></span>|<span data-ttu-id="ac9f6-121">Type **localhost**.</span><span class="sxs-lookup"><span data-stu-id="ac9f6-121">Type **localhost**.</span></span>|  
    |<span data-ttu-id="ac9f6-122">**Port**</span><span class="sxs-lookup"><span data-stu-id="ac9f6-122">**Port**</span></span>|<span data-ttu-id="ac9f6-123">Type **24000**.</span><span class="sxs-lookup"><span data-stu-id="ac9f6-123">Type **24000**.</span></span>|  
  
4.  <span data-ttu-id="ac9f6-124">Dans la boîte de dialogue Propriétés de Port d’envoi pour **Pipeline d’envoi**, sélectionnez **BTAHL72XPipelines.BTAHL72XSendPipeline**.</span><span class="sxs-lookup"><span data-stu-id="ac9f6-124">In the Send Port Properties dialog box, for **Send Pipeline**, select **BTAHL72XPipelines.BTAHL72XSendPipeline**.</span></span>  
  
5.  <span data-ttu-id="ac9f6-125">Dans l’arborescence de la Console, cliquez sur **filtres**, puis procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="ac9f6-125">In the Console Tree, click **Filters**, and then do the following:</span></span>  
  
    |<span data-ttu-id="ac9f6-126">Utiliser</span><span class="sxs-lookup"><span data-stu-id="ac9f6-126">Use this</span></span>|<span data-ttu-id="ac9f6-127">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="ac9f6-127">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="ac9f6-128">**Propriété**</span><span class="sxs-lookup"><span data-stu-id="ac9f6-128">**Property**</span></span>|<span data-ttu-id="ac9f6-129">Pour **propriété**, sélectionnez **BTS. MessageType**.</span><span class="sxs-lookup"><span data-stu-id="ac9f6-129">For **Property**, select **BTS.MessageType**.</span></span>|  
    |<span data-ttu-id="ac9f6-130">**Opérateur**</span><span class="sxs-lookup"><span data-stu-id="ac9f6-130">**Operator**</span></span>|<span data-ttu-id="ac9f6-131">Sélectionnez  **==**  dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="ac9f6-131">Select **==** from the drop-down list.</span></span>|  
    |<span data-ttu-id="ac9f6-132">**Valeur**</span><span class="sxs-lookup"><span data-stu-id="ac9f6-132">**Value**</span></span>|<span data-ttu-id="ac9f6-133">Type **http://microsoft.com/HealthCare/HL7/2X#QRY_Q01_24_GLO_DEF**.</span><span class="sxs-lookup"><span data-stu-id="ac9f6-133">Type **http://microsoft.com/HealthCare/HL7/2X#QRY_Q01_24_GLO_DEF**.</span></span>|  
    |<span data-ttu-id="ac9f6-134">**Regrouper par**</span><span class="sxs-lookup"><span data-stu-id="ac9f6-134">**Group By**</span></span>|<span data-ttu-id="ac9f6-135">Sélectionnez **et** dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="ac9f6-135">Select **AND** from the drop-down list.</span></span>|  
    |<span data-ttu-id="ac9f6-136">**Propriété**</span><span class="sxs-lookup"><span data-stu-id="ac9f6-136">**Property**</span></span>|<span data-ttu-id="ac9f6-137">Pour **propriété** sur la deuxième ligne, sélectionnez **BTAHL7Schemas.MSH5_1**.</span><span class="sxs-lookup"><span data-stu-id="ac9f6-137">For **Property** on the second line, select **BTAHL7Schemas.MSH5_1**.</span></span>|  
    |<span data-ttu-id="ac9f6-138">**Opérateur**</span><span class="sxs-lookup"><span data-stu-id="ac9f6-138">**Operator**</span></span>|<span data-ttu-id="ac9f6-139">Sélectionnez  **==**  dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="ac9f6-139">Select **==** from the drop-down list.</span></span>|  
    |<span data-ttu-id="ac9f6-140">**Valeur**</span><span class="sxs-lookup"><span data-stu-id="ac9f6-140">**Value**</span></span>|<span data-ttu-id="ac9f6-141">Type **HIS**.</span><span class="sxs-lookup"><span data-stu-id="ac9f6-141">Type **HIS**.</span></span>|  
  
    > [!NOTE]
    >  <span data-ttu-id="ac9f6-142">Le premier filtre spécifie que le port d’envoi sélectionne uniquement les messages qui se conforment à la req ^ schéma Q01 créé à l’étape 3 a.</span><span class="sxs-lookup"><span data-stu-id="ac9f6-142">The first filter specifies that the send port only selects messages conforming to the QRY^Q01 schema you created in step 3A.</span></span> <span data-ttu-id="ac9f6-143">Le deuxième filtre spécifie la destination à laquelle le [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Interface moteur envoie ces messages.</span><span class="sxs-lookup"><span data-stu-id="ac9f6-143">The second filter specifies the destination to which the [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Interface Engine sends these messages.</span></span>  
  
6.  <span data-ttu-id="ac9f6-144">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="ac9f6-144">Click **OK**.</span></span>  
  
7.  <span data-ttu-id="ac9f6-145">Dans la console d’Administration, sélectionnez **Ports d’envoi**, avec le bouton droit **HIS_Send**, puis cliquez sur **Démarrer**.</span><span class="sxs-lookup"><span data-stu-id="ac9f6-145">In the Administration console, select **Send Ports**, right-click **HIS_Send**, and then click **Start**.</span></span>  
  
 <span data-ttu-id="ac9f6-146">Passez à [étape 7 : créer un Port d’envoi pour remettre des Messages de réponse](../../adapters-and-accelerators/accelerator-hl7/step-7-create-a-send-port-to-deliver-response-messages.md).</span><span class="sxs-lookup"><span data-stu-id="ac9f6-146">Proceed to [Step 7: Create a Send Port to Deliver Response Messages](../../adapters-and-accelerators/accelerator-hl7/step-7-create-a-send-port-to-deliver-response-messages.md).</span></span>