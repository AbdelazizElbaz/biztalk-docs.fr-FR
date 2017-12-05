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
ms.openlocfilehash: ad4424327f6cd24624abe6b4a850f3c24153e6a4
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="step-1-deploy-the-projects"></a><span data-ttu-id="d416e-102">Étape 1 : déployer les projets</span><span class="sxs-lookup"><span data-stu-id="d416e-102">Step 1: Deploy the Projects</span></span>
<span data-ttu-id="d416e-103">![Étape 1 sur 3](../adapters-and-accelerators/adapter-oracle-database/media/step-1of3.gif "Step_1of3")</span><span class="sxs-lookup"><span data-stu-id="d416e-103">![Step 1 of 3](../adapters-and-accelerators/adapter-oracle-database/media/step-1of3.gif "Step_1of3")</span></span>  
  
 <span data-ttu-id="d416e-104">**Durée :** 5 minutes</span><span class="sxs-lookup"><span data-stu-id="d416e-104">**Time to complete:** 5 minutes</span></span>  
  
 <span data-ttu-id="d416e-105">**Objectif :** dans cette étape, vous déployez les projets EAISchemas et EAIOrchestration.</span><span class="sxs-lookup"><span data-stu-id="d416e-105">**Objective:** In this step, you deploy the EAISchemas and EAIOrchestration projects.</span></span>  
  
 <span data-ttu-id="d416e-106">**Objectif :** lorsque vous déployez un projet ou une solution dans Visual Studio, les assemblys sont automatiquement générés et déployés dans l’application spécifiée.</span><span class="sxs-lookup"><span data-stu-id="d416e-106">**Purpose:** When you deploy a project or solution in Visual Studio, the assemblies are automatically built and deployed into the specified application.</span></span> <span data-ttu-id="d416e-107">Dans le cadre de ce processus, l'assembly et les orchestrations, schémas et mappages qu'il contient (appelés « artefacts ») sont importés dans la base de données de gestion BizTalk locale et associés à l'application spécifiée.</span><span class="sxs-lookup"><span data-stu-id="d416e-107">As part of this process, the assembly along with the orchestrations, schemas, and maps that it contains (called "artifacts") are imported into the local BizTalk Management database and associated in the database with the specified application.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="d416e-108">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="d416e-108">Prerequisites</span></span>  
  
-   [<span data-ttu-id="d416e-109">Leçon 1 : Définir des schémas et un mappage</span><span class="sxs-lookup"><span data-stu-id="d416e-109">Lesson 1: Define Schemas and a Map</span></span>](../core/lesson-1-define-schemas-and-a-map.md)  
  
-   [<span data-ttu-id="d416e-110">Leçon 2 : Définir le processus d’entreprise</span><span class="sxs-lookup"><span data-stu-id="d416e-110">Lesson 2: Define the Business Process</span></span>](../core/lesson-2-define-the-business-process.md)  
  
-   <span data-ttu-id="d416e-111">Connectez-vous en tant que membre de le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] groupe Administrateurs</span><span class="sxs-lookup"><span data-stu-id="d416e-111">Sign in as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group</span></span>

-   <span data-ttu-id="d416e-112">Exécuter Visual Studio avec des privilèges d’administrateur</span><span class="sxs-lookup"><span data-stu-id="d416e-112">Run Visual Studio with Administrative privileges</span></span>

