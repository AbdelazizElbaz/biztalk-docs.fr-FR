---
title: "Créer des jetons de l’environnement et des variables | Documents Microsoft »"
description: "Mettre à jour le fichier de liaison pour utiliser des jetons de l’environnement et créer des variables dans VSTS pour automatiser le déploiement d’applications BizTalk Server"
ms.custom: 
ms.date: 11/08/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.prod: biztalk-server
ms.topic: article
ms.assetid: 28bb2d4a-f45c-466d-ba65-0ca8cad0bffd
caps.latest.revision: "4"
author: tordgladnordahl
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6d84fa393410e3084c87e762140530a45b0b78b5
ms.sourcegitcommit: a0165ec2f1e8b58545638666b7bfa2bf440036fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="configure-environmental-tokens-and-variables-for-automatic-deployment"></a><span data-ttu-id="649bd-103">Configurer des jetons de l’environnement et les variables pour un déploiement automatique</span><span class="sxs-lookup"><span data-stu-id="649bd-103">Configure environmental tokens and variables for automatic deployment</span></span>
<span data-ttu-id="649bd-104">Utiliser des variables Visual Studio Team Services (VSTS) dans votre [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] fichiers de liaison.</span><span class="sxs-lookup"><span data-stu-id="649bd-104">Use Visual Studio Team Services (VSTS) variables in your [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] binding files.</span></span>

## <a name="overview"></a><span data-ttu-id="649bd-105">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="649bd-105">Overview</span></span>
<span data-ttu-id="649bd-106">Dans un environnement de VSTS, vous pouvez ajouter des variables et les définir sur une valeur.</span><span class="sxs-lookup"><span data-stu-id="649bd-106">In a VSTS environment, you can add variables, and set them to a value.</span></span> <span data-ttu-id="649bd-107">Par exemple, vous pouvez créer un *sendPortPath* variable et définissez sa valeur à un dossier physique sur votre [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="649bd-107">For example, you can create a *sendPortPath* variable, and set its value to a physical folder on your [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)].</span></span> 

<span data-ttu-id="649bd-108">Dans la [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] fichier de liaison d’application, les variables configurables peuvent s’agir d’une balise XML, telles que le nom d’emplacement de réception, héberger, URI du port d’envoi et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="649bd-108">Within the [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] application binding file, the configurable variables can be anything within an XML tag, such as the receive location name, host, send port URI, and so on.</span></span> 

<span data-ttu-id="649bd-109">Ces variables sont spécifiques à votre environnement de VSTS et peut être utilisés pour déployer la même application à plusieurs [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] environnements.</span><span class="sxs-lookup"><span data-stu-id="649bd-109">These variables are specific to your VSTS environment, and can be used to deploy the same application to multiple [!INCLUDE[btsBizTalkServerNoVersion_md](../includes/btsbiztalkservernoversion-md.md)] environments.</span></span> 

<span data-ttu-id="649bd-110">Nous vous montrent comment ajouter la variable VSTS dans votre fichier de liaison et la création de la variable dans VSTS.</span><span class="sxs-lookup"><span data-stu-id="649bd-110">We show you how to add the VSTS variable in your binding file, and how to create the variable within VSTS.</span></span> 

## <a name="add-variables-to-the-binding-file"></a><span data-ttu-id="649bd-111">Ajouter des variables dans le fichier de liaison</span><span class="sxs-lookup"><span data-stu-id="649bd-111">Add variables to the binding file</span></span>

1. <span data-ttu-id="649bd-112">Ouvrez le fichier de liaison d’application :</span><span class="sxs-lookup"><span data-stu-id="649bd-112">Open the application binding file:</span></span>

    ![Ouvrez le fichier de liaison](../core/media/biztalk-feature-pack-1-binding-1.png)

2. <span data-ttu-id="649bd-114">Recherchez l’élément que vous souhaitez modifier :</span><span class="sxs-lookup"><span data-stu-id="649bd-114">Find the element you want to change:</span></span>

    ![Sélectionnez l’élément](../core/media/biztalk-feature-pack-1-binding-2.png)
    
3. <span data-ttu-id="649bd-116">Supprimer la valeur par défaut et remplacez-la par vous variables : `$(YourValue)`.</span><span class="sxs-lookup"><span data-stu-id="649bd-116">Remove the populated value, and replace it with you variables: `$(YourValue)`.</span></span> <span data-ttu-id="649bd-117">Par exemple, entrez `$(SendPort1)`:</span><span class="sxs-lookup"><span data-stu-id="649bd-117">For example, enter `$(SendPort1)`:</span></span> 

    ![Fichier de liaison](../core/media/biztalk-feature-pack-1-binding-3.png)

4. <span data-ttu-id="649bd-119">Lorsque vous avez terminé, enregistrez le fichier de liaison et l’ajouter à votre modèle de génération JSON (étapes de [étape 1 : modèle de .json & mise à jour du projet Ajouter une Application](feature-pack-add-application-project.md)).</span><span class="sxs-lookup"><span data-stu-id="649bd-119">When done, save the binding file, and add it to your JSON build template (steps in [Step 1: Add Application project & update .json template](feature-pack-add-application-project.md)).</span></span>

## <a name="create-the-variables-in-vsts"></a><span data-ttu-id="649bd-120">Créez les variables dans VSTS</span><span class="sxs-lookup"><span data-stu-id="649bd-120">Create the variables in VSTS</span></span>

1. <span data-ttu-id="649bd-121">Dans votre compte VSTS, sélectionnez **créer et libérer**, puis sélectionnez **versions**.</span><span class="sxs-lookup"><span data-stu-id="649bd-121">In your VSTS account, select **Build and release**, and select **Releases**.</span></span>

2. <span data-ttu-id="649bd-122">Sélectionnez votre **définition de la version**, puis sélectionnez **Variables**:</span><span class="sxs-lookup"><span data-stu-id="649bd-122">Select your **Release definition**, and select **Variables**:</span></span>  

    ![Fichier de liaison](../core/media/vsts-release-variables.png)

3. <span data-ttu-id="649bd-124">Sélectionnez **ajouter**et créer les noms de variables et les valeurs :</span><span class="sxs-lookup"><span data-stu-id="649bd-124">Select **Add**, and create the variable names and values:</span></span>   

    ![configurer les variables](../core/media/environment-specific-variables.png)

4. <span data-ttu-id="649bd-126">**Enregistrer** vos modifications.</span><span class="sxs-lookup"><span data-stu-id="649bd-126">**Save** your changes.</span></span> <span data-ttu-id="649bd-127">Lorsque le déploiement est initialisé, les valeurs sont ajoutées à partir du fichier de liaison.</span><span class="sxs-lookup"><span data-stu-id="649bd-127">When the deploy is initiated, the values are added from the binding file.</span></span>

## <a name="see-also"></a><span data-ttu-id="649bd-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="649bd-128">See also</span></span>
[<span data-ttu-id="649bd-129">Configurer le déploiement automatique avec Visual Studio Team Services</span><span class="sxs-lookup"><span data-stu-id="649bd-129">Configure automatic deployment with Visual Studio Team Services</span></span>](configure-automatic-deployment-with-visual-studio-team-services-in-biztalk.md)  
[<span data-ttu-id="649bd-130">Télécharger le Feature Pack</span><span class="sxs-lookup"><span data-stu-id="649bd-130">Configure the feature pack</span></span>](configure-the-feature-pack.md)