---
title: "Étape 3E : ajouter un Port d’envoi interagir pour l’interaction scénario en temps réel | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d9522386-e980-4ab1-b65a-939ca7936ad9
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ec380c088f27fe09f518c385990e3801b5c019dd
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="step-3e-add-an-interact-send-port-for-the-interact-real-time-scenario"></a><span data-ttu-id="356bb-102">Étape 3E : ajouter un Port d’envoi interagir pour l’interaction scénario en temps réel</span><span class="sxs-lookup"><span data-stu-id="356bb-102">Step 3E: Add an INTERACT Send Port for the InterAct Real-Time Scenario</span></span>
<span data-ttu-id="356bb-103">Complète [étape 3D : ajouter un Port d’envoi FILE pour capturer le Message Sw:HandleResponse pour le scénario en temps réel interagir](../../adapters-and-accelerators/fileact-interact/step-3d-add-file-send-port-to-get-sw-handleresponse-message-for-interact.md) avant de commencer cette étape.</span><span class="sxs-lookup"><span data-stu-id="356bb-103">Complete [Step 3D: Add a FILE Send Port to Capture the Sw:HandleResponse Message for the InterAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-3d-add-file-send-port-to-get-sw-handleresponse-message-for-interact.md) before you begin this step.</span></span>
  
## <a name="add-an-interact-send-port"></a><span data-ttu-id="356bb-104">Ajouter un port d’envoi INTERACT</span><span class="sxs-lookup"><span data-stu-id="356bb-104">Add an INTERACT send port</span></span>  
  
1.  <span data-ttu-id="356bb-105">Démarrer **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="356bb-105">Start **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="356bb-106">Dans l’arborescence de la console, développez le groupe BizTalk, puis développez l’application BizTalk pour laquelle vous souhaitez créer un port d’envoi.</span><span class="sxs-lookup"><span data-stu-id="356bb-106">In the console tree, expand the BizTalk group, and then expand the BizTalk application for which you want to create a send port.</span></span>  
  
3.  <span data-ttu-id="356bb-107">Avec le bouton droit **Ports d’envoi**, pointez sur **nouveau**, puis cliquez sur **Port d’envoi statique avec sollicitation-réponse**.</span><span class="sxs-lookup"><span data-stu-id="356bb-107">Right-click **Send Ports**, point to **New**, and then click **Static Solicit-Response Send Port**.</span></span>  
  
4.  <span data-ttu-id="356bb-108">Dans le **propriétés de Port d’envoi** fenêtre, le nom du port d’envoi **Tutorial_IA_SendRequest_RealTime**.</span><span class="sxs-lookup"><span data-stu-id="356bb-108">In the **Send Port Properties** window, name the send port **Tutorial_IA_SendRequest_RealTime**.</span></span>  
  
5.  <span data-ttu-id="356bb-109">Dans le **propriétés de Port d’envoi** fenêtre, à partir de la **type de Transport** la liste déroulante, sélectionnez **interagir**, puis cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="356bb-109">In the **Send Port Properties** window, from the **Transport type** drop-down list, select **INTERACT**, and then click **Configure**.</span></span>  
  
