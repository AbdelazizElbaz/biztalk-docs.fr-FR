---
title: "Procédure pas à pas : Appel de la stratégie à partir d’une Orchestration | Documents Microsoft"
ms.custom: 
ms.date: 2016-04-05
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cb2d2974-8a36-4d36-905c-799e4236ef99
caps.latest.revision: "30"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 36de942d34a4235b689b464192a460451e7c921a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="walkthrough-invoking-the-policy-from-an-orchestration"></a><span data-ttu-id="47e9d-102">Procédure pas à pas : Appel de la stratégie à partir d’une Orchestration</span><span class="sxs-lookup"><span data-stu-id="47e9d-102">Walkthrough: Invoking the Policy from an Orchestration</span></span>
<span data-ttu-id="47e9d-103">Vous pouvez appeler une stratégie à partir d'une orchestration à l'aide de l'une des méthodes suivantes :</span><span class="sxs-lookup"><span data-stu-id="47e9d-103">You can invoke a policy from an orchestration in one of the following ways:</span></span>  
  
-   <span data-ttu-id="47e9d-104">À l’aide de la **appeler règles** forme</span><span class="sxs-lookup"><span data-stu-id="47e9d-104">By using the **Call Rules** shape</span></span>  
  
-   <span data-ttu-id="47e9d-105">À l’aide de la **Expression** mettre en forme et l’appelant de façon programmée le moteur de règles pour exécuter la stratégie (**Policy.Execute** méthode)</span><span class="sxs-lookup"><span data-stu-id="47e9d-105">By using the **Expression** shape, and programmatically invoking the rule engine to execute the policy (**Policy.Execute** method)</span></span>  
  
 <span data-ttu-id="47e9d-106">À l’aide de la **appeler règles** forme est la façon la plus courante et recommandée pour appeler une stratégie à partir d’une orchestration.</span><span class="sxs-lookup"><span data-stu-id="47e9d-106">Using the **Call Rules** shape is the most common way and also the recommended way to invoke a policy from an orchestration.</span></span> <span data-ttu-id="47e9d-107">Cette procédure pas à pas fournit des instructions détaillées pour l’utilisation de la **appeler règles** forme pour appeler le **ProcessPurchaseOrder** stratégie.</span><span class="sxs-lookup"><span data-stu-id="47e9d-107">This walkthrough provides step-by-step procedures for using the **Call Rules** shape to invoke the **ProcessPurchaseOrder** policy.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="47e9d-108">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="47e9d-108">Prerequisites</span></span>  
 <span data-ttu-id="47e9d-109">Vous devez effectuer la [procédure pas à pas : test de la stratégie](../core/walkthrough-testing-the-policy.md) procédure pas à pas avant d’effectuer cette procédure pas à pas.</span><span class="sxs-lookup"><span data-stu-id="47e9d-109">You must complete the [Walkthrough: Testing the Policy](../core/walkthrough-testing-the-policy.md) walkthrough before performing this walkthrough.</span></span>  
  
## <a name="overview-of-this-walkthrough"></a><span data-ttu-id="47e9d-110">Vue d’ensemble de cette procédure pas à pas</span><span class="sxs-lookup"><span data-stu-id="47e9d-110">Overview of This Walkthrough</span></span>  
 <span data-ttu-id="47e9d-111">Cette procédure est composée de sept autres procédures, comme illustré dans le tableau ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="47e9d-111">This walkthrough contains seven procedures, as described in the following table.</span></span>  
  
|<span data-ttu-id="47e9d-112">Titre de la procédure</span><span class="sxs-lookup"><span data-stu-id="47e9d-112">Procedure title</span></span>|<span data-ttu-id="47e9d-113">Description de la procédure</span><span class="sxs-lookup"><span data-stu-id="47e9d-113">Procedure description</span></span>|  
|---------------------|---------------------------|  
|<span data-ttu-id="47e9d-114">Pour créer un projet BizTalk avec un schéma et une orchestration</span><span class="sxs-lookup"><span data-stu-id="47e9d-114">To create a BizTalk project with a schema and an orchestration</span></span>|<span data-ttu-id="47e9d-115">Fournit des instructions détaillées pour la création d’un schéma et une orchestration qui appelle le **ProcessPurchaseOrder** stratégie.</span><span class="sxs-lookup"><span data-stu-id="47e9d-115">Provides step-by-step instructions for creating a schema and an orchestration that invokes the **ProcessPurchaseOrder** policy.</span></span>|  
|<span data-ttu-id="47e9d-116">Pour créer des variables de message</span><span class="sxs-lookup"><span data-stu-id="47e9d-116">To create message variables</span></span>|<span data-ttu-id="47e9d-117">Fournit des instructions détaillées pour la création des variables de message utilisées dans l'orchestration.</span><span class="sxs-lookup"><span data-stu-id="47e9d-117">Provides step-by-step instructions for creating message variables used in the orchestration.</span></span>|  
|<span data-ttu-id="47e9d-118">Pour configurer des formes</span><span class="sxs-lookup"><span data-stu-id="47e9d-118">To configure shapes</span></span>|<span data-ttu-id="47e9d-119">Fournit des instructions détaillées pour la configuration de formes dans l'orchestration.</span><span class="sxs-lookup"><span data-stu-id="47e9d-119">Provides step-by-step instructions for configuring shapes in the orchestration.</span></span>|  
|<span data-ttu-id="47e9d-120">Pour créer des ports</span><span class="sxs-lookup"><span data-stu-id="47e9d-120">To create ports</span></span>|<span data-ttu-id="47e9d-121">Fournit des instructions détaillées pour la création de ports dans l'orchestration.</span><span class="sxs-lookup"><span data-stu-id="47e9d-121">Provides step-by-step instructions for creating ports in the orchestration.</span></span>|  
|<span data-ttu-id="47e9d-122">Pour connecter des ports aux formes</span><span class="sxs-lookup"><span data-stu-id="47e9d-122">To connect ports with the shapes</span></span>|<span data-ttu-id="47e9d-123">Fournit des instructions détaillées pour la connexion de ports aux formes.</span><span class="sxs-lookup"><span data-stu-id="47e9d-123">Provides step-by-step instructions for connecting ports with the shapes.</span></span>|  
|<span data-ttu-id="47e9d-124">Pour créer et déployer la solution</span><span class="sxs-lookup"><span data-stu-id="47e9d-124">To build and deploy the solution</span></span>|<span data-ttu-id="47e9d-125">Fournit des instructions détaillées pour la création et le déploiement de la solution.</span><span class="sxs-lookup"><span data-stu-id="47e9d-125">Provides step-by-step instructions for building and deploying the solution.</span></span>|  
|<span data-ttu-id="47e9d-126">Pour tester la solution</span><span class="sxs-lookup"><span data-stu-id="47e9d-126">To test the solution</span></span>|<span data-ttu-id="47e9d-127">Fournit des instructions pas à pas pour le test de la solution.</span><span class="sxs-lookup"><span data-stu-id="47e9d-127">Provides step-by-step instructions for testing the solution.</span></span>|  
  
