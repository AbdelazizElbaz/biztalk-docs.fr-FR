---
title: "Étape 3 a : ajouter un fichier emplacement de réception pour le scénario en temps réel d’interagir | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e5579375-8c05-4583-bcaa-b483ac275d8a
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6c29b3eb291b1b36daab5d77aae74f6055a3c738
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-3a-add-a-file-receive-location-for-the-interact-real-time-scenario"></a><span data-ttu-id="82939-102">Étape 3 a : ajouter un fichier emplacement de réception pour l’interaction du scénario en temps réel</span><span class="sxs-lookup"><span data-stu-id="82939-102">Step 3A: Add a FILE Receive Location for the InterAct Real-Time Scenario</span></span>
<span data-ttu-id="82939-103">Configurer un emplacement de réception qui vous permet de supprimer facilement les fichiers de test de validation.</span><span class="sxs-lookup"><span data-stu-id="82939-103">Set up a receive location that enables you to easily drop test files for validation.</span></span> <span data-ttu-id="82939-104">Cet emplacement vous permet de tester le scénario.</span><span class="sxs-lookup"><span data-stu-id="82939-104">You use this location to test the scenario.</span></span>  
  
## <a name="add-a-file-receive-location"></a><span data-ttu-id="82939-105">Ajouter l’emplacement de réception de fichier</span><span class="sxs-lookup"><span data-stu-id="82939-105">Add a FILE receive location</span></span>  
  
1.  <span data-ttu-id="82939-106">Démarrer **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="82939-106">Start **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="82939-107">Dans l’arborescence de la console, développez le groupe BizTalk, puis développez l’application BizTalk pour laquelle vous souhaitez créer un port de réception.</span><span class="sxs-lookup"><span data-stu-id="82939-107">In the console tree, expand the BizTalk group, and then expand the BizTalk application for which you want to create a receive port.</span></span>  
  
3.  <span data-ttu-id="82939-108">Avec le bouton droit **Ports de réception**, pointez sur **nouveau**, puis cliquez sur **Port de réception unidirectionnel.**</span><span class="sxs-lookup"><span data-stu-id="82939-108">Right-click **Receive Ports**, point to **New**, and then click **One-way Receive Port.**</span></span>  
  
4.  <span data-ttu-id="82939-109">Dans le **propriétés du Port de réception** fenêtre, le nom du port de réception, **Tutorial_IA_InputRequest_RealTime**.</span><span class="sxs-lookup"><span data-stu-id="82939-109">In the **Receive Port Properties** window, name the receive port, **Tutorial_IA_InputRequest_RealTime**.</span></span>  
  
5.  <span data-ttu-id="82939-110">Dans le **propriétés du Port de réception** fenêtre, dans le **emplacements de réception** , cliquez sur **nouveau**.</span><span class="sxs-lookup"><span data-stu-id="82939-110">In the **Receive Port Properties** window, on the **Receive Locations** tab, click **New**.</span></span>  
  
6.  <span data-ttu-id="82939-111">Dans le **propriétés de l’emplacement de réception** fenêtre, dans le **général** onglet, à partir de la **type de Transport** la liste déroulante, sélectionnez **fichier**, et puis cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="82939-111">In the **Receive Location Properties** window, on the **General** tab, from the **Transport type** drop-down list, select **FILE**, and then click **Configure**.</span></span>  
  
7.  <span data-ttu-id="82939-112">Dans le **propriétés du Transport FILE** boîte de dialogue le **dossier de réception** , tapez **C:\SWIFTAdapterTutorial\Interact\InputRequest_RealTime**, puis cliquez sur  **OK**.</span><span class="sxs-lookup"><span data-stu-id="82939-112">In the **FILE Transport Properties** dialog box, in the **Receive folder** box, type **C:\SWIFTAdapterTutorial\Interact\InputRequest_RealTime**, and then click **OK**.</span></span>  
  
