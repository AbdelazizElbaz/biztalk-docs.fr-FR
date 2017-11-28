---
title: "Procédure pas à pas : Module 3 - l’accès à des propriétés SharePoint à partir d’une Orchestration | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- orchestrations, Windows SharePoint Services adapters
- tutorials, Windows SharePoint Services adapters
- Windows SharePoint Services adapters, orchestrations
- Windows SharePoint Services adapter tutorials, accessing SharePoint properties
ms.assetid: 310c4002-3416-44c6-b409-1d5467063e28
caps.latest.revision: "45"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a44fd7e30bf511ee77cc1f3e79f6ba63908259ff
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="walkthrough-module-3---accessing-sharepoint-properties-from-an-orchestration"></a><span data-ttu-id="816a9-102">Procédure pas à pas : Module 3 - l’accès à des propriétés SharePoint à partir d’une Orchestration</span><span class="sxs-lookup"><span data-stu-id="816a9-102">Walkthrough: Module 3 - Accessing SharePoint Properties from an Orchestration</span></span>
<span data-ttu-id="816a9-103">Cette procédure pas à pas est la suite de [procédure pas à pas : Module 2 - intégration d’Office avec l’adaptateur Windows SharePoint Services](../core/walkthrough-module-2--integrate-office-with-the-sharepoint-adapter-in-biztalk.md) et vous montre comment accéder aux propriétés de contexte Windows SharePoint Services d’un message entrant à durée d’exécution, puis déterminer la destination de ce message basée sur une propriété à l’aide des ports dynamiques dans une orchestration.</span><span class="sxs-lookup"><span data-stu-id="816a9-103">This walkthrough is a continuation of [Walkthrough: Module 2 - Integrating Office with the Windows SharePoint Services Adapter](../core/walkthrough-module-2--integrate-office-with-the-sharepoint-adapter-in-biztalk.md) and shows you how to access the Windows SharePoint Services context properties of an incoming message at run time and then determine the destination of that message based on a property using dynamic ports in an orchestration.</span></span> <span data-ttu-id="816a9-104">Pour une présentation de l’adaptateur Windows SharePoint Services, consultez [quel est l’adaptateur Windows SharePoint Services ?](../core/what-is-the-windows-sharepoint-services-adapter.md).</span><span class="sxs-lookup"><span data-stu-id="816a9-104">For an introduction to the Windows SharePoint Services adapter see [What Is the Windows SharePoint Services Adapter?](../core/what-is-the-windows-sharepoint-services-adapter.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="816a9-105">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="816a9-105">Prerequisites</span></span>  
 <span data-ttu-id="816a9-106">La configuration suivante est requise pour exécuter les procédures décrites dans cette rubrique :</span><span class="sxs-lookup"><span data-stu-id="816a9-106">The following are prerequisites for performing the procedures in this topic:</span></span>  
  
-   <span data-ttu-id="816a9-107">Vous devez disposer d'un déploiement de serveur unique avec une installation complète de [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] s'exécutant sous [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] ou [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="816a9-107">You must have a single server deployment with a complete installation of [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] running on [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] or [!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)].</span></span>  
  
-   <span data-ttu-id="816a9-108">Vous devez effectuer les procédures suivantes : [procédure pas à pas : Module 1 - envoi et réception de Messages avec l’adaptateur Windows SharePoint Services](../core/walkthrough-module-1--send-and-receive-messages-with-the-sharepoint-adapter.md) et [procédure pas à pas : Module 2 - intégration d’Office avec Windows Adaptateur SharePoint Services](../core/walkthrough-module-2--integrate-office-with-the-sharepoint-adapter-in-biztalk.md)</span><span class="sxs-lookup"><span data-stu-id="816a9-108">You must complete the following walkthroughs: [Walkthrough: Module 1 - Sending and Receiving Messages with the Windows SharePoint Services Adapter](../core/walkthrough-module-1--send-and-receive-messages-with-the-sharepoint-adapter.md) and [Walkthrough: Module 2 - Integrating Office with the Windows SharePoint Services Adapter](../core/walkthrough-module-2--integrate-office-with-the-sharepoint-adapter-in-biztalk.md)</span></span>  
  
 <span data-ttu-id="816a9-109">Pour plus d’informations sur l’utilisation de l’adaptateur Windows SharePoint Services dans un déploiement de serveurs multiples, consultez [configuration et déploiement de l’adaptateur Windows SharePoint Services](../core/setting-up-and-deploying-the-windows-sharepoint-services-adapter.md).</span><span class="sxs-lookup"><span data-stu-id="816a9-109">For information about using the Windows SharePoint Services Adapter in a multi server deployment, see [Setting Up and Deploying the Windows SharePoint Services Adapter](../core/setting-up-and-deploying-the-windows-sharepoint-services-adapter.md).</span></span>  
  
## <a name="modify-the-biztalk-project"></a><span data-ttu-id="816a9-110">Modification du projet BizTalk</span><span class="sxs-lookup"><span data-stu-id="816a9-110">Modify the BizTalk project</span></span>  
 <span data-ttu-id="816a9-111">Cette procédure vous permet de modifier le schéma PurchaseOrder de [procédure pas à pas : Module 2 - intégration d’Office avec l’adaptateur Windows SharePoint Services](../core/walkthrough-module-2--integrate-office-with-the-sharepoint-adapter-in-biztalk.md).</span><span class="sxs-lookup"><span data-stu-id="816a9-111">In this procedure you modify the PurchaseOrder schema from [Walkthrough: Module 2 - Integrating Office with the Windows SharePoint Services Adapter](../core/walkthrough-module-2--integrate-office-with-the-sharepoint-adapter-in-biztalk.md).</span></span> <span data-ttu-id="816a9-112">Cette procédure montre comment promouvoir une propriété de schéma pour un accès facile dans une orchestration BizTalk.</span><span class="sxs-lookup"><span data-stu-id="816a9-112">This procedure illustrates how to promote a schema property for easy access in a BizTalk orchestration.</span></span>  
  
#### <a name="modify-the-purchaseorderxsd-schema"></a><span data-ttu-id="816a9-113">Modification du schéma PurchaseOrder.xsd</span><span class="sxs-lookup"><span data-stu-id="816a9-113">Modify the PurchaseOrder.xsd schema</span></span>  
  
1.  <span data-ttu-id="816a9-114">Démarrer **Microsoft Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="816a9-114">Start **Microsoft Visual Studio**.</span></span>  
  
2.  <span data-ttu-id="816a9-115">Cliquez sur **fichier**, cliquez sur **ouvrir**, puis cliquez sur **projet/Solution**.</span><span class="sxs-lookup"><span data-stu-id="816a9-115">Click **File**, click **Open**, and then click **Project/Solution**.</span></span>  
  
3.  <span data-ttu-id="816a9-116">Accédez à la `OrderProcess.sln` de fichiers, puis cliquez sur **ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="816a9-116">Browse to the `OrderProcess.sln` file, and then click **Open**.</span></span>  
  
4.  <span data-ttu-id="816a9-117">Dans **l’Explorateur de solutions**, avec le bouton droit le `OrderProcessSchema.xsd` de fichiers, puis cliquez sur **ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="816a9-117">In **Solution Explorer**, right-click the `OrderProcessSchema.xsd` file, and then click **Open**.</span></span>  
  
5.  <span data-ttu-id="816a9-118">Dans **l’Éditeur BizTalk**, développez `PurchaseOrder`.</span><span class="sxs-lookup"><span data-stu-id="816a9-118">In **BizTalk Editor**, expand `PurchaseOrder`.</span></span>  
  
6.  <span data-ttu-id="816a9-119">Avec le bouton droit `Amount`, cliquez sur **promouvoir**, puis cliquez sur **Promotion rapide**.</span><span class="sxs-lookup"><span data-stu-id="816a9-119">Right-click `Amount`, click **Promote**, and then click **Quick Promotion**.</span></span>  
  
7.  <span data-ttu-id="816a9-120">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="816a9-120">Click **OK**.</span></span>  
  
    > [!NOTE]
    >  [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]<span data-ttu-id="816a9-121"> crée un schéma de propriété ad hoc dans le projet en cours.</span><span class="sxs-lookup"><span data-stu-id="816a9-121"> creates a property schema for this in the current project.</span></span>  
  
8.  <span data-ttu-id="816a9-122">Enregistrez `PurchaseOrder.xsd`.</span><span class="sxs-lookup"><span data-stu-id="816a9-122">Save `PurchaseOrder.xsd`.</span></span>  
  
## <a name="create-an-orchestration"></a><span data-ttu-id="816a9-123">Création d'une orchestration</span><span class="sxs-lookup"><span data-stu-id="816a9-123">Create an orchestration</span></span>  
 <span data-ttu-id="816a9-124">Cette procédure permet de créer une orchestration BizTalk.</span><span class="sxs-lookup"><span data-stu-id="816a9-124">In this procedure you create a new BizTalk orchestration.</span></span> <span data-ttu-id="816a9-125">Cette procédure crée l'orchestration utilisée pour traiter un message reçu par l'adaptateur Windows Sharepoint Services.</span><span class="sxs-lookup"><span data-stu-id="816a9-125">This procedure creates the orchestration that is used to process a message received by the Windows Sharepoint Services adapter.</span></span>  
  
#### <a name="add-a-biztalk-orchestration"></a><span data-ttu-id="816a9-126">Ajout d'une orchestration BizTalk</span><span class="sxs-lookup"><span data-stu-id="816a9-126">Add a BizTalk orchestration</span></span>  
  
1.  <span data-ttu-id="816a9-127">Dans **l’Explorateur de solutions**, avec le bouton droit le `OrderProcess` de projet, cliquez sur **ajouter**, puis cliquez sur **un nouvel élément**.</span><span class="sxs-lookup"><span data-stu-id="816a9-127">In **Solution Explorer**, right-click the `OrderProcess` project, click **Add**, and then click **New Item**.</span></span>  
  
2.  <span data-ttu-id="816a9-128">Sous **catégories**, sélectionnez **fichiers d’Orchestration**.</span><span class="sxs-lookup"><span data-stu-id="816a9-128">Under **Categories**, select **Orchestration Files**.</span></span>  
  
3.  <span data-ttu-id="816a9-129">Sous **modèles**, sélectionnez **Orchestration BizTalk**.</span><span class="sxs-lookup"><span data-stu-id="816a9-129">Under **Templates**, select **BizTalk Orchestration**.</span></span>  
  
4.  <span data-ttu-id="816a9-130">Type `MyCompanyOrderProcessing` dans les **nom** champ, puis cliquez sur **ajouter**.</span><span class="sxs-lookup"><span data-stu-id="816a9-130">Type `MyCompanyOrderProcessing` in the **Name** field, and then click **Add**.</span></span>  
  
## <a name="create-receive-information"></a><span data-ttu-id="816a9-131">Création d'informations de réception</span><span class="sxs-lookup"><span data-stu-id="816a9-131">Create receive information</span></span>  
 <span data-ttu-id="816a9-132">Cette procédure permet de créer un message, un port de réception et une forme Réception pour l'orchestration.</span><span class="sxs-lookup"><span data-stu-id="816a9-132">In this procedure you create a new message, receive port, and receive shape for the orchestration.</span></span> <span data-ttu-id="816a9-133">Elle montre comment configurer une orchestration pour recevoir un message de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="816a9-133">This procedure illustrates how to configure an orchestration to receive a message from [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
#### <a name="create-a-new-message"></a><span data-ttu-id="816a9-134">Création d'un message</span><span class="sxs-lookup"><span data-stu-id="816a9-134">Create a new message</span></span>  
  
1.  <span data-ttu-id="816a9-135">Dans **Vue Orchestration**, avec le bouton droit **Messages**, puis cliquez sur **nouveau Message**.</span><span class="sxs-lookup"><span data-stu-id="816a9-135">In **Orchestration View**, right-click **Messages**, and then click **New Message**.</span></span> <span data-ttu-id="816a9-136">Cette action génère un nouveau message nommé `Message_1`.</span><span class="sxs-lookup"><span data-stu-id="816a9-136">This will generate a new message with the name `Message_1`.</span></span>  
  
2.  <span data-ttu-id="816a9-137">Avec le bouton droit `Message_1`, cliquez sur **renommer**, puis tapez `Message_PO`.</span><span class="sxs-lookup"><span data-stu-id="816a9-137">Right-click `Message_1`, click **Rename**, and then type `Message_PO`.</span></span>  
  
3.  <span data-ttu-id="816a9-138">Avec le bouton droit `Message_PO`, puis cliquez sur **fenêtre Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="816a9-138">Right-click `Message_PO`, and then click **Properties Window**.</span></span>  
  
4.  <span data-ttu-id="816a9-139">Dans le **Type de Message** propriétés, développez **schémas**, puis sélectionnez `OrderProcess.OrderProcessSchema` schéma.</span><span class="sxs-lookup"><span data-stu-id="816a9-139">In the **Message Type** property, expand **Schemas**, and then select `OrderProcess.OrderProcessSchema` schema.</span></span>  
  
#### <a name="add-a-receive-port-to-the-orchestration"></a><span data-ttu-id="816a9-140">Ajout d'un port de réception à l'orchestration</span><span class="sxs-lookup"><span data-stu-id="816a9-140">Add a receive port to the orchestration</span></span>  
  
1.  <span data-ttu-id="816a9-141">Sous **Orchestrations BizTalk** dans la boîte à outils, faites glisser un **Port** forme sur la Surface du Port.</span><span class="sxs-lookup"><span data-stu-id="816a9-141">Under **BizTalk Orchestrations** in the Toolbox, drag a **Port** shape to the Port Surface.</span></span> <span data-ttu-id="816a9-142">L'Assistant Configuration du port démarre.</span><span class="sxs-lookup"><span data-stu-id="816a9-142">The Port Configuration Wizard will start.</span></span>  
  
2.  <span data-ttu-id="816a9-143">Dans l’écran d’accueil, cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="816a9-143">On the Welcome screen, click **Next**.</span></span>  
  
3.  <span data-ttu-id="816a9-144">Type `ReceivePurchaseOrder` dans les **nom** champ, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="816a9-144">Type `ReceivePurchaseOrder` in the **Name** field, and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="816a9-145">Sélectionnez **créer un nouveau Type de Port**.</span><span class="sxs-lookup"><span data-stu-id="816a9-145">Select **Create a new Port Type**.</span></span>  
  
5.  <span data-ttu-id="816a9-146">Type `PurchaseOrderPT` dans les **nom du Type de Port** champ, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="816a9-146">Type `PurchaseOrderPT` in the **Port Type Name** field, and then click **Next**.</span></span>  
  
6.  <span data-ttu-id="816a9-147">Sur le **écran de liaison de Port**, conservez les valeurs par défaut, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="816a9-147">On the **Port Binding screen**, leave the default values, and then click **Next**.</span></span>  
  
7.  <span data-ttu-id="816a9-148">Cliquez sur **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="816a9-148">Click **Finish**.</span></span>  
  
8.  <span data-ttu-id="816a9-149">Dans **Vue Orchestration**, sous **Types de ports**, développez le `PurchaseOrderPT` type de port.</span><span class="sxs-lookup"><span data-stu-id="816a9-149">In **Orchestration View**, under **Port Types**, expand the `PurchaseOrderPT` port type.</span></span>  
  
9. <span data-ttu-id="816a9-150">Avec le bouton droit `Operation_1`, cliquez sur **renommer**, puis tapez `PurchaseOrderOperation`.</span><span class="sxs-lookup"><span data-stu-id="816a9-150">Right-click `Operation_1`, click **Rename**, and then type `PurchaseOrderOperation`.</span></span>  
  
#### <a name="add-a-receive-shape-to-the-orchestration"></a><span data-ttu-id="816a9-151">Ajout d'une forme Réception à l'orchestration</span><span class="sxs-lookup"><span data-stu-id="816a9-151">Add a Receive shape to the orchestration</span></span>  
  
1.  <span data-ttu-id="816a9-152">Sous **Orchestrations BizTalk** dans la boîte à outils, faites glisser un **réception** forme à l’Orchestration.</span><span class="sxs-lookup"><span data-stu-id="816a9-152">Under **BizTalk Orchestrations** in the Toolbox, drag a **Receive** shape to the Orchestration.</span></span>  
  
2.  <span data-ttu-id="816a9-153">Avec le bouton droit de la forme réception, puis cliquez sur **fenêtre Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="816a9-153">Right-click the Receive shape, and then click **Properties Window**.</span></span>  
  
3.  <span data-ttu-id="816a9-154">Définir le **activer** propriété `True`.</span><span class="sxs-lookup"><span data-stu-id="816a9-154">Set the **Activate** property to `True`.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="816a9-155">Si la propriété Activer est définie sur false, vous obtenez l'erreur suivante : « erreur X2214 : vous devez indiquer au moins un ensemble de corrélations déjà initialisé pour une réception sans activation située sur un port autre qu'un port d'autocorrélation ».</span><span class="sxs-lookup"><span data-stu-id="816a9-155">If the activate property is set to false, you will get the following error: "error X2214: you must specify at least one already-initialized correlation set for a non-activation receive that is on a non-selfcorrelating port"</span></span>  
  
4.  <span data-ttu-id="816a9-156">Type `Receive_PO` dans les **nom** champ.</span><span class="sxs-lookup"><span data-stu-id="816a9-156">Type `Receive_PO` in the **Name** field.</span></span>  
  
5.  <span data-ttu-id="816a9-157">Dans le **fenêtre Propriétés**, sélectionnez `Message_PO` pour la propriété de Message.</span><span class="sxs-lookup"><span data-stu-id="816a9-157">In the **Properties Window**, select `Message_PO` for the Message property.</span></span>  
  
6.  <span data-ttu-id="816a9-158">Sélectionnez `ReceivePurchaseOrder.PurchaseOrderOperation.Request` pour le **opération** propriété.</span><span class="sxs-lookup"><span data-stu-id="816a9-158">Select `ReceivePurchaseOrder.PurchaseOrderOperation.Request` for the **Operation** property.</span></span> <span data-ttu-id="816a9-159">Cela lie le port à la forme Réception dans le Concepteur d'orchestration.</span><span class="sxs-lookup"><span data-stu-id="816a9-159">This will tie the port to the Receive shape in the Orchestration Designer.</span></span>  
  
## <a name="create-send-information"></a><span data-ttu-id="816a9-160">Création d'informations d'envoi</span><span class="sxs-lookup"><span data-stu-id="816a9-160">Create send information</span></span>  
 <span data-ttu-id="816a9-161">Cette procédure permet de créer un message, des ports d'envoi et une structure de décision pour l'orchestration.</span><span class="sxs-lookup"><span data-stu-id="816a9-161">In this procedure you create a new message, send ports, and decision structure to the orchestration.</span></span> <span data-ttu-id="816a9-162">Cette procédure montre comment configurer une orchestration avec une logique de décision et comment configurer une orchestration pour envoyer un message à un port d'envoi.</span><span class="sxs-lookup"><span data-stu-id="816a9-162">This procedure illustrates how to configure an orchestration with decision logic and how to configure an orchestration to send a message to a send port.</span></span>  
  
#### <a name="create-a-new-message"></a><span data-ttu-id="816a9-163">Création d'un message</span><span class="sxs-lookup"><span data-stu-id="816a9-163">Create a new message</span></span>  
  
1.  <span data-ttu-id="816a9-164">Dans **Vue Orchestration**, avec le bouton droit **Messages**, puis cliquez sur **nouveau Message**.</span><span class="sxs-lookup"><span data-stu-id="816a9-164">In **Orchestration View**, right-click **Messages**, and then click **New Message**.</span></span> <span data-ttu-id="816a9-165">Cette action génère un nouveau message nommé `Message_1`.</span><span class="sxs-lookup"><span data-stu-id="816a9-165">This will generate a new message with the name `Message_1`.</span></span>  
  
2.  <span data-ttu-id="816a9-166">Avec le bouton droit `Message_1`, cliquez sur **renommer**, puis tapez `Message_Task`.</span><span class="sxs-lookup"><span data-stu-id="816a9-166">Right-click `Message_1`, click **Rename**, and then type `Message_Task`.</span></span>  
  
3.  <span data-ttu-id="816a9-167">Avec le bouton droit `Message_Task`, puis cliquez sur **fenêtre Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="816a9-167">Right-click `Message_Task`, and then click **Properties Window**.</span></span>  
  
4.  <span data-ttu-id="816a9-168">Dans le **Type de Message** propriétés, développez **schémas**, puis sélectionnez `OrderProcess.OrderProcessSchema` schéma.</span><span class="sxs-lookup"><span data-stu-id="816a9-168">In the **Message Type** property, expand **Schemas**, and then select `OrderProcess.OrderProcessSchema` schema.</span></span>  
  
#### <a name="add-a-send-port-to-the-orchestration"></a><span data-ttu-id="816a9-169">Ajout d'un port d'envoi à l'orchestration</span><span class="sxs-lookup"><span data-stu-id="816a9-169">Add a send port to the orchestration</span></span>  
  
1.  <span data-ttu-id="816a9-170">Sous **Orchestrations BizTalk** dans la boîte à outils, faites glisser un **Port** forme sur la Surface du Port.</span><span class="sxs-lookup"><span data-stu-id="816a9-170">Under **BizTalk Orchestrations** in the Toolbox, drag a **Port** shape to the Port Surface.</span></span> <span data-ttu-id="816a9-171">L'Assistant Configuration du port démarre.</span><span class="sxs-lookup"><span data-stu-id="816a9-171">The Port Configuration Wizard will start.</span></span>  
  
2.  <span data-ttu-id="816a9-172">Dans l’écran d’accueil, cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="816a9-172">On the Welcome screen, click **Next**.</span></span>  
  
3.  <span data-ttu-id="816a9-173">Type `SendPurchaseOrder` dans les **nom** champ, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="816a9-173">Type `SendPurchaseOrder` in the **Name** field, and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="816a9-174">Sélectionnez **utiliser un Type de Port existant**.</span><span class="sxs-lookup"><span data-stu-id="816a9-174">Select **Use an existing Port Type**.</span></span>  
  
5.  <span data-ttu-id="816a9-175">Sous **Types de ports disponibles**, sélectionnez `OrderProcess.PurchaseOrderPT`, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="816a9-175">Under **Available Port Types**, select `OrderProcess.PurchaseOrderPT`, and then click **Next**.</span></span>  
  
6.  <span data-ttu-id="816a9-176">Sur le **écran de liaison de Port**, sous **direction de communication du Port**, sélectionnez `I'll always be sending messages on this port`, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="816a9-176">On the **Port Binding screen**, under **Port direction of communication**, select `I'll always be sending messages on this port`, and then click **Next**.</span></span>  
  
7.  <span data-ttu-id="816a9-177">Cliquez sur **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="816a9-177">Click **Finish**.</span></span>  
  
#### <a name="add-a-send-shape-to-the-orchestration"></a><span data-ttu-id="816a9-178">Ajout d'une forme Envoi à l'orchestration</span><span class="sxs-lookup"><span data-stu-id="816a9-178">Add a Send shape to the orchestration</span></span>  
  
1.  <span data-ttu-id="816a9-179">Sous **Orchestrations BizTalk** dans la boîte à outils, faites glisser un **envoyer** forme pour le Concepteur d’Orchestration.</span><span class="sxs-lookup"><span data-stu-id="816a9-179">Under **BizTalk Orchestrations** in the Toolbox, drag a **Send** shape to the Orchestration Designer.</span></span> <span data-ttu-id="816a9-180">Placez-la sous la forme Réception `Receive_PO`.</span><span class="sxs-lookup"><span data-stu-id="816a9-180">Place it below the `Receive_PO` Receive shape.</span></span>  
  
2.  <span data-ttu-id="816a9-181">Avec le bouton droit de la forme envoi, puis cliquez sur **fenêtre Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="816a9-181">Right-click the Send shape, and then click **Properties Window**.</span></span>  
  
3.  <span data-ttu-id="816a9-182">Type `Send_PO` dans les **nom** champ.</span><span class="sxs-lookup"><span data-stu-id="816a9-182">Type `Send_PO` in the **Name** field.</span></span>  
  
4.  <span data-ttu-id="816a9-183">Sélectionnez `Message_PO` pour le **Message** propriété.</span><span class="sxs-lookup"><span data-stu-id="816a9-183">Select `Message_PO` for the **Message** property.</span></span>  
  
5.  <span data-ttu-id="816a9-184">Sélectionnez `SendPurchaseOrder.PurchaseOrderOperation.Request` pour le **opération** propriété.</span><span class="sxs-lookup"><span data-stu-id="816a9-184">Select `SendPurchaseOrder.PurchaseOrderOperation.Request` for the **Operation** property.</span></span> <span data-ttu-id="816a9-185">Cela lie le port à la forme Envoi dans le Concepteur d'orchestration.</span><span class="sxs-lookup"><span data-stu-id="816a9-185">This will tie the port to the Send shape in the Orchestration Designer.</span></span>  
  
#### <a name="add-a-decide-shape-to-the-orchestration"></a><span data-ttu-id="816a9-186">Ajout d'une forme Décider à l'orchestration</span><span class="sxs-lookup"><span data-stu-id="816a9-186">Add a Decide shape to the orchestration</span></span>  
  
1.  <span data-ttu-id="816a9-187">Sous **Orchestrations BizTalk** dans la boîte à outils, faites glisser un **décider** forme pour le Concepteur d’Orchestration.</span><span class="sxs-lookup"><span data-stu-id="816a9-187">Under **BizTalk Orchestrations** in the Toolbox, drag a **Decide** shape to the Orchestration Designer.</span></span> <span data-ttu-id="816a9-188">Placez-la sous la forme Envoi `Send_PO`.</span><span class="sxs-lookup"><span data-stu-id="816a9-188">Place it below the `Send_PO` Send shape.</span></span>  
  
2.  <span data-ttu-id="816a9-189">Avec le bouton droit de la forme décider, puis cliquez sur **fenêtre Propriétés.**</span><span class="sxs-lookup"><span data-stu-id="816a9-189">Right-click the Decide shape, and then click **Properties Window.**</span></span>  
  
3.  <span data-ttu-id="816a9-190">Type `NeedsApproval` dans les **nom** champ.</span><span class="sxs-lookup"><span data-stu-id="816a9-190">Type `NeedsApproval` in the **Name** field.</span></span>  
  
4.  <span data-ttu-id="816a9-191">Dans le Concepteur d’Orchestration, cliquez sur **Rule_1** sur la forme décider.</span><span class="sxs-lookup"><span data-stu-id="816a9-191">In Orchestration Designer, click **Rule_1** on the Decide shape.</span></span>  
  
5.  <span data-ttu-id="816a9-192">Dans la fenêtre Propriétés, tapez `ApprovalRequired` pour le **nom** propriété.</span><span class="sxs-lookup"><span data-stu-id="816a9-192">In the Properties Windows, type `ApprovalRequired` for the **Name** property.</span></span>  
  
6.  <span data-ttu-id="816a9-193">Cliquez sur le **Expression** propriété de champ, puis cliquez sur le bouton de sélection (**...** ) bouton.</span><span class="sxs-lookup"><span data-stu-id="816a9-193">Click the **Expression** property field, and then click the ellipsis (**…**) button.</span></span>  
  
7.  <span data-ttu-id="816a9-194">Dans l'Éditeur d'expression BizTalk, tapez ou copiez ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="816a9-194">In the BizTalk Expression Editor, type or copy the following:</span></span>  
  
    ```  
    Message_PO(OrderProcess.PropertySchema.Amount) > 1000  
    ```  
  
8.  <span data-ttu-id="816a9-195">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="816a9-195">Click **OK**.</span></span>  
  
#### <a name="add-another-send-port-to-the-orchestration"></a><span data-ttu-id="816a9-196">Ajout d'un autre port d'envoi à l'orchestration</span><span class="sxs-lookup"><span data-stu-id="816a9-196">Add another send port to the orchestration</span></span>  
  
1.  <span data-ttu-id="816a9-197">Sous **Orchestrations BizTalk** dans la boîte à outils, faites glisser un **Port** forme sur la Surface du Port.</span><span class="sxs-lookup"><span data-stu-id="816a9-197">Under **BizTalk Orchestrations** in the Toolbox, drag a **Port** shape to the Port Surface.</span></span> <span data-ttu-id="816a9-198">L'Assistant Configuration du port démarre.</span><span class="sxs-lookup"><span data-stu-id="816a9-198">The Port Configuration Wizard will start.</span></span>  
  
2.  <span data-ttu-id="816a9-199">Dans l’écran d’accueil, cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="816a9-199">On the Welcome screen, click **Next**.</span></span>  
  
3.  <span data-ttu-id="816a9-200">Type `SendToTasksList` dans les **nom** champ, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="816a9-200">Type `SendToTasksList` in the **Name** field, and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="816a9-201">Sélectionnez **utiliser un Type de Port existant**.</span><span class="sxs-lookup"><span data-stu-id="816a9-201">Select **Use an existing Port Type**.</span></span>  
  
5.  <span data-ttu-id="816a9-202">Sous **Types de ports disponibles**, sélectionnez `OrderProcess.PurchaseOrderPT`, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="816a9-202">Under **Available Port Types**, select `OrderProcess.PurchaseOrderPT`, and then click **Next**.</span></span>  
  
6.  <span data-ttu-id="816a9-203">Sur le **écran de liaison de Port**, sous **direction de communication du Port**, sélectionnez `I'll always be sending messages on this port`.</span><span class="sxs-lookup"><span data-stu-id="816a9-203">On the **Port Binding screen**, under **Port direction of communication**, select `I'll always be sending messages on this port`.</span></span>  
  
7.  <span data-ttu-id="816a9-204">Sous **liaison de Port**, sélectionnez `Dynamic`, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="816a9-204">Under **Port binding**, select `Dynamic`, and then click **Next**.</span></span>  
  
8.  <span data-ttu-id="816a9-205">Cliquez sur **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="816a9-205">Click **Finish**.</span></span>  
  
#### <a name="add-a-send-shape-to-the-decide-shape"></a><span data-ttu-id="816a9-206">Ajout d'une forme Envoi à la forme Décider</span><span class="sxs-lookup"><span data-stu-id="816a9-206">Add a Send shape to the Decide shape</span></span>  
  
1.  <span data-ttu-id="816a9-207">Sous **Orchestrations BizTalk** dans la boîte à outils, faites glisser un **envoyer** forme pour le Concepteur d’Orchestration.</span><span class="sxs-lookup"><span data-stu-id="816a9-207">Under **BizTalk Orchestrations** in the Toolbox, drag a **Send** shape to the Orchestration Designer.</span></span> <span data-ttu-id="816a9-208">Placez-la sous la forme `ApprovalRequired`.</span><span class="sxs-lookup"><span data-stu-id="816a9-208">Place it below the `ApprovalRequired` shape.</span></span>  
  
2.  <span data-ttu-id="816a9-209">Avec le bouton droit de la forme envoi, puis cliquez sur **fenêtre Propriétés**</span><span class="sxs-lookup"><span data-stu-id="816a9-209">Right-click the Send shape, and then click **Properties Window**</span></span>  
  
3.  <span data-ttu-id="816a9-210">Type `CreateApprovalTask` dans les **nom** champ.</span><span class="sxs-lookup"><span data-stu-id="816a9-210">Type `CreateApprovalTask` in the **Name** field.</span></span>  
  
4.  <span data-ttu-id="816a9-211">Sélectionnez `Message_Task` pour le **Message** propriété.</span><span class="sxs-lookup"><span data-stu-id="816a9-211">Select `Message_Task` for the **Message** property.</span></span>  
  
5.  <span data-ttu-id="816a9-212">Sélectionnez `SendToTasksList.PurchaseOrderOperation.Request` pour le **opération** propriété.</span><span class="sxs-lookup"><span data-stu-id="816a9-212">Select `SendToTasksList.PurchaseOrderOperation.Request` for the **Operation** property.</span></span> <span data-ttu-id="816a9-213">Cela lie le port à la forme Envoi dans le Concepteur d'orchestration.</span><span class="sxs-lookup"><span data-stu-id="816a9-213">This will tie the port to the Send shape in the Orchestration Designer.</span></span>  
  
## <a name="create-an-expression"></a><span data-ttu-id="816a9-214">Créer une expression</span><span class="sxs-lookup"><span data-stu-id="816a9-214">Create an expression</span></span>  
 <span data-ttu-id="816a9-215">Dans cette procédure, vous allez ajouter une forme Expression à votre solution, qui attribue la valeur du chemin des tâches à une variable.</span><span class="sxs-lookup"><span data-stu-id="816a9-215">In this procedure you add an Expression shape to your solution which assigns the Tasks path value to a variable.</span></span> <span data-ttu-id="816a9-216">Cette procédure montre comment ajouter une logique à une orchestration pour modifier les propriétés d'un port d'envoi dynamique.</span><span class="sxs-lookup"><span data-stu-id="816a9-216">This procedure illustrates how to add logic to an orchestration to modify the properties of a dynamic send port.</span></span>  
  
#### <a name="create-a-new-expression"></a><span data-ttu-id="816a9-217">Création d'une expression</span><span class="sxs-lookup"><span data-stu-id="816a9-217">Create a new expression</span></span>  
  
1.  <span data-ttu-id="816a9-218">Sous **Orchestrations BizTalk** dans la boîte à outils, faites glisser un **Expression** avant de mettre en forme le `CreateApprovalTask` forme envoi.</span><span class="sxs-lookup"><span data-stu-id="816a9-218">Under **BizTalk Orchestrations** in the Toolbox, drag an **Expression** shape before the `CreateApprovalTask` Send shape.</span></span>  
  
2.  <span data-ttu-id="816a9-219">Avec le bouton droit de la forme Expression, puis cliquez sur **fenêtre Propriétés.**</span><span class="sxs-lookup"><span data-stu-id="816a9-219">Right-click the Expression shape, and then click **Properties Window.**</span></span>  
  
3.  <span data-ttu-id="816a9-220">Type `SetPortDestination` dans les **nom** champ.</span><span class="sxs-lookup"><span data-stu-id="816a9-220">Type `SetPortDestination` in the **Name** field.</span></span>  
  
4.  <span data-ttu-id="816a9-221">Cliquez sur le **Expression** propriété de champ, puis cliquez sur le bouton de sélection (**...** ) bouton.</span><span class="sxs-lookup"><span data-stu-id="816a9-221">Click the **Expression** property field, and then click the ellipsis (**…**) button.</span></span>  
  
5.  <span data-ttu-id="816a9-222">Dans le **Éditeur d’Expression BizTalk**, tapez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="816a9-222">In the **BizTalk Expression Editor**, type the following:</span></span>  
  
    ```  
    SendToTasksList(Microsoft.XLANGs.BaseTypes.Address) = "wss://localhost/sites/WSSAdapterWalkthrough/Lists/Tasks/";  
    ```  
  
6.  <span data-ttu-id="816a9-223">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="816a9-223">Click **OK**.</span></span>  
  
## <a name="construct-a-new-message"></a><span data-ttu-id="816a9-224">Construction d'un nouveau message</span><span class="sxs-lookup"><span data-stu-id="816a9-224">Construct a new message</span></span>  
 <span data-ttu-id="816a9-225">Dans cette procédure, vous allez ajouter une forme Construire à la solution, qui construira une nouvelle instance d'un type de message à l'intérieur de l'orchestration.</span><span class="sxs-lookup"><span data-stu-id="816a9-225">In this procedure you add a Construct shape to the solution which will construct a new instance of a message type within the orchestration.</span></span> <span data-ttu-id="816a9-226">Cette procédure montre comment créer un message qui est une copie du message entrant, puis modifier les propriétés de contexte du nouveau message.</span><span class="sxs-lookup"><span data-stu-id="816a9-226">This procedure illustrates how to create a new message that is a copy of the inbound message and then modify the context properties of the new message.</span></span> <span data-ttu-id="816a9-227">Cette étape est obligatoire parce que les messages sont immuables dans BizTalk. Une fois que vous avez construit un message original, vous ne pouvez plus le modifier.</span><span class="sxs-lookup"><span data-stu-id="816a9-227">This step is required because messages are immutable in BizTalk; that is, once you have constructed it, you cannot modify the original.</span></span>  
  
#### <a name="add-a-construct-shape"></a><span data-ttu-id="816a9-228">Ajout d'une forme Construction</span><span class="sxs-lookup"><span data-stu-id="816a9-228">Add a Construct Shape</span></span>  
  
1.  <span data-ttu-id="816a9-229">Sous **Orchestrations BizTalk** dans la boîte à outils, faites glisser un **construire un Message** avant de mettre en forme le `SetPortDestination` forme Expression.</span><span class="sxs-lookup"><span data-stu-id="816a9-229">Under **BizTalk Orchestrations** in the Toolbox, drag a **Construct Message** shape before the `SetPortDestination` Expression shape.</span></span>  
  
2.  <span data-ttu-id="816a9-230">Avec le bouton droit de la forme construire un Message, puis cliquez sur **fenêtre Propriétés.**</span><span class="sxs-lookup"><span data-stu-id="816a9-230">Right-click the Construct Message shape, and then click **Properties Window.**</span></span>  
  
3.  <span data-ttu-id="816a9-231">Type `ConstructTaskMessage`dans les **nom** champ.</span><span class="sxs-lookup"><span data-stu-id="816a9-231">Type `ConstructTaskMessage`in the **Name** field.</span></span>  
  
4.  <span data-ttu-id="816a9-232">Sélectionnez `Message_Task` pour le **Messages construits** propriété.</span><span class="sxs-lookup"><span data-stu-id="816a9-232">Select `Message_Task` for the **Messages Constructed** property.</span></span>  
  
5.  <span data-ttu-id="816a9-233">Sous **Orchestrations BizTalk** dans la boîte à outils, faites glisser un **assignation du Message** mettre en forme le `ConstructTaskMessage` **construire un Message** forme.</span><span class="sxs-lookup"><span data-stu-id="816a9-233">Under **BizTalk Orchestrations** in the Toolbox, drag a **Message Assignment** shape into the `ConstructTaskMessage`**Construct Message** shape.</span></span>  
  
6.  <span data-ttu-id="816a9-234">Dans le **fenêtre Propriétés**, type `InitTaskMessage` dans les **nom** champ.</span><span class="sxs-lookup"><span data-stu-id="816a9-234">In the **Properties Window**, type `InitTaskMessage` in the **Name** field.</span></span>  
  
7.  <span data-ttu-id="816a9-235">Cliquez sur le **Expression** propriété de champ, puis cliquez sur le bouton de sélection (**...** ) bouton.</span><span class="sxs-lookup"><span data-stu-id="816a9-235">Click the **Expression** property field, and then click the ellipsis (**…**) button.</span></span>  
  
8.  <span data-ttu-id="816a9-236">Dans le **Éditeur d’Expression BizTalk**, tapez ou copiez les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="816a9-236">In the **BizTalk Expression Editor**, type or copy the following:</span></span>  
  
    ```  
    Message_Task = Message_PO;  
    Message_Task(WSS.ConfigOverwrite) = "no";  
    Message_Task(WSS.ConfigNamespaceAliases)= "orchns='http://OrderProcess.PurchaseOrder'";  
    Message_Task(WSS.ConfigPropertiesXml) = "<ConfigPropertiesXml><PropertyName1>Title</PropertyName1><PropertySource1>Approve %XPATH=//orchns:PurchaseOrder/orchns:PurchaseOrderID%</PropertySource1><PropertyName3>Status</PropertyName3><PropertySource3>Not Started</PropertySource3><PropertyName4>Priority</PropertyName4><PropertySource4>(1) High</PropertySource4></ConfigPropertiesXml>";  
    ```  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="816a9-237">Les valeurs fournies pour ces propriétés de contexte respectent la casse.</span><span class="sxs-lookup"><span data-stu-id="816a9-237">These values supplied for these context properties are case sensitive.</span></span> <span data-ttu-id="816a9-238">Lors de la définition de valeurs de configuration pour un port dynamique avec des propriétés de contexte, vous devez veiller à utiliser la casse appropriée, sans quoi une erreur se produit quand BizTalk tente de router le document vers le port d'envoi désigné.</span><span class="sxs-lookup"><span data-stu-id="816a9-238">When setting configuration values for a dynamic port with context properties you must ensure that you use the proper case or an error will occur when BizTalk attempts to route the document to the designated send port.</span></span>  
  
9. <span data-ttu-id="816a9-239">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="816a9-239">Click **OK**.</span></span>  
  
10. <span data-ttu-id="816a9-240">Cliquez sur **fichier**, puis cliquez sur **Enregistrer tout**.</span><span class="sxs-lookup"><span data-stu-id="816a9-240">Click **File**, and then click **Save All**.</span></span>  
  
## <a name="build-the-biztalk-project"></a><span data-ttu-id="816a9-241">Création du projet BizTalk</span><span class="sxs-lookup"><span data-stu-id="816a9-241">Build the BizTalk project</span></span>  
 <span data-ttu-id="816a9-242">Dans cette procédure, vous allez construire et déployer le projet BizTalk.</span><span class="sxs-lookup"><span data-stu-id="816a9-242">In this procedure you build and deploy the BizTalk project.</span></span> <span data-ttu-id="816a9-243">Cette étape est nécessaire pour créer et déployer l'assembly que [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] utilise au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="816a9-243">This step is required to create and deploy the assembly that [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] uses at runtime.</span></span>  
  
#### <a name="build-and-deploy-the-solution"></a><span data-ttu-id="816a9-244">Création et déploiement de la solution</span><span class="sxs-lookup"><span data-stu-id="816a9-244">Build and deploy the solution</span></span>  
  
1.  <span data-ttu-id="816a9-245">Cliquez sur **générer**, puis cliquez sur **OrderProcess de Build**.</span><span class="sxs-lookup"><span data-stu-id="816a9-245">Click **Build**, and then click **Build OrderProcess**.</span></span>  
  
2.  <span data-ttu-id="816a9-246">Cliquez sur **générer**, puis cliquez sur **OrderProcess de déployer**.</span><span class="sxs-lookup"><span data-stu-id="816a9-246">Click **Build**, and then click **Deploy OrderProcess**.</span></span>  
  
3.  <span data-ttu-id="816a9-247">Fermez Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="816a9-247">Close Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span></span>  
  
## <a name="modify-the-receive-location-and-send-port"></a><span data-ttu-id="816a9-248">Modification de l'emplacement de réception et du port d'envoi</span><span class="sxs-lookup"><span data-stu-id="816a9-248">Modify the receive location and send port</span></span>  
 <span data-ttu-id="816a9-249">Dans cette procédure, vous allez modifier l'emplacement de réception et le port d'envoi existants pour utiliser le traitement XML pour les pipelines.</span><span class="sxs-lookup"><span data-stu-id="816a9-249">In this procedure you modify the existing receive location and send port to use XML processing for the pipelines.</span></span> <span data-ttu-id="816a9-250">Le pipeline de réception XML conserve les propriétés de message utilisées durant le traitement de l'orchestration, puis le pipeline d'envoi XML conserve les propriétés de message appliquées dans l'orchestration, qui sont ensuite utilisées pour le routage des messages.</span><span class="sxs-lookup"><span data-stu-id="816a9-250">The receive XML pipeline persists message properties used during orchestration processing and the send XML pipeline persists the message properties that were applied in the orchestration which are subsequently used for message routing.</span></span>  
  
#### <a name="modify-the-receive-location"></a><span data-ttu-id="816a9-251">Modification de l'emplacement de réception</span><span class="sxs-lookup"><span data-stu-id="816a9-251">Modify the receive location</span></span>  
  
1.  <span data-ttu-id="816a9-252">Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)], puis cliquez sur **Administration de BizTalk Server.**</span><span class="sxs-lookup"><span data-stu-id="816a9-252">Click **Start**, point to **All Programs**, point to **Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)], and then click **BizTalk Server Administration.**</span></span>  
  
