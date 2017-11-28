---
title: "Étape 3E : ajouter un Port d’envoi FILE pour capturer les messages Sw:ExchangeFileResponse pour le scénario en temps réel FileAct | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b9314f86-a2c9-4ef3-8474-b7e2e2f8bf66
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 18e26d13196a46045191b9e5767040e2216ceba2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-3e-add-a-file-send-port-to-capture-swexchangefileresponse-message-for-the-fileact-real-time-scenario"></a><span data-ttu-id="4c7b3-102">Étape 3E : ajouter un Port d’envoi FILE pour capturer les messages Sw:ExchangeFileResponse pour le scénario en temps réel FileAct</span><span class="sxs-lookup"><span data-stu-id="4c7b3-102">Step 3E: Add a FILE Send Port to Capture Sw:ExchangeFileResponse Message for the FileAct Real-Time Scenario</span></span>
<span data-ttu-id="4c7b3-103">Avant de commencer cette étape, vous devez effectuer [étape 3D : ajouter un Port d’envoi FILEACT pour le scénario en temps réel de FileAct](../../adapters-and-accelerators/fileact-interact/step-3d-add-a-fileact-send-port-for-the-fileact-real-time-scenario.md).</span><span class="sxs-lookup"><span data-stu-id="4c7b3-103">Before you begin this step, you must complete [Step 3D: Add a FILEACT Send Port for the FileAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-3d-add-a-fileact-send-port-for-the-fileact-real-time-scenario.md).</span></span>  
  
### <a name="to-add-a-file-send-port-to-capture-swexchangefileresponse-message"></a><span data-ttu-id="4c7b3-104">Pour ajouter un fichier de port d’envoi pour capturer les messages Sw:ExchangeFileResponse</span><span class="sxs-lookup"><span data-stu-id="4c7b3-104">To add a FILE send port to capture Sw:ExchangeFileResponse message</span></span>  
  
1.  <span data-ttu-id="4c7b3-105">Démarrer **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="4c7b3-105">Start **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="4c7b3-106">Dans l’arborescence de la console, développez le groupe BizTalk, puis développez l’application BizTalk pour laquelle vous souhaitez créer un port d’envoi.</span><span class="sxs-lookup"><span data-stu-id="4c7b3-106">In the console tree, expand the BizTalk group, and then expand the BizTalk application for which you want to create a send port.</span></span>  
  
3.  <span data-ttu-id="4c7b3-107">Avec le bouton droit **Ports d’envoi**, pointez sur **nouveau**, puis cliquez sur **Port d’envoi unidirectionnel statique.**</span><span class="sxs-lookup"><span data-stu-id="4c7b3-107">Right-click **Send Ports**, point to **New**, and then click **Static One-way Send Port.**</span></span>  
  
4.  <span data-ttu-id="4c7b3-108">Dans le **propriétés de Port d’envoi** fenêtre, le nom du port d’envoi Tutorial_FA_SendResponseToSender.</span><span class="sxs-lookup"><span data-stu-id="4c7b3-108">In the **Send Port Properties** window, name the send port, Tutorial_FA_SendResponseToSender.</span></span>  
  
5.  <span data-ttu-id="4c7b3-109">Dans le **propriétés de Port d’envoi** fenêtre, à partir de la **type de Transport** la liste déroulante, sélectionnez **fichier**, puis cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="4c7b3-109">In the **Send Port Properties** window, from the **Transport type** drop-down list, select **FILE**, and then click **Configure**.</span></span>  
  
6.  <span data-ttu-id="4c7b3-110">Dans le **propriétés du Transport FILE** boîte de dialogue le **dossier de Destination** zone, tapez C:\SWIFTAdapterTutorial\Fileact\ResponseClient, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="4c7b3-110">In the **FILE Transport Properties** dialog box, in the **Destination folder** box, type C:\SWIFTAdapterTutorial\Fileact\ResponseClient, and then click **OK**.</span></span>  
  
7.  <span data-ttu-id="4c7b3-111">Dans le **propriétés de Port d’envoi** fenêtre, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="4c7b3-111">In the **Send Port Properties** window, do the following:</span></span>  
  
    |<span data-ttu-id="4c7b3-112">**Utilisez cette**</span><span class="sxs-lookup"><span data-stu-id="4c7b3-112">**Use this**</span></span>|<span data-ttu-id="4c7b3-113">**Pour ce faire**</span><span class="sxs-lookup"><span data-stu-id="4c7b3-113">**To do this**</span></span>|  
    |------------------|--------------------|  
    |<span data-ttu-id="4c7b3-114">**Gestionnaire d’envoi**</span><span class="sxs-lookup"><span data-stu-id="4c7b3-114">**Send handler**</span></span>|<span data-ttu-id="4c7b3-115">Dans la liste déroulante, sélectionnez **BizTalkServerApplication**.</span><span class="sxs-lookup"><span data-stu-id="4c7b3-115">From the drop-down list, select **BizTalkServerApplication**.</span></span>|  
    |<span data-ttu-id="4c7b3-116">**Pipeline d’envoi**</span><span class="sxs-lookup"><span data-stu-id="4c7b3-116">**Send pipeline**</span></span>|<span data-ttu-id="4c7b3-117">Dans la liste déroulante, sélectionnez **XMLTransmit**.</span><span class="sxs-lookup"><span data-stu-id="4c7b3-117">From the drop-down list, select **XMLTransmit**.</span></span>|  
  
