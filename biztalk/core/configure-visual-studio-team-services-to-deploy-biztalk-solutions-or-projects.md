---
redirect_url: /biztalk/core/feature-pack-add-build-release-definitions/
redirect_document_id: True
ROBOTS: NOINDEX
title: "Configurer Visual Studio Team Services pour déployer des solutions BizTalk Server ou des projets | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2555712a-dfe4-420e-9a61-1d1a6d98c322
caps.latest.revision: "6"
author: tordgladnordahl
ms.author: tonordah
manager: anneta
ms.openlocfilehash: 95d8e9fc274793471335fc03bc38c82c1b3e3469
ms.sourcegitcommit: a0165ec2f1e8b58545638666b7bfa2bf440036fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="configure-visual-studio-team-services-to-deploy-biztalk-server-solutions-or-projects"></a><span data-ttu-id="d2654-102">Configurer Visual Studio Team Services pour déployer des solutions BizTalk Server ou des projets</span><span class="sxs-lookup"><span data-stu-id="d2654-102">Configure Visual Studio Team Services to deploy BizTalk Server solutions or projects</span></span>
<span data-ttu-id="d2654-103">Configurer VSTS pour déployer automatiquement [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] projets.</span><span class="sxs-lookup"><span data-stu-id="d2654-103">Set up VSTS to automatically deploy [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] projects.</span></span> 

<span data-ttu-id="d2654-104">**En commençant par [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] [!INCLUDE[featurepack1](../includes/featurepack1.md)]** , vous pouvez automatiquement générer votre [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] solutions à l’aide de Visual Studio Team Services (VSTS).</span><span class="sxs-lookup"><span data-stu-id="d2654-104">**Starting with [!INCLUDE[bts2016_md](../includes/bts2016-md.md)] [!INCLUDE[featurepack1](../includes/featurepack1.md)]**, you can automatically build your [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] solutions using Visual Studio Team Services (VSTS).</span></span> 

<span data-ttu-id="d2654-105">Cette rubrique vous montre comment installer et configurer Visual Studio Team Services (VSTS) pour utiliser le déploiement automatique de BizTalk.</span><span class="sxs-lookup"><span data-stu-id="d2654-105">This topic shows you how to set up and configure Visual Studio Team Service (VSTS) to use automatic deployment for BizTalk.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="d2654-106">L’agent VSTS ne peut être installé que sur un [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] dans le groupe.</span><span class="sxs-lookup"><span data-stu-id="d2654-106">The VSTS agent can only be installed on one [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] in the group.</span></span> 

## <a name="prerequisites"></a><span data-ttu-id="d2654-107">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="d2654-107">Prerequisites</span></span>

