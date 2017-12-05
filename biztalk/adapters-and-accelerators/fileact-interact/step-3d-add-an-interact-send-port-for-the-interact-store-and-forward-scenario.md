---
title: "Étape 3D : ajouter un Port d’envoi interagissent pour le magasin d’interagir et le scénario avant | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cd126d9a-f4e4-429e-bab0-8b4c9c555e36
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 11b4e17a4435c5d9e6e99cd3ed471fa8819923e8
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="step-3d-add-an-interact-send-port-for-the-interact-store-and-forward-scenario"></a><span data-ttu-id="38fad-102">Étape 3D : ajouter un Port d’envoi interagissent pour le magasin d’interagir et le scénario avant</span><span class="sxs-lookup"><span data-stu-id="38fad-102">Step 3D: Add an INTERACT Send Port for the InterAct Store and Forward Scenario</span></span>
<span data-ttu-id="38fad-103">Complète [étape 3c : ajouter un Port d’envoi FILE pour capturer le Message Sw:HandleRequest pour le magasin d’interagir et le scénario par progression](../../adapters-and-accelerators/fileact-interact/step-3c-add-file-send-port-to-get-sw-handlerequest-interact-store-and-forward.md) avant de commencer cette étape.</span><span class="sxs-lookup"><span data-stu-id="38fad-103">Complete [Step 3C: Add a FILE Send Port to Capture the Sw:HandleRequest Message for the InterAct Store and Forward Scenario](../../adapters-and-accelerators/fileact-interact/step-3c-add-file-send-port-to-get-sw-handlerequest-interact-store-and-forward.md) before you begin this step.</span></span>
  
## <a name="add-an-interact-send-port"></a><span data-ttu-id="38fad-104">Ajouter un port d’envoi INTERACT</span><span class="sxs-lookup"><span data-stu-id="38fad-104">Add an INTERACT send port</span></span>  
  
1.  <span data-ttu-id="38fad-105">Démarrer **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="38fad-105">Start **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="38fad-106">Dans l’arborescence de la console, développez le groupe BizTalk, puis développez l’application BizTalk pour laquelle vous souhaitez créer un port d’envoi.</span><span class="sxs-lookup"><span data-stu-id="38fad-106">In the console tree, expand the BizTalk group, and then expand the BizTalk application for which you want to create a send port.</span></span>  
  
3.  <span data-ttu-id="38fad-107">Avec le bouton droit **Ports d’envoi**, pointez sur **nouveau**, puis cliquez sur **Port d’envoi statique avec sollicitation-réponse**.</span><span class="sxs-lookup"><span data-stu-id="38fad-107">Right-click **Send Ports**, point to **New**, and then click **Static Solicit-Response Send Port**.</span></span>  
  
4.  <span data-ttu-id="38fad-108">Dans le **propriétés de Port d’envoi** fenêtre, le nom du port d’envoi Tutorial_IA_SendRequest_SnF.</span><span class="sxs-lookup"><span data-stu-id="38fad-108">In the **Send Port Properties** window, name the send port, Tutorial_IA_SendRequest_SnF.</span></span>  
  
5.  <span data-ttu-id="38fad-109">Dans le **propriétés de Port d’envoi** fenêtre, à partir de la **type de Transport** la liste déroulante, sélectionnez **interagir**, puis cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="38fad-109">In the **Send Port Properties** window, from the **Transport type** drop-down list, select **INTERACT**, and then click **Configure**.</span></span>  
  
