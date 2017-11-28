---
title: "Étape 2 : Configurer et démarrer l’Application1 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5cb061ca-acf4-4de4-a634-b3bb98876989
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cc9c3c027126d3a461bf99329b70fda57b9be647
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-2-configure-and-start-the-application"></a><span data-ttu-id="2e079-102">Étape 2 : Configurer et démarrer l’Application</span><span class="sxs-lookup"><span data-stu-id="2e079-102">Step 2: Configure and Start the Application</span></span>
<span data-ttu-id="2e079-103">![Étape 2 sur 3](../adapters-and-accelerators/adapter-oracle-database/media/step-2of3.gif "Step_2of3")</span><span class="sxs-lookup"><span data-stu-id="2e079-103">![Step 2 of 3](../adapters-and-accelerators/adapter-oracle-database/media/step-2of3.gif "Step_2of3")</span></span>  
  
 <span data-ttu-id="2e079-104">**Durée :** 10 minutes</span><span class="sxs-lookup"><span data-stu-id="2e079-104">**Time to complete:** 10 minutes</span></span>  
  
 <span data-ttu-id="2e079-105">**Objectif :** dans cette étape, configurer et démarrer l’application EAISolution.</span><span class="sxs-lookup"><span data-stu-id="2e079-105">**Objective:** In this step, you configure and start the EAISolution application.</span></span>  
  
 <span data-ttu-id="2e079-106">**Objectif :** la configuration concerne principalement la liaison.</span><span class="sxs-lookup"><span data-stu-id="2e079-106">**Purpose:** The configuration is mostly about binding.</span></span>  <span data-ttu-id="2e079-107">Une liaison crée un mappage entre un point de terminaison logique, tel qu'un port d'orchestration ou un lien de rôle, et un point de terminaison physique, tel qu'un tiers ou un port de réception/envoi.</span><span class="sxs-lookup"><span data-stu-id="2e079-107">A binding creates a mapping between a logical endpoint, such as an orchestration port or a role link, and a physical endpoint, such as a send and receive port or party.</span></span> <span data-ttu-id="2e079-108">Elle permet aux différents composants d'une solution d'entreprise BizTalk de communiquer.</span><span class="sxs-lookup"><span data-stu-id="2e079-108">This enables communication between different components of a BizTalk business solution.</span></span> <span data-ttu-id="2e079-109">Vous pouvez créer des liaisons dans la console Administration de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="2e079-109">You can create bindings by using the BizTalk Server Administration console.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="2e079-110">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="2e079-110">Prerequisites</span></span>  
 <span data-ttu-id="2e079-111">Les conditions suivantes sont requises avant de commencer cette étape :</span><span class="sxs-lookup"><span data-stu-id="2e079-111">Note the following requirements before you begin this step:</span></span>  
  
-   <span data-ttu-id="2e079-112">Avant de commencer cette étape, vous devez effectuer [étape 1 : déployer les projets](../core/step-1-deploy-the-projects.md).</span><span class="sxs-lookup"><span data-stu-id="2e079-112">Before you begin this step you must complete [Step 1: Deploy the Projects](../core/step-1-deploy-the-projects.md).</span></span>  
  
-   <span data-ttu-id="2e079-113">Vous devez ouvrir une session en tant que membre du groupe d'administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2e079-113">You must log on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="2e079-114">Procédures</span><span class="sxs-lookup"><span data-stu-id="2e079-114">Procedures</span></span>  
 <span data-ttu-id="2e079-115">L'application BizTalk est une fonctionnalité de BizTalk Server qui facilite et accélère le déploiement, la gestion et la résolution des incidents sur les solutions d'entreprise BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="2e079-115">The BizTalk application is a feature of BizTalk Server that makes it quicker and easier to deploy, manage, and troubleshoot BizTalk Server business solutions.</span></span> <span data-ttu-id="2e079-116">Une application BizTalk est un regroupement logique d'éléments, appelés « artefacts », qui sont utilisés dans une solution d'entreprise BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="2e079-116">A BizTalk application is a logical grouping of the items, called "artifacts," used in a BizTalk Server business solution.</span></span>  <span data-ttu-id="2e079-117">Pour plus d’informations, consultez [qu’est une Application BizTalk ?](../core/what-is-a-biztalk-application.md).</span><span class="sxs-lookup"><span data-stu-id="2e079-117">For more information, see [What Is a BizTalk Application?](../core/what-is-a-biztalk-application.md).</span></span>  <span data-ttu-id="2e079-118">Dans [étape 1 : déployer les projets](../core/step-1-deploy-the-projects.md), nous configurons le nom de l’application à être « EAISolution » avant de déployer les projets.</span><span class="sxs-lookup"><span data-stu-id="2e079-118">In [Step 1: Deploy the Projects](../core/step-1-deploy-the-projects.md), we configure the application name to be “EAISolution” before we deploy the projects.</span></span>  <span data-ttu-id="2e079-119">Ainsi, l'application EAISolution contient l'orchestration, les deux schémas et le mappage.</span><span class="sxs-lookup"><span data-stu-id="2e079-119">So the EAISolution application contains the orchestration, the two schema, and the map.</span></span>  
  