2.  <span data-ttu-id="816a9-253">Développez **Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] **composant logiciel enfichable Administration**, développez **groupe BizTalk**, développez **Applications**, développez  **BizTalk Application 1**, puis cliquez sur le **emplacements de réception** nœud.</span><span class="sxs-lookup"><span data-stu-id="816a9-253">Expand **Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] **Administration SnapIn**, expand **BizTalk Group**, expand **Applications**, expand **BizTalk Application 1**, and then click the **Receive Locations** node.</span></span>  
  
3.  <span data-ttu-id="816a9-254">Avec le bouton droit `SourceLocation`, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="816a9-254">Right-click `SourceLocation`, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="816a9-255">Dans le **propriétés de l’emplacement de réception** boîte de dialogue **général**, sélectionnez `XMLReceive` pour le **pipeline de réception** propriété.</span><span class="sxs-lookup"><span data-stu-id="816a9-255">In the **Receive Location Properties** dialog box, under **General**, select `XMLReceive` for the **Receive pipeline** property.</span></span>  
  
5.  <span data-ttu-id="816a9-256">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="816a9-256">Click **OK**.</span></span>  
  
#### <a name="modify-the-send-port"></a><span data-ttu-id="816a9-257">Modification du port d'envoi</span><span class="sxs-lookup"><span data-stu-id="816a9-257">Modify the send port</span></span>  
  
