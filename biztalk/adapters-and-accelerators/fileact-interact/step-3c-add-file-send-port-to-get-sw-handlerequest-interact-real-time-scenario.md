---
title: "Étape 3c : ajouter le port d’envoi FILE pour obtenir Sw:HandleRequest-interagir scénario en temps réel | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 31e9c942-ba74-4ae2-b6e1-5266d0fbcb14
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4ddc38913b8bf9ea5c9450334e58dfaeb5ff4ad3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-3c-add-file-send-port-to-get-swhandlerequest-interact-real-time-scenario"></a><span data-ttu-id="096cc-102">Étape 3c : ajouter le port d’envoi FILE pour obtenir Sw:HandleRequest-interagir scénario en temps réel</span><span class="sxs-lookup"><span data-stu-id="096cc-102">Step 3C: Add FILE send port to get Sw:HandleRequest-InterAct real-time scenario</span></span>
<span data-ttu-id="096cc-103">Lorsque vous envoyez un message à votre partenaire, SWIFT transforme l’en-tête de message et transmet le message à votre partenaire en tant qu’un message Sw:HandleRequest.</span><span class="sxs-lookup"><span data-stu-id="096cc-103">When you send a message to your partner, SWIFT transforms the message header and forwards the message to your partner as a Sw:HandleRequest message.</span></span> <span data-ttu-id="096cc-104">Avant de commencer cette étape, vous devez effectuer [étape 3 b : ajouter un emplacement de réception interagissent pour le scénario en temps réel interagir](../../adapters-and-accelerators/fileact-interact/step-3b-add-an-interact-receive-location-for-the-interact-real-time-scenario.md).</span><span class="sxs-lookup"><span data-stu-id="096cc-104">Before you begin this step, you must complete [Step 3B: Add an INTERACT Receive Location for the InterAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-3b-add-an-interact-receive-location-for-the-interact-real-time-scenario.md).</span></span>  
  
### <a name="to-add-a-file-send-port-to-capture-swhandlerequest-message"></a><span data-ttu-id="096cc-105">Pour ajouter un fichier de port d’envoi pour capturer les messages Sw:HandleRequest</span><span class="sxs-lookup"><span data-stu-id="096cc-105">To add a FILE send port to capture Sw:HandleRequest message</span></span>  
  
1.  <span data-ttu-id="096cc-106">Démarrer **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="096cc-106">Start **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="096cc-107">Dans l’arborescence de la console, développez le groupe BizTalk, puis développez l’application BizTalk pour laquelle vous souhaitez créer un port d’envoi.</span><span class="sxs-lookup"><span data-stu-id="096cc-107">In the console tree, expand the BizTalk group, and then expand the BizTalk application for which you want to create a send port.</span></span>  
  
3.  <span data-ttu-id="096cc-108">Avec le bouton droit **Ports d’envoi**, pointez sur **nouveau**, puis cliquez sur **Port d’envoi unidirectionnel statique.**</span><span class="sxs-lookup"><span data-stu-id="096cc-108">Right-click **Send Ports**, point to **New**, and then click **Static One-way Send Port.**</span></span>  
  
4.  <span data-ttu-id="096cc-109">Dans le **propriétés de Port d’envoi** fenêtre, le nom du port d’envoi **Tutorial_IA_SendResponseToReceiver**.</span><span class="sxs-lookup"><span data-stu-id="096cc-109">In the **Send Port Properties** window, name the send port **Tutorial_IA_SendResponseToReceiver**.</span></span>  
  
5.  <span data-ttu-id="096cc-110">Dans le **propriétés de Port d’envoi** fenêtre, à partir de la **type de Transport** la liste déroulante, sélectionnez **fichier**, puis cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="096cc-110">In the **Send Port Properties** window, from the **Transport type** drop-down list, select **FILE**, and then click **Configure**.</span></span>  
  
6.  <span data-ttu-id="096cc-111">Dans le **propriétés du Transport FILE** boîte de dialogue le **dossier de Destination** zone, tapez C:\SWIFTAdapterTutorial\Interact\HandleRequest, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="096cc-111">In the **FILE Transport Properties** dialog box, in the **Destination folder** box, type C:\SWIFTAdapterTutorial\Interact\HandleRequest, and then click **OK**.</span></span>  
  
7.  <span data-ttu-id="096cc-112">Dans le **propriétés de Port d’envoi** fenêtre, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="096cc-112">In the **Send Port Properties** window, do the following:</span></span>  
  
    |<span data-ttu-id="096cc-113">**Utilisez cette**</span><span class="sxs-lookup"><span data-stu-id="096cc-113">**Use this**</span></span>|<span data-ttu-id="096cc-114">**Pour ce faire**</span><span class="sxs-lookup"><span data-stu-id="096cc-114">**To do this**</span></span>|  
    |------------------|--------------------|  
    |<span data-ttu-id="096cc-115">**Gestionnaire d’envoi**</span><span class="sxs-lookup"><span data-stu-id="096cc-115">**Send handler**</span></span>|<span data-ttu-id="096cc-116">Dans la liste déroulante, sélectionnez **BizTalkServerApplication**.</span><span class="sxs-lookup"><span data-stu-id="096cc-116">From the drop-down list, select **BizTalkServerApplication**.</span></span>|  
    |<span data-ttu-id="096cc-117">**Pipeline d’envoi**</span><span class="sxs-lookup"><span data-stu-id="096cc-117">**Send pipeline**</span></span>|<span data-ttu-id="096cc-118">Dans la liste déroulante, sélectionnez **XMLTransmit**.</span><span class="sxs-lookup"><span data-stu-id="096cc-118">From the drop-down list, select **XMLTransmit**.</span></span>|  
  
