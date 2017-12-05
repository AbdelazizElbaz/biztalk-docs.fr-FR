---
title: "Étape 2 : Définir le processus d’entreprise | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b37bd9f1-5ee2-434d-950a-cf12967b6fc2
caps.latest.revision: "49"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5e29a9d3f1256fc24cf0a8f57b8ce0b7b1ba707d
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="step-2-define-the-business-process"></a><span data-ttu-id="7d982-102">Étape 2 : Définir le processus d'entreprise</span><span class="sxs-lookup"><span data-stu-id="7d982-102">Step 2: Define the Business Process</span></span>
<span data-ttu-id="7d982-103">![Étape 2 sur 4](../adapters-and-accelerators/adapter-oracle-ebs/media/step-2of4.gif "Step_2of4")</span><span class="sxs-lookup"><span data-stu-id="7d982-103">![Step 2 of 4](../adapters-and-accelerators/adapter-oracle-ebs/media/step-2of4.gif "Step_2of4")</span></span>  
  
 <span data-ttu-id="7d982-104">**Durée :** 8 minutes</span><span class="sxs-lookup"><span data-stu-id="7d982-104">**Time to complete:** 8 minutes</span></span>  
  
 <span data-ttu-id="7d982-105">**Objectif :** dans cette étape, vous utilisez le Concepteur d’Orchestration pour définir votre processus d’entreprise.</span><span class="sxs-lookup"><span data-stu-id="7d982-105">**Objective:** In this step, you use Orchestration Designer to define your business process.</span></span>  
  
 <span data-ttu-id="7d982-106">**Objectif :** le flux de travail de l’orchestration représente et automatise les processus d’entreprise de votre entreprise pour l’approbation des demandes de réapprovisionnement de stock.</span><span class="sxs-lookup"><span data-stu-id="7d982-106">**Purpose:** The workflow of the orchestration represents and automates your company's business process for approving inventory replenishment requests.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="7d982-107">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="7d982-107">Prerequisites</span></span>  
 <span data-ttu-id="7d982-108">Les conditions suivantes sont requises avant de commencer cette étape :</span><span class="sxs-lookup"><span data-stu-id="7d982-108">Note the following requirements before you begin this step:</span></span>  
  
-   <span data-ttu-id="7d982-109">Avant de commencer cette étape, vous devez effectuer [étape 1 : ajouter un projet EAIOrchestration à la Solution](../core/step-1-add-eaiorchestration-project-to-the-solution.md).</span><span class="sxs-lookup"><span data-stu-id="7d982-109">Before you begin this step you must complete [Step 1: Add EAIOrchestration Project to the Solution](../core/step-1-add-eaiorchestration-project-to-the-solution.md).</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="7d982-110">Procédures</span><span class="sxs-lookup"><span data-stu-id="7d982-110">Procedures</span></span>  
 <span data-ttu-id="7d982-111">La première étape de développement d'une orchestration consiste à utiliser des formes d'action pour représenter le processus d'entreprise.</span><span class="sxs-lookup"><span data-stu-id="7d982-111">The first step for developing an orchestration is to use action shapes to represent the business process.</span></span>  
  
#### <a name="to-create-the-eai-business-process-workflow"></a><span data-ttu-id="7d982-112">Pour créer le workflow du processus d'entreprise EAI</span><span class="sxs-lookup"><span data-stu-id="7d982-112">To create the EAI business process workflow</span></span>  
  
1.  <span data-ttu-id="7d982-113">À partir de Visual Studio, dans l’Explorateur de solutions, double-cliquez sur **EAIProcess.odx** pour ouvrir l’orchestration.</span><span class="sxs-lookup"><span data-stu-id="7d982-113">From Visual Studio, in Solution Explorer, double-click **EAIProcess.odx** to open the orchestration.</span></span>  
  
