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
ms.openlocfilehash: 17f181933daac5170c517a23f809eb97b54f2900
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-2-define-the-business-process"></a><span data-ttu-id="5782a-102">Étape 2 : Définir le processus d'entreprise</span><span class="sxs-lookup"><span data-stu-id="5782a-102">Step 2: Define the Business Process</span></span>
<span data-ttu-id="5782a-103">![Étape 2 sur 4](../adapters-and-accelerators/adapter-oracle-ebs/media/step-2of4.gif "Step_2of4")</span><span class="sxs-lookup"><span data-stu-id="5782a-103">![Step 2 of 4](../adapters-and-accelerators/adapter-oracle-ebs/media/step-2of4.gif "Step_2of4")</span></span>  
  
 <span data-ttu-id="5782a-104">**Durée :** 8 minutes</span><span class="sxs-lookup"><span data-stu-id="5782a-104">**Time to complete:** 8 minutes</span></span>  
  
 <span data-ttu-id="5782a-105">**Objectif :** dans cette étape, vous utilisez le Concepteur d’Orchestration pour définir votre processus d’entreprise.</span><span class="sxs-lookup"><span data-stu-id="5782a-105">**Objective:** In this step, you use Orchestration Designer to define your business process.</span></span>  
  
 <span data-ttu-id="5782a-106">**Objectif :** le flux de travail de l’orchestration représente et automatise les processus d’entreprise de votre entreprise pour l’approbation des demandes de réapprovisionnement de stock.</span><span class="sxs-lookup"><span data-stu-id="5782a-106">**Purpose:** The workflow of the orchestration represents and automates your company's business process for approving inventory replenishment requests.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="5782a-107">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="5782a-107">Prerequisites</span></span>  
 <span data-ttu-id="5782a-108">Les conditions suivantes sont requises avant de commencer cette étape :</span><span class="sxs-lookup"><span data-stu-id="5782a-108">Note the following requirements before you begin this step:</span></span>  
  
-   <span data-ttu-id="5782a-109">Avant de commencer cette étape, vous devez effectuer [étape 1 : ajouter un projet EAIOrchestration à la Solution](../core/step-1-add-eaiorchestration-project-to-the-solution.md).</span><span class="sxs-lookup"><span data-stu-id="5782a-109">Before you begin this step you must complete [Step 1: Add EAIOrchestration Project to the Solution](../core/step-1-add-eaiorchestration-project-to-the-solution.md).</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="5782a-110">Procédures</span><span class="sxs-lookup"><span data-stu-id="5782a-110">Procedures</span></span>  
 <span data-ttu-id="5782a-111">La première étape de développement d'une orchestration consiste à utiliser des formes d'action pour représenter le processus d'entreprise.</span><span class="sxs-lookup"><span data-stu-id="5782a-111">The first step for developing an orchestration is to use action shapes to represent the business process.</span></span>  
  
#### <a name="to-create-the-eai-business-process-workflow"></a><span data-ttu-id="5782a-112">Pour créer le workflow du processus d'entreprise EAI</span><span class="sxs-lookup"><span data-stu-id="5782a-112">To create the EAI business process workflow</span></span>  
  
1.  <span data-ttu-id="5782a-113">À partir de Visual Studio, dans l’Explorateur de solutions, double-cliquez sur **EAIProcess.odx** pour ouvrir l’orchestration.</span><span class="sxs-lookup"><span data-stu-id="5782a-113">From Visual Studio, in Solution Explorer, double-click **EAIProcess.odx** to open the orchestration.</span></span>  
  