8.  <span data-ttu-id="096cc-119">Dans le **propriétés de Port d’envoi** fenêtre, dans le **filtres** onglet, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="096cc-119">In the **Send Port Properties** window, on the **Filters** tab, do the following:</span></span>  
  
    |<span data-ttu-id="096cc-120">**Utilisez cette**</span><span class="sxs-lookup"><span data-stu-id="096cc-120">**Use this**</span></span>|<span data-ttu-id="096cc-121">**Pour ce faire**</span><span class="sxs-lookup"><span data-stu-id="096cc-121">**To do this**</span></span>|  
    |------------------|--------------------|  
    |<span data-ttu-id="096cc-122">**Propriété**</span><span class="sxs-lookup"><span data-stu-id="096cc-122">**Property**</span></span>|<span data-ttu-id="096cc-123">Dans la liste déroulante, sélectionnez **BTS. ReceivePortName**.</span><span class="sxs-lookup"><span data-stu-id="096cc-123">From the drop-down list, select **BTS.ReceivePortName**.</span></span>|  
    |<span data-ttu-id="096cc-124">**Opérateur**</span><span class="sxs-lookup"><span data-stu-id="096cc-124">**Operator**</span></span>|<span data-ttu-id="096cc-125">Dans la liste déroulante, sélectionnez  **==** .</span><span class="sxs-lookup"><span data-stu-id="096cc-125">From the drop-down list, select **==**.</span></span>|  
    |<span data-ttu-id="096cc-126">**Valeur**</span><span class="sxs-lookup"><span data-stu-id="096cc-126">**Value**</span></span>|<span data-ttu-id="096cc-127">Type **Tutorial_IA_HandleRequestOneWay_RealTime.**</span><span class="sxs-lookup"><span data-stu-id="096cc-127">Type **Tutorial_IA_HandleRequestOneWay_RealTime.**</span></span>|  
    |<span data-ttu-id="096cc-128">**Regrouper par**</span><span class="sxs-lookup"><span data-stu-id="096cc-128">**Group by**</span></span>|<span data-ttu-id="096cc-129">Laissez la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="096cc-129">Leave the default value.</span></span>|  
  
9. <span data-ttu-id="096cc-130">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="096cc-130">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="096cc-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="096cc-131">See Also</span></span>  
 <span data-ttu-id="096cc-132">[Étape 3 : Créer l’envoi et Ports de réception l’interaction du scénario en temps réel](../../adapters-and-accelerators/fileact-interact/step-3-create-send-and-receive-ports-for-the-interact-real-time-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="096cc-132">[Step 3: Create Send and Receive Ports for the InterAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-3-create-send-and-receive-ports-for-the-interact-real-time-scenario.md) </span></span>  
 <span data-ttu-id="096cc-133">[Étape 3 a : ajouter un fichier emplacement de réception pour l’interaction du scénario en temps réel](../../adapters-and-accelerators/fileact-interact/step-3a-add-a-file-receive-location-for-the-interact-real-time-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="096cc-133">[Step 3A: Add a FILE Receive Location for the InterAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-3a-add-a-file-receive-location-for-the-interact-real-time-scenario.md) </span></span>  
 <span data-ttu-id="096cc-134">[Étape 3 b : ajouter un interagir emplacement de réception pour l’interaction scénario en temps réel](../../adapters-and-accelerators/fileact-interact/step-3b-add-an-interact-receive-location-for-the-interact-real-time-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="096cc-134">[Step 3B: Add an INTERACT Receive Location for the InterAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-3b-add-an-interact-receive-location-for-the-interact-real-time-scenario.md) </span></span>  
 <span data-ttu-id="096cc-135">[Étape 3D : ajouter un Port d’envoi FILE pour capturer le Message Sw:HandleResponse pour l’interaction du scénario en temps réel](../../adapters-and-accelerators/fileact-interact/step-3d-add-file-send-port-to-get-sw-handleresponse-message-for-interact.md) </span><span class="sxs-lookup"><span data-stu-id="096cc-135">[Step 3D: Add a FILE Send Port to Capture the Sw:HandleResponse Message for the InterAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-3d-add-file-send-port-to-get-sw-handleresponse-message-for-interact.md) </span></span>  
 [<span data-ttu-id="096cc-136">Étape 3E : ajouter un Port d’envoi interagir pour l’interaction scénario en temps réel</span><span class="sxs-lookup"><span data-stu-id="096cc-136">Step 3E: Add an INTERACT Send Port for the InterAct Real-Time Scenario</span></span>](../../adapters-and-accelerators/fileact-interact/step-3e-add-an-interact-send-port-for-the-interact-real-time-scenario.md)