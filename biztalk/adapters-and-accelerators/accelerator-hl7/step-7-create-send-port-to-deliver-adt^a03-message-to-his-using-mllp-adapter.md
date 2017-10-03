---
title: "Étape 7 : Créer un Port d’envoi pour remettre le ADT ^ Message A03 à son à l’aide de l’adaptateur MLLP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- end-to-end tutorial, send ports
- creating, send ports
- send ports, creating
ms.assetid: d9e7f281-3d25-4675-a13e-0e2057f5e69a
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fc122ab37ee0d618c3bd75792a5b88571dd49162
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-7-create-a-send-port-to-deliver-the-adta03-message-to-his-using-the-mllp-adapter"></a><span data-ttu-id="3ee72-102">Étape 7 : Créer un Port d’envoi pour remettre le ADT ^ Message A03 à son à l’aide de l’adaptateur MLLP</span><span class="sxs-lookup"><span data-stu-id="3ee72-102">Step 7: Create a Send Port to Deliver the ADT^A03 Message to HIS Using the MLLP Adapter</span></span>
<span data-ttu-id="3ee72-103">Dans cette étape, vous créez le port d’envoi pour envoyer le message à l’hôpital informations système HIS () à l’aide de l’adaptateur MLLP.</span><span class="sxs-lookup"><span data-stu-id="3ee72-103">In this step, you create the send port to send the message to the Hospital Information System (HIS) using the MLLP adapter.</span></span>  
  
### <a name="to-create-the-tutorialmllpsend-send-port"></a><span data-ttu-id="3ee72-104">Pour créer le port d’envoi Tutorial_MllpSend</span><span class="sxs-lookup"><span data-stu-id="3ee72-104">To create the Tutorial_MllpSend send port</span></span>  
  
1.  <span data-ttu-id="3ee72-105">Dans la Console Administration de BizTalk Server, cliquez sur **Ports d’envoi**, pointez sur **nouveau**, puis cliquez sur **Port d’envoi unidirectionnel statique**.</span><span class="sxs-lookup"><span data-stu-id="3ee72-105">In the BizTalk Server Administration Console, right-click **Send Ports**, point to **New**, and then click **Static One-way Send Port**.</span></span>  
  
2.  <span data-ttu-id="3ee72-106">Dans la boîte de dialogue Propriétés de Port d’envoi, effectuez les actions suivantes :</span><span class="sxs-lookup"><span data-stu-id="3ee72-106">In the Send Port Properties dialog box, do the following actions:</span></span>  
  
    |<span data-ttu-id="3ee72-107">Utiliser</span><span class="sxs-lookup"><span data-stu-id="3ee72-107">Use this</span></span>|<span data-ttu-id="3ee72-108">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="3ee72-108">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="3ee72-109">**Nom**</span><span class="sxs-lookup"><span data-stu-id="3ee72-109">**Name**</span></span>|<span data-ttu-id="3ee72-110">Type **Tutorial_MllpSend**.</span><span class="sxs-lookup"><span data-stu-id="3ee72-110">Type **Tutorial_MllpSend**.</span></span>|  
    |<span data-ttu-id="3ee72-111">**Type de transport**</span><span class="sxs-lookup"><span data-stu-id="3ee72-111">**Transport type**</span></span>|<span data-ttu-id="3ee72-112">Sélectionnez **MLLP** dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="3ee72-112">Select **MLLP** from the drop-down list.</span></span>|  
    |<span data-ttu-id="3ee72-113">**Configurer**</span><span class="sxs-lookup"><span data-stu-id="3ee72-113">**Configure**</span></span>|<span data-ttu-id="3ee72-114">Cliquez sur **configurer** pour ouvrir le **propriétés du Transport MLLP** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="3ee72-114">Click **Configure** to open the **MLLP Transport Properties** dialog box.</span></span>|  
  