2.  <span data-ttu-id="5782a-114">Dans le Concepteur d’Orchestration, l’orchestration de boîte à outils, faites glisser le **réception** mettre en forme et déposez-la entre les **commencer** (cercle vert) et **fin** les formes (octogone rouge).</span><span class="sxs-lookup"><span data-stu-id="5782a-114">In Orchestration Designer, from the orchestration Toolbox, drag the **Receive** shape, and drop it between the **Begin** (green circle) and **End** (red octagon) shapes.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="5782a-115">Si la boîte à outils n’est pas ouvert, dans le **vue** menu, cliquez sur **boîte à outils**.</span><span class="sxs-lookup"><span data-stu-id="5782a-115">If the Toolbox is not open, in the **View** menu, click **Toolbox**.</span></span> <span data-ttu-id="5782a-116">Pour l'ancrer à l'écran, cliquez sur l'icône en forme de punaise.</span><span class="sxs-lookup"><span data-stu-id="5782a-116">To anchor it on the screen, click the thumbtack icon.</span></span>  
  
3.  <span data-ttu-id="5782a-117">Dans la boîte à outils, faites glisser le **décider** forme sous la forme réception.</span><span class="sxs-lookup"><span data-stu-id="5782a-117">From the toolbox, drag the **Decide** shape beneath the Receive shape.</span></span>  
  
4.  <span data-ttu-id="5782a-118">Dans la boîte à outils, faites glisser le **transformer** forme pour la branche de gauche de la forme décider.</span><span class="sxs-lookup"><span data-stu-id="5782a-118">From the toolbox, drag the **Transform** shape to the left branch of the Decide shape.</span></span> <span data-ttu-id="5782a-119">La forme Transformer est imbriquée dans la forme Construire un message.</span><span class="sxs-lookup"><span data-stu-id="5782a-119">The Transform shape is nested inside the Construct Message shape.</span></span>  
  
5.  <span data-ttu-id="5782a-120">Dans la boîte à outils, faites glisser le **envoyer** forme sous la forme Transformer.</span><span class="sxs-lookup"><span data-stu-id="5782a-120">From the toolbox, drag the **Send** shape beneath the Transform shape.</span></span>  
  
6.  <span data-ttu-id="5782a-121">Dans la boîte à outils, faites glisser le **envoyer** forme pour la branche de droite de la forme décider.</span><span class="sxs-lookup"><span data-stu-id="5782a-121">From the toolbox, drag the **Send** shape to the right branch of the Decide shape.</span></span>  <span data-ttu-id="5782a-122">L'orchestration se présente comme suit après avoir ajouté les formes d'action :</span><span class="sxs-lookup"><span data-stu-id="5782a-122">The orchestration looks like the following after you added the action shapes:</span></span>  
  
     <span data-ttu-id="5782a-123">![Processus EAI](../core/media/eaiprocess.gif "EAIProcess")</span><span class="sxs-lookup"><span data-stu-id="5782a-123">![EAI process](../core/media/eaiprocess.gif "EAIProcess")</span></span>  
  
 <span data-ttu-id="5782a-124">L'étape suivante consiste à définir des variables de message.</span><span class="sxs-lookup"><span data-stu-id="5782a-124">The next step is to define message variables.</span></span>  <span data-ttu-id="5782a-125">Plusieurs formes d'action présentent une propriété-message qui doit être spécifiée.</span><span class="sxs-lookup"><span data-stu-id="5782a-125">Several action shapes have a message property that needs to be specified.</span></span>  
  
#### <a name="to-define-message-variables"></a><span data-ttu-id="5782a-126">Pour définir des variables de message</span><span class="sxs-lookup"><span data-stu-id="5782a-126">To define message variables</span></span>  
  
1.  <span data-ttu-id="5782a-127">À partir de Visual Studio, cliquez sur le **vue** menu, cliquez sur **autres fenêtres**, puis cliquez sur **Vue Orchestration**.</span><span class="sxs-lookup"><span data-stu-id="5782a-127">From Visual Studio, click the **View** menu, click **Other Windows**, and then click **Orchestration View**.</span></span>  
  
2.  <span data-ttu-id="5782a-128">À partir de la vue Orchestration, cliquez sur **Messages**, puis cliquez sur **nouveau Message**.</span><span class="sxs-lookup"><span data-stu-id="5782a-128">From Orchestration View, right-click **Messages**, and then click **New Message**.</span></span>  
  
