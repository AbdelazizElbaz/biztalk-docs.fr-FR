---
title: "Étape 2c : ajouter un Port d’envoi FILEACT pour et le scénario de transfert (Pull) de FileAct | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8743a868-9625-477b-a7da-673bfa262723
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 803a8c671081afd3ba18b81d4770b80b26205eaf
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="step-2c-add-a-fileact-send-port-for-the-fileact-store-and-forward-pull-scenario"></a><span data-ttu-id="92060-102">Étape 2c : ajouter un Port d’envoi FILEACT pour et le scénario de transfert (Pull) de FileAct</span><span class="sxs-lookup"><span data-stu-id="92060-102">Step 2C: Add a FILEACT Send Port for the FileAct Store and Forward (Pull) Scenario</span></span>
<span data-ttu-id="92060-103">Avant de commencer cette étape, vous devez effectuer [étape 2 b : ajouter des Ports d’envoi FILE pour capturer le Sw:HandleFileRequest et les Messages Sw:HandleSnFRequest et le scénario de (extraits) avant de FileAct](../../adapters-and-accelerators/fileact-interact/step-2b-add-file-send-ports--get-sw-handlefilerequest-and-sw-handlesnfrequest.md).</span><span class="sxs-lookup"><span data-stu-id="92060-103">Before you begin this step, you must complete [Step 2B: Add FILE Send Ports to Capture the Sw:HandleFileRequest and Sw:HandleSnFRequest Messages for the FileAct Store and Forward (Pull) Scenario](../../adapters-and-accelerators/fileact-interact/step-2b-add-file-send-ports--get-sw-handlefilerequest-and-sw-handlesnfrequest.md).</span></span>  
  
### <a name="to-add-a-fileact-send-port"></a><span data-ttu-id="92060-104">Pour ajouter un port d’envoi FileACT</span><span class="sxs-lookup"><span data-stu-id="92060-104">To add a FileACT send port</span></span>  
  
1.  <span data-ttu-id="92060-105">Démarrer **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="92060-105">Start **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="92060-106">Dans l’arborescence de la console, développez le groupe BizTalk, puis développez l’application BizTalk pour laquelle vous souhaitez créer un port d’envoi.</span><span class="sxs-lookup"><span data-stu-id="92060-106">In the console tree, expand the BizTalk group, and then expand the BizTalk application for which you want to create a send port.</span></span>  
  
3.  <span data-ttu-id="92060-107">Avec le bouton droit **Ports d’envoi**, pointez sur **nouveau**, puis cliquez sur **Port d’envoi statique avec sollicitation-réponse**.</span><span class="sxs-lookup"><span data-stu-id="92060-107">Right-click **Send Ports**, point to **New**, and then click **Static Solicit-Response Send Port**.</span></span>  
  
4.  <span data-ttu-id="92060-108">Dans le **propriétés de Port d’envoi** fenêtre, le nom du port d’envoi **Tutorial_FA_SendRequest_SnF**.</span><span class="sxs-lookup"><span data-stu-id="92060-108">In the **Send Port Properties** window, name the send port, **Tutorial_FA_SendRequest_SnF**.</span></span>  
  
5.  <span data-ttu-id="92060-109">Dans le **propriétés de Port d’envoi** fenêtre, à partir de la **type de Transport** la liste déroulante, sélectionnez **FILEACT**, puis cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="92060-109">In the **Send Port Properties** window, from the **Transport type** drop-down list, select **FILEACT**, and then click **Configure**.</span></span>  
  