2.  <span data-ttu-id="7d982-114">Dans le Concepteur d’Orchestration, l’orchestration de boîte à outils, faites glisser le **réception** mettre en forme et déposez-la entre les **commencer** (cercle vert) et **fin** les formes (octogone rouge).</span><span class="sxs-lookup"><span data-stu-id="7d982-114">In Orchestration Designer, from the orchestration Toolbox, drag the **Receive** shape, and drop it between the **Begin** (green circle) and **End** (red octagon) shapes.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="7d982-115">Si la boîte à outils n’est pas ouvert, dans le **vue** menu, cliquez sur **boîte à outils**.</span><span class="sxs-lookup"><span data-stu-id="7d982-115">If the Toolbox is not open, in the **View** menu, click **Toolbox**.</span></span> <span data-ttu-id="7d982-116">Pour l'ancrer à l'écran, cliquez sur l'icône en forme de punaise.</span><span class="sxs-lookup"><span data-stu-id="7d982-116">To anchor it on the screen, click the thumbtack icon.</span></span>  
  
3.  <span data-ttu-id="7d982-117">Dans la boîte à outils, faites glisser le **décider** forme sous la forme réception.</span><span class="sxs-lookup"><span data-stu-id="7d982-117">From the toolbox, drag the **Decide** shape beneath the Receive shape.</span></span>  
  
4.  <span data-ttu-id="7d982-118">Dans la boîte à outils, faites glisser le **transformer** forme pour la branche de gauche de la forme décider.</span><span class="sxs-lookup"><span data-stu-id="7d982-118">From the toolbox, drag the **Transform** shape to the left branch of the Decide shape.</span></span> <span data-ttu-id="7d982-119">La forme Transformer est imbriquée dans la forme Construire un message.</span><span class="sxs-lookup"><span data-stu-id="7d982-119">The Transform shape is nested inside the Construct Message shape.</span></span>  
  
5.  <span data-ttu-id="7d982-120">Dans la boîte à outils, faites glisser le **envoyer** forme sous la forme Transformer.</span><span class="sxs-lookup"><span data-stu-id="7d982-120">From the toolbox, drag the **Send** shape beneath the Transform shape.</span></span>  
  
6.  <span data-ttu-id="7d982-121">Dans la boîte à outils, faites glisser le **envoyer** forme pour la branche de droite de la forme décider.</span><span class="sxs-lookup"><span data-stu-id="7d982-121">From the toolbox, drag the **Send** shape to the right branch of the Decide shape.</span></span>  <span data-ttu-id="7d982-122">L'orchestration se présente comme suit après avoir ajouté les formes d'action :</span><span class="sxs-lookup"><span data-stu-id="7d982-122">The orchestration looks like the following after you added the action shapes:</span></span>  
  
     <span data-ttu-id="7d982-123">![Processus EAI](../core/media/eaiprocess.gif "EAIProcess")</span><span class="sxs-lookup"><span data-stu-id="7d982-123">![EAI process](../core/media/eaiprocess.gif "EAIProcess")</span></span>  
  
 <span data-ttu-id="7d982-124">L'étape suivante consiste à définir des variables de message.</span><span class="sxs-lookup"><span data-stu-id="7d982-124">The next step is to define message variables.</span></span>  <span data-ttu-id="7d982-125">Plusieurs formes d'action présentent une propriété-message qui doit être spécifiée.</span><span class="sxs-lookup"><span data-stu-id="7d982-125">Several action shapes have a message property that needs to be specified.</span></span>  
  
#### <a name="to-define-message-variables"></a><span data-ttu-id="7d982-126">Pour définir des variables de message</span><span class="sxs-lookup"><span data-stu-id="7d982-126">To define message variables</span></span>  
  
1.  <span data-ttu-id="7d982-127">À partir de Visual Studio, cliquez sur le **vue** menu, cliquez sur **autres fenêtres**, puis cliquez sur **Vue Orchestration**.</span><span class="sxs-lookup"><span data-stu-id="7d982-127">From Visual Studio, click the **View** menu, click **Other Windows**, and then click **Orchestration View**.</span></span>  
  