3.  <span data-ttu-id="5782a-129">Dans la fenêtre Propriétés, effectuez les paramétrages suivants :</span><span class="sxs-lookup"><span data-stu-id="5782a-129">In the Properties window, do the following:</span></span>  
  
    |<span data-ttu-id="5782a-130">Utiliser</span><span class="sxs-lookup"><span data-stu-id="5782a-130">Use this</span></span>|<span data-ttu-id="5782a-131">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="5782a-131">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="5782a-132">**Identificateur**</span><span class="sxs-lookup"><span data-stu-id="5782a-132">**Identifier**</span></span>|<span data-ttu-id="5782a-133">Type **RequestMessage**.</span><span class="sxs-lookup"><span data-stu-id="5782a-133">Type **RequestMessage**.</span></span>|  
    |<span data-ttu-id="5782a-134">**Type de message**</span><span class="sxs-lookup"><span data-stu-id="5782a-134">**Message Type**</span></span>|<span data-ttu-id="5782a-135">Cliquez sur **schémas**, puis cliquez sur  **\<sélectionner à partir de l’assembly référencé... >**.</span><span class="sxs-lookup"><span data-stu-id="5782a-135">Click **Schemas**, and then click **\<Select from referenced assembly …>**.</span></span> <span data-ttu-id="5782a-136">Dans la fenêtre Sélectionner le Type d’artefact, cliquez sur **EAISchemas**, puis cliquez sur **demande**.</span><span class="sxs-lookup"><span data-stu-id="5782a-136">From the Select Artifact Type window, click **EAISchemas**, and then click **Request**.</span></span> <span data-ttu-id="5782a-137">Cliquez sur **OK**</span><span class="sxs-lookup"><span data-stu-id="5782a-137">Click **OK**</span></span>|  
  
4.  <span data-ttu-id="5782a-138">À partir de la vue Orchestration, cliquez sur **Messages**, puis cliquez sur **nouveau Message**.</span><span class="sxs-lookup"><span data-stu-id="5782a-138">From Orchestration View, right-click **Messages**, and then click **New Message**.</span></span>  
  
5.  <span data-ttu-id="5782a-139">Dans la fenêtre Propriétés, effectuez les paramétrages suivants :</span><span class="sxs-lookup"><span data-stu-id="5782a-139">In the Properties window, do the following:</span></span>  
  
    |<span data-ttu-id="5782a-140">Utiliser</span><span class="sxs-lookup"><span data-stu-id="5782a-140">Use this</span></span>|<span data-ttu-id="5782a-141">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="5782a-141">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="5782a-142">**Identificateur**</span><span class="sxs-lookup"><span data-stu-id="5782a-142">**Identifier**</span></span>|<span data-ttu-id="5782a-143">Type **RequestDeclineMessage**.</span><span class="sxs-lookup"><span data-stu-id="5782a-143">Type **RequestDeclineMessage**.</span></span>|  
    |<span data-ttu-id="5782a-144">**Type de message**</span><span class="sxs-lookup"><span data-stu-id="5782a-144">**Message Type**</span></span>|<span data-ttu-id="5782a-145">Cliquez sur **schémas**, puis cliquez sur  **\<sélectionner à partir de l’assembly référencé... >**.</span><span class="sxs-lookup"><span data-stu-id="5782a-145">Click **Schemas**, and then click **\<Select from referenced assembly …>**.</span></span> <span data-ttu-id="5782a-146">Dans la fenêtre Sélectionner le Type d’artefact, cliquez sur **EAISchemas**, puis cliquez sur **RequestDecline**.</span><span class="sxs-lookup"><span data-stu-id="5782a-146">From the Select Artifact Type window, click **EAISchemas**, and then click **RequestDecline**.</span></span> <span data-ttu-id="5782a-147">Cliquez sur **OK**</span><span class="sxs-lookup"><span data-stu-id="5782a-147">Click **OK**</span></span>|  
  
