---
title: "Étape 7 : Créer un Port d’envoi pour remettre des Messages de réponse | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: interrogative tutorial, send ports
ms.assetid: 5edaefb6-72f2-4317-9477-f3a0d0027e0c
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1260772f3b3df5f0dea96b0aa66023e107b9aa6c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-7-create-a-send-port-to-deliver-response-messages"></a><span data-ttu-id="d56db-102">Étape 7 : Créer un Port d’envoi pour remettre des Messages de réponse</span><span class="sxs-lookup"><span data-stu-id="d56db-102">Step 7: Create a Send Port to Deliver Response Messages</span></span>
<span data-ttu-id="d56db-103">Dans cette étape, vous créez le port d’envoi pour fournir les réponses de requêtes l’admission, rejet, et transférer (ADT) système.</span><span class="sxs-lookup"><span data-stu-id="d56db-103">In this step, you create the send port to deliver the query responses back to the Admissions, Discharge, and Transfer (ADT) system.</span></span>  
  
### <a name="to-create-the-adtsend-send-port"></a><span data-ttu-id="d56db-104">Pour créer le port d’envoi ADT_Send</span><span class="sxs-lookup"><span data-stu-id="d56db-104">To create the ADT_Send send port</span></span>  
  
1.  <span data-ttu-id="d56db-105">Dans la Console Administration de BizTalk Server, cliquez sur **Ports d’envoi**, pointez sur **nouveau**, puis sélectionnez **Port d’envoi unidirectionnel statique**.</span><span class="sxs-lookup"><span data-stu-id="d56db-105">In the BizTalk Server Administration Console, right-click **Send Ports**, point to **New**, and then select **Static One-way Send Port**.</span></span>  
  
2.  <span data-ttu-id="d56db-106">Dans la boîte de dialogue Propriétés de Port d’envoi, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="d56db-106">In the Send Port Properties dialog box, do the following:</span></span>  
  
    |<span data-ttu-id="d56db-107">Utiliser</span><span class="sxs-lookup"><span data-stu-id="d56db-107">Use this</span></span>|<span data-ttu-id="d56db-108">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="d56db-108">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="d56db-109">**Nom**</span><span class="sxs-lookup"><span data-stu-id="d56db-109">**Name**</span></span>|<span data-ttu-id="d56db-110">Type **ADT_Send**.</span><span class="sxs-lookup"><span data-stu-id="d56db-110">Type **ADT_Send**.</span></span>|  
    |<span data-ttu-id="d56db-111">**Type de transport**</span><span class="sxs-lookup"><span data-stu-id="d56db-111">**Transport type**</span></span>|<span data-ttu-id="d56db-112">Sélectionnez **MLLP**.</span><span class="sxs-lookup"><span data-stu-id="d56db-112">Select **MLLP**.</span></span>|  
    |<span data-ttu-id="d56db-113">**Configurer**</span><span class="sxs-lookup"><span data-stu-id="d56db-113">**Configure**</span></span>|<span data-ttu-id="d56db-114">Cliquez sur le **configurer** bouton à droite de **Type**.</span><span class="sxs-lookup"><span data-stu-id="d56db-114">Click the **Configure** button to the right of **Type**.</span></span>|  
  
3.  <span data-ttu-id="d56db-115">Dans la boîte de dialogue Propriétés du Transport MLLP, entrez les informations suivantes, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="d56db-115">In the MLLP Transport Properties dialog box, enter the following information, and then click **OK**.</span></span>  
  
    |<span data-ttu-id="d56db-116">Utiliser</span><span class="sxs-lookup"><span data-stu-id="d56db-116">Use this</span></span>|<span data-ttu-id="d56db-117">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="d56db-117">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="d56db-118">**Nom de la connexion**</span><span class="sxs-lookup"><span data-stu-id="d56db-118">**Connection Name**</span></span>|<span data-ttu-id="d56db-119">Type **ADT_SendMLLP**.</span><span class="sxs-lookup"><span data-stu-id="d56db-119">Type **ADT_SendMLLP**.</span></span>|  
    |<span data-ttu-id="d56db-120">**Hôte**</span><span class="sxs-lookup"><span data-stu-id="d56db-120">**Host**</span></span>|<span data-ttu-id="d56db-121">Type **localhost**.</span><span class="sxs-lookup"><span data-stu-id="d56db-121">Type **localhost**.</span></span>|  
    |<span data-ttu-id="d56db-122">**Port**</span><span class="sxs-lookup"><span data-stu-id="d56db-122">**Port**</span></span>|<span data-ttu-id="d56db-123">Type **25000**.</span><span class="sxs-lookup"><span data-stu-id="d56db-123">Type **25000**.</span></span>|  
  