2.  <span data-ttu-id="7d982-128">À partir de la vue Orchestration, cliquez sur **Messages**, puis cliquez sur **nouveau Message**.</span><span class="sxs-lookup"><span data-stu-id="7d982-128">From Orchestration View, right-click **Messages**, and then click **New Message**.</span></span>  
  
3.  <span data-ttu-id="7d982-129">Dans la fenêtre Propriétés, effectuez les paramétrages suivants :</span><span class="sxs-lookup"><span data-stu-id="7d982-129">In the Properties window, do the following:</span></span>  
  
    |<span data-ttu-id="7d982-130">Utiliser</span><span class="sxs-lookup"><span data-stu-id="7d982-130">Use this</span></span>|<span data-ttu-id="7d982-131">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="7d982-131">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="7d982-132">**Identificateur**</span><span class="sxs-lookup"><span data-stu-id="7d982-132">**Identifier**</span></span>|<span data-ttu-id="7d982-133">Type **RequestMessage**.</span><span class="sxs-lookup"><span data-stu-id="7d982-133">Type **RequestMessage**.</span></span>|  
    |<span data-ttu-id="7d982-134">**Type de message**</span><span class="sxs-lookup"><span data-stu-id="7d982-134">**Message Type**</span></span>|<span data-ttu-id="7d982-135">Cliquez sur **schémas**, puis cliquez sur  **\<sélectionner dans l’assembly référencé... \>**.</span><span class="sxs-lookup"><span data-stu-id="7d982-135">Click **Schemas**, and then click **\<Select from referenced assembly …\>**.</span></span> <span data-ttu-id="7d982-136">Dans la fenêtre Sélectionner le Type d’artefact, cliquez sur **EAISchemas**, puis cliquez sur **demande**.</span><span class="sxs-lookup"><span data-stu-id="7d982-136">From the Select Artifact Type window, click **EAISchemas**, and then click **Request**.</span></span> <span data-ttu-id="7d982-137">Cliquez sur **OK**</span><span class="sxs-lookup"><span data-stu-id="7d982-137">Click **OK**</span></span>|  
  
4.  <span data-ttu-id="7d982-138">À partir de la vue Orchestration, cliquez sur **Messages**, puis cliquez sur **nouveau Message**.</span><span class="sxs-lookup"><span data-stu-id="7d982-138">From Orchestration View, right-click **Messages**, and then click **New Message**.</span></span>  
  
5.  <span data-ttu-id="7d982-139">Dans la fenêtre Propriétés, effectuez les paramétrages suivants :</span><span class="sxs-lookup"><span data-stu-id="7d982-139">In the Properties window, do the following:</span></span>  
  
    |<span data-ttu-id="7d982-140">Utiliser</span><span class="sxs-lookup"><span data-stu-id="7d982-140">Use this</span></span>|<span data-ttu-id="7d982-141">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="7d982-141">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="7d982-142">**Identificateur**</span><span class="sxs-lookup"><span data-stu-id="7d982-142">**Identifier**</span></span>|<span data-ttu-id="7d982-143">Type **RequestDeclineMessage**.</span><span class="sxs-lookup"><span data-stu-id="7d982-143">Type **RequestDeclineMessage**.</span></span>|  
    |<span data-ttu-id="7d982-144">**Type de message**</span><span class="sxs-lookup"><span data-stu-id="7d982-144">**Message Type**</span></span>|<span data-ttu-id="7d982-145">Cliquez sur **schémas**, puis cliquez sur  **\<sélectionner dans l’assembly référencé... \>**.</span><span class="sxs-lookup"><span data-stu-id="7d982-145">Click **Schemas**, and then click **\<Select from referenced assembly …\>**.</span></span> <span data-ttu-id="7d982-146">Dans la fenêtre Sélectionner le Type d’artefact, cliquez sur **EAISchemas**, puis cliquez sur **RequestDecline**.</span><span class="sxs-lookup"><span data-stu-id="7d982-146">From the Select Artifact Type window, click **EAISchemas**, and then click **RequestDecline**.</span></span> <span data-ttu-id="7d982-147">Cliquez sur **OK**</span><span class="sxs-lookup"><span data-stu-id="7d982-147">Click **OK**</span></span>|  
  