1.  <span data-ttu-id="816a9-258">Cliquez sur le **Ports d’envoi** nœud.</span><span class="sxs-lookup"><span data-stu-id="816a9-258">Click the **Send Ports** node.</span></span>  
  
2.  <span data-ttu-id="816a9-259">Avec le bouton droit `SendToDestination`, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="816a9-259">Right-click `SendToDestination`, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="816a9-260">Dans le **propriétés de Port d’envoi** boîte de dialogue **général**, sélectionnez `XMLTransmit` pour le **pipeline d’envoi** propriété.</span><span class="sxs-lookup"><span data-stu-id="816a9-260">In the **Send Port Properties** dialog box, under **General**, select `XMLTransmit` for the **Send pipeline** property.</span></span>  
  
4.  <span data-ttu-id="816a9-261">Sélectionnez le **filtres** onglet.</span><span class="sxs-lookup"><span data-stu-id="816a9-261">Select the **Filters** tab.</span></span>  
  
5.  <span data-ttu-id="816a9-262">Sélectionnez la condition existante, appuyez sur SUPPR, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="816a9-262">Select the existing condition, press DELETE, and then click **OK**.</span></span>  
  
#### <a name="start-a-new-send-port"></a><span data-ttu-id="816a9-263">Démarrage d'un nouveau port d'envoi</span><span class="sxs-lookup"><span data-stu-id="816a9-263">Start a new send port</span></span>  
  