6.  <span data-ttu-id="92060-110">Dans le **propriétés du Transport FILEACT** boîte de dialogue zone, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="92060-110">In the **FILEACT Transport Properties** dialog box, do the following:</span></span>  
  
    |<span data-ttu-id="92060-111">**Utilisez cette**</span><span class="sxs-lookup"><span data-stu-id="92060-111">**Use this**</span></span>|<span data-ttu-id="92060-112">**Pour ce faire**</span><span class="sxs-lookup"><span data-stu-id="92060-112">**To do this**</span></span>|  
    |------------------|--------------------|  
    |<span data-ttu-id="92060-113">**Mot de passe**</span><span class="sxs-lookup"><span data-stu-id="92060-113">**Password**</span></span>|<span data-ttu-id="92060-114">Définissez le mot de passe pour la connectivité des trous.</span><span class="sxs-lookup"><span data-stu-id="92060-114">Set the password as appropriate for SAG connectivity.</span></span>|  
    |<span data-ttu-id="92060-115">**Nom d'utilisateur**</span><span class="sxs-lookup"><span data-stu-id="92060-115">**User name**</span></span>|<span data-ttu-id="92060-116">Définissez le nom d’utilisateur pour la connectivité des trous.</span><span class="sxs-lookup"><span data-stu-id="92060-116">Set the user name as appropriate for SAG connectivity.</span></span>|  
    |<span data-ttu-id="92060-117">**Mode de l’adaptateur**</span><span class="sxs-lookup"><span data-stu-id="92060-117">**Adapter Mode**</span></span>|<span data-ttu-id="92060-118">Dans la liste déroulante, sélectionnez **stocker et transférer**.</span><span class="sxs-lookup"><span data-stu-id="92060-118">From the drop-down list, select **Store and Forward**.</span></span>|  
    |<span data-ttu-id="92060-119">**Indicateur de non répudiation**</span><span class="sxs-lookup"><span data-stu-id="92060-119">**Non-Repudiation Indicator**</span></span>|<span data-ttu-id="92060-120">Dans la liste déroulante, sélectionnez **FALSE**.</span><span class="sxs-lookup"><span data-stu-id="92060-120">From the drop-down list, select **FALSE**.</span></span>|  
    |<span data-ttu-id="92060-121">**Type de demande**</span><span class="sxs-lookup"><span data-stu-id="92060-121">**Request Type**</span></span>|<span data-ttu-id="92060-122">A la valeur approprié \<RequestType\> chaîne, en fonction de votre configuration avec SWIFT.</span><span class="sxs-lookup"><span data-stu-id="92060-122">Set to the appropriate \<RequestType\> string, based on your provisioning with SWIFT.</span></span>|  
    |<span data-ttu-id="92060-123">**RequestCrypto**</span><span class="sxs-lookup"><span data-stu-id="92060-123">**RequestCrypto**</span></span>|<span data-ttu-id="92060-124">Dans la liste déroulante, sélectionnez **FALSE**.</span><span class="sxs-lookup"><span data-stu-id="92060-124">From the drop-down list, select **FALSE**.</span></span>|  
    |<span data-ttu-id="92060-125">**Demandeur**</span><span class="sxs-lookup"><span data-stu-id="92060-125">**Requestor**</span></span>|<span data-ttu-id="92060-126">A la valeur approprié \<demandeur\> chaîne, en fonction de votre configuration avec SWIFT.</span><span class="sxs-lookup"><span data-stu-id="92060-126">Set to the appropriate \<Requestor\> string, based on your provisioning with SWIFT.</span></span>|  
    |<span data-ttu-id="92060-127">**Répondeur**</span><span class="sxs-lookup"><span data-stu-id="92060-127">**Responder**</span></span>|<span data-ttu-id="92060-128">A la valeur approprié \<répondeur\> chaîne.</span><span class="sxs-lookup"><span data-stu-id="92060-128">Set to the appropriate \<Responder\> string.</span></span>|  
    |<span data-ttu-id="92060-129">**Nom du service**</span><span class="sxs-lookup"><span data-stu-id="92060-129">**Service Name**</span></span>|<span data-ttu-id="92060-130">A la valeur approprié  **\<nom du service\>**.</span><span class="sxs-lookup"><span data-stu-id="92060-130">Set to the appropriate **\<service name\>**.</span></span>|  
    |<span data-ttu-id="92060-131">**Indicateur d’accusé de réception**</span><span class="sxs-lookup"><span data-stu-id="92060-131">**Acknowledgement Indicator**</span></span>|<span data-ttu-id="92060-132">Dans la liste déroulante, sélectionnez **FALSE**.</span><span class="sxs-lookup"><span data-stu-id="92060-132">From the drop-down list, select **FALSE**.</span></span>|  
    |<span data-ttu-id="92060-133">**Fin de l’événement**</span><span class="sxs-lookup"><span data-stu-id="92060-133">**Event end-point**</span></span>|<span data-ttu-id="92060-134">Dans la liste déroulante, sélectionnez **FALSE**.</span><span class="sxs-lookup"><span data-stu-id="92060-134">From the drop-down list, select **FALSE**.</span></span>|  
    |<span data-ttu-id="92060-135">**Compression de fichiers**</span><span class="sxs-lookup"><span data-stu-id="92060-135">**File Compression**</span></span>|<span data-ttu-id="92060-136">Dans la liste déroulante, sélectionnez **aucun**.</span><span class="sxs-lookup"><span data-stu-id="92060-136">From the drop-down list, select **None**.</span></span>|  
    |<span data-ttu-id="92060-137">**Nom du dossier physique**</span><span class="sxs-lookup"><span data-stu-id="92060-137">**Physical Folder Name**</span></span>|<span data-ttu-id="92060-138">Tapez C:\SWIFTAdapterTutorial\Fileact\ClientLocation.</span><span class="sxs-lookup"><span data-stu-id="92060-138">Type C:\SWIFTAdapterTutorial\Fileact\ClientLocation.</span></span>|  
    |<span data-ttu-id="92060-139">**Transfert de point de terminaison**</span><span class="sxs-lookup"><span data-stu-id="92060-139">**Transfer end-point**</span></span>|<span data-ttu-id="92060-140">Tapez le point de terminaison approprié pour le jeu de routage trous.</span><span class="sxs-lookup"><span data-stu-id="92060-140">Type the appropriate end-point for the SAG routing set.</span></span> <span data-ttu-id="92060-141">Cette valeur doit correspondre au point de terminaison SNL que vous avez configuré dans les trous.</span><span class="sxs-lookup"><span data-stu-id="92060-141">This value should match the SNL endpoint you configured in SAG.</span></span>|  
    |<span data-ttu-id="92060-142">**Profil_service**</span><span class="sxs-lookup"><span data-stu-id="92060-142">**ServiceProfile**</span></span>|<span data-ttu-id="92060-143">Dans la liste déroulante, sélectionnez **nombre de transactions**.</span><span class="sxs-lookup"><span data-stu-id="92060-143">From the drop-down list, select **Transaction Count**.</span></span>|  
    |<span data-ttu-id="92060-144">**Accusé de réception**</span><span class="sxs-lookup"><span data-stu-id="92060-144">**Delivery notification**</span></span>|<span data-ttu-id="92060-145">Dans la liste déroulante, sélectionnez **FALSE**.</span><span class="sxs-lookup"><span data-stu-id="92060-145">From the drop-down list, select **FALSE**.</span></span>|  
    |<span data-ttu-id="92060-146">**File d’attente de notification**</span><span class="sxs-lookup"><span data-stu-id="92060-146">**Notify queue**</span></span>|<span data-ttu-id="92060-147">Tapez le nom de la file d’attente, en fonction de votre configuration avec SWIFT.</span><span class="sxs-lookup"><span data-stu-id="92060-147">Type the queue name, based on your provisioning with SWIFT.</span></span>|  
  
    > [!NOTE]
    >  <span data-ttu-id="92060-148">Si le message avec le nombre de transactions doit être transféré, définir le Mode de profil de Service pour « nombre de transactions » dans le FileAct port d’envoi.</span><span class="sxs-lookup"><span data-stu-id="92060-148">If message with Transaction Count is to be transferred, set the Service Profile Mode to “Transaction Count” in the FileAct send port.</span></span>  
  