#### <a name="to-configure-the-properties-of-the-shapes"></a><span data-ttu-id="5782a-148">Pour configurer les propriétés des formes</span><span class="sxs-lookup"><span data-stu-id="5782a-148">To configure the properties of the shapes</span></span>  
  
1.  <span data-ttu-id="5782a-149">Dans l’aire de conception, cliquez sur le **réception** forme pour la sélectionner.</span><span class="sxs-lookup"><span data-stu-id="5782a-149">On the design surface, click the **Receive** shape to select it.</span></span>  
  
2.  <span data-ttu-id="5782a-150">Dans la fenêtre Propriétés, effectuez les paramétrages suivants :</span><span class="sxs-lookup"><span data-stu-id="5782a-150">In the Properties window, do the following:</span></span>  
  
    |<span data-ttu-id="5782a-151">Utiliser</span><span class="sxs-lookup"><span data-stu-id="5782a-151">Use this</span></span>|<span data-ttu-id="5782a-152">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="5782a-152">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="5782a-153">**Nom**</span><span class="sxs-lookup"><span data-stu-id="5782a-153">**Name**</span></span>|<span data-ttu-id="5782a-154">Type **ReceiveRequest**.</span><span class="sxs-lookup"><span data-stu-id="5782a-154">Type **ReceiveRequest**.</span></span>|  
    |<span data-ttu-id="5782a-155">**Message**</span><span class="sxs-lookup"><span data-stu-id="5782a-155">**Message**</span></span>|<span data-ttu-id="5782a-156">Sélectionnez **RequestMessage**.</span><span class="sxs-lookup"><span data-stu-id="5782a-156">Select **RequestMessage**.</span></span>|  
    |<span data-ttu-id="5782a-157">**Activate**</span><span class="sxs-lookup"><span data-stu-id="5782a-157">**Activate**</span></span>|<span data-ttu-id="5782a-158">Dans la liste déroulante, sélectionnez **True**.</span><span class="sxs-lookup"><span data-stu-id="5782a-158">From the drop-down list, select **True**.</span></span>|  
  
    > [!NOTE]
    >  <span data-ttu-id="5782a-159">Si la fenêtre Propriétés n’est pas ouverte, dans le **vue** menu, cliquez sur **fenêtre Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="5782a-159">If the Property window is not open, in the **View** menu, click **Properties Window**.</span></span>  
  
3.  <span data-ttu-id="5782a-160">Dans l’aire de conception, cliquez sur le **décider** forme.</span><span class="sxs-lookup"><span data-stu-id="5782a-160">On the design surface, click the **Decide** shape.</span></span>  
  
4.  <span data-ttu-id="5782a-161">Dans la fenêtre Propriétés, effectuez les paramétrages suivants :</span><span class="sxs-lookup"><span data-stu-id="5782a-161">In the Properties window, do the following:</span></span>  
  
    |<span data-ttu-id="5782a-162">Utiliser</span><span class="sxs-lookup"><span data-stu-id="5782a-162">Use this</span></span>|<span data-ttu-id="5782a-163">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="5782a-163">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="5782a-164">**Nom**</span><span class="sxs-lookup"><span data-stu-id="5782a-164">**Name**</span></span>|<span data-ttu-id="5782a-165">Type **CheckGrandTotal**.</span><span class="sxs-lookup"><span data-stu-id="5782a-165">Type **CheckGrandTotal**.</span></span>|  
  
    > [!NOTE]
    >  <span data-ttu-id="5782a-166">Si la fenêtre Propriétés n’est pas ouverte, dans le **vue** menu, cliquez sur **fenêtre Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="5782a-166">If the Property window is not open, in the **View** menu, click **Properties Window**.</span></span>  
  
