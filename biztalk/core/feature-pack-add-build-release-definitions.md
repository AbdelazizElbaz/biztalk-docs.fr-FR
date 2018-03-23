---
title: 'Étape 3 : créer les définitions de build et de version | Documents Microsoft'
description: Dans VSTS, créez une définition de build pour générer les projets de votre git ou le référentiel TFS, puis créer une définition de mise en production pour déployer l’application BizTalk Server
ms.custom: ''
ms.date: 11/20/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5ce84071fbc105fd9faddd794792273aae2e76b9
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/23/2018
---
# <a name="step-3-create-the-build-and-release-definition"></a><span data-ttu-id="dd3e0-103">Étape 3 : Créer la version et définition de version</span><span class="sxs-lookup"><span data-stu-id="dd3e0-103">Step 3: Create the build and release definition</span></span>

<span data-ttu-id="dd3e0-104">Les définitions de build et de mise en production sont des tâches de Visual Studio Team Services et probablement doivent être effectuées que par un administrateur de VSTS. La définition de build génère votre projet au sein de votre référentiel git et les définitions de mise en production déploie sur votre environnement BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="dd3e0-104">The build and release definitions are Visual Studio Team Services tasks, and should probably be done by a VSTS admin. The build definition builds your project within your git repository, and the release definitions deploys it to your BizTalk Server environment.</span></span> 

## <a name="before-you-begin"></a><span data-ttu-id="dd3e0-105">Avant de commencer</span><span class="sxs-lookup"><span data-stu-id="dd3e0-105">Before you begin</span></span>
<span data-ttu-id="dd3e0-106">Complète [étape 2 : jeton de VSTS de créer et installer l’agent](feature-pack-create-vsts-token.md).</span><span class="sxs-lookup"><span data-stu-id="dd3e0-106">Complete [Step 2 - Create VSTS token and install agent](feature-pack-create-vsts-token.md).</span></span>

## <a name="add-the-build-tasks"></a><span data-ttu-id="dd3e0-107">Ajouter les tâches de génération</span><span class="sxs-lookup"><span data-stu-id="dd3e0-107">Add the Build tasks</span></span>
1. <span data-ttu-id="dd3e0-108">Dans votre projet, sélectionnez **créer et libérer**.</span><span class="sxs-lookup"><span data-stu-id="dd3e0-108">In your project, select **Build and release**.</span></span> <span data-ttu-id="dd3e0-109">L’onglet de Builds s’ouvre.</span><span class="sxs-lookup"><span data-stu-id="dd3e0-109">The Builds tab opens.</span></span> <span data-ttu-id="dd3e0-110">Créer un **nouveau** définition :</span><span class="sxs-lookup"><span data-stu-id="dd3e0-110">Create a **New** definition:</span></span>

    ![Nouvelle définition de build](../core/media/vsts-new-definition.png)

2. <span data-ttu-id="dd3e0-112">Sélectionnez le **vide** modèle, puis sélectionnez **appliquer**:</span><span class="sxs-lookup"><span data-stu-id="dd3e0-112">Select the **Empty** template, and select **Apply**:</span></span>  

    ![Sélectionner un modèle vide](../core/media/vsts-emtpy-template.png)
 
3. <span data-ttu-id="dd3e0-114">Définir le **file d’attente de l’Agent** par défaut :</span><span class="sxs-lookup"><span data-stu-id="dd3e0-114">Set the **Agent Queue** to Default:</span></span> 

    ![Choisissez la file d’attente par défaut](../core/media/vsts-select-agent-queue.png)

4. <span data-ttu-id="dd3e0-116">Dans **Phase 1**, ajoutez une tâche, sélectionnez **Visual Studio Build**, puis sélectionnez **ajouter**:</span><span class="sxs-lookup"><span data-stu-id="dd3e0-116">In **Phase 1**, add a task, select **Visual Studio Build**, and select **Add**:</span></span>

    ![Ajouter la que tâche de génération de Visual Studio](../core/media/vsts-add-visual-studio-task.png)