6.  <span data-ttu-id="356bb-110">Dans le **propriétés du Transport interagir** boîte de dialogue zone, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="356bb-110">In the **INTERACT Transport Properties** dialog box, do the following:</span></span>  
  
    |<span data-ttu-id="356bb-111">**Utilisez cette**</span><span class="sxs-lookup"><span data-stu-id="356bb-111">**Use this**</span></span>|<span data-ttu-id="356bb-112">**Pour ce faire**</span><span class="sxs-lookup"><span data-stu-id="356bb-112">**To do this**</span></span>|  
    |------------------|--------------------|  
    |<span data-ttu-id="356bb-113">**Mot de passe**</span><span class="sxs-lookup"><span data-stu-id="356bb-113">**Password**</span></span>|<span data-ttu-id="356bb-114">Définissez le mot de passe pour la connectivité des trous.</span><span class="sxs-lookup"><span data-stu-id="356bb-114">Set the password as appropriate for SAG connectivity.</span></span>|  
    |<span data-ttu-id="356bb-115">**Nom d'utilisateur**</span><span class="sxs-lookup"><span data-stu-id="356bb-115">**User name**</span></span>|<span data-ttu-id="356bb-116">Définissez le nom d’utilisateur pour la connectivité des trous.</span><span class="sxs-lookup"><span data-stu-id="356bb-116">Set the user name as appropriate for SAG connectivity.</span></span>|  
    |<span data-ttu-id="356bb-117">**Mode de l’adaptateur**</span><span class="sxs-lookup"><span data-stu-id="356bb-117">**Adapter Mode**</span></span>|<span data-ttu-id="356bb-118">Dans la liste déroulante, sélectionnez **en temps réel**.</span><span class="sxs-lookup"><span data-stu-id="356bb-118">From the drop-down list, select **RealTime**.</span></span>|  
    |<span data-ttu-id="356bb-119">**Format de message**</span><span class="sxs-lookup"><span data-stu-id="356bb-119">**Message format**</span></span>|<span data-ttu-id="356bb-120">**InteractMessage**.</span><span class="sxs-lookup"><span data-stu-id="356bb-120">**InteractMessage**.</span></span>|  
    |<span data-ttu-id="356bb-121">**Indicateur de non répudiation**</span><span class="sxs-lookup"><span data-stu-id="356bb-121">**Non-Repudiation Indicator**</span></span>|<span data-ttu-id="356bb-122">**FALSE**.</span><span class="sxs-lookup"><span data-stu-id="356bb-122">**FALSE**.</span></span>|  
    |<span data-ttu-id="356bb-123">**Type de demande**</span><span class="sxs-lookup"><span data-stu-id="356bb-123">**Request Type**</span></span>|<span data-ttu-id="356bb-124">Tapez la commande appropriée \<RequestType\> chaîne, en fonction de votre configuration avec SWIFT.</span><span class="sxs-lookup"><span data-stu-id="356bb-124">Type the appropriate \<RequestType\> string, based on your provisioning with SWIFT.</span></span>|  
    |<span data-ttu-id="356bb-125">**ResponseCrypto**</span><span class="sxs-lookup"><span data-stu-id="356bb-125">**ResponseCrypto**</span></span>|<span data-ttu-id="356bb-126">**FALSE**.</span><span class="sxs-lookup"><span data-stu-id="356bb-126">**FALSE**.</span></span>|  
    |<span data-ttu-id="356bb-127">**Demandeur**</span><span class="sxs-lookup"><span data-stu-id="356bb-127">**Requestor**</span></span>|<span data-ttu-id="356bb-128">Affectez-lui la valeur approprié \<demandeur\> chaîne, en fonction de votre configuration avec SWIFT.</span><span class="sxs-lookup"><span data-stu-id="356bb-128">Set it to the appropriate \<Requestor\> string, based on your provisioning with SWIFT.</span></span>|  
    |<span data-ttu-id="356bb-129">**Répondeur**</span><span class="sxs-lookup"><span data-stu-id="356bb-129">**Responder**</span></span>|<span data-ttu-id="356bb-130">Affectez-lui la valeur approprié \<répondeur\> chaîne, en fonction de votre configuration avec SWIFT.</span><span class="sxs-lookup"><span data-stu-id="356bb-130">Set it to the appropriate \<Responder\> string, based on your provisioning with SWIFT.</span></span>|  
    |<span data-ttu-id="356bb-131">**Nom du service**</span><span class="sxs-lookup"><span data-stu-id="356bb-131">**Service Name**</span></span>|<span data-ttu-id="356bb-132">Affectez-lui la valeur approprié \<nom du service\>, en fonction de votre configuration avec SWIFT.</span><span class="sxs-lookup"><span data-stu-id="356bb-132">Set it to the appropriate \<service name\>, based on your provisioning with SWIFT.</span></span>|  
    |<span data-ttu-id="356bb-133">**Accusé de réception**</span><span class="sxs-lookup"><span data-stu-id="356bb-133">**Delivery Notification**</span></span>|<span data-ttu-id="356bb-134">Dans la liste déroulante, sélectionnez **FALSE**.</span><span class="sxs-lookup"><span data-stu-id="356bb-134">From the drop-down list, select  **FALSE**.</span></span>|  
    |<span data-ttu-id="356bb-135">**File d’attente de notification**</span><span class="sxs-lookup"><span data-stu-id="356bb-135">**Notify queue**</span></span>|<span data-ttu-id="356bb-136">Tapez le nom de la file d’attente appropriée, en fonction de votre configuration avec SWIFT.</span><span class="sxs-lookup"><span data-stu-id="356bb-136">Type the appropriate queue name, based on your provisioning with SWIFT.</span></span>|  
  
    > [!NOTE]
    >  <span data-ttu-id="356bb-137">Si une seule charge utile doit être transféré, jeu du MessageFormat à « Payloadonly » dans l’interagir port de réception et port d’envoi interagir.</span><span class="sxs-lookup"><span data-stu-id="356bb-137">If only payload is to be transferred, set the MessageFormat to “Payloadonly” in the INTERACT receive port and INTERACT send port.</span></span> <span data-ttu-id="356bb-138">Définir la réception et pipelines d’envoi à PassThru.</span><span class="sxs-lookup"><span data-stu-id="356bb-138">Set the receive and send pipelines to PassThru.</span></span>  
  