* <span data-ttu-id="d2654-108">Installer [Feature Pack 1](https://www.microsoft.com/download/details.aspx?id=55100) sur votre[!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d2654-108">Install [Feature Pack 1](https://www.microsoft.com/download/details.aspx?id=55100) on your [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]</span></span>
* <span data-ttu-id="d2654-109">Certains expérience et la base de connaissances avec la création et l’utilisation avec les définitions de VSTS.</span><span class="sxs-lookup"><span data-stu-id="d2654-109">Some experience and knowledge with creating and working with definitions in VSTS.</span></span> <span data-ttu-id="d2654-110">Si vous êtes débutant VSTS, il peut s’agir de bonnes ressources :</span><span class="sxs-lookup"><span data-stu-id="d2654-110">If you're brand new to VSTS, these may be good resources:</span></span> 

  [<span data-ttu-id="d2654-111">Vue d’ensemble de Visual Studio Team Services</span><span class="sxs-lookup"><span data-stu-id="d2654-111">Visual Studio Team Services overview</span></span>](https://www.visualstudio.com/docs/overview)  
  [<span data-ttu-id="d2654-112">L’élément de configuration/CD pour les internautes novices</span><span class="sxs-lookup"><span data-stu-id="d2654-112">CI/CD for newbies</span></span>](https://www.visualstudio.com/docs/build/get-started/ci-cd-part-1)
  

## <a name="create-a-vsts-account-and-create-a-definition"></a><span data-ttu-id="d2654-113">Créer un compte VSTS et créer une définition</span><span class="sxs-lookup"><span data-stu-id="d2654-113">Create a VSTS account and create a definition</span></span>

1. <span data-ttu-id="d2654-114">Dans un navigateur web, accédez à votre [le profil Visual Studio online](https://app.vsaex.visualstudio.com/go/profile), connectez-vous, puis sélectionnez un **créer nouveau compte**:</span><span class="sxs-lookup"><span data-stu-id="d2654-114">In a web browser, go to your [Visual Studio online profile](https://app.vsaex.visualstudio.com/go/profile), sign in, and select a **Create new account**:</span></span>

    ![Créer un nouveau compte](../core/media/create-a-new-account.png)

2. <span data-ttu-id="d2654-116">Entrez un nom pour le compte de votre référentiel de code source par défaut et sélectionnez **continuer**:</span><span class="sxs-lookup"><span data-stu-id="d2654-116">Enter a name for the account, select your preferred source code repository, and select **Continue**:</span></span>

    ![Créez un nouveau projet](../core/media/create-a-new-project.png)

3. <span data-ttu-id="d2654-118">Votre nouveau compte est créé et un site même `https://YourAccountName.visualstudio.com/MyFirstProject` s’ouvre.</span><span class="sxs-lookup"><span data-stu-id="d2654-118">Your new account is created, and a site similar to `https://YourAccountName.visualstudio.com/MyFirstProject` opens.</span></span>
    
4. <span data-ttu-id="d2654-119">Installer le [service de déployer l’Application BizTalk](https://marketplace.visualstudio.com/items?itemName=ms-biztalk.deploy-biztalk-application) pour le compte que vous venez de créer.</span><span class="sxs-lookup"><span data-stu-id="d2654-119">Install the [Deploy BizTalk Application service](https://marketplace.visualstudio.com/items?itemName=ms-biztalk.deploy-biztalk-application) to the account you just created.</span></span>

    ![Nouvelle version de build](../core/media/build-new-release.png)

5. <span data-ttu-id="d2654-121">Vous pouvez obtenir des invites.</span><span class="sxs-lookup"><span data-stu-id="d2654-121">You may get some prompts.</span></span> <span data-ttu-id="d2654-122">Confirmer pour continuer.</span><span class="sxs-lookup"><span data-stu-id="d2654-122">Confirm to continue.</span></span> <span data-ttu-id="d2654-123">Assurez-vous que vous êtes connecté à votre projet dans VSTS.</span><span class="sxs-lookup"><span data-stu-id="d2654-123">Be sure you're signed in to your project in VSTS.</span></span>

6. <span data-ttu-id="d2654-124">Sélectionnez **Build et version**et créer un **nouveau** définition de build :</span><span class="sxs-lookup"><span data-stu-id="d2654-124">Select **Build and release**, and create a **New** build definition:</span></span>

    ![Sélectionner la Build et mise en production](../core/media/select-build-and-release.png)

    > [!TIP]
    > <span data-ttu-id="d2654-126">Vérifiez que vous êtes à `https://YourAccountName.visualstudio.com/MyFirstProject`.</span><span class="sxs-lookup"><span data-stu-id="d2654-126">Be sure you're at `https://YourAccountName.visualstudio.com/MyFirstProject`.</span></span> <span data-ttu-id="d2654-127">Dans le cas contraire, le **nouveau** ou **nouvelle définition** boutons ne peuvent pas être il.</span><span class="sxs-lookup"><span data-stu-id="d2654-127">Otherwise, the **New** or **New definition** buttons may not be there.</span></span> 
    
7. <span data-ttu-id="d2654-128">Sélectionnez le **Visual Studio** modèle, puis sélectionnez **suivant**:</span><span class="sxs-lookup"><span data-stu-id="d2654-128">Select the **Visual Studio** template, and select **Next**:</span></span>

    ![Sélectionnez visual studio, cliquez sur Suivant](../core/media/select-visual-studio-and-click-next.png)

8. <span data-ttu-id="d2654-130">Passez en revue vos paramètres, puis sélectionnez **créer**.</span><span class="sxs-lookup"><span data-stu-id="d2654-130">Review your settings, and select **Create**.</span></span>

9. <span data-ttu-id="d2654-131">Supprimer les étapes que vous n’avez pas besoin.</span><span class="sxs-lookup"><span data-stu-id="d2654-131">Delete the steps you don't need.</span></span> <span data-ttu-id="d2654-132">Pour ce didacticiel, vous pouvez supprimer les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="d2654-132">For this tutorial, you can delete the following:</span></span> 
* <span data-ttu-id="d2654-133">Restauration de NuGet</span><span class="sxs-lookup"><span data-stu-id="d2654-133">NuGet Restore</span></span>
* <span data-ttu-id="d2654-134">Assemblys de test</span><span class="sxs-lookup"><span data-stu-id="d2654-134">Test assemblies</span></span>
* <span data-ttu-id="d2654-135">Publier le chemin d’accès des symboles</span><span class="sxs-lookup"><span data-stu-id="d2654-135">Publish symbols path</span></span> 

    ![Supprimer des étapes inutiles](../core/media/delete-steps-not-needed.png)

10. <span data-ttu-id="d2654-137">**Facultatif**.</span><span class="sxs-lookup"><span data-stu-id="d2654-137">**Optional**.</span></span> <span data-ttu-id="d2654-138">Si vous souhaitez activer l’intégration continue (CI), sélectionnez **déclencheurs** dans le menu et vérifiez **l’intégration continue (CI)**.</span><span class="sxs-lookup"><span data-stu-id="d2654-138">If you want to enable Continous Integration (CI), select **Triggers** in the menu, and check **Continous integration (CI)**.</span></span>

<span data-ttu-id="d2654-139">Ensuite, installez l’agent sur votre [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d2654-139">Next, install the agent on your [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)].</span></span> 

## <a name="install-the-agent"></a><span data-ttu-id="d2654-140">Installer l’Agent</span><span class="sxs-lookup"><span data-stu-id="d2654-140">Install the Agent</span></span>

<span data-ttu-id="d2654-141">Pour la solution fonctionne, activer un Agent Windows privé sur votre ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="d2654-141">For the solution to work, enable a private Windows Agent on your local machine.</span></span> <span data-ttu-id="d2654-142">N’oubliez pas, **l’agent doit être installé que sur un seul [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] dans le groupe**.</span><span class="sxs-lookup"><span data-stu-id="d2654-142">Remember, **the agent must be installed on only one [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] in the group**.</span></span> 

1. <span data-ttu-id="d2654-143">Dans la définition, sélectionnez le **général** onglet (en haut).</span><span class="sxs-lookup"><span data-stu-id="d2654-143">In your definition, select the **General** tab (at the top).</span></span>
2. <span data-ttu-id="d2654-144">Pour le **file d’attente de l’agent par défaut** propriété, sélectionnez le **par défaut** agent à partir de la liste.</span><span class="sxs-lookup"><span data-stu-id="d2654-144">For the **Default agent queue** property, select the **Default** agent from the list.</span></span> 
3. <span data-ttu-id="d2654-145">Sélectionnez **gérer** à côté du **file d’attente de l’agent par défaut** propriété.</span><span class="sxs-lookup"><span data-stu-id="d2654-145">Select **Manage** next to the **Default agent queue** property.</span></span> <span data-ttu-id="d2654-146">Un nouvel onglet de navigateur s’ouvre.</span><span class="sxs-lookup"><span data-stu-id="d2654-146">A new browser tab opens.</span></span>

    ![Créer le nouvel agent de gestion](../core/media/create-new-management-agent.png)

4. <span data-ttu-id="d2654-148">Dans le volet gauche, la file d’attente par défaut est sélectionné.</span><span class="sxs-lookup"><span data-stu-id="d2654-148">In the left pane, the Default queue is selected.</span></span> <span data-ttu-id="d2654-149">Si un agent est déjà répertorié, en ligne, vous avez terminé.</span><span class="sxs-lookup"><span data-stu-id="d2654-149">If an agent is already listed, and online, then you're done.</span></span> <span data-ttu-id="d2654-150">Vous disposez d’un agent installé et en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="d2654-150">You have an agent installed, and running.</span></span> 

    <span data-ttu-id="d2654-151">Si un agent n’est pas répertorié, puis sélectionnez **agent de téléchargement**et continuer l’installation sur votre [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d2654-151">If an agent is not listed, then select **Download agent**, and continue with the installation on your [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="d2654-152">**Accédez à [déployer un agent sur Windows](https://www.visualstudio.com/docs/build/actions/agents/v2-windows) pour connaître la procédure** pour installer l’agent et démarrer un agent.</span><span class="sxs-lookup"><span data-stu-id="d2654-152">**Go to [Deploy an agent on Windows](https://www.visualstudio.com/docs/build/actions/agents/v2-windows) for the complete steps** to install the agent, and start an agent.</span></span> 

    > [!IMPORTANT]
    > <span data-ttu-id="d2654-153">Suivez les étapes indiquées dans [déployer un agent sur Windows](https://www.visualstudio.com/docs/build/actions/agents/v2-windows).</span><span class="sxs-lookup"><span data-stu-id="d2654-153">Follow all the steps at [Deploy an agent on Windows](https://www.visualstudio.com/docs/build/actions/agents/v2-windows).</span></span> <span data-ttu-id="d2654-154">N’ignorez pas cette étape.</span><span class="sxs-lookup"><span data-stu-id="d2654-154">Do not skip this step.</span></span> 

5. <span data-ttu-id="d2654-155">Avec l’agent par défaut **Online**, revenez à la **général** onglet dans votre définition, puis confirmez **par défaut** est sélectionné pour le **file d’attente de l’agent par défaut**.</span><span class="sxs-lookup"><span data-stu-id="d2654-155">With the default agent **Online**, go back to the **General** tab in your definition, and confirm **Default** is selected for the **Default agent queue**.</span></span>
6. <span data-ttu-id="d2654-156">**Enregistrer** et **nouvelle build en file d’attente**.</span><span class="sxs-lookup"><span data-stu-id="d2654-156">**Save** and **Queue new build**.</span></span>

<span data-ttu-id="d2654-157">Ensuite, créez la définition de déploiement d’Application BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="d2654-157">Next, create the BizTalk Server Application Deployment definition.</span></span>

## <a name="create-the-biztalk-deployment-definition"></a><span data-ttu-id="d2654-158">Créer la définition de déploiement BizTalk</span><span class="sxs-lookup"><span data-stu-id="d2654-158">Create the BizTalk deployment definition</span></span>

1. <span data-ttu-id="d2654-159">Sélectionnez le **génère** onglet, sélectionnez **toutes les définitions de**, puis sélectionnez **nouveau**:</span><span class="sxs-lookup"><span data-stu-id="d2654-159">Select the **Builds** tab, select **All Definitions**, and select **New**:</span></span>

    ![Créer la définition de la nouvelle version](../core/media/create-new-release-defintion.png)

2. <span data-ttu-id="d2654-161">Sélectionnez le **vide** modèle, puis sélectionnez **suivant**:</span><span class="sxs-lookup"><span data-stu-id="d2654-161">Select the **Empty** template, and select **Next**:</span></span>

    ![Créer la nouvelle définition d’un modèle vide](../core/media/create-new-defintion-from-an-empty-template.png)

3. <span data-ttu-id="d2654-163">Sélectionnez votre **référentiel** source et **branche** pour la définition.</span><span class="sxs-lookup"><span data-stu-id="d2654-163">Select your **Repository** source and **Branch** for the definition.</span></span>
4. <span data-ttu-id="d2654-164">**Facultatif**.</span><span class="sxs-lookup"><span data-stu-id="d2654-164">**Optional**.</span></span> <span data-ttu-id="d2654-165">Sélectionnez **intégration continue**.</span><span class="sxs-lookup"><span data-stu-id="d2654-165">Select **Continous Integration**.</span></span>
5. <span data-ttu-id="d2654-166">Sélectionnez le **par défaut** agent à partir de la liste de la file d’attente, puis sélectionnez **créer**.</span><span class="sxs-lookup"><span data-stu-id="d2654-166">Select the **Default** agent from the queue list, and select **Create**.</span></span>
6. <span data-ttu-id="d2654-167">**Étape de génération ajouter**, sélectionnez le **déploiement d’Application BizTalk Server** de tâches, puis sélectionnez **ajouter**.</span><span class="sxs-lookup"><span data-stu-id="d2654-167">**Add build step**, select the **BizTalk Server Application Deployment** task, and select **Add**.</span></span> <span data-ttu-id="d2654-168">**Fermer** le catalogue de la tâche.</span><span class="sxs-lookup"><span data-stu-id="d2654-168">**Close** the task catalog.</span></span>

    ![Ajouter nouveau déploiement de définition](../core/media/add-new-deploy-definition.png)

7. <span data-ttu-id="d2654-170">Sélectionnez le **nom de l’opération** vous souhaitez utiliser :</span><span class="sxs-lookup"><span data-stu-id="d2654-170">Select the **Operation Name** you want to use:</span></span>
    * <span data-ttu-id="d2654-171">**Créer la nouvelle Application BizTalk** déploie une nouvelle application.</span><span class="sxs-lookup"><span data-stu-id="d2654-171">**Create new BizTalk Application** deploys a new application.</span></span> <span data-ttu-id="d2654-172">Si l’application existe déjà, il désinstalle les applications actuelles (point) et installe la nouvelle application.</span><span class="sxs-lookup"><span data-stu-id="d2654-172">If the application already exsist, it uninstalls the current applications (full stop), and installs the new application.</span></span> <span data-ttu-id="d2654-173">Si l’intégration continue est activée, elle automatiquement redéploie l’application lorsqu’elle est mise à jour dans le référentiel.</span><span class="sxs-lookup"><span data-stu-id="d2654-173">If continous integration is enabled, it automatically redeploys the application when it is updated in the repository.</span></span>
    * <span data-ttu-id="d2654-174">**Mettre à jour une Application BizTalk existant** ajoute des modifications, par exemple **schémas** à une application déjà en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="d2654-174">**Update an exsisting BizTalk Application** appends changes, such as **Schemas** to an already running application.</span></span> <span data-ttu-id="d2654-175">Il ne nécessite pas un redéploiement complet de l’application.</span><span class="sxs-lookup"><span data-stu-id="d2654-175">It does not require a full redeploy of the application.</span></span>
8. <span data-ttu-id="d2654-176">Entrez le **nom de l’Application** dans votre [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] environnement.</span><span class="sxs-lookup"><span data-stu-id="d2654-176">Enter the **Application name** in your [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] environment.</span></span>
9. <span data-ttu-id="d2654-177">Dans **chemin d’accès du package de déploiement**, sélectionnez le chemin d’accès vers le fichier zip dans votre référentiel.</span><span class="sxs-lookup"><span data-stu-id="d2654-177">In **Deployment package path**, select the path to the zip file in your repository.</span></span>
10. <span data-ttu-id="d2654-178">Sélectionnez **déclencheurs** , dans le menu, activez **intégration continue**et sélectionnez le bon **branche** pour la build.</span><span class="sxs-lookup"><span data-stu-id="d2654-178">Select **Triggers** from the menu, enable **Continous Integration**, and select the correct **Branch** for the build.</span></span>
11. <span data-ttu-id="d2654-179">Sélectionnez **enregistrer**:</span><span class="sxs-lookup"><span data-stu-id="d2654-179">Select **Save**:</span></span>

    ![Enregistrer la nouvelle définition de build](../core/media/save-the-new-build-definition.png)

12. <span data-ttu-id="d2654-181">Nommez le nouveau **définition**et définissez le chemin d’accès correct.</span><span class="sxs-lookup"><span data-stu-id="d2654-181">Name the new **Definition**, and set the correct path.</span></span> 
13. <span data-ttu-id="d2654-182">Une fois que la définition est enregistrée, sélectionnez **la nouvelle build en file d’attente**.</span><span class="sxs-lookup"><span data-stu-id="d2654-182">Once the definition is saved, select **Queue the new build**.</span></span> <span data-ttu-id="d2654-183">Ensuite, sélectionnez le **agent file d’attente**et ajouter un commentaire à la validation.</span><span class="sxs-lookup"><span data-stu-id="d2654-183">Then, select the **Queue agent**, and add a comment to the commit.</span></span>