5. <span data-ttu-id="dd3e0-118">Cliquez sur la tâche de génération de Visual Studio vous venez d’ajouter et définissez les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="dd3e0-118">Click the Visual Studio Build task you just added, and set the following properties:</span></span>  

    | <span data-ttu-id="dd3e0-119">Propriété</span><span class="sxs-lookup"><span data-stu-id="dd3e0-119">Property</span></span> | <span data-ttu-id="dd3e0-120">La valeur</span><span class="sxs-lookup"><span data-stu-id="dd3e0-120">Set to</span></span> |
    | --- | --- | 
    | <span data-ttu-id="dd3e0-121">Nom complet</span><span class="sxs-lookup"><span data-stu-id="dd3e0-121">Display name</span></span> | <span data-ttu-id="dd3e0-122">*Votre_nom_de_projet* générer solution \*\*\*.sln</span><span class="sxs-lookup"><span data-stu-id="dd3e0-122">*YourProjectName* Build solution \*\*\*.sln</span></span> | 
    | <span data-ttu-id="dd3e0-123">Version de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="dd3e0-123">Visual Studio version</span></span> | <span data-ttu-id="dd3e0-124">Visual Studio 2015</span><span class="sxs-lookup"><span data-stu-id="dd3e0-124">Visual Studio 2015</span></span> | 
    | <span data-ttu-id="dd3e0-125">Architecture de MSBuild</span><span class="sxs-lookup"><span data-stu-id="dd3e0-125">MSBuild Architecture</span></span> | <span data-ttu-id="dd3e0-126">MSBuild x86</span><span class="sxs-lookup"><span data-stu-id="dd3e0-126">MSBuild x86</span></span> | 

6. <span data-ttu-id="dd3e0-127">Dans **Phase 1**, ajoutez une tâche, sélectionnez **publier des artefacts de Build**, puis sélectionnez **ajouter**:</span><span class="sxs-lookup"><span data-stu-id="dd3e0-127">In **Phase 1**, add a task, select **Publish Build Artifacts**, and select **Add**:</span></span> 

    ![Ajouter la que tâche de génération de Visual Studio](../core/media/vsts-add-publish-build-task.png)

7. <span data-ttu-id="dd3e0-129">Sélectionnez le **publier un artefact** de tâches, puis entrez votre choix **nom d’affichage**.</span><span class="sxs-lookup"><span data-stu-id="dd3e0-129">Select the **Publish Artifact** task, and enter your preferred **Display name**.</span></span> <span data-ttu-id="dd3e0-130">Pour **chemin d’accès à la publication**, sélectionnez le **...**  affiché, puis choisissez le dossier de projet d’application (par exemple, appProjectHelloWorld).</span><span class="sxs-lookup"><span data-stu-id="dd3e0-130">For **Path to publish**, select the **...**  button, and choose the application project folder (e.g. appProjectHelloWorld).</span></span> <span data-ttu-id="dd3e0-131">Sélectionnez **OK**.</span><span class="sxs-lookup"><span data-stu-id="dd3e0-131">Select **OK**.</span></span>

8. <span data-ttu-id="dd3e0-132">Le **nom de l’objet** peut être comme vous le souhaitez.</span><span class="sxs-lookup"><span data-stu-id="dd3e0-132">The **Artifact Name** can be anything you want.</span></span> <span data-ttu-id="dd3e0-133">Sélectionnez **enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="dd3e0-133">Select **Save**.</span></span> 

9. <span data-ttu-id="dd3e0-134">Accédez à **déclencheurs**et définissez la **déclencher état** à **activé**:</span><span class="sxs-lookup"><span data-stu-id="dd3e0-134">Go to **Triggers**, and set the **Trigger status** to **Enabled**:</span></span>  

    ![Ajouter la que tâche de génération de Visual Studio](../core/media/vsts-continuous-integration.png)