> [!TIP]
> <span data-ttu-id="d416e-113">Vous pouvez télécharger les fichiers requis du didacticiel à [didacticiel 1 : intégration](https://www.microsoft.com/download/details.aspx?id=22793).</span><span class="sxs-lookup"><span data-stu-id="d416e-113">You can download the required tutorial files at [Tutorial 1: Enterprise Application Integration](https://www.microsoft.com/download/details.aspx?id=22793).</span></span>

## <a name="open-the-solution-with-administrative-rights"></a><span data-ttu-id="d416e-114">Ouvrez la solution avec des droits d’administration</span><span class="sxs-lookup"><span data-stu-id="d416e-114">Open the solution with administrative rights</span></span>  
  
1.  <span data-ttu-id="d416e-115">Connectez-vous à Windows en tant que membre du groupe Administrateurs de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="d416e-115">Sign in to Windows as a member of the BizTalk Server Administrators group.</span></span>  
  
2.  <span data-ttu-id="d416e-116">Démarrer **Microsoft Visual Studio** en tant qu’administrateur.</span><span class="sxs-lookup"><span data-stu-id="d416e-116">Start **Microsoft Visual Studio** as an administrator.</span></span>  
  
3.  <span data-ttu-id="d416e-117">Dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], dans le **fichier** menu, pointez sur **ouvrir**, puis cliquez sur **projet/Solution**.</span><span class="sxs-lookup"><span data-stu-id="d416e-117">In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], on the **File** menu, point to **Open**, and then click **Project/Solution**.</span></span>  
  
4.  <span data-ttu-id="d416e-118">Dans le **ouvrir le projet** boîte de dialogue, cliquez sur Parcourir pour le **EAISolution.sln** fichier solution du projet, puis cliquez sur **ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="d416e-118">In the **Open Project** dialog box, browse to the **EAISolution.sln** project solution file, and then click **Open**.</span></span>  
  
 <span data-ttu-id="d416e-119">Le processus de déploiement requiert la signature avec un nom fort de l'assembly.</span><span class="sxs-lookup"><span data-stu-id="d416e-119">The deployment process requires that assembly is strongly signed.</span></span>  <span data-ttu-id="d416e-120">Vous devez vous connecter à vos assemblys en associant le projet avec un fichier de clé de nom fort assembly.</span><span class="sxs-lookup"><span data-stu-id="d416e-120">You must sign your assemblies by associating the project with a strong name assembly key file.</span></span>  <span data-ttu-id="d416e-121">Ce fichier est inclus dans les fichiers du didacticiel.</span><span class="sxs-lookup"><span data-stu-id="d416e-121">This file is included in the tutorial files.</span></span>  
  
 <span data-ttu-id="d416e-122">L'application BizTalk est une fonctionnalité de BizTalk Server qui facilite et accélère le déploiement, la gestion et la résolution des incidents sur les solutions d'entreprise BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="d416e-122">The BizTalk application is a feature of BizTalk Server that makes it quicker and easier to deploy, manage, and troubleshoot BizTalk Server business solutions.</span></span> <span data-ttu-id="d416e-123">Une application BizTalk est un regroupement logique d'éléments, appelés « artefacts », qui sont utilisés dans une solution d'entreprise BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="d416e-123">A BizTalk application is a logical grouping of the items, called "artifacts," used in a BizTalk Server business solution.</span></span> <span data-ttu-id="d416e-124">Nous pouvons spécifier un nom d'application pour un projet.</span><span class="sxs-lookup"><span data-stu-id="d416e-124">We can specify an application name for a project.</span></span>  <span data-ttu-id="d416e-125">Le processus de déploiement crée automatiquement une nouvelle application portant le nom spécifié s’il n’existe.</span><span class="sxs-lookup"><span data-stu-id="d416e-125">The deployment process automatically creates a new application having the specified name if it doesn’t exist.</span></span>  
  
## <a name="configure-and-deploy-the-projects"></a><span data-ttu-id="d416e-126">Configurer et déployer des projets</span><span class="sxs-lookup"><span data-stu-id="d416e-126">Configure and deploy the projects</span></span>  
  
1.  <span data-ttu-id="d416e-127">Dans l’Explorateur de solutions, cliquez sur le **EAISchemas** de projet, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="d416e-127">In Solution Explorer, right-click the **EAISchemas** project, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="d416e-128">Cliquez sur le **signature** onglet, sélectionnez **signer l’assembly**.</span><span class="sxs-lookup"><span data-stu-id="d416e-128">Click the **Signing** tab, select **Sign the assembly**.</span></span>  
  
