---
title: "Étape 2c : ajouter un Port d’envoi interagissent pour le magasin d’interagir et le scénario de transfert (Pull) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 57038f77-85c3-4811-ab3d-df6e2da8fbcf
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fb46943b20676dbe98f79db8760043bb51606c56
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="step-2c-add-an-interact-send-port-for-the-interact-store-and-forward-pull-scenario"></a><span data-ttu-id="95eae-102">Étape 2c : ajouter un Port d’envoi interagissent pour le magasin d’interagir et le scénario de transfert (Pull)</span><span class="sxs-lookup"><span data-stu-id="95eae-102">Step 2C: Add an INTERACT Send Port for the InterAct Store and Forward (Pull) Scenario</span></span>
<span data-ttu-id="95eae-103">Avant de commencer cette étape, vous devez effectuer [étape 2 b : ajouter des Ports d’envoi FILE pour capturer le Message Sw:HandleRequest pour le magasin d’interagir et le scénario de (Pull) vers l’avant](../../adapters-and-accelerators/fileact-interact/step-2b-add-file-send-ports-to-get-sw-handlerequest-message-for-interact.md).</span><span class="sxs-lookup"><span data-stu-id="95eae-103">Before you begin this step, you must complete [Step 2B: Add FILE Send Ports to Capture the Sw:HandleRequest Message for the InterAct Store and Forward (Pull) Scenario](../../adapters-and-accelerators/fileact-interact/step-2b-add-file-send-ports-to-get-sw-handlerequest-message-for-interact.md).</span></span>  
  
### <a name="to-add-an-interact-send-port"></a><span data-ttu-id="95eae-104">Pour ajouter un port d’envoi INTERACT</span><span class="sxs-lookup"><span data-stu-id="95eae-104">To add an INTERACT send port</span></span>  
  
1.  <span data-ttu-id="95eae-105">Démarrer **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="95eae-105">Start **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="95eae-106">Dans l’arborescence de la console, développez le groupe BizTalk, puis développez l’application BizTalk pour laquelle vous souhaitez créer un port d’envoi.</span><span class="sxs-lookup"><span data-stu-id="95eae-106">In the console tree, expand the BizTalk group, and then expand the BizTalk application for which you want to create a send port.</span></span>  
  
3.  <span data-ttu-id="95eae-107">Avec le bouton droit **Ports d’envoi**, pointez sur **nouveau**, puis cliquez sur **Port d’envoi statique avec sollicitation-réponse**.</span><span class="sxs-lookup"><span data-stu-id="95eae-107">Right-click **Send Ports**, point to **New**, and then click **Static Solicit-Response Send Port**.</span></span>  
  
4.  <span data-ttu-id="95eae-108">Dans le **propriétés de Port d’envoi** fenêtre, le nom du port d’envoi **Tutorial_IA_SendRequest_SnF**.</span><span class="sxs-lookup"><span data-stu-id="95eae-108">In the **Send Port Properties** window, name the send port, **Tutorial_IA_SendRequest_SnF**.</span></span>  
  
5.  <span data-ttu-id="95eae-109">Dans le **propriétés de Port d’envoi** fenêtre, à partir de la **type de Transport** la liste déroulante, sélectionnez **interagir**, puis cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="95eae-109">In the **Send Port Properties** window, from the **Transport type** drop-down list, select **INTERACT**, and then click **Configure**.</span></span>  
  