#### <a name="to-open-the-eaisolution-application-from-biztalk-server-administration-console"></a><span data-ttu-id="2e079-120">Ouverture de l'application EAISolution à partir de la console Administration de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="2e079-120">To open the EAISolution application from BizTalk Server Administration Console</span></span>  
  
1.  <span data-ttu-id="2e079-121">Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2e079-121">Click **Start**, point to **All Programs**, point to [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)].</span></span>  
  
2.  <span data-ttu-id="2e079-122">Dans l’arborescence de la console sur le côté gauche de la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], avec le bouton droit **groupe BizTalk**, puis cliquez sur **Actualiser**.</span><span class="sxs-lookup"><span data-stu-id="2e079-122">In the console tree on the left side of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], right-click **BizTalk Group**, and then click **Refresh**.</span></span>  
  
3.  <span data-ttu-id="2e079-123">Développez **groupe BizTalk**, développez **Applications**, puis cliquez sur **EAISolution**.</span><span class="sxs-lookup"><span data-stu-id="2e079-123">Expand **BizTalk Group**, expand **Applications**, and then click **EAISolution**.</span></span>  
  
 <span data-ttu-id="2e079-124">Dans [leçon 2 : définir le processus d’entreprise](../core/lesson-2-define-the-business-process.md), nous avons créé une orchestration.</span><span class="sxs-lookup"><span data-stu-id="2e079-124">In [Lesson 2: Define the Business Process](../core/lesson-2-define-the-business-process.md), we created an orchestration.</span></span>  <span data-ttu-id="2e079-125">Dans l'orchestration, nous avons défini les ports logiques.</span><span class="sxs-lookup"><span data-stu-id="2e079-125">In the orchestration, we defined the logical ports.</span></span>  <span data-ttu-id="2e079-126">Dans les procédures suivantes, vous allez définir les ports physiques, puis les lier aux ports logiques.</span><span class="sxs-lookup"><span data-stu-id="2e079-126">In the following procedures, you will define the physical ports and bind the physical ports to the logical ports.</span></span>  
  
#### <a name="to-create-the-receiverequest-port"></a><span data-ttu-id="2e079-127">Création du port ReceiveRequest</span><span class="sxs-lookup"><span data-stu-id="2e079-127">To create the ReceiveRequest port</span></span>  
  
1.  <span data-ttu-id="2e079-128">À partir de la Console Administration de BizTalk Server, sous la **EAISolution** nœud, avec le bouton droit **Ports de réception**, pointez sur **nouveau**, puis cliquez sur **unidirectionnel Port de réception**.</span><span class="sxs-lookup"><span data-stu-id="2e079-128">From BizTalk Server Administration Console, under the **EAISolution** node, right-click **Receive Ports**, point to **New**, and then click **One-way Receive Port**.</span></span>  
  
2.  <span data-ttu-id="2e079-129">Sous l'onglet Général, effectuez les paramétrages suivants :</span><span class="sxs-lookup"><span data-stu-id="2e079-129">On the General tab,  do the following:</span></span>  
  
    |<span data-ttu-id="2e079-130">Utiliser</span><span class="sxs-lookup"><span data-stu-id="2e079-130">Use this</span></span>|<span data-ttu-id="2e079-131">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="2e079-131">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="2e079-132">**Nom**</span><span class="sxs-lookup"><span data-stu-id="2e079-132">**Name**</span></span>|<span data-ttu-id="2e079-133">Type **EAISolutionReceiveRequestPort**.</span><span class="sxs-lookup"><span data-stu-id="2e079-133">Type **EAISolutionReceiveRequestPort**.</span></span>|  
    |<span data-ttu-id="2e079-134">**Activer le routage des messages ayant échoué**</span><span class="sxs-lookup"><span data-stu-id="2e079-134">**Enable routing for failed messages**</span></span>|<span data-ttu-id="2e079-135">(désactivé)</span><span class="sxs-lookup"><span data-stu-id="2e079-135">(clear)</span></span>|  
  
