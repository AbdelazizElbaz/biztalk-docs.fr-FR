---
title: "Étape 3D : ajouter un Port d’envoi FILE pour capturer le Message Sw:HandleResponse pour le scénario en temps réel d’interagir | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e05e4d20-4cf2-402f-aaea-66987cb6515a
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5a0c8c8721d9f7de7b1cd1e57537aa02d2ed8fd5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-3d-add-a-file-send-port-to-capture-the-swhandleresponse-message-for-the-interact-real-time-scenario"></a><span data-ttu-id="ff6d9-102">Étape 3D : ajouter un Port d’envoi FILE pour capturer le Message Sw:HandleResponse pour l’interaction du scénario en temps réel</span><span class="sxs-lookup"><span data-stu-id="ff6d9-102">Step 3D: Add a FILE Send Port to Capture the Sw:HandleResponse Message for the InterAct Real-Time Scenario</span></span>
<span data-ttu-id="ff6d9-103">Complète [étape 3c : ajouter un Port d’envoi FILE pour capturer le Message Sw:HandleRequest pour le scénario en temps réel interagir](../../adapters-and-accelerators/fileact-interact/step-3c-add-file-send-port-to-get-sw-handlerequest-interact-real-time-scenario.md) avant de commencer cette étape.</span><span class="sxs-lookup"><span data-stu-id="ff6d9-103">Complete [Step 3C: Add a FILE Send Port to Capture the Sw:HandleRequest Message for the InterAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-3c-add-file-send-port-to-get-sw-handlerequest-interact-real-time-scenario.md) before you begin this step.</span></span>
  
## <a name="add-a-file-send-port-to-capture-swhandleresponse-message"></a><span data-ttu-id="ff6d9-104">Ajouter un fichier de port d’envoi pour capturer les messages Sw:HandleResponse</span><span class="sxs-lookup"><span data-stu-id="ff6d9-104">Add a FILE send port to capture Sw:HandleResponse message</span></span>  
  
1.  <span data-ttu-id="ff6d9-105">Démarrer **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="ff6d9-105">Start **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="ff6d9-106">Dans l’arborescence de la console, développez le groupe BizTalk, puis développez l’application BizTalk pour laquelle vous souhaitez créer un port d’envoi.</span><span class="sxs-lookup"><span data-stu-id="ff6d9-106">In the console tree, expand the BizTalk group, and then expand the BizTalk application for which you want to create a send port.</span></span>  
  
3.  <span data-ttu-id="ff6d9-107">Avec le bouton droit **Ports d’envoi**, pointez sur **nouveau**, puis cliquez sur **Port d’envoi unidirectionnel statique.**</span><span class="sxs-lookup"><span data-stu-id="ff6d9-107">Right-click **Send Ports**, point to **New**, and then click **Static One-way Send Port.**</span></span>  
  
4.  <span data-ttu-id="ff6d9-108">Dans le **propriétés de Port d’envoi** fenêtre, le nom du port d’envoi **Tutorial_IA_SendResponseToSender**.</span><span class="sxs-lookup"><span data-stu-id="ff6d9-108">In the **Send Port Properties** window, name the send port **Tutorial_IA_SendResponseToSender**.</span></span>  
  
5.  <span data-ttu-id="ff6d9-109">Dans le **propriétés de Port d’envoi** fenêtre, à partir de la **Transporttype** la liste déroulante, sélectionnez **fichier**, puis cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="ff6d9-109">In the **Send Port Properties** window, from the **Transporttype** drop-down list, select **FILE**, and then click **Configure**.</span></span>  
  
6.  <span data-ttu-id="ff6d9-110">Dans le **propriétés du Transport FILE** boîte de dialogue le **dossier de Destination** , tapez **C:\SWIFTAdapterTutorial\Interact\Response**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="ff6d9-110">In the **FILE Transport Properties** dialog box, in the **Destination folder** box, type **C:\SWIFTAdapterTutorial\Interact\Response**, and then click **OK**.</span></span>  
  
