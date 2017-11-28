---
title: "Étape 3 a : ajouter un fichier emplacement de réception pour le magasin d’interagir et scénario avant | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5f4bae51-6869-4334-a3a1-ef7e662197ca
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7d2027878771249ceb2dcb45683a71b4475a75cd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-3a-add-a-file-receive-location-for-the-interact-store-and-forward-scenario"></a><span data-ttu-id="81ce4-102">Étape 3 a : ajouter un fichier emplacement de réception pour le magasin d’interagir et d’un scénario avant</span><span class="sxs-lookup"><span data-stu-id="81ce4-102">Step 3A: Add a FILE Receive Location for the InterAct Store and Forward Scenario</span></span>
<span data-ttu-id="81ce4-103">Complète [étape 2 : ajouter une Configuration pour le Paramfile pour le magasin d’interagir et le scénario par progression SWIFTNet](../../adapters-and-accelerators/fileact-interact/step-2-add-swiftnet-configuration-to-paramfile-for-interact-store-and-forward.md) avant de commencer cette étape.</span><span class="sxs-lookup"><span data-stu-id="81ce4-103">Complete [Step 2: Add SWIFTNet Configuration to the Paramfile for the InterAct Store and Forward Scenario](../../adapters-and-accelerators/fileact-interact/step-2-add-swiftnet-configuration-to-paramfile-for-interact-store-and-forward.md) before you begin this step.</span></span>
  
## <a name="add-a-file-receive-location"></a><span data-ttu-id="81ce4-104">Ajouter l’emplacement de réception de fichier</span><span class="sxs-lookup"><span data-stu-id="81ce4-104">Add a FILE receive location</span></span>  
  
1.  <span data-ttu-id="81ce4-105">Démarrer **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="81ce4-105">Start **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="81ce4-106">Dans l’arborescence de la console, développez le groupe BizTalk, puis développez l’application BizTalk pour laquelle vous souhaitez créer un port de réception.</span><span class="sxs-lookup"><span data-stu-id="81ce4-106">In the console tree, expand the BizTalk group, and then expand the BizTalk application for which you want to create a receive port.</span></span>  
  
3.  <span data-ttu-id="81ce4-107">Avec le bouton droit **Ports de réception**, pointez sur **nouveau**, puis cliquez sur **Port de réception unidirectionnel.**</span><span class="sxs-lookup"><span data-stu-id="81ce4-107">Right-click **Receive Ports**, point to **New**, and then click **One-way Receive Port.**</span></span>  
  
4.  <span data-ttu-id="81ce4-108">Dans le **propriétés du Port de réception** fenêtre, nom du port de réception, Tutorial_IA_InputRequest_SnF.</span><span class="sxs-lookup"><span data-stu-id="81ce4-108">In the **Receive Port Properties** window, name the receive port, Tutorial_IA_InputRequest_SnF.</span></span>  
  
5.  <span data-ttu-id="81ce4-109">Dans le **propriétés du Port de réception** fenêtre, dans le **emplacements de réception** , cliquez sur **nouveau**.</span><span class="sxs-lookup"><span data-stu-id="81ce4-109">In the **Receive Port Properties** window, on the **Receive Locations** tab, click **New**.</span></span>  
  
6.  <span data-ttu-id="81ce4-110">Dans le **propriétés de l’emplacement de réception** fenêtre, dans le **général** onglet, à partir de la **type de Transport** la liste déroulante, sélectionnez **fichier**, et puis cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="81ce4-110">In the **Receive Location Properties** window, on the **General** tab, from the **Transport type** drop-down list, select **FILE**, and then click **Configure**.</span></span>  
  
7.  <span data-ttu-id="81ce4-111">Dans le **propriétés du Transport FILE** boîte de dialogue, tapez C:\SWIFTAdapterTutorial\Interact\InputRequest_SnF, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="81ce4-111">In the **FILE Transport Properties** dialog box, type C:\SWIFTAdapterTutorial\Interact\InputRequest_SnF, and then click **OK**.</span></span>  
  