6.  <span data-ttu-id="95eae-110">Dans le **propriétés du Transport interagir** boîte de dialogue zone, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="95eae-110">In the **INTERACT Transport Properties** dialog box, do the following:</span></span>  
  
    |<span data-ttu-id="95eae-111">**Utilisez cette**</span><span class="sxs-lookup"><span data-stu-id="95eae-111">**Use this**</span></span>|<span data-ttu-id="95eae-112">**Pour ce faire**</span><span class="sxs-lookup"><span data-stu-id="95eae-112">**To do this**</span></span>|  
    |------------------|--------------------|  
    |<span data-ttu-id="95eae-113">**Mot de passe**</span><span class="sxs-lookup"><span data-stu-id="95eae-113">**Password**</span></span>|<span data-ttu-id="95eae-114">Définissez le mot de passe pour la connectivité des trous.</span><span class="sxs-lookup"><span data-stu-id="95eae-114">Set the password as appropriate for SAG connectivity.</span></span>|  
    |<span data-ttu-id="95eae-115">**Nom d'utilisateur**</span><span class="sxs-lookup"><span data-stu-id="95eae-115">**User name**</span></span>|<span data-ttu-id="95eae-116">Définissez le nom d’utilisateur pour la connectivité des trous.</span><span class="sxs-lookup"><span data-stu-id="95eae-116">Set the user name as appropriate for SAG connectivity.</span></span>|  
    |<span data-ttu-id="95eae-117">**Format de message**</span><span class="sxs-lookup"><span data-stu-id="95eae-117">**Message format**</span></span>|<span data-ttu-id="95eae-118">**InteractMessage**</span><span class="sxs-lookup"><span data-stu-id="95eae-118">**InteractMessage**</span></span>|  
    |<span data-ttu-id="95eae-119">**Indicateur de non répudiation**</span><span class="sxs-lookup"><span data-stu-id="95eae-119">**Non-Repudiation Indicator**</span></span>|<span data-ttu-id="95eae-120">**FALSE**</span><span class="sxs-lookup"><span data-stu-id="95eae-120">**FALSE**</span></span>|  
    |<span data-ttu-id="95eae-121">**Type de demande**</span><span class="sxs-lookup"><span data-stu-id="95eae-121">**Request Type**</span></span>|<span data-ttu-id="95eae-122">Tapez la commande appropriée \<RequestType\> chaîne, en fonction de votre configuration avec SWIFT.</span><span class="sxs-lookup"><span data-stu-id="95eae-122">Type the appropriate \<RequestType\> string, based on your provisioning with SWIFT.</span></span>|  
    |<span data-ttu-id="95eae-123">**ResponseCrypto**</span><span class="sxs-lookup"><span data-stu-id="95eae-123">**ResponseCrypto**</span></span>|<span data-ttu-id="95eae-124">**FALSE**</span><span class="sxs-lookup"><span data-stu-id="95eae-124">**FALSE**</span></span>|  
    |<span data-ttu-id="95eae-125">**Demandeur**</span><span class="sxs-lookup"><span data-stu-id="95eae-125">**Requestor**</span></span>|<span data-ttu-id="95eae-126">Tapez la commande appropriée \<RequestorDN\> chaîne, en fonction de votre configuration avec SWIFT.</span><span class="sxs-lookup"><span data-stu-id="95eae-126">Type the appropriate \<RequestorDN\> string, based on your provisioning with SWIFT.</span></span>|  
    |<span data-ttu-id="95eae-127">**Répondeur**</span><span class="sxs-lookup"><span data-stu-id="95eae-127">**Responder**</span></span>|<span data-ttu-id="95eae-128">Tapez la commande appropriée \<ResponderDN\> chaîne, en fonction de votre configuration avec SWIFT.</span><span class="sxs-lookup"><span data-stu-id="95eae-128">Type the appropriate \<ResponderDN\> string, based on your provisioning with SWIFT.</span></span>|  
    |<span data-ttu-id="95eae-129">**Nom du service**</span><span class="sxs-lookup"><span data-stu-id="95eae-129">**Service Name**</span></span>|<span data-ttu-id="95eae-130">Tapez la commande appropriée \<nom du service\>, en fonction de votre configuration avec SWIFT.</span><span class="sxs-lookup"><span data-stu-id="95eae-130">Type the appropriate \<service name\>, based on your provisioning with SWIFT.</span></span>|  
    |<span data-ttu-id="95eae-131">**Accusé de réception**</span><span class="sxs-lookup"><span data-stu-id="95eae-131">**Delivery Notification**</span></span>|<span data-ttu-id="95eae-132">Dans la liste déroulante, sélectionnez **FALSE**.</span><span class="sxs-lookup"><span data-stu-id="95eae-132">From the drop-down list, select **FALSE**.</span></span>|  
    |<span data-ttu-id="95eae-133">**File d’attente de notification**</span><span class="sxs-lookup"><span data-stu-id="95eae-133">**Notify queue**</span></span>|<span data-ttu-id="95eae-134">Tapez le nom de la file d’attente appropriée, en fonction de votre configuration avec SWIFT.</span><span class="sxs-lookup"><span data-stu-id="95eae-134">Type the appropriate queue name, based on your provisioning with SWIFT.</span></span>|  
  
    > [!NOTE]
    >  <span data-ttu-id="95eae-135">Si une seule charge utile doit être transféré, jeu du MessageFormat à « Charge » dans l’interagir port de réception et port d’envoi interagir.</span><span class="sxs-lookup"><span data-stu-id="95eae-135">If only payload is to be transferred, set the MessageFormat to “Payload” in the INTERACT receive port and INTERACT send port.</span></span> <span data-ttu-id="95eae-136">Affectez les pipelines de réception et d’envoi PassThru.</span><span class="sxs-lookup"><span data-stu-id="95eae-136">Set the Receive and Send pipelines to PassThru.</span></span>  
  
7.  <span data-ttu-id="95eae-137">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="95eae-137">Click **OK**.</span></span>  
  
