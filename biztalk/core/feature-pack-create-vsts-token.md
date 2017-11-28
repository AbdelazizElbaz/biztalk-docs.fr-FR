---
title: "Étape 2 : créer un jeton VSTS et installer l’agent | Documents Microsoft"
description: "Créer le clone de jeton, l’accès de sécurité VSTS à votre projet VSTS dans Visual Studio et installez l’agent de build pour automatiser le déploiement de vos projets BizTalk Server"
ms.custom: 
ms.date: 11/20/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 77296d9f2325bebaba4f4fa1ce7c55034ef1ead6
ms.sourcegitcommit: f65e8ed2b8c18cded26b9d60868fb6a56bcc1205
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="step-2-create-the-token--install-the-agent"></a><span data-ttu-id="7915d-103">Étape 2 : Créer le jeton et installer l’agent</span><span class="sxs-lookup"><span data-stu-id="7915d-103">Step 2: Create the token & install the agent</span></span>

<span data-ttu-id="7915d-104">Un jeton d’accès personnel (PAT) est créé dans Visual Studio Team Services.</span><span class="sxs-lookup"><span data-stu-id="7915d-104">A personal access token (PAT) is created in Visual Studio Team Services.</span></span> <span data-ttu-id="7915d-105">Ce jeton est votre mot de passe et est utilisé par l’agent de build VSTS pour s’authentifier.</span><span class="sxs-lookup"><span data-stu-id="7915d-105">This token is your password, and is used by the VSTS build agent to authenticate.</span></span> <span data-ttu-id="7915d-106">Le jeton s’affiche uniquement lorsque vous la créez.</span><span class="sxs-lookup"><span data-stu-id="7915d-106">The token is only displayed when you create it.</span></span> <span data-ttu-id="7915d-107">Après cela, il ne s’affiche plus.</span><span class="sxs-lookup"><span data-stu-id="7915d-107">After that, it isn't displayed anymore.</span></span> <span data-ttu-id="7915d-108">Par conséquent, une fois que vous le créez, enregistrez-le dans un autre fichier dans un emplacement en mesure de se souvenir.</span><span class="sxs-lookup"><span data-stu-id="7915d-108">So once you create it, save it to another file in a remember-able location.</span></span> 