1.  <span data-ttu-id="816a9-264">Cliquez sur le **Ports d’envoi** nœud.</span><span class="sxs-lookup"><span data-stu-id="816a9-264">Click the **Send Ports** node.</span></span>  
  
2.  <span data-ttu-id="816a9-265">Avec le bouton droit `OrderProcess_1.0.0.0_OrderProcess.MyCompanyOrderProcess_SendToTasksList_<GUID>`, puis cliquez sur **Démarrer**.</span><span class="sxs-lookup"><span data-stu-id="816a9-265">Right-click `OrderProcess_1.0.0.0_OrderProcess.MyCompanyOrderProcess_SendToTasksList_<GUID>`, and then click **Start**.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="816a9-266">Vous devrez peut-être actualiser la console si elle n'est pas visible.</span><span class="sxs-lookup"><span data-stu-id="816a9-266">You may have to refresh the console if this is not visible.</span></span>  
  
## <a name="bind-the-orchestration"></a><span data-ttu-id="816a9-267">Liaison de l'orchestration</span><span class="sxs-lookup"><span data-stu-id="816a9-267">Bind the orchestration</span></span>  
 <span data-ttu-id="816a9-268">Dans cette procédure, vous allez lier l'orchestration aux ports spécifiés.</span><span class="sxs-lookup"><span data-stu-id="816a9-268">In this procedure you bind the orchestration to the specified ports.</span></span> <span data-ttu-id="816a9-269">Cette procédure est obligatoire pour lier des ports physiques à l'orchestration que vous avez construite et déployée.</span><span class="sxs-lookup"><span data-stu-id="816a9-269">This procedure is required to tie physical ports to the orchestration that you built and deployed.</span></span>  
  
