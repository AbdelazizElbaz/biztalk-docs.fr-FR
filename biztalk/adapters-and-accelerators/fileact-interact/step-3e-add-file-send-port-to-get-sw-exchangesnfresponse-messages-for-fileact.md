---
title: "Étape 3E : ajouter un Port d’envoi de fichier pour l’et de transférer le scénario afin de capturer les messages Sw-ExchangeSnFResponse FileAct | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 04bad2ab-1ea4-4602-9dee-5b9af9be3b93
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 44cf320f22f5acc2511d6327c36c54cda8f0dd1c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-3e-add-a-file-send-port-for-the-fileact-store-and-forward-scenario-to-capture-sw-exchangesnfresponse-messages"></a><span data-ttu-id="bfa09-102">Étape 3E : ajouter un Port d’envoi de fichier pour l’et de transférer le scénario afin de capturer les messages Sw-ExchangeSnFResponse FileAct</span><span class="sxs-lookup"><span data-stu-id="bfa09-102">Step 3E: Add a FILE Send Port for the FileAct Store and Forward Scenario to capture Sw-ExchangeSnFResponse messages</span></span>
<span data-ttu-id="bfa09-103">Avant de commencer cette étape, vous devez effectuer [étape 3D : ajouter un Port d’envoi FILEACT pour et le scénario de transfert de FileAct](../../adapters-and-accelerators/fileact-interact/step-3d-add-a-fileact-send-port-for-the-fileact-store-and-forward-scenario.md).</span><span class="sxs-lookup"><span data-stu-id="bfa09-103">Before you begin this step, you must complete [Step 3D: Add a FILEACT Send Port for the FileAct Store and Forward Scenario](../../adapters-and-accelerators/fileact-interact/step-3d-add-a-fileact-send-port-for-the-fileact-store-and-forward-scenario.md).</span></span>  
  
### <a name="to-add-a-file-send-port-to-capture-status-events"></a><span data-ttu-id="bfa09-104">Pour ajouter un port d’envoi FILE pour capturer les événements d’état :</span><span class="sxs-lookup"><span data-stu-id="bfa09-104">To add a FILE send port to capture Status Events:</span></span>  
  
1.  <span data-ttu-id="bfa09-105">Démarrer **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="bfa09-105">Start **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="bfa09-106">Dans l’arborescence de la console, développez le groupe BizTalk, puis développez l’application BizTalk pour laquelle vous souhaitez créer un port d’envoi.</span><span class="sxs-lookup"><span data-stu-id="bfa09-106">In the console tree, expand the BizTalk group, and then expand the BizTalk application for which you want to create a send port.</span></span>  
  
3.  <span data-ttu-id="bfa09-107">Avec le bouton droit **Ports d’envoi**, pointez sur **nouveau**, puis cliquez sur **Port d’envoi unidirectionnel statique**.</span><span class="sxs-lookup"><span data-stu-id="bfa09-107">Right-click **Send Ports**, point to **New**, and then click **Static One-way Send Port**.</span></span>  
  
4.  <span data-ttu-id="bfa09-108">Dans le **propriétés de Port d’envoi** fenêtre, le nom du port d’envoi Tutorial_ GetStatusReports.</span><span class="sxs-lookup"><span data-stu-id="bfa09-108">In the **Send Port Properties** window, name the send port, Tutorial_ GetStatusReports.</span></span>  
  
5.  <span data-ttu-id="bfa09-109">Dans le **propriétés de Port d’envoi** fenêtre, à partir de la **type de Transport** la liste déroulante, sélectionnez **fichier**, puis cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="bfa09-109">In the **Send Port Properties** window, from the **Transport type** drop-down list, select **FILE**, and then click **Configure**.</span></span>  
  
6.  <span data-ttu-id="bfa09-110">Dans le **propriétés du Transport FILE** boîte de dialogue le **dossier de Destination** zone, tapez C:\SWIFTAdapterTutorial\Fileact\ StatusEvents, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="bfa09-110">In the **FILE Transport Properties** dialog box, in the **Destination folder** box, type C:\SWIFTAdapterTutorial\Fileact\ StatusEvents, and then click **OK**.</span></span>  
  