7.  <span data-ttu-id="92060-149">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="92060-149">Click **OK**.</span></span>  
  
8.  <span data-ttu-id="92060-150">Dans le **propriétés de Port d’envoi** fenêtre, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="92060-150">In the **Send Port Properties** window, do the following:</span></span>  
  
    |<span data-ttu-id="92060-151">**Utilisez cette**</span><span class="sxs-lookup"><span data-stu-id="92060-151">**Use this**</span></span>|<span data-ttu-id="92060-152">**Pour ce faire**</span><span class="sxs-lookup"><span data-stu-id="92060-152">**To do this**</span></span>|  
    |------------------|--------------------|  
    |<span data-ttu-id="92060-153">**Gestionnaire d’envoi**</span><span class="sxs-lookup"><span data-stu-id="92060-153">**Send handler**</span></span>|<span data-ttu-id="92060-154">Dans la liste déroulante, sélectionnez le **FileActHost**.</span><span class="sxs-lookup"><span data-stu-id="92060-154">From the drop-down list, select the **FileActHost**.</span></span>|  
    |<span data-ttu-id="92060-155">**Pipeline d’envoi**</span><span class="sxs-lookup"><span data-stu-id="92060-155">**Send pipeline**</span></span>|<span data-ttu-id="92060-156">Dans la liste déroulante, sélectionnez **XMLTransmit**.</span><span class="sxs-lookup"><span data-stu-id="92060-156">From the drop-down list, select **XMLTransmit**.</span></span>|  
    |<span data-ttu-id="92060-157">**Pipeline de réception**</span><span class="sxs-lookup"><span data-stu-id="92060-157">**Receive pipeline**</span></span>|<span data-ttu-id="92060-158">Dans la liste déroulante, sélectionnez **XMLReceive**.</span><span class="sxs-lookup"><span data-stu-id="92060-158">From the drop-down list, select **XMLReceive**.</span></span>|  
  