#### <a name="bind-the-orchestration"></a><span data-ttu-id="816a9-270">Liaison de l'orchestration</span><span class="sxs-lookup"><span data-stu-id="816a9-270">Bind the orchestration</span></span>  
  
1.  <span data-ttu-id="816a9-271">Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] console d’Administration, cliquez sur le **Orchestrations** nœud.</span><span class="sxs-lookup"><span data-stu-id="816a9-271">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, click the **Orchestrations** node.</span></span>  
  
2.  <span data-ttu-id="816a9-272">Cliquez sur le `OrderProcess.MyCompanyOrderProcessing` orchestration, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="816a9-272">Right-click the `OrderProcess.MyCompanyOrderProcessing` orchestration, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="816a9-273">Sélectionnez le **liaisons** onglet.</span><span class="sxs-lookup"><span data-stu-id="816a9-273">Select the **Bindings** tab.</span></span>  
  
4.  <span data-ttu-id="816a9-274">Sous **hôte**, sélectionnez `BizTalkServerApplication` dans les **hôte** champ.</span><span class="sxs-lookup"><span data-stu-id="816a9-274">Under **Host**, select `BizTalkServerApplication` in the **Host** field.</span></span>  
  
5.  <span data-ttu-id="816a9-275">Sous **liaisons**, sélectionnez `FromSource` pour la `ReceivePurchaseOrder` ports logiques entrants.</span><span class="sxs-lookup"><span data-stu-id="816a9-275">Under **Bindings**, select `FromSource` for the `ReceivePurchaseOrder` Inbound Logical Port.</span></span>  
  