#### <a name="to-configure-the-properties-of-the-shapes"></a><span data-ttu-id="7d982-148">Pour configurer les propriétés des formes</span><span class="sxs-lookup"><span data-stu-id="7d982-148">To configure the properties of the shapes</span></span>  
  
1.  <span data-ttu-id="7d982-149">Dans l’aire de conception, cliquez sur le **réception** forme pour la sélectionner.</span><span class="sxs-lookup"><span data-stu-id="7d982-149">On the design surface, click the **Receive** shape to select it.</span></span>  
  
2.  <span data-ttu-id="7d982-150">Dans la fenêtre Propriétés, effectuez les paramétrages suivants :</span><span class="sxs-lookup"><span data-stu-id="7d982-150">In the Properties window, do the following:</span></span>  
  
    |<span data-ttu-id="7d982-151">Utiliser</span><span class="sxs-lookup"><span data-stu-id="7d982-151">Use this</span></span>|<span data-ttu-id="7d982-152">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="7d982-152">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="7d982-153">**Nom**</span><span class="sxs-lookup"><span data-stu-id="7d982-153">**Name**</span></span>|<span data-ttu-id="7d982-154">Type **ReceiveRequest**.</span><span class="sxs-lookup"><span data-stu-id="7d982-154">Type **ReceiveRequest**.</span></span>|  
    |<span data-ttu-id="7d982-155">**Message**</span><span class="sxs-lookup"><span data-stu-id="7d982-155">**Message**</span></span>|<span data-ttu-id="7d982-156">Sélectionnez **RequestMessage**.</span><span class="sxs-lookup"><span data-stu-id="7d982-156">Select **RequestMessage**.</span></span>|  
    |<span data-ttu-id="7d982-157">**Activate**</span><span class="sxs-lookup"><span data-stu-id="7d982-157">**Activate**</span></span>|<span data-ttu-id="7d982-158">Dans la liste déroulante, sélectionnez **True**.</span><span class="sxs-lookup"><span data-stu-id="7d982-158">From the drop-down list, select **True**.</span></span>|  
  
    > [!NOTE]
    >  <span data-ttu-id="7d982-159">Si la fenêtre Propriétés n’est pas ouverte, dans le **vue** menu, cliquez sur **fenêtre Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="7d982-159">If the Property window is not open, in the **View** menu, click **Properties Window**.</span></span>  
  
3.  <span data-ttu-id="7d982-160">Dans l’aire de conception, cliquez sur le **décider** forme.</span><span class="sxs-lookup"><span data-stu-id="7d982-160">On the design surface, click the **Decide** shape.</span></span>  
  
4.  <span data-ttu-id="7d982-161">Dans la fenêtre Propriétés, effectuez les paramétrages suivants :</span><span class="sxs-lookup"><span data-stu-id="7d982-161">In the Properties window, do the following:</span></span>  
  
    |<span data-ttu-id="7d982-162">Utiliser</span><span class="sxs-lookup"><span data-stu-id="7d982-162">Use this</span></span>|<span data-ttu-id="7d982-163">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="7d982-163">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="7d982-164">**Nom**</span><span class="sxs-lookup"><span data-stu-id="7d982-164">**Name**</span></span>|<span data-ttu-id="7d982-165">Type **CheckGrandTotal**.</span><span class="sxs-lookup"><span data-stu-id="7d982-165">Type **CheckGrandTotal**.</span></span>|  
  
    > [!NOTE]
    >  <span data-ttu-id="7d982-166">Si la fenêtre Propriétés n’est pas ouverte, dans le **vue** menu, cliquez sur **fenêtre Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="7d982-166">If the Property window is not open, in the **View** menu, click **Properties Window**.</span></span>  
  