7.  <span data-ttu-id="356bb-139">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="356bb-139">Click **OK**.</span></span>  
  
8.  <span data-ttu-id="356bb-140">Dans le **propriétés de Port d’envoi** fenêtre, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="356bb-140">In the **Send Port Properties** window, do the following:</span></span>  
  
    |<span data-ttu-id="356bb-141">**Utilisez cette**</span><span class="sxs-lookup"><span data-stu-id="356bb-141">**Use this**</span></span>|<span data-ttu-id="356bb-142">**Pour ce faire**</span><span class="sxs-lookup"><span data-stu-id="356bb-142">**To do this**</span></span>|  
    |------------------|--------------------|  
    |<span data-ttu-id="356bb-143">**Gestionnaire d’envoi**</span><span class="sxs-lookup"><span data-stu-id="356bb-143">**Send handler**</span></span>|<span data-ttu-id="356bb-144">Dans la liste déroulante, sélectionnez l’hôte d’interagir.</span><span class="sxs-lookup"><span data-stu-id="356bb-144">From the drop-down list, select the Interact host.</span></span>|  
    |<span data-ttu-id="356bb-145">**Pipeline d’envoi**</span><span class="sxs-lookup"><span data-stu-id="356bb-145">**Send pipeline**</span></span>|<span data-ttu-id="356bb-146">Dans la liste déroulante, sélectionnez **XMLTransmit**.</span><span class="sxs-lookup"><span data-stu-id="356bb-146">From the drop-down list, select **XMLTransmit**.</span></span>|  
    |<span data-ttu-id="356bb-147">**Pipeline de réception**</span><span class="sxs-lookup"><span data-stu-id="356bb-147">**Receive pipeline**</span></span>|<span data-ttu-id="356bb-148">**XMLReceive**</span><span class="sxs-lookup"><span data-stu-id="356bb-148">**XMLReceive**</span></span>|  
  