3.  <span data-ttu-id="2e079-136">Cliquez sur **emplacements de réception**, puis cliquez sur **nouveau**.</span><span class="sxs-lookup"><span data-stu-id="2e079-136">Click **Receive Locations**, and then click **New**.</span></span>  
  
4.  <span data-ttu-id="2e079-137">Dans la boîte de dialogue ReceiveLocation1 - Propriétés d'emplacement de réception, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="2e079-137">From Receive Location1 – Receive Location Properties, do the following:</span></span>  
  
    |<span data-ttu-id="2e079-138">Utiliser</span><span class="sxs-lookup"><span data-stu-id="2e079-138">Use this</span></span>|<span data-ttu-id="2e079-139">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="2e079-139">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="2e079-140">**Nom**</span><span class="sxs-lookup"><span data-stu-id="2e079-140">**Name**</span></span>|<span data-ttu-id="2e079-141">Type **EAISolutionReceiveRequestLocation**.</span><span class="sxs-lookup"><span data-stu-id="2e079-141">Type **EAISolutionReceiveRequestLocation**.</span></span>|  
    |<span data-ttu-id="2e079-142">**Type**</span><span class="sxs-lookup"><span data-stu-id="2e079-142">**Type**</span></span>|<span data-ttu-id="2e079-143">Sélectionnez **fichier**.</span><span class="sxs-lookup"><span data-stu-id="2e079-143">Select **File**.</span></span>|  
    |<span data-ttu-id="2e079-144">**Gestionnaire de réception**</span><span class="sxs-lookup"><span data-stu-id="2e079-144">**Receive handler**</span></span>|<span data-ttu-id="2e079-145">Sélectionnez **BizTalkServerApplication**.</span><span class="sxs-lookup"><span data-stu-id="2e079-145">Select **BizTalkServerApplication**.</span></span>|  
    |<span data-ttu-id="2e079-146">**Pipeline de réception**</span><span class="sxs-lookup"><span data-stu-id="2e079-146">**Receive pipeline**</span></span>|<span data-ttu-id="2e079-147">Sélectionnez **XMLReceive**.</span><span class="sxs-lookup"><span data-stu-id="2e079-147">Select **XMLReceive**.</span></span>|  
  
5.  <span data-ttu-id="2e079-148">Cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="2e079-148">Click **Configure**.</span></span>  
  
6.  <span data-ttu-id="2e079-149">Dans la boîte de dialogue Propriétés du transport FILE, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="2e079-149">From File Transport Properties, do the following:</span></span>  
  
    |<span data-ttu-id="2e079-150">Utiliser</span><span class="sxs-lookup"><span data-stu-id="2e079-150">Use this</span></span>|<span data-ttu-id="2e079-151">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="2e079-151">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="2e079-152">**Dossier de réception**</span><span class="sxs-lookup"><span data-stu-id="2e079-152">**Receive folder**</span></span>|<span data-ttu-id="2e079-153">Type **C:\BTSTutorials\WareHouse\Request**.</span><span class="sxs-lookup"><span data-stu-id="2e079-153">Type **C:\BTSTutorials\WareHouse\Request**.</span></span>|  
  
7.  <span data-ttu-id="2e079-154">Cliquez sur **OK** trois fois.</span><span class="sxs-lookup"><span data-stu-id="2e079-154">Click **OK** three times.</span></span>  
  
#### <a name="to-create-the-senddecline-port"></a><span data-ttu-id="2e079-155">Création du port SendDecline</span><span class="sxs-lookup"><span data-stu-id="2e079-155">To create the SendDecline port</span></span>  
  
1.  <span data-ttu-id="2e079-156">À partir de la Console Administration de BizTalk Server, sous la **EAISolution** nœud, avec le bouton droit **Ports d’envoi**, pointez sur **nouveau**, puis cliquez sur **unidirectionnel statique Port d’envoi**.</span><span class="sxs-lookup"><span data-stu-id="2e079-156">From BizTalk Server Administration Console, under the **EAISolution** node, right-click **Send Ports**, point to **New**, and then click **Static One-way Send Port**.</span></span>  
  
