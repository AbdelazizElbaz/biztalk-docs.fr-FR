---
title: 'Étape 3 : Créer et déployer un Project_hl7_main d’événement (Message) de déclencheur | Documents Microsoft'
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- interrogative tutorial, trigger events
ms.assetid: 90b65ad1-7953-4009-a1eb-1c2a85c7980a
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5ba388eef1f5dbfb885e33c6263c4e0f8ef4be29
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="step-3-create-and-deploy-a-trigger-event-message-projecthl7main"></a><span data-ttu-id="c3cbd-102">Étape 3 : Créer et déployer un Project_hl7_main d’événement (Message) de déclencheur</span><span class="sxs-lookup"><span data-stu-id="c3cbd-102">Step 3: Create and Deploy a Trigger Event (Message) Project_hl7_main</span></span>
<span data-ttu-id="c3cbd-103">Dans cette étape, vous créez le schéma utilisé par un message d’événement déclencheur.</span><span class="sxs-lookup"><span data-stu-id="c3cbd-103">In this step, you create the schema used by a trigger event message.</span></span> <span data-ttu-id="c3cbd-104">Par exemple, le système décharge d’admission et de transfert (ADT) qui envoie un message à l’hôpital informations système (HIS).</span><span class="sxs-lookup"><span data-stu-id="c3cbd-104">For example, the Admissions Discharge and Transfer system (ADT) that sends a message to the Hospital Information System (HIS).</span></span> <span data-ttu-id="c3cbd-105">Ce schéma permet de définir le format de votre message.</span><span class="sxs-lookup"><span data-stu-id="c3cbd-105">You use this schema to define the format of your message.</span></span>  
  
### <a name="to-create-the-project-for-the-trigger-event-message"></a><span data-ttu-id="c3cbd-106">Pour créer le projet pour le message d’événement déclencheur</span><span class="sxs-lookup"><span data-stu-id="c3cbd-106">To create the project for the trigger event message</span></span>  
  
1.  <span data-ttu-id="c3cbd-107">Dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], dans le **fichier** menu, pointez sur **nouveau**, puis cliquez sur **projet**.</span><span class="sxs-lookup"><span data-stu-id="c3cbd-107">In [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], on the **File** menu, point to **New**, and then click **Project**.</span></span>  
  
2.  <span data-ttu-id="c3cbd-108">Dans la boîte de dialogue Nouveau projet, dans le **Types de projets** liste, développez **projets BizTalk**, puis cliquez sur **BTAHL7Projects**.</span><span class="sxs-lookup"><span data-stu-id="c3cbd-108">In the New Project dialog box, in the **Project Types** list, expand **BizTalk Projects**, and then click **BTAHL7Projects**.</span></span>  
  
3.  <span data-ttu-id="c3cbd-109">Dans le **modèles** , cliquez sur **projet BTAHL7 vide**.</span><span class="sxs-lookup"><span data-stu-id="c3cbd-109">In the **Templates** list, click **Empty BTAHL7 Project**.</span></span>  
  
4.  <span data-ttu-id="c3cbd-110">Dans le **nom** , tapez **BTAHL7V24Body projet**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="c3cbd-110">In the **Name** field, type **BTAHL7V24Body Project**, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="c3cbd-111">Dans l’Explorateur de solutions, sous le nœud pour votre nouveau **BTAHL7V24Body** de projet, cliquez sur **références**, puis cliquez sur **ajouter une référence**.</span><span class="sxs-lookup"><span data-stu-id="c3cbd-111">In Solution Explorer, under the node for your new **BTAHL7V24Body** project, right-click **References**, and then click **Add Reference**.</span></span>  
  
6.  <span data-ttu-id="c3cbd-112">Dans la boîte de dialogue Ajouter une référence, cliquez sur le **projets** onglet, sélectionnez **Interrogative_24Schemas**, cliquez sur **ajouter**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="c3cbd-112">In the Add Reference dialog box, click the **Projects** tab, select **Interrogative_24Schemas**, click **Add**, and then click **OK**.</span></span>  
  