10. <span data-ttu-id="dd3e0-136">**Enregistrer et de file d’attente** pour tester votre définition de build.</span><span class="sxs-lookup"><span data-stu-id="dd3e0-136">**Save & Queue** to test your build definition.</span></span> <span data-ttu-id="dd3e0-137">Lorsque vous la file d’attente, vous êtes invité à entrer votre branche et de la file d’attente de l’agent.</span><span class="sxs-lookup"><span data-stu-id="dd3e0-137">When you queue, you are prompted for the agent queue and your branch.</span></span> <span data-ttu-id="dd3e0-138">Sélectionnez le **par défaut** agent file d’attente et choisissez votre branche.</span><span class="sxs-lookup"><span data-stu-id="dd3e0-138">Select the **Default** agent queue, and choose your branch.</span></span> <span data-ttu-id="dd3e0-139">Sélectionnez **file d’attente**.</span><span class="sxs-lookup"><span data-stu-id="dd3e0-139">Select **Queue**.</span></span>  

11. <span data-ttu-id="dd3e0-140">Une nouvelle build est démarrée, et vous pouvez le sélectionner pour vérifier la réussite ou l’échec.</span><span class="sxs-lookup"><span data-stu-id="dd3e0-140">A new build is started, and you can select it to check for a success or failure.</span></span> 

## <a name="add-the-release-tasks"></a><span data-ttu-id="dd3e0-141">Ajoutez les tâches de mise en production</span><span class="sxs-lookup"><span data-stu-id="dd3e0-141">Add the release tasks</span></span>

<span data-ttu-id="dd3e0-142">Lorsque la build réussit, la définition de la mise en production déploie votre application sur votre serveur BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="dd3e0-142">When the build succeeds, the release definition deploys your application to your BizTalk Server.</span></span> 

1. <span data-ttu-id="dd3e0-143">Sélectionnez le **versions** onglet, sélectionnez **nouvelle définition**.</span><span class="sxs-lookup"><span data-stu-id="dd3e0-143">Select the **Releases** tab, select **New definition**.</span></span> 

2. <span data-ttu-id="dd3e0-144">Sélectionnez le **vide** modèle, puis sélectionnez **appliquer**:</span><span class="sxs-lookup"><span data-stu-id="dd3e0-144">Select the **Empty** template, and select **Apply**:</span></span>

    ![Ajouter un modèle vide](../core/media/vsts-empty-release-template.png)

3. <span data-ttu-id="dd3e0-146">Modifier la **nom de l’environnement** à **Dev**, ou tout ce que vous voulez appeler.</span><span class="sxs-lookup"><span data-stu-id="dd3e0-146">Change the **Environment name** to **Dev**, or whatever you want to call it.</span></span> 

4. <span data-ttu-id="dd3e0-147">Sélectionnez **ajouter artefact**, sélectionnez votre projet, votre définition de build, puis sélectionnez **ajouter**:</span><span class="sxs-lookup"><span data-stu-id="dd3e0-147">Select **Add artifact**, select your project, your build definition, and select **Add**:</span></span> 

5. <span data-ttu-id="dd3e0-148">Accédez à la **tâches** onglet, ajoutez une nouvelle tâche :</span><span class="sxs-lookup"><span data-stu-id="dd3e0-148">Go to the **Tasks** tab, add a new task:</span></span> 

    ![Ajouter une tâche de mise en production](../core/media/vsts-new-release-tasks.png)