5.  <span data-ttu-id="7d982-167">Dans l’aire de conception, cliquez sur le **Rule_1** forme.</span><span class="sxs-lookup"><span data-stu-id="7d982-167">On the design surface, click the **Rule_1** shape.</span></span>  
  
6.  <span data-ttu-id="7d982-168">Dans la fenêtre Propriétés, effectuez les paramétrages suivants :</span><span class="sxs-lookup"><span data-stu-id="7d982-168">In the Properties window, do the following:</span></span>  
  
    |<span data-ttu-id="7d982-169">Utiliser</span><span class="sxs-lookup"><span data-stu-id="7d982-169">Use this</span></span>|<span data-ttu-id="7d982-170">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="7d982-170">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="7d982-171">**Nom**</span><span class="sxs-lookup"><span data-stu-id="7d982-171">**Name**</span></span>|<span data-ttu-id="7d982-172">Type **DeclineRule**.</span><span class="sxs-lookup"><span data-stu-id="7d982-172">Type **DeclineRule**.</span></span>|  
    |<span data-ttu-id="7d982-173">**Expression**</span><span class="sxs-lookup"><span data-stu-id="7d982-173">**Expression**</span></span>|<span data-ttu-id="7d982-174">Cliquez sur le bouton de sélection (**...** ), puis tapez `RequestMessage(EAISchemas.PropertySchema.GrandTotal ) > 10000`.</span><span class="sxs-lookup"><span data-stu-id="7d982-174">Click the ellipses (**…**), and then type `RequestMessage(EAISchemas.PropertySchema.GrandTotal ) > 10000`.</span></span> <span data-ttu-id="7d982-175">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="7d982-175">Click **OK**.</span></span>|  
  
7.  <span data-ttu-id="7d982-176">Dans l’aire de conception, cliquez sur le **ConstructMessage_1** forme.</span><span class="sxs-lookup"><span data-stu-id="7d982-176">On the design surface, click the **ConstructMessage_1** shape.</span></span>  
  
8.  <span data-ttu-id="7d982-177">Dans la fenêtre Propriétés, effectuez les paramétrages suivants :</span><span class="sxs-lookup"><span data-stu-id="7d982-177">In the Properties window, do the following:</span></span>  
  
    |<span data-ttu-id="7d982-178">Utiliser</span><span class="sxs-lookup"><span data-stu-id="7d982-178">Use this</span></span>|<span data-ttu-id="7d982-179">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="7d982-179">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="7d982-180">**Nom**</span><span class="sxs-lookup"><span data-stu-id="7d982-180">**Name**</span></span>|<span data-ttu-id="7d982-181">Type **ConstructRequestDeclineMessage**.</span><span class="sxs-lookup"><span data-stu-id="7d982-181">Type **ConstructRequestDeclineMessage**.</span></span>|  
    |<span data-ttu-id="7d982-182">**Messages construits**</span><span class="sxs-lookup"><span data-stu-id="7d982-182">**Messages Constructed**</span></span>|<span data-ttu-id="7d982-183">Sélectionnez **RequestDeclineMessage**.</span><span class="sxs-lookup"><span data-stu-id="7d982-183">Select **RequestDeclineMessage**.</span></span>|  
  
9. <span data-ttu-id="7d982-184">Dans l’aire de conception, cliquez sur le **Transform_1** forme.</span><span class="sxs-lookup"><span data-stu-id="7d982-184">On the design surface, click the **Transform_1** shape.</span></span>  
  