7.  <span data-ttu-id="ff6d9-111">Dans le **propriétés de Port d’envoi** fenêtre, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="ff6d9-111">In the **Send Port Properties** window, do the following:</span></span>  
  
    |<span data-ttu-id="ff6d9-112">**Utilisez cette**</span><span class="sxs-lookup"><span data-stu-id="ff6d9-112">**Use this**</span></span>|<span data-ttu-id="ff6d9-113">**Pour ce faire**</span><span class="sxs-lookup"><span data-stu-id="ff6d9-113">**To do this**</span></span>|  
    |------------------|--------------------|  
    |<span data-ttu-id="ff6d9-114">**Gestionnaire d’envoi**</span><span class="sxs-lookup"><span data-stu-id="ff6d9-114">**Send handler**</span></span>|<span data-ttu-id="ff6d9-115">Dans la liste déroulante, sélectionnez **BizTalkServerApplication**.</span><span class="sxs-lookup"><span data-stu-id="ff6d9-115">From the drop-down list, select **BizTalkServerApplication**.</span></span>|  
    |<span data-ttu-id="ff6d9-116">**Pipeline d’envoi**</span><span class="sxs-lookup"><span data-stu-id="ff6d9-116">**Send pipeline**</span></span>|<span data-ttu-id="ff6d9-117">Dans la liste déroulante, sélectionnez **XMLTransmit**.</span><span class="sxs-lookup"><span data-stu-id="ff6d9-117">From the drop-down list, select **XMLTransmit**.</span></span>|  
  
8.  <span data-ttu-id="ff6d9-118">Dans le **propriétés de Port d’envoi** fenêtre, dans le **filtres** onglet, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="ff6d9-118">In the **Send Port Properties** window, on the **Filters** tab, do the following:</span></span>  
  
    |<span data-ttu-id="ff6d9-119">**Utilisez cette**</span><span class="sxs-lookup"><span data-stu-id="ff6d9-119">**Use this**</span></span>|<span data-ttu-id="ff6d9-120">**Pour ce faire**</span><span class="sxs-lookup"><span data-stu-id="ff6d9-120">**To do this**</span></span>|  
    |------------------|--------------------|  
    |<span data-ttu-id="ff6d9-121">Tout d’abord la ligne : **propriété**</span><span class="sxs-lookup"><span data-stu-id="ff6d9-121">First row: **Property**</span></span>|<span data-ttu-id="ff6d9-122">Dans la liste déroulante, sélectionnez **BTS. SPName**.</span><span class="sxs-lookup"><span data-stu-id="ff6d9-122">From the drop-down list, select **BTS.SPName**.</span></span>|  
    |<span data-ttu-id="ff6d9-123">Tout d’abord la ligne : **(opérateur)**</span><span class="sxs-lookup"><span data-stu-id="ff6d9-123">First row: **Operator**</span></span>|<span data-ttu-id="ff6d9-124">Dans la liste déroulante, sélectionnez  **==** .</span><span class="sxs-lookup"><span data-stu-id="ff6d9-124">From the drop-down list, select **==**.</span></span>|  
    |<span data-ttu-id="ff6d9-125">Tout d’abord la ligne : **valeur**</span><span class="sxs-lookup"><span data-stu-id="ff6d9-125">First row: **Value**</span></span>|<span data-ttu-id="ff6d9-126">Type **Tutorial_IA_HandleRequest_RealTime**.</span><span class="sxs-lookup"><span data-stu-id="ff6d9-126">Type **Tutorial_IA_HandleRequest_RealTime**.</span></span>|  
    |<span data-ttu-id="ff6d9-127">Tout d’abord la ligne : **regrouper par**</span><span class="sxs-lookup"><span data-stu-id="ff6d9-127">First row: **Group by**</span></span>|<span data-ttu-id="ff6d9-128">Dans la liste déroulante, sélectionnez **ou**.</span><span class="sxs-lookup"><span data-stu-id="ff6d9-128">From the drop-down list, select **OR**.</span></span>|  
    |<span data-ttu-id="ff6d9-129">Deuxième ligne : **propriété**</span><span class="sxs-lookup"><span data-stu-id="ff6d9-129">Second row: **Property**</span></span>|<span data-ttu-id="ff6d9-130">Dans la liste déroulante, sélectionnez **BTS. MessageType**.</span><span class="sxs-lookup"><span data-stu-id="ff6d9-130">From the drop-down list, select **BTS.MessageType**.</span></span>|  
    |<span data-ttu-id="ff6d9-131">Deuxième ligne : **(opérateur)**</span><span class="sxs-lookup"><span data-stu-id="ff6d9-131">Second row: **Operator**</span></span>|<span data-ttu-id="ff6d9-132">Dans la liste déroulante, sélectionnez  **==** .</span><span class="sxs-lookup"><span data-stu-id="ff6d9-132">From the drop-down list, select **==**.</span></span>|  
    |<span data-ttu-id="ff6d9-133">Deuxième ligne : **valeur**</span><span class="sxs-lookup"><span data-stu-id="ff6d9-133">Second row: **Value**</span></span>|<span data-ttu-id="ff6d9-134">Type **SwInt-ExchangeResponse**.</span><span class="sxs-lookup"><span data-stu-id="ff6d9-134">Type **SwInt-ExchangeResponse**.</span></span>|  
    |<span data-ttu-id="ff6d9-135">Deuxième ligne : **regrouper par**</span><span class="sxs-lookup"><span data-stu-id="ff6d9-135">Second row: **Group by**</span></span>|<span data-ttu-id="ff6d9-136">Laissez la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="ff6d9-136">Leave the default value.</span></span>|  
  
