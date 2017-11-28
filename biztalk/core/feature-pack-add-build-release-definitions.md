---
title: "Étape 3 : créer les définitions de build et de version | Documents Microsoft"
description: "Dans VSTS, créez une définition de build pour générer les projets de votre git ou le référentiel TFS, puis créer une définition de mise en production pour déployer l’application BizTalk Server"
ms.custom: 
ms.date: 11/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: de86d35fd615d8c0f1eee1127804645067c4bf6e
ms.sourcegitcommit: a0165ec2f1e8b58545638666b7bfa2bf440036fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="step-3-create-the-build-and-release-definition"></a><span data-ttu-id="7824e-103">Étape 3 : Créer la version et définition de version</span><span class="sxs-lookup"><span data-stu-id="7824e-103">Step 3: Create the build and release definition</span></span>

<span data-ttu-id="7824e-104">Les définitions de build et de mise en production sont des tâches de Visual Studio Team Services et probablement doivent être effectuées que par un administrateur de VSTS. La définition de build génère votre projet au sein de votre référentiel git et les définitions de mise en production déploie sur votre environnement BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="7824e-104">The build and release definitions are Visual Studio Team Services tasks, and should probably be done by a VSTS admin. The build definition builds your project within your git repository, and the release definitions deploys it to your BizTalk Server environment.</span></span> 

## <a name="add-the-build-tasks"></a><span data-ttu-id="7824e-105">Ajouter les tâches de génération</span><span class="sxs-lookup"><span data-stu-id="7824e-105">Add the Build tasks</span></span>
1. <span data-ttu-id="7824e-106">Dans votre projet, sélectionnez **créer et libérer**.</span><span class="sxs-lookup"><span data-stu-id="7824e-106">In your project, select **Build and release**.</span></span> <span data-ttu-id="7824e-107">L’onglet de Builds s’ouvre.</span><span class="sxs-lookup"><span data-stu-id="7824e-107">The Builds tab opens.</span></span> <span data-ttu-id="7824e-108">Créer un **nouveau** définition :</span><span class="sxs-lookup"><span data-stu-id="7824e-108">Create a **New** definition:</span></span>

    ![Nouvelle définition de build](../core/media/vsts-new-definition.png)

2. <span data-ttu-id="7824e-110">Sélectionnez le **vide** modèle, puis sélectionnez **appliquer**:</span><span class="sxs-lookup"><span data-stu-id="7824e-110">Select the **Empty** template, and select **Apply**:</span></span>  

    ![Sélectionner un modèle vide](../core/media/vsts-emtpy-template.png)
 
3. <span data-ttu-id="7824e-112">Définir le **file d’attente de l’Agent** par défaut :</span><span class="sxs-lookup"><span data-stu-id="7824e-112">Set the **Agent Queue** to Default:</span></span> 

    ![Choisissez la file d’attente par défaut](../core/media/vsts-select-agent-queue.png)

4. <span data-ttu-id="7824e-114">Dans **Phase 1**, ajoutez une tâche, sélectionnez **Visual Studio Build**, puis sélectionnez **ajouter**:</span><span class="sxs-lookup"><span data-stu-id="7824e-114">In **Phase 1**, add a task, select **Visual Studio Build**, and select **Add**:</span></span>

    ![Ajouter la que tâche de génération de Visual Studio](../core/media/vsts-add-visual-studio-task.png)

5. <span data-ttu-id="7824e-116">Cliquez sur la tâche de génération de Visual Studio vous venez d’ajouter et définissez les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="7824e-116">Click the Visual Studio Build task you just added, and set the following properties:</span></span>  

    | <span data-ttu-id="7824e-117">Propriété</span><span class="sxs-lookup"><span data-stu-id="7824e-117">Property</span></span> | <span data-ttu-id="7824e-118">La valeur</span><span class="sxs-lookup"><span data-stu-id="7824e-118">Set to</span></span> |
    | --- | --- | 
    | <span data-ttu-id="7824e-119">Nom complet</span><span class="sxs-lookup"><span data-stu-id="7824e-119">Display name</span></span> | <span data-ttu-id="7824e-120">*Votre_nom_de_projet* générer solution **\*.sln</span><span class="sxs-lookup"><span data-stu-id="7824e-120">*YourProjectName* Build solution **\*.sln</span></span> | 
    | <span data-ttu-id="7824e-121">Version de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="7824e-121">Visual Studio version</span></span> | <span data-ttu-id="7824e-122">Visual Studio 2015</span><span class="sxs-lookup"><span data-stu-id="7824e-122">Visual Studio 2015</span></span> | 
    | <span data-ttu-id="7824e-123">Architecture de MSBuild</span><span class="sxs-lookup"><span data-stu-id="7824e-123">MSBuild Architecture</span></span> | <span data-ttu-id="7824e-124">MSBuild x86</span><span class="sxs-lookup"><span data-stu-id="7824e-124">MSBuild x86</span></span> | 