8.  <span data-ttu-id="82939-113">Dans le **propriétés de l’emplacement de réception** fenêtre, dans le **général** onglet, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="82939-113">In the **Receive Location Properties** window, on the **General** tab, do the following:</span></span>  
  
    |<span data-ttu-id="82939-114">**Utilisez cette**</span><span class="sxs-lookup"><span data-stu-id="82939-114">**Use this**</span></span>|<span data-ttu-id="82939-115">**Pour ce faire**</span><span class="sxs-lookup"><span data-stu-id="82939-115">**To do this**</span></span>|  
    |------------------|--------------------|  
    |<span data-ttu-id="82939-116">**Gestionnaire de réception**</span><span class="sxs-lookup"><span data-stu-id="82939-116">**Receive handler**</span></span>|<span data-ttu-id="82939-117">Dans la liste déroulante, sélectionnez **BizTalkServerApplication**.</span><span class="sxs-lookup"><span data-stu-id="82939-117">From the drop-down list, select **BizTalkServerApplication**.</span></span>|  
    |<span data-ttu-id="82939-118">**Pipeline de réception**</span><span class="sxs-lookup"><span data-stu-id="82939-118">**Receive pipeline**</span></span>|<span data-ttu-id="82939-119">Dans la liste déroulante, sélectionnez **XMLReceive**.</span><span class="sxs-lookup"><span data-stu-id="82939-119">From the drop-down list, select **XMLReceive**.</span></span>|  
  
9. <span data-ttu-id="82939-120">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="82939-120">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82939-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="82939-121">See Also</span></span>  
 <span data-ttu-id="82939-122">[Étape 3 : Créer l’envoi et Ports de réception l’interaction du scénario en temps réel](../../adapters-and-accelerators/fileact-interact/step-3-create-send-and-receive-ports-for-the-interact-real-time-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="82939-122">[Step 3: Create Send and Receive Ports for the InterAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-3-create-send-and-receive-ports-for-the-interact-real-time-scenario.md) </span></span>  
 <span data-ttu-id="82939-123">[Étape 3 b : ajouter un interagir emplacement de réception pour l’interaction scénario en temps réel](../../adapters-and-accelerators/fileact-interact/step-3b-add-an-interact-receive-location-for-the-interact-real-time-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="82939-123">[Step 3B: Add an INTERACT Receive Location for the InterAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-3b-add-an-interact-receive-location-for-the-interact-real-time-scenario.md) </span></span>  
 <span data-ttu-id="82939-124">[Étape 3c : ajouter un Port d’envoi FILE pour capturer le Message Sw:HandleRequest pour l’interaction du scénario en temps réel](../../adapters-and-accelerators/fileact-interact/step-3c-add-file-send-port-to-get-sw-handlerequest-interact-real-time-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="82939-124">[Step 3C: Add a FILE Send Port to Capture the Sw:HandleRequest Message for the InterAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-3c-add-file-send-port-to-get-sw-handlerequest-interact-real-time-scenario.md) </span></span>  
 <span data-ttu-id="82939-125">[Étape 3D : ajouter un Port d’envoi FILE pour capturer le Message Sw:HandleResponse pour l’interaction du scénario en temps réel](../../adapters-and-accelerators/fileact-interact/step-3d-add-file-send-port-to-get-sw-handleresponse-message-for-interact.md) </span><span class="sxs-lookup"><span data-stu-id="82939-125">[Step 3D: Add a FILE Send Port to Capture the Sw:HandleResponse Message for the InterAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-3d-add-file-send-port-to-get-sw-handleresponse-message-for-interact.md) </span></span>  
 [<span data-ttu-id="82939-126">Étape 3E : ajouter un Port d’envoi interagir pour l’interaction scénario en temps réel</span><span class="sxs-lookup"><span data-stu-id="82939-126">Step 3E: Add an INTERACT Send Port for the InterAct Real-Time Scenario</span></span>](../../adapters-and-accelerators/fileact-interact/step-3e-add-an-interact-send-port-for-the-interact-real-time-scenario.md)