2.  <span data-ttu-id="2e079-157">Sous l’onglet Général, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="2e079-157">On the General tab, do the following:</span></span>  
  
    |<span data-ttu-id="2e079-158">Utiliser</span><span class="sxs-lookup"><span data-stu-id="2e079-158">Use this</span></span>|<span data-ttu-id="2e079-159">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="2e079-159">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="2e079-160">**Nom**</span><span class="sxs-lookup"><span data-stu-id="2e079-160">**Name**</span></span>|<span data-ttu-id="2e079-161">Type **EAISolutionSendDeclinePort**.</span><span class="sxs-lookup"><span data-stu-id="2e079-161">Type **EAISolutionSendDeclinePort**.</span></span>|  
    |<span data-ttu-id="2e079-162">**Type**</span><span class="sxs-lookup"><span data-stu-id="2e079-162">**Type**</span></span>|<span data-ttu-id="2e079-163">Sélectionnez **fichier**.</span><span class="sxs-lookup"><span data-stu-id="2e079-163">Select **File**.</span></span>|  
    |<span data-ttu-id="2e079-164">**Gestionnaire d’envoi**</span><span class="sxs-lookup"><span data-stu-id="2e079-164">**Send handler**</span></span>|<span data-ttu-id="2e079-165">Sélectionnez **BizTAlkServerApplication**.</span><span class="sxs-lookup"><span data-stu-id="2e079-165">Select **BizTAlkServerApplication**.</span></span>|  
    |<span data-ttu-id="2e079-166">**Pipeline d’envoi**</span><span class="sxs-lookup"><span data-stu-id="2e079-166">**Send pipeline**</span></span>|<span data-ttu-id="2e079-167">Sélectionnez **XML Transmit**.</span><span class="sxs-lookup"><span data-stu-id="2e079-167">Select **XML Transmit**.</span></span>|  
  
3.  <span data-ttu-id="2e079-168">Cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="2e079-168">Click **Configure**.</span></span>  
  
4.  <span data-ttu-id="2e079-169">Dans la boîte de dialogue Propriétés du transport FILE, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="2e079-169">From File Transport Properties, do the following:</span></span>  
  
    |<span data-ttu-id="2e079-170">Utiliser</span><span class="sxs-lookup"><span data-stu-id="2e079-170">Use this</span></span>|<span data-ttu-id="2e079-171">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="2e079-171">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="2e079-172">**Dossier de réception**</span><span class="sxs-lookup"><span data-stu-id="2e079-172">**Receive folder**</span></span>|<span data-ttu-id="2e079-173">Type **C:\BTSTutorials\WareHouse\RequestDecline**.</span><span class="sxs-lookup"><span data-stu-id="2e079-173">Type **C:\BTSTutorials\WareHouse\RequestDecline**.</span></span>|  
    |<span data-ttu-id="2e079-174">**Nom de fichier**</span><span class="sxs-lookup"><span data-stu-id="2e079-174">**File name**</span></span>|<span data-ttu-id="2e079-175">Type **RequestDecline_%MessageID%.xml**.</span><span class="sxs-lookup"><span data-stu-id="2e079-175">Type **RequestDecline_%MessageID%.xml**.</span></span>|  
  
5.  <span data-ttu-id="2e079-176">Cliquez deux fois sur **OK** .</span><span class="sxs-lookup"><span data-stu-id="2e079-176">Click **OK** twice.</span></span>  
  
#### <a name="to-create-the-sendtoerp-port"></a><span data-ttu-id="2e079-177">Création du port SendToERP</span><span class="sxs-lookup"><span data-stu-id="2e079-177">To create the SendToERP port</span></span>  
  
1.  <span data-ttu-id="2e079-178">À partir de la Console Administration de BizTalk Server, sous la **EAISolution** nœud, avec le bouton droit **Ports d’envoi**, pointez sur **nouveau**, puis cliquez sur **unidirectionnel statique Port d’envoi**.</span><span class="sxs-lookup"><span data-stu-id="2e079-178">From BizTalk Server Administration Console, under the **EAISolution** node, right-click **Send Ports**, point to **New**, and then click **Static One-way Send Port**.</span></span>  
  
