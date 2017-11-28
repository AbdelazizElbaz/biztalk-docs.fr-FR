---
title: "Étape 2 a - ajouter des emplacements de réception FILE | Documents Microsoft"
description: "Étape 2 a - ajouter le fichier emplacements de réception pour le magasin de FileAct et d’un scénario de transfert (Pull) dans BizTalk Server"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 13720ebb-fbe4-4fe1-a095-9ae14c62def1
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e297a85f309445c3caf569d2d752be58997e9754
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-2a-add-file-receive-locations-for-the-fileact-store-and-forward-pull-scenario"></a><span data-ttu-id="5162f-103">Étape 2 a : ajouter le fichier emplacements de réception pour le magasin de FileAct et d’un scénario de transfert (extraction de données)</span><span class="sxs-lookup"><span data-stu-id="5162f-103">Step 2A: Add FILE Receive Locations for the FileAct Store and Forward (Pull) Scenario</span></span>
<span data-ttu-id="5162f-104">Avant de commencer cette étape, vous devez effectuer [étape 1 : configurer l’adaptateur SWIFT pour et le scénario de (extraits) avant de FileAct](step-1-configure-the-swift-adapter-for-fileact-store-and-forward-pull-scenario.md).</span><span class="sxs-lookup"><span data-stu-id="5162f-104">Before you begin this step, you must complete [Step 1: Configure the SWIFT Adapter for the FileAct Store and Forward (Pull) Scenario](step-1-configure-the-swift-adapter-for-fileact-store-and-forward-pull-scenario.md).</span></span>  
  
## <a name="add-a-file-receive-location"></a><span data-ttu-id="5162f-105">Ajouter un emplacement de réception de fichier</span><span class="sxs-lookup"><span data-stu-id="5162f-105">Add a FILE Receive location</span></span>  
  
1.  <span data-ttu-id="5162f-106">Démarrer **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="5162f-106">Start **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="5162f-107">Dans l’arborescence de la console, développez le groupe BizTalk, puis développez l’application BizTalk pour laquelle vous souhaitez créer un port de réception.</span><span class="sxs-lookup"><span data-stu-id="5162f-107">In the console tree, expand the BizTalk group, and then expand the BizTalk application for which you want to create a receive port.</span></span>  
  
3.  <span data-ttu-id="5162f-108">Avec le bouton droit **Ports de réception**, pointez sur **nouveau**, puis cliquez sur **Port de réception unidirectionnel.**</span><span class="sxs-lookup"><span data-stu-id="5162f-108">Right-click **Receive Ports**, point to **New**, and then click **One-way Receive Port.**</span></span>  
  
4.  <span data-ttu-id="5162f-109">Dans le **propriétés du Port de réception** fenêtre, le nom du port de réception, **Tutorial_FA_InputRequest_SnF**.</span><span class="sxs-lookup"><span data-stu-id="5162f-109">In the **Receive Port Properties** window, name the receive port, **Tutorial_FA_InputRequest_SnF**.</span></span>  
  
5.  <span data-ttu-id="5162f-110">Dans le **propriétés du Port de réception** fenêtre, dans le **emplacements de réception** , cliquez sur **nouveau**.</span><span class="sxs-lookup"><span data-stu-id="5162f-110">In the **Receive Port Properties** window, on the **Receive Locations** tab, click **New**.</span></span>  
  
6.  <span data-ttu-id="5162f-111">Dans le **propriétés de l’emplacement de réception** fenêtre, dans le **général** onglet, à partir de la **type de Transport** la liste déroulante, sélectionnez **fichier**, et puis cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="5162f-111">In the **Receive Location Properties** window, on the **General** tab, from the **Transport type** drop-down list, select **FILE**, and then click **Configure**.</span></span>  
  
7.  <span data-ttu-id="5162f-112">Dans le **propriétés du Transport FILE** boîte de dialogue, tapez **C:\SWIFTAdapterTutorial\Fileact\FileRequestDropSnF**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="5162f-112">In the **FILE Transport Properties** dialog box, type **C:\SWIFTAdapterTutorial\Fileact\FileRequestDropSnF**, and then click **OK**.</span></span>  
  
8.  <span data-ttu-id="5162f-113">Dans le **propriétés de l’emplacement de réception** fenêtre, dans le **général** onglet, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="5162f-113">In the **Receive Location Properties** window, on the **General** tab, do the following:</span></span>  
  
    |<span data-ttu-id="5162f-114">**Utilisez cette**</span><span class="sxs-lookup"><span data-stu-id="5162f-114">**Use this**</span></span>|<span data-ttu-id="5162f-115">**Pour ce faire**</span><span class="sxs-lookup"><span data-stu-id="5162f-115">**To do this**</span></span>|  
    |------------------|--------------------|  
    |<span data-ttu-id="5162f-116">**Gestionnaire de réception**</span><span class="sxs-lookup"><span data-stu-id="5162f-116">**Receive handler**</span></span>|<span data-ttu-id="5162f-117">Dans la liste déroulante, sélectionnez **BizTalkServerApplication**.</span><span class="sxs-lookup"><span data-stu-id="5162f-117">From the drop-down list, select **BizTalkServerApplication**.</span></span>|  
    |<span data-ttu-id="5162f-118">**Pipeline de réception**</span><span class="sxs-lookup"><span data-stu-id="5162f-118">**Receive pipeline**</span></span>|<span data-ttu-id="5162f-119">Dans la liste déroulante, sélectionnez **XMLReceive**.</span><span class="sxs-lookup"><span data-stu-id="5162f-119">From the drop-down list, select **XMLReceive**.</span></span>|  
  