6.  <span data-ttu-id="816a9-276">Sous **liaisons**, sélectionnez `SendToDestination` pour la `SendPurchaseOrder` ports logiques sortants.</span><span class="sxs-lookup"><span data-stu-id="816a9-276">Under **Bindings**, select `SendToDestination` for the `SendPurchaseOrder` Outbound Logical Port.</span></span>  
  
7.  <span data-ttu-id="816a9-277">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="816a9-277">Click **OK**.</span></span>  
  
8.  <span data-ttu-id="816a9-278">Bouton droit sur `OrderProcess.MyCompanyOrderProcessing` orchestration, puis cliquez sur **Démarrer**.</span><span class="sxs-lookup"><span data-stu-id="816a9-278">Right click `OrderProcess.MyCompanyOrderProcessing` orchestration, and then click **Start**.</span></span>  
  
## <a name="send-a-message-through-the-system"></a><span data-ttu-id="816a9-279">Envoi d'un message via le système</span><span class="sxs-lookup"><span data-stu-id="816a9-279">Send a message through the system</span></span>  
 <span data-ttu-id="816a9-280">Dans cette procédure, vous allez créer un formulaire InfoPath et le télécharger sur le site Web Windows SharePoint Services.</span><span class="sxs-lookup"><span data-stu-id="816a9-280">In this procedure you create an InfoPath form and upload it to the Windows SharePoint Services Web site.</span></span> <span data-ttu-id="816a9-281">L'adaptateur Windows SharePoint Services prend ce message, l'archive dans la bibliothèque de documents d'archive, puis l'envoie dans la bibliothèque de documents de destination.</span><span class="sxs-lookup"><span data-stu-id="816a9-281">The Windows SharePoint Services adapter will take that message, archive it in the Archive document library, and then send it to the Destination document library.</span></span> <span data-ttu-id="816a9-282">Durant le traitement de ce message, des propriétés de contexte Windows SharePoint Services seront utilisées pour déterminer la destination.</span><span class="sxs-lookup"><span data-stu-id="816a9-282">During the processing of this message, Windows SharePoint Services context properties will be accessed that help determine the destination.</span></span>  
  
