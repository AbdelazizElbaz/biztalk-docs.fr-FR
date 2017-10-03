---
title: "Étape 1 : Déployer les projets | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0467c140-1f4c-4cfa-b46f-dc1d0f8755d4
caps.latest.revision: "44"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: eb4262b2bb424a339f866f3b4a14ae03c2e507f6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-1-deploy-the-projects"></a><span data-ttu-id="9199e-102">Étape 1 : déployer les projets</span><span class="sxs-lookup"><span data-stu-id="9199e-102">Step 1: Deploy the Projects</span></span>
<span data-ttu-id="9199e-103">![Étape 1 sur 3](../adapters-and-accelerators/adapter-oracle-database/media/step-1of3.gif "Step_1of3")</span><span class="sxs-lookup"><span data-stu-id="9199e-103">![Step 1 of 3](../adapters-and-accelerators/adapter-oracle-database/media/step-1of3.gif "Step_1of3")</span></span>  
  
 <span data-ttu-id="9199e-104">**Durée :** 5 minutes</span><span class="sxs-lookup"><span data-stu-id="9199e-104">**Time to complete:** 5 minutes</span></span>  
  
 <span data-ttu-id="9199e-105">**Objectif :** dans cette étape, vous déployez les projets EAISchemas et EAIOrchestration.</span><span class="sxs-lookup"><span data-stu-id="9199e-105">**Objective:** In this step, you deploy the EAISchemas and EAIOrchestration projects.</span></span>  
  
 <span data-ttu-id="9199e-106">**Objectif :** lorsque vous déployez un projet ou une solution dans Visual Studio, les assemblys sont automatiquement générés et déployés dans l’application spécifiée.</span><span class="sxs-lookup"><span data-stu-id="9199e-106">**Purpose:** When you deploy a project or solution in Visual Studio, the assemblies are automatically built and deployed into the specified application.</span></span> <span data-ttu-id="9199e-107">Dans le cadre de ce processus, l'assembly et les orchestrations, schémas et mappages qu'il contient (appelés « artefacts ») sont importés dans la base de données de gestion BizTalk locale et associés à l'application spécifiée.</span><span class="sxs-lookup"><span data-stu-id="9199e-107">As part of this process, the assembly along with the orchestrations, schemas, and maps that it contains (called "artifacts") are imported into the local BizTalk Management database and associated in the database with the specified application.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="9199e-108">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="9199e-108">Prerequisites</span></span>  
 <span data-ttu-id="9199e-109">Les conditions suivantes sont requises avant de commencer cette étape :</span><span class="sxs-lookup"><span data-stu-id="9199e-109">Note the following requirements before you begin this step:</span></span>  
  
-   <span data-ttu-id="9199e-110">Avant de commencer cette étape, vous devez étudier les leçons suivantes :</span><span class="sxs-lookup"><span data-stu-id="9199e-110">Before you begin this step you must complete the following lessons:</span></span>  
  
    -   [<span data-ttu-id="9199e-111">Leçon 1 : Définir des schémas et un mappage</span><span class="sxs-lookup"><span data-stu-id="9199e-111">Lesson 1: Define Schemas and a Map</span></span>](../core/lesson-1-define-schemas-and-a-map.md)  
  
    -   [<span data-ttu-id="9199e-112">Leçon 2 : Définir le processus d’entreprise</span><span class="sxs-lookup"><span data-stu-id="9199e-112">Lesson 2: Define the Business Process</span></span>](../core/lesson-2-define-the-business-process.md)  
  
-   <span data-ttu-id="9199e-113">Vous devez ouvrir une session en tant que membre du groupe d'administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9199e-113">You must log on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group.</span></span>  
  
-   <span data-ttu-id="9199e-114">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devez exécuter Visual Studio avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="9199e-114">On a system that supports User Account Control (UAC), you must run Visual Studio with Administrative privileges.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="9199e-115">Procédures</span><span class="sxs-lookup"><span data-stu-id="9199e-115">Procedures</span></span>  
 <span data-ttu-id="9199e-116">Pour déployer l'application à l'aide de Visual Studio, vous devez vous connecter à Windows en tant que membre du groupe d'administrateurs BizTalk Server et exécuter Visual Studio en tant qu'administrateur.</span><span class="sxs-lookup"><span data-stu-id="9199e-116">To deploy the application using Visual Studio, you must log on Windows as a member of the BizTalk Server Administrators group and run Visual Studio as administrator.</span></span>  <span data-ttu-id="9199e-117">Sinon, une erreur « Accès refusé » se produira.</span><span class="sxs-lookup"><span data-stu-id="9199e-117">Otherwise you will get the “Access is denied” error.</span></span>  
  