## <a name="step-3a-add-the-schemas"></a><span data-ttu-id="c3cbd-113">Étape 3 a : ajoutez les schémas</span><span class="sxs-lookup"><span data-stu-id="c3cbd-113">Step 3A: Add the Schemas</span></span>  
 <span data-ttu-id="c3cbd-114">Utilisez la procédure suivante pour ajouter les nouveaux schémas au projet.</span><span class="sxs-lookup"><span data-stu-id="c3cbd-114">Use the following procedure to add the new schemas to the project.</span></span>  
  
#### <a name="to-add-the-schemas-to-the-project"></a><span data-ttu-id="c3cbd-115">Pour ajouter les schémas au projet</span><span class="sxs-lookup"><span data-stu-id="c3cbd-115">To add the schemas to the project</span></span>  
  
1.  <span data-ttu-id="c3cbd-116">Dans l’Explorateur de solutions, cliquez sur **BTAHL7V24Body projet**, pointez sur **ajouter**, puis cliquez sur **un nouvel élément**.</span><span class="sxs-lookup"><span data-stu-id="c3cbd-116">In Solution Explorer, right-click **BTAHL7V24Body Project**, point to **Add**, and then click **New Item**.</span></span>  
  
2.  <span data-ttu-id="c3cbd-117">Dans la boîte de dialogue Ajouter un nouvel élément, développez **des éléments de projet BizTalk**, puis double-cliquez sur **BTAHL7 schémas** dans le volet droit.</span><span class="sxs-lookup"><span data-stu-id="c3cbd-117">In the Add New Item dialog box, expand **BizTalk Project Items**, and then double-click **BTAHL7 Schemas** in the right pane.</span></span>  
  
3.  <span data-ttu-id="c3cbd-118">Dans la boîte de dialogue Sélecteur de schémas HL7, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="c3cbd-118">In the HL7 Schema Selector dialog box, do the following:</span></span>  
  
    |<span data-ttu-id="c3cbd-119">Utiliser</span><span class="sxs-lookup"><span data-stu-id="c3cbd-119">Use this</span></span>|<span data-ttu-id="c3cbd-120">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="c3cbd-120">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="c3cbd-121">**Classe de message**</span><span class="sxs-lookup"><span data-stu-id="c3cbd-121">**Message Class**</span></span>|<span data-ttu-id="c3cbd-122">Conserver **V2.X** sélectionné.</span><span class="sxs-lookup"><span data-stu-id="c3cbd-122">Keep **V2.X** selected.</span></span>|  
    |<span data-ttu-id="c3cbd-123">**Version**</span><span class="sxs-lookup"><span data-stu-id="c3cbd-123">**Version**</span></span>|<span data-ttu-id="c3cbd-124">Sélectionnez **2.4**.</span><span class="sxs-lookup"><span data-stu-id="c3cbd-124">Select **2.4**.</span></span>|  
    |<span data-ttu-id="c3cbd-125">**Type de message**</span><span class="sxs-lookup"><span data-stu-id="c3cbd-125">**Message Type**</span></span>|<span data-ttu-id="c3cbd-126">Sélectionnez **req**.</span><span class="sxs-lookup"><span data-stu-id="c3cbd-126">Select **QRY**.</span></span>|  
    |<span data-ttu-id="c3cbd-127">**Événement déclencheur**</span><span class="sxs-lookup"><span data-stu-id="c3cbd-127">**Trigger Event**</span></span>|<span data-ttu-id="c3cbd-128">Sélectionnez **Q01**.</span><span class="sxs-lookup"><span data-stu-id="c3cbd-128">Select **Q01**.</span></span>|  
  