6.  <span data-ttu-id="38fad-110">Dans le **propriétés du Transport interagir** boîte de dialogue zone, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="38fad-110">In the **INTERACT Transport Properties** dialog box, do the following:</span></span>  
  
    |<span data-ttu-id="38fad-111">**Utilisez cette**</span><span class="sxs-lookup"><span data-stu-id="38fad-111">**Use this**</span></span>|<span data-ttu-id="38fad-112">**Pour ce faire**</span><span class="sxs-lookup"><span data-stu-id="38fad-112">**To do this**</span></span>|  
    |------------------|--------------------|  
    |<span data-ttu-id="38fad-113">**Mot de passe**</span><span class="sxs-lookup"><span data-stu-id="38fad-113">**Password**</span></span>|<span data-ttu-id="38fad-114">Définissez le mot de passe pour la connectivité des trous.</span><span class="sxs-lookup"><span data-stu-id="38fad-114">Set the password as appropriate for SAG connectivity.</span></span>|  
    |<span data-ttu-id="38fad-115">**Nom d'utilisateur**</span><span class="sxs-lookup"><span data-stu-id="38fad-115">**User name**</span></span>|<span data-ttu-id="38fad-116">Définissez le nom d’utilisateur pour la connectivité des trous.</span><span class="sxs-lookup"><span data-stu-id="38fad-116">Set the user name as appropriate for SAG connectivity.</span></span>|  
    |<span data-ttu-id="38fad-117">**Format de message**</span><span class="sxs-lookup"><span data-stu-id="38fad-117">**Message format**</span></span>|<span data-ttu-id="38fad-118">**InteractMessage**</span><span class="sxs-lookup"><span data-stu-id="38fad-118">**InteractMessage**</span></span>|  
    |<span data-ttu-id="38fad-119">**Indicateur de non répudiation**</span><span class="sxs-lookup"><span data-stu-id="38fad-119">**Non-Repudiation Indicator**</span></span>|<span data-ttu-id="38fad-120">**FALSE**</span><span class="sxs-lookup"><span data-stu-id="38fad-120">**FALSE**</span></span>|  
    |<span data-ttu-id="38fad-121">**Type de demande**</span><span class="sxs-lookup"><span data-stu-id="38fad-121">**Request Type**</span></span>|<span data-ttu-id="38fad-122">Tapez la commande appropriée \<RequestType\> chaîne, en fonction de votre configuration avec SWIFT.</span><span class="sxs-lookup"><span data-stu-id="38fad-122">Type the appropriate \<RequestType\> string, based on your provisioning with SWIFT.</span></span>|  
    |<span data-ttu-id="38fad-123">**ResponseCrypto**</span><span class="sxs-lookup"><span data-stu-id="38fad-123">**ResponseCrypto**</span></span>|<span data-ttu-id="38fad-124">**FALSE**</span><span class="sxs-lookup"><span data-stu-id="38fad-124">**FALSE**</span></span>|  
    |<span data-ttu-id="38fad-125">**Demandeur**</span><span class="sxs-lookup"><span data-stu-id="38fad-125">**Requestor**</span></span>|<span data-ttu-id="38fad-126">Tapez la commande appropriée \<RequestorDN\> chaîne, en fonction de votre configuration avec SWIFT.</span><span class="sxs-lookup"><span data-stu-id="38fad-126">Type the appropriate \<RequestorDN\> string, based on your provisioning with SWIFT.</span></span>|  
    |<span data-ttu-id="38fad-127">**Répondeur**</span><span class="sxs-lookup"><span data-stu-id="38fad-127">**Responder**</span></span>|<span data-ttu-id="38fad-128">Tapez la commande appropriée \<ResponderDN\> chaîne, en fonction de votre configuration avec SWIFT.</span><span class="sxs-lookup"><span data-stu-id="38fad-128">Type the appropriate \<ResponderDN\> string, based on your provisioning with SWIFT.</span></span>|  
    |<span data-ttu-id="38fad-129">**Nom du service**</span><span class="sxs-lookup"><span data-stu-id="38fad-129">**Service Name**</span></span>|<span data-ttu-id="38fad-130">Tapez la commande appropriée \<nom du service\>, en fonction de votre configuration avec SWIFT.</span><span class="sxs-lookup"><span data-stu-id="38fad-130">Type the appropriate \<service name\>, based on your provisioning with SWIFT.</span></span>|  
    |<span data-ttu-id="38fad-131">**Accusé de réception**</span><span class="sxs-lookup"><span data-stu-id="38fad-131">**Delivery Notification**</span></span>|<span data-ttu-id="38fad-132">Dans la liste déroulante, sélectionnez **FALSE**.</span><span class="sxs-lookup"><span data-stu-id="38fad-132">From the drop-down list, select **FALSE**.</span></span>|  
    |<span data-ttu-id="38fad-133">**File d’attente de notification**</span><span class="sxs-lookup"><span data-stu-id="38fad-133">**Notify queue**</span></span>|<span data-ttu-id="38fad-134">Tapez le nom de la file d’attente appropriée, en fonction de votre configuration avec SWIFT.</span><span class="sxs-lookup"><span data-stu-id="38fad-134">Type the appropriate queue name, based on your provisioning with SWIFT.</span></span>|  
  
    > [!NOTE]
    >  <span data-ttu-id="38fad-135">Si une seule charge utile doit être transféré, jeu du MessageFormat à « Charge » dans l’interagir port de réception et port d’envoi interagir.</span><span class="sxs-lookup"><span data-stu-id="38fad-135">If only payload is to be transferred, set the MessageFormat to “Payload” in the INTERACT receive port and INTERACT send port.</span></span> <span data-ttu-id="38fad-136">Affectez les pipelines de réception et d’envoi PassThru.</span><span class="sxs-lookup"><span data-stu-id="38fad-136">Set the Receive and Send pipelines to PassThru.</span></span>  
  