6. <span data-ttu-id="dd3e0-150">Dans la liste, filtrer les résultats, sélectionnez le **déploiement d’Application BizTalk Server** de tâches, puis sélectionnez **ajouter**:</span><span class="sxs-lookup"><span data-stu-id="dd3e0-150">From the list, filter the results, select the **BizTalk Server Application Deployment** task, and select **Add**:</span></span>  

    ![Ajouter la tâche de déploiement BizTalk](../core/media/vsts-biztalk-application-deployment-task.png)

    <span data-ttu-id="dd3e0-152">Si **déploiement d’Application BizTalk Server** ins't dans la liste, puis installez-le à [déployer l’Application BizTalk](https://marketplace.visualstudio.com/items?itemName=ms-biztalk.deploy-biztalk-application).</span><span class="sxs-lookup"><span data-stu-id="dd3e0-152">If **BizTalk Server Application Deployment** ins't listed, then install it at [Deploy BizTalk Application](https://marketplace.visualstudio.com/items?itemName=ms-biztalk.deploy-biztalk-application).</span></span>

7. <span data-ttu-id="dd3e0-153">Sélectionnez le **déployer** , entrez les valeurs et de la tâche :</span><span class="sxs-lookup"><span data-stu-id="dd3e0-153">Select the **Deploy** task, and enter the values:</span></span> 

    <span data-ttu-id="dd3e0-154">**Nom de l’opération**: les options disponibles : \* **créer la nouvelle Application BizTalk**: déploie une nouvelle application.</span><span class="sxs-lookup"><span data-stu-id="dd3e0-154">**Operation Name**: Your options: \* **Create new BizTalk Application**: Deploys a new application.</span></span> <span data-ttu-id="dd3e0-155">Si l’application existe déjà, il désinstalle les applications actuelles (point) et installe la nouvelle application.</span><span class="sxs-lookup"><span data-stu-id="dd3e0-155">If the application already exists, it uninstalls the current applications (full stop), and installs the new application.</span></span> <span data-ttu-id="dd3e0-156">Si l’intégration continue est activée, elle automatiquement redéploie l’application lorsqu’elle est mise à jour dans le référentiel.</span><span class="sxs-lookup"><span data-stu-id="dd3e0-156">If continuous integration is enabled, it automatically redeploys the application when it is updated in the repository.</span></span> 
        <span data-ttu-id="dd3e0-157">\* **Mettre à jour une Application BizTalk existante**: ajoute des modifications, tels que des schémas à une application déjà en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="dd3e0-157">\* **Update an existing BizTalk Application**: Appends changes, such as schemas, to an already running application.</span></span> <span data-ttu-id="dd3e0-158">Il ne nécessite pas un redéploiement complet de l’application.</span><span class="sxs-lookup"><span data-stu-id="dd3e0-158">It does not require a full redeploy of the application.</span></span>
        <span data-ttu-id="dd3e0-159">\* **Installer l’Application BizTalk Server**: [installer les applications](../core/how-to-install-a-biztalk-application.md), et que vous entrez le nom d’ordinateur de gestion BizTalk et le chemin d’accès du package de déploiement.</span><span class="sxs-lookup"><span data-stu-id="dd3e0-159">\* **Install BizTalk Server Application**: [Install the applications](../core/how-to-install-a-biztalk-application.md), and you enter the BizTalk management computer name, and the deployment package path.</span></span>

        ![Deploy operations](../core/media/vsts-deploy-operations.png)

    <span data-ttu-id="dd3e0-160">**Nom de l’application**: le texte que vous entrez sera le nom de l’application dans l’Administration de BizTalk.</span><span class="sxs-lookup"><span data-stu-id="dd3e0-160">**Application Name**: The text you enter will be the application name in BizTalk Administration.</span></span> <span data-ttu-id="dd3e0-161">Faire **pas** Entrez BizTalk Application 1.</span><span class="sxs-lookup"><span data-stu-id="dd3e0-161">Do **not** enter BizTalk Application 1.</span></span>

    <span data-ttu-id="dd3e0-162">**Package de déploiement**: sélectionnez le fichier zip dans votre projet d’application, puis sélectionnez **OK**.</span><span class="sxs-lookup"><span data-stu-id="dd3e0-162">**Deployment package**: Select the zip file to your application project, and select **OK**.</span></span> 

8. <span data-ttu-id="dd3e0-163">Sélectionnez le **phase Agent** tâche.</span><span class="sxs-lookup"><span data-stu-id="dd3e0-163">Select the **Agent phase** task.</span></span> <span data-ttu-id="dd3e0-164">Sélectionnez le **par défaut** file d’attente de l’Agent.</span><span class="sxs-lookup"><span data-stu-id="dd3e0-164">Select the **Default** Agent queue.</span></span> <span data-ttu-id="dd3e0-165">**Enregistrer** vos modifications.</span><span class="sxs-lookup"><span data-stu-id="dd3e0-165">**Save** your changes.</span></span>

9. <span data-ttu-id="dd3e0-166">Sélectionnez **Release** > **créer version**:</span><span class="sxs-lookup"><span data-stu-id="dd3e0-166">Select **Release** > **Create release**:</span></span>  

    ![La version finale, créez la mise en production](../core/media/vsts-create-release.png)

10. <span data-ttu-id="dd3e0-168">Sélectionnez **file d’attente**.</span><span class="sxs-lookup"><span data-stu-id="dd3e0-168">Select **Queue**.</span></span> <span data-ttu-id="dd3e0-169">Vérifiez l’état en cliquant sur le lien mise en production.</span><span class="sxs-lookup"><span data-stu-id="dd3e0-169">Check the status by clicking the release link.</span></span> <span data-ttu-id="dd3e0-170">En cas d’échec, l’erreur s’affiche.</span><span class="sxs-lookup"><span data-stu-id="dd3e0-170">If it fails, the error displays.</span></span> <span data-ttu-id="dd3e0-171">Si elle réussit, l’application est ajoutée à la console Administration de BizTalk.</span><span class="sxs-lookup"><span data-stu-id="dd3e0-171">If it succeeds, the application is added to the BizTalk Administration console.</span></span> 

## <a name="what-you-did"></a><span data-ttu-id="dd3e0-172">Ce que vous avez fait</span><span class="sxs-lookup"><span data-stu-id="dd3e0-172">What you did</span></span>

<span data-ttu-id="dd3e0-173">Dans VSTS, vous avez créé une définition de build qui génère votre application dans Git ou Team Foundation Version Control (que vous avez choisi).</span><span class="sxs-lookup"><span data-stu-id="dd3e0-173">In VSTS, you created a build definition that builds your application within Git or Team Foundation Version Control (whatever you chose).</span></span> <span data-ttu-id="dd3e0-174">Lorsque des modifications sont apportées dans le contrôle de code source, les modifications sont détectées automatiquement et vous pouvez les envoyer.</span><span class="sxs-lookup"><span data-stu-id="dd3e0-174">When changes are made within the source control, the changes are automatically detected, and you can push them.</span></span> <span data-ttu-id="dd3e0-175">Une fois la build terminée, vous avez créé une définition de mise en production qui déploie l’application à BizTalk Server, que vous pouvez visualiser dans Administration de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="dd3e0-175">After the build completes, you created a release definition that deploys the application to BizTalk Server, which you can see in BizTalk Server Administration.</span></span> 

## <a name="next-step"></a><span data-ttu-id="dd3e0-176">Étape suivante</span><span class="sxs-lookup"><span data-stu-id="dd3e0-176">Next step</span></span>
<span data-ttu-id="dd3e0-177">À ce stade, vous avez terminé.</span><span class="sxs-lookup"><span data-stu-id="dd3e0-177">At this step, you're done.</span></span> <span data-ttu-id="dd3e0-178">Si vous préférez, vous pouvez créer des jetons de l’environnement dans votre fichier de liaison XML BizTalk et créer des variables dans VSTS qui correspondent aux jetons de l’environnement.</span><span class="sxs-lookup"><span data-stu-id="dd3e0-178">If you prefer, you can create environmental tokens within your BizTalk XML binding file, and create variables within VSTS that match the environmental tokens.</span></span> <span data-ttu-id="dd3e0-179">Consultez [configurer des jetons de l’environnement et les variables](configure-environmental-tokens-and-variables-for-automatic-deployment.md) pour plus d’informations.</span><span class="sxs-lookup"><span data-stu-id="dd3e0-179">See [Configure environmental tokens and variables](configure-environmental-tokens-and-variables-for-automatic-deployment.md) for the details.</span></span> 