3.  <span data-ttu-id="d416e-129">Dans la liste déroulante de la **choisir un fichier de clé de nom fort** boîte, sélectionnez  **\<Parcourir... \>**.</span><span class="sxs-lookup"><span data-stu-id="d416e-129">From the drop-down list in the **Choose a strong name key file** box, select **\<Browse…\>**.</span></span>  
  
4.  <span data-ttu-id="d416e-130">Dans le **sélectionner le fichier** boîte de dialogue, accédez à **C:\BTStutorials**, cliquez sur **btsTutorials.snk**, puis cliquez sur **ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="d416e-130">In the **Select File** dialog box, navigate to **C:\BTStutorials**, click **btsTutorials.snk**, and then click **Open**.</span></span> 
  
5.  <span data-ttu-id="d416e-131">Cliquez sur le **déploiement** onglet, dans la zone à droite de **nom de l’Application**, type `EAISolution`.</span><span class="sxs-lookup"><span data-stu-id="d416e-131">Click the **Deployment** tab, in the box to the right of **Application Name**, type `EAISolution`.</span></span>  
  
6.  <span data-ttu-id="d416e-132">Dans la liste déroulante dans la zone à droite de **redéployer**, sélectionnez **True**.</span><span class="sxs-lookup"><span data-stu-id="d416e-132">From the drop-down list in the box to the right of **Redeploy**, select **True**.</span></span>  
  
7.  <span data-ttu-id="d416e-133">Dans l’Explorateur de solutions, cliquez sur **EAISchemas**, puis cliquez sur **déployer**.</span><span class="sxs-lookup"><span data-stu-id="d416e-133">In Solution Explorer, right-click **EAISchemas**, and then click **Deploy**.</span></span>  <span data-ttu-id="d416e-134">La fenêtre Sortie doit s'afficher :</span><span class="sxs-lookup"><span data-stu-id="d416e-134">The Output window should display:</span></span>  
  
    ```  
    ========== Build: 1 succeeded or up-to-date, 0 failed, 0 skipped ==========  
    ========== Deploy: 1 succeeded, 0 failed, 0 skipped ==========  
  
    ```  
  
8.  <span data-ttu-id="d416e-135">Répétez les étapes 1 à 7 pour déployer le projet EAIOrchestration.</span><span class="sxs-lookup"><span data-stu-id="d416e-135">Repeat steps 1 through 7 to deploy the EAIOrchestration project.</span></span>  
  
## <a name="what-did-i-just-do"></a><span data-ttu-id="d416e-136">Actions effectuées</span><span class="sxs-lookup"><span data-stu-id="d416e-136">What did I just do?</span></span>  
 <span data-ttu-id="d416e-137">Au cours de cette étape, vous avez déployé les projets EAISchemas et EAIOrchestration.</span><span class="sxs-lookup"><span data-stu-id="d416e-137">In this step, you deployed the EAISchemas and EAIOrchestration projects.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="d416e-138">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="d416e-138">Next Steps</span></span>  
 <span data-ttu-id="d416e-139">Vous allez créer les ports physiques et les lier aux ports logiques de l'orchestration.</span><span class="sxs-lookup"><span data-stu-id="d416e-139">You create the physical ports, and bind them to the logical ports of the orchestration.</span></span>  
  
 <span data-ttu-id="d416e-140">[Étape 2 : Configurer et démarrer l’Application](../core/step-2-configure-and-start-the-application1.md) </span><span class="sxs-lookup"><span data-stu-id="d416e-140">[Step 2: Configure and Start the Application](../core/step-2-configure-and-start-the-application1.md) </span></span>  
 [<span data-ttu-id="d416e-141">Étape 3 : Tester la solution</span><span class="sxs-lookup"><span data-stu-id="d416e-141">Step 3: Test the Solution</span></span>](../core/step-3-test-the-solution2.md)