#### <a name="create-an-infopath-form-to-send-through-the-system"></a><span data-ttu-id="816a9-283">Création d'un formulaire InfoPath pour envoi via le système</span><span class="sxs-lookup"><span data-stu-id="816a9-283">Create an InfoPath form to send through the system</span></span>  
  
1.  <span data-ttu-id="816a9-284">Ouvrez un navigateur Web, puis accédez à l'URL du site que vous avez créé</span><span class="sxs-lookup"><span data-stu-id="816a9-284">Open a Web browser and navigate to the URL of the site you created.</span></span> <span data-ttu-id="816a9-285">Par exemple, `http://<server_name>/sites/WSSAdapterWalkthrough`.</span><span class="sxs-lookup"><span data-stu-id="816a9-285">For example, `http://<server_name>/sites/WSSAdapterWalkthrough`.</span></span>  
  
2.  <span data-ttu-id="816a9-286">Dans le menu de lancement rapide, cliquez sur `InfoPathSolutions`.</span><span class="sxs-lookup"><span data-stu-id="816a9-286">In the Quick Launch menu, click `InfoPathSolutions`.</span></span>  
  
3.  <span data-ttu-id="816a9-287">Cliquez sur le `PurchaseOrder` fichier pour afficher la **télécharger le fichier** boîte de dialogue, puis cliquez sur **ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="816a9-287">Click the `PurchaseOrder` file to display the **File Download** dialog box, and then click **Open**.</span></span> <span data-ttu-id="816a9-288">InfoPath va charger le formulaire.</span><span class="sxs-lookup"><span data-stu-id="816a9-288">InfoPath will load the form.</span></span>  
  