#### <a name="to-open-the-solution-with-administrative-privileges"></a><span data-ttu-id="9199e-118">Pour ouvrir la solution avec des privilèges d'administrateur</span><span class="sxs-lookup"><span data-stu-id="9199e-118">To open the solution with administrative privileges</span></span>  
  
1.  <span data-ttu-id="9199e-119">Connectez-vous à Windows en tant que membre du groupe d'administrateurs de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="9199e-119">Log on Windows as a member of the BizTalk Server Administrators group.</span></span>  
  
2.  <span data-ttu-id="9199e-120">Démarrer **Microsoft Visual Studio** en tant qu’administrateur.</span><span class="sxs-lookup"><span data-stu-id="9199e-120">Start **Microsoft Visual Studio** as an administrator.</span></span>  
  
3.  <span data-ttu-id="9199e-121">Dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], dans le **fichier** menu, pointez sur **ouvrir**, puis cliquez sur **projet/Solution**.</span><span class="sxs-lookup"><span data-stu-id="9199e-121">In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], on the **File** menu, point to **Open**, and then click **Project/Solution**.</span></span>  
  
4.  <span data-ttu-id="9199e-122">Dans le **ouvrir le projet** boîte de dialogue, cliquez sur Parcourir pour le **EAISolution.sln** fichier solution du projet, puis cliquez sur **ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="9199e-122">In the **Open Project** dialog box, browse to the **EAISolution.sln** project solution file, and then click **Open**.</span></span>  
  
 <span data-ttu-id="9199e-123">Le processus de déploiement requiert la signature avec un nom fort de l'assembly.</span><span class="sxs-lookup"><span data-stu-id="9199e-123">The deployment process requires that assembly is strongly signed.</span></span>  <span data-ttu-id="9199e-124">Vous devez vous connecter à vos assemblys en associant le projet avec un fichier de clé de nom fort assembly.</span><span class="sxs-lookup"><span data-stu-id="9199e-124">You must sign your assemblies by associating the project with a strong name assembly key file.</span></span>  <span data-ttu-id="9199e-125">Ce fichier est fourni dans le cadre du didacticiel.</span><span class="sxs-lookup"><span data-stu-id="9199e-125">This file is provided by the tutorial files.</span></span>  
  
 <span data-ttu-id="9199e-126">L'application BizTalk est une fonctionnalité de BizTalk Server qui facilite et accélère le déploiement, la gestion et la résolution des incidents sur les solutions d'entreprise BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="9199e-126">The BizTalk application is a feature of BizTalk Server that makes it quicker and easier to deploy, manage, and troubleshoot BizTalk Server business solutions.</span></span> <span data-ttu-id="9199e-127">Une application BizTalk est un regroupement logique d'éléments, appelés « artefacts », qui sont utilisés dans une solution d'entreprise BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="9199e-127">A BizTalk application is a logical grouping of the items, called "artifacts," used in a BizTalk Server business solution.</span></span> <span data-ttu-id="9199e-128">Nous pouvons spécifier un nom d'application pour un projet.</span><span class="sxs-lookup"><span data-stu-id="9199e-128">We can specify an application name for a project.</span></span>  <span data-ttu-id="9199e-129">Le processus de déploiement crée automatiquement une nouvelle application qui porte le nom spécifié s'il n'existe pas.</span><span class="sxs-lookup"><span data-stu-id="9199e-129">The deployment process will automatically create a new application having the specified name if it doesn’t exist.</span></span>  
  
#### <a name="to-configure-and-deploy-the-projects"></a><span data-ttu-id="9199e-130">Pour configurer et déployer les projets</span><span class="sxs-lookup"><span data-stu-id="9199e-130">To configure and deploy the projects</span></span>  
  