5.  <span data-ttu-id="5782a-167">Dans l’aire de conception, cliquez sur le **Rule_1** forme.</span><span class="sxs-lookup"><span data-stu-id="5782a-167">On the design surface, click the **Rule_1** shape.</span></span>  
  
6.  <span data-ttu-id="5782a-168">Dans la fenêtre Propriétés, effectuez les paramétrages suivants :</span><span class="sxs-lookup"><span data-stu-id="5782a-168">In the Properties window, do the following:</span></span>  
  
    |<span data-ttu-id="5782a-169">Utiliser</span><span class="sxs-lookup"><span data-stu-id="5782a-169">Use this</span></span>|<span data-ttu-id="5782a-170">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="5782a-170">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="5782a-171">**Nom**</span><span class="sxs-lookup"><span data-stu-id="5782a-171">**Name**</span></span>|<span data-ttu-id="5782a-172">Type **DeclineRule**.</span><span class="sxs-lookup"><span data-stu-id="5782a-172">Type **DeclineRule**.</span></span>|  
    |<span data-ttu-id="5782a-173">**Expression**</span><span class="sxs-lookup"><span data-stu-id="5782a-173">**Expression**</span></span>|<span data-ttu-id="5782a-174">Cliquez sur le bouton de sélection (**...** ), puis tapez `RequestMessage(EAISchemas.PropertySchema.GrandTotal ) > 10000`.</span><span class="sxs-lookup"><span data-stu-id="5782a-174">Click the ellipses (**…**), and then type `RequestMessage(EAISchemas.PropertySchema.GrandTotal ) > 10000`.</span></span> <span data-ttu-id="5782a-175">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="5782a-175">Click **OK**.</span></span>|  
  
7.  <span data-ttu-id="5782a-176">Dans l’aire de conception, cliquez sur le **ConstructMessage_1** forme.</span><span class="sxs-lookup"><span data-stu-id="5782a-176">On the design surface, click the **ConstructMessage_1** shape.</span></span>  
  
8.  <span data-ttu-id="5782a-177">Dans la fenêtre Propriétés, effectuez les paramétrages suivants :</span><span class="sxs-lookup"><span data-stu-id="5782a-177">In the Properties window, do the following:</span></span>  
  
    |<span data-ttu-id="5782a-178">Utiliser</span><span class="sxs-lookup"><span data-stu-id="5782a-178">Use this</span></span>|<span data-ttu-id="5782a-179">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="5782a-179">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="5782a-180">**Nom**</span><span class="sxs-lookup"><span data-stu-id="5782a-180">**Name**</span></span>|<span data-ttu-id="5782a-181">Type **ConstructRequestDeclineMessage**.</span><span class="sxs-lookup"><span data-stu-id="5782a-181">Type **ConstructRequestDeclineMessage**.</span></span>|  
    |<span data-ttu-id="5782a-182">**Messages construits**</span><span class="sxs-lookup"><span data-stu-id="5782a-182">**Messages Constructed**</span></span>|<span data-ttu-id="5782a-183">Sélectionnez **RequestDeclineMessage**.</span><span class="sxs-lookup"><span data-stu-id="5782a-183">Select **RequestDeclineMessage**.</span></span>|  
  
9. <span data-ttu-id="5782a-184">Dans l’aire de conception, cliquez sur le **Transform_1** forme.</span><span class="sxs-lookup"><span data-stu-id="5782a-184">On the design surface, click the **Transform_1** shape.</span></span>  
  
