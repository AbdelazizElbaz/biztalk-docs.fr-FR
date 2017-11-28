---
title: "Étape 3c : ajouter un Port d’envoi FILE pour capturer les Messages Sw:HandleFileRequest et Sw:HandleSnFRequest pour et le scénario de transfert de FileAct | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cc41e352-acc5-47eb-bb87-38990f0e76a7
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ae6858164ee82f935c607246e7e93ffd86908f93
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-3c-add-a-file-send-port-to-capture-the-swhandlefilerequest-and-swhandlesnfrequest-messages-for-the-fileact-store-and-forward-scenario"></a><span data-ttu-id="00cc5-102">Étape 3c : ajouter un Port d’envoi FILE pour capturer les Messages Sw:HandleFileRequest et Sw:HandleSnFRequest pour et le scénario de transfert de FileAct</span><span class="sxs-lookup"><span data-stu-id="00cc5-102">Step 3C: Add a FILE Send Port to Capture the Sw:HandleFileRequest and Sw:HandleSnFRequest Messages for the FileAct Store and Forward Scenario</span></span>
<span data-ttu-id="00cc5-103">Avant de commencer cette étape, vous devez effectuer [étape 3 b : ajouter un emplacement de réception FILEACT pour et le scénario de transfert de FileAct](../../adapters-and-accelerators/fileact-interact/step-3b-add-a-fileact-receive-location-for-fileact-store-and-forward-scenario.md).</span><span class="sxs-lookup"><span data-stu-id="00cc5-103">Before you begin this step, you must complete [Step 3B: Add a FILEACT Receive Location for the FileAct Store and Forward Scenario](../../adapters-and-accelerators/fileact-interact/step-3b-add-a-fileact-receive-location-for-fileact-store-and-forward-scenario.md).</span></span>  
  
### <a name="to-add-a-file-send-port-to-capture-swresponseserver-message"></a><span data-ttu-id="00cc5-104">Pour ajouter un fichier de port d’envoi pour capturer les messages Sw:ResponseServer</span><span class="sxs-lookup"><span data-stu-id="00cc5-104">To add a FILE send port to capture Sw:ResponseServer message</span></span>  
  
1.  <span data-ttu-id="00cc5-105">Démarrer **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="00cc5-105">Start **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="00cc5-106">Dans l’arborescence de la console, développez le groupe BizTalk, puis développez l’application BizTalk pour laquelle vous souhaitez créer un port d’envoi.</span><span class="sxs-lookup"><span data-stu-id="00cc5-106">In the console tree, expand the BizTalk group, and then expand the BizTalk application for which you want to create a send port.</span></span>  
  
3.  <span data-ttu-id="00cc5-107">Avec le bouton droit **Ports d’envoi**, pointez sur **nouveau**, puis cliquez sur **Port d’envoi unidirectionnel statique.**</span><span class="sxs-lookup"><span data-stu-id="00cc5-107">Right-click **Send Ports**, point to **New**, and then click **Static One-way Send Port.**</span></span>  
  
4.  <span data-ttu-id="00cc5-108">Dans le **propriétés de Port d’envoi** fenêtre, le nom du port d’envoi Tutorial_FA_SendResponseToReceiver.</span><span class="sxs-lookup"><span data-stu-id="00cc5-108">In the **Send Port Properties** window, name the send port, Tutorial_FA_SendResponseToReceiver.</span></span>  
  
5.  <span data-ttu-id="00cc5-109">Dans le **propriétés de Port d’envoi** fenêtre, à partir de la **type de Transport** la liste déroulante, sélectionnez **fichier**, puis cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="00cc5-109">In the **Send Port Properties** window, from the **Transport type** drop-down list, select **FILE**, and then click **Configure**.</span></span>  
  
6.  <span data-ttu-id="00cc5-110">Dans le **propriétés du Transport FILE** boîte de dialogue le **dossier de Destination** zone, tapez C:\SWIFTAdapterTutorial\Fileact\ResponseServer, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="00cc5-110">In the **FILE Transport Properties** dialog box, in the **Destination folder** box, type C:\SWIFTAdapterTutorial\Fileact\ResponseServer, and then click **OK**.</span></span>  
  