2.  <span data-ttu-id="2e079-179">Sous l’onglet Général, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="2e079-179">On the General tab, do the following:</span></span>  
  
    |<span data-ttu-id="2e079-180">Utiliser</span><span class="sxs-lookup"><span data-stu-id="2e079-180">Use this</span></span>|<span data-ttu-id="2e079-181">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="2e079-181">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="2e079-182">**Nom**</span><span class="sxs-lookup"><span data-stu-id="2e079-182">**Name**</span></span>|<span data-ttu-id="2e079-183">Type **EAISolutionSendToERPPort**.</span><span class="sxs-lookup"><span data-stu-id="2e079-183">Type **EAISolutionSendToERPPort**.</span></span>|  
    |<span data-ttu-id="2e079-184">**Type**</span><span class="sxs-lookup"><span data-stu-id="2e079-184">**Type**</span></span>|<span data-ttu-id="2e079-185">Sélectionnez **fichier**.</span><span class="sxs-lookup"><span data-stu-id="2e079-185">Select **File**.</span></span>|  
    |<span data-ttu-id="2e079-186">**Gestionnaire d’envoi**</span><span class="sxs-lookup"><span data-stu-id="2e079-186">**Send handler**</span></span>|<span data-ttu-id="2e079-187">Sélectionnez **BizTAlkServerApplication**.</span><span class="sxs-lookup"><span data-stu-id="2e079-187">Select **BizTAlkServerApplication**.</span></span>|  
    |<span data-ttu-id="2e079-188">**Pipeline d’envoi**</span><span class="sxs-lookup"><span data-stu-id="2e079-188">**Send pipeline**</span></span>|<span data-ttu-id="2e079-189">Sélectionnez **XML Transmit**.</span><span class="sxs-lookup"><span data-stu-id="2e079-189">Select **XML Transmit**.</span></span>|  
  
3.  <span data-ttu-id="2e079-190">Cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="2e079-190">Click **Configure**.</span></span>  
  
4.  <span data-ttu-id="2e079-191">Dans la boîte de dialogue Propriétés du transport FILE, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="2e079-191">From File Transport Properties, do the following:</span></span>  
  
    |<span data-ttu-id="2e079-192">Utiliser</span><span class="sxs-lookup"><span data-stu-id="2e079-192">Use this</span></span>|<span data-ttu-id="2e079-193">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="2e079-193">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="2e079-194">**Dossier de réception**</span><span class="sxs-lookup"><span data-stu-id="2e079-194">**Receive folder**</span></span>|<span data-ttu-id="2e079-195">Type **C:\BTSTutorials\ERP\Request**.</span><span class="sxs-lookup"><span data-stu-id="2e079-195">Type **C:\BTSTutorials\ERP\Request**.</span></span>|  
    |<span data-ttu-id="2e079-196">**Nom de fichier**</span><span class="sxs-lookup"><span data-stu-id="2e079-196">**File name**</span></span>|<span data-ttu-id="2e079-197">Type **Request_%MessageID%.xml**.</span><span class="sxs-lookup"><span data-stu-id="2e079-197">Type **Request_%MessageID%.xml**.</span></span>|  
  
5.  <span data-ttu-id="2e079-198">Cliquez deux fois sur **OK** .</span><span class="sxs-lookup"><span data-stu-id="2e079-198">Click **OK** twice.</span></span>  
  
#### <a name="to-bind-the-ports"></a><span data-ttu-id="2e079-199">Liaison des ports</span><span class="sxs-lookup"><span data-stu-id="2e079-199">To bind the ports</span></span>  
  
1.  <span data-ttu-id="2e079-200">À partir de la Console Administration de BizTalk Server, avec le bouton droit **EAISolution**, puis cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="2e079-200">From BizTalk Server Administration Console, right-click **EAISolution**, and then click **Configure**.</span></span>  
  
2.  <span data-ttu-id="2e079-201">Configurer l’application, dans le volet gauche, cliquez sur **EAIProcess**.</span><span class="sxs-lookup"><span data-stu-id="2e079-201">From Configure Application, in the left pane, click **EAIProcess**.</span></span>  <span data-ttu-id="2e079-202">Il s'agit de l'orchestration que nous avons créée.</span><span class="sxs-lookup"><span data-stu-id="2e079-202">This is the orchestration we created.</span></span>  
  
