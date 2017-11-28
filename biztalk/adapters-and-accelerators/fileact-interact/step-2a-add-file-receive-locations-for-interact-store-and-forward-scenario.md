---
title: "Étape 2 a : ajouter le fichier emplacements de réception pour le magasin d’interagir et le scénario de transfert (Pull) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: acdc30e1-d80c-40bf-864d-bf136c77a2b8
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 195480b616437eea7b1cfafa703d4ec5d0bd2b54
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-2a-add-file-receive-locations-for-the-interact-store-and-forward-pull-scenario"></a><span data-ttu-id="c8e18-102">Étape 2 a : ajouter le fichier emplacements de réception pour le magasin d’interagir et le scénario de transfert (Pull)</span><span class="sxs-lookup"><span data-stu-id="c8e18-102">Step 2A: Add FILE Receive Locations for the InterAct Store and Forward (Pull) Scenario</span></span>
<span data-ttu-id="c8e18-103">Avant de commencer cette étape, vous devez effectuer [étape 2 : ajouter une Configuration pour le Paramfile pour le magasin d’interagir et le scénario par progression SWIFTNet](../../adapters-and-accelerators/fileact-interact/step-2-add-swiftnet-configuration-to-paramfile-for-interact-store-and-forward.md).</span><span class="sxs-lookup"><span data-stu-id="c8e18-103">Before you begin this step, you must complete [Step 2: Add SWIFTNet Configuration to the Paramfile for the InterAct Store and Forward Scenario](../../adapters-and-accelerators/fileact-interact/step-2-add-swiftnet-configuration-to-paramfile-for-interact-store-and-forward.md).</span></span>  
  
### <a name="to-add-a-file-receive-location"></a><span data-ttu-id="c8e18-104">Pour ajouter un emplacement de réception de fichier</span><span class="sxs-lookup"><span data-stu-id="c8e18-104">To add a FILE Receive location</span></span>  
  
1.  <span data-ttu-id="c8e18-105">Démarrer **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="c8e18-105">Start **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="c8e18-106">Dans l’arborescence de la console, développez le groupe BizTalk, puis développez l’application BizTalk pour laquelle vous souhaitez créer un port de réception.</span><span class="sxs-lookup"><span data-stu-id="c8e18-106">In the console tree, expand the BizTalk group, and then expand the BizTalk application for which you want to create a receive port.</span></span>  
  
3.  <span data-ttu-id="c8e18-107">Avec le bouton droit **Ports de réception**, pointez sur **nouveau**, puis cliquez sur **Port de réception unidirectionnel.**</span><span class="sxs-lookup"><span data-stu-id="c8e18-107">Right-click **Receive Ports**, point to **New**, and then click **One-way Receive Port.**</span></span>  
  
4.  <span data-ttu-id="c8e18-108">Dans le **propriétés du Port de réception** fenêtre, le nom du port de réception, **Tutorial_IA_InputRequest_SnF**.</span><span class="sxs-lookup"><span data-stu-id="c8e18-108">In the **Receive Port Properties** window, name the receive port, **Tutorial_IA_InputRequest_SnF**.</span></span>  
  
5.  <span data-ttu-id="c8e18-109">Dans le **propriétés du Port de réception** fenêtre, dans le **emplacements de réception** , cliquez sur **nouveau**.</span><span class="sxs-lookup"><span data-stu-id="c8e18-109">In the **Receive Port Properties** window, on the **Receive Locations** tab, click **New**.</span></span>  
  
6.  <span data-ttu-id="c8e18-110">Dans le **propriétés de l’emplacement de réception** fenêtre, dans le **général** onglet, à partir de la **type de Transport** la liste déroulante, sélectionnez **fichier**, et puis cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="c8e18-110">In the **Receive Location Properties** window, on the **General** tab, from the **Transport type** drop-down list, select **FILE**, and then click **Configure**.</span></span>  
  
7.  <span data-ttu-id="c8e18-111">Dans le **propriétés du Transport FILE** boîte de dialogue, tapez **C:\SWIFTAdapterTutorial\Interact\InputRequest_SnF**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="c8e18-111">In the **FILE Transport Properties** dialog box, type **C:\SWIFTAdapterTutorial\Interact\InputRequest_SnF**, and then click **OK**.</span></span>  
  
8.  <span data-ttu-id="c8e18-112">Dans le **propriétés de l’emplacement de réception** fenêtre, dans le **général** onglet, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="c8e18-112">In the **Receive Location Properties** window, on the **General** tab, do the following:</span></span>  
  
    |<span data-ttu-id="c8e18-113">**Utilisez cette**</span><span class="sxs-lookup"><span data-stu-id="c8e18-113">**Use this**</span></span>|<span data-ttu-id="c8e18-114">**Pour ce faire**</span><span class="sxs-lookup"><span data-stu-id="c8e18-114">**To do this**</span></span>|  
    |------------------|--------------------|  
    |<span data-ttu-id="c8e18-115">**Gestionnaire de réception**</span><span class="sxs-lookup"><span data-stu-id="c8e18-115">**Receive handler**</span></span>|<span data-ttu-id="c8e18-116">Dans la liste déroulante, sélectionnez **BizTalkServerApplication**.</span><span class="sxs-lookup"><span data-stu-id="c8e18-116">From the drop-down list, select **BizTalkServerApplication**.</span></span>|  
    |<span data-ttu-id="c8e18-117">**Pipeline de réception**</span><span class="sxs-lookup"><span data-stu-id="c8e18-117">**Receive pipeline**</span></span>|<span data-ttu-id="c8e18-118">Dans la liste déroulante, sélectionnez **XMLReceive**.</span><span class="sxs-lookup"><span data-stu-id="c8e18-118">From the drop-down list, select **XMLReceive**.</span></span>|  
  