3.  <span data-ttu-id="3ee72-115">Dans la boîte de dialogue Propriétés du Transport MLLP, effectuez les actions suivantes, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="3ee72-115">In the MLLP Transport Properties dialog box, do the following actions and then click **OK**.</span></span>  
  
    |<span data-ttu-id="3ee72-116">Utiliser</span><span class="sxs-lookup"><span data-stu-id="3ee72-116">Use this</span></span>|<span data-ttu-id="3ee72-117">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="3ee72-117">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="3ee72-118">**Nom de la connexion**</span><span class="sxs-lookup"><span data-stu-id="3ee72-118">**Connection Name**</span></span>|<span data-ttu-id="3ee72-119">Type **1WaySend**.</span><span class="sxs-lookup"><span data-stu-id="3ee72-119">Type **1WaySend**.</span></span>|  
    |<span data-ttu-id="3ee72-120">**Hôte**</span><span class="sxs-lookup"><span data-stu-id="3ee72-120">**Host**</span></span>|<span data-ttu-id="3ee72-121">Type **localhost**.</span><span class="sxs-lookup"><span data-stu-id="3ee72-121">Type **localhost**.</span></span>|  
    |<span data-ttu-id="3ee72-122">**Port**</span><span class="sxs-lookup"><span data-stu-id="3ee72-122">**Port**</span></span>|<span data-ttu-id="3ee72-123">Type **14000**.</span><span class="sxs-lookup"><span data-stu-id="3ee72-123">Type **14000**.</span></span>|  
  
4.  <span data-ttu-id="3ee72-124">Dans la boîte de dialogue Propriétés de Port d’envoi pour **Pipeline d’envoi**, sélectionnez **BTAHL72XPipelines.BTAHL72XSendPipeline**.</span><span class="sxs-lookup"><span data-stu-id="3ee72-124">In the Send Port Properties dialog box, for **Send Pipeline**, select **BTAHL72XPipelines.BTAHL72XSendPipeline**.</span></span>  
  
5.  <span data-ttu-id="3ee72-125">Dans le volet gauche, sélectionnez **filtres**, puis procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="3ee72-125">In the left pane, select **Filters**, and then do the following:</span></span>  
  
    |<span data-ttu-id="3ee72-126">Utiliser</span><span class="sxs-lookup"><span data-stu-id="3ee72-126">Use this</span></span>|<span data-ttu-id="3ee72-127">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="3ee72-127">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="3ee72-128">**Propriété**</span><span class="sxs-lookup"><span data-stu-id="3ee72-128">**Property**</span></span>|<span data-ttu-id="3ee72-129">Sélectionnez **BTS. ReceivePortName** dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="3ee72-129">Select **BTS.ReceivePortName** from the drop-down list.</span></span>|  
    |<span data-ttu-id="3ee72-130">**Opérateur**</span><span class="sxs-lookup"><span data-stu-id="3ee72-130">**Operator**</span></span>|<span data-ttu-id="3ee72-131">Sélectionnez  **==**  dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="3ee72-131">Select **==** from the drop-down list.</span></span>|  
    |<span data-ttu-id="3ee72-132">**Valeur**</span><span class="sxs-lookup"><span data-stu-id="3ee72-132">**Value**</span></span>|<span data-ttu-id="3ee72-133">Type **Tutorial_1WayReceive**.</span><span class="sxs-lookup"><span data-stu-id="3ee72-133">Type **Tutorial_1WayReceive**.</span></span>|  
  
    > [!NOTE]
    >  <span data-ttu-id="3ee72-134">Le port d’écoute le port spécifié dans 1WayReceive pour tous les messages.</span><span class="sxs-lookup"><span data-stu-id="3ee72-134">The port will listen to the port specified in 1WayReceive for any messages.</span></span>  
  
6.  <span data-ttu-id="3ee72-135">Cliquez sur **appliquer**, puis cliquez sur **OK.**</span><span class="sxs-lookup"><span data-stu-id="3ee72-135">Click **Apply**, and then click **OK.**</span></span>  
  
7.  <span data-ttu-id="3ee72-136">Dans la Console d’Administration, cliquez sur **Ports d’envoi**, avec le bouton droit **Tutorial_MllpSend**, puis cliquez sur **Démarrer**.</span><span class="sxs-lookup"><span data-stu-id="3ee72-136">In the Administration Console, click **Send Ports**, right-click **Tutorial_MllpSend**, and then click **Start**.</span></span>  
  
 <span data-ttu-id="3ee72-137">Passez à [étape 8 : configurer les informations de tiers](../../adapters-and-accelerators/accelerator-hl7/step-8-configure-party-information.md).</span><span class="sxs-lookup"><span data-stu-id="3ee72-137">Proceed to [Step 8: Configure Party Information](../../adapters-and-accelerators/accelerator-hl7/step-8-configure-party-information.md).</span></span>