10. <span data-ttu-id="7d982-185">Dans la fenêtre Propriétés, effectuez les paramétrages suivants :</span><span class="sxs-lookup"><span data-stu-id="7d982-185">In the Properties window, do the following:</span></span>  
  
    |<span data-ttu-id="7d982-186">Utiliser</span><span class="sxs-lookup"><span data-stu-id="7d982-186">Use this</span></span>|<span data-ttu-id="7d982-187">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="7d982-187">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="7d982-188">**Nom**</span><span class="sxs-lookup"><span data-stu-id="7d982-188">**Name**</span></span>|<span data-ttu-id="7d982-189">Type **TransformRequestToRequestDeclineMessage**.</span><span class="sxs-lookup"><span data-stu-id="7d982-189">Type **TransformRequestToRequestDeclineMessage**.</span></span>|  
    |<span data-ttu-id="7d982-190">**Nom de mappage**</span><span class="sxs-lookup"><span data-stu-id="7d982-190">**Map Name**</span></span>|<span data-ttu-id="7d982-191">Cliquez sur **...** .</span><span class="sxs-lookup"><span data-stu-id="7d982-191">Click **…**.</span></span> <span data-ttu-id="7d982-192">Dans Configuration de la forme Transformer, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="7d982-192">From Transform Configuration, do the following:</span></span><br /><br /> <span data-ttu-id="7d982-193">Entrez les informations de configuration :</span><span class="sxs-lookup"><span data-stu-id="7d982-193">Enter the configuration information:</span></span><br /><br /> <span data-ttu-id="7d982-194">-Cliquez sur **mappage existant**.</span><span class="sxs-lookup"><span data-stu-id="7d982-194">- Click **Existing Map**.</span></span><br /><br /> <span data-ttu-id="7d982-195">Nom de mappage complet :</span><span class="sxs-lookup"><span data-stu-id="7d982-195">Fully Qualified Map Name:</span></span><br /><br /> <span data-ttu-id="7d982-196">-Sélectionnez  **\<sélectionner dans l’assembly référencé\>**.</span><span class="sxs-lookup"><span data-stu-id="7d982-196">- Select **\<Select from referenced assembly\>**.</span></span>  <span data-ttu-id="7d982-197">Dans le volet gauche, sélectionnez **EAISchemas**.</span><span class="sxs-lookup"><span data-stu-id="7d982-197">From the left pane, select **EAISchemas**.</span></span>  <span data-ttu-id="7d982-198">Dans le volet de droite, sélectionnez EAISchemas.MapToReqDecline.</span><span class="sxs-lookup"><span data-stu-id="7d982-198">From the right pane, select EAISchemas.MapToReqDecline.</span></span>  <span data-ttu-id="7d982-199">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="7d982-199">Click **OK**.</span></span><br /><br /> <span data-ttu-id="7d982-200">Source</span><span class="sxs-lookup"><span data-stu-id="7d982-200">Source</span></span><br /><br /> <span data-ttu-id="7d982-201">-RequestMessage</span><span class="sxs-lookup"><span data-stu-id="7d982-201">- RequestMessage</span></span><br /><br /> <span data-ttu-id="7d982-202">Destination</span><span class="sxs-lookup"><span data-stu-id="7d982-202">Destination</span></span><br /><br /> <span data-ttu-id="7d982-203">-RequestDeclineMessage</span><span class="sxs-lookup"><span data-stu-id="7d982-203">- RequestDeclineMessage</span></span>|  
  
11. <span data-ttu-id="7d982-204">Dans l’aire de conception, cliquez sur le **Send_1** forme.</span><span class="sxs-lookup"><span data-stu-id="7d982-204">On the design surface, click the **Send_1** shape.</span></span>  
  
12. <span data-ttu-id="7d982-205">Dans la fenêtre Propriétés, effectuez les paramétrages suivants :</span><span class="sxs-lookup"><span data-stu-id="7d982-205">In the Properties window, do the following:</span></span>  
  
    |<span data-ttu-id="7d982-206">Utiliser</span><span class="sxs-lookup"><span data-stu-id="7d982-206">Use this</span></span>|<span data-ttu-id="7d982-207">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="7d982-207">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="7d982-208">**Nom**</span><span class="sxs-lookup"><span data-stu-id="7d982-208">**Name**</span></span>|<span data-ttu-id="7d982-209">Type **SendRequestDecline**.</span><span class="sxs-lookup"><span data-stu-id="7d982-209">Type **SendRequestDecline**.</span></span>|  
    |<span data-ttu-id="7d982-210">**Message**</span><span class="sxs-lookup"><span data-stu-id="7d982-210">**Message**</span></span>|<span data-ttu-id="7d982-211">Sélectionnez **RequestDeclineMessage**.</span><span class="sxs-lookup"><span data-stu-id="7d982-211">Select **RequestDeclineMessage**.</span></span>|  
  