9. <span data-ttu-id="ff6d9-137">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="ff6d9-137">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff6d9-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ff6d9-138">See Also</span></span>  
 <span data-ttu-id="ff6d9-139">[Étape 3 : Créer l’envoi et Ports de réception l’interaction du scénario en temps réel](../../adapters-and-accelerators/fileact-interact/step-3-create-send-and-receive-ports-for-the-interact-real-time-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="ff6d9-139">[Step 3: Create Send and Receive Ports for the InterAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-3-create-send-and-receive-ports-for-the-interact-real-time-scenario.md) </span></span>  
 <span data-ttu-id="ff6d9-140">[Étape 3 a : ajouter un fichier emplacement de réception pour l’interaction du scénario en temps réel](../../adapters-and-accelerators/fileact-interact/step-3a-add-a-file-receive-location-for-the-interact-real-time-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="ff6d9-140">[Step 3A: Add a FILE Receive Location for the InterAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-3a-add-a-file-receive-location-for-the-interact-real-time-scenario.md) </span></span>  
 <span data-ttu-id="ff6d9-141">[Étape 3 b : ajouter un interagir emplacement de réception pour l’interaction scénario en temps réel](../../adapters-and-accelerators/fileact-interact/step-3b-add-an-interact-receive-location-for-the-interact-real-time-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="ff6d9-141">[Step 3B: Add an INTERACT Receive Location for the InterAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-3b-add-an-interact-receive-location-for-the-interact-real-time-scenario.md) </span></span>  
 <span data-ttu-id="ff6d9-142">[Étape 3c : ajouter un Port d’envoi FILE pour capturer le Message Sw:HandleRequest pour l’interaction du scénario en temps réel](../../adapters-and-accelerators/fileact-interact/step-3c-add-file-send-port-to-get-sw-handlerequest-interact-real-time-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="ff6d9-142">[Step 3C: Add a FILE Send Port to Capture the Sw:HandleRequest Message for the InterAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-3c-add-file-send-port-to-get-sw-handlerequest-interact-real-time-scenario.md) </span></span>  
 [<span data-ttu-id="ff6d9-143">Étape 3E : ajouter un Port d’envoi interagir pour l’interaction scénario en temps réel</span><span class="sxs-lookup"><span data-stu-id="ff6d9-143">Step 3E: Add an INTERACT Send Port for the InterAct Real-Time Scenario</span></span>](../../adapters-and-accelerators/fileact-interact/step-3e-add-an-interact-send-port-for-the-interact-real-time-scenario.md)