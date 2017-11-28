---
title: "Étape 1 : ajouter json mise à jour et de projet d’Application | Documents Microsoft"
description: "Ajouter le projet d’Application BizTalk Server dans Visual Studio et mettre à jour le fichier BizTalkServerInventory.json aux DLL, de fichiers de liaison et de séquence de déploiement de vos applications - Visual Studio Team Services"
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
ms.openlocfilehash: 46cb8a2072280e62cd8c3438521531f8cf3b55aa
ms.sourcegitcommit: a0165ec2f1e8b58545638666b7bfa2bf440036fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="step-1-add-the-biztalk-server-application-project-in-visual-studio"></a><span data-ttu-id="bd33e-103">Étape 1 : Ajouter le projet d’Application BizTalk Server dans Visual Studio</span><span class="sxs-lookup"><span data-stu-id="bd33e-103">Step 1: Add the BizTalk Server Application project in Visual Studio</span></span>

<span data-ttu-id="bd33e-104">.Btaproj – lorsque vous générez vos applications à l’aide de Visual Studio Team Services, un nouveau fichier de projet BizTalk est créé.</span><span class="sxs-lookup"><span data-stu-id="bd33e-104">When you build your applications using Visual Studio Team Services, a new BizTalk project file is created – .btaproj.</span></span> <span data-ttu-id="bd33e-105">Ce projet conserve toutes les applications BizTalk que vous générez et déployez à l’aide de la génération VSTS et fonctionnalités de la version.</span><span class="sxs-lookup"><span data-stu-id="bd33e-105">This new project holds all the BizTalk applications that you build and deploy using the VSTS build and release features.</span></span> 

<span data-ttu-id="bd33e-106">Le projet d’Application BizTalk inclut le `BizTalkServerInventory.json` fichier.</span><span class="sxs-lookup"><span data-stu-id="bd33e-106">The BizTalk Application Project includes the `BizTalkServerInventory.json` file.</span></span> <span data-ttu-id="bd33e-107">Dans ce fichier, ajouter vos assemblys BizTalk, ajoutez les fichiers de liaison pour votre application BizTalk, puis définissez une séquence de déploiement.</span><span class="sxs-lookup"><span data-stu-id="bd33e-107">In this file, add your BizTalk assemblies, add the binding files for your BizTalk application, and then set a deployment sequence.</span></span> 

## <a name="before-you-begin"></a><span data-ttu-id="bd33e-108">Avant de commencer</span><span class="sxs-lookup"><span data-stu-id="bd33e-108">Before you begin</span></span>