10. <span data-ttu-id="5782a-185">Dans la fenêtre Propriétés, effectuez les paramétrages suivants :</span><span class="sxs-lookup"><span data-stu-id="5782a-185">In the Properties window, do the following:</span></span>  
  
    |<span data-ttu-id="5782a-186">Utiliser</span><span class="sxs-lookup"><span data-stu-id="5782a-186">Use this</span></span>|<span data-ttu-id="5782a-187">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="5782a-187">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="5782a-188">**Nom**</span><span class="sxs-lookup"><span data-stu-id="5782a-188">**Name**</span></span>|<span data-ttu-id="5782a-189">Type **TransformRequestToRequestDeclineMessage**.</span><span class="sxs-lookup"><span data-stu-id="5782a-189">Type **TransformRequestToRequestDeclineMessage**.</span></span>|  
    |<span data-ttu-id="5782a-190">**Nom de mappage**</span><span class="sxs-lookup"><span data-stu-id="5782a-190">**Map Name**</span></span>|<span data-ttu-id="5782a-191">Cliquez sur **...** .</span><span class="sxs-lookup"><span data-stu-id="5782a-191">Click **…**.</span></span> <span data-ttu-id="5782a-192">Dans Configuration de la forme Transformer, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="5782a-192">From Transform Configuration, do the following:</span></span><br /><br /> <span data-ttu-id="5782a-193">Entrez les informations de configuration :</span><span class="sxs-lookup"><span data-stu-id="5782a-193">Enter the configuration information:</span></span><br /><br /> <span data-ttu-id="5782a-194">-Cliquez sur **mappage existant**.</span><span class="sxs-lookup"><span data-stu-id="5782a-194">- Click **Existing Map**.</span></span><br /><br /> <span data-ttu-id="5782a-195">Nom de mappage complet :</span><span class="sxs-lookup"><span data-stu-id="5782a-195">Fully Qualified Map Name:</span></span><br /><br /> <span data-ttu-id="5782a-196">-Sélectionnez  **\<sélectionner dans l’assembly référencé >**.</span><span class="sxs-lookup"><span data-stu-id="5782a-196">- Select **\<Select from referenced assembly>**.</span></span>  <span data-ttu-id="5782a-197">Dans le volet gauche, sélectionnez **EAISchemas**.</span><span class="sxs-lookup"><span data-stu-id="5782a-197">From the left pane, select **EAISchemas**.</span></span>  <span data-ttu-id="5782a-198">Dans le volet de droite, sélectionnez EAISchemas.MapToReqDecline.</span><span class="sxs-lookup"><span data-stu-id="5782a-198">From the right pane, select EAISchemas.MapToReqDecline.</span></span>  <span data-ttu-id="5782a-199">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="5782a-199">Click **OK**.</span></span><br /><br /> <span data-ttu-id="5782a-200">Source</span><span class="sxs-lookup"><span data-stu-id="5782a-200">Source</span></span><br /><br /> <span data-ttu-id="5782a-201">-RequestMessage</span><span class="sxs-lookup"><span data-stu-id="5782a-201">- RequestMessage</span></span><br /><br /> <span data-ttu-id="5782a-202">Destination</span><span class="sxs-lookup"><span data-stu-id="5782a-202">Destination</span></span><br /><br /> <span data-ttu-id="5782a-203">-RequestDeclineMessage</span><span class="sxs-lookup"><span data-stu-id="5782a-203">- RequestDeclineMessage</span></span>|  
  
11. <span data-ttu-id="5782a-204">Dans l’aire de conception, cliquez sur le **Send_1** forme.</span><span class="sxs-lookup"><span data-stu-id="5782a-204">On the design surface, click the **Send_1** shape.</span></span>  
  
12. <span data-ttu-id="5782a-205">Dans la fenêtre Propriétés, effectuez les paramétrages suivants :</span><span class="sxs-lookup"><span data-stu-id="5782a-205">In the Properties window, do the following:</span></span>  
  
    |<span data-ttu-id="5782a-206">Utiliser</span><span class="sxs-lookup"><span data-stu-id="5782a-206">Use this</span></span>|<span data-ttu-id="5782a-207">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="5782a-207">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="5782a-208">**Nom**</span><span class="sxs-lookup"><span data-stu-id="5782a-208">**Name**</span></span>|<span data-ttu-id="5782a-209">Type **SendRequestDecline**.</span><span class="sxs-lookup"><span data-stu-id="5782a-209">Type **SendRequestDecline**.</span></span>|  
    |<span data-ttu-id="5782a-210">**Message**</span><span class="sxs-lookup"><span data-stu-id="5782a-210">**Message**</span></span>|<span data-ttu-id="5782a-211">Sélectionnez **RequestDeclineMessage**.</span><span class="sxs-lookup"><span data-stu-id="5782a-211">Select **RequestDeclineMessage**.</span></span>|  
  