### <a name="to-create-a-biztalk-project-with-a-schema-and-an-orchestration"></a><span data-ttu-id="47e9d-128">Pour créer un projet BizTalk avec un schéma et une orchestration</span><span class="sxs-lookup"><span data-stu-id="47e9d-128">To create a BizTalk project with a schema and an orchestration</span></span>  
  
1.  <span data-ttu-id="47e9d-129">Démarrer **Microsoft Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="47e9d-129">Start **Microsoft Visual Studio**.</span></span>  
  
2.  <span data-ttu-id="47e9d-130">Dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], dans le **fichier** menu, pointez sur **nouveau**, puis cliquez sur **projet**.</span><span class="sxs-lookup"><span data-stu-id="47e9d-130">In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], on the **File** menu, point to **New**, and then click **Project**.</span></span>  
  
3.  <span data-ttu-id="47e9d-131">Dans le **nouveau projet** boîte de dialogue zone, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="47e9d-131">In the **New Project** dialog box, do the following:</span></span>  
  
    |<span data-ttu-id="47e9d-132">Utiliser</span><span class="sxs-lookup"><span data-stu-id="47e9d-132">Use this</span></span>|<span data-ttu-id="47e9d-133">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="47e9d-133">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="47e9d-134">**Types de projets**</span><span class="sxs-lookup"><span data-stu-id="47e9d-134">**Project types**</span></span>|<span data-ttu-id="47e9d-135">Cliquez sur **projets BizTalk**.</span><span class="sxs-lookup"><span data-stu-id="47e9d-135">Click **BizTalk Projects**.</span></span>|  
    |<span data-ttu-id="47e9d-136">**Modèles**</span><span class="sxs-lookup"><span data-stu-id="47e9d-136">**Templates**</span></span>|<span data-ttu-id="47e9d-137">Cliquez sur **vide le projet BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="47e9d-137">Click **Empty BizTalk Server Project**.</span></span>|  
    |<span data-ttu-id="47e9d-138">**Nom**</span><span class="sxs-lookup"><span data-stu-id="47e9d-138">**Name**</span></span>|<span data-ttu-id="47e9d-139">Type **RuleTest**.</span><span class="sxs-lookup"><span data-stu-id="47e9d-139">Type **RuleTest**.</span></span>|  
    |<span data-ttu-id="47e9d-140">**Emplacement**</span><span class="sxs-lookup"><span data-stu-id="47e9d-140">**Location**</span></span>|<span data-ttu-id="47e9d-141">Spécifiez **C:\BRE-Walkthroughs**.</span><span class="sxs-lookup"><span data-stu-id="47e9d-141">Specify **C:\BRE-Walkthroughs**.</span></span>|  
    |<span data-ttu-id="47e9d-142">**Nom de solution**</span><span class="sxs-lookup"><span data-stu-id="47e9d-142">**Solution Name**</span></span>|<span data-ttu-id="47e9d-143">Type **RuleTestSol**.</span><span class="sxs-lookup"><span data-stu-id="47e9d-143">Type **RuleTestSol**.</span></span>|  
    |<span data-ttu-id="47e9d-144">**Créer le répertoire pour la solution**</span><span class="sxs-lookup"><span data-stu-id="47e9d-144">**Create directory for solution**</span></span>|<span data-ttu-id="47e9d-145">Activez cette case à cocher afin de créer un répertoire pour les fichiers de la solution.</span><span class="sxs-lookup"><span data-stu-id="47e9d-145">Select this check box to create a directory for the solution files.</span></span>|  
  
4.  <span data-ttu-id="47e9d-146">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="47e9d-146">Click **OK**.</span></span> <span data-ttu-id="47e9d-147">Le **RuleTest** projet doit s’afficher dans l’Explorateur de solutions.</span><span class="sxs-lookup"><span data-stu-id="47e9d-147">The **RuleTest** project should appear in Solution Explorer.</span></span> <span data-ttu-id="47e9d-148">Si vous ne voyez pas l’Explorateur de solutions, cliquez sur **l’Explorateur de solutions** sur la **vue** menu.</span><span class="sxs-lookup"><span data-stu-id="47e9d-148">If you do not see Solution Explorer, click **Solution Explorer** on the **View** menu.</span></span>  
  
5.  <span data-ttu-id="47e9d-149">Dans l’Explorateur de solutions, cliquez sur **RuleTest**, pointez sur **ajouter**, puis cliquez sur **élément existant**.</span><span class="sxs-lookup"><span data-stu-id="47e9d-149">In Solution Explorer, right-click **RuleTest**, point to **Add**, and then click **Existing Item**.</span></span>  
  