9. <span data-ttu-id="356bb-149">Dans le **propriétés de Port d’envoi** fenêtre, dans le **filtres** onglet, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="356bb-149">In the **Send Port Properties** window, on the **Filters** tab, do the following:</span></span>  
  
    |<span data-ttu-id="356bb-150">**Utilisez cette**</span><span class="sxs-lookup"><span data-stu-id="356bb-150">**Use this**</span></span>|<span data-ttu-id="356bb-151">**Pour ce faire**</span><span class="sxs-lookup"><span data-stu-id="356bb-151">**To do this**</span></span>|  
    |------------------|--------------------|  
    |<span data-ttu-id="356bb-152">**Propriété**</span><span class="sxs-lookup"><span data-stu-id="356bb-152">**Property**</span></span>|<span data-ttu-id="356bb-153">Dans la liste déroulante, sélectionnez **BTS. ReceivePortName**.</span><span class="sxs-lookup"><span data-stu-id="356bb-153">From the drop-down list, select **BTS.ReceivePortName**.</span></span>|  
    |<span data-ttu-id="356bb-154">**Opérateur**</span><span class="sxs-lookup"><span data-stu-id="356bb-154">**Operator**</span></span>|<span data-ttu-id="356bb-155">Dans la liste déroulante, sélectionnez  **==** .</span><span class="sxs-lookup"><span data-stu-id="356bb-155">From the drop-down list, select **==**.</span></span>|  
    |<span data-ttu-id="356bb-156">**Valeur**</span><span class="sxs-lookup"><span data-stu-id="356bb-156">**Value**</span></span>|<span data-ttu-id="356bb-157">Type **Tutorial_IA_InputRequest_RealTime**.</span><span class="sxs-lookup"><span data-stu-id="356bb-157">Type **Tutorial_IA_InputRequest_RealTime**.</span></span>|  
    |<span data-ttu-id="356bb-158">**Regrouper par**</span><span class="sxs-lookup"><span data-stu-id="356bb-158">**Group by**</span></span>|<span data-ttu-id="356bb-159">Laissez la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="356bb-159">Leave the default value.</span></span>|  
  
10. <span data-ttu-id="356bb-160">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="356bb-160">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="356bb-161">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="356bb-161">See Also</span></span>  
 <span data-ttu-id="356bb-162">[Étape 3 : Créer l’envoi et Ports de réception l’interaction du scénario en temps réel](../../adapters-and-accelerators/fileact-interact/step-3-create-send-and-receive-ports-for-the-interact-real-time-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="356bb-162">[Step 3: Create Send and Receive Ports for the InterAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-3-create-send-and-receive-ports-for-the-interact-real-time-scenario.md) </span></span>  
 <span data-ttu-id="356bb-163">[Étape 3 a : ajouter un fichier emplacement de réception pour l’interaction du scénario en temps réel](../../adapters-and-accelerators/fileact-interact/step-3a-add-a-file-receive-location-for-the-interact-real-time-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="356bb-163">[Step 3A: Add a FILE Receive Location for the InterAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-3a-add-a-file-receive-location-for-the-interact-real-time-scenario.md) </span></span>  
 <span data-ttu-id="356bb-164">[Étape 3 b : ajouter un interagir emplacement de réception pour l’interaction scénario en temps réel](../../adapters-and-accelerators/fileact-interact/step-3b-add-an-interact-receive-location-for-the-interact-real-time-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="356bb-164">[Step 3B: Add an INTERACT Receive Location for the InterAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-3b-add-an-interact-receive-location-for-the-interact-real-time-scenario.md) </span></span>  
 <span data-ttu-id="356bb-165">[Étape 3c : ajouter un Port d’envoi FILE pour capturer le Message Sw:HandleRequest pour l’interaction du scénario en temps réel](../../adapters-and-accelerators/fileact-interact/step-3c-add-file-send-port-to-get-sw-handlerequest-interact-real-time-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="356bb-165">[Step 3C: Add a FILE Send Port to Capture the Sw:HandleRequest Message for the InterAct Real-Time Scenario](../../adapters-and-accelerators/fileact-interact/step-3c-add-file-send-port-to-get-sw-handlerequest-interact-real-time-scenario.md) </span></span>  
 [<span data-ttu-id="356bb-166">Étape 3D : Ajouter un port d’envoi FILE pour capturer le message Sw:HandleResponse pour le scénario en temps réel InterAct</span><span class="sxs-lookup"><span data-stu-id="356bb-166">Step 3D: Add a FILE Send Port to Capture the Sw:HandleResponse Message for the InterAct Real-Time Scenario</span></span>](../../adapters-and-accelerators/fileact-interact/step-3d-add-file-send-port-to-get-sw-handleresponse-message-for-interact.md)