* <span data-ttu-id="bd33e-109">Ces étapes supposent que vous avez un projet BizTalk existant.</span><span class="sxs-lookup"><span data-stu-id="bd33e-109">These steps assume you have an existing BizTalk project.</span></span> <span data-ttu-id="bd33e-110">Si non, vous pouvez utiliser l’exemple HelloWorld SDK (\Program Files (x86) \Microsoft BizTalk Server *yourVersion*\SDK\Samples\Orchestrations\HelloWorld).</span><span class="sxs-lookup"><span data-stu-id="bd33e-110">If not, you can use the HelloWorld SDK sample (\Program Files (x86)\Microsoft BizTalk Server *yourVersion*\SDK\Samples\Orchestrations\HelloWorld).</span></span> 
* <span data-ttu-id="bd33e-111">Avoir le chemin d’accès au fichier de liaison XML à votre projet BizTalk prêt.</span><span class="sxs-lookup"><span data-stu-id="bd33e-111">Have the path to the XML binding file to your BizTalk project ready.</span></span> 
* <span data-ttu-id="bd33e-112">Connaître votre compte VSTS, votre collection et détails de votre projet d’équipe.</span><span class="sxs-lookup"><span data-stu-id="bd33e-112">Know your VSTS account, your collection, and your team project details.</span></span>
* <span data-ttu-id="bd33e-113">Être familiarisé avec les concepts de git, y compris le clonage et l’utilisation de référentiels.</span><span class="sxs-lookup"><span data-stu-id="bd33e-113">Be familiar with git concepts, including cloning and working with repositories.</span></span> 
* <span data-ttu-id="bd33e-114">Veillez [Feature Pack 1](https://www.microsoft.com/download/details.aspx?id=55100) est installé</span><span class="sxs-lookup"><span data-stu-id="bd33e-114">Be sure [Feature Pack 1](https://www.microsoft.com/download/details.aspx?id=55100) is installed</span></span>

## <a name="add-the-application-project"></a><span data-ttu-id="bd33e-115">Ajouter le projet d’application</span><span class="sxs-lookup"><span data-stu-id="bd33e-115">Add the application project</span></span>

1. <span data-ttu-id="bd33e-116">Sur le serveur BizTalk, ouvrez votre solution (ProjectName.sln) dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="bd33e-116">On the BizTalk Server, open your solution (ProjectName.sln) in Visual Studio.</span></span> <span data-ttu-id="bd33e-117">Ne sélectionnez pas de Visual Studio Blend.</span><span class="sxs-lookup"><span data-stu-id="bd33e-117">Do not select Visual Studio Blend.</span></span>

2. <span data-ttu-id="bd33e-118">Dans l’Explorateur de solutions, cliquez sur votre projet, puis sélectionnez **Build**.</span><span class="sxs-lookup"><span data-stu-id="bd33e-118">In solution explorer, right-click your project, and select **Build**.</span></span> <span data-ttu-id="bd33e-119">Assurez-vous que votre build terminée.</span><span class="sxs-lookup"><span data-stu-id="bd33e-119">Be sure your build succeeds.</span></span> <span data-ttu-id="bd33e-120">Avec le bouton droit de votre projet, puis sélectionnez **déployer**.</span><span class="sxs-lookup"><span data-stu-id="bd33e-120">Right-click your project, and select **Deploy**.</span></span> <span data-ttu-id="bd33e-121">Assurez-vous que votre déploiement réussit.</span><span class="sxs-lookup"><span data-stu-id="bd33e-121">Be sure your deploy succeeds.</span></span>

3. <span data-ttu-id="bd33e-122">Avec le bouton droit de votre solution, sélectionnez **ajouter**, puis sélectionnez **ajouter un nouveau projet**.</span><span class="sxs-lookup"><span data-stu-id="bd33e-122">Right-click your solution, select **Add**, and select **Add New Project**.</span></span>

4. <span data-ttu-id="bd33e-123">Sélectionnez le **projets BizTalk** onglet, sélectionnez **.NET Framework 4.6.1** à partir de la liste déroulante, puis sélectionnez **projet d’Application de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="bd33e-123">Select the **BizTalk Projects** tab, select **.NET Framework 4.6.1** from the drop-down list, and select **BizTalk Server Application Project**.</span></span> <span data-ttu-id="bd33e-124">Entrez un nom (par exemple, appProjectHelloWorld), puis sélectionnez **OK**:</span><span class="sxs-lookup"><span data-stu-id="bd33e-124">Enter a name (e.g. appProjectHelloWorld), and select **OK**:</span></span>  

    ![Ajouter le projet d’application](../core/media/add-application-project.png)

5. <span data-ttu-id="bd33e-126">Dans l’Explorateur de solutions, cliquez sur votre projet nouvellement ajouté l’application (.btaproj), sélectionnez **ajouter**, sélectionnez **référence**.</span><span class="sxs-lookup"><span data-stu-id="bd33e-126">In Solution Explorer, right-click your newly-added application project (.btaproj), select **Add**, select **Reference**.</span></span> <span data-ttu-id="bd33e-127">Développez le **projets** et vérifiez votre projet BizTalk (le projet que vous déployez à l’aide de VSTS).</span><span class="sxs-lookup"><span data-stu-id="bd33e-127">Expand the **Projects** tab, and check your BizTalk project (the project you are deploying using VSTS).</span></span> <span data-ttu-id="bd33e-128">Sélectionnez **OK**.</span><span class="sxs-lookup"><span data-stu-id="bd33e-128">Select **OK**.</span></span>  
    <span data-ttu-id="bd33e-129">Une fois ajouté, développez **références** sous votre projet d’application (par exemple, appProjectHelloWorld) pour afficher le projet BizTalk que vous venez d’ajouter.</span><span class="sxs-lookup"><span data-stu-id="bd33e-129">Once added, expand **References** under your application project (e.g. appProjectHelloWorld) to see the BizTalk project you just added.</span></span> 

6. <span data-ttu-id="bd33e-130">Dans l’Explorateur de solutions, cliquez sur votre projet d’application (.btaproj), sélectionnez **ajouter**, sélectionnez **élément existant**, et **ajouter** votre fichier XML de liaison.</span><span class="sxs-lookup"><span data-stu-id="bd33e-130">In Solution Explorer, right-click your application project (.btaproj), select **Add**, select **Existing Item**, and **Add** your binding XML file.</span></span>

7. <span data-ttu-id="bd33e-131">Ouvrez les propriétés de binding.xml, puis définissez **copier dans le répertoire de sortie** à **toujours copier**.</span><span class="sxs-lookup"><span data-stu-id="bd33e-131">Open the properties of binding.xml, and set **Copy to Output Directory** to **Copy always**.</span></span> <span data-ttu-id="bd33e-132">**Enregistrer** vos modifications :</span><span class="sxs-lookup"><span data-stu-id="bd33e-132">**Save** your changes:</span></span>  

    ![Propriétés du fichier de liaison](../core/media/xml-binding-file-properties.png)


## <a name="configure-the-json-template"></a><span data-ttu-id="bd33e-134">Configurer le modèle JSON</span><span class="sxs-lookup"><span data-stu-id="bd33e-134">Configure the JSON template</span></span>

1. <span data-ttu-id="bd33e-135">Dans Visual Studio, dans votre projet d’application (.btaproj), ouvrez le `BizTalkServerInventory.json` fichier.</span><span class="sxs-lookup"><span data-stu-id="bd33e-135">In Visual Studio, in your application project (.btaproj), open the `BizTalkServerInventory.json` file.</span></span> 

2. <span data-ttu-id="bd33e-136">Le modèle inclut les sections suivantes :</span><span class="sxs-lookup"><span data-stu-id="bd33e-136">The template includes the following sections:</span></span> 

    | | |
    |---|---|
    |<span data-ttu-id="bd33e-137">BizTalkAssemblies</span><span class="sxs-lookup"><span data-stu-id="bd33e-137">BizTalkAssemblies</span></span> | <span data-ttu-id="bd33e-138">Les assemblys utilisés dans vos applications</span><span class="sxs-lookup"><span data-stu-id="bd33e-138">The assemblies used in your applications</span></span> |
    |<span data-ttu-id="bd33e-139">BindingFiles</span><span class="sxs-lookup"><span data-stu-id="bd33e-139">BindingFiles</span></span> | <span data-ttu-id="bd33e-140">Les fichiers de liaison que vous référencez</span><span class="sxs-lookup"><span data-stu-id="bd33e-140">The binding files you are referencing</span></span>|
    |<span data-ttu-id="bd33e-141">DeploymentSequence</span><span class="sxs-lookup"><span data-stu-id="bd33e-141">DeploymentSequence</span></span> | <span data-ttu-id="bd33e-142">La séquence des éléments à installer</span><span class="sxs-lookup"><span data-stu-id="bd33e-142">The sequence for the elements to be installed</span></span>|
    
    <span data-ttu-id="bd33e-143">Exemple de modèle :</span><span class="sxs-lookup"><span data-stu-id="bd33e-143">Sample template:</span></span> 
    
    ![Image de modèle FP1 Json 1](../core/media/fp1-json-template-image-1.png)

    > [!IMPORTANT]
    > <span data-ttu-id="bd33e-145">Selon la complexité de votre solution, les éléments que vous souhaitez dans la build doivent être référencées dans ce fichier de modèle JSON.</span><span class="sxs-lookup"><span data-stu-id="bd33e-145">Depending on the complexity of your solution, the elements you want in the build must be referenced in this JSON template file.</span></span>

3. <span data-ttu-id="bd33e-146">Dans `BizTalkAssemblies`, ajoutez les assemblys utilisés par votre projet BizTalk :</span><span class="sxs-lookup"><span data-stu-id="bd33e-146">In `BizTalkAssemblies`, add the assemblies used by your BizTalk project:</span></span> 

    ```
    "BizTalkAssemblies": [
        {
            "Name": "AssemblyName"
            "Path": "PathToAssembly
        }
    ]
    ```

4. <span data-ttu-id="bd33e-147">Dans `BindingsFiles`, ajoutez les fichiers de liaison pour votre projet BizTalk :</span><span class="sxs-lookup"><span data-stu-id="bd33e-147">In `BindingsFiles`, add the binding files for your BizTalk project:</span></span> 

    ```
    "BindingsFiles": [
        {
            "Name": "Binding File Name"
            "Path": "PathToBindingFile
        }
    ]
    ```

5. <span data-ttu-id="bd33e-148">Dans `DeploymentSequence`, ajoutez les noms d’application dans l’ordre que vous souhaitez les déployé et installé sur le [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="bd33e-148">In `DeploymentSequence`, add the application names in the order you want them deployed, and installed on the [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)]:</span></span> 

    ```
    "DeploymentSequence": [
        {
            "NameOfFirst", "NameOfSecond", "NameOfThird"
        }
    ]
    ```


6. <span data-ttu-id="bd33e-149">**Enregistrer** vos modifications.</span><span class="sxs-lookup"><span data-stu-id="bd33e-149">**Save** your changes.</span></span> <span data-ttu-id="bd33e-150">Lorsque vous avez terminé, votre fichier .json ressemble à ceci :</span><span class="sxs-lookup"><span data-stu-id="bd33e-150">When finished, your .json file looks like the following:</span></span> 

    ```
    {
      "$schema": "C:\\Program Files (x86)\\Microsoft BizTalk Server 2016\\Developer Tools\\BizTalkServerAppplicationSchema.json",
      "BizTalkAssemblies": [
        {
          "Name": "HelloWorld",
          "Path": "HelloWorld\\bin\\Release\\HelloWorld.dll"
        }
      ],
      "BindingsFiles": [
        {
          "Name": "HelloWorldBinding",
          "Path": "HelloWorld\\HelloWorldBinding.xml"
        }
      ],
      "DeploymentSequence": [
        "HelloWorld", "HelloWorldBinding"
      ]
    }
    ```

7. <span data-ttu-id="bd33e-151">**Facultatif**.</span><span class="sxs-lookup"><span data-stu-id="bd33e-151">**Optional**.</span></span> <span data-ttu-id="bd33e-152">Avec le bouton droit de votre projet d’application (par exemple, appProjectHelloWorld), puis sélectionnez **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="bd33e-152">Right-click your application project (e.g. appProjectHelloWorld), and select **Properties**.</span></span> <span data-ttu-id="bd33e-153">Vous pouvez définir la version Debug ou Release une nouvelle valeur.</span><span class="sxs-lookup"><span data-stu-id="bd33e-153">You can set the Debug or Release version to a new value.</span></span> <span data-ttu-id="bd33e-154">Nous ne dans ces étapes, mais sachez que vous pouvez effectuer cela.</span><span class="sxs-lookup"><span data-stu-id="bd33e-154">We don’t in these steps, but be aware you can do this.</span></span>  

    ![Définissez la version debug ou release](../core/media/application-project-version.png)

8. <span data-ttu-id="bd33e-156">Avec le bouton droit de votre projet d’application (par exemple, appProjectHelloWorld), puis sélectionnez **Build**.</span><span class="sxs-lookup"><span data-stu-id="bd33e-156">Right-click your application project (e.g. appProjectHelloWorld), and select **Build**.</span></span> <span data-ttu-id="bd33e-157">Si elle réussit, un fichier zip est créé dans  ***yourApplicationProject*\bin\debug** dossier :</span><span class="sxs-lookup"><span data-stu-id="bd33e-157">If it succeeds, a zip file is created in ***yourApplicationProject*\bin\debug** folder:</span></span>  

    ![Générer le fichier zip](../core/media/application-project-zip-file.png)

9. <span data-ttu-id="bd33e-159">Sélectionnez votre solution, puis sélectionnez le **Team Explorer** onglet. Sous VSTS, sélectionnez **connexion**.</span><span class="sxs-lookup"><span data-stu-id="bd33e-159">Select your solution, and select the **Team Explorer** tab. Under VSTS, select **Connect**.</span></span>  

    ![Se connecter à Team Services](../core/media/connect-team-services.png)

10. <span data-ttu-id="bd33e-161">Sélectionnez votre compte VSTS, votre collection et votre projet d’équipe.</span><span class="sxs-lookup"><span data-stu-id="bd33e-161">Select your VSTS account, your collection, and your team project.</span></span> <span data-ttu-id="bd33e-162">Sélectionnez **OK**.</span><span class="sxs-lookup"><span data-stu-id="bd33e-162">Select **OK**.</span></span> <span data-ttu-id="bd33e-163">Si vous n’avez pas encore créé le compte VSTS, puis créer un ([étape 2 : créer le jeton VSTS](feature-pack-create-vsts-token.md) fournit quelques conseils).</span><span class="sxs-lookup"><span data-stu-id="bd33e-163">If you didn’t create a VSTS account yet, then create one ([Step 2: Create the VSTS token](feature-pack-create-vsts-token.md) provides some guidance).</span></span> <span data-ttu-id="bd33e-164">Une fois qu’elle est créée, revenez à cette étape et connectez-vous.</span><span class="sxs-lookup"><span data-stu-id="bd33e-164">Once it's created, come back to this step, and connect.</span></span>  

    ![Sélectionnez votre projet et collection](../core/media/team-collections-projects.png)

11. <span data-ttu-id="bd33e-166">Lorsque vous vous connectez, vous pouvez obtenir une invite pour cloner ce référentiel.</span><span class="sxs-lookup"><span data-stu-id="bd33e-166">When you connect, you may get a prompt to clone this repository.</span></span> <span data-ttu-id="bd33e-167">Sélectionnez le **cloner ce référentiel** lien.</span><span class="sxs-lookup"><span data-stu-id="bd33e-167">Select the **Clone this repository** link.</span></span>  

    ![Cloner le référentiel](../core/media/vsts-clone-repository.png)

12. <span data-ttu-id="bd33e-169">Notez l’URL et les chemins d’accès, puis sélectionnez **Clone**:</span><span class="sxs-lookup"><span data-stu-id="bd33e-169">Note the URL and paths, and select **Clone**:</span></span>  

    ![Chemins d’accès du référentiel](../core/media/clone-repo-paths.png)

<span data-ttu-id="bd33e-171">Une fois terminé, la tâche de déploiement de Service Visual Studio Team honore les fichiers requis et la séquence d’installation.</span><span class="sxs-lookup"><span data-stu-id="bd33e-171">Once completed, the Visual Studio Team Service deployment task honors the required files and the install sequence.</span></span> 

> [!TIP]
> <span data-ttu-id="bd33e-172">Si vous apportez des modifications à votre projet une fois que vous clonez dans git, vous pouvez **étape** vos modifications, puis **Push**, dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="bd33e-172">If you make changes to your project after you clone in git, you can **Stage** your changes, and then **Push**, all within Visual Studio.</span></span> 

## <a name="what-you-did"></a><span data-ttu-id="bd33e-173">Ce que vous avez fait</span><span class="sxs-lookup"><span data-stu-id="bd33e-173">What you did</span></span>

<span data-ttu-id="bd33e-174">Dans votre projet BizTalk, vous avez ajouté un projet d’Application de BizTalk (.btaproj).</span><span class="sxs-lookup"><span data-stu-id="bd33e-174">In your BizTalk project, you added a BizTalk Application project (.btaproj).</span></span> <span data-ttu-id="bd33e-175">Ce projet est utilisé pour automatiser les déploiements de vos projets BizTalk Server à l’aide de VSTS.</span><span class="sxs-lookup"><span data-stu-id="bd33e-175">This project is used to automate deployments of your BizTalk Server projects using VSTS.</span></span> <span data-ttu-id="bd33e-176">Une fois que vous avez créé le projet d’application, vous avez ajouté une référence à votre projet d’application BizTalk.</span><span class="sxs-lookup"><span data-stu-id="bd33e-176">After you created the application project, you added a reference to your BizTalk application project.</span></span> <span data-ttu-id="bd33e-177">Ensuite, de mise à jour un fichier JSON qui indique le déploiement automatisé, les DLL à déployer, le fichier de liaison à utiliser et la commande pour déployer les applications.</span><span class="sxs-lookup"><span data-stu-id="bd33e-177">Then, you updated a JSON file that tells the automated deployment what DLLs to deploy, which binding file to use, and the order to deploy the applications.</span></span> 

## <a name="next-steps"></a><span data-ttu-id="bd33e-178">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="bd33e-178">Next steps</span></span>
[<span data-ttu-id="bd33e-179">Étape 2 : Créer le jeton VSTS</span><span class="sxs-lookup"><span data-stu-id="bd33e-179">Step 2: Create the VSTS token</span></span>](feature-pack-create-vsts-token.md)  
[<span data-ttu-id="bd33e-180">Étape 3 : Création de la build et définitions de version</span><span class="sxs-lookup"><span data-stu-id="bd33e-180">Step 3: Create the build and release definitions</span></span>](feature-pack-add-build-release-definitions.md)  
[<span data-ttu-id="bd33e-181">Configurer les variables et les jetons de l’environnement</span><span class="sxs-lookup"><span data-stu-id="bd33e-181">Configure environmental tokens and variables</span></span>](configure-environmental-tokens-and-variables-for-automatic-deployment.md)