7.  <span data-ttu-id="38fad-137">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="38fad-137">Click **OK**.</span></span>  
  
8.  <span data-ttu-id="38fad-138">Dans le **propriétés de Port d’envoi** fenêtre, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="38fad-138">In the **Send Port Properties** window, do the following:</span></span>  
  
    |<span data-ttu-id="38fad-139">**Utilisez cette**</span><span class="sxs-lookup"><span data-stu-id="38fad-139">**Use this**</span></span>|<span data-ttu-id="38fad-140">**Pour ce faire**</span><span class="sxs-lookup"><span data-stu-id="38fad-140">**To do this**</span></span>|  
    |------------------|--------------------|  
    |<span data-ttu-id="38fad-141">**Gestionnaire d’envoi**</span><span class="sxs-lookup"><span data-stu-id="38fad-141">**Send handler**</span></span>|<span data-ttu-id="38fad-142">Dans la liste déroulante, sélectionnez l’hôte d’interagir.</span><span class="sxs-lookup"><span data-stu-id="38fad-142">From the drop-down list, select the Interact host.</span></span>|  
    |<span data-ttu-id="38fad-143">**Pipeline d’envoi**</span><span class="sxs-lookup"><span data-stu-id="38fad-143">**Send pipeline**</span></span>|<span data-ttu-id="38fad-144">Dans la liste déroulante, sélectionnez **XMLTransmit**.</span><span class="sxs-lookup"><span data-stu-id="38fad-144">From the drop-down list, select **XMLTransmit**.</span></span>|  
    |<span data-ttu-id="38fad-145">**Pipeline de réception**</span><span class="sxs-lookup"><span data-stu-id="38fad-145">**Receive pipeline**</span></span>|<span data-ttu-id="38fad-146">Dans la liste déroulante, sélectionnez **XMLReceive**.</span><span class="sxs-lookup"><span data-stu-id="38fad-146">From the drop-down list, select **XMLReceive**.</span></span>|  
  