7.  <span data-ttu-id="00cc5-111">Dans le **propriétés de Port d’envoi** fenêtre, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="00cc5-111">In the **Send Port Properties** window, do the following:</span></span>  
  
    |<span data-ttu-id="00cc5-112">**Utilisez cette**</span><span class="sxs-lookup"><span data-stu-id="00cc5-112">**Use this**</span></span>|<span data-ttu-id="00cc5-113">**Pour ce faire**</span><span class="sxs-lookup"><span data-stu-id="00cc5-113">**To do this**</span></span>|  
    |------------------|--------------------|  
    |<span data-ttu-id="00cc5-114">**Gestionnaire d’envoi**</span><span class="sxs-lookup"><span data-stu-id="00cc5-114">**Send handler**</span></span>|<span data-ttu-id="00cc5-115">Dans la liste déroulante, sélectionnez **BizTalkServerApplication**.</span><span class="sxs-lookup"><span data-stu-id="00cc5-115">From the drop-down list, select **BizTalkServerApplication**.</span></span>|  
    |<span data-ttu-id="00cc5-116">**Pipeline d’envoi**</span><span class="sxs-lookup"><span data-stu-id="00cc5-116">**Send pipeline**</span></span>|<span data-ttu-id="00cc5-117">Dans la liste déroulante, sélectionnez **XMLTransmit**.</span><span class="sxs-lookup"><span data-stu-id="00cc5-117">From the drop-down list, select **XMLTransmit**.</span></span>|  
  
8.  <span data-ttu-id="00cc5-118">Dans le **propriétés de Port d’envoi** fenêtre, dans le **filtres** onglet, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="00cc5-118">In the **Send Port Properties** window, on the **Filters** tab, do the following:</span></span>  
  
    |<span data-ttu-id="00cc5-119">**Utilisez cette**</span><span class="sxs-lookup"><span data-stu-id="00cc5-119">**Use this**</span></span>|<span data-ttu-id="00cc5-120">**Pour ce faire**</span><span class="sxs-lookup"><span data-stu-id="00cc5-120">**To do this**</span></span>|  
    |------------------|--------------------|  
    |<span data-ttu-id="00cc5-121">**Tout d’abord de ligne : propriété**</span><span class="sxs-lookup"><span data-stu-id="00cc5-121">**First row: Property**</span></span>|<span data-ttu-id="00cc5-122">Dans la liste déroulante, sélectionnez **BTS. MessageType**.</span><span class="sxs-lookup"><span data-stu-id="00cc5-122">From the drop-down list, select **BTS.MessageType**.</span></span>|  
    |<span data-ttu-id="00cc5-123">**Tout d’abord de ligne : (opérateur)**</span><span class="sxs-lookup"><span data-stu-id="00cc5-123">**First row: Operator**</span></span>|<span data-ttu-id="00cc5-124">Dans la liste déroulante, sélectionnez  **==** .</span><span class="sxs-lookup"><span data-stu-id="00cc5-124">From the drop-down list, select **==**.</span></span>|  
    |<span data-ttu-id="00cc5-125">**Tout d’abord de ligne : valeur**</span><span class="sxs-lookup"><span data-stu-id="00cc5-125">**First row: Value**</span></span>|<span data-ttu-id="00cc5-126">Type **Sw-HandleFileRequest**.</span><span class="sxs-lookup"><span data-stu-id="00cc5-126">Type **Sw-HandleFileRequest**.</span></span>|  
    |<span data-ttu-id="00cc5-127">**Tout d’abord de ligne : regrouper par**</span><span class="sxs-lookup"><span data-stu-id="00cc5-127">**First row: Group by**</span></span>|<span data-ttu-id="00cc5-128">Dans la liste déroulante, sélectionnez **ou**.</span><span class="sxs-lookup"><span data-stu-id="00cc5-128">From the drop-down list, select **OR**.</span></span>|  
    |<span data-ttu-id="00cc5-129">**Deuxième ligne : propriété**</span><span class="sxs-lookup"><span data-stu-id="00cc5-129">**Second row: Property**</span></span>|<span data-ttu-id="00cc5-130">Dans la liste déroulante, sélectionnez **BTS. MessageType**.</span><span class="sxs-lookup"><span data-stu-id="00cc5-130">From the drop-down list, select **BTS.MessageType**.</span></span>|  
    |<span data-ttu-id="00cc5-131">**Deuxième ligne : (opérateur)**</span><span class="sxs-lookup"><span data-stu-id="00cc5-131">**Second row: Operator**</span></span>|<span data-ttu-id="00cc5-132">Dans la liste déroulante, sélectionnez  **==** .</span><span class="sxs-lookup"><span data-stu-id="00cc5-132">From the drop-down list, select **==**.</span></span>|  
    |<span data-ttu-id="00cc5-133">**Deuxième ligne : valeur**</span><span class="sxs-lookup"><span data-stu-id="00cc5-133">**Second row: Value**</span></span>|<span data-ttu-id="00cc5-134">Type **Sw-HandleSnFRequest**.</span><span class="sxs-lookup"><span data-stu-id="00cc5-134">Type **Sw-HandleSnFRequest**.</span></span>|  
    |<span data-ttu-id="00cc5-135">**Deuxième ligne : regrouper par**</span><span class="sxs-lookup"><span data-stu-id="00cc5-135">**Second row: Group by**</span></span>|<span data-ttu-id="00cc5-136">Laissez la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="00cc5-136">Leave the default value.</span></span>|  
  