8.  <span data-ttu-id="81ce4-112">Dans le **propriétés de l’emplacement de réception** fenêtre, dans le **général** onglet, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="81ce4-112">In the **Receive Location Properties** window, on the **General** tab, do the following:</span></span>  
  
    |<span data-ttu-id="81ce4-113">**Utilisez cette**</span><span class="sxs-lookup"><span data-stu-id="81ce4-113">**Use this**</span></span>|<span data-ttu-id="81ce4-114">**Pour ce faire**</span><span class="sxs-lookup"><span data-stu-id="81ce4-114">**To do this**</span></span>|  
    |------------------|--------------------|  
    |<span data-ttu-id="81ce4-115">**Gestionnaire de réception**</span><span class="sxs-lookup"><span data-stu-id="81ce4-115">**Receive handler**</span></span>|<span data-ttu-id="81ce4-116">Dans la liste déroulante, sélectionnez **BizTalkServerApplication**.</span><span class="sxs-lookup"><span data-stu-id="81ce4-116">From the drop-down list, select **BizTalkServerApplication**.</span></span>|  
    |<span data-ttu-id="81ce4-117">**Pipeline de réception**</span><span class="sxs-lookup"><span data-stu-id="81ce4-117">**Receive pipeline**</span></span>|<span data-ttu-id="81ce4-118">Dans la liste déroulante, sélectionnez **XMLReceive**.</span><span class="sxs-lookup"><span data-stu-id="81ce4-118">From the drop-down list, select **XMLReceive**.</span></span>|  
  
9. <span data-ttu-id="81ce4-119">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="81ce4-119">Click **OK**.</span></span>  
  
## <a name="complete-steps"></a><span data-ttu-id="81ce4-120">Étapes à suivre</span><span class="sxs-lookup"><span data-stu-id="81ce4-120">Complete steps</span></span>
 <span data-ttu-id="81ce4-121">[Étape 3 : Créer des Ports d’envoi et Ports de réception pour le magasin d’interagir et d’un scénario avant](../../adapters-and-accelerators/fileact-interact/step-3-create-send-and-receive-ports-for-interact-store-and-forward-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="81ce4-121">[Step 3: Create Send Ports and Receive Ports for the InterAct Store and Forward Scenario](../../adapters-and-accelerators/fileact-interact/step-3-create-send-and-receive-ports-for-interact-store-and-forward-scenario.md) </span></span>  
 <span data-ttu-id="81ce4-122">[Étape 3 b : ajouter un interagir emplacement de réception pour le magasin d’interagir et d’un scénario avant](../../adapters-and-accelerators/fileact-interact/step-3b-add-interact-receive-location-for-interact-store-and-forward-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="81ce4-122">[Step 3B: Add an INTERACT Receive Location for the InterAct Store and Forward Scenario](../../adapters-and-accelerators/fileact-interact/step-3b-add-interact-receive-location-for-interact-store-and-forward-scenario.md) </span></span>  
 [<span data-ttu-id="81ce4-123">Étape 3c : ajouter un Port d’envoi FILE pour capturer le Message Sw:HandleRequest pour le magasin d’interagir et le scénario avant</span><span class="sxs-lookup"><span data-stu-id="81ce4-123">Step 3C: Add a FILE Send Port to Capture the Sw:HandleRequest Message for the InterAct Store and Forward Scenario</span></span>](../../adapters-and-accelerators/fileact-interact/step-3c-add-file-send-port-to-get-sw-handlerequest-interact-store-and-forward.md)  
 [<span data-ttu-id="81ce4-124">Étape 3D : ajouter un Port d’envoi interagissent pour le magasin d’interagir et le scénario avant</span><span class="sxs-lookup"><span data-stu-id="81ce4-124">Step 3D: Add an INTERACT Send Port for the InterAct Store and Forward Scenario</span></span>](../../adapters-and-accelerators/fileact-interact/step-3d-add-an-interact-send-port-for-the-interact-store-and-forward-scenario.md)