9. <span data-ttu-id="38fad-147">Dans le **propriétés de Port d’envoi** fenêtre, dans le **filtres** onglet, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="38fad-147">In the **Send Port Properties** window, on the **Filters** tab, do the following:</span></span>  
  
    |<span data-ttu-id="38fad-148">**Utilisez cette**</span><span class="sxs-lookup"><span data-stu-id="38fad-148">**Use this**</span></span>|<span data-ttu-id="38fad-149">**Pour ce faire**</span><span class="sxs-lookup"><span data-stu-id="38fad-149">**To do this**</span></span>|  
    |------------------|--------------------|  
    |<span data-ttu-id="38fad-150">**Propriété**</span><span class="sxs-lookup"><span data-stu-id="38fad-150">**Property**</span></span>|<span data-ttu-id="38fad-151">Dans la liste déroulante, sélectionnez **BTS. ReceivePortName**.</span><span class="sxs-lookup"><span data-stu-id="38fad-151">From the drop-down list, select **BTS.ReceivePortName**.</span></span>|  
    |<span data-ttu-id="38fad-152">**Opérateur**</span><span class="sxs-lookup"><span data-stu-id="38fad-152">**Operator**</span></span>|<span data-ttu-id="38fad-153">Dans la liste déroulante, sélectionnez  **==** .</span><span class="sxs-lookup"><span data-stu-id="38fad-153">From the drop-down list, select **==**.</span></span>|  
    |<span data-ttu-id="38fad-154">**Valeur**</span><span class="sxs-lookup"><span data-stu-id="38fad-154">**Value**</span></span>|<span data-ttu-id="38fad-155">Type Tutorial_IA_InputRequest_SnF.</span><span class="sxs-lookup"><span data-stu-id="38fad-155">Type Tutorial_IA_InputRequest_SnF.</span></span>|  
    |<span data-ttu-id="38fad-156">**Regrouper par**</span><span class="sxs-lookup"><span data-stu-id="38fad-156">**Group by**</span></span>|<span data-ttu-id="38fad-157">Laissez la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="38fad-157">Leave the default value.</span></span>|  
  
10. <span data-ttu-id="38fad-158">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="38fad-158">Click **OK**.</span></span>  
  
## <a name="complete-steps"></a><span data-ttu-id="38fad-159">Étapes à suivre</span><span class="sxs-lookup"><span data-stu-id="38fad-159">Complete steps</span></span>
 <span data-ttu-id="38fad-160">[Étape 3 : Créer des Ports d’envoi et Ports de réception pour le magasin d’interagir et d’un scénario avant](../../adapters-and-accelerators/fileact-interact/step-3-create-send-and-receive-ports-for-interact-store-and-forward-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="38fad-160">[Step 3: Create Send Ports and Receive Ports for the InterAct Store and Forward Scenario](../../adapters-and-accelerators/fileact-interact/step-3-create-send-and-receive-ports-for-interact-store-and-forward-scenario.md) </span></span>  
 <span data-ttu-id="38fad-161">[Étape 3 a : ajouter un fichier emplacement de réception pour le magasin d’interagir et d’un scénario avant](../../adapters-and-accelerators/fileact-interact/step-3a-add-a-file-receive-location-for-interact-store-and-forward-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="38fad-161">[Step 3A: Add a FILE Receive Location for the InterAct Store and Forward Scenario](../../adapters-and-accelerators/fileact-interact/step-3a-add-a-file-receive-location-for-interact-store-and-forward-scenario.md) </span></span>  
 <span data-ttu-id="38fad-162">[Étape 3 b : ajouter un interagir emplacement de réception pour le magasin d’interagir et d’un scénario avant](../../adapters-and-accelerators/fileact-interact/step-3b-add-interact-receive-location-for-interact-store-and-forward-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="38fad-162">[Step 3B: Add an INTERACT Receive Location for the InterAct Store and Forward Scenario](../../adapters-and-accelerators/fileact-interact/step-3b-add-interact-receive-location-for-interact-store-and-forward-scenario.md) </span></span>  
 [<span data-ttu-id="38fad-163">Étape 3C : Ajouter un port d’envoi FILE pour capturer le message Sw:HandleRequest pour le scénario de stockage et de redirection InterAct</span><span class="sxs-lookup"><span data-stu-id="38fad-163">Step 3C: Add a FILE Send Port to Capture the Sw:HandleRequest Message for the InterAct Store and Forward Scenario</span></span>](../../adapters-and-accelerators/fileact-interact/step-3c-add-file-send-port-to-get-sw-handlerequest-interact-store-and-forward.md)  