9. <span data-ttu-id="c8e18-119">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="c8e18-119">Click **OK**.</span></span>  
  
10. <span data-ttu-id="c8e18-120">Répétez les étapes 1 et 2.</span><span class="sxs-lookup"><span data-stu-id="c8e18-120">Repeat steps 1 and 2.</span></span>  
  
11. <span data-ttu-id="c8e18-121">Avec le bouton droit **Ports de réception**, pointez sur **nouveau**, puis cliquez sur **Port de réception unidirectionnel.**</span><span class="sxs-lookup"><span data-stu-id="c8e18-121">Right-click **Receive Ports**, point to **New**, and then click **One-way Receive Port.**</span></span>  
  
12. <span data-ttu-id="c8e18-122">Dans le **propriétés du Port de réception** fenêtre, le nom du port de réception, **Tutorial_IA_InputRequest_PullMode**.</span><span class="sxs-lookup"><span data-stu-id="c8e18-122">In the **Receive Port Properties** window, name the receive port, **Tutorial_IA_InputRequest_PullMode**.</span></span>  
  
13. <span data-ttu-id="c8e18-123">Dans le **propriétés du Port de réception** fenêtre, dans le **emplacements de réception** , cliquez sur **nouveau**.</span><span class="sxs-lookup"><span data-stu-id="c8e18-123">In the **Receive Port Properties** window, on the **Receive Locations** tab, click **New**.</span></span>  
  
14. <span data-ttu-id="c8e18-124">Dans le **propriétés de l’emplacement de réception** fenêtre, dans le **général** onglet, à partir de la **type de Transport** la liste déroulante, sélectionnez **fichier**, et puis cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="c8e18-124">In the **Receive Location Properties** window, on the **General** tab, from the **Transport type** drop-down list, select **FILE**, and then click **Configure**.</span></span>  
  
15. <span data-ttu-id="c8e18-125">Dans le **propriétés du Transport FILE** boîte de dialogue, tapez **C:\SWIFTAdapterTutorial\Interact\PullRequest**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="c8e18-125">In the **FILE Transport Properties** dialog box, type **C:\SWIFTAdapterTutorial\Interact\PullRequest**, and then click **OK**.</span></span>  
  
16. <span data-ttu-id="c8e18-126">Dans le **propriétés de l’emplacement de réception** fenêtre, dans le **général** onglet, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="c8e18-126">In the **Receive Location Properties** window, on the **General** tab, do the following:</span></span>  
  
    |<span data-ttu-id="c8e18-127">**Utilisez cette**</span><span class="sxs-lookup"><span data-stu-id="c8e18-127">**Use this**</span></span>|<span data-ttu-id="c8e18-128">**Pour ce faire**</span><span class="sxs-lookup"><span data-stu-id="c8e18-128">**To do this**</span></span>|  
    |------------------|--------------------|  
    |<span data-ttu-id="c8e18-129">**Gestionnaire de réception**</span><span class="sxs-lookup"><span data-stu-id="c8e18-129">**Receive handler**</span></span>|<span data-ttu-id="c8e18-130">Dans la liste déroulante, sélectionnez **BizTalkServerApplication**.</span><span class="sxs-lookup"><span data-stu-id="c8e18-130">From the drop-down list, select **BizTalkServerApplication**.</span></span>|  
    |<span data-ttu-id="c8e18-131">**Pipeline de réception**</span><span class="sxs-lookup"><span data-stu-id="c8e18-131">**Receive pipeline**</span></span>|<span data-ttu-id="c8e18-132">Dans la liste déroulante, sélectionnez **XMLReceive**.</span><span class="sxs-lookup"><span data-stu-id="c8e18-132">From the drop-down list, select **XMLReceive**.</span></span>|  
  
17. <span data-ttu-id="c8e18-133">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="c8e18-133">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8e18-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c8e18-134">See Also</span></span>  
 <span data-ttu-id="c8e18-135">[Étape 2 b : ajouter des Ports d’envoi FILE pour capturer le Message Sw:HandleRequest pour le magasin d’interagir et le scénario de transfert (Pull)](../../adapters-and-accelerators/fileact-interact/step-2b-add-file-send-ports-to-get-sw-handlerequest-message-for-interact.md) </span><span class="sxs-lookup"><span data-stu-id="c8e18-135">[Step 2B: Add FILE Send Ports to Capture the Sw:HandleRequest Message for the InterAct Store and Forward (Pull) Scenario](../../adapters-and-accelerators/fileact-interact/step-2b-add-file-send-ports-to-get-sw-handlerequest-message-for-interact.md) </span></span>  
 [<span data-ttu-id="c8e18-136">Étape 2c : ajouter un Port d’envoi interagissent pour le magasin d’interagir et le scénario de transfert (Pull)</span><span class="sxs-lookup"><span data-stu-id="c8e18-136">Step 2C: Add an INTERACT Send Port for the InterAct Store and Forward (Pull) Scenario</span></span>](../../adapters-and-accelerators/fileact-interact/step-2c-add-interact-send-port-for-interact-store-and-forward-pull-scenario.md)