3.  <span data-ttu-id="2e079-203">Dans le volet droit, effectuez les opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="2e079-203">From the right pane, do the following:</span></span>  
  
    |<span data-ttu-id="2e079-204">Utiliser</span><span class="sxs-lookup"><span data-stu-id="2e079-204">Use this</span></span>|<span data-ttu-id="2e079-205">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="2e079-205">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="2e079-206">**Hôte**</span><span class="sxs-lookup"><span data-stu-id="2e079-206">**Host**</span></span>|<span data-ttu-id="2e079-207">Sélectionnez **BizTalkServerApplication**.</span><span class="sxs-lookup"><span data-stu-id="2e079-207">Select **BizTalkServerApplication**.</span></span>|  
    |<span data-ttu-id="2e079-208">**Port de réception** pour **ReceiveRequestPort**</span><span class="sxs-lookup"><span data-stu-id="2e079-208">**Receive Port** for **ReceiveRequestPort**</span></span>|<span data-ttu-id="2e079-209">Sélectionnez **EAISolutionReceiveReqeustPort**.</span><span class="sxs-lookup"><span data-stu-id="2e079-209">Select **EAISolutionReceiveReqeustPort**.</span></span>|  
    |<span data-ttu-id="2e079-210">**Groupes de ports de ports d’envoi** pour **ReceiveRequestPort**</span><span class="sxs-lookup"><span data-stu-id="2e079-210">**Send PortsSend Port Groups** for **ReceiveRequestPort**</span></span>|<span data-ttu-id="2e079-211">Sélectionnez **EAISolutionSendDeclinePort**.</span><span class="sxs-lookup"><span data-stu-id="2e079-211">Select **EAISolutionSendDeclinePort**.</span></span>|  
    |<span data-ttu-id="2e079-212">**Port de réception** pour **ReceiveRequestPort**</span><span class="sxs-lookup"><span data-stu-id="2e079-212">**Receive Port** for **ReceiveRequestPort**</span></span>|<span data-ttu-id="2e079-213">Sélectionnez **EAISolutionSendToERPPort**.</span><span class="sxs-lookup"><span data-stu-id="2e079-213">Select **EAISolutionSendToERPPort**.</span></span>|  
  
4.  <span data-ttu-id="2e079-214">Cliquez sur **OK** pour enregistrer la configuration.</span><span class="sxs-lookup"><span data-stu-id="2e079-214">Click **OK** to save the configuration.</span></span>  
  
#### <a name="to-start-the-application"></a><span data-ttu-id="2e079-215">Pour démarrer l'application</span><span class="sxs-lookup"><span data-stu-id="2e079-215">To start the application</span></span>  
  
1.  <span data-ttu-id="2e079-216">À partir de la Console Administration de BizTalk Server, avec le bouton droit **EAISolution**, puis cliquez sur **Démarrer**.</span><span class="sxs-lookup"><span data-stu-id="2e079-216">From BizTalk Server Administration Console, right-click **EAISolution**, and then click **Start**.</span></span>  
  
2.  <span data-ttu-id="2e079-217">Dans la boîte de dialogue, cliquez sur **Démarrer**.</span><span class="sxs-lookup"><span data-stu-id="2e079-217">From the dialog, click **Start**.</span></span>  
  
## <a name="what-did-i-just-do"></a><span data-ttu-id="2e079-218">Actions effectuées</span><span class="sxs-lookup"><span data-stu-id="2e079-218">What did I just do?</span></span>  
 <span data-ttu-id="2e079-219">Au cours de cette étape, vous avez configuré et démarré l'application EAIApplication.</span><span class="sxs-lookup"><span data-stu-id="2e079-219">In this step, you configured and started the EAIApplication application.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="2e079-220">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="2e079-220">Next Steps</span></span>  
 <span data-ttu-id="2e079-221">Vous testez comment la solution EAI traite les messages de [étape 3 : tester la Solution](../core/step-3-test-the-solution2.md).</span><span class="sxs-lookup"><span data-stu-id="2e079-221">You test how the EAI solution processes messages in [Step 3: Test the Solution](../core/step-3-test-the-solution2.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e079-222">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2e079-222">See Also</span></span>  
 <span data-ttu-id="2e079-223">[Étape 1 : Déployer des projets](../core/step-1-deploy-the-projects.md) </span><span class="sxs-lookup"><span data-stu-id="2e079-223">[Step 1: Deploy the Projects](../core/step-1-deploy-the-projects.md) </span></span>  
 [<span data-ttu-id="2e079-224">Étape 3 : Tester la Solution</span><span class="sxs-lookup"><span data-stu-id="2e079-224">Step 3: Test the Solution</span></span>](../core/step-3-test-the-solution2.md)