1.  <span data-ttu-id="9199e-131">Dans l’Explorateur de solutions, cliquez sur le **EAISchemas** de projet, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="9199e-131">In Solution Explorer, right-click the **EAISchemas** project, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="9199e-132">Cliquez sur le **signature** onglet, sélectionnez **signer l’assembly**.</span><span class="sxs-lookup"><span data-stu-id="9199e-132">Click the **Signing** tab, select **Sign the assembly**.</span></span>  
  
3.  <span data-ttu-id="9199e-133">Dans la liste déroulante de la **choisir un fichier de clé de nom fort** boîte, sélectionnez  **\<Parcourir... >**.</span><span class="sxs-lookup"><span data-stu-id="9199e-133">From the drop-down list in the **Choose a strong name key file** box, select **\<Browse…>**.</span></span>  
  
4.  <span data-ttu-id="9199e-134">Dans le **sélectionner le fichier** boîte de dialogue, accédez à **C:\BTStutorials**, cliquez sur **btsTutorials.snk**, puis cliquez sur **ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="9199e-134">In the **Select File** dialog box, navigate to **C:\BTStutorials**, click **btsTutorials.snk**, and then click **Open**.</span></span>  
  
5.  <span data-ttu-id="9199e-135">Cliquez sur le **déploiement** onglet, dans la zone à droite de **nom de l’Application**, type `EAISolution`.</span><span class="sxs-lookup"><span data-stu-id="9199e-135">Click the **Deployment** tab, in the box to the right of **Application Name**, type `EAISolution`.</span></span>  
  
6.  <span data-ttu-id="9199e-136">Dans la liste déroulante dans la zone à droite de **redéployer**, sélectionnez **True**.</span><span class="sxs-lookup"><span data-stu-id="9199e-136">From the drop-down list in the box to the right of **Redeploy**, select **True**.</span></span>  
  
7.  <span data-ttu-id="9199e-137">Dans l’Explorateur de solutions, cliquez sur **EAISchemas**, puis cliquez sur **déployer**.</span><span class="sxs-lookup"><span data-stu-id="9199e-137">In Solution Explorer, right-click **EAISchemas**, and then click **Deploy**.</span></span>  <span data-ttu-id="9199e-138">La fenêtre Sortie doit s'afficher :</span><span class="sxs-lookup"><span data-stu-id="9199e-138">The Output window should display:</span></span>  
  
    ```  
    ========== Build: 1 succeeded or up-to-date, 0 failed, 0 skipped ==========  
    ========== Deploy: 1 succeeded, 0 failed, 0 skipped ==========  
  
    ```  
  
8.  <span data-ttu-id="9199e-139">Répétez les étapes 1 à 7 pour déployer le projet EAIOrchestration.</span><span class="sxs-lookup"><span data-stu-id="9199e-139">Repeat step 1 through 7 to deploy the EAIOrchestration project.</span></span>  
  
## <a name="what-did-i-just-do"></a><span data-ttu-id="9199e-140">Actions effectuées</span><span class="sxs-lookup"><span data-stu-id="9199e-140">What did I just do?</span></span>  
 <span data-ttu-id="9199e-141">Au cours de cette étape, vous avez déployé les projets EAISchemas et EAIOrchestration.</span><span class="sxs-lookup"><span data-stu-id="9199e-141">In this step, you deployed the EAISchemas and EAIOrchestration projects.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="9199e-142">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="9199e-142">Next Steps</span></span>  
 <span data-ttu-id="9199e-143">Vous allez créer les ports physiques et les lier aux ports logiques de l'orchestration.</span><span class="sxs-lookup"><span data-stu-id="9199e-143">You create the physical ports, and bind them to the logical ports of the orchestration.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9199e-144">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9199e-144">See Also</span></span>  
 <span data-ttu-id="9199e-145">[Étape 2 : Configurer et démarrer l’Application](../core/step-2-configure-and-start-the-application1.md) </span><span class="sxs-lookup"><span data-stu-id="9199e-145">[Step 2: Configure and Start the Application](../core/step-2-configure-and-start-the-application1.md) </span></span>  
 [<span data-ttu-id="9199e-146">Étape 3 : Tester la Solution</span><span class="sxs-lookup"><span data-stu-id="9199e-146">Step 3: Test the Solution</span></span>](../core/step-3-test-the-solution2.md)