4.  <span data-ttu-id="816a9-289">Dans le **Purchase Order ID** , tapez `1003`.</span><span class="sxs-lookup"><span data-stu-id="816a9-289">In the **Purchase Order ID** field, type `1003`.</span></span>  
  
5.  <span data-ttu-id="816a9-290">Dans le **facturation** , tapez `John Doe`.</span><span class="sxs-lookup"><span data-stu-id="816a9-290">In the **Bill To** field, type `John Doe`.</span></span>  
  
6.  <span data-ttu-id="816a9-291">Dans le **quantité** , tapez `1750`.</span><span class="sxs-lookup"><span data-stu-id="816a9-291">In the **Amount** field, type `1750`.</span></span>  
  
7.  <span data-ttu-id="816a9-292">Dans le **Purchase Order Date** , tapez `1/3/2005`.</span><span class="sxs-lookup"><span data-stu-id="816a9-292">In the **Purchase Order Date** field, type `1/3/2005`.</span></span>  
  
8.  <span data-ttu-id="816a9-293">Cliquez sur **Enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="816a9-293">Click **Save**.</span></span>  
  
9. <span data-ttu-id="816a9-294">Dans le **enregistrer en tant que** boîte de dialogue, tapez `http://<server_name>/sites/WSSAdapterWalkthrough/Source`dans les **nom de fichier** champ, puis appuyez sur ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="816a9-294">In the **Save As** dialog box, type `http://<server_name>/sites/WSSAdapterWalkthrough/Source`in the **file name** field, and then press ENTER.</span></span>  
  
10. <span data-ttu-id="816a9-295">Type `PurchaseOrder3.xml` dans les **nom de fichier** champ, puis cliquez sur **enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="816a9-295">Type `PurchaseOrder3.xml` in the **file name** field, and then click **Save**.</span></span>  
  
11. <span data-ttu-id="816a9-296">Fermez InfoPath.</span><span class="sxs-lookup"><span data-stu-id="816a9-296">Close InfoPath.</span></span>  
  
12. <span data-ttu-id="816a9-297">Dans le navigateur Web, cliquez sur **Documents et listes**.</span><span class="sxs-lookup"><span data-stu-id="816a9-297">In the Web browser, click **Documents and Lists**.</span></span>  
  
13. <span data-ttu-id="816a9-298">Sous **bibliothèques de documents**, cliquez sur **Destination**.</span><span class="sxs-lookup"><span data-stu-id="816a9-298">Under **Document Libraries**, click **Destination**.</span></span>  
  
14. <span data-ttu-id="816a9-299">Dans la bibliothèque de documents de destination, vous allez voir votre message répertorié dans cette bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="816a9-299">In the Destination document library, you will now see your message listed in this library.</span></span> <span data-ttu-id="816a9-300">Vous y trouverez également une copie archivée dans la bibliothèque de documents d’Archive.</span><span class="sxs-lookup"><span data-stu-id="816a9-300">You will also find a copy archived in the Archive document library.</span></span>  
  
15. <span data-ttu-id="816a9-301">Cliquez sur **Accueil**.</span><span class="sxs-lookup"><span data-stu-id="816a9-301">Click **Home**.</span></span>  
  
16. <span data-ttu-id="816a9-302">Sous **répertorie**, cliquez sur **tâches**.</span><span class="sxs-lookup"><span data-stu-id="816a9-302">Under **Lists**, click **Tasks**.</span></span>  
  
17. <span data-ttu-id="816a9-303">Dans la liste Tâches, vous verrez la tâche d'approbation créée.</span><span class="sxs-lookup"><span data-stu-id="816a9-303">In the Tasks list you will see the newly created approval task.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="816a9-304">Comme le montant du bon de commande était supérieur à 1 000,00 $, la tâche a été créée.</span><span class="sxs-lookup"><span data-stu-id="816a9-304">Since the amount of the purchase order was over $1,000.00, the task was created.</span></span>  
  
## <a name="summary"></a><span data-ttu-id="816a9-305">Résumé</span><span class="sxs-lookup"><span data-stu-id="816a9-305">Summary</span></span>  
 <span data-ttu-id="816a9-306">Cette procédure pas à pas vous a montré comment accéder aux propriétés de contexte Windows SharePoint Services et déterminer la destination des messages transitant par les ports dynamiques.</span><span class="sxs-lookup"><span data-stu-id="816a9-306">In this walkthrough you have seen how to access the Windows SharePoint Services context properties and how to determine the destination of messages going through dynamic ports.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="816a9-307">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="816a9-307">Next Steps</span></span>  
 <span data-ttu-id="816a9-308">Continuez à consulter le reste de la section sur l'adaptateur Windows SharePoint.</span><span class="sxs-lookup"><span data-stu-id="816a9-308">Continue to review the rest of the Windows SharePoint Services adapter section.</span></span> <span data-ttu-id="816a9-309">Pour plus d'informations, consultez les rubriques sous Voir aussi.</span><span class="sxs-lookup"><span data-stu-id="816a9-309">For more information, see the topics in See Also.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="816a9-310">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="816a9-310">See Also</span></span>  
 <span data-ttu-id="816a9-311">[Nouveautés de l’adaptateur Windows SharePoint Services ?](../core/what-is-the-windows-sharepoint-services-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="816a9-311">[What Is the Windows SharePoint Services Adapter?](../core/what-is-the-windows-sharepoint-services-adapter.md) </span></span>  
 [<span data-ttu-id="816a9-312">Procédures pas à pas de carte de Windows SharePoint Services</span><span class="sxs-lookup"><span data-stu-id="816a9-312">Windows SharePoint Services Adapter Walkthroughs</span></span>](../core/windows-sharepoint-services-adapter-walkthroughs.md)