6. <span data-ttu-id="7824e-125">Dans **Phase 1**, ajoutez une tâche, sélectionnez **publier des artefacts de Build**, puis sélectionnez **ajouter**:</span><span class="sxs-lookup"><span data-stu-id="7824e-125">In **Phase 1**, add a task, select **Publish Build Artifacts**, and select **Add**:</span></span> 

    ![Ajouter la que tâche de génération de Visual Studio](../core/media/vsts-add-publish-build-task.png)

7. <span data-ttu-id="7824e-127">Sélectionnez le **publier un artefact** de tâches, puis entrez votre choix **nom d’affichage**.</span><span class="sxs-lookup"><span data-stu-id="7824e-127">Select the **Publish Artifact** task, and enter your preferred **Display name**.</span></span> <span data-ttu-id="7824e-128">Pour **chemin d’accès à la publication**, sélectionnez le **...**  affiché, puis choisissez le dossier de projet d’application (par exemple, appProjectHelloWorld).</span><span class="sxs-lookup"><span data-stu-id="7824e-128">For **Path to publish**, select the **...**  button, and choose the application project folder (e.g. appProjectHelloWorld).</span></span> <span data-ttu-id="7824e-129">Sélectionnez **OK**.</span><span class="sxs-lookup"><span data-stu-id="7824e-129">Select **OK**.</span></span>

8. <span data-ttu-id="7824e-130">Le **nom de l’objet** peut être comme vous le souhaitez.</span><span class="sxs-lookup"><span data-stu-id="7824e-130">The **Artifact Name** can be anything you want.</span></span> <span data-ttu-id="7824e-131">Sélectionnez **enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="7824e-131">Select **Save**.</span></span> 

9. <span data-ttu-id="7824e-132">Accédez à **déclencheurs**et définissez la **déclencher état** à **activé**:</span><span class="sxs-lookup"><span data-stu-id="7824e-132">Go to **Triggers**, and set the **Trigger status** to **Enabled**:</span></span>  

    ![Ajouter la que tâche de génération de Visual Studio](../core/media/vsts-continuous-integration.png)

10. <span data-ttu-id="7824e-134">**Enregistrer et de file d’attente** pour tester votre définition de build.</span><span class="sxs-lookup"><span data-stu-id="7824e-134">**Save & Queue** to test your build definition.</span></span> <span data-ttu-id="7824e-135">Lorsque vous la file d’attente, vous êtes invité à entrer votre branche et de la file d’attente de l’agent.</span><span class="sxs-lookup"><span data-stu-id="7824e-135">When you queue, you are prompted for the agent queue and your branch.</span></span> <span data-ttu-id="7824e-136">Sélectionnez le **par défaut** agent file d’attente et choisissez votre branche.</span><span class="sxs-lookup"><span data-stu-id="7824e-136">Select the **Default** agent queue, and choose your branch.</span></span> <span data-ttu-id="7824e-137">Sélectionnez **file d’attente**.</span><span class="sxs-lookup"><span data-stu-id="7824e-137">Select **Queue**.</span></span>  

11. <span data-ttu-id="7824e-138">Une nouvelle build est démarrée, et vous pouvez le sélectionner pour vérifier la réussite ou l’échec.</span><span class="sxs-lookup"><span data-stu-id="7824e-138">A new build is started, and you can select it to check for a success or failure.</span></span> 

## <a name="add-the-release-tasks"></a><span data-ttu-id="7824e-139">Ajoutez les tâches de mise en production</span><span class="sxs-lookup"><span data-stu-id="7824e-139">Add the release tasks</span></span>

<span data-ttu-id="7824e-140">Lorsque la build réussit, la définition de la mise en production déploie votre application sur votre serveur BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="7824e-140">When the build succeeds, the release definition deploys your application to your BizTalk Server.</span></span> 

1. <span data-ttu-id="7824e-141">Sélectionnez le **versions** onglet, sélectionnez **nouvelle définition**.</span><span class="sxs-lookup"><span data-stu-id="7824e-141">Select the **Releases** tab, select **New definition**.</span></span> 