4.  <span data-ttu-id="c3cbd-129">Cliquez sur **Terminer** pour ajouter le schéma au projet.</span><span class="sxs-lookup"><span data-stu-id="c3cbd-129">Click **Finish** to add the schema to the project.</span></span>  
  
     <span data-ttu-id="c3cbd-130">Cette opération crée le fichier de schéma de requête QRY_Q01_24_GLO_DEF.xsd.</span><span class="sxs-lookup"><span data-stu-id="c3cbd-130">This creates the query schema file QRY_Q01_24_GLO_DEF.xsd.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="c3cbd-131">Ne fermez pas la boîte de dialogue Sélecteur de schémas HL7.</span><span class="sxs-lookup"><span data-stu-id="c3cbd-131">Do not close the HL7 Schema Selector dialog box.</span></span>  
  
5.  <span data-ttu-id="c3cbd-132">Dans la boîte de dialogue Sélecteur de schémas HL7, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="c3cbd-132">In the HL7 Schema Selector dialog box, do the following:</span></span>  
  
    |<span data-ttu-id="c3cbd-133">Utiliser</span><span class="sxs-lookup"><span data-stu-id="c3cbd-133">Use this</span></span>|<span data-ttu-id="c3cbd-134">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="c3cbd-134">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="c3cbd-135">**Classe de message**</span><span class="sxs-lookup"><span data-stu-id="c3cbd-135">**Message Class**</span></span>|<span data-ttu-id="c3cbd-136">Conserver **V2.X** sélectionné.</span><span class="sxs-lookup"><span data-stu-id="c3cbd-136">Keep **V2.X** selected.</span></span>|  
    |<span data-ttu-id="c3cbd-137">**Version**</span><span class="sxs-lookup"><span data-stu-id="c3cbd-137">**Version**</span></span>|<span data-ttu-id="c3cbd-138">Sélectionnez **2.4**.</span><span class="sxs-lookup"><span data-stu-id="c3cbd-138">Select **2.4**.</span></span>|  
    |<span data-ttu-id="c3cbd-139">**Type de message**</span><span class="sxs-lookup"><span data-stu-id="c3cbd-139">**Message Type**</span></span>|<span data-ttu-id="c3cbd-140">Sélectionnez **DSR**.</span><span class="sxs-lookup"><span data-stu-id="c3cbd-140">Select **DSR**.</span></span>|  
    |<span data-ttu-id="c3cbd-141">**Événement déclencheur**</span><span class="sxs-lookup"><span data-stu-id="c3cbd-141">**Trigger Event**</span></span>|<span data-ttu-id="c3cbd-142">Sélectionnez **Q01**.</span><span class="sxs-lookup"><span data-stu-id="c3cbd-142">Select **Q01**.</span></span>|  
  
6.  <span data-ttu-id="c3cbd-143">Cliquez sur **Terminer** pour ajouter le schéma au projet.</span><span class="sxs-lookup"><span data-stu-id="c3cbd-143">Click **Finish** to add the schema to the project.</span></span>  
  
     <span data-ttu-id="c3cbd-144">Cette opération crée le fichier de schéma de réponse DSR_Q01_24_GLO_DEF.xsd.</span><span class="sxs-lookup"><span data-stu-id="c3cbd-144">This creates the response schema file DSR_Q01_24_GLO_DEF.xsd.</span></span>  
  
7.  <span data-ttu-id="c3cbd-145">Cliquez sur **Annuler** pour fermer la **sélecteur de schémas HL7** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="c3cbd-145">Click **Cancel** to close the **HL7 Schema Selector** dialog box.</span></span>  
  
## <a name="step-3b-assign-a-strong-key-to-the-assembly-and-deploy"></a><span data-ttu-id="c3cbd-146">Étape 3 b : assigner une clé forte à l’Assembly et le déployer</span><span class="sxs-lookup"><span data-stu-id="c3cbd-146">Step 3B: Assign a Strong Key to the Assembly and Deploy</span></span>  
 <span data-ttu-id="c3cbd-147">Utilisez la procédure suivante pour affecter une clé forte à l’assembly, puis déployer l’assembly.</span><span class="sxs-lookup"><span data-stu-id="c3cbd-147">Use the following procedure to assign a strong key to the assembly and then deploy the assembly.</span></span>  
  