4.  <span data-ttu-id="d56db-124">Dans la boîte de dialogue Propriétés de Port d’envoi pour **Pipeline d’envoi**, sélectionnez **BTAHL72XPipelines.BTAHL72XSendPipeline**.</span><span class="sxs-lookup"><span data-stu-id="d56db-124">In the Send Port Properties dialog box, for **Send Pipeline**, select **BTAHL72XPipelines.BTAHL72XSendPipeline**.</span></span>  
  
5.  <span data-ttu-id="d56db-125">Dans l’arborescence de la Console, cliquez sur **filtres**, puis procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="d56db-125">In the Console Tree, click **Filters**, and then do the following:</span></span>  
  
    |<span data-ttu-id="d56db-126">Utiliser</span><span class="sxs-lookup"><span data-stu-id="d56db-126">Use this</span></span>|<span data-ttu-id="d56db-127">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="d56db-127">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="d56db-128">**Propriété**</span><span class="sxs-lookup"><span data-stu-id="d56db-128">**Property**</span></span>|<span data-ttu-id="d56db-129">Sélectionnez **BTS. MessageType**.</span><span class="sxs-lookup"><span data-stu-id="d56db-129">Select **BTS.MessageType**.</span></span>|  
    |<span data-ttu-id="d56db-130">**Opérateur**</span><span class="sxs-lookup"><span data-stu-id="d56db-130">**Operator**</span></span>|<span data-ttu-id="d56db-131">Sélectionnez  **==**  dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="d56db-131">Select **==** from the drop-down list.</span></span>|  
    |<span data-ttu-id="d56db-132">**Valeur**</span><span class="sxs-lookup"><span data-stu-id="d56db-132">**Value**</span></span>|<span data-ttu-id="d56db-133">Type **http://microsoft.com/HealthCare/HL7/2X#DSR_Q01_24_GLO_DEF**.</span><span class="sxs-lookup"><span data-stu-id="d56db-133">Type **http://microsoft.com/HealthCare/HL7/2X#DSR_Q01_24_GLO_DEF**.</span></span>|  
    |<span data-ttu-id="d56db-134">**Regrouper par**</span><span class="sxs-lookup"><span data-stu-id="d56db-134">**Group By**</span></span>|<span data-ttu-id="d56db-135">Sélectionnez **et** dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="d56db-135">Select **AND** from the drop-down list.</span></span>|  
    |<span data-ttu-id="d56db-136">**Propriété**</span><span class="sxs-lookup"><span data-stu-id="d56db-136">**Property**</span></span>|<span data-ttu-id="d56db-137">Dans la première propriété, cliquez sur la zone vierge, puis **BTAHL7Schemas.MSH5_1**.</span><span class="sxs-lookup"><span data-stu-id="d56db-137">Under the first property, click the blank box, and then select **BTAHL7Schemas.MSH5_1**.</span></span>|  
    |<span data-ttu-id="d56db-138">**Opérateur**</span><span class="sxs-lookup"><span data-stu-id="d56db-138">**Operator**</span></span>|<span data-ttu-id="d56db-139">Sélectionnez  **==**  dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="d56db-139">Select **==** from the drop-down list.</span></span>|  
    |<span data-ttu-id="d56db-140">**Valeur**</span><span class="sxs-lookup"><span data-stu-id="d56db-140">**Value**</span></span>|<span data-ttu-id="d56db-141">Type **ADT**.</span><span class="sxs-lookup"><span data-stu-id="d56db-141">Type **ADT**.</span></span>|  
  
    > [!NOTE]
    >  <span data-ttu-id="d56db-142">Le premier filtre spécifie que le port d’envoi sélectionne uniquement les messages conformes au DSR ^ schéma Q01 créé à l’étape 3 a.</span><span class="sxs-lookup"><span data-stu-id="d56db-142">The first filter specifies that the send port only selects messages conforming to the DSR^Q01 schema you created in step 3A.</span></span> <span data-ttu-id="d56db-143">Le deuxième filtre spécifie la destination à laquelle le [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Interface moteur envoie ces messages.</span><span class="sxs-lookup"><span data-stu-id="d56db-143">The second filter specifies the destination to which the [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Interface Engine sends these messages.</span></span>  
  
6.  <span data-ttu-id="d56db-144">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="d56db-144">Click **OK**.</span></span>  
  
7.  <span data-ttu-id="d56db-145">Dans la Console d’Administration, cliquez sur **Ports d’envoi**, avec le bouton droit **ADT_Send**, puis cliquez sur **Démarrer**.</span><span class="sxs-lookup"><span data-stu-id="d56db-145">In the Administration Console, click **Send Ports**, right-click **ADT_Send**, and then click **Start**.</span></span>  
  
 <span data-ttu-id="d56db-146">Passez à [étape 8 : configurer les informations de tiers](../../adapters-and-accelerators/accelerator-hl7/step-8-configure-party-information-hl7-main.md).</span><span class="sxs-lookup"><span data-stu-id="d56db-146">Proceed to [Step 8: Configure Party Information](../../adapters-and-accelerators/accelerator-hl7/step-8-configure-party-information-hl7-main.md).</span></span>