2. <span data-ttu-id="7824e-142">Sélectionnez le **vide** modèle, puis sélectionnez **appliquer**:</span><span class="sxs-lookup"><span data-stu-id="7824e-142">Select the **Empty** template, and select **Apply**:</span></span>

    ![Ajouter un modèle vide](../core/media/vsts-empty-release-template.png)

3. <span data-ttu-id="7824e-144">Modifier la **nom de l’environnement** à **Dev**, ou tout ce que vous voulez appeler.</span><span class="sxs-lookup"><span data-stu-id="7824e-144">Change the **Environment name** to **Dev**, or whatever you want to call it.</span></span> 

4. <span data-ttu-id="7824e-145">Sélectionnez **ajouter artefact**, sélectionnez votre projet, votre définition de build, puis sélectionnez **ajouter**:</span><span class="sxs-lookup"><span data-stu-id="7824e-145">Select **Add artifact**, select your project, your build definition, and select **Add**:</span></span> 

5. <span data-ttu-id="7824e-146">Accédez à la **tâches** onglet, ajoutez une nouvelle tâche :</span><span class="sxs-lookup"><span data-stu-id="7824e-146">Go to the **Tasks** tab, add a new task:</span></span> 

    ![Ajouter une tâche de mise en production](../core/media/vsts-new-release-tasks.png)