6.  <span data-ttu-id="47e9d-150">Parcourir et d’ajouter le **PO.xsd** fichier de schéma que vous avez créé dans le [procédure pas à pas : création d’une stratégie commerciale Simple](../core/walkthrough-creating-a-simple-business-policy.md) procédure pas à pas.</span><span class="sxs-lookup"><span data-stu-id="47e9d-150">Browse and add the **PO.xsd** schema file you created in the [Walkthrough: Creating a Simple Business Policy](../core/walkthrough-creating-a-simple-business-policy.md) walkthrough.</span></span> <span data-ttu-id="47e9d-151">Visual Studio effectue une copie de la **PO.xsd** de fichier et l’ajoute au projet.</span><span class="sxs-lookup"><span data-stu-id="47e9d-151">Visual Studio makes a copy of the **PO.xsd** file and adds it to the project.</span></span>  
  
7.  <span data-ttu-id="47e9d-152">Dans l’Explorateur de solutions, cliquez sur **RuleTest**, pointez sur **ajouter**, puis cliquez sur **un nouvel élément**.</span><span class="sxs-lookup"><span data-stu-id="47e9d-152">In Solution Explorer, right-click **RuleTest**, point to **Add**, and then click **New Item**.</span></span>  
  
8.  <span data-ttu-id="47e9d-153">Dans le **ajouter un nouvel élément** boîte de dialogue zone, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="47e9d-153">In the **Add New Item** dialog box, do the following:</span></span>  
  
    |<span data-ttu-id="47e9d-154">Utiliser</span><span class="sxs-lookup"><span data-stu-id="47e9d-154">Use this</span></span>|<span data-ttu-id="47e9d-155">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="47e9d-155">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="47e9d-156">**Catégories**</span><span class="sxs-lookup"><span data-stu-id="47e9d-156">**Categories**</span></span>|<span data-ttu-id="47e9d-157">Cliquez sur **fichiers d’Orchestration**.</span><span class="sxs-lookup"><span data-stu-id="47e9d-157">Click **Orchestration Files**.</span></span>|  
    |<span data-ttu-id="47e9d-158">**Modèles**</span><span class="sxs-lookup"><span data-stu-id="47e9d-158">**Templates**</span></span>|<span data-ttu-id="47e9d-159">Cliquez sur **Orchestration BizTalk**.</span><span class="sxs-lookup"><span data-stu-id="47e9d-159">Click **BizTalk Orchestration**.</span></span>|  
    |<span data-ttu-id="47e9d-160">**Nom**</span><span class="sxs-lookup"><span data-stu-id="47e9d-160">**Name**</span></span>|<span data-ttu-id="47e9d-161">Type **RuleTest.odx**.</span><span class="sxs-lookup"><span data-stu-id="47e9d-161">Type **RuleTest.odx**.</span></span>|  
  
9. <span data-ttu-id="47e9d-162">Cliquez sur **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="47e9d-162">Click **Add**.</span></span>  
  
10. <span data-ttu-id="47e9d-163">Avec le bouton droit **déposez une forme à partir de la boîte à outils ici**, pointez sur **insérer une forme**, puis cliquez sur **réception**.</span><span class="sxs-lookup"><span data-stu-id="47e9d-163">Right-click **Drop a shape from the toolbox here**, point to **Insert Shape**, and then click **Receive**.</span></span>  
  
11. <span data-ttu-id="47e9d-164">Dans la fenêtre Propriétés, remplacez le nom de la **réception** à mettre en forme **ReceivePO**et définissez la valeur de la **activer** propriété `true`.</span><span class="sxs-lookup"><span data-stu-id="47e9d-164">In the Properties window, change the name of the **Receive** shape to **ReceivePO**, and set the value of the **Activate** property to `true`.</span></span>  
  
12. <span data-ttu-id="47e9d-165">Dans la boîte à outils, sur le **Orchestrations BizTalk** onglet, faites glisser le **appeler règles** forme sur une ligne de connexion sous la **réception** forme.</span><span class="sxs-lookup"><span data-stu-id="47e9d-165">In the Toolbox, on the **BizTalk Orchestrations** tab, drag the **Call Rules** shape onto a connecting line below the **Receive** shape.</span></span>  
  
13. <span data-ttu-id="47e9d-166">Dans la fenêtre Propriétés, remplacez le nom de la **appeler règles** à mettre en forme **CallProcessPOPolicy**.</span><span class="sxs-lookup"><span data-stu-id="47e9d-166">In the Properties window, change the name of the **Call Rules** shape to **CallProcessPOPolicy**.</span></span>  
  
14. <span data-ttu-id="47e9d-167">Avec le bouton ci-dessous le **appeler règles** mettre en forme, pointez sur **insérer une forme**, puis cliquez sur **envoyer**.</span><span class="sxs-lookup"><span data-stu-id="47e9d-167">Right-click below the **Call Rules** shape, point to **Insert Shape**, and then click **Send**.</span></span>  
  
