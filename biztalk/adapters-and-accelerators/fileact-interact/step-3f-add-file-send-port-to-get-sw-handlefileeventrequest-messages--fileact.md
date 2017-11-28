---
title: "Étape 3 : ajouter un Port d’envoi de fichier pour le scénario en temps réel FileAct capturer les Messages Sw-HandleFileEventRequest | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0b7594b0-0443-41b7-ae04-55b2cc8bf90e
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b1d70c338696f1c4455161a88c8d2988e0ea0ccb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-3f-add-a-file-send-port-for-the-fileact-real-time-scenario-to-capture-sw-handlefileeventrequest-messages"></a><span data-ttu-id="f229c-102">Étape 3 : ajouter un Port d’envoi de fichier pour le scénario en temps réel FileAct capturer les Messages Sw-HandleFileEventRequest</span><span class="sxs-lookup"><span data-stu-id="f229c-102">Step 3F: Add a FILE Send Port for the FileAct Real-Time Scenario to Capture Sw-HandleFileEventRequest Messages</span></span>
<span data-ttu-id="f229c-103">Avant de commencer cette étape, vous devez effectuer [étape 3E : ajouter un Port d’envoi FILE à capturer le Message Sw:ExchangeFileResponse pour le scénario en temps réel de FileAct](../../adapters-and-accelerators/fileact-interact/step-3e-add-file-send-port-to-get-sw-exchangefileresponse-message-for-fileact.md)</span><span class="sxs-lookup"><span data-stu-id="f229c-103">Before you begin this step, you must complete [Step 3E: Add a FILE Send Port to Capture Sw:ExchangeFileResponse Message for the FileAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-3e-add-file-send-port-to-get-sw-exchangefileresponse-message-for-fileact.md)</span></span>  
  
### <a name="to-add-a-file-send-port-to-capture-status-events"></a><span data-ttu-id="f229c-104">Pour ajouter un port d’envoi FILE pour capturer les événements d’état :</span><span class="sxs-lookup"><span data-stu-id="f229c-104">To add a FILE send port to capture Status Events:</span></span>  
  
1.  <span data-ttu-id="f229c-105">Démarrer **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="f229c-105">Start **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="f229c-106">Dans l’arborescence de la console, développez le groupe BizTalk, puis développez l’application BizTalk pour laquelle vous souhaitez créer un port d’envoi.</span><span class="sxs-lookup"><span data-stu-id="f229c-106">In the console tree, expand the BizTalk group, and then expand the BizTalk application for which you want to create a send port.</span></span>  
  
3.  <span data-ttu-id="f229c-107">Avec le bouton droit **Ports d’envoi**, pointez sur **nouveau**, puis cliquez sur **Port d’envoi unidirectionnel statique**.</span><span class="sxs-lookup"><span data-stu-id="f229c-107">Right-click **Send Ports**, point to **New**, and then click **Static One-way Send Port**.</span></span>  
  
4.  <span data-ttu-id="f229c-108">Dans le **propriétés de Port d’envoi** fenêtre, le nom du port d’envoi Tutorial_ GetStatusReports.</span><span class="sxs-lookup"><span data-stu-id="f229c-108">In the **Send Port Properties** window, name the send port, Tutorial_ GetStatusReports.</span></span>  
  
5.  <span data-ttu-id="f229c-109">Dans le **propriétés de Port d’envoi** fenêtre, à partir de la **type de Transport** la liste déroulante, sélectionnez **fichier**, puis cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="f229c-109">In the **Send Port Properties** window, from the **Transport type** drop-down list, select **FILE**, and then click **Configure**.</span></span>  
  
6.  <span data-ttu-id="f229c-110">Dans le **propriétés du Transport FILE** boîte de dialogue le **dossier de Destination** zone, tapez C:\SWIFTAdapterTutorial\Fileact\ StatusEvents, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="f229c-110">In the **FILE Transport Properties** dialog box, in the **Destination folder** box, type C:\SWIFTAdapterTutorial\Fileact\ StatusEvents, and then click **OK**.</span></span>  
  