<span data-ttu-id="7915d-109">Plus d’informations sur PAT à [authentifier l’accès avec des jetons d’accès personnels pour VSTS et TFS](https://docs.microsoft.com/vsts/accounts/use-personal-access-tokens-to-authenticate).</span><span class="sxs-lookup"><span data-stu-id="7915d-109">More info on PAT at [Authenticate access with personal access tokens for VSTS and TFS](https://docs.microsoft.com/vsts/accounts/use-personal-access-tokens-to-authenticate).</span></span> 

<span data-ttu-id="7915d-110">Après avoir créé le jeton, vous installez l’agent de build et configurez pour utiliser ce jeton.</span><span class="sxs-lookup"><span data-stu-id="7915d-110">After you create the token, you install the build agent, and configure it to use this token.</span></span> 

## <a name="before-you-begin"></a><span data-ttu-id="7915d-111">Avant de commencer</span><span class="sxs-lookup"><span data-stu-id="7915d-111">Before you begin</span></span>
<span data-ttu-id="7915d-112">Complète [l’étape 1 - projet d’ajouter une Application et de mettre à jour de json](feature-pack-add-application-project.md).</span><span class="sxs-lookup"><span data-stu-id="7915d-112">Complete [Step 1 - Add Application project and update json](feature-pack-add-application-project.md).</span></span>

## <a name="sign-into-vsts-and-create-the-token"></a><span data-ttu-id="7915d-113">Se connecter dans VSTS et créer le jeton</span><span class="sxs-lookup"><span data-stu-id="7915d-113">Sign into VSTS, and create the token</span></span>
1. <span data-ttu-id="7915d-114">Accédez à [https://app.vsaex.visualstudio.com/go/profile](https://app.vsaex.visualstudio.com/go/profile)et connectez-vous avec votre compte professionnel ou scolaire.</span><span class="sxs-lookup"><span data-stu-id="7915d-114">Go to [https://app.vsaex.visualstudio.com/go/profile](https://app.vsaex.visualstudio.com/go/profile), and sign-in with your work or school account.</span></span> <span data-ttu-id="7915d-115">Une fois que vous vous connectez, votre compte VSTS est répertorié.</span><span class="sxs-lookup"><span data-stu-id="7915d-115">After you sign in, your VSTS account is listed.</span></span> <span data-ttu-id="7915d-116">Dans l’exemple suivant, le compte est **mandiaprojects.visualstudio.com**.</span><span class="sxs-lookup"><span data-stu-id="7915d-116">In the following example, the account is **mandiaprojects.visualstudio.com**.</span></span>  

    ![Compte VSTS](../core/media/team-services-accounts.png)

    <span data-ttu-id="7915d-118">Si vous n’avez pas un compte, sélectionnez **créer nouveau compte**et entrez un nom.</span><span class="sxs-lookup"><span data-stu-id="7915d-118">If you don’t have an account, select **Create new account**, and enter a name.</span></span> <span data-ttu-id="7915d-119">Pour gérer votre code, choisissez vos préférences personnelles entre **Git ou Team Foundation Version Control**.</span><span class="sxs-lookup"><span data-stu-id="7915d-119">To manage your code, choose your personal preference between **Git or Team Foundation Version Control**.</span></span> <span data-ttu-id="7915d-120">Lorsque vous avez terminé, votre nouveau compte est créé et un site même *https://YourAccountName.visualstudio.com/MyFirstProject* s’ouvre :</span><span class="sxs-lookup"><span data-stu-id="7915d-120">When finished, your new account is created, and a site similar to *https://YourAccountName.visualstudio.com/MyFirstProject* opens:</span></span>  

    ![GIT ou TFS](../core/media/git-or-team-foundation.png)

2. <span data-ttu-id="7915d-122">Ouvrez votre compte VSTS (https://*YourAccountName*. visualstudio.com).</span><span class="sxs-lookup"><span data-stu-id="7915d-122">Open your VSTS account (https://*YourAccountName*.visualstudio.com).</span></span> <span data-ttu-id="7915d-123">Sélectionnez l’icône dans le coin supérieur droit, puis sélectionnez **sécurité**:</span><span class="sxs-lookup"><span data-stu-id="7915d-123">Select your icon in the top right-side corner, and select **Security**:</span></span> 

    ![Ouvrez la sécurité de votre compte](../core/media/vsts-account-security.png)

3. <span data-ttu-id="7915d-125">**Jetons d’accès personnels** s’ouvre automatiquement.</span><span class="sxs-lookup"><span data-stu-id="7915d-125">**Personal access tokens** automatically opens.</span></span> <span data-ttu-id="7915d-126">Si vous disposez d’un agent existant, sélectionnez-le et confirmez **Pools d’agents (lecture, gérer)** est sélectionnée :</span><span class="sxs-lookup"><span data-stu-id="7915d-126">If you have an existing agent, select it, and confirm **Agent Pools (read, manage)** is selected:</span></span>

    ![Lire et de gérer les pools d’agents-](../core/media/agent-pools-read-manage.png)

    > [!IMPORTANT]
    > <span data-ttu-id="7915d-128">Vous devez connaître le jeton d’accès.</span><span class="sxs-lookup"><span data-stu-id="7915d-128">You must know the access token.</span></span> <span data-ttu-id="7915d-129">Si vous n’et que vous n’avez pas à noter n’importe où, il ne peut pas être récupéré.</span><span class="sxs-lookup"><span data-stu-id="7915d-129">If you don’t, and didn’t note it anywhere, it cannot be retrieved.</span></span> <span data-ttu-id="7915d-130">Dans ce cas, créez un nouvel agent.</span><span class="sxs-lookup"><span data-stu-id="7915d-130">In this situation, create a new agent.</span></span> 

    <span data-ttu-id="7915d-131">Si vous n’avez pas un agent existant, sélectionnez **ajouter**, entrez une description, définir la date d’expiration et sélectionnez votre compte.</span><span class="sxs-lookup"><span data-stu-id="7915d-131">If you don’t have an existing agent, select **Add**, enter a description, set the expiration date, and select your account.</span></span> <span data-ttu-id="7915d-132">Dans **sélectionné étendues**, sélectionnez **Pools d’agents (lecture, gérer)**:</span><span class="sxs-lookup"><span data-stu-id="7915d-132">In **Selected scopes**, select **Agent Pools (read, manage)**:</span></span> 

    ![Créer le nouvel agent - lecture et gérer](../core/media/vsts-new-build-agent.png)

    <span data-ttu-id="7915d-134">Sélectionnez **créer un jeton**.</span><span class="sxs-lookup"><span data-stu-id="7915d-134">Select **Create Token**.</span></span> <span data-ttu-id="7915d-135">**Notez la valeur du jeton ; vous avez besoin dans les futures opérations.**</span><span class="sxs-lookup"><span data-stu-id="7915d-135">**Note the token value; you need in future steps.**</span></span>

4. <span data-ttu-id="7915d-136">Sélectionnez **Code**, puis sélectionnez **Clone dans Visual Studio**:</span><span class="sxs-lookup"><span data-stu-id="7915d-136">Select **Code**, and select **Clone in Visual Studio**:</span></span>  

    ![Dans votre projet, sélectionnez le Code](../core/media/vsts-project-code.png)  

    ![Cloner dans Visual Studio](../core/media/vsts-clone-in-visual-studio.png)

5. <span data-ttu-id="7915d-139">Visual Studio s’ouvre.</span><span class="sxs-lookup"><span data-stu-id="7915d-139">Visual Studio opens.</span></span> <span data-ttu-id="7915d-140">Dans Visual Studio, ouvrez votre solution BizTalk.</span><span class="sxs-lookup"><span data-stu-id="7915d-140">Within Visual Studio, open your BizTalk solution.</span></span> 

## <a name="install-the-build-agent"></a><span data-ttu-id="7915d-141">Installer l’Agent de Build</span><span class="sxs-lookup"><span data-stu-id="7915d-141">Install the Build Agent</span></span>

<span data-ttu-id="7915d-142">L’agent de build est installé sur l’ordinateur de développement de BizTalk.</span><span class="sxs-lookup"><span data-stu-id="7915d-142">The build agent is installed on the BizTalk development computer.</span></span> <span data-ttu-id="7915d-143">Si vous utilisez des groupes de déploiement, l’agent de build est installé sur tous les serveurs BizTalk que vous voulez procéder au déploiement.</span><span class="sxs-lookup"><span data-stu-id="7915d-143">If using deployment groups, the build agent is installed on all the BizTalk servers you want to deploy to.</span></span> <span data-ttu-id="7915d-144">Les étapes suivantes vous montrent comment installer l’agent de build sur un ordinateur unique.</span><span class="sxs-lookup"><span data-stu-id="7915d-144">The following steps show you how to install the build agent on a single computer.</span></span> <span data-ttu-id="7915d-145">Pour plus d’informations sur l’utilisation de groupes de déploiement, consultez [groupes de déploiement](https://docs.microsoft.com/vsts/build-release/concepts/definitions/release/deployment-groups/index).</span><span class="sxs-lookup"><span data-stu-id="7915d-145">For details on using deployment groups, see [Deployment groups](https://docs.microsoft.com/vsts/build-release/concepts/definitions/release/deployment-groups/index).</span></span>

1. <span data-ttu-id="7915d-146">Ouvrez votre compte VSTS et le projet, qui est un élément comme *https://YourAccountName.visualstudio.com/MyFirstProject*.</span><span class="sxs-lookup"><span data-stu-id="7915d-146">Open your VSTS account and project, which is something like *https://YourAccountName.visualstudio.com/MyFirstProject*.</span></span> <span data-ttu-id="7915d-147">Sélectionnez l’icône des paramètres, puis sélectionnez **files d’attente de l’Agent**:</span><span class="sxs-lookup"><span data-stu-id="7915d-147">Select the settings icon, and select **Agent Queues**:</span></span>  

    ![Paramètres > files d’attente de l’Agent](../core/media/vsts-settings-agent-queues.png)

2. <span data-ttu-id="7915d-149">Sélectionnez le **par défaut** agent, puis sélectionnez **télécharger l’Agent**.</span><span class="sxs-lookup"><span data-stu-id="7915d-149">Select the **Default** agent, and select **Download Agent**.</span></span> <span data-ttu-id="7915d-150">Sélectionnez le **télécharger** bouton et enregistrez le fichier à votre **télécharge** dossiers.</span><span class="sxs-lookup"><span data-stu-id="7915d-150">Select the **Download** button, and save the file to your **Downloads** folders.</span></span>

3. <span data-ttu-id="7915d-151">Les étapes d’installation ouvrent automatiquement.</span><span class="sxs-lookup"><span data-stu-id="7915d-151">The install steps automatically open.</span></span> <span data-ttu-id="7915d-152">Suivez ces étapes pour plus d’informations plus récentes.</span><span class="sxs-lookup"><span data-stu-id="7915d-152">Follow those steps for the most up-to-date details.</span></span> <span data-ttu-id="7915d-153">Voici quelques conseils :</span><span class="sxs-lookup"><span data-stu-id="7915d-153">Here is some guidance:</span></span> 

    1. <span data-ttu-id="7915d-154">Ouvrez Windows PowerShell en tant qu’administrateur.</span><span class="sxs-lookup"><span data-stu-id="7915d-154">Open Windows PowerShell as Administrator.</span></span>

    2. <span data-ttu-id="7915d-155">Pour créer l’agent, entrez :</span><span class="sxs-lookup"><span data-stu-id="7915d-155">To create the agent, enter:</span></span> 

        ```powershell
        PS C:\> mkdir agent ; cd agent  

        PS C:\agent> Add-Type -AssemblyName System.IO.Compression.FileSystem ; [System.IO.Compression.ZipFile]::ExtractToDirectory("$HOME\Downloads\vsts-agent-win7-x64-2.124.0.zip", "$PWD")
        ```
    
        <span data-ttu-id="7915d-156">Les modifications de version de fichier de l’agent vsts.</span><span class="sxs-lookup"><span data-stu-id="7915d-156">The vsts-agent file version changes.</span></span> <span data-ttu-id="7915d-157">Par conséquent, suivez les étapes d’installation VSTS pour des détails spécifiques.</span><span class="sxs-lookup"><span data-stu-id="7915d-157">So follow the VSTS install steps for specific details.</span></span> <span data-ttu-id="7915d-158">Une fois que vous avez atteint Entrez, il peut prendre quelques minutes pour l’invite à retourner.</span><span class="sxs-lookup"><span data-stu-id="7915d-158">After you hit enter, it may take a couple of minutes for the prompt to return.</span></span> 

    3. <span data-ttu-id="7915d-159">Pour configurer l’agent, entrez :</span><span class="sxs-lookup"><span data-stu-id="7915d-159">To configure the agent, enter:</span></span> 

        ```powershell
        PS C:\agent> .\config.cmd
        ```

    4. <span data-ttu-id="7915d-160">Entrez les informations suivantes :</span><span class="sxs-lookup"><span data-stu-id="7915d-160">Enter the following details:</span></span>  
        
        | <span data-ttu-id="7915d-161">Propriété</span><span class="sxs-lookup"><span data-stu-id="7915d-161">Property</span></span> | <span data-ttu-id="7915d-162">Valeur</span><span class="sxs-lookup"><span data-stu-id="7915d-162">Value</span></span> |
        | --- | --- |
        | <span data-ttu-id="7915d-163">URL du serveur</span><span class="sxs-lookup"><span data-stu-id="7915d-163">Server URL</span></span>| <span data-ttu-id="7915d-164">https://{your-account}.VisualStudio.com</span><span class="sxs-lookup"><span data-stu-id="7915d-164">https://{your-account}.visualstudio.com</span></span> |
        | <span data-ttu-id="7915d-165">Type d’authentification</span><span class="sxs-lookup"><span data-stu-id="7915d-165">Authentication Type</span></span> | <span data-ttu-id="7915d-166">PAT</span><span class="sxs-lookup"><span data-stu-id="7915d-166">PAT</span></span> |
        | <span data-ttu-id="7915d-167">Jeton d’accès personnel</span><span class="sxs-lookup"><span data-stu-id="7915d-167">Personal access token</span></span> | <span data-ttu-id="7915d-168">Collez votre jeton VSTS</span><span class="sxs-lookup"><span data-stu-id="7915d-168">Paste your VSTS token</span></span> |
        | <span data-ttu-id="7915d-169">Pool d’agents</span><span class="sxs-lookup"><span data-stu-id="7915d-169">Agent pool</span></span> | <span data-ttu-id="7915d-170">Entrez la valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="7915d-170">Enter for the default</span></span> |
        | <span data-ttu-id="7915d-171">Nom de l’agent</span><span class="sxs-lookup"><span data-stu-id="7915d-171">Agent name</span></span> | <span data-ttu-id="7915d-172">Entrez la valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="7915d-172">Enter for the default</span></span> |
        | <span data-ttu-id="7915d-173">Remplacer</span><span class="sxs-lookup"><span data-stu-id="7915d-173">Replace</span></span> | <span data-ttu-id="7915d-174">*S’affiche uniquement si vous disposez d’un agent existant*</span><span class="sxs-lookup"><span data-stu-id="7915d-174">*Only displays if you have an existing agent*</span></span> |
        | <span data-ttu-id="7915d-175">Dossier de travail</span><span class="sxs-lookup"><span data-stu-id="7915d-175">Work folder</span></span> | <span data-ttu-id="7915d-176">Entrez la valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="7915d-176">Enter for the default</span></span> |
        | <span data-ttu-id="7915d-177">Exécutez l’agent en tant que service</span><span class="sxs-lookup"><span data-stu-id="7915d-177">Run agent as a service</span></span> | <span data-ttu-id="7915d-178">O</span><span class="sxs-lookup"><span data-stu-id="7915d-178">Y</span></span> |
        | <span data-ttu-id="7915d-179">Compte d'utilisateur</span><span class="sxs-lookup"><span data-stu-id="7915d-179">User account</span></span> | <span data-ttu-id="7915d-180">Il vous revient de, mais vous risquez de rencontrer un problème d’autorisations.</span><span class="sxs-lookup"><span data-stu-id="7915d-180">This is up to you, but you may run into a permissions issue.</span></span> <br/><br/><span data-ttu-id="7915d-181">Songez à votre session compte actuel, qui est un administrateur local</span><span class="sxs-lookup"><span data-stu-id="7915d-181">Consider entering your current logged-on account, which is a local Admin.</span></span> |

    5. <span data-ttu-id="7915d-182">Lorsque vous avez terminé, votre fenêtre PowerShell ressemble à ceci :</span><span class="sxs-lookup"><span data-stu-id="7915d-182">When finished, your PowerShell window looks like the following:</span></span>  
    
        ![Installation de l’agent](../core/media/vsts-agent-powershell-install.png)

4. <span data-ttu-id="7915d-184">Ouvrez services.msc pour voir le nouveau service.</span><span class="sxs-lookup"><span data-stu-id="7915d-184">Open services.msc to see the new service.</span></span> <span data-ttu-id="7915d-185">Il doit être en cours d’exécution :</span><span class="sxs-lookup"><span data-stu-id="7915d-185">It should be running:</span></span>  

    ![Service est en cours d’exécution.](../core/media/vsts-service.png)

    <span data-ttu-id="7915d-187">Si le service ne parvient pas à démarrer, [supprimer et reconfigurer un agent](https://docs.microsoft.com/vsts/build-release/actions/agents/v2-windows) à l’aide d’un compte avec des privilèges plus.</span><span class="sxs-lookup"><span data-stu-id="7915d-187">If the service fails to start, [remove and re-configure an agent](https://docs.microsoft.com/vsts/build-release/actions/agents/v2-windows) using an account with more privilages.</span></span>


## <a name="what-you-did"></a><span data-ttu-id="7915d-188">Ce que vous avez fait</span><span class="sxs-lookup"><span data-stu-id="7915d-188">What you did</span></span>

<span data-ttu-id="7915d-189">Vous connectez à votre compte VSTS et créé un jeton de sécurité.</span><span class="sxs-lookup"><span data-stu-id="7915d-189">You signed into your VSTS account, and created a security token.</span></span> <span data-ttu-id="7915d-190">Ce jeton de sécurité est similaire à un mot de passe et vous donne accès à votre projet VSTS.</span><span class="sxs-lookup"><span data-stu-id="7915d-190">This security token is like a password, and gives you access to your VSTS project.</span></span> <span data-ttu-id="7915d-191">Il s’affiche uniquement une fois, par conséquent, être que vous l’avez enregistré.</span><span class="sxs-lookup"><span data-stu-id="7915d-191">It's only displayed once, so be sure you saved it.</span></span> <span data-ttu-id="7915d-192">Vous également cloné votre projet VSTS dans Visual Studio et créé un agent qui s’exécute en tant que service sur votre ordinateur de développement de BizTalk.</span><span class="sxs-lookup"><span data-stu-id="7915d-192">You also cloned your VSTS project into Visual Studio, and created an agent that runs as a service on your BizTalk development computer.</span></span> <span data-ttu-id="7915d-193">Cet agent utilise le jeton de sécurité.</span><span class="sxs-lookup"><span data-stu-id="7915d-193">This agent uses the security token.</span></span> 

## <a name="next-steps"></a><span data-ttu-id="7915d-194">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="7915d-194">Next steps</span></span>
[<span data-ttu-id="7915d-195">Étape 3 : Création de la build et définitions de version</span><span class="sxs-lookup"><span data-stu-id="7915d-195">Step 3: Create the build and release definitions</span></span>](feature-pack-add-build-release-definitions.md)  
[<span data-ttu-id="7915d-196">Configurer les variables et les jetons de l’environnement</span><span class="sxs-lookup"><span data-stu-id="7915d-196">Configure environmental tokens and variables</span></span>](configure-environmental-tokens-and-variables-for-automatic-deployment.md)