8.  <span data-ttu-id="95eae-138">Dans le **propriétés de Port d’envoi** fenêtre, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="95eae-138">In the **Send Port Properties** window, do the following:</span></span>  
  
    |<span data-ttu-id="95eae-139">**Utilisez cette**</span><span class="sxs-lookup"><span data-stu-id="95eae-139">**Use this**</span></span>|<span data-ttu-id="95eae-140">**Pour ce faire**</span><span class="sxs-lookup"><span data-stu-id="95eae-140">**To do this**</span></span>|  
    |------------------|--------------------|  
    |<span data-ttu-id="95eae-141">**Gestionnaire d’envoi**</span><span class="sxs-lookup"><span data-stu-id="95eae-141">**Send handler**</span></span>|<span data-ttu-id="95eae-142">Dans la liste déroulante, sélectionnez l’hôte d’interagir.</span><span class="sxs-lookup"><span data-stu-id="95eae-142">From the drop-down list, select the Interact host.</span></span>|  
    |<span data-ttu-id="95eae-143">**Pipeline d’envoi**</span><span class="sxs-lookup"><span data-stu-id="95eae-143">**Send pipeline**</span></span>|<span data-ttu-id="95eae-144">Dans la liste déroulante, sélectionnez **XMLTransmit**.</span><span class="sxs-lookup"><span data-stu-id="95eae-144">From the drop-down list, select **XMLTransmit**.</span></span>|  
    |<span data-ttu-id="95eae-145">**Pipeline de réception**</span><span class="sxs-lookup"><span data-stu-id="95eae-145">**Receive pipeline**</span></span>|<span data-ttu-id="95eae-146">Dans la liste déroulante, sélectionnez **XMLReceive**.</span><span class="sxs-lookup"><span data-stu-id="95eae-146">From the drop-down list, select **XMLReceive**.</span></span>|  
  
9. <span data-ttu-id="95eae-147">Dans le **propriétés de Port d’envoi** fenêtre, dans le **filtres** onglet, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="95eae-147">In the **Send Port Properties** window, on the **Filters** tab, do the following:</span></span>  
  
    |<span data-ttu-id="95eae-148">**Utilisez cette**</span><span class="sxs-lookup"><span data-stu-id="95eae-148">**Use this**</span></span>|<span data-ttu-id="95eae-149">**Pour ce faire**</span><span class="sxs-lookup"><span data-stu-id="95eae-149">**To do this**</span></span>|  
    |------------------|--------------------|  
    |<span data-ttu-id="95eae-150">**Propriété**</span><span class="sxs-lookup"><span data-stu-id="95eae-150">**Property**</span></span>|<span data-ttu-id="95eae-151">Dans la liste déroulante, sélectionnez **BTS. ReceivePortName**.</span><span class="sxs-lookup"><span data-stu-id="95eae-151">From the drop-down list, select **BTS.ReceivePortName**.</span></span>|  
    |<span data-ttu-id="95eae-152">**Opérateur**</span><span class="sxs-lookup"><span data-stu-id="95eae-152">**Operator**</span></span>|<span data-ttu-id="95eae-153">Dans la liste déroulante, sélectionnez  **==** .</span><span class="sxs-lookup"><span data-stu-id="95eae-153">From the drop-down list, select **==**.</span></span>|  
    |<span data-ttu-id="95eae-154">**Valeur**</span><span class="sxs-lookup"><span data-stu-id="95eae-154">**Value**</span></span>|<span data-ttu-id="95eae-155">Type **Tutorial_IA_InputRequest_SnF**.</span><span class="sxs-lookup"><span data-stu-id="95eae-155">Type **Tutorial_IA_InputRequest_SnF**.</span></span>|  
    |<span data-ttu-id="95eae-156">**Regrouper par**</span><span class="sxs-lookup"><span data-stu-id="95eae-156">**Group by**</span></span>|<span data-ttu-id="95eae-157">Laissez la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="95eae-157">Leave the default value.</span></span>|  
  
10. <span data-ttu-id="95eae-158">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="95eae-158">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95eae-159">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="95eae-159">See Also</span></span>  
 <span data-ttu-id="95eae-160">[Étape 2 a : ajouter le fichier emplacements de réception pour le magasin d’interagir et le scénario de transfert (Pull)](../../adapters-and-accelerators/fileact-interact/step-2a-add-file-receive-locations-for-interact-store-and-forward-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="95eae-160">[Step 2A: Add FILE Receive Locations for the InterAct Store and Forward (Pull) Scenario](../../adapters-and-accelerators/fileact-interact/step-2a-add-file-receive-locations-for-interact-store-and-forward-scenario.md) </span></span>  
 [<span data-ttu-id="95eae-161">Étape 2B : Ajouter des ports d’envoi FILE pour capturer le message Sw:HandleRequest pour le scénario de stockage et de redirection (Pull) InterAct</span><span class="sxs-lookup"><span data-stu-id="95eae-161">Step 2B: Add FILE Send Ports to Capture the Sw:HandleRequest Message for the InterAct Store and Forward (Pull) Scenario</span></span>](../../adapters-and-accelerators/fileact-interact/step-2b-add-file-send-ports-to-get-sw-handlerequest-message-for-interact.md)