#### <a name="to-assign-a-strong-key-and-deploy-the-assembly"></a><span data-ttu-id="c3cbd-148">Pour affecter une clé forte et de déployer l’assembly</span><span class="sxs-lookup"><span data-stu-id="c3cbd-148">To assign a strong key and deploy the assembly</span></span>  
  
1.  <span data-ttu-id="c3cbd-149">Dans l’Explorateur de solutions, cliquez sur **BTAHL7V24Body** de projet, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="c3cbd-149">In Solution Explorer, right-click **BTAHL7V24Body** project, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="c3cbd-150">Dans le **Pages de propriétés BTAHL7V24Body** boîte de dialogue, cliquez sur **Assembly**.</span><span class="sxs-lookup"><span data-stu-id="c3cbd-150">In the **BTAHL7V24Body Property Pages** dialog box, click **Assembly**.</span></span>  
  
3.  <span data-ttu-id="c3cbd-151">Dans le volet droit, faites défiler jusqu'à la **nom fort** , cliquez sur le champ situé à droite de **fichier de clé d’Assembly**, puis cliquez sur le bouton de sélection (...).</span><span class="sxs-lookup"><span data-stu-id="c3cbd-151">In the right pane, scroll down to the **Strong name** section, click the field to the right of **Assembly Key File**, and then click the ellipsis (…) button.</span></span>  
  
4.  <span data-ttu-id="c3cbd-152">Dans le **fichier de clé d’Assembly** boîte de dialogue, accédez à \< *lecteur*\>: \Program Files\\ [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk \<version\>Accelerator for HL7\SDK\Interrogative didacticiel, cliquez sur **key.snk**, puis cliquez sur **ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="c3cbd-152">In the **Assembly Key File** dialog box, browse to \<*drive*\>:\Program Files\\[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk \<version\> Accelerator for HL7\SDK\Interrogative Tutorial, click **key.snk**, and then click **Open**.</span></span>  
  
5.  <span data-ttu-id="c3cbd-153">Dans le **Pages de propriétés BTAHL7V24Body** boîte de dialogue, cliquez sur **OK** pour enregistrer vos modifications.</span><span class="sxs-lookup"><span data-stu-id="c3cbd-153">In the **BTAHL7V24Body Property Pages** dialog box, click **OK** to save your changes.</span></span>  
  
6.  <span data-ttu-id="c3cbd-154">Dans l’Explorateur de solutions avec le bouton droit **BTAHL7V24Body projet**, puis cliquez sur **déployer**.</span><span class="sxs-lookup"><span data-stu-id="c3cbd-154">In Solution Explorer right-click **BTAHL7V24Body Project**, and then click **Deploy**.</span></span> <span data-ttu-id="c3cbd-155">Assurez-vous de qu'un message de réussite s’affiche dans la fenêtre Sortie.</span><span class="sxs-lookup"><span data-stu-id="c3cbd-155">Ensure a success message appears in the output window.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="c3cbd-156">Si un message de réussite de déploiement n’apparaît pas, utilisez [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] pour résoudre les problèmes de vos schémas.</span><span class="sxs-lookup"><span data-stu-id="c3cbd-156">If a successful deploy message does not appear, use [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] to troubleshoot your schemas.</span></span>  
  
 <span data-ttu-id="c3cbd-157">Passez à [étape 4 : créer le Port de réception pour accepter les Messages de requête ADT](../../adapters-and-accelerators/accelerator-hl7/step-4-create-the-receive-port-for-accepting-adt-query-messages.md).</span><span class="sxs-lookup"><span data-stu-id="c3cbd-157">Proceed to [Step 4: Create the Receive Port for Accepting ADT Query Messages](../../adapters-and-accelerators/accelerator-hl7/step-4-create-the-receive-port-for-accepting-adt-query-messages.md).</span></span>