9. <span data-ttu-id="5162f-120">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="5162f-120">Click **OK**.</span></span>  
  
10. <span data-ttu-id="5162f-121">Répétez les étapes 1 et 2.</span><span class="sxs-lookup"><span data-stu-id="5162f-121">Repeat steps 1 and 2.</span></span>  
  
11. <span data-ttu-id="5162f-122">Avec le bouton droit **Ports de réception**, pointez sur **nouveau**, puis cliquez sur **Port de réception unidirectionnel.**</span><span class="sxs-lookup"><span data-stu-id="5162f-122">Right-click **Receive Ports**, point to **New**, and then click **One-way Receive Port.**</span></span>  
  
12. <span data-ttu-id="5162f-123">Dans le **propriétés du Port de réception** fenêtre, le nom du port de réception, **Tutorial_ FA_InputRequest_PullMode**.</span><span class="sxs-lookup"><span data-stu-id="5162f-123">In the **Receive Port Properties** window, name the receive port, **Tutorial_ FA_InputRequest_PullMode**.</span></span>  
  
13. <span data-ttu-id="5162f-124">Dans le **propriétés du Port de réception** fenêtre, dans le **emplacements de réception** , cliquez sur **nouveau**.</span><span class="sxs-lookup"><span data-stu-id="5162f-124">In the **Receive Port Properties** window, on the **Receive Locations** tab, click **New**.</span></span>  
  
14. <span data-ttu-id="5162f-125">Dans le **propriétés de l’emplacement de réception** fenêtre, dans le **général** onglet, à partir de la **type de Transport** la liste déroulante, sélectionnez **fichier**, et puis cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="5162f-125">In the **Receive Location Properties** window, on the **General** tab, from the **Transport type** drop-down list, select **FILE**, and then click **Configure**.</span></span>  
  
15. <span data-ttu-id="5162f-126">Dans le **propriétés du Transport FILE** boîte de dialogue, tapez **C:\SWIFTAdapterTutorial\Interact\PullRequest**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="5162f-126">In the **FILE Transport Properties** dialog box, type **C:\SWIFTAdapterTutorial\Interact\PullRequest**, and then click **OK**.</span></span>  
  
16. <span data-ttu-id="5162f-127">Dans le **propriétés de l’emplacement de réception** fenêtre, dans le **général** onglet, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="5162f-127">In the **Receive Location Properties** window, on the **General** tab, do the following:</span></span>  
  
    |<span data-ttu-id="5162f-128">**Utilisez cette**</span><span class="sxs-lookup"><span data-stu-id="5162f-128">**Use this**</span></span>|<span data-ttu-id="5162f-129">**Pour ce faire**</span><span class="sxs-lookup"><span data-stu-id="5162f-129">**To do this**</span></span>|  
    |------------------|--------------------|  
    |<span data-ttu-id="5162f-130">**Gestionnaire de réception**</span><span class="sxs-lookup"><span data-stu-id="5162f-130">**Receive handler**</span></span>|<span data-ttu-id="5162f-131">Dans la liste déroulante, sélectionnez **BizTalkServerApplication**.</span><span class="sxs-lookup"><span data-stu-id="5162f-131">From the drop-down list, select **BizTalkServerApplication**.</span></span>|  
    |<span data-ttu-id="5162f-132">**Pipeline de réception**</span><span class="sxs-lookup"><span data-stu-id="5162f-132">**Receive pipeline**</span></span>|<span data-ttu-id="5162f-133">Dans la liste déroulante, sélectionnez **XMLReceive**.</span><span class="sxs-lookup"><span data-stu-id="5162f-133">From the drop-down list, select **XMLReceive**.</span></span>|  
  
17. <span data-ttu-id="5162f-134">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="5162f-134">Click **OK**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="5162f-135">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="5162f-135">Next steps</span></span>
-  [<span data-ttu-id="5162f-136">Étape 2 b : ajouter des Ports d’envoi FILE pour capturer le Sw:HandleFileRequest et scénario Sw:HandleSnFRequest des Messages pour le magasin de FileAct et le transfert (Pull)</span><span class="sxs-lookup"><span data-stu-id="5162f-136">Step 2B: Add FILE Send Ports to Capture the Sw:HandleFileRequest and Sw:HandleSnFRequest Messages for the FileAct Store and Forward (Pull) Scenario</span></span>](step-2b-add-file-send-ports--get-sw-handlefilerequest-and-sw-handlesnfrequest.md)   
-  [<span data-ttu-id="5162f-137">Étape 2c : ajouter un Port d’envoi FILEACT pour et le scénario de transfert (Pull) de FileAct</span><span class="sxs-lookup"><span data-stu-id="5162f-137">Step 2C: Add a FILEACT Send Port for the FileAct Store and Forward (Pull) Scenario</span></span>](step-2c-add-a-fileact-send-port-for-fileact-store-and-forward-pull-scenario.md)