15. <span data-ttu-id="47e9d-168">Dans la fenêtre Propriétés, remplacez le nom de la **envoyer** à mettre en forme **SendPO**.</span><span class="sxs-lookup"><span data-stu-id="47e9d-168">In the Properties window, change the name of the **Send** shape to **SendPO**.</span></span> <span data-ttu-id="47e9d-169">L'orchestration doit présenter l'aspect suivant :</span><span class="sxs-lookup"><span data-stu-id="47e9d-169">The orchestration should look like the following figure.</span></span>  
  
     <span data-ttu-id="47e9d-170">![BRE &#45; Procédure pas à pas &#45; UnconfiguredOrch](../core/media/1f3502ac-82a9-40bf-ae31-6e8356a283e2.gif "1f3502ac-82a9-40bf-ae31-6e8356a283e2")</span><span class="sxs-lookup"><span data-stu-id="47e9d-170">![BRE&#45;Walkthrough&#45;UnconfiguredOrch](../core/media/1f3502ac-82a9-40bf-ae31-6e8356a283e2.gif "1f3502ac-82a9-40bf-ae31-6e8356a283e2")</span></span>  
  
### <a name="to-create-message-variables"></a><span data-ttu-id="47e9d-171">Pour créer des variables de message</span><span class="sxs-lookup"><span data-stu-id="47e9d-171">To create message variables</span></span>  
  
1.  <span data-ttu-id="47e9d-172">Dans la fenêtre Vue Orchestration, cliquez sur **Messages**, puis cliquez sur **nouveau Message**.</span><span class="sxs-lookup"><span data-stu-id="47e9d-172">In the Orchestration View window, right-click **Messages**, and then click **New Message**.</span></span> <span data-ttu-id="47e9d-173">Si vous ne voyez pas la fenêtre Vue Orchestration, cliquez sur le **vue** menu, pointez sur **autres fenêtres**, puis cliquez sur **Vue Orchestration**.</span><span class="sxs-lookup"><span data-stu-id="47e9d-173">If you do not see the Orchestration View window, click the **View** menu, point to **Other Windows**, and then click **Orchestration View**.</span></span> <span data-ttu-id="47e9d-174">Normalement, la fenêtre Vue Orchestration correspond à l'onglet situé à côté de celui de la fenêtre Explorateur de solutions. Par défaut, le nouveau message nommé **Message_1**.</span><span class="sxs-lookup"><span data-stu-id="47e9d-174">Typically, the Orchestration View window is on the tab next to the Solution Explorer tab. By default, the new message is named **Message_1**.</span></span>  
  
     <span data-ttu-id="47e9d-175">![BRE &#45; Procédure pas à pas &#45; OrchViewNewMsg](../core/media/a0b7fee3-af90-4c01-9464-146f0ca449e5.gif "a0b7fee3-af90-4c01-9464-146f0ca449e5")</span><span class="sxs-lookup"><span data-stu-id="47e9d-175">![BRE&#45;Walkthrough&#45;OrchViewNewMsg](../core/media/a0b7fee3-af90-4c01-9464-146f0ca449e5.gif "a0b7fee3-af90-4c01-9464-146f0ca449e5")</span></span>  
  
2.  <span data-ttu-id="47e9d-176">Dans la fenêtre Vue Orchestration, cliquez sur **Message_1**.</span><span class="sxs-lookup"><span data-stu-id="47e9d-176">In the Orchestration View window, click **Message_1**.</span></span>  
  
3.  <span data-ttu-id="47e9d-177">Dans la fenêtre Propriétés, effectuez les paramétrages suivants :</span><span class="sxs-lookup"><span data-stu-id="47e9d-177">In the Properties window, do the following:</span></span>  
  
    |<span data-ttu-id="47e9d-178">Utiliser</span><span class="sxs-lookup"><span data-stu-id="47e9d-178">Use this</span></span>|<span data-ttu-id="47e9d-179">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="47e9d-179">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="47e9d-180">**Identificateur**</span><span class="sxs-lookup"><span data-stu-id="47e9d-180">**Identifier**</span></span>|<span data-ttu-id="47e9d-181">Type **POInst**, puis appuyez sur ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="47e9d-181">Type **POInst**, and then press ENTER.</span></span>|  
    |<span data-ttu-id="47e9d-182">**Type de message**</span><span class="sxs-lookup"><span data-stu-id="47e9d-182">**Message Type**</span></span>|<span data-ttu-id="47e9d-183">Dans la liste déroulante, développez **schémas**, puis sélectionnez **RuleTest.PO**.</span><span class="sxs-lookup"><span data-stu-id="47e9d-183">From the drop-down list, expand **Schemas**, and then select **RuleTest.PO**.</span></span>|  
  
     <span data-ttu-id="47e9d-184">![BRE &#45; Procédure pas à pas &#45; MsgProps](../core/media/c82cfb67-63f6-4133-95bf-daadac0e213a.gif "c82cfb67-63f6-4133-95bf-daadac0e213a")</span><span class="sxs-lookup"><span data-stu-id="47e9d-184">![BRE&#45;Walkthrough&#45;MsgProps](../core/media/c82cfb67-63f6-4133-95bf-daadac0e213a.gif "c82cfb67-63f6-4133-95bf-daadac0e213a")</span></span>  
  
### <a name="to-configure-shapes"></a><span data-ttu-id="47e9d-185">Pour configurer des formes</span><span class="sxs-lookup"><span data-stu-id="47e9d-185">To configure shapes</span></span>  
  
1.  <span data-ttu-id="47e9d-186">Sélectionnez le **réception** forme dans le Concepteur d’Orchestration.</span><span class="sxs-lookup"><span data-stu-id="47e9d-186">Select the **Receive** shape in Orchestration Designer.</span></span>  
  
2.  <span data-ttu-id="47e9d-187">Dans la fenêtre Propriétés, sélectionnez **POInst** pour le **Message** propriété.</span><span class="sxs-lookup"><span data-stu-id="47e9d-187">In the Properties window, select **POInst** for the **Message** property.</span></span>  
  
3.  <span data-ttu-id="47e9d-188">Double-cliquez sur le **appeler règles** forme dans le Concepteur d’Orchestration.</span><span class="sxs-lookup"><span data-stu-id="47e9d-188">Double-click the **Call Rules** shape in Orchestration Designer.</span></span>  
  
4.  <span data-ttu-id="47e9d-189">Dans le **configuration de la stratégie appeler règles** boîte de dialogue, sélectionnez **ProcessPurchaseOrder** pour la stratégie.</span><span class="sxs-lookup"><span data-stu-id="47e9d-189">In the **Call Rules policy configuration** dialog box, select **ProcessPurchaseOrder** for the policy.</span></span>  
  
5.  <span data-ttu-id="47e9d-190">Cliquez sur Suivant pour  **\*** ci-dessous **nom de paramètre**, puis sélectionnez **POInst** en tant que paramètre à la stratégie.</span><span class="sxs-lookup"><span data-stu-id="47e9d-190">Click next to **\***, below **Parameter Name**, and select **POInst** as a parameter to the policy.</span></span>  
  
     <span data-ttu-id="47e9d-191">![BRE &#45; Procédure pas à pas &#45; ConfigureCallRules](../core/media/0e7dab04-41db-433b-bbf5-b13901033b41.gif "0e7dab04-41db-433b-bbf5-b13901033b41")</span><span class="sxs-lookup"><span data-stu-id="47e9d-191">![BRE&#45;Walkthrough&#45;ConfigureCallRules](../core/media/0e7dab04-41db-433b-bbf5-b13901033b41.gif "0e7dab04-41db-433b-bbf5-b13901033b41")</span></span>  
  
6.  <span data-ttu-id="47e9d-192">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="47e9d-192">Click **OK**.</span></span>  
  
7.  <span data-ttu-id="47e9d-193">Sélectionnez le **envoyer** forme de l’orchestration.</span><span class="sxs-lookup"><span data-stu-id="47e9d-193">Select the **Send** shape in the orchestration.</span></span>  
  
8.  <span data-ttu-id="47e9d-194">Dans la fenêtre Propriétés, définissez la valeur de la **Type de Message** propriété **POInst**.</span><span class="sxs-lookup"><span data-stu-id="47e9d-194">In the Properties window, set the value of the **Message Type** property to **POInst**.</span></span>  
  
### <a name="to-create-ports"></a><span data-ttu-id="47e9d-195">Pour créer des ports</span><span class="sxs-lookup"><span data-stu-id="47e9d-195">To create ports</span></span>  
  
1.  <span data-ttu-id="47e9d-196">Créez deux dossiers, **entrée** et **sortie**, dans le dossier C:\BRE-Walkthroughs\RuleTestSol.</span><span class="sxs-lookup"><span data-stu-id="47e9d-196">Create two folders, **Input** and **Output**, in the C:\BRE-Walkthroughs\RuleTestSol folder.</span></span>  
  
2.  <span data-ttu-id="47e9d-197">Avec le bouton droit de la surface du port de gauche de l’orchestration, puis cliquez sur **nouveau Port configuré**.</span><span class="sxs-lookup"><span data-stu-id="47e9d-197">Right-click the left port surface of the orchestration, and then click **New Configured Port**.</span></span>  
  
3.  <span data-ttu-id="47e9d-198">Cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="47e9d-198">Click **Next**.</span></span> <span data-ttu-id="47e9d-199">Type **ReceivePOPrt** pour le nom du port.</span><span class="sxs-lookup"><span data-stu-id="47e9d-199">Type **ReceivePOPrt** for the port name.</span></span>  
  
4.  <span data-ttu-id="47e9d-200">Cliquez sur **suivant** à deux reprises.</span><span class="sxs-lookup"><span data-stu-id="47e9d-200">Click **Next** twice.</span></span>  
  
5.  <span data-ttu-id="47e9d-201">Sélectionnez **spécifier maintenant** pour le **liaison de port**.</span><span class="sxs-lookup"><span data-stu-id="47e9d-201">Select **Specify Now** for the **port binding**.</span></span>  
  
6.  <span data-ttu-id="47e9d-202">Spécifiez **fichier** pour le **transport**, puis tapez le nom du répertoire d’entrée en tant que **C:\BRE-Walkthroughs\RuleTestSol\Input\\\*.xml** en même temps que le masque de fichier (**\*.xml**) pour l’URI.</span><span class="sxs-lookup"><span data-stu-id="47e9d-202">Specify **FILE** for the **transport**, and type the name of the input directory as **C:\BRE-Walkthroughs\RuleTestSol\Input\\\*.xml** along with the file mask (**\*.xml**) for the URI.</span></span>  
  
7.  <span data-ttu-id="47e9d-203">Cliquez sur **Suivant**, puis sur **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="47e9d-203">Click **Next**, and then click **Finish**.</span></span>  
  
8.  <span data-ttu-id="47e9d-204">Avec le bouton droit de la surface du port de droite de l’orchestration, puis cliquez sur **nouveau Port configuré**.</span><span class="sxs-lookup"><span data-stu-id="47e9d-204">Right-click the right port surface of the orchestration, and then click **New Configuration Port**.</span></span>  
  
9. <span data-ttu-id="47e9d-205">Cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="47e9d-205">Click **Next**.</span></span> <span data-ttu-id="47e9d-206">Type **SendPOPort** pour le nom du port.</span><span class="sxs-lookup"><span data-stu-id="47e9d-206">Type **SendPOPort** for the port name.</span></span>  
  
10. <span data-ttu-id="47e9d-207">Cliquez sur **suivant** à deux reprises.</span><span class="sxs-lookup"><span data-stu-id="47e9d-207">Click **Next** twice.</span></span>  
  
11. <span data-ttu-id="47e9d-208">Modifier la **direction de communication du Port** à **toujours envoyer les messages sur ce port**.</span><span class="sxs-lookup"><span data-stu-id="47e9d-208">Change the **Port direction of communication** to **I'll always be sending messages on this port**.</span></span>  
  
12. <span data-ttu-id="47e9d-209">Sélectionnez **spécifier maintenant** pour le **liaison de port**.</span><span class="sxs-lookup"><span data-stu-id="47e9d-209">Select **Specify Now** for the **port binding**.</span></span>  
  
13. <span data-ttu-id="47e9d-210">Spécifiez **fichier** pour le **transport**, puis tapez le nom du répertoire de sortie en tant que **C:\BRE-Walkthroughs\RuleTestSol\Output**et %MessageID%.xml en tant que le fichier de sortie nom.</span><span class="sxs-lookup"><span data-stu-id="47e9d-210">Specify **FILE** for the **transport**, and type the name of the output directory as **C:\BRE-Walkthroughs\RuleTestSol\Output**,and %MessageID%.xml as the output file name.</span></span>  
  
14. <span data-ttu-id="47e9d-211">Cliquez sur **Suivant**, puis sur **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="47e9d-211">Click **Next**, and then click **Finish**.</span></span>  
  
### <a name="to-connect-ports-with-the-shapes"></a><span data-ttu-id="47e9d-212">Pour connecter des ports aux formes</span><span class="sxs-lookup"><span data-stu-id="47e9d-212">To connect ports with the shapes</span></span>  
  
1.  <span data-ttu-id="47e9d-213">Connecter le **ReceivePOPrt** port pour le **ReceivePO** forme.</span><span class="sxs-lookup"><span data-stu-id="47e9d-213">Connect the **ReceivePOPrt** port to the **ReceivePO** shape.</span></span> <span data-ttu-id="47e9d-214">(dans la surface du port, faites glisser la flèche à droite du port ReceivePort vers la boîte de la forme ReceivePO).</span><span class="sxs-lookup"><span data-stu-id="47e9d-214">(Drag the arrow to the right of ReceivePOPrt port on the port surface to the box on the ReceivePO shape.)</span></span>  
  
     <span data-ttu-id="47e9d-215">![BRE &#45; Procédure pas à pas &#45; ConnectRP](../core/media/75bdf79e-ca98-43bb-8ff6-5f46005a6490.gif "75bdf79e-ca98-43bb-8ff6-5f46005a6490")</span><span class="sxs-lookup"><span data-stu-id="47e9d-215">![BRE&#45;Walkthrough&#45;ConnectRP](../core/media/75bdf79e-ca98-43bb-8ff6-5f46005a6490.gif "75bdf79e-ca98-43bb-8ff6-5f46005a6490")</span></span>  
  
2.  <span data-ttu-id="47e9d-216">Connecter le **SendPO** à mettre en forme le **SendPOPrt** port.</span><span class="sxs-lookup"><span data-stu-id="47e9d-216">Connect the **SendPO** shape to the **SendPOPrt** port.</span></span>  
  
     <span data-ttu-id="47e9d-217">![BRE &#45; Procédure pas à pas &#45; ConnectSP](../core/media/7513f52b-2782-4357-b8eb-1874dec33869.gif "7513f52b-2782-4357-b8eb-1874dec33869")</span><span class="sxs-lookup"><span data-stu-id="47e9d-217">![BRE&#45;Walkthrough&#45;ConnectSP](../core/media/7513f52b-2782-4357-b8eb-1874dec33869.gif "7513f52b-2782-4357-b8eb-1874dec33869")</span></span>  
  
### <a name="to-build-and-deploy-the-solution"></a><span data-ttu-id="47e9d-218">Pour créer et déployer la solution</span><span class="sxs-lookup"><span data-stu-id="47e9d-218">To build and deploy the solution</span></span>  
  
1.  <span data-ttu-id="47e9d-219">Démarrer **Microsoft Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="47e9d-219">Start **Microsoft Visual Studio**.</span></span>  
  
2.  <span data-ttu-id="47e9d-220">Dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], dans l’Explorateur de solutions, cliquez sur le **RuleTest** de projet, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="47e9d-220">In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], in Solution Explorer, right-click the **RuleTest** project, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="47e9d-221">Dans le Concepteur de projet (dans le volet central), cliquez sur **signature**.</span><span class="sxs-lookup"><span data-stu-id="47e9d-221">In Project Designer (in the center pane), click **Signing**.</span></span>  
  
4.  <span data-ttu-id="47e9d-222">Dans l’onglet signature, cochez **signer l’assembly** case à cocher ; Dans la liste déroulante **choisir un fichier de clé de nom fort**, cliquez sur **nouveau**; Dans le **nom de fichier de clé** , entrez Test de la règle ; Dans le **mot de passe** champ (facultatif), définir le mot de passe, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="47e9d-222">In Signing tab, Check **Sign the assembly** checkbox; In the dropdown list **Choose a strong name key file**, click **New**; In the **Key File name** field, enter Rule Test; In the **Password** field (Optional),  set Password, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="47e9d-223">Dans le Concepteur de projets, cliquez sur **déploiement** pour basculer vers l’onglet déploiement.</span><span class="sxs-lookup"><span data-stu-id="47e9d-223">In Project Designer, click **Deployment** to switch to the Deployment tab.</span></span>  
  
6.  <span data-ttu-id="47e9d-224">Spécifiez **RuleTestApp** comme nom d’application.</span><span class="sxs-lookup"><span data-stu-id="47e9d-224">Specify **RuleTestApp** as the application name.</span></span>  
  
     <span data-ttu-id="47e9d-225">![BRE &#45; Procédure pas à pas &#45; RuleTestApp](../core/media/b153e5b0-ca46-4d27-bfa1-9ad4e58e9787.gif "b153e5b0-ca46-4d27-bfa1-9ad4e58e9787")</span><span class="sxs-lookup"><span data-stu-id="47e9d-225">![BRE&#45;Walkthrough&#45;RuleTestApp](../core/media/b153e5b0-ca46-4d27-bfa1-9ad4e58e9787.gif "b153e5b0-ca46-4d27-bfa1-9ad4e58e9787")</span></span>  
  
7.  <span data-ttu-id="47e9d-226">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="47e9d-226">Click **OK**.</span></span>  
  
8.  <span data-ttu-id="47e9d-227">Cliquez sur le **RuleTest** de projet, puis cliquez sur **générer**.</span><span class="sxs-lookup"><span data-stu-id="47e9d-227">Right-click the **RuleTest** project, and then click **Build**.</span></span>  
  
9. <span data-ttu-id="47e9d-228">Cliquez sur le **RuleTest** de projet, puis cliquez sur **déployer**.</span><span class="sxs-lookup"><span data-stu-id="47e9d-228">Right-click the **RuleTest** project, and then click **Deploy**.</span></span>  
  
### <a name="to-test-the-solution"></a><span data-ttu-id="47e9d-229">Pour tester la solution</span><span class="sxs-lookup"><span data-stu-id="47e9d-229">To test the solution</span></span>  
  
1.  <span data-ttu-id="47e9d-230">Dans l’éditeur des règles d’entreprise, développez **stratégies**, développez **ProcessPurchaseOrder**, avec le bouton droit **Version 1.0**, puis cliquez sur **publier**.</span><span class="sxs-lookup"><span data-stu-id="47e9d-230">In Business Rule Composer, expand **Policies**, expand **ProcessPurchaseOrder**, right-click **Version 1.0**, and then click **Publish**.</span></span>  
  
2.  <span data-ttu-id="47e9d-231">Avec le bouton droit **Version 1.0 - publiée**, puis cliquez sur **déployer**.</span><span class="sxs-lookup"><span data-stu-id="47e9d-231">Right-click **Version 1.0 - Published**, and then click **Deploy**.</span></span>  
  
3.  <span data-ttu-id="47e9d-232">Dans le **Démarrer** menu, ouvrir **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="47e9d-232">In the **Start** menu, open **BizTalk Server Administration**.</span></span> <span data-ttu-id="47e9d-233">Si la console Administration de BizTalk Server est déjà ouverte, appuyez sur la touche F5 pour l'actualiser.</span><span class="sxs-lookup"><span data-stu-id="47e9d-233">If you have the BizTalk Server Administration console already open, press F5 to refresh it.</span></span>  
  
4.  <span data-ttu-id="47e9d-234">Développez **racine de la Console**, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], développez **groupe BizTalk**, puis développez **Applications**.</span><span class="sxs-lookup"><span data-stu-id="47e9d-234">Expand **Console Root**, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Group**, and then expand **Applications**.</span></span>  
  
5.  <span data-ttu-id="47e9d-235">Avec le bouton droit **RuleTestApp**, puis cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="47e9d-235">Right-click **RuleTestApp**, and then click **Configure**.</span></span>  
  
6.  <span data-ttu-id="47e9d-236">Cliquez sur **Orchestration_1**et spécifiez **BizTalkServerApplication** en tant que l’ordinateur hôte.</span><span class="sxs-lookup"><span data-stu-id="47e9d-236">Click **Orchestration_1**, and specify **BizTalkServerApplication** as the host.</span></span>  
  
     <span data-ttu-id="47e9d-237">![BRE &#45; Procédure pas à pas &#45; AppHost](../core/media/ba348a98-661f-4e71-8b9b-b8c5fadf035a.gif "ba348a98-661f-4e71-8b9b-b8c5fadf035a")</span><span class="sxs-lookup"><span data-stu-id="47e9d-237">![BRE&#45;Walkthrough&#45;AppHost](../core/media/ba348a98-661f-4e71-8b9b-b8c5fadf035a.gif "ba348a98-661f-4e71-8b9b-b8c5fadf035a")</span></span>  
  
7.  <span data-ttu-id="47e9d-238">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="47e9d-238">Click **OK**.</span></span>  
  
8.  <span data-ttu-id="47e9d-239">Avec le bouton droit **RuleTestApp**, puis cliquez sur **Démarrer**.</span><span class="sxs-lookup"><span data-stu-id="47e9d-239">Right-click **RuleTestApp**, and then click **Start**.</span></span>  
  
9. <span data-ttu-id="47e9d-240">Dans le **démarrer l’Application 'RuleTestApp'** boîte de dialogue, cliquez sur **Démarrer**, puis attendez que l’application est démarrée avec succès.</span><span class="sxs-lookup"><span data-stu-id="47e9d-240">In the **Start 'RuleTestApp' Application** dialog box, click **Start**, and then wait until the application is started successfully.</span></span>  
  
10. <span data-ttu-id="47e9d-241">Ouvrez **SamplePO.xml** et **SamplePO2.xml** dans le bloc-notes et remplacez la valeur de la **état** au champ **XYZ**.</span><span class="sxs-lookup"><span data-stu-id="47e9d-241">Open **SamplePO.xml** and **SamplePO2.xml** in Notepad and change the value of the **Status** field to **XYZ**.</span></span>  
  
11. <span data-ttu-id="47e9d-242">Copie le **SamplePO.xml** fichier à partir du répertoire C:\BRE-Walkthroughs vers le répertoire C:\BRE-Walkthroughs\RuleTestSol\Input pour l’orchestration.</span><span class="sxs-lookup"><span data-stu-id="47e9d-242">Copy the **SamplePO.xml** file from the C:\BRE-Walkthroughs directory to the C:\BRE-Walkthroughs\RuleTestSol\Input directory for the orchestration.</span></span>  
  
12. <span data-ttu-id="47e9d-243">Un fichier de sortie doit s'afficher pour l'orchestration dans le répertoire C:\BRE-Walkthroughs\RuleTestSol\Output.</span><span class="sxs-lookup"><span data-stu-id="47e9d-243">You should see an output file in the C:\BRE-Walkthroughs\RuleTestSol\Output directory for the orchestration.</span></span> <span data-ttu-id="47e9d-244">Ouvrez le fichier XML de sortie et notez que la valeur de la **état** champ est défini sur **approuvé**.</span><span class="sxs-lookup"><span data-stu-id="47e9d-244">Open the output XML file and notice that the value of the **Status** field is set to **Approved**.</span></span>  
  
13. <span data-ttu-id="47e9d-245">Répétez les étapes 11 et 12 avec **SamplePO2.xml**et notez que la valeur de la **état** champ dans le document de sortie est identique à celle du document d’entrée (**xyz**).</span><span class="sxs-lookup"><span data-stu-id="47e9d-245">Repeat steps 11 and 12 with **SamplePO2.xml**, and notice that the value of the **Status** field in the output document is the same as in the input document (**xyz**).</span></span>  
  
## <a name="comments"></a><span data-ttu-id="47e9d-246">Commentaires</span><span class="sxs-lookup"><span data-stu-id="47e9d-246">Comments</span></span>  
  
-   <span data-ttu-id="47e9d-247">Dans cette procédure pas à pas, pour ajouter une forme à l'orchestration, vous n'avez pas utilisé celles de la Boîte à outils.</span><span class="sxs-lookup"><span data-stu-id="47e9d-247">In this walkthrough, to add the shapes to the orchestration, you did not use the shapes from the Toolbox.</span></span> <span data-ttu-id="47e9d-248">Vous avez en effet cliqué avec le bouton droit de votre souris pour sélectionner la forme à insérer.</span><span class="sxs-lookup"><span data-stu-id="47e9d-248">Instead, you clicked the right mouse button and selected the shape that you wanted to insert.</span></span>  
  
-   <span data-ttu-id="47e9d-249">La configuration de la **appeler règles** forme examine la toute dernière version enregistrée lors de la détermination des types utilisés.</span><span class="sxs-lookup"><span data-stu-id="47e9d-249">The configuration for the **Call Rules** shape looks at the latest saved version when determining the types used.</span></span> <span data-ttu-id="47e9d-250">Lors de l'exécution, la dernière version déployée sera utilisée.</span><span class="sxs-lookup"><span data-stu-id="47e9d-250">At run time, the latest deployed version will be used.</span></span>  
  
-   <span data-ttu-id="47e9d-251">Si vous envisagez d’utiliser une version autre que la dernière version déployée de la stratégie, vous devez utiliser un **Expression** mettre en forme et appeler le moteur de règles par programme pour exécuter la stratégie de cette version.</span><span class="sxs-lookup"><span data-stu-id="47e9d-251">If you plan to use a policy version other than the latest deployed version, you should use an **Expression** shape, and invoke the rule engine programmatically to execute the policy of that specific version.</span></span> <span data-ttu-id="47e9d-252">Pour plus d’informations, consultez [comment exécuter les stratégies](../core/how-to-execute-policies.md).</span><span class="sxs-lookup"><span data-stu-id="47e9d-252">For more information, see [How to Execute Policies](../core/how-to-execute-policies.md).</span></span>  
  
-   <span data-ttu-id="47e9d-253">Le **appeler règles** forme reconstruit le message, comme si vous utilisez un **construire un Message** forme, ce qui peut entraîner des propriétés de contexte du message soit perdu.</span><span class="sxs-lookup"><span data-stu-id="47e9d-253">The **Call Rules** shape reconstructs the message, as if using a **Construct Message** shape, which in turn may cause context properties of the message to be lost.</span></span>  
  
-   <span data-ttu-id="47e9d-254">Une stratégie ne peut plus être modifiée une fois publiée.</span><span class="sxs-lookup"><span data-stu-id="47e9d-254">A policy cannot be modified after it is published.</span></span>  
  
-   <span data-ttu-id="47e9d-255">Les applications clientes ne peuvent accéder qu'aux stratégies déployées.</span><span class="sxs-lookup"><span data-stu-id="47e9d-255">The client applications can access only the deployed policies.</span></span> <span data-ttu-id="47e9d-256">Si une application cliente appelle une stratégie qui n’est pas déployée, le moteur de règles génère une **RuleEngineDeploymentNotDeployedException** exception.</span><span class="sxs-lookup"><span data-stu-id="47e9d-256">If a client application invokes a policy that is not deployed, the rule engine generates a **RuleEngineDeploymentNotDeployedException** exception.</span></span> <span data-ttu-id="47e9d-257">Le message d'erreur détaillé s'affiche dans le journal des événements de l'application.</span><span class="sxs-lookup"><span data-stu-id="47e9d-257">You can see the detailed error message in the application event log.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="47e9d-258">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="47e9d-258">Next Steps</span></span>  
 <span data-ttu-id="47e9d-259">Maintenant que vous avez terminé cette procédure pas à pas, effectuez la [procédure pas à pas : création et utilisation d’un vocabulaire dans la stratégie](../core/walkthrough-creating-and-using-a-vocabulary-in-the-policy.md) procédure pas à pas, ce qui vous donne des instructions détaillées pour créer un vocabulaire et à son utilisation dans les **ProcessPurchaseOrder** stratégie.</span><span class="sxs-lookup"><span data-stu-id="47e9d-259">Now that you have completed this walkthrough, perform the [Walkthrough: Creating and Using a Vocabulary in the Policy](../core/walkthrough-creating-and-using-a-vocabulary-in-the-policy.md) walkthrough, which gives you step-by-step instructions for creating a vocabulary and using the vocabulary in the **ProcessPurchaseOrder** policy.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47e9d-260">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="47e9d-260">See Also</span></span>  
 <span data-ttu-id="47e9d-261">[Évaluation de la condition et exécution d’Action](../core/condition-evaluation-and-action-execution.md) </span><span class="sxs-lookup"><span data-stu-id="47e9d-261">[Condition Evaluation and Action Execution](../core/condition-evaluation-and-action-execution.md) </span></span>  
 <span data-ttu-id="47e9d-262">[Agenda et priorité](../core/agenda-and-priority.md) </span><span class="sxs-lookup"><span data-stu-id="47e9d-262">[Agenda and Priority](../core/agenda-and-priority.md) </span></span>  
 [<span data-ttu-id="47e9d-263">Appel des règles d’entreprise dans les Orchestrations</span><span class="sxs-lookup"><span data-stu-id="47e9d-263">Invoking Business Rules in Orchestrations</span></span>](../core/invoking-business-rules-in-orchestrations.md)