8.  <span data-ttu-id="4c7b3-118">Dans le **propriétés de Port d’envoi** fenêtre, dans le **filtres** onglet, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="4c7b3-118">In the **Send Port Properties** window, on the **Filters** tab, do the following:</span></span>  
  
    |<span data-ttu-id="4c7b3-119">**Utilisez cette**</span><span class="sxs-lookup"><span data-stu-id="4c7b3-119">**Use this**</span></span>|<span data-ttu-id="4c7b3-120">**Pour ce faire**</span><span class="sxs-lookup"><span data-stu-id="4c7b3-120">**To do this**</span></span>|  
    |------------------|--------------------|  
    |<span data-ttu-id="4c7b3-121">**Propriété**</span><span class="sxs-lookup"><span data-stu-id="4c7b3-121">**Property**</span></span>|<span data-ttu-id="4c7b3-122">Dans la liste déroulante, sélectionnez **BTS. SPName**.</span><span class="sxs-lookup"><span data-stu-id="4c7b3-122">From the drop-down list, select **BTS.SPName**.</span></span>|  
    |<span data-ttu-id="4c7b3-123">**Opérateur**</span><span class="sxs-lookup"><span data-stu-id="4c7b3-123">**Operator**</span></span>|<span data-ttu-id="4c7b3-124">Dans la liste déroulante, sélectionnez  **==** .</span><span class="sxs-lookup"><span data-stu-id="4c7b3-124">From the drop-down list, select **==**.</span></span>|  
    |<span data-ttu-id="4c7b3-125">**Valeur**</span><span class="sxs-lookup"><span data-stu-id="4c7b3-125">**Value**</span></span>|<span data-ttu-id="4c7b3-126">Type Tutorial_FA_SendRequest_RealTime.</span><span class="sxs-lookup"><span data-stu-id="4c7b3-126">Type Tutorial_FA_SendRequest_RealTime.</span></span>|  
    |<span data-ttu-id="4c7b3-127">**Regrouper par**</span><span class="sxs-lookup"><span data-stu-id="4c7b3-127">**Group by**</span></span>|<span data-ttu-id="4c7b3-128">Laissez la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="4c7b3-128">Leave the default value.</span></span>|  
  
9. <span data-ttu-id="4c7b3-129">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="4c7b3-129">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c7b3-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4c7b3-130">See Also</span></span>  
 <span data-ttu-id="4c7b3-131">[Étape 3 : Créer les Ports d’envoi et Ports de réception pour le scénario en temps réel FileAct](../../adapters-and-accelerators/fileact-interact/step-3-create-the-send-ports-and-receive-ports-for-fileact-real-time-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="4c7b3-131">[Step 3: Create the Send Ports and Receive Ports for the FileAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-3-create-the-send-ports-and-receive-ports-for-fileact-real-time-scenario.md) </span></span>  
 <span data-ttu-id="4c7b3-132">[Étape 3 a : ajouter un fichier emplacement de réception pour le scénario en temps réel FileAct](../../adapters-and-accelerators/fileact-interact/step-3a-add-a-file-receive-location-for-the-fileact-real-time-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="4c7b3-132">[Step 3A: Add a FILE Receive Location for the FileAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-3a-add-a-file-receive-location-for-the-fileact-real-time-scenario.md) </span></span>  
 <span data-ttu-id="4c7b3-133">[Étape 3 b : ajouter un FILEACT emplacement de réception pour le scénario en temps réel FileAct](../../adapters-and-accelerators/fileact-interact/step-3b-add-a-fileact-receive-location-for-the-fileact-real-time-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="4c7b3-133">[Step 3B: Add a FILEACT Receive Location for the FileAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-3b-add-a-fileact-receive-location-for-the-fileact-real-time-scenario.md) </span></span>  
 <span data-ttu-id="4c7b3-134">[Étape 3c : ajouter un Port d’envoi FILE pour capturer les messages Sw:HandleRequest pour le scénario en temps réel FileAct](../../adapters-and-accelerators/fileact-interact/step-3c-add-file-send-port-to-get-sw-handlerequest-message-for-fileact.md) </span><span class="sxs-lookup"><span data-stu-id="4c7b3-134">[Step 3C: Add a FILE Send Port to Capture Sw:HandleRequest Message for the FileAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-3c-add-file-send-port-to-get-sw-handlerequest-message-for-fileact.md) </span></span>  
 [<span data-ttu-id="4c7b3-135">Étape 3D : ajouter un Port d’envoi FILEACT pour le scénario en temps réel FileAct</span><span class="sxs-lookup"><span data-stu-id="4c7b3-135">Step 3D: Add a FILEACT Send Port for the FileAct Real-Time Scenario</span></span>](../../adapters-and-accelerators/fileact-interact/step-3d-add-a-fileact-send-port-for-the-fileact-real-time-scenario.md)