13. <span data-ttu-id="5782a-212">Dans l’aire de conception, cliquez sur le **Send_2** forme.</span><span class="sxs-lookup"><span data-stu-id="5782a-212">On the design surface, click the **Send_2** shape.</span></span>  
  
14. <span data-ttu-id="5782a-213">Dans la fenêtre Propriétés, effectuez les paramétrages suivants :</span><span class="sxs-lookup"><span data-stu-id="5782a-213">In the Properties window, do the following:</span></span>  
  
    |<span data-ttu-id="5782a-214">Utiliser</span><span class="sxs-lookup"><span data-stu-id="5782a-214">Use this</span></span>|<span data-ttu-id="5782a-215">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="5782a-215">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="5782a-216">**Nom**</span><span class="sxs-lookup"><span data-stu-id="5782a-216">**Name**</span></span>|<span data-ttu-id="5782a-217">Type **SendRequestToERP**.</span><span class="sxs-lookup"><span data-stu-id="5782a-217">Type **SendRequestToERP**.</span></span>|  
    |<span data-ttu-id="5782a-218">**Message**</span><span class="sxs-lookup"><span data-stu-id="5782a-218">**Message**</span></span>|<span data-ttu-id="5782a-219">Sélectionnez **RequestMessage**.</span><span class="sxs-lookup"><span data-stu-id="5782a-219">Select **RequestMessage**.</span></span>|  
  
## <a name="what-did-i-just-do"></a><span data-ttu-id="5782a-220">Actions effectuées</span><span class="sxs-lookup"><span data-stu-id="5782a-220">What did I just do?</span></span>  
 <span data-ttu-id="5782a-221">Au cours de cette étape, vous avez utilisé le Concepteur d'orchestration pour définir votre processus d'entreprise.</span><span class="sxs-lookup"><span data-stu-id="5782a-221">In this step, you used Orchestration Designer to define your business process.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="5782a-222">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="5782a-222">Next Steps</span></span>  
 <span data-ttu-id="5782a-223">Ajouter des ports logiques à l’orchestration dans [étape 3 : ajouter des Ports à l’Orchestration](../core/step-3-add-ports-to-the-orchestration.md).</span><span class="sxs-lookup"><span data-stu-id="5782a-223">You add logical ports to the orchestration in [Step 3: Add Ports to the Orchestration](../core/step-3-add-ports-to-the-orchestration.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5782a-224">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5782a-224">See Also</span></span>  
 <span data-ttu-id="5782a-225">[Étape 1 : Ajouter un projet EAIOrchestration à la Solution](../core/step-1-add-eaiorchestration-project-to-the-solution.md) </span><span class="sxs-lookup"><span data-stu-id="5782a-225">[Step 1: Add EAIOrchestration Project to the Solution](../core/step-1-add-eaiorchestration-project-to-the-solution.md) </span></span>  
 <span data-ttu-id="5782a-226">[Étape 3 : Ajouter des Ports à l’Orchestration](../core/step-3-add-ports-to-the-orchestration.md) </span><span class="sxs-lookup"><span data-stu-id="5782a-226">[Step 3: Add Ports to the Orchestration](../core/step-3-add-ports-to-the-orchestration.md) </span></span>  
 [<span data-ttu-id="5782a-227">Étape 4 : Création du projet EAIOrchestration</span><span class="sxs-lookup"><span data-stu-id="5782a-227">Step 4: Build the EAIOrchestration Project</span></span>](../core/step-4-build-the-eaiorchestration-project.md)