7.  <span data-ttu-id="f229c-111">Dans le **propriétés de Port d’envoi** fenêtre, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="f229c-111">In the **Send Port Properties** window, do the following:</span></span>  
  
    |<span data-ttu-id="f229c-112">**Utilisez cette**</span><span class="sxs-lookup"><span data-stu-id="f229c-112">**Use this**</span></span>|<span data-ttu-id="f229c-113">**Pour ce faire**</span><span class="sxs-lookup"><span data-stu-id="f229c-113">**To do this**</span></span>|  
    |------------------|--------------------|  
    |<span data-ttu-id="f229c-114">**Gestionnaire d’envoi**</span><span class="sxs-lookup"><span data-stu-id="f229c-114">**Send handler**</span></span>|<span data-ttu-id="f229c-115">Dans la liste déroulante, sélectionnez **BizTalkServerApplication**.</span><span class="sxs-lookup"><span data-stu-id="f229c-115">From the drop-down list, select **BizTalkServerApplication**.</span></span>|  
    |<span data-ttu-id="f229c-116">**Pipeline d’envoi**</span><span class="sxs-lookup"><span data-stu-id="f229c-116">**Send pipeline**</span></span>|<span data-ttu-id="f229c-117">Dans la liste déroulante, sélectionnez **XMLTransmit**.</span><span class="sxs-lookup"><span data-stu-id="f229c-117">From the drop-down list, select **XMLTransmit**.</span></span>|  
  
8.  <span data-ttu-id="f229c-118">Dans le **propriétés de Port d’envoi** fenêtre, dans le **filtres** onglet, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="f229c-118">In the **Send Port Properties** window, on the **Filters** tab, do the following:</span></span>  
  
    |<span data-ttu-id="f229c-119">**Utilisez cette**</span><span class="sxs-lookup"><span data-stu-id="f229c-119">**Use this**</span></span>|<span data-ttu-id="f229c-120">**Pour ce faire**</span><span class="sxs-lookup"><span data-stu-id="f229c-120">**To do this**</span></span>|  
    |------------------|--------------------|  
    |<span data-ttu-id="f229c-121">**Propriété**</span><span class="sxs-lookup"><span data-stu-id="f229c-121">**Property**</span></span>|<span data-ttu-id="f229c-122">Sélectionnez BTS.</span><span class="sxs-lookup"><span data-stu-id="f229c-122">Select BTS.</span></span> <span data-ttu-id="f229c-123">MessageType</span><span class="sxs-lookup"><span data-stu-id="f229c-123">MessageType</span></span>|  
    |<span data-ttu-id="f229c-124">**Opérateur**</span><span class="sxs-lookup"><span data-stu-id="f229c-124">**Operator**</span></span>|<span data-ttu-id="f229c-125">Sélectionnez ==</span><span class="sxs-lookup"><span data-stu-id="f229c-125">Select ==</span></span>|  
    |<span data-ttu-id="f229c-126">**Valeur**</span><span class="sxs-lookup"><span data-stu-id="f229c-126">**Value**</span></span>|<span data-ttu-id="f229c-127">Type Sw-HandleFileEventRequest</span><span class="sxs-lookup"><span data-stu-id="f229c-127">Type Sw-HandleFileEventRequest</span></span>|  
    |<span data-ttu-id="f229c-128">**Grouper**</span><span class="sxs-lookup"><span data-stu-id="f229c-128">**Group**</span></span>|<span data-ttu-id="f229c-129">Ou</span><span class="sxs-lookup"><span data-stu-id="f229c-129">Or</span></span>|  
    |<span data-ttu-id="f229c-130">**Propriété**</span><span class="sxs-lookup"><span data-stu-id="f229c-130">**Property**</span></span>|<span data-ttu-id="f229c-131">Sélectionnez BTS.</span><span class="sxs-lookup"><span data-stu-id="f229c-131">Select BTS.</span></span> <span data-ttu-id="f229c-132">MessageType</span><span class="sxs-lookup"><span data-stu-id="f229c-132">MessageType</span></span>|  
    |<span data-ttu-id="f229c-133">**Opérateur**</span><span class="sxs-lookup"><span data-stu-id="f229c-133">**Operator**</span></span>|<span data-ttu-id="f229c-134">Sélectionnez ==</span><span class="sxs-lookup"><span data-stu-id="f229c-134">Select ==</span></span>|  
    |<span data-ttu-id="f229c-135">**Valeur**</span><span class="sxs-lookup"><span data-stu-id="f229c-135">**Value**</span></span>|<span data-ttu-id="f229c-136">Type Sw-ExchangeSnFResponse</span><span class="sxs-lookup"><span data-stu-id="f229c-136">Type Sw-ExchangeSnFResponse</span></span>|