9. <span data-ttu-id="92060-159">Dans le **propriétés de Port d’envoi** fenêtre, dans le **filtres** onglet, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="92060-159">In the **Send Port Properties** window, on the **Filters** tab, do the following:</span></span>  
  
    |<span data-ttu-id="92060-160">**Utilisez cette**</span><span class="sxs-lookup"><span data-stu-id="92060-160">**Use this**</span></span>|<span data-ttu-id="92060-161">**Pour ce faire**</span><span class="sxs-lookup"><span data-stu-id="92060-161">**To do this**</span></span>|  
    |------------------|--------------------|  
    |<span data-ttu-id="92060-162">**Propriété**</span><span class="sxs-lookup"><span data-stu-id="92060-162">**Property**</span></span>|<span data-ttu-id="92060-163">Dans la liste déroulante, sélectionnez **BTS. ReceivePortName**.</span><span class="sxs-lookup"><span data-stu-id="92060-163">From the drop-down list, select **BTS.ReceivePortName**.</span></span>|  
    |<span data-ttu-id="92060-164">**Opérateur**</span><span class="sxs-lookup"><span data-stu-id="92060-164">**Operator**</span></span>|<span data-ttu-id="92060-165">Dans la liste déroulante, sélectionnez  **==** .</span><span class="sxs-lookup"><span data-stu-id="92060-165">From the drop-down list, select **==**.</span></span>|  
    |<span data-ttu-id="92060-166">**Valeur**</span><span class="sxs-lookup"><span data-stu-id="92060-166">**Value**</span></span>|<span data-ttu-id="92060-167">Type **Tutorial_IA_InputRequest_SnF**.</span><span class="sxs-lookup"><span data-stu-id="92060-167">Type **Tutorial_IA_InputRequest_SnF**.</span></span>|  
    |<span data-ttu-id="92060-168">**Regrouper par**</span><span class="sxs-lookup"><span data-stu-id="92060-168">**Group by**</span></span>|<span data-ttu-id="92060-169">Laissez la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="92060-169">Leave the default value.</span></span>|  
  
10. <span data-ttu-id="92060-170">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="92060-170">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92060-171">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="92060-171">See Also</span></span>  
 <span data-ttu-id="92060-172">[Étape 2 a : ajouter le fichier emplacements de réception pour le magasin de FileAct et d’un scénario de transfert (extraction de données)](../../adapters-and-accelerators/fileact-interact/step-2a-add-file-receive-locations-for-fileact-store-and-forward-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="92060-172">[Step 2A: Add FILE Receive Locations for the FileAct Store and Forward (Pull) Scenario](../../adapters-and-accelerators/fileact-interact/step-2a-add-file-receive-locations-for-fileact-store-and-forward-scenario.md) </span></span>  
 [<span data-ttu-id="92060-173">Étape 2B : Ajouter des ports d’envoi FILE pour capturer les messages Sw:HandleFileRequest et Sw:HandleSnFRequest pour le scénario de stockage et de redirection (Pull) FileAct</span><span class="sxs-lookup"><span data-stu-id="92060-173">Step 2B: Add FILE Send Ports to Capture the Sw:HandleFileRequest and Sw:HandleSnFRequest Messages for the FileAct Store and Forward (Pull) Scenario</span></span>](../../adapters-and-accelerators/fileact-interact/step-2b-add-file-send-ports--get-sw-handlefilerequest-and-sw-handlesnfrequest.md)