6. <span data-ttu-id="7824e-148">Dans la liste, filtrer les résultats, sélectionnez le **déploiement d’Application BizTalk Server** de tâches, puis sélectionnez **ajouter**:</span><span class="sxs-lookup"><span data-stu-id="7824e-148">From the list, filter the results, select the **BizTalk Server Application Deployment** task, and select **Add**:</span></span>  

    ![Ajouter la tâche de déploiement BizTalk](../core/media/vsts-biztalk-application-deployment-task.png)

    <span data-ttu-id="7824e-150">Si **déploiement d’Application BizTalk Server** ins't dans la liste, puis installez-le à [déployer l’Application BizTalk](https://marketplace.visualstudio.com/items?itemName=ms-biztalk.deploy-biztalk-application).</span><span class="sxs-lookup"><span data-stu-id="7824e-150">If **BizTalk Server Application Deployment** ins't listed, then install it at [Deploy BizTalk Application](https://marketplace.visualstudio.com/items?itemName=ms-biztalk.deploy-biztalk-application).</span></span>

7. <span data-ttu-id="7824e-151">Sélectionnez le **déployer** , entrez les valeurs et de la tâche :</span><span class="sxs-lookup"><span data-stu-id="7824e-151">Select the **Deploy** task, and enter the values:</span></span> 

    <span data-ttu-id="7824e-152">**Nom de l’opération**: sélectionnez **créer la nouvelle Application BizTalk**.</span><span class="sxs-lookup"><span data-stu-id="7824e-152">**Operation Name**: Select **Create new BizTalk Application**.</span></span> <span data-ttu-id="7824e-153">Cette option déploie une nouvelle application.</span><span class="sxs-lookup"><span data-stu-id="7824e-153">This option deploys a new application.</span></span> <span data-ttu-id="7824e-154">Si l’application existe déjà, il désinstalle les applications actuelles (point) et installe la nouvelle application.</span><span class="sxs-lookup"><span data-stu-id="7824e-154">If the application already exists, it uninstalls the current applications (full stop), and installs the new application.</span></span> <span data-ttu-id="7824e-155">Si l’intégration continue est activée, elle automatiquement redéploie l’application lorsqu’elle est mise à jour dans le référentiel.</span><span class="sxs-lookup"><span data-stu-id="7824e-155">If continuous integration is enabled, it automatically redeploys the application when it is updated in the repository.</span></span> <span data-ttu-id="7824e-156">**Mettre à jour une Application BizTalk existante** ajoute des modifications, tels que des schémas à une application déjà en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="7824e-156">**Update an existing BizTalk Application** appends changes, such as schemas, to an already running application.</span></span> <span data-ttu-id="7824e-157">Il ne nécessite pas un redéploiement complet de l’application.</span><span class="sxs-lookup"><span data-stu-id="7824e-157">It does not require a full redeploy of the application.</span></span>

    <span data-ttu-id="7824e-158">**Nom de l’application**: le texte que vous entrez sera le nom de l’application dans l’Administration de BizTalk.</span><span class="sxs-lookup"><span data-stu-id="7824e-158">**Application Name**: The text you enter will be the application name in BizTalk Administration.</span></span> <span data-ttu-id="7824e-159">Faire **pas** Entrez BizTalk Application 1.</span><span class="sxs-lookup"><span data-stu-id="7824e-159">Do **not** enter BizTalk Application 1.</span></span>

    <span data-ttu-id="7824e-160">**Package de déploiement**: sélectionnez le fichier zip dans votre projet d’application, puis sélectionnez **OK**.</span><span class="sxs-lookup"><span data-stu-id="7824e-160">**Deployment package**: Select the zip file to your application project, and select **OK**.</span></span> 

8. <span data-ttu-id="7824e-161">Sélectionnez le **phase Agent** tâche.</span><span class="sxs-lookup"><span data-stu-id="7824e-161">Select the **Agent phase** task.</span></span> <span data-ttu-id="7824e-162">Sélectionnez le **par défaut** file d’attente de l’Agent.</span><span class="sxs-lookup"><span data-stu-id="7824e-162">Select the **Default** Agent queue.</span></span> <span data-ttu-id="7824e-163">**Enregistrer** vos modifications.</span><span class="sxs-lookup"><span data-stu-id="7824e-163">**Save** your changes.</span></span>

9. <span data-ttu-id="7824e-164">Sélectionnez **Release** > **créer version**:</span><span class="sxs-lookup"><span data-stu-id="7824e-164">Select **Release** > **Create release**:</span></span>  

    ![La version finale, créez la mise en production](../core/media/vsts-create-release.png)

10. <span data-ttu-id="7824e-166">Sélectionnez **file d’attente**.</span><span class="sxs-lookup"><span data-stu-id="7824e-166">Select **Queue**.</span></span> <span data-ttu-id="7824e-167">Vérifiez l’état en cliquant sur le lien mise en production.</span><span class="sxs-lookup"><span data-stu-id="7824e-167">Check the status by clicking the release link.</span></span> <span data-ttu-id="7824e-168">En cas d’échec, l’erreur s’affiche.</span><span class="sxs-lookup"><span data-stu-id="7824e-168">If it fails, the error displays.</span></span> <span data-ttu-id="7824e-169">Si elle réussit, l’application est ajoutée à la console Administration de BizTalk.</span><span class="sxs-lookup"><span data-stu-id="7824e-169">If it succeeds, the application is added to the BizTalk Administration console.</span></span> 

## <a name="what-you-did"></a><span data-ttu-id="7824e-170">Ce que vous avez fait</span><span class="sxs-lookup"><span data-stu-id="7824e-170">What you did</span></span>

<span data-ttu-id="7824e-171">Dans VSTS, vous avez créé une définition de build qui génère votre application dans Git ou Team Foundation Version Control (que vous avez choisi).</span><span class="sxs-lookup"><span data-stu-id="7824e-171">In VSTS, you created a build definition that builds your application within Git or Team Foundation Version Control (whatever you chose).</span></span> <span data-ttu-id="7824e-172">Lorsque des modifications sont apportées dans le contrôle de code source, les modifications sont détectées automatiquement et vous pouvez les envoyer.</span><span class="sxs-lookup"><span data-stu-id="7824e-172">When changes are made within the source control, the changes are automatically detected, and you can push them.</span></span> <span data-ttu-id="7824e-173">Une fois la build terminée, vous avez créé une définition de mise en production qui déploie l’application à BizTalk Server, que vous pouvez visualiser dans Administration de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="7824e-173">After the build completes, you created a release definition that deploys the application to BizTalk Server, which you can see in BizTalk Server Administration.</span></span> 

## <a name="next-step"></a><span data-ttu-id="7824e-174">Étape suivante</span><span class="sxs-lookup"><span data-stu-id="7824e-174">Next step</span></span>
<span data-ttu-id="7824e-175">À ce stade, vous avez terminé.</span><span class="sxs-lookup"><span data-stu-id="7824e-175">At this step, you're done.</span></span> <span data-ttu-id="7824e-176">Si vous préférez, vous pouvez créer des jetons de l’environnement dans votre fichier de liaison XML BizTalk et créer des variables dans VSTS qui correspondent aux jetons de l’environnement.</span><span class="sxs-lookup"><span data-stu-id="7824e-176">If you prefer, you can create environmental tokens within your BizTalk XML binding file, and create variables within VSTS that match the environmental tokens.</span></span> <span data-ttu-id="7824e-177">Consultez [configurer des jetons de l’environnement et les variables](configure-environmental-tokens-and-variables-for-automatic-deployment.md) pour plus d’informations.</span><span class="sxs-lookup"><span data-stu-id="7824e-177">See [Configure environmental tokens and variables](configure-environmental-tokens-and-variables-for-automatic-deployment.md) for the details.</span></span> 