9. <span data-ttu-id="00cc5-137">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="00cc5-137">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00cc5-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="00cc5-138">See Also</span></span>  
 <span data-ttu-id="00cc5-139">[Étape 3 : Créer des Ports d’envoi et Ports de réception d’et le scénario de transfert de FileAct](../../adapters-and-accelerators/fileact-interact/step-3-create-send-ports-and-receive-ports-for-the-fileact-store-and-forward.md) </span><span class="sxs-lookup"><span data-stu-id="00cc5-139">[Step 3: Create Send Ports and Receive Ports for the FileAct Store and Forward Scenario](../../adapters-and-accelerators/fileact-interact/step-3-create-send-ports-and-receive-ports-for-the-fileact-store-and-forward.md) </span></span>  
 <span data-ttu-id="00cc5-140">[Étape 3 a : ajouter un fichier emplacement de réception pour et le scénario de transfert de FileAct](../../adapters-and-accelerators/fileact-interact/step-3a-add-a-file-receive-location-for-the-fileact-store-and-forward-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="00cc5-140">[Step 3A: Add a FILE Receive Location for the FileAct Store and Forward Scenario](../../adapters-and-accelerators/fileact-interact/step-3a-add-a-file-receive-location-for-the-fileact-store-and-forward-scenario.md) </span></span>  
 <span data-ttu-id="00cc5-141">[Étape 3 b : ajouter un FILEACT emplacement de réception pour et le scénario de transfert de FileAct](../../adapters-and-accelerators/fileact-interact/step-3b-add-a-fileact-receive-location-for-fileact-store-and-forward-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="00cc5-141">[Step 3B: Add a FILEACT Receive Location for the FileAct Store and Forward Scenario](../../adapters-and-accelerators/fileact-interact/step-3b-add-a-fileact-receive-location-for-fileact-store-and-forward-scenario.md) </span></span>  
 [<span data-ttu-id="00cc5-142">Étape 3D : ajouter un Port d’envoi FILEACT pour et le scénario de transfert de FileAct</span><span class="sxs-lookup"><span data-stu-id="00cc5-142">Step 3D: Add a FILEACT Send Port for the FileAct Store and Forward Scenario</span></span>](../../adapters-and-accelerators/fileact-interact/step-3d-add-a-fileact-send-port-for-the-fileact-store-and-forward-scenario.md)