7.  <span data-ttu-id="bfa09-111">Dans le **propriétés de Port d’envoi** fenêtre, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="bfa09-111">In the **Send Port Properties** window, do the following:</span></span>  
  
    |<span data-ttu-id="bfa09-112">**Utilisez cette**</span><span class="sxs-lookup"><span data-stu-id="bfa09-112">**Use this**</span></span>|<span data-ttu-id="bfa09-113">**Pour ce faire**</span><span class="sxs-lookup"><span data-stu-id="bfa09-113">**To do this**</span></span>|  
    |------------------|--------------------|  
    |<span data-ttu-id="bfa09-114">**Gestionnaire d’envoi**</span><span class="sxs-lookup"><span data-stu-id="bfa09-114">**Send handler**</span></span>|<span data-ttu-id="bfa09-115">Dans la liste déroulante, sélectionnez **BizTalkServerApplication**.</span><span class="sxs-lookup"><span data-stu-id="bfa09-115">From the drop-down list, select **BizTalkServerApplication**.</span></span>|  
    |<span data-ttu-id="bfa09-116">**Pipeline d’envoi**</span><span class="sxs-lookup"><span data-stu-id="bfa09-116">**Send pipeline**</span></span>|<span data-ttu-id="bfa09-117">Dans la liste déroulante, sélectionnez **XMLTransmit**.</span><span class="sxs-lookup"><span data-stu-id="bfa09-117">From the drop-down list, select **XMLTransmit**.</span></span>|  
  
8.  <span data-ttu-id="bfa09-118">Dans le **propriétés de Port d’envoi** fenêtre, dans le **filtres** onglet, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="bfa09-118">In the **Send Port Properties** window, on the **Filters** tab, do the following:</span></span>  
  
    |<span data-ttu-id="bfa09-119">**Utilisez cette**</span><span class="sxs-lookup"><span data-stu-id="bfa09-119">**Use this**</span></span>|<span data-ttu-id="bfa09-120">**Pour ce faire**</span><span class="sxs-lookup"><span data-stu-id="bfa09-120">**To do this**</span></span>|  
    |------------------|--------------------|  
    |<span data-ttu-id="bfa09-121">**Propriété**</span><span class="sxs-lookup"><span data-stu-id="bfa09-121">**Property**</span></span>|<span data-ttu-id="bfa09-122">Sélectionnez BTS. MessageType</span><span class="sxs-lookup"><span data-stu-id="bfa09-122">Select BTS.MessageType</span></span>|  
    |<span data-ttu-id="bfa09-123">**Opérateur**</span><span class="sxs-lookup"><span data-stu-id="bfa09-123">**Operator**</span></span>|<span data-ttu-id="bfa09-124">Sélectionnez ==</span><span class="sxs-lookup"><span data-stu-id="bfa09-124">Select ==</span></span>|  
    |<span data-ttu-id="bfa09-125">**Valeur**</span><span class="sxs-lookup"><span data-stu-id="bfa09-125">**Value**</span></span>|<span data-ttu-id="bfa09-126">Type Sw-HandleFileEventRequest</span><span class="sxs-lookup"><span data-stu-id="bfa09-126">Type Sw-HandleFileEventRequest</span></span>|  
    |<span data-ttu-id="bfa09-127">**Grouper**</span><span class="sxs-lookup"><span data-stu-id="bfa09-127">**Group**</span></span>|<span data-ttu-id="bfa09-128">Ou</span><span class="sxs-lookup"><span data-stu-id="bfa09-128">Or</span></span>|  
    |<span data-ttu-id="bfa09-129">**Propriété**</span><span class="sxs-lookup"><span data-stu-id="bfa09-129">**Property**</span></span>|<span data-ttu-id="bfa09-130">Sélectionnez BTS.</span><span class="sxs-lookup"><span data-stu-id="bfa09-130">Select BTS.</span></span> <span data-ttu-id="bfa09-131">MessageType</span><span class="sxs-lookup"><span data-stu-id="bfa09-131">MessageType</span></span>|  
    |<span data-ttu-id="bfa09-132">**Opérateur**</span><span class="sxs-lookup"><span data-stu-id="bfa09-132">**Operator**</span></span>|<span data-ttu-id="bfa09-133">Sélectionnez ==</span><span class="sxs-lookup"><span data-stu-id="bfa09-133">Select ==</span></span>|  
    |<span data-ttu-id="bfa09-134">**Valeur**</span><span class="sxs-lookup"><span data-stu-id="bfa09-134">**Value**</span></span>|<span data-ttu-id="bfa09-135">Type Sw-ExchangeSnFResponse</span><span class="sxs-lookup"><span data-stu-id="bfa09-135">Type Sw-ExchangeSnFResponse</span></span>|