13. <span data-ttu-id="7d982-212">Dans l’aire de conception, cliquez sur le **Send_2** forme.</span><span class="sxs-lookup"><span data-stu-id="7d982-212">On the design surface, click the **Send_2** shape.</span></span>  
  
14. <span data-ttu-id="7d982-213">Dans la fenêtre Propriétés, effectuez les paramétrages suivants :</span><span class="sxs-lookup"><span data-stu-id="7d982-213">In the Properties window, do the following:</span></span>  
  
    |<span data-ttu-id="7d982-214">Utiliser</span><span class="sxs-lookup"><span data-stu-id="7d982-214">Use this</span></span>|<span data-ttu-id="7d982-215">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="7d982-215">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="7d982-216">**Nom**</span><span class="sxs-lookup"><span data-stu-id="7d982-216">**Name**</span></span>|<span data-ttu-id="7d982-217">Type **SendRequestToERP**.</span><span class="sxs-lookup"><span data-stu-id="7d982-217">Type **SendRequestToERP**.</span></span>|  
    |<span data-ttu-id="7d982-218">**Message**</span><span class="sxs-lookup"><span data-stu-id="7d982-218">**Message**</span></span>|<span data-ttu-id="7d982-219">Sélectionnez **RequestMessage**.</span><span class="sxs-lookup"><span data-stu-id="7d982-219">Select **RequestMessage**.</span></span>|  
  
## <a name="what-did-i-just-do"></a><span data-ttu-id="7d982-220">Actions effectuées</span><span class="sxs-lookup"><span data-stu-id="7d982-220">What did I just do?</span></span>  
 <span data-ttu-id="7d982-221">Au cours de cette étape, vous avez utilisé le Concepteur d'orchestration pour définir votre processus d'entreprise.</span><span class="sxs-lookup"><span data-stu-id="7d982-221">In this step, you used Orchestration Designer to define your business process.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="7d982-222">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="7d982-222">Next Steps</span></span>  
 <span data-ttu-id="7d982-223">Ajouter des ports logiques à l’orchestration dans [étape 3 : ajouter des Ports à l’Orchestration](../core/step-3-add-ports-to-the-orchestration.md).</span><span class="sxs-lookup"><span data-stu-id="7d982-223">You add logical ports to the orchestration in [Step 3: Add Ports to the Orchestration](../core/step-3-add-ports-to-the-orchestration.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d982-224">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7d982-224">See Also</span></span>  
 <span data-ttu-id="7d982-225">[Étape 1 : Ajouter un projet EAIOrchestration à la Solution](../core/step-1-add-eaiorchestration-project-to-the-solution.md) </span><span class="sxs-lookup"><span data-stu-id="7d982-225">[Step 1: Add EAIOrchestration Project to the Solution](../core/step-1-add-eaiorchestration-project-to-the-solution.md) </span></span>  
 <span data-ttu-id="7d982-226">[Étape 3 : Ajouter des Ports à l’Orchestration](../core/step-3-add-ports-to-the-orchestration.md) </span><span class="sxs-lookup"><span data-stu-id="7d982-226">[Step 3: Add Ports to the Orchestration](../core/step-3-add-ports-to-the-orchestration.md) </span></span>  
 [<span data-ttu-id="7d982-227">Étape 4 : Créer le projet EAIOrchestration</span><span class="sxs-lookup"><span data-stu-id="7d982-227">Step 4: Build the EAIOrchestration Project</span></span>